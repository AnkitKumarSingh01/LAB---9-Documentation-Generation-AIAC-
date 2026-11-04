# Lab 9.3: Documentation Generation

## Overview

This project demonstrates manual and AI-assisted generation of Python docstrings and inline comments. It covers function-level documentation, class comments, module-level documentation, and NumPy-style docstrings.

## Task 1 — Basic docstring generation

### Purpose

Create a function that returns the sum of even numbers and the sum of odd numbers.

### Manually documented implementation

```python
def sum\\\\\\\_even\\\\\\\_odd(numbers):
    """Calculate the sums of even and odd integers in a list.

    Args:
        numbers (list\\\\\\\[int]): A list of integers to process.

    Returns:
        tuple\\\\\\\[int, int]: A tuple containing (sum\\\\\\\_of\\\\\\\_evens, sum\\\\\\\_of\\\\\\\_odds).

    Example:
        >>> sum\\\\\\\_even\\\\\\\_odd(\\\\\\\[1, 2, 3, 4, 5])
        (6, 9)
    """
    even\\\\\\\_sum = 0
    odd\\\\\\\_sum = 0

    for number in numbers:
        if number % 2 == 0:
            even\\\\\\\_sum += number
        else:
            odd\\\\\\\_sum += number

    return even\\\\\\\_sum, odd\\\\\\\_sum


if \\\\\\\_\\\\\\\_name\\\\\\\_\\\\\\\_ == "\\\\\\\_\\\\\\\_main\\\\\\\_\\\\\\\_":
    sample = \\\\\\\[1, 2, 3, 4, 5, 6]
    print("Input:", sample)
    even\\\\\\\_total, odd\\\\\\\_total = sum\\\\\\\_even\\\\\\\_odd(sample)
    print("Sum of even numbers:", even\\\\\\\_total)
    print("Sum of odd numbers:", odd\\\\\\\_total)
```

### AI-assisted docstring example

The following is an illustrative AI-generated alternative. It should be treated as a draft and reviewed before use.

```python
def sum\\\\\\\_even\\\\\\\_odd(numbers):
    """Return the total of even values and the total of odd values.

    Args:
        numbers: An iterable containing integer values.

    Returns:
        A two-item tuple: the first item is the sum of even values,
        and the second item is the sum of odd values.

    Raises:
        TypeError: If an element does not support the modulo operation
            or addition with an integer.
    """
    even\\\\\\\_sum = 0
    odd\\\\\\\_sum = 0

    for number in numbers:
        if number % 2 == 0:
            even\\\\\\\_sum += number
        else:
            odd\\\\\\\_sum += number

    return even\\\\\\\_sum, odd\\\\\\\_sum
```

### Comparison

* Both versions explain the two returned totals and the argument.
* The manual version explicitly says `list\\\\\\\[int]` and gives a runnable example.
* The AI version uses the broader word “iterable”, which is not exactly the stated list requirement.
* The AI version includes a possible `TypeError`, but the exact exception behaviour depends on the input and Python operations.
* The manual version is more aligned with the assignment's specified input; the AI version is concise but needs verification.

### Expected output

```text
Input: \\\\\\\[1, 2, 3, 4, 5, 6]
Sum of even numbers: 12
Sum of odd numbers: 9
```

## Task 2 — Automatic inline comments

### Purpose

Create an `sru\\\\\\\_student` class with `name`, `roll\\\\\\\_no`, and `hostel\\\\\\\_status`, plus `fee\\\\\\\_update()` and `display\\\\\\\_details()` methods. A `fee` field is initialized to zero so the update method has a balance to modify.

### Manually commented implementation

