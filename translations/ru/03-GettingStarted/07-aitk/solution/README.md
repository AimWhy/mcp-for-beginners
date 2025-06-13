<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "e9490aedc71f99bc774af57b207a7adb",
  "translation_date": "2025-06-13T02:30:37+00:00",
  "source_file": "03-GettingStarted/07-aitk/solution/README.md",
  "language_code": "ru"
}
-->
# 📘 Решение задания: Расширение вашего MCP-сервера калькулятора инструментом для вычисления квадратного корня

## Обзор
В этом задании вы расширили ваш MCP-сервер калькулятора, добавив новый инструмент для вычисления квадратного корня числа. Это позволяет вашему AI-агенту обрабатывать более сложные математические запросы, например «Какой квадратный корень из 16?» или «Вычисли √49», используя естественные языковые команды.

## 🛠️ Реализация инструмента квадратного корня
Для добавления этой функции вы определили новую функцию-инструмент в файле server.py. Вот реализация:

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

## 🔍 Как это работает

- **Импортируйте инструмент `math.sqrt` с помощью `@server.tool()` с именем `sqrt`.**
- Позволили вашему AI-агенту выполнять вычисления квадратного корня через естественные языковые запросы.
- Попрактиковались в добавлении новых инструментов и перезапуске сервера для интеграции дополнительных функций.

Не стесняйтесь экспериментировать дальше, добавляя больше математических инструментов, таких как возведение в степень или логарифмы, чтобы продолжать расширять возможности вашего агента!

**Отказ от ответственности**:  
Этот документ был переведен с помощью сервиса автоматического перевода [Co-op Translator](https://github.com/Azure/co-op-translator). Несмотря на наши усилия по обеспечению точности, имейте в виду, что автоматический перевод может содержать ошибки или неточности. Оригинальный документ на его исходном языке следует считать авторитетным источником. Для получения критически важной информации рекомендуется обращаться к профессиональному переводу, выполненному человеком. Мы не несем ответственности за любые недоразумения или неправильные толкования, возникшие в результате использования данного перевода.