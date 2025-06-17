<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "e9490aedc71f99bc774af57b207a7adb",
  "translation_date": "2025-06-17T16:48:56+00:00",
  "source_file": "03-GettingStarted/07-aitk/solution/README.md",
  "language_code": "my"
}
-->
# 📘 အလုပ်အပ်တာ ဖြေရှင်းချက်: သင်၏ Calculator MCP Server ကို စတုရန်းမြစ်ကိရိယာဖြင့် တိုးချဲ့ခြင်း

## အကျဉ်းချုပ်  
ဒီအလုပ်အပ်တာမှာ သင်၏ calculator MCP server ကို တိုးချဲ့ပြီး အရေအတွက်တစ်ခု၏ စတုရန်းမြစ်ကိုတွက်ချက်ပေးနိုင်တဲ့ ကိရိယာအသစ်တစ်ခု ထည့်သွင်းခဲ့ပါတယ်။ ဒီထည့်သွင်းမှုကြောင့် သင့် AI ကိုယ်စားလှယ်က "၁၆ ရဲ့ စတုရန်းမြစ် ဘာလဲ?" သို့မဟုတ် "√၄၉ ကိုတွက်ပါ" စတဲ့ သဘာဝဘာသာစကား ဖြင့် မေးခွန်းများကို ပိုမိုရှုပ်ထွေးတဲ့ သင်္ချာဆိုင်ရာ စုံစမ်းချက်များကို ကိုင်တွယ်နိုင်ပါပြီ။

## 🛠️ စတုရန်းမြစ်ကိရိယာကို အကောင်အထည်ဖော်ခြင်း  
ဒီလုပ်ဆောင်ချက်ကို ထည့်သွင်းဖို့ server.py ဖိုင်ထဲမှာ ကိရိယာအသစ် function တစ်ခုကို သတ်မှတ်ခဲ့ပါတယ်။ အောက်မှာ အကောင်အထည်ဖော်ထားတဲ့ နမူနာကို ကြည့်ရှုနိုင်ပါတယ်။

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

## 🔍 လုပ်ဆောင်ပုံ  

- **`math.sqrt()` ကိရိယာကို `math` မှ import လုပ်ခြင်း**  
- သင်၏ AI ကိုယ်စားလှယ်ကို သဘာဝဘာသာစကားဖြင့် စတုရန်းမြစ်တွက်ချက်မှုများကို ကိုင်တွယ်နိုင်အောင် ဖွင့်လှစ်ပေးခြင်း  
- ကိရိယာအသစ်များ ထည့်သွင်းပြီး server ကို ပြန်စတင်ခြင်းဖြင့် လုပ်ဆောင်ချက်အသစ်များ ပေါင်းထည့်ခြင်းကို လေ့ကျင့်ခဲ့ခြင်း  

သင့် AI ကိုယ်စားလှယ်၏ စွမ်းရည်များကို ပိုမိုတိုးတက်အောင် exponentiation သို့မဟုတ် logarithmic လုပ်ဆောင်ချက်များကဲ့သို့ သင်္ချာကိရိယာများ ပိုမိုထည့်သွင်းကာ စမ်းသပ်နိုင်ပါတယ်!

**တစ်ဖန်မှတ်ချက်**  
ဤစာတမ်းကို AI ဘာသာပြန်ဝန်ဆောင်မှု [Co-op Translator](https://github.com/Azure/co-op-translator) ကို အသုံးပြု၍ ဘာသာပြန်ထားပါသည်။ တိကျမှန်ကန်မှုအတွက် ကြိုးစားပေမယ့် အလိုအလျောက် ဘာသာပြန်ခြင်းသည် အမှားများ သို့မဟုတ် မှားယွင်းချက်များ ပါဝင်နိုင်ကြောင်း သတိပြုပါရန် လိုအပ်ပါသည်။ မူရင်းစာတမ်းကို မိခင်ဘာသာဖြင့်သာ ယုံကြည်စိတ်ချရသော အရင်းအမြစ်အဖြစ် သတ်မှတ်သင့်ပါသည်။ အရေးကြီးသော သတင်းအချက်အလက်များအတွက် ပရော်ဖက်ရှင်နယ် လူသား ဘာသာပြန်ခြင်းကို အကြံပြုပါသည်။ ဤဘာသာပြန်ချက်ကို အသုံးပြုရာမှ ဖြစ်ပေါ်လာသော နားလည်မှုမှားယွင်းမှုများအတွက် ကျွန်ုပ်တို့သည် တာဝန်မယူပါ။