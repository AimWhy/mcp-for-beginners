<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "e9490aedc71f99bc774af57b207a7adb",
  "translation_date": "2025-05-17T12:33:59+00:00",
  "source_file": "03-GettingStarted/06-aitk/solution/README.md",
  "language_code": "ne"
}
-->
# 📘 असाइनमेन्ट समाधान: तपाईंको क्याल्कुलेटर MCP सर्भरलाई वर्गमूल उपकरणले विस्तार गर्नुहोस्

## अवलोकन
यस असाइनमेन्टमा, तपाईंले आफ्नो क्याल्कुलेटर MCP सर्भरमा नयाँ उपकरण थप्नुभयो जसले सङ्ख्याको वर्गमूल गणना गर्छ। यस थपले तपाईंको AI एजेन्टलाई थप उन्नत गणितीय प्रश्नहरू, जस्तै "१६ को वर्गमूल के हो?" वा "√४९ गणना गर्नुहोस्," प्राकृतिक भाषाको संकेतहरू प्रयोग गरेर समाधान गर्न सक्षम बनाउँछ।

## 🛠️ वर्गमूल उपकरण कार्यान्वयन गर्दै
यो कार्यक्षमता थप्नका लागि, तपाईंले आफ्नो server.py फाइलमा नयाँ उपकरण कार्यफङ्क्शन परिभाषित गर्नुभयो। यहाँ कार्यान्वयन छ:

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

## 🔍 यो कसरी काम गर्छ

- `math` उपकरणलाई आयात गर्नुहोस्।
- तपाईंको AI एजेन्टलाई प्राकृतिक भाषाको संकेतहरू मार्फत वर्गमूल गणना गर्न सक्षम बनाउनुहोस्।
- नयाँ उपकरणहरू थप्ने र थप कार्यक्षमताहरू समाहित गर्न सर्भर पुनः सुरु गर्ने अभ्यास गर्नुहोस्।

अझै धेरै गणितीय उपकरणहरू, जस्तै घातांक गणना वा लघुगणकीय कार्यहरू, थपेर तपाईंको एजेन्टको क्षमताहरू बढाउन थप अन्वेषण गर्न नहिचकिचाउनुहोस्!

**अस्वीकरण**:  
यो दस्तावेज़ AI अनुवाद सेवा [Co-op Translator](https://github.com/Azure/co-op-translator) प्रयोग गरेर अनुवाद गरिएको छ। हामी शुद्धताको लागि प्रयास गर्छौं, तर कृपया ध्यान दिनुहोस् कि स्वचालित अनुवादहरूले त्रुटिहरू वा अशुद्धताहरू समावेश गर्न सक्दछन्। यसको मौलिक भाषा मा रहेको दस्तावेजलाई आधिकारिक स्रोत मान्नुपर्छ। महत्वपूर्ण जानकारीको लागि, पेशेवर मानव अनुवाद सिफारिस गरिन्छ। यस अनुवादको प्रयोगबाट उत्पन्न हुने कुनै पनि गलतफहमी वा गलत व्याख्या को लागि हामी जिम्मेवार छैनौं।