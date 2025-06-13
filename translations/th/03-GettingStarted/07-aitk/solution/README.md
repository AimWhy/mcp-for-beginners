<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "e9490aedc71f99bc774af57b207a7adb",
  "translation_date": "2025-06-13T02:31:55+00:00",
  "source_file": "03-GettingStarted/07-aitk/solution/README.md",
  "language_code": "th"
}
-->
# 📘 โซลูชันการบ้าน: ขยาย MCP Server เครื่องคิดเลขของคุณด้วยเครื่องมือหาค่ารากที่สอง

## ภาพรวม  
ในการบ้านนี้ คุณได้เพิ่มฟีเจอร์ให้กับ MCP Server เครื่องคิดเลขของคุณโดยการเพิ่มเครื่องมือใหม่ที่คำนวณค่ารากที่สองของตัวเลข การเพิ่มนี้ช่วยให้ AI agent ของคุณสามารถจัดการกับคำถามทางคณิตศาสตร์ขั้นสูงขึ้น เช่น "รากที่สองของ 16 คืออะไร?" หรือ "คำนวณ √49" โดยใช้คำสั่งภาษาธรรมชาติ

## 🛠️ การใช้งานเครื่องมือหาค่ารากที่สอง  
เพื่อเพิ่มฟังก์ชันนี้ คุณได้กำหนดฟังก์ชันเครื่องมือใหม่ในไฟล์ server.py ของคุณ ดังนี้:

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

## 🔍 วิธีการทำงาน  

- **นำเข้า `math` และใช้ฟังก์ชัน `math.sqrt()` ร่วมกับ `@server.tool()` เพื่อสร้างเครื่องมือ `sqrt`**  
- เปิดโอกาสให้ AI agent ของคุณสามารถจัดการกับการคำนวณรากที่สองผ่านคำสั่งภาษาธรรมชาติได้  
- ฝึกฝนการเพิ่มเครื่องมือใหม่และรีสตาร์ทเซิร์ฟเวอร์เพื่อผสานฟังก์ชันเพิ่มเติม  

ลองทดลองเพิ่มเครื่องมือทางคณิตศาสตร์อื่น ๆ เช่น ฟังก์ชันเลขยกกำลัง หรือฟังก์ชันลอการิทึม เพื่อพัฒนาความสามารถของ agent ของคุณต่อไป!

**ข้อจำกัดความรับผิดชอบ**:  
เอกสารนี้ได้รับการแปลโดยใช้บริการแปลภาษาด้วย AI [Co-op Translator](https://github.com/Azure/co-op-translator) แม้เราจะพยายามให้การแปลมีความถูกต้อง แต่โปรดทราบว่าการแปลอัตโนมัติอาจมีข้อผิดพลาดหรือความคลาดเคลื่อนได้ เอกสารต้นฉบับในภาษาดั้งเดิมควรถือเป็นแหล่งข้อมูลที่น่าเชื่อถือ สำหรับข้อมูลที่สำคัญ ควรใช้บริการแปลโดยผู้เชี่ยวชาญมนุษย์ เราไม่รับผิดชอบต่อความเข้าใจผิดหรือการตีความที่ผิดพลาดใด ๆ ที่เกิดจากการใช้การแปลนี้