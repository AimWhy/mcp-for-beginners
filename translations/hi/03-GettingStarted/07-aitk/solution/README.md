<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "e9490aedc71f99bc774af57b207a7adb",
  "translation_date": "2025-06-12T22:32:06+00:00",
  "source_file": "03-GettingStarted/07-aitk/solution/README.md",
  "language_code": "hi"
}
-->
# 📘 असाइनमेंट समाधान: अपने Calculator MCP Server में Square Root टूल जोड़ना

## अवलोकन
इस असाइनमेंट में, आपने अपने calculator MCP server को एक नए टूल से बेहतर बनाया जो किसी संख्या का वर्गमूल निकालता है। इस जोड़ से आपका AI एजेंट और भी उन्नत गणितीय सवालों को समझ सकता है, जैसे "16 का वर्गमूल क्या है?" या "√49 कैलकुलेट करें," और यह प्राकृतिक भाषा के संकेतों का उपयोग करता है।

## 🛠️ Square Root टूल को लागू करना
इस फंक्शनैलिटी को जोड़ने के लिए, आपने अपने server.py फाइल में एक नया टूल फंक्शन डिफाइन किया। यहाँ इसका इम्प्लीमेंटेशन है:

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

## 🔍 यह कैसे काम करता है

- **`math.sqrt()` टूल को इम्पोर्ट करें।**
- अपने AI एजेंट को प्राकृतिक भाषा के संकेतों के माध्यम से वर्गमूल की गणना संभालने में सक्षम बनाया।
- नए टूल्स जोड़ने और अतिरिक्त फंक्शनैलिटी इंटीग्रेट करने के लिए सर्वर को रीस्टार्ट करने का अभ्यास किया।

अपने एजेंट की क्षमताओं को और बढ़ाने के लिए घातांक या लघुगणकीय फंक्शन जैसे और गणितीय टूल्स जोड़कर प्रयोग करने में संकोच न करें!

**अस्वीकरण**:  
इस दस्तावेज़ का अनुवाद AI अनुवाद सेवा [Co-op Translator](https://github.com/Azure/co-op-translator) का उपयोग करके किया गया है। जबकि हम सटीकता के लिए प्रयासरत हैं, कृपया ध्यान दें कि स्वचालित अनुवादों में त्रुटियाँ या अशुद्धियाँ हो सकती हैं। मूल दस्तावेज़ को उसकी मूल भाषा में प्रामाणिक स्रोत माना जाना चाहिए। महत्वपूर्ण जानकारी के लिए पेशेवर मानव अनुवाद की सलाह दी जाती है। इस अनुवाद के उपयोग से उत्पन्न किसी भी गलतफहमी या गलत व्याख्या के लिए हम जिम्मेदार नहीं हैं।