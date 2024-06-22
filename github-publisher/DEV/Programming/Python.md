1. [Basic Syntax](Python.md#basic-syntax)   
2. [Control Structures](Python.md#control-structures)  
3. [Functions](Python.md#functions)  
4. [Data Structures](Python.md#data-structures)  
5. [Module and Packages](Python.md#module-and-packages)  
6. [File Handling](Python.md#file-handling)  
7. [Exception Handling](Python.md#exception-handling)  
8. [Object-Oriented Programming (OOP)](Python.md#object-oriented-programming-oop)  
9. [Libraries and Frameworks](Python.md#libraries-and-frameworks)  
10. [My Projects in Python](Python.md#my-projects-in-python)  
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
  
### Data Structures  
  
```python  
my_list = [1, 2, 3, 4]                  # List  
my_tuple = (1, 2, 3, 4)                 # Tuple  
my_dict = {'name': 'Alice', 'age': 25}  # Dictionary  
my_set = {1, 2, 3, 4}                   # Set  
```  
  
# Control Structures  
## Conditional Statements  
  
```python  
if x > 0:  
    print("Positive")  
elif x == 0:  
    print("Zero")  
else:  
    print("Negative")  
```  
  
## Loops  
  
```python  
[[For]] Loop  
for i in range(5):  
    print(i)  
  
[[While]] Loop  
count = 0  
while count < 5:  
    print(count)  
    count += 1  
  
[[While]] True Loop  
count = 0  
while True:  
    print(count)  
    count += 1  
    if count >= 5:  
        break  
  
```  
  
## List Comprehension  
  
```python  
squares = [x**2 for x in range(10)]  
```  
  
# Functions  
  
```python  
# Function Definition  
def greet(name):  
    return f"Hello, {name}!"  
  
# Calling a Function  
print(greet("Alice"))  
  
# Lambda Function  
add = lambda a, b: a + b  
print(add(2, 3))  
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
  
<<<<<<< HEAD  
# Data Structures  
# Module and Packages  
# File Handling  
# Exception Handling  
# Object-Oriented Programming (OOP)  
## Libraries and Frameworks  
## My Projects in Python  
## Data Structures  
## Module and Packages  
## File Handling  
## Exception Handling  
## Object-Oriented Programming (OOP)  
## Libraries and Frameworks  
## My Projects in Python  
  