```python
class sru\\\\\\\_student:
    # Initialize a student record with the supplied details.
    def \\\\\\\_\\\\\\\_init\\\\\\\_\\\\\\\_(self, name, roll\\\\\\\_no, hostel\\\\\\\_status):
        self.name = name                  # Store the student's name.
        self.roll\\\\\\\_no = roll\\\\\\\_no            # Store the student's roll number.
        self.hostel\\\\\\\_status = hostel\\\\\\\_status  # Store whether the student lives in a hostel.
        self.fee = 0                      # Start with a default fee balance of zero.

    # Add an amount to the student's fee balance.
    def fee\\\\\\\_update(self, amount):
        self.fee += amount                # Increase the current fee by the given amount.

    # Print the student's current details and fee balance.
    def display\\\\\\\_details(self):
        print("Name:", self.name)         # Display the student's name.
        print("Roll No:", self.roll\\\\\\\_no)   # Display the student's roll number.
        print("Hostel Status:", self.hostel\\\\\\\_status)  # Display hostel information.
        print("Fee:", self.fee)           # Display the updated fee balance.


if \\\\\\\_\\\\\\\_name\\\\\\\_\\\\\\\_ == "\\\\\\\_\\\\\\\_main\\\\\\\_\\\\\\\_":
    student = sru\\\\\\\_student("Aarav", 101, "Yes")
    student.fee\\\\\\\_update(25000)
    student.display\\\\\\\_details()
```

### AI-assisted comments/documentation example

This is a representative AI-assisted version, with comments expressed as class and method docstrings and descriptive code structure.

```python
class sru\\\\\\\_student:
    """Represent a student and maintain a simple fee balance."""

    def \\\\\\\_\\\\\\\_init\\\\\\\_\\\\\\\_(self, name, roll\\\\\\\_no, hostel\\\\\\\_status):
        self.name = name
        self.roll\\\\\\\_no = roll\\\\\\\_no
        self.hostel\\\\\\\_status = hostel\\\\\\\_status
        self.fee = 0

    def fee\\\\\\\_update(self, amount):
        """Add the specified amount to the student's fee balance."""
        self.fee += amount

    def display\\\\\\\_details(self):
        """Print all stored student details, including the fee balance."""
        print("Name:", self.name)
        print("Roll No:", self.roll\\\\\\\_no)
        print("Hostel Status:", self.hostel\\\\\\\_status)
        print("Fee:", self.fee)


if \\\\\\\_\\\\\\\_name\\\\\\\_\\\\\\\_ == "\\\\\\\_\\\\\\\_main\\\\\\\_\\\\\\\_":
    student = sru\\\\\\\_student("Aarav", 101, "Yes")
    student.fee\\\\\\\_update(25000)
    student.display\\\\\\\_details()
```

### Comparison and critical evaluation

* Manual comments explain why each logical block exists and what each assignment stores.
* AI-generated docstrings provide a compact overview of the class and methods.
* AI comments can be redundant when they merely repeat obvious code, such as `self.name = name`.
* Neither version validates fee amounts; negative amounts could reduce the balance. Validation was not explicitly required by the assignment.
* AI may misunderstand business rules unless the prompt explains whether `fee\\\\\\\_update()` should add, replace, or calculate a fee.
* Comments should be updated whenever code changes; stale comments are worse than no comments.

### Expected output

```text
Name: Aarav
Roll No: 101
Hostel Status: Yes
Fee: 25000
```

## Task 3 — Module-level and function-level documentation

### Purpose

Build a calculator module with addition, subtraction, multiplication, and division functions, documented in NumPy style.

### Manually documented implementation

