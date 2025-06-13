<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "e9490aedc71f99bc774af57b207a7adb",
  "translation_date": "2025-06-13T02:31:04+00:00",
  "source_file": "03-GettingStarted/07-aitk/solution/README.md",
  "language_code": "bn"
}
-->
# 📘 অ্যাসাইনমেন্ট সলিউশন: আপনার ক্যালকুলেটর MCP সার্ভারে স্কয়ার রুট টুল যুক্ত করা

## ওভারভিউ
এই অ্যাসাইনমেন্টে, আপনি আপনার ক্যালকুলেটর MCP সার্ভারে একটি নতুন টুল যোগ করেছেন যা একটি সংখ্যার স্কয়ার রুট হিসাব করে। এই সংযোজনের মাধ্যমে আপনার AI এজেন্ট আরও জটিল গাণিতিক প্রশ্ন যেমন "16 এর স্কয়ার রুট কত?" অথবা "√49 হিসাব করুন" প্রাকৃতিক ভাষার মাধ্যমে সমাধান করতে সক্ষম হয়েছে।

## 🛠️ স্কয়ার রুট টুল বাস্তবায়ন
এই ফাংশনালিটি যোগ করতে, আপনি আপনার server.py ফাইলে একটি নতুন টুল ফাংশন সংজ্ঞায়িত করেছেন। এখানে তার বাস্তবায়ন দেওয়া হলো:

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

- **`math.sqrt()` টুলটি ইমপোর্ট করেছেন।**
- আপনার AI এজেন্টকে প্রাকৃতিক ভাষার মাধ্যমে স্কয়ার রুট হিসাব করার ক্ষমতা দিয়েছেন।
- নতুন টুল যোগ করা এবং সার্ভার রিস্টার্ট করে অতিরিক্ত ফাংশনালিটি একত্রিত করার অনুশীলন করেছেন।

আপনার এজেন্টের সক্ষমতা বাড়াতে আরও গাণিতিক টুল যেমন ঘাতফল বা লগারিদমিক ফাংশন যোগ করার মাধ্যমে আরও পরীক্ষা-নিরীক্ষা করতে পারেন!

**অস্বীকারোক্তি**:  
এই নথিটি AI অনুবাদ সেবা [Co-op Translator](https://github.com/Azure/co-op-translator) ব্যবহার করে অনূদিত হয়েছে। আমরা যথাসাধ্য সঠিকতার চেষ্টা করি, তবে দয়া করে জানুন যে স্বয়ংক্রিয় অনুবাদে ত্রুটি বা ভুল থাকতে পারে। মূল নথিটি তার নিজ ভাষায়ই কর্তৃপক্ষিক উৎস হিসাবে বিবেচিত হবে। গুরুত্বপূর্ণ তথ্যের জন্য পেশাদার মানব অনুবাদ গ্রহণ করা উচিৎ। এই অনুবাদের ব্যবহার থেকে উদ্ভূত কোনো ভুল বোঝাবুঝি বা ভুল ব্যাখ্যার জন্য আমরা দায়বদ্ধ নই।