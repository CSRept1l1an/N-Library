1. [[Python#Basic Syntax|Basic Syntax]] 
2. [[Python#Control Structures|Control Structures]]
3. [[Python#Functions|Functions]]
4. [[Python#Data Structures|Data Structures]]
5. [[Python#Module and Packages|Module and Packages]]
6. [[Python#File Handling|File Handling]]
7. [[Python#Exception Handling|Exception Handling]]
8. [[Python#Object-Oriented Programming (OOP)|Object-Oriented Programming (OOP)]]
9. [[Python#Libraries and Frameworks|Libraries and Frameworks]]
10. [[Python#My Projects in Python|My Projects in Python]]
## Basic Syntax
### Variables and Data Types
#### Variables

```python
x = 5             # Integer
y = 3.14          # Float
name = "Alice"    # String
is_valid = True   # Boolean
```

#### Numeric Types

```python
num_int = 10 # Integer 
num_float = 3.14 # Float 
num_complex = 1 + 2j # Complex number
```

#### Strings

```python
name = "Alice"
message = 'Hello, World!'

# String Operations
concatenation = "Hello" + " " + "World"   # Concatenation
substring = message[7:]                   # Slicing
formatted_string = f"My name is {name}"   # Formatted strings (f-strings)
string_length = len(name)                 # Length of a string

# String Methods
uppercase = message.upper()        # Convert to uppercase
lowercase = message.lower()        # Convert to lowercase
replace_str = message.replace('Hello', 'Hi')  # Replace a substring

# String Indexing and Slicing
first_char = message[0]            # Accessing first character
last_char = message[-1]            # Accessing last character
substring = message[7:12]          # Slicing a portion of the string
```

#### Type Conversion 
```python
int_to_float = float(10) # Convert integer to float 
float_to_int = int(3.14) # Convert float to integer 
int_to_string = str(10) # Convert integer to string 
string_to_int = int("10") # Convert string to integer
```
### Operators
#### Arithmetic Operators

```python
a = 10
b = 3
print(a + b)    # Addition   -> 13
print(a - b)    # Subtraction -> 7
print(a * b)    # Multiplication -> 30
print(a / b)    # Division -> 3.3333333333333335
print(a // b)   # Integer Division -> 3
print(a % b)    # Modulus -> 1
print(a ** b)   # Exponentiation -> 1000
```

#### Comparison Operators

```python
a = 10
b = 3
print(a > b)    # Greater than         -> True
print(a < b)    # Less than            -> False
print(a == b)   # Equal to             -> False
print(a != b)   # Not equal to         -> True
print(a >= b)   # Greater than or equal to -> True
print(a <= b)   # Less than or equal to -> False
```

#### Logical operators

```python
p = True 
q = False 
print(p and q) # Logical AND -> False 
print(p or q) # Logical OR -> True 
print(not p) # Logical NOT -> False
```

#### Assignment Operators

```python
x = 5
x += 3    # Equivalent to x = x + 3
print(x)  # Output: 8

y = 10
y *= 2    # Equivalent to y = y * 2
print(y)  # Output: 20
```

#### Identity Operators

```python
list1 = [1, 2, 3]
list2 = [1, 2, 3]
print(list1 is list2)   # False (different objects)
print(list1 is not list2)  # True

x = 5
y = 5
print(x is y)           # True (same object)
```

#### Membership Operators

```python
my_list = [1, 2, 3, 4]
print(1 in my_list)     # True
print(5 not in my_list) # True
```

### Comments

```python
# This is a single-line comment

"""
This is a
multi-line comment
or docstring
"""
```

## Control Structures
### Conditional Statements

```python
if x > 0:
    print("Positive")
elif x == 0:
    print("Zero")
else:
    print("Negative")
```

### Loops

```python
#For Loop
for i in range(5):
    print(i)

#While Loop
count = 0
while count < 5:
    print(count)
    count += 1

#While True Loop
count = 0
while True:
    print(count)
    count += 1
    if count >= 5:
        break

```

### List Comprehension

```python
squares = [x**2 for x in range(10)]
print(squares) # Output [0, 1, 4, 9, 16, 25, 36, 49, 64, 81]
```

## Functions
### Function Basics

```python
def greet(name):
    return f"Hello, {name}!"

print(greet("Alice"))  # Output: Hello, Alice!
```

### Functional Arguments

```python
def greet_with_message(name, message="Hello"):
    return f"{message}, {name}!"

print(greet_with_message("Bob"))  # Output: Hello, Bob!
print(greet_with_message("Charlie", "Hi"))  # Output: Hi, Charlie!
```

### Variable-Length Arguments

```python
# `*args` for variable positional arguments
def print_args(*args):
    for arg in args:
        print(arg)

print_args(1, 2, 3)  # Output: 1 2 3

# `**kwargs` for variable keyword arguments
def print_kwargs(**kwargs):
    for key, value in kwargs.items():
        print(f"{key}: {value}")

print_kwargs(name="Alice", age=30)  # Output: name: Alice, age: 30
```

### Lambda Functions

```python
# Anonymous functions using `lambda`
add = lambda a, b: a + b
print(add(2, 3))  # Output: 5
```

### Returning Values

```python
def square_and_cube(x):
    return x**2, x**3

square, cube = square_and_cube(3)
print(f"Square: {square}, Cube: {cube}")  # Output: Square: 9, Cube: 27
```

### Default Parameter Values

```python
def greet_with_default(name="Guest"):
    return f"Hello, {name}!"

print(greet_with_default())  # Output: Hello, Guest!
print(greet_with_default("Bob"))  # Output: Hello, Bob!
```

### Recursion

```python
# Providing hints about function parameters and return types
def factorial(n):
    return 1 if n == 0 else n * factorial(n-1)

print(factorial(5))  # Output: 120 (5! = 5 * 4 * 3 * 2 * 1)
```

### Function Annotations

```python
# Providing hints about function parameters and return types
def add_numbers(a: int, b: int) -> int:
    return a + b

print(add_numbers(3, 4))  # Output: 7
```
## Excepting Handling

```python
try:
    result = 10 / 0
except ZeroDivisionError:
    print("Cannot divide by zero")
except Exception as e:
    print(f"An error occurred: {e}")
finally:
    print("This will always execute")
```

## File Handling

```python
# Reading from a file
with open('file.txt', 'r') as file:
    content = file.read()

# Writing to a file
with open('file.txt', 'w') as file:
    file.write("Hello, World!")
```

## Modules and Packages

```python
# Importing a Module
import math
print(math.sqrt(16))

# Importing specific function from a module
from math import sqrt
print(sqrt(16))

# Aliasing a Module
import numpy as np
print(np.array([1, 2, 3]))
```

## Classes and Objects

```python

# Defining a Class
class Dog:
    def __init__(self, name, age):
        self.name = name
        self.age = age

    def bark(self):
        return f"{self.name} says woof!"

# Creating an Object
my_dog = Dog("Buddy", 3)
print(my_dog.bark())
```

## Data Structures
### Data Structures

```python
my_list = [1, 2, 3, 4]                  # List
my_tuple = (1, 2, 3, 4)                 # Tuple
my_dict = {'name': 'Alice', 'age': 25}  # Dictionary
my_set = {1, 2, 3, 4}                   # Set
```

## Module and Packages
## File Handling
## Exception Handling
## Object-Oriented Programming (OOP)
## Libraries and Frameworks
## My Projects in Python