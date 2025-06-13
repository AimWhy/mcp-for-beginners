<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "e9490aedc71f99bc774af57b207a7adb",
  "translation_date": "2025-06-13T02:31:47+00:00",
  "source_file": "03-GettingStarted/07-aitk/solution/README.md",
  "language_code": "el"
}
-->
# 📘 Λύση Άσκησης: Επέκταση του MCP Server του Υπολογιστή σας με Εργαλείο Τετραγωνικής Ρίζας

## Επισκόπηση  
Σε αυτήν την άσκηση, βελτιώσατε τον MCP server του υπολογιστή σας προσθέτοντας ένα νέο εργαλείο που υπολογίζει την τετραγωνική ρίζα ενός αριθμού. Αυτή η προσθήκη επιτρέπει στον AI πράκτορά σας να χειρίζεται πιο προχωρημένα μαθηματικά ερωτήματα, όπως «Ποια είναι η τετραγωνική ρίζα του 16;» ή «Υπολόγισε √49», χρησιμοποιώντας φυσικές γλωσσικές εντολές.

## 🛠️ Υλοποίηση του Εργαλείου Τετραγωνικής Ρίζας  
Για να προσθέσετε αυτή τη λειτουργία, ορίσατε μια νέα συνάρτηση εργαλείου στο αρχείο server.py σας. Να η υλοποίηση:

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

## 🔍 Πώς Λειτουργεί

- **Εισάγετε το εργαλείο `math.sqrt()` με `@server.tool()` που ονομάζεται `sqrt`.  
- Επιτρέψατε στον AI πράκτορά σας να χειρίζεται υπολογισμούς τετραγωνικής ρίζας μέσω φυσικών γλωσσικών εντολών.  
- Εξασκηθήκατε στην προσθήκη νέων εργαλείων και στην επανεκκίνηση του server για να ενσωματώσετε επιπλέον λειτουργίες.

Μη διστάσετε να πειραματιστείτε περαιτέρω προσθέτοντας περισσότερα μαθηματικά εργαλεία, όπως εκθετικές ή λογαριθμικές συναρτήσεις, για να συνεχίσετε να βελτιώνετε τις δυνατότητες του πράκτορά σας!

**Αποποίηση ευθυνών**:  
Αυτό το έγγραφο έχει μεταφραστεί χρησιμοποιώντας την υπηρεσία αυτόματης μετάφρασης AI [Co-op Translator](https://github.com/Azure/co-op-translator). Παρόλο που προσπαθούμε για ακρίβεια, παρακαλούμε να έχετε υπόψη ότι οι αυτόματες μεταφράσεις μπορεί να περιέχουν λάθη ή ανακρίβειες. Το πρωτότυπο έγγραφο στη γλώσσα του θεωρείται η αυθεντική πηγή. Για κρίσιμες πληροφορίες, συνιστάται η επαγγελματική μετάφραση από άνθρωπο. Δεν φέρουμε ευθύνη για οποιεσδήποτε παρεξηγήσεις ή λανθασμένες ερμηνείες που προκύπτουν από τη χρήση αυτής της μετάφρασης.