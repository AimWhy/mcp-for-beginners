<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "e9490aedc71f99bc774af57b207a7adb",
  "translation_date": "2025-06-13T02:31:21+00:00",
  "source_file": "03-GettingStarted/07-aitk/solution/README.md",
  "language_code": "pa"
}
-->
# 📘 ਅਸਾਈਨਮੈਂਟ ਹੱਲ: ਆਪਣੇ ਕੈਲਕੂਲੇਟਰ MCP ਸਰਵਰ ਵਿੱਚ ਵਰਗਮੂਲ ਟੂਲ ਸ਼ਾਮਲ ਕਰਨਾ

## ਝਲਕ
ਇਸ ਅਸਾਈਨਮੈਂਟ ਵਿੱਚ, ਤੁਸੀਂ ਆਪਣੇ ਕੈਲਕੂਲੇਟਰ MCP ਸਰਵਰ ਨੂੰ ਇੱਕ ਨਵਾਂ ਟੂਲ ਜੋੜ ਕੇ ਸੁਧਾਰਿਆ ਜੋ ਕਿਸੇ ਸੰਖਿਆ ਦਾ ਵਰਗਮੂਲ ਕੱਢਦਾ ਹੈ। ਇਸ ਜੋੜ ਨਾਲ ਤੁਹਾਡਾ AI ਏਜੰਟ ਹੋਰ ਅੱਗੇ ਵਧੇ ਹੋਏ ਗਣਿਤੀ ਪ੍ਰਸ਼ਨਾਂ ਨੂੰ ਸੰਭਾਲ ਸਕਦਾ ਹੈ, ਜਿਵੇਂ "16 ਦਾ ਵਰਗਮੂਲ ਕੀ ਹੈ?" ਜਾਂ "√49 ਕੈਲਕੂਲੇਟ ਕਰੋ," ਕੁਦਰਤੀ ਭਾਸ਼ਾ ਦੇ ਪ੍ਰੰਪਟਾਂ ਦੀ ਵਰਤੋਂ ਕਰਕੇ।

## 🛠️ ਵਰਗਮੂਲ ਟੂਲ ਲਾਗੂ ਕਰਨਾ
ਇਹ ਫੰਕਸ਼ਨਾਲਿਟੀ ਸ਼ਾਮਲ ਕਰਨ ਲਈ, ਤੁਸੀਂ ਆਪਣੇ server.py ਫਾਇਲ ਵਿੱਚ ਇੱਕ ਨਵਾਂ ਟੂਲ ਫੰਕਸ਼ਨ ਪਰਿਭਾਸ਼ਿਤ ਕੀਤਾ। ਇਹ ਹੈ ਇਸਦੀ ਲਾਗੂਆਈ:

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

## 🔍 ਇਹ ਕਿਵੇਂ ਕੰਮ ਕਰਦਾ ਹੈ

- **`math.sqrt()` ਟੂਲ ਨੂੰ ਇੰਪੋਰਟ ਕਰੋ।**
- ਤੁਹਾਡੇ AI ਏਜੰਟ ਨੂੰ ਕੁਦਰਤੀ ਭਾਸ਼ਾ ਦੇ ਪ੍ਰੰਪਟਾਂ ਰਾਹੀਂ ਵਰਗਮੂਲ ਕੈਲਕੂਲੇਸ਼ਨ ਕਰਨ ਯੋਗ ਬਣਾਇਆ।
- ਨਵੇਂ ਟੂਲ ਸ਼ਾਮਲ ਕਰਨ ਅਤੇ ਸਰਵਰ ਨੂੰ ਰੀਸਟਾਰਟ ਕਰਨ ਦੀ ਪ੍ਰੈਕਟਿਸ ਕੀਤੀ ਤਾਂ ਜੋ ਵਾਧੂ ਫੰਕਸ਼ਨਾਲਿਟੀਜ਼ ਜੁੜ ਸਕਣ।

ਹੋਰ ਗਣਿਤੀ ਟੂਲ ਜਿਵੇਂ ਘਾਤਾਕਾਰੀ ਜਾਂ ਲੋਗਾਰਿਦਮਿਕ ਫੰਕਸ਼ਨਾਂ ਨੂੰ ਸ਼ਾਮਲ ਕਰਕੇ ਆਪਣੇ ਏਜੰਟ ਦੀ ਸਮਰੱਥਾ ਹੋਰ ਵਧਾਉਣ ਲਈ ਅਜ਼ਮਾਇਸ਼ ਜਾਰੀ ਰੱਖੋ!

**ਡਿਸਕਲੇਮਰ**:  
ਇਹ ਦਸਤਾਵੇਜ਼ AI ਅਨੁਵਾਦ ਸੇਵਾ [Co-op Translator](https://github.com/Azure/co-op-translator) ਦੀ ਵਰਤੋਂ ਕਰਕੇ ਅਨੁਵਾਦ ਕੀਤਾ ਗਿਆ ਹੈ। ਜਦੋਂ ਕਿ ਅਸੀਂ ਸਹੀਤਾ ਲਈ ਕੋਸ਼ਿਸ਼ ਕਰਦੇ ਹਾਂ, ਕਿਰਪਾ ਕਰਕੇ ਧਿਆਨ ਰੱਖੋ ਕਿ ਸਵੈਚਾਲਿਤ ਅਨੁਵਾਦਾਂ ਵਿੱਚ ਗਲਤੀਆਂ ਜਾਂ ਅਸਹੀਤਾਵਾਂ ਹੋ ਸਕਦੀਆਂ ਹਨ। ਮੂਲ ਦਸਤਾਵੇਜ਼ ਆਪਣੀ ਮੂਲ ਭਾਸ਼ਾ ਵਿੱਚ ਪ੍ਰਮਾਣਿਕ ਸਰੋਤ ਮੰਨਿਆ ਜਾਣਾ ਚਾਹੀਦਾ ਹੈ। ਮਹੱਤਵਪੂਰਨ ਜਾਣਕਾਰੀ ਲਈ, ਪੇਸ਼ੇਵਰ ਮਨੁੱਖੀ ਅਨੁਵਾਦ ਦੀ ਸਿਫਾਰਸ਼ ਕੀਤੀ ਜਾਂਦੀ ਹੈ। ਅਸੀਂ ਇਸ ਅਨੁਵਾਦ ਦੀ ਵਰਤੋਂ ਤੋਂ ਉਪਜਣ ਵਾਲੀਆਂ ਕਿਸੇ ਵੀ ਗਲਤਫਹਿਮੀਆਂ ਜਾਂ ਗਲਤ ਵਿਅਖਿਆਵਾਂ ਲਈ ਜ਼ਿੰਮੇਵਾਰ ਨਹੀਂ ਹਾਂ।