<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "e9490aedc71f99bc774af57b207a7adb",
  "translation_date": "2025-06-13T02:33:42+00:00",
  "source_file": "03-GettingStarted/07-aitk/solution/README.md",
  "language_code": "bg"
}
-->
# 📘 Решение на задачата: Разширяване на вашия MCP сървър за калкулатор с инструмент за квадратен корен

## Преглед
В тази задача разширихте вашия MCP сървър за калкулатор, като добавихте нов инструмент, който изчислява квадратния корен на число. Това допълнение позволява на вашия AI агент да обработва по-сложни математически запитвания, като „Какъв е квадратният корен на 16?“ или „Изчисли √49“, използвайки естествен език.

## 🛠️ Имплементиране на инструмента за квадратен корен
За да добавите тази функционалност, дефинирахте нова функция за инструмент във файла server.py. Ето имплементацията:

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

## 🔍 Как работи

- **Импортирайте инструмента `math.sqrt()` и го декорирайте с @server.tool() като `sqrt` функция.**
- Позволихте на вашия AI агент да извършва изчисления на квадратни корени чрез естествени езикови заявки.
- Практикувахте добавянето на нови инструменти и рестартирането на сървъра, за да интегрирате допълнителни функционалности.

Не се колебайте да експериментирате, като добавите още математически инструменти, като степенуване или логаритмични функции, за да продължите да подобрявате възможностите на вашия агент!

**Отказ от отговорност**:  
Този документ е преведен с помощта на AI преводаческа услуга [Co-op Translator](https://github.com/Azure/co-op-translator). Въпреки че се стремим към точност, моля, имайте предвид, че автоматизираните преводи могат да съдържат грешки или неточности. Оригиналният документ на неговия език трябва да се счита за авторитетен източник. За критична информация се препоръчва професионален човешки превод. Ние не носим отговорност за каквито и да е недоразумения или неправилни тълкувания, възникнали в резултат на използването на този превод.