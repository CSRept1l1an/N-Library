0. [[Python#About Python|About Python]]
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
## About Python
### History of Python
Python was created by Guido van Rossum and was first released in 1991. Van Rossum began working on Python in the late 1980s as a successor to the ABC language, aiming to create a language that was easy to read and write. Python was named after the British comedy series "Monty Python's Flying Circus," reflecting van Rossum's intention to make programming fun. Since its release, Python has grown in popularity and undergone numerous improvements, becoming one of the most widely used programming languages in the world.

### Evolution and Versions
Python has evolved significantly since its inception, with several major versions introducing new features and improvements:

- **Python 1.0 (1994):** The first official release, including [[DEV/Programming/Python#Variables and Data Types|basic data types]], [[DEV/Programming/Python#**Exception Handling**|error handling]], and [[DEV/Programming/Python#**Functions**|functions]].
- **Python 2.0 (2000):** Introduced new features like list comprehensions, garbage collection, and Unicode support. Python 2.x series continued until 2010 with Python 2.7, which became the last release of the 2.x series.
- **Python 3.0 (2008):** A major overhaul designed to rectify fundamental design flaws in the language. Python 3 introduced changes that were not backward compatible with Python 2, such as print function syntax, integer division, and a unified string representation. Python 3.x series continues to receive updates, with ongoing improvements and feature additions.
- **Python 3.6 (2016):** Introduced formatted string literals (f-strings), type hints, and improvements to asynchronous programming.
- **Python 3.7 (2018):** Added data classes, further improvements to asynchronous programming, and changes to the core language.
- **Python 3.8 (2019):** Introduced the walrus operator (assignment expressions) and positional-only arguments.
- **Python 3.9 (2020):** Added new syntax features, type hinting improvements, and performance enhancements.
- **Python 3.10 (2021):** Introduced pattern matching, parenthesized context managers, and various optimizations.

### Why Python?
Python has become a popular programming language for a wide range of applications due to several key factors:

1. **Readability and Simplicity:** Python's clean and readable syntax makes it easy to learn and understand, promoting good coding practices and reducing the likelihood of errors.

2. **Versatility:** Python is a general-purpose language used in various domains, including web development, data science, machine learning, automation, scientific computing, and more. Its versatility makes it a go-to language for many developers.

3. **Extensive Libraries and Frameworks:** Python boasts a rich ecosystem of libraries and frameworks that simplify development tasks. Popular libraries include NumPy and pandas for data manipulation, TensorFlow and PyTorch for machine learning, Django and Flask for web development, and many others.

4. **Community and Support:** Python has a large, active, and welcoming community that contributes to its development and provides extensive resources for learning and troubleshooting. The community-driven nature of Python ensures continuous improvement and support.

5. **Cross-Platform Compatibility:** Python runs on various platforms, including Windows, macOS, and Linux, making it highly portable and suitable for cross-platform development.

6. **Integration Capabilities:** Python can easily integrate with other languages and technologies, allowing developers to leverage existing codebases and tools. It is often used as a scripting language to automate tasks and glue together components of a larger system.

7. **Strong Support for Data Science and AI:** Python has become the language of choice for data science and artificial intelligence due to its powerful libraries and tools for data analysis, visualization, and machine learning. This has led to its widespread adoption in academia and industry.

8. **Robust Standard Library:** Python's standard library provides a wide range of modules and functions that facilitate various programming tasks, from file I/O and system operations to networking and internet protocols.

Python's combination of readability, versatility, extensive support, and strong community makes it an excellent choice for beginners and experienced developers alike, contributing to its enduring popularity and widespread use across different fields.

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

## Data Structures
### Data Structures

```python
my_list = [1, 2, 3, 4]                  # List
my_tuple = (1, 2, 3, 4)                 # Tuple
my_dict = {'name': 'Alice', 'age': 25}  # Dictionary
my_set = {1, 2, 3, 4}                   # Set
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

## File Handling
### Opening and Closing Files
```python
# Open a file
file = open('filename.txt', mode)

# Close a file
file.close()
```

**Modes:**
- `'r'` : Read (default)
- `'w'` : Write (truncates file)
- `'x'` : Create (fails if exists)
- `'a'` : Append
- `'b'` : Binary mode
- `'t'` : Text mode (default)
- `'+'` : Read and write

### Reading Files
```python
# Read the entire file
with open('filename.txt', 'r') as file:
    content = file.read()

# Read line by line
with open('filename.txt', 'r') as file:
    for line in file:
        print(line, end='')

# Read specific number of characters
with open('filename.txt', 'r') as file:
    content = file.read(100)  # reads first 100 characters

# Read all lines into a list
with open('filename.txt', 'r') as file:
    lines = file.readlines()
```

### Writing Files
```python
# Write to a file (overwrites)
with open('filename.txt', 'w') as file:
    file.write('Hello, World!')

# Append to a file
with open('filename.txt', 'a') as file:
    file.write('Hello, again!')

# Write a list of lines
lines = ['First line\n', 'Second line\n', 'Third line\n']
with open('filename.txt', 'w') as file:
    file.writelines(lines)
```

### Working with Binary Files
```python
# Read binary file
with open('filename.bin', 'rb') as file:
    content = file.read()

# Write binary file
with open('filename.bin', 'wb') as file:
    file.write(b'Binary data')
```

### Seeking and Telling
```python
with open('filename.txt', 'r') as file:
    file.seek(10)   # move to the 10th byte
    position = file.tell()  # get current position
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

## Exception Handling
### `try`-`except` Block

```python
try:
	# Code that might raise an exception
	pass 
except SomeException as e: 
	# Code that runs if exception occurs
	print(f"Error: {e}")
```

### `else` Block

```python
try:
    # Code that might raise an exception
    pass
except SomeException as e:
    # Code that runs if exception occurs
    print(f"Error: {e}")
else:
    # Code that runs if no exception occurs
    print("Success!")
```

### `finally` Block

```python
try:
    # Code that might raise an exception
    pass
except SomeException as e:
    # Code that runs if exception occurs
    print(f"Error: {e}")
finally:
    # Code that always runs
    print("Execution completed.")
```

## Object-Oriented Programming (OOP)
## Libraries and Frameworks
## My Projects in Python