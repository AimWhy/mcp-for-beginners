<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "e9490aedc71f99bc774af57b207a7adb",
  "translation_date": "2025-05-17T12:33:38+00:00",
  "source_file": "03-GettingStarted/06-aitk/solution/README.md",
  "language_code": "mr"
}
-->
# 📘 असाइनमेंट समाधान: आपल्या कॅल्क्युलेटर MCP सर्व्हरमध्ये वर्गमूळ साधन जोडणे

## आढावा
या असाइनमेंटमध्ये, तुम्ही आपल्या कॅल्क्युलेटर MCP सर्व्हरमध्ये एक नवीन साधन जोडले आहे जे एका संख्येचे वर्गमूळ गणना करते. या जोडणीमुळे तुमच्या AI एजंटला अधिक प्रगत गणितीय प्रश्न हाताळण्याची क्षमता मिळते, जसे की "16 चे वर्गमूळ काय आहे?" किंवा "√49 गणना करा," नैसर्गिक भाषा प्रॉम्प्ट्स वापरून.

## 🛠️ वर्गमूळ साधन लागू करणे
ही कार्यक्षमता जोडण्यासाठी, तुम्ही आपल्या server.py फाइलमध्ये एक नवीन साधन फंक्शन परिभाषित केले आहे. येथे त्याची अंमलबजावणी आहे:

```python
"""
Sample MCP Calculator Server implementation in Python.

This module demonstrates how to create a simple MCP server with calculator tools
that can perform basic arithmetic operations (add, subtract, multiply, divide).
"""

from mcp.server.fastmcp import FastMCP
import math

server = FastMCP("calculator")

@server.tool()
def add(a: float, b: float) -> float:
    """Add two numbers together and return the result."""
    return a + b

@server.tool()
def subtract(a: float, b: float) -> float:
    """Subtract b from a and return the result."""
    return a - b

@server.tool()
def multiply(a: float, b: float) -> float:
    """Multiply two numbers together and return the result."""
    return a * b

@server.tool()
def divide(a: float, b: float) -> float:
    """
    Divide a by b and return the result.
    
    Raises:
        ValueError: If b is zero
    """
    if b == 0:
        raise ValueError("Cannot divide by zero")
    return a / b

@server.tool()
def sqrt(a: float) -> float:
    """
    Return the square root of a.

    Raises:
        ValueError: If a is negative.
    """
    if a < 0:
        raise ValueError("Cannot compute the square root of a negative number.")
    return math.sqrt(a)
```

## 🔍 हे कसे कार्य करते

- **`math` module**: To perform mathematical operations beyond basic arithmetic, Python provides the built-in `math` module. This module includes a variety of mathematical functions and constants. By importing it using `import math`, you gain access to functions like `math.sqrt()`, which computes the square root of a number.
- **Function Definition**: The `@server.tool()` decorator registers the `sqrt` function as a tool accessible by your AI agent.
- **Input Parameter**: The function accepts a single argument `a` of type `float`.
- **Error Handling**: If `a` is negative, the function raises a `ValueError` to prevent computing the square root of a negative number, which is not supported by the `math.sqrt()` function.
- **Return Value**: For non-negative inputs, the function returns the square root of `a` using Python's built-in `math.sqrt()` method.

## 🔄 Restarting the Server
After adding the new `sqrt` tool, it's essential to restart your MCP server to ensure the agent recognizes and can utilize the newly added functionality.

## 💬 Example Prompts to Test the New Tool
Here are some natural language prompts you can use to test the square root functionality:

- "What is the square root of 25?"
- "Calculate the square root of 81."
- "Find the square root of 0."
- "What is the square root of 2.25?"

These prompts should trigger the agent to invoke the `sqrt` tool and return the correct results.

## ✅ Summary
By completing this assignment, you've:

- Extended your calculator MCP server with a new `sqrt` साधन आयात करा.
- नैसर्गिक भाषा प्रॉम्प्ट्सद्वारे वर्गमूळ गणना हाताळण्यासाठी तुमच्या AI एजंटला सक्षम केले.
- नवीन साधने जोडणे आणि अतिरिक्त कार्यक्षमता समाकलित करण्यासाठी सर्व्हर पुन्हा सुरू करणे याचा सराव केला.

तुमच्या एजंटच्या क्षमतेला वाढवण्यासाठी घातांक किंवा लघुगणकीय कार्ये यासारखी अधिक गणितीय साधने जोडून पुढील प्रयोग करण्यास मोकळे रहा!

**अस्वीकरण**:  
हा दस्तऐवज AI भाषांतर सेवा [Co-op Translator](https://github.com/Azure/co-op-translator) वापरून भाषांतरित केला आहे. आम्ही अचूकतेसाठी प्रयत्नशील असलो तरी कृपया लक्षात घ्या की स्वयंचलित भाषांतरे त्रुटी किंवा अचूकता नसलेली असू शकतात. मूळ दस्तऐवज त्याच्या स्थानिक भाषेत अधिकृत स्रोत म्हणून विचारात घेतला पाहिजे. महत्त्वपूर्ण माहितीसाठी, व्यावसायिक मानवी भाषांतराची शिफारस केली जाते. या भाषांतराच्या वापरामुळे उद्भवणाऱ्या कोणत्याही गैरसमज किंवा चुकीच्या अर्थासाठी आम्ही जबाबदार नाही.