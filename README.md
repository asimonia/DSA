# Python Cheat Sheet

A Cheat Sheet 📜 to **revise** Python syntax in **less time**. Particularly useful for solving Data Structure and Algorithmic problems or a quick overview before an interview.

# Table of Contents
- [Basics](#basics)
- [Data Structures](#data-structures)
  - [Lists](#lists)
  - [Dictionary](#dictionary)
  - [Counter](#counter)
  - [Deque](#deque)
  - [Heapq](#heapq)
  - [Sets](#sets)
  - [Tuples](#tuples)
  - [Strings](#strings)
- [Built-in Functions](#built-in-functions)
- [Advanced Topics](#advanced-topics)
- [Tips & Gotchas](#tips--gotchas)

# Basics

## Data Types
![Python Data Types](https://user-images.githubusercontent.com/59110866/173563442-1a6fa3d2-b569-4eb0-99cc-9b91cc8be1eb.png)

## Keywords
```python
# Logical
and	                           
not	                           
or	                          
in	                          

# Looping
for
while
break
continue

# Boolean and Null
False	                        
True	                        
None	                        
```


# Data Structures

## Lists
Time Complexities:
![List Operations](https://user-images.githubusercontent.com/47276307/172330098-1c5f0a6e-7f80-4f4f-9be6-1d734e2c70cd.jpg)

```python
nums = [1,2,3]

# Common Operations
nums.append(1)     # Add to end
nums.pop(index=-1) # Remove & return last element by default
nums.insert(0,10)  # Add 10 from left (at index 0 which is start)
nums.index(1)      # Find index


# List Slicing
nums[start:stop:step]  # Generic slice syntax
nums[-1]    # Last item
nums[::-1]  # Reverse list
nums[1:]    # Everything after index 1
nums[:3]    # First three elements
nums[:]     # List copy
```

## Dictionary
Time Complexities:
![Dictionary Operations](https://user-images.githubusercontent.com/47276307/172330107-e68e3228-1c76-4bfb-bb38-04d18f94d5b9.jpg)

```python
d = {'a':1, 'b':2}

# Essential Operations
d.get('key', default)     # Safe access with default
d.setdefault('key', 0)    # Set if missing
d.items()                 # Key-value pairs
d.keys()                  # Just keys
d.values()               # Just values
d.pop(key)              # Remove and return value

# Advanced Usage
from collections import defaultdict
d = defaultdict(list)     # Auto-initialize missing keys
d = defaultdict(int)      # Useful for counting
```

## Counter
```python
from collections import Counter

# Initialize
c = Counter(['a','a','b'])    # From iterable
c = Counter("hello")          # From string

# Operations
c.most_common(2)      # Top 2 frequent elements
c['a'] += 1           # Increment count
c.update("more")      # Add counts from iterable
c.total()             # Sum of all counts
```

## Deque
Time Complexities:
![Deque Operations](https://user-images.githubusercontent.com/47276307/172330115-78500420-3276-4e45-8ce3-fd668b7eb14e.jpg)

```python
from collections import deque

# Perfect for BFS - O(1) operations on both ends
d = deque()
d.append(1)          # Add right
d.appendleft(2)      # Add left
d.pop()              # Remove right
d.popleft()          # Remove left
d.extend([1,2,3])    # Extend right
d.extendleft([1,2,3])# Extend left
d.rotate(n)          # Rotate n steps right (negative for left)
```

## Heapq

```python
import heapq

# MinHeap Operations - All O(log n) except heapify
nums = [3,1,4,1,5]
heapq.heapify(nums)          # Convert to heap in-place: O(n)
heapq.heappush(nums, 2)      # Add element: O(log n)
smallest = heapq.heappop(nums)  # Remove smallest: O(log n)

# MaxHeap Trick: Multiply by -1
nums = [-x for x in nums]    # Convert to maxheap: O(n)
heapq.heapify(nums)          # O(n)
largest = -heapq.heappop(nums)  # Get largest: O(log n)

# Advanced Operations
k_largest = heapq.nlargest(k, nums)    # O(n * log k)
k_smallest = heapq.nsmallest(k, nums)  # O(n * log k)

# Custom Priority Queue
heap = []
heapq.heappush(heap, (priority, item))  # Sort by priority
```

## Sets

```python
s = {1,2,3}

# Common Operations
s.add(4)             # Add element
s.remove(4)          # Remove (raises error if missing)
```

## Tuples
```python
# Tuples are immutable lists
t = (1, 2, 3, 1)

# Essential Operations
t.count(1)      # Count occurrences of value
t.index(2)      # Find first index of value

# Useful Patterns
x, y = (1, 2)   # Tuple unpacking
coords = [(1,2), (3,4)]  # Tuple in collections
```

## Strings
```python
s = "hello world"

# Essential Methods
s.split()            # Split on whitespace
s.split(',')         # Split on comma and return a list
s.strip()            # Remove leading/trailing whitespace
s.lower()            # Convert to lowercase
s.upper()            # Convert to uppercase
s.isalnum()          # Check if alphanumeric
s.isalpha()          # Check if alphabetic
s.isdigit()          # Check if all digits
s.find('sub')        # Index of substring (-1 if not found)
s.count('sub')       # Count occurrences
s.replace('old', 'new')  # Replace all occurrences

# ASCII Conversion
ord('a')             # Char to ASCII (97)
chr(97)              # ASCII to char ('a')

# Join Lists
''.join(['a','b'])   # Concatenate list elements
```

# Built-in Functions

```python
# Iteration Helpers
enumerate(lst)        # Index + value pairs
zip(lst1, lst2)      # Parallel iteration

# Type Conversion
int('42')            # String to int
str(42)              # Int to string
float('inf')         # + inf
float('-inf')        # - inf
list('abc')          # String to list
''.join(['a','b'])   # List to string
set([1,2,2])         # List to set

# Math
abs(-5)              # Absolute value
pow(2, 3)            # Power
round(3.14159, 2)    # Round to decimals

# Common stats
max(itr)	           # largest item in an iterable
min(itr)	           # smallest item in an iterable
sum(itr)	           # sum of elements in an iterable
len(itr)             # number of elements
```

# Advanced Topics

## Math Module Essentials
```python
import math

# Constants
math.pi       # 3.141592653589793
math.e        # 2.718281828459045

# Common Functions
math.ceil(2.3)        # 3 - Smallest integer greater than x
math.floor(2.3)       # 2 - Largest integer less than x
math.gcd(a, b)        # Greatest common divisor
math.log(x, base)     # Logarithm with specified base
math.sqrt(x)          # Square root
math.pow(x, y)        # x^y (prefer x ** y for integers)

```

## Important Python Integer Operations
```python

# Negative number handling
x = -3
y = 2
print(x // y)        # -2 (floor division)
print(int(x/y))      # -1 (preferred for negative numbers)
print(x % y)         # 1 (Python's modulo with negative numbers)
```

# Tips & Gotchas

1. Integer Division:
```python
# Use int() for consistent negative number handling
print(-3//2)        # Returns -2
print(int(-3/2))    # Returns -1 (usually desired)
```

2. Default Dictionaries:
```python
# Prefer defaultdict for frequency counting
from collections import defaultdict
freq = defaultdict(int)
for x in lst:
    freq[x] += 1    # No KeyError if x is new
```

3. Heap Priority:
```python
# For custom priority in heapq, use tuples
heap = []
heapq.heappush(heap, (priority, item))
```

4. List Comprehension:
```python
# Often clearer than map/filter
squares = [x*x for x in range(10) if x % 2 == 0]
```

5. String Building:
```python
# Use join() instead of += for strings
chars = ['a', 'b', 'c']
word = ''.join(chars)  # More efficient
```

6. Using Sets for Efficiency:
```python
# O(1) lookup for contains operations
seen = set()
if x in seen:  # Much faster than list lookup
    print("Found!")
```

7. Custom Sort Keys:
```python
# Sort by length then alphabetically
words.sort(key=lambda x: (len(x), x))

# Sort a list of tuples by the first element
# items = [(3,2),(2,5),(-2,9)]
sorted_list = sorted(items, key=lambda x:x[0])
# sorted = [(-2,9),(2,5),(3,2)]
```

8. Object Instances:
```python
# Boolean value, check to see if object is instance of class
number = 10
text = "hello"

isinstance(number, int)       # True
isinstance(text, str)         # True
isinstance(number, float)     # False

# == vs is operator
a = [1, 2, 3]
b = [1, 2, 3]
print(a is b)  # False (they are distinct objects in memory)

c = a
print(a is c)  # True (c now refers to the same object as a)
```

9. List Concatentation and Repetition:
```python
list1 = ["a", "b", "c"]
list2 = [1, 2, 3]
list1 + list2  # ["a", "b", "c", 1, 2, 3]
[1, 2] * 2     # [1, 2, 1, 2]
```

10. Splat Operator
```python
numbers = [1, 2, 3]
print(*numbers)  # Equivalent to print(1, 2, 3)
```

```
