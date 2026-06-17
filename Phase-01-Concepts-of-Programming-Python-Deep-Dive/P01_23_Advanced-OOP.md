## What Is This?
Advanced Object-Oriented Programming (OOP) refers to a set of techniques used to create complex, reusable, and maintainable software systems by defining relationships between objects and their interactions. Think of it like a city's infrastructure, where buildings, roads, and services are designed to work together seamlessly, allowing the city to function efficiently. Just as a city's infrastructure is built using a set of rules and guidelines, advanced OOP provides a set of principles and techniques to build robust and scalable software systems.

## How It Works Internally
### Introduction to Dunder Methods
Dunder methods, also known as magic methods, are special methods in Python classes that are surrounded by double underscores (also called "dunders") on either side of the method name. These methods are used to define the behavior of an object when it is used in a specific context, such as when it is initialized, compared, or converted to a string.

### Layer 1: Basic Dunder Methods
Let's start with some basic dunder methods:
```text
# Initialize an object
__init__

# Return a string representation of an object
__str__

# Return a formal string representation of an object
__repr__

# Delete an object
__del__
```
These methods are the foundation of object-oriented programming in Python and are used to define the basic behavior of an object.

### Layer 2: Arithmetic Dunder Methods
Arithmetic dunder methods are used to define the behavior of an object when it is used in arithmetic operations:
```text
# Add two objects
__add__

# Subtract two objects
__sub__

# Multiply two objects
__mul__

# Divide two objects
__truediv__

# Floor divide two objects
__floordiv__

# Modulus of two objects
__mod__

# Power of two objects
__pow__
```
These methods allow you to define how objects interact with each other in arithmetic operations.

### Layer 3: Comparison Dunder Methods
Comparison dunder methods are used to define the behavior of an object when it is compared to another object:
```text
# Equal to
__eq__

# Not equal to
__ne__

# Less than
__lt__

# Less than or equal to
__le__

# Greater than
__gt__

# Greater than or equal to
__ge__
```
These methods allow you to define how objects are compared to each other.

### Layer 4: Container Dunder Methods
Container dunder methods are used to define the behavior of an object when it is used as a container:
```text
# Get the length of a container
__len__

# Get an item from a container
__getitem__

# Set an item in a container
__setitem__

# Delete an item from a container
__delitem__

# Check if an item is in a container
__contains__

# Iterate over a container
__iter__

# Get the next item from a container
__next__
```
These methods allow you to define how objects interact with each other as containers.

### Callable Dunder Method
The `__call__` method is used to make an object callable like a function:
```text
# Make an object callable
__call__
```
This method allows you to define how an object is called like a function.

### Context Manager Dunder Methods
Context manager dunder methods are used to define the behavior of an object when it is used as a context manager:
```text
# Enter a context
__enter__

# Exit a context
__exit__
```
These methods allow you to define how objects interact with each other as context managers.

### Decorators
Decorators are a way to wrap a function to extend its behavior:
```text
# Define a decorator
def decorator(func):
    # Extend the behavior of the function
    def wrapper():
        # Code to extend the behavior
        func()
    return wrapper
```
Decorators allow you to define how functions interact with each other.

### Function Decorators
Function decorators are used to decorate functions:
```text
# Define a function decorator
def function_decorator(func):
    # Extend the behavior of the function
    def wrapper():
        # Code to extend the behavior
        func()
    return wrapper
```
Function decorators allow you to define how functions interact with each other.

### Decorator with Arguments
Decorators can also take arguments:
```text
# Define a decorator with arguments
def decorator_with_args(arg):
    # Define a decorator
    def decorator(func):
        # Extend the behavior of the function
        def wrapper():
            # Code to extend the behavior
            func()
        return wrapper
    return decorator
```
Decorators with arguments allow you to define how functions interact with each other with additional context.

### Static Method
A static method is a method that belongs to a class rather than an instance:
```text
# Define a static method
@staticmethod
def static_method():
    # Code for the static method
    pass
```
Static methods allow you to define utility functions that belong to a class.

### Class Method
A class method is a method that is called on a class rather than an instance:
```text
# Define a class method
@classmethod
def class_method(cls):
    # Code for the class method
    pass
```
Class methods allow you to define alternative constructors and other class-level functionality.

### Property
A property is a way to implement getters and setters for attributes:
```text
# Define a property
@property
def attr(self):
    # Code to get the attribute
    pass
```
Properties allow you to define how attributes are accessed and modified.

### Functools Wraps
Functools wraps is a decorator that preserves the metadata of a function:
```text
# Import functools wraps
from functools import wraps

# Define a decorator
def decorator(func):
    # Preserve the metadata of the function
    @wraps(func)
    def wrapper():
        # Code to extend the behavior
        func()
    return wrapper
```
Functools wraps allows you to define how functions interact with each other while preserving their metadata.

### Chaining Decorators
Decorators can be chained together:
```text
# Define two decorators
def decorator1(func):
    # Code to extend the behavior
    def wrapper():
        func()
    return wrapper

def decorator2(func):
    # Code to extend the behavior
    def wrapper():
        func()
    return wrapper

# Chain the decorators
@decorator1
@decorator2
def func():
    # Code for the function
    pass
```
Chaining decorators allows you to define how functions interact with each other in a layered way.

### Class-Based Decorators
Class-based decorators are a way to define decorators using classes:
```text
# Define a class-based decorator
class Decorator:
    def __init__(self, func):
        self.func = func

    def __call__(self, *args, **kwargs):
        # Code to extend the behavior
        self.func(*args, **kwargs)
```
Class-based decorators allow you to define how functions interact with each other using classes.

