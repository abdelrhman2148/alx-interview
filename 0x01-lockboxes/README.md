# 0x01. Lockboxes

## Project Overview

In this project, we are tasked with solving the **Lockboxes** problem. Given `n` locked boxes, each numbered sequentially from `0` to `n - 1`, where each box may contain keys to other boxes, we need to determine if all boxes can be opened, starting with the first unlocked box, `boxes[0]`.

The challenge tests understanding of algorithmic thinking, especially related to traversal techniques (similar to graph traversal), and Python data structures.

## Learning Objectives

At the end of this project, you should be able to explain the following without the help of external resources:
- How to manipulate lists in Python.
- Basics of graph theory and how it applies to this problem.
- The importance of algorithmic efficiency and complexity.
- How to implement and optimize recursive or iterative solutions.
- Set operations for keeping track of visited states in problems involving traversal.

## Requirements

- Allowed editors: `vi`, `vim`, `emacs`
- Files will be interpreted/compiled on Ubuntu 20.04 LTS using `python3` (version 3.4.3)
- All files should end with a new line
- The first line of all your Python scripts must be: `#!/usr/bin/python3`
- A `README.md` file at the root of the project is mandatory
- Your code should follow the **PEP 8** style guide (version 1.7.x)
- All files must be executable

## Task

### 0. Lockboxes

Write a method that determines if all the boxes can be opened.  
- **Prototype**: `def canUnlockAll(boxes)`
- `boxes` is a list of lists where each list represents a box and may contain keys to other boxes.
- A key with the same number as a box opens that box.
- You can assume all keys will be positive integers.
- The first box (`boxes[0]`) is unlocked by default.
- Return `True` if all boxes can be opened, otherwise return `False`.

### Example

```python
boxes = [[1], [2], [3], [4], []]
print(canUnlockAll(boxes))  # True

boxes = [[1, 4, 6], [2], [0, 4, 1], [5, 6, 2], [3], [4, 1], [6]]
print(canUnlockAll(boxes))  # True

boxes = [[1, 4], [2], [0, 4, 1], [3], [], [4, 1], [5, 6]]
print(canUnlockAll(boxes))  # False
```

### Approach

The problem can be approached by considering the boxes as nodes in a graph, and the keys as edges connecting these nodes. The goal is to check if we can traverse the graph starting from the first node (box 0) and reach every other node (box). A common approach is to use **Depth-First Search (DFS)** or **Breadth-First Search (BFS)** to explore all boxes and keys.

### Algorithm Explanation

1. **Initialize**:
   - A set to keep track of unlocked boxes.
   - A stack (or queue) to manage which boxes to explore next (starting with box `0`).

2. **Traverse the Boxes**:
   - While there are boxes to explore, check the keys in the current box.
   - Unlock any new boxes you haven’t opened yet.
   - Add newly unlocked boxes to the stack to explore their keys.

3. **Check Result**:
   - If the number of unlocked boxes equals `n` (the total number of boxes), return `True`.
   - Otherwise, return `False`.

## Testing

You can test your implementation using the example inputs provided in the task, and you can create more complex scenarios to ensure the algorithm works under various conditions.

## Resources

- [Python Lists (Official Documentation)](https://docs.python.org/3/tutorial/datastructures.html)
- [Graph Theory Basics](https://www.khanacademy.org/computing/computer-science/algorithms#graphs)
- [PEP 8 Python Style Guide](https://www.python.org/dev/peps/pep-0008/)
- [Big O Notation](https://www.geeksforgeeks.org/analysis-of-algorithms-set-1-asymptotic-analysis/)

## Author
- **Abdelrhman Fikri**
