# 0x07. Rotate 2D Matrix

## Description

This project involves implementing an in-place algorithm to rotate an \( n \times n \) 2D matrix by 90 degrees clockwise. The task requires manipulating the matrix without creating a new copy, focusing on space-efficient solutions. The project emphasizes understanding concepts like matrix transposition, row reversal, and efficient data manipulation in Python.

---

## Learning Objectives

By completing this project, you will learn:

- How to represent and manipulate 2D matrices in Python.
- The concept of in-place operations to minimize space complexity.
- Matrix transposition and its role in rotations.
- Using nested loops to iterate and modify elements in a 2D matrix.
- Problem-solving and algorithmic thinking skills in Python.

---

## Requirements

### General
- **Editors:** vi, vim, emacs  
- **Environment:** Ubuntu 20.04 LTS with Python 3.8.10  
- **Style:** Code must follow the [pycodestyle](https://pypi.org/project/pycodestyle/) (version 2.8.0).  
- **Modules:** No external modules are allowed.  
- **Documentation:** Every module and function must include docstrings.  
- **Execution:** All files must be executable and end with a new line.  

---

## Resources

- [Python Official Documentation](https://docs.python.org/3/tutorial/datastructures.html)
- [Inplace Rotate Square Matrix by 90 Degrees](https://www.geeksforgeeks.org/inplace-rotate-square-matrix-by-90-degrees-in-python/)
- [Transpose a Matrix](https://www.geeksforgeeks.org/transpose-matrix-single-line-python/)
- TutorialsPoint: [Python Lists](https://www.tutorialspoint.com/python/python_lists.htm)

---

## Usage

### Prototype
```python
def rotate_2d_matrix(matrix):
    """
    Rotate a 2D matrix 90 degrees clockwise in place.
    Args:
        matrix (list of list of int): The n x n 2D matrix to rotate.
    Do not return anything. The matrix is modified in place.
    """
```

### Example
```python
#!/usr/bin/python3
"""
Test 0x07 - Rotate 2D Matrix
"""
rotate_2d_matrix = __import__('0-rotate_2d_matrix').rotate_2d_matrix

if __name__ == "__main__":
    matrix = [
        [1, 2, 3],
        [4, 5, 6],
        [7, 8, 9]
    ]
    rotate_2d_matrix(matrix)
    print(matrix)
```

#### Output
```plaintext
[[7, 4, 1],
 [8, 5, 2],
 [9, 6, 3]]
```

---

## Implementation Steps

1. **Matrix Transposition:** Swap elements across the main diagonal.
2. **Reverse Rows:** Reverse the order of elements in each row.
3. **In-place Modification:** Perform all operations directly on the input matrix to ensure no additional space is used.

### Code
```python
#!/usr/bin/python3
"""Function to rotate a 2D matrix 90 degrees clockwise in place"""


def rotate_2d_matrix(matrix):
    """
    Rotate a 2D matrix 90 degrees clockwise in place.
    Args:
        matrix (list of list of int): The n x n 2D matrix to rotate.
    Do not return anything. The matrix is modified in place.
    """
    n = len(matrix)

    # Transpose the matrix
    for i in range(n):
        for j in range(i, n):
            matrix[i][j], matrix[j][i] = matrix[j][i], matrix[i][j]

    # Reverse each row
    for i in range(n):
        matrix[i].reverse()
```

---

## Repository Details

- **GitHub Repository:** [alx-interview](https://github.com/alx-interview)  
- **Directory:** `0x07-rotate_2d_matrix`  
- **File:** `0-rotate_2d_matrix.py`  

## License

This project is part of the ALX Software Engineering Program.
