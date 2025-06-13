<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "e9490aedc71f99bc774af57b207a7adb",
  "translation_date": "2025-06-13T02:31:10+00:00",
  "source_file": "03-GettingStarted/07-aitk/solution/README.md",
  "language_code": "mr"
}
-->
# 📘 Assignment Solution: Extending Your Calculator MCP Server with a Square Root Tool

## Overview
या असाइनमेंटमध्ये, तुम्ही तुमच्या calculator MCP सर्व्हरमध्ये एक नवीन टूल जोडले ज्यामुळे एखाद्या संख्येचा वर्गमुळ काढता येतो. या जोडणीमुळे तुमचा AI एजंट अधिक प्रगत गणितीय प्रश्न हाताळू शकतो, जसे की "16 चा वर्गमुळ काय आहे?" किंवा "√49 काढा," हे नैसर्गिक भाषेतील प्रॉम्प्ट्स वापरून.

## 🛠️ Implementing the Square Root Tool
ही फंक्शनॅलिटी जोडण्यासाठी, तुम्ही तुमच्या server.py फाइलमध्ये एक नवीन टूल फंक्शन डिफाईन केलं. इथे त्याची अंमलबजावणी आहे:

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

## 🔍 How It Works

- **`math.sqrt()` टूल आयात करा.**
- तुमच्या AI एजंटला वर्गमुळ काढण्याचे गणितीय प्रश्न नैसर्गिक भाषेतून हाताळण्यास सक्षम करा.
- नवीन टूल्स जोडण्याचा आणि सर्व्हर रीस्टार्ट करून नवीन फंक्शनॅलिटी इंटिग्रेट करण्याचा सराव करा.

आणखी गणितीय टूल्स जसे की घातांक किंवा लोगारिदमिक फंक्शन्स जोडून तुमच्या एजंटच्या क्षमतांना अजून वाढवण्याचा प्रयत्न करा!

**अस्वीकरण**:  
हा दस्तऐवज AI भाषांतर सेवा [Co-op Translator](https://github.com/Azure/co-op-translator) वापरून भाषांतरित केला आहे. आम्ही अचूकतेसाठी प्रयत्न करतो, परंतु कृपया लक्षात घ्या की स्वयंचलित भाषांतरांमध्ये चुका किंवा अचूकतेच्या त्रुटी असू शकतात. मूळ दस्तऐवज त्याच्या स्थानिक भाषेत अधिकृत स्रोत मानला जावा. महत्त्वाच्या माहितीकरिता, व्यावसायिक मानवी भाषांतर करण्याची शिफारस केली जाते. या भाषांतराचा वापर करून उद्भवणाऱ्या कोणत्याही गैरसमजुती किंवा चुकीच्या अर्थलागी आम्ही जबाबदार नाही.