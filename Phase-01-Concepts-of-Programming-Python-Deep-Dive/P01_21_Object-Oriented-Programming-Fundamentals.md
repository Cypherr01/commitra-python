## What Is This?
Object-Oriented Programming (OOP) is a programming paradigm that revolves around the concept of objects and classes, which are used to represent and manipulate data. Think of it like a restaurant: you can have multiple waiters (objects) who all follow the same set of rules (class) to take orders and serve food. Just as each waiter has their own name, uniform, and way of taking orders, objects in OOP have their own properties (like name and uniform) and behaviors (like taking orders).

## How It Works Internally
### Procedural vs OOP
OOP exists because procedural programming, which focuses on procedures or functions that perform specific tasks, can become cumbersome and hard to manage as programs grow in size. Imagine a big library with millions of books - procedural programming would be like having one huge catalog with all the information, while OOP would be like having many smaller catalogs, each for a specific type of book, making it easier to find what you need.

### Real-world Modeling
In the real world, objects have state (attributes) and behavior (methods). For example, a car has attributes like color, model, and year, and behaviors like accelerating and braking. In OOP, we can represent this using classes and objects.

### Class Keyword
The `class` keyword is used to define a blueprint for objects. It's like a recipe for making a cake - the recipe is the class, and the actual cake you make is the object.

### Constructor
The `__init__` method, also known as the constructor, is called when an object is created. It's like setting up a new cake recipe - you need to put in the ingredients and mix them together before you can bake the cake.

### Self
The `self` keyword is a reference to the current instance of the class. It's like a name tag that says "I'm this specific cake".

### Instance Attributes
Instance attributes belong to each object and are used to store data that is unique to that object. For example, each cake has its own ingredients and decorations.

### Class Attributes
Class attributes are shared across all instances of a class. For example, all cakes have the same recipe, but each cake can have different ingredients and decorations.

### Instance Methods
Instance methods take `self` as a parameter and are used to perform actions on an object. For example, you can have a method to bake the cake or decorate it.

### String Representation
The `__str__` method is used to provide a human-readable string representation of an object. It's like writing a description of the cake on a card.

### Representation
The `__repr__` method is used to provide an unambiguous string representation of an object. It's like writing a detailed recipe for the cake.

### Object Creation
Objects are created using the class name followed by parentheses. For example, `cake = Cake()` creates a new cake object.

### Object Lifecycle
The object lifecycle consists of creation, use, and garbage collection. It's like making a cake, eating it, and then throwing away the leftovers.

### Deleting Objects
The `del` keyword is used to remove a reference to an object. It's like throwing away the cake - if no one has a reference to it, it will be garbage collected.

```text
# Pseudocode for object creation and deletion
CREATE object
USE object
DELETE object
```

### LAYER 1: Minimum Viable Version
Imagine a simple program that creates a cake object and prints its ingredients.

```text
# Pseudocode for minimum viable version
CLASS Cake
  INIT ingredients
  PRINT ingredients
CREATE cake
PRINT cake.ingredients
```

### LAYER 2: Why the Simple Version Breaks
The simple version breaks when we try to create multiple cake objects with different ingredients.

```text
# Pseudocode for why the simple version breaks
CREATE cake1
CREATE cake2
PRINT cake1.ingredients  # prints cake2's ingredients
```

### LAYER 3: Production Version
The production version uses instance attributes to store the ingredients for each cake object.

```text
# Pseudocode for production version
CLASS Cake
  INIT ingredients
  INSTANCE ATTRIBUTES ingredients
CREATE cake1
CREATE cake2
PRINT cake1.ingredients  # prints cake1's ingredients
```

### LAYER 4: Edge Cases
One edge case is when we try to create a cake object with no ingredients.

```text
# Pseudocode for edge case
CREATE cake
PRINT cake.ingredients  # raises an error
```

Another edge case is when we try to delete a cake object that is still being used.

```text
# Pseudocode for edge case
CREATE cake
USE cake
DELETE cake  # raises an error
```

CORE INSIGHT: Objects have state and behavior, and classes are used to define the blueprint for objects.

## Syntax and Structure
```python
class Cake:
  def __init__(self, ingredients):
    # Initialize the cake object with ingredients
    self.ingredients = ingredients

  def __str__(self):
    # Return a human-readable string representation of the cake
    return f"Cake with {self.ingredients}"

  def bake(self):
    # Bake the cake
    print("Baking the cake")

# Create a cake object
cake = Cake(["flour", "sugar", "eggs"])

# Print the cake's ingredients
print(cake.ingredients)

# Bake the cake
cake.bake()
```