### Slots
Slots are a way to restrict the attributes of an object:
```text
# Define a class with slots
class Class:
    __slots__ = ('attr1', 'attr2')

    def __init__(self, attr1, attr2):
        self.attr1 = attr1
        self.attr2 = attr2
```
Slots allow you to define how objects are structured and what attributes they can have.

### Dataclass
Dataclass is a decorator that automatically generates special methods for a class:
```text
# Import dataclass
from dataclasses import dataclass

# Define a dataclass
@dataclass
class Class:
    attr1: str
    attr2: str
```
Dataclass allows you to define how objects are structured and what attributes they can have, while automatically generating special methods.

### Named Tuples
Named tuples are a way to define lightweight classes:
```text
# Import namedtuple
from collections import namedtuple

# Define a named tuple
Class = namedtuple('Class', ('attr1', 'attr2'))
```
Named tuples allow you to define how objects are structured and what attributes they can have, in a lightweight way.

### Dict
The `__dict__` attribute is a dictionary that contains the attributes of an object:
```text
# Define a class
class Class:
    def __init__(self, attr1, attr2):
        self.attr1 = attr1
        self.attr2 = attr2

# Access the __dict__ attribute
obj = Class('value1', 'value2')
print(obj.__dict__)
```
The `__dict__` attribute allows you to access and modify the attributes of an object.

### Mixins
Mixins are classes that provide a set of methods that can be used by other classes:
```text
# Define a mixin
class Mixin:
    def method(self):
        # Code for the method
        pass

# Define a class that uses the mixin
class Class(Mixin):
    pass
```
Mixins allow you to define how classes interact with each other and share functionality.

### Composition Over Inheritance
Composition over inheritance is a principle that suggests using composition instead of inheritance to define the relationships between classes:
```text
# Define a class that uses composition
class Class:
    def __init__(self):
        self.attr = OtherClass()
```
Composition over inheritance allows you to define how classes interact with each other in a flexible and maintainable way.

CORE INSIGHT: Advanced OOP is all about defining the relationships between objects and their interactions, using a set of techniques such as dunder methods, decorators, and composition over inheritance. This matters to you because it allows you to create complex, reusable, and maintainable software systems that can solve real-world problems.

## Syntax and Structure
```python
# Define a class with dunder methods
class Class:
    def __init__(self, attr1, attr2):
        # Initialize the attributes
        self.attr1 = attr1
        self.attr2 = attr2

    def __str__(self):
        # Return a string representation of the object
        return f'Class({self.attr1}, {self.attr2})'

    def __repr__(self):
        # Return a formal string representation of the object
        return f'Class({self.attr1}, {self.attr2})'

    def __add__(self, other):
        # Define the behavior of the + operator
        return Class(self.attr1 + other.attr1, self.attr2 + other.attr2)

# Create an instance of the class
obj = Class('value1', 'value2')

# Use the dunder methods
print(obj)  # Output: Class(value1, value2)
print(repr(obj))  # Output: Class(value1, value2)
print(obj + Class('value3', 'value4'))  # Output: Class(value1value3, value2value4)
```
This example demonstrates how to define a class with dunder methods and use them to define the behavior of an object.

## Practical Example
```python
# Define a class that represents a point in 2D space
class Point:
    def __init__(self, x, y):
        # Initialize the attributes
        self.x = x
        self.y = y

    def __str__(self):
        # Return a string representation of the object
        return f'Point({self.x}, {self.y})'

    def __repr__(self):
        # Return a formal string representation of the object
        return f'Point({self.x}, {self.y})'

    def __add__(self, other):
        # Define the behavior of the + operator
        return Point(self.x + other.x, self.y + other.y)

    def __sub__(self, other):
        # Define the behavior of the - operator
        return Point(self.x - other.x, self.y - other.y)

    def __mul__(self, scalar):
        # Define the behavior of the * operator
        return Point(self.x * scalar, self.y * scalar)

    def __truediv__(self, scalar):
        # Define the behavior of the / operator
        return Point(self.x / scalar, self.y / scalar)

# Create an instance of the class
point = Point(1, 2)

# Use the dunder methods
print(point)  # Output: Point(1, 2)
print(repr(point))  # Output: Point(1, 2)
print(point + Point(3, 4))  # Output: Point(4, 6)
print(point - Point(3, 4))  # Output: Point(-2, -2)
print(point * 2)  # Output: Point(2, 4)
print(point / 2)  # Output: Point(0.5, 1.0)
```
This example demonstrates how to define a class that represents a point in 2D space and use dunder methods to define its behavior.

## How This Connects to the Project
Before learning about advanced OOP, the E-Commerce Store Simulator project would have been incomplete, with no way to define complex relationships between objects. Now, with the knowledge of advanced OOP, the project can be completed, with classes that represent products, orders, and customers, and dunder methods that define their behavior. The exact file and function name where this concept lives in the project is `product.py` and `Order` class. One real company that uses this exact pattern is Amazon, which uses object-oriented programming to define the relationships between products, orders, and customers.

## Common Mistakes Beginners Make
**Wrong idea:** Beginners often think that decorators are only used for logging and authentication. 
**Correct idea:** Decorators can be used for a wide range of purposes, including caching, rate limiting, and error handling. 
A common mistake is to use inheritance instead of composition, which can lead to tight coupling and make the code harder to maintain. 
Another mistake is to not use dunder methods, which can make the code less readable and less maintainable. 
A mistake that seems optional but is critical at scale is not using slots, which can lead to memory issues and slow performance. 
A missed configuration or flag is not using functools wraps, which can lead to lost