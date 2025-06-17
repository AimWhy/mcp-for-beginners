<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "e9490aedc71f99bc774af57b207a7adb",
  "translation_date": "2025-06-17T16:49:04+00:00",
  "source_file": "03-GettingStarted/07-aitk/solution/README.md",
  "language_code": "uk"
}
-->
# 📘 Розв’язок завдання: Розширення сервера калькулятора MCP інструментом для обчислення квадратного кореня

## Огляд
У цьому завданні ви розширили сервер калькулятора MCP, додавши новий інструмент, який обчислює квадратний корінь числа. Це дозволяє вашому AI-агенту працювати з більш складними математичними запитами, наприклад: «Який квадратний корінь з 16?» або «Обчисли √49», використовуючи природні мовні запити.

## 🛠️ Реалізація інструмента квадратного кореня
Щоб додати цю функціональність, ви визначили нову функцію інструмента у файлі server.py. Ось реалізація:

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

## 🔍 Як це працює

- **Імпортували інструмент `math.sqrt()` з модуля math.**
- Надали вашому AI-агенту можливість обробляти обчислення квадратного кореня через запити природною мовою.
- Відпрацювали додавання нових інструментів та перезапуск сервера для інтеграції додаткових функцій.

Не соромтеся експериментувати далі, додаючи інші математичні інструменти, такі як піднесення до степеня або логарифмічні функції, щоб ще більше розширити можливості вашого агента!

**Відмова від відповідальності**:  
Цей документ був перекладений за допомогою сервісу автоматичного перекладу [Co-op Translator](https://github.com/Azure/co-op-translator). Хоча ми прагнемо до точності, будь ласка, майте на увазі, що автоматичні переклади можуть містити помилки або неточності. Оригінальний документ рідною мовою слід вважати авторитетним джерелом. Для критично важливої інформації рекомендується звертатися до професійного людського перекладу. Ми не несемо відповідальності за будь-які непорозуміння або неправильні тлумачення, що виникли внаслідок використання цього перекладу.