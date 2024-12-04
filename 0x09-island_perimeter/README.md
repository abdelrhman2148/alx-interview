# 0x09. Island Perimeter

## Description

This project focuses on creating an algorithm to calculate the perimeter of an island within a 2D grid map. The island is represented by cells with a value of `1`, surrounded by water cells (`0`). The goal is to iterate through the grid and determine the total perimeter contributed by all land cells, adhering to specific conditions.

## Learning Objectives

By completing this project, you will:

- Deepen your understanding of **2D arrays** and matrix traversal.
- Enhance problem-solving skills using **conditional logic** and **iteration**.
- Apply Python programming concepts to design efficient solutions.
- Strengthen your ability to document and write clean, **PEP 8-compliant** code.

---

## Requirements

### General

- Allowed editors: `vi`, `vim`, `emacs`
- Files will be interpreted/compiled on **Ubuntu 20.04 LTS** using `python3` (version 3.4.3).
- Code must adhere to the **PEP 8 style guide** (version 1.7).
- Do not import external modules.
- All files and functions must be documented.
- Files should end with a new line and must be executable.

---

## Function Prototype

```python
def island_perimeter(grid):
    """
    Computes the perimeter of an island within a grid.

    Parameters:
    grid: 2D list where:
        - 0 represents water.
        - 1 represents land.

    Returns:
    int: The calculated perimeter of the island.
    """
```

### Constraints

- `grid` is a rectangular 2D list with dimensions not exceeding 100x100.
- The grid contains only **one island**, completely surrounded by water.
- The island has no lakes (i.e., water cells completely enclosed by land).

---

## Algorithm Explanation

The algorithm identifies land cells and calculates their contribution to the perimeter by checking their adjacent cells:

1. **Identify Land Cells**  
   Iterate through the grid and find cells with a value of `1`.

2. **Check Neighboring Cells**  
   For each land cell, check the four possible directions (up, down, left, right):
   - If the neighboring cell is out of bounds or contains water (`0`), it contributes to the perimeter.

3. **Sum Contributions**  
   Accumulate the contributions from all land cells to compute the total perimeter.

---

## Example Usage

### Input Grid
```python
grid = [
    [0, 0, 0, 0, 0, 0],
    [0, 1, 0, 0, 0, 0],
    [0, 1, 0, 0, 0, 0],
    [0, 1, 1, 1, 0, 0],
    [0, 0, 0, 0, 0, 0]
]
```

### Expected Output
```
12
```

### Execution
```bash
$ ./0-main.py
12
```

---

## File Structure

```
alx-interview/
│
├── 0x09-island_perimeter/
│   ├── README.md             # This documentation
│   ├── 0-island_perimeter.py # Function implementation
│   ├── 0-main.py             # Test script
```

---

## Development Process

1. **Plan**  
   Understand the problem constraints and identify edge cases:
   - A grid with no land cells.
   - An island occupying the entire grid.

2. **Implement**  
   Write a Python function to handle the grid traversal and perimeter calculation.

3. **Test**  
   Validate the solution using sample test cases and edge cases.

---

## Resources

- [PEP 8 Style Guide](https://peps.python.org/pep-0008/)
- [Python Official Documentation: Nested Lists](https://docs.python.org/3/tutorial/datastructures.html#nested-list-comprehensions)
- [GeeksforGeeks: Multidimensional Arrays in Python](https://www.geeksforgeeks.org/python-using-2d-arrays-lists/)

---

## Author

**Abdelrhman Fikri**  