## Practical Example
```python
class Product:
  def __init__(self, name, price):
    # Initialize the product object with name and price
    self.name = name
    self.price = price

  def __str__(self):
    # Return a human-readable string representation of the product
    return f"{self.name} - ${self.price}"

# Create a product object
product = Product("Cake", 10.99)

# Print the product's name and price
print(product)
```

## How This Connects to the Project
Before using OOP, the E-Commerce Store Simulator project would have had a hard time managing multiple products, customers, and orders. With OOP, we can create classes for each of these entities and use objects to represent individual instances. For example, we can have a `Product` class with attributes like `name` and `price`, and methods like `add_to_cart`. The `Customer` class can have attributes like `name` and `address`, and methods like `place_order`. The `Order` class can have attributes like `products` and `total_price`, and methods like `calculate_total`. This makes the project more organized and easier to manage.

## Common Mistakes Beginners Make
**Most common mistake**: Not using `self` when accessing instance attributes. For example, `ingredients` instead of `self.ingredients`.
Wrong idea: You can access instance attributes without using `self`.
Correct idea: You must use `self` to access instance attributes.
**Looks right but is silently wrong**: Using `class` attributes instead of instance attributes. For example, `Cake.ingredients` instead of `self.ingredients`.
**Seems optional but critical at scale**: Not using `__str__` and `__repr__` methods to provide a human-readable string representation of objects.
**Missed config or flag**: Not using the `__init__` method to initialize objects.
**Interview question**: How do you implement inheritance in Python?

## Verification Task 1
Debug the following code:
```python
class Cake:
  def __init__(self, ingredients):
    ingredients = ingredients

  def __str__(self):
    return f"Cake with {self.ingredients}"

cake = Cake(["flour", "sugar", "eggs"])
print(cake)
```
## Solution 1
The problem is that the `ingredients` attribute is not being assigned to the object. To fix this, we need to use `self.ingredients` instead of `ingredients` in the `__init__` method.
```python
class Cake:
  def __init__(self, ingredients):
    self.ingredients = ingredients

  def __str__(self):
    return f"Cake with {self.ingredients}"

cake = Cake(["flour", "sugar", "eggs"])
print(cake)
```

## Verification Task 2
Design a `Product` class that has attributes like `name` and `price`, and methods like `add_to_cart`. Should we use a list or a dictionary to store the products in the cart?
## Solution 2
We should use a dictionary to store the products in the cart, where the key is the product name and the value is the quantity. This allows us to easily look up and update the quantity of each product.

## Verification Task 3
Code review: The following code has a bug:
```python
class Customer:
  def __init__(self, name, address):
    self.name = name
    self.address = address

  def place_order(self, products):
    for product in products:
      print(f"Ordering {product}")

customer = Customer("John", "123 Main St")
customer.place_order(["Cake", "Ice Cream"])
```
Find and fix the bug.
## Solution 3
The bug is that the `place_order` method is not checking if the customer has enough money to place the order. To fix this, we need to add a `balance` attribute to the `Customer` class and check if the balance is sufficient before placing the order.
```python
class Customer:
  def __init__(self, name, address, balance):
    self.name = name
    self.address = address
    self.balance = balance

  def place_order(self, products):
    total_price = 0
    for product in products:
      total_price += 10.99  # assume each product costs $10.99
    if self.balance >= total_price:
      for product in products:
        print(f"Ordering {product}")
      self.balance -= total_price
    else:
      print("Insufficient balance")

customer = Customer("John", "123 Main St", 100)
customer.place_order(["Cake", "Ice Cream"])
```

## What Comes Next
The next topic is Advanced OOP, which builds on the fundamentals of OOP covered in this topic. Advanced OOP will cover more complex concepts like inheritance, polymorphism, and encapsulation, which are essential for building large-scale applications. The concept of classes and objects covered in this topic will be directly used in Advanced OOP to create more complex and sophisticated programs.

## Reference Summary
Object-Oriented Programming (OOP) is a programming paradigm that revolves around the concept of objects and classes. Classes are used to define the blueprint for objects, which have state (attributes) and behavior (methods). The `class` keyword is used to define a class, and the `__init__` method is used to initialize objects. The `self` keyword is used to access instance attributes, and the `__str__` and `__repr__` methods are used to provide a human-readable string representation of objects. OOP is essential for building large-scale applications, and its concepts are used in many areas of programming, including web development, game development, and artificial intelligence. The E-Commerce Store Simulator project uses OOP to create classes for products, customers, and orders, making it more organized and easier to manage. By mastering OOP, developers can create more complex and sophisticated programs that are efficient, scalable, and maintainable. This matters to you because it will help you build a strong foundation in programming and enable you to create more complex and sophisticated programs.