```python
"""Basic arithmetic calculator functions.

This module provides four functions for addition, subtraction,
multiplication, and division of two numeric operands.
"""


def add(a, b):
    """Add two numbers.

    Parameters
    ----------
    a : int or float
        First operand.
    b : int or float
        Second operand.

    Returns
    -------
    int or float
        The sum of a and b.
    """
    return a + b


def subtract(a, b):
    """Subtract the second number from the first.

    Parameters
    ----------
    a : int or float
        Number from which to subtract.
    b : int or float
        Number to subtract.

    Returns
    -------
    int or float
        The difference a - b.
    """
    return a - b


def multiply(a, b):
    """Multiply two numbers.

    Parameters
    ----------
    a : int or float
        First factor.
    b : int or float
        Second factor.

    Returns
    -------
    int or float
        The product of a and b.
    """
    return a \\\\\\\* b


def divide(a, b):
    """Divide the first number by the second.

    Parameters
    ----------
    a : int or float
        Numerator.
    b : int or float
        Denominator; must not be zero.

    Returns
    -------
    float
        The quotient a / b.

    Raises
    ------
    ZeroDivisionError
        If b is zero.
    """
    if b == 0:
        raise ZeroDivisionError("Cannot divide by zero.")
    return a / b


if \\\\\\\_\\\\\\\_name\\\\\\\_\\\\\\\_ == "\\\\\\\_\\\\\\\_main\\\\\\\_\\\\\\\_":
    print("Addition:", add(10, 5))
    print("Subtraction:", subtract(10, 5))
    print("Multiplication:", multiply(10, 5))
    print("Division:", divide(10, 5))
```

### AI-assisted documentation example

```python
"""Reusable arithmetic calculator module.

The module exposes basic arithmetic operations for two numeric inputs.
Each function documents its parameters, return value, and relevant
error conditions.
"""


def add(a, b):
    """Return the sum of two numeric values.

    Parameters
    ----------
    a : int or float
        First value.
    b : int or float
        Second value.

    Returns
    -------
    int or float
        The result of a + b.
    """
    return a + b


def subtract(a, b):
    """Return the result of subtracting b from a.

    Parameters
    ----------
    a : int or float
        Initial value.
    b : int or float
        Value to subtract.

    Returns
    -------
    int or float
        The result of a - b.
    """
    return a - b


def multiply(a, b):
    """Return the product of two numeric values.

    Parameters
    ----------
    a : int or float
        First factor.
    b : int or float
        Second factor.

    Returns
    -------
    int or float
        The result of a \\\\\\\* b.
    """
    return a \\\\\\\* b


def divide(a, b):
    """Return a divided by b.

    Parameters
    ----------
    a : int or float
        Numerator.
    b : int or float
        Denominator. Must be non-zero.

    Returns
    -------
    float
        The quotient.

    Raises
    ------
    ZeroDivisionError
        Raised when b equals zero.
    """
    if b == 0:
        raise ZeroDivisionError("Cannot divide by zero.")
    return a / b
```

### Comparison

* Both versions use NumPy-style sections: Parameters, Returns, and Raises where applicable.
* The manual module docstring describes the actual four operations and their purpose.
* The AI module docstring is slightly more general and explicitly states that errors are documented.
* Both division functions check for a zero denominator and raise `ZeroDivisionError`.
* The manual version gives a more detailed description of the denominator; the AI version is shorter.
* The two versions are functionally equivalent for ordinary numeric inputs.

### Expected output

```text
Addition: 15
Subtraction: 5
Multiplication: 50
Division: 2.0
```

## AI-assistance prompts used

These prompts can be pasted into GitHub Copilot, Cursor, or another coding assistant. The AI-generated examples above are representative drafts prepared for this report; they are not claimed to be captured outputs from a particular external AI tool.

### Prompt for Task 1

> Generate a Google Style docstring for the Python function `sum\\\\\\\_even\\\\\\\_odd(numbers)`. It accepts a list of integers and returns a tuple containing the sum of even numbers and the sum of odd numbers, in that order. Include Args, Returns, and one simple example. Do not change the function logic.

### Prompt for Task 2

> Add clear, accurate inline comments to this `sru\\\\\\\_student` class. Explain the purpose of the attributes, constructor, fee update, and display method. Avoid comments that merely repeat obvious Python syntax. Do not change the program behaviour.

### Prompt for Task 3

> Generate a module-level docstring and NumPy-style docstrings for add, subtract, multiply, and divide. Document parameter types, return values, and the ZeroDivisionError raised by division by zero. Do not alter the implementation.

## Conclusion

The lab demonstrates that documentation improves maintainability by explaining purpose, inputs, outputs, and exceptional cases. AI tools can speed up first drafts, but developers must verify accuracy, remove redundant comments, and keep documentation consistent with the implementation.

