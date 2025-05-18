<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "e9490aedc71f99bc774af57b207a7adb",
  "translation_date": "2025-05-17T12:33:23+00:00",
  "source_file": "03-GettingStarted/06-aitk/solution/README.md",
  "language_code": "bn"
}
-->
# 📘 অ্যাসাইনমেন্ট সমাধান: আপনার ক্যালকুলেটর MCP সার্ভারে বর্গমূল টুল যুক্ত করা

## ওভারভিউ
এই অ্যাসাইনমেন্টে, আপনি আপনার ক্যালকুলেটর MCP সার্ভারে একটি নতুন টুল যোগ করেছেন যা একটি সংখ্যার বর্গমূল গণনা করে। এই সংযোজনটি আপনার AI এজেন্টকে আরও উন্নত গাণিতিক প্রশ্নগুলির সাথে মোকাবিলা করতে সক্ষম করে, যেমন "১৬-এর বর্গমূল কত?" বা "√৪৯ গণনা করুন," প্রাকৃতিক ভাষার প্রম্পট ব্যবহার করে।

## 🛠️ বর্গমূল টুল বাস্তবায়ন
এই কার্যকারিতা যোগ করার জন্য, আপনি আপনার server.py ফাইলে একটি নতুন টুল ফাংশন সংজ্ঞায়িত করেছেন। এখানে বাস্তবায়ন রয়েছে:

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

## 🔍 এটি কীভাবে কাজ করে

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

- Extended your calculator MCP server with a new `sqrt` টুল আমদানি করুন।
- আপনার AI এজেন্টকে প্রাকৃতিক ভাষার প্রম্পটের মাধ্যমে বর্গমূল গণনা পরিচালনা করতে সক্ষম করেছেন।
- নতুন টুল যোগ করার এবং অতিরিক্ত কার্যকারিতা সংযুক্ত করতে সার্ভার পুনরায় শুরু করার অনুশীলন করেছেন।

আপনার এজেন্টের সক্ষমতা আরও উন্নত করতে ঘাত বা লগারিদমিক ফাংশনের মতো আরও গাণিতিক টুল যোগ করে আরও পরীক্ষা-নিরীক্ষা করতে দ্বিধা করবেন না!

**অস্বীকৃতি**:  
এই নথিটি AI অনুবাদ পরিষেবা [Co-op Translator](https://github.com/Azure/co-op-translator) ব্যবহার করে অনুবাদ করা হয়েছে। আমরা যথাসম্ভব সঠিকতার চেষ্টা করি, তবে অনুগ্রহ করে সচেতন থাকুন যে স্বয়ংক্রিয় অনুবাদে ত্রুটি বা অসঙ্গতি থাকতে পারে। মূল ভাষায় থাকা নথিটিকেই প্রামাণিক উৎস হিসেবে বিবেচনা করা উচিত। গুরুত্বপূর্ণ তথ্যের জন্য পেশাদার মানব অনুবাদ সুপারিশ করা হয়। এই অনুবাদ ব্যবহারের ফলে কোনো ভুল বোঝাবুঝি বা ভুল ব্যাখ্যার জন্য আমরা দায়ী থাকব না।