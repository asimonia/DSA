# Python Cheat Sheet

A Cheat Sheet 📜 to **revise** Python syntax in **less time**. Particularly useful for solving Data Structure and Algorithmic problems or a quick overview before an interview.

# Table of Contents
- [Basics](#basics)
- [Data Structures](#data-structures)
  - [Lists](#lists)
  - [Dictionary](#dictionary)
  - [Deque](#deque)
  - [Heapq](#heapq)
  - [Sets](#sets)
  - [Tuples](#tuples)
  - [Strings](#strings)
- [Built-in Functions](#built-in-functions)
- [Math Topics](#math-topics)
- [Tips & Gotchas](#tips--gotchas)
- [Advanced Data Structures & Algorithms](#advanced-data-structures--algorithms)
  - [Recursion](#recursion)
  - [Linked Lists](#linked-lists)
  - [Binary Trees](#binary-trees)
  - [Graphs](#graphs)
  - [Two Pointer](#two-pointer)
  - [Sliding Window](#sliding-window)
  - [Binary Search](#binary-search)

# Basics

## Data Types
![Python Data Types](https://user-images.githubusercontent.com/59110866/173563442-1a6fa3d2-b569-4eb0-99cc-9b91cc8be1eb.png)

## Looping
```python
# Iterating through a list
fruits = ["apple", "banana", "cherry"]
for fruit in fruits:
    print(fruit)

# Iterating through a string
name = "Python"
for char in name:
    print(char)

# Generates numbers from 0 to 4 (inclusive and exclusive)
for i in range(0, 5):
    print(i)
               
# While loop with continue
i = 0
while i < 5:
    i += 1
    if i == 3:
        continue  # Skip printing 3
    print(i)

# While loop with break
i = 0
while i < 5:
    i += 1
    if i == 3:
        break  # Exit the loop when i is 3
    print(i)
print("Loop ended")              
```
## Branching
```python
if target < root.val:
  return binary_search_tree_includes(root.left, target)
elif target > root.val:
  return binary_search_tree_includes(root.right, target)
else:
  return True
```

# Data Structures

## Lists
Time Complexities:
![List Operations](https://user-images.githubusercontent.com/47276307/172330098-1c5f0a6e-7f80-4f4f-9be6-1d734e2c70cd.jpg)

```python
nums = [1,2,3]

# Common Operations
nums.append(1)           # Add to end
nums.pop(index=-1)       # Remove & return last element by default
nums.insert(0,10)        # Add 10 from left (at index 0 which is start)
nums.index(1)            # Find index
nums.sort(reverse=False) # Inplace sort


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
d.items()                 # Key-value pairs
d.keys()                  # Just keys
d.values()               # Just values
d.pop(key)              # Remove and return value

# Advanced Usage
from collections import defaultdict
d = defaultdict(list)     # Auto-initialize missing keys
d = defaultdict(int)      # Useful for counting
```

## Deque
Time Complexities:
![Deque Operations](https://user-images.githubusercontent.com/47276307/172330115-78500420-3276-4e45-8ce3-fd668b7eb14e.jpg)

```python
from collections import deque

# Perfect for BFS - O(1) operations on both ends
d = deque()
d.append(1)          # Add right
d.popleft()          # Remove left
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

# Math Topics

## Math and Statistics Module Essentials
```python
import math
from statistics import mean, median

# Common Functions
math.ceil(2.3)        # 3 - Smallest integer greater than x
math.floor(2.3)       # 2 - Largest integer less than x
math.sqrt(x)          # Square root

mean([10, 20, 30])         # 20
median([10, 20, 30])       # 20
```

## Important Python Integer Operations
```python

# Negative number handling
x = -3
y = 2
print(x // y)        # -2 (floor division)
print(x % y)         # 1 (Python's modulo with negative numbers)
```

# Tips & Gotchas


1. Heap Priority:
```python
# For custom priority in heapq, use tuples
heap = []
heapq.heappush(heap, (priority, item))
```

2. List Comprehension:
```python
# Often clearer than map/filter
squares = [x*x for x in range(10) if x % 2 == 0]
```

3. String Building:
```python
# Use join() instead of += for strings
chars = ['a', 'b', 'c']
word = ''.join(chars)  # More efficient
```

4. Custom Sort Keys:
```python
# Sort by length then alphabetically
# words = ['banana', 'apple', 'pear']
sorted_words = sorted(words, key=lambda x: (len(x), x))
# sorted_words -> ['pear', 'apple', 'banana']


# Sort a list of tuples by the first element
# items = [(3,2),(2,5),(-2,9)]
sorted_list = sorted(items, key=lambda x:x[0])
# sorted = [(-2,9),(2,5),(3,2)]
```

5. Object Instances:
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

6. List Concatentation and Repetition:
```python
list1 = ["a", "b", "c"]
list2 = [1, 2, 3]
list1 + list2  # ["a", "b", "c", 1, 2, 3]
[1, 2] * 2     # [1, 2, 1, 2]
```

7. Splat Operator
```python
numbers = [1, 2, 3]
print(*numbers)  # Equivalent to print(1, 2, 3)
```

8. Looping methods
```python
# With index and value
for i, n in enumerate(nums):
    print(i, n)

# Loop through multiple arrays simultaneously with unpacking
nums1 = [1, 3, 5]
nums2 = [2, 4, 6]
for n1, n2 in zip(nums1, nums2):
    print(n1, n2)
```

# Advanced Data Structures & Algorithms

## Recursion
1. Define the base cases (there can be multiple)
2. Define the recursive case so that the subproblems will converge to the base case
3. Think about the values your function will return and invoke the function from within

## Linked Lists
<img width="800" height="330" alt="image" src="https://github.com/user-attachments/assets/5c92fdae-9d39-4706-adf7-6f628971131b" />

- Linked List:
  - Data Structure: Non-contiguous
  - Memory Allocation: Typically allocated one by one to individual elements
  - Insertion/Deletion: Efficient
  - Access: Sequential

- Array:
  - Data Structure: Contiguous
  - Memory Allocation: Typically allocated to the whole array
  - Insertion/Deletion: Inefficient
  - Access: Random

```python
class Node:
    def __init__(self, val):
        self.val = val
        self.next = None

# Traversing the linked list, all you need to do is pass the head
# A -> B -> C -> D -> None

def print_list(head):
    current = head
    while current is not None:
        print(current.val)
        current = current.next

def recursive_list(head):
    if head is None:
        return
    print(head.val)
    recursive_list(head.next)

if __name__ == '__main__':
    a = Node('A')
    b = Node('B')
    c = Node('C')
    d = Node('D')

    a.next = b
    b.next = c
    c.next = d
    print_list(a)
    recursive_list(a)
```

## Binary Trees
<img width="1043" height="697" alt="image" src="https://github.com/user-attachments/assets/d254a9c4-6961-4980-96b4-6624f0184e87" />

### Properties
- at most 2 children per node, referred to left and right
- exactly one root
- exactly one path between root and any node

### Definitions
- Nodes: The fundamental part of a binary tree, where each node contains data and link to two child nodes.
- Root: The topmost node in a tree is known as the root node. It has no parent and serves as the starting point for all nodes in the tree.
- Parent Node: A node that has one or more child nodes. In a binary tree, each node can have at most two children.
- Child Node: A node that is a descendant of another node (its parent).
- Sibling Node: Nodes that share the same parent.
- Leaf Node: A node that does not have any children or both children are null.
- Subtree: A portion of the tree that consists of a node and all of its descendants
- Depth of a Node: The number of edges from a specific node to the root node. The depth of the root node is zero.
- Height of a Binary Tree: The maximum number of edges on the path from the root node to the farthest leaf node.  Important: an empty tree has a negative one height.

### Tree Traversals
**DFS Traversal:** Explore one branch fully before backtracking.  The name of the order represents when the node gets visited.
- Preorder: Visits the node first, then left subtree, then right subtree
- Inorder: Visits left subtree, then the node, then the right subtree
- Postorder: Visits left subtree, then right subtree, then the node.

**BFS Traversal:** Explore branches far and wide.
- Level order: BFS explores all nodes at the present depth before moving on to nodes at the next depth level.

```python
class Node:
    def __init__(self, val):
        self.val = val
        self.left = None
        self.right = None

# In-order DFS: Left, Root, Right
def in_order_dfs(node):
    if node is None:
        return
    in_order_dfs(node.left)
    print(node.val, end=' ')
    in_order_dfs(node.right)

# Pre-order DFS: Root, Left, Right
def pre_order_dfs(node):
    if node is None:
        return
    print(node.val, end=' ')
    pre_order_dfs(node.left)
    pre_order_dfs(node.right)

# Post-order DFS: Left, Right, Root
def post_order_dfs(node):
    if node is None:
        return
    post_order_dfs(node.left)
    post_order_dfs(node.right)
    print(node.val, end=' ')

# BFS: Level order traversal
from collections import deque
def bfs(root):
    if root is None:
        return
    queue = deque([root])
    while queue:
        node = queue.popleft()
        print(node.val, end=' ')
        if node.left:
            queue.append(node.left)
        if node.right:
            queue.append(node.right)

if __name__ == "__main__":
    # Creating the tree
    root = Node("a")
    b = Node("b")
    c = Node("c")
    d = Node("d")
    e = Node("e")
    f = Node("f")
    
    root.left = b
    root.right = c
    b.left = d
    b.right = e
    c.right = f
    
    #           a
    #         /   \
    #        b      c
    #      /  \       \
    #    d     e       f

    print("In-order DFS: ", end='')
    in_order_dfs(root)
    print("\nPre-order DFS: ", end='')
    pre_order_dfs(root)
    print("\nPost-order DFS: ", end='')
    post_order_dfs(root)
    print("\nLevel order: ", end='')
    bfs(root)
```

  
### Binary Search Tree
Properties of Binary Search Tree:
- The left subtree of a node contains only nodes with keys less than the node's key.
- The right subtree of a node contains only nodes with keys greater than the node's key.
- The left and right subtree each must also be a binary search tree.  
- There must be no duplicate nodes(BST may have duplicate values with different handling approaches).

<img width="1001" height="471" alt="image" src="https://github.com/user-attachments/assets/0377610e-e615-45cc-ad03-e2a36140482f" />

### Balanced Tree
To check if a Binary tree is balanced we need to check three conditions:

1. The absolute difference between heights of left and right subtrees at any node should be less than 1.
2. For each node, its left subtree should be a balanced binary tree.
3. For each node, its right subtree should be a balanced binary tree.

<img width="1043" height="746" alt="image" src="https://github.com/user-attachments/assets/79be44b4-16b1-45f2-9ee9-7981501dd770" />

```python
# height between the left and right subtrees differs by at most 1 for every node.
def height(node):
    if node is None:
        return -1
    return 1 + max(height(node.left), height(node.right))

def is_tree_balanced(root):
  
    if root is None:
        return True

    lHeight = height(root.left)
    rHeight = height(root.right)

    if abs(lHeight - rHeight) > 1:
        return False

    return is_tree_balanced(root.left) and is_tree_balanced(root.right)
```

### Complete Binary Tree
- every level is filled except possibly bottom level
- nodes at the bottom level must be as far left as possible
- by definition, it is balanced

### Heap
- binary tree data structure that are _balanced_ this is for O(log n) lookup and insertion
- heaps stores items and maintains an order of items
- no relation between the siblings
- more relaxed than search tree order
- Min Heap
  - root is the minimum
  - the children are greater than or equal to the parent for each subtree
- Max Heap
  - root is the maximum
  - the children are less than or equal to the parent for each subtree

## Graphs

## Two Pointer

## Sliding Window

## Binary Search
```python
# Search in O(log N) time
def binary_search(numbers, target):
  lo = 0
  hi = len(numbers) - 1


  while lo <= hi:
    midpoint = (hi + lo) // 2
    # target is in lower half, search lower half
    if target < numbers[midpoint]:
      hi = midpoint - 1
    # target is in upper half, search upper half  
    elif target > numbers[midpoint]:
      lo = midpoint + 1
    else:
      return midpoint
  return -1
```
