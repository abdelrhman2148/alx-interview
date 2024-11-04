# 0x05. N Queens

## Overview
The **N Queens problem** is a classic puzzle in computer science that involves placing **N queens** on an **N×N chessboard** such that no two queens threaten each other. The goal is to find all possible solutions for a given board size, where each queen can attack along rows, columns, and diagonals.

This project utilizes the **backtracking algorithm** to efficiently explore all potential arrangements of queens on the board while avoiding conflicts. Implementing this solution requires understanding backtracking, recursion, list manipulation, and handling command-line arguments in Python.

## Key Concepts

- **Backtracking**: A recursive algorithmic technique for exploring potential solutions and reverting choices when a solution path is unviable.
- **Recursion**: Using recursive functions to navigate possible board configurations.
- **List Manipulation**: Storing and modifying the positions of queens on the board using Python lists.
- **Command-Line Arguments**: Handling input with the `sys` module to specify the board size (N) from the command line.

## Requirements

- **Environment**: The program will be interpreted on **Ubuntu 20.04 LTS** using **Python 3.4.3**.
- **File Requirements**:
  - All files should be executable and end with a new line.
  - All code must adhere to **PEP 8** style guidelines (version 1.7.*).
  - The project root folder must contain a `README.md` file.
  - The first line of each file must be `#!/usr/bin/python3`.

## Usage

To run the program, execute the following command in the terminal:
```bash
./0-nqueens.py N
```
where `N` is the board size, specifying the number of queens.

### Input Validation
- If the program is called with the wrong number of arguments, it will print:
  ```
  Usage: nqueens N
  ```
  and exit with a status of 1.
- If `N` is not an integer, the program will print:
  ```
  N must be a number
  ```
  and exit with a status of 1.
- If `N` is less than 4, the program will print:
  ```
  N must be at least 4
  ```
  and exit with a status of 1.

### Output
For each solution, the program will print the positions of queens in a format like:
```python
[[0, 1], [1, 3], [2, 0], [3, 2]]
```
Each list entry represents a queen’s position on the board as `[row, column]`.

### Example
```bash
$ ./0-nqueens.py 4
[[0, 1], [1, 3], [2, 0], [3, 2]]
[[0, 2], [1, 0], [2, 3], [3, 1]]
```

## File Structure

- **0-nqueens.py**: Main Python file containing the implementation for solving the N Queens problem.

## Solution Outline

1. **Backtracking Function** (`backtrack`): Recursively explores potential queen placements. If a queen can be placed without conflicts, the function proceeds to the next row.
2. **Conflict Tracking**:
   - **Column Set**: Tracks occupied columns.
   - **Positive Diagonal Set**: Tracks occupied `row + col` diagonals.
   - **Negative Diagonal Set**: Tracks occupied `row - col` diagonals.
3. **Result Storage**: Saves each valid board configuration.

## Additional Resources

- [Backtracking Algorithms](https://example.com)
- [Recursion in Python](https://example.com)
- [List Manipulation](https://example.com)
- [Python Command-Line Arguments](https://example.com)

## Author

Abdelrhman Fikri
