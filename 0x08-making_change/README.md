# README.md

## Project Title: 0x08. Making Change

### Description:
The goal of this project is to solve the classic **coin change problem**, where you are given a list of coin denominations and a total amount. You must determine the fewest number of coins needed to make up the given total. The challenge here is to implement a solution that is not only correct but also efficient, applying key concepts from **Greedy Algorithms** and **Dynamic Programming**.

### Key Concepts:

1. **Greedy Algorithms**:
   - Understanding greedy algorithms is crucial for this project. A greedy algorithm makes locally optimal choices with the hope of finding a global optimum. In the case of the coin change problem, the greedy approach picks the largest coin first and subtracts it from the remaining amount, continuing until the target is met or surpassed.
   - However, greedy algorithms can fail in some cases (for example, when the coin denominations do not allow for an optimal greedy choice). It is important to know when to apply it and when a more comprehensive dynamic programming approach is needed.

2. **Dynamic Programming**:
   - Dynamic programming (DP) is a method used to solve optimization problems by breaking them down into simpler subproblems. In the context of the coin change problem, DP can be used to calculate the minimum number of coins required by solving smaller subproblems and building the solution step by step.
   - This approach ensures the solution is optimal, even in cases where greedy algorithms fail.

3. **Algorithmic Complexity**:
   - Understanding the time and space complexity of the chosen algorithm is essential. In this project, you should aim to create a solution that efficiently handles larger inputs while meeting the constraints.

### Problem Statement:

Given a pile of coins of different values, determine the fewest number of coins needed to meet a given total amount. If it is not possible to meet the total with the available coins, return `-1`.

- **Prototype**:
  ```python
  def makeChange(coins, total):
  ```
- **Input**:
  - `coins`: a list of positive integers representing coin denominations.
  - `total`: an integer representing the total amount to be met.
  
- **Output**:
  - Return the fewest number of coins needed to make up the total.
  - If the total cannot be met using the available coins, return `-1`.
  - If the total is `0` or less, return `0`.

### Example:

```python
makeChange([1, 2, 25], 37)  # Output: 7
makeChange([1256, 54, 48, 16, 102], 1453)  # Output: -1
```

### Solution Approach:

1. **Greedy Algorithm**:
   - First, we sort the coin denominations in descending order.
   - We then iterate through the coins, starting with the largest coin, and subtract it from the total as many times as possible.
   - We repeat this process until the remaining amount is reduced to `0` or no further coins can be used.

2. **Edge Cases**:
   - If the `total` is less than or equal to `0`, we return `0` as no coins are needed.
   - If after attempting to use all the coins, the total cannot be reached, return `-1`.

### Code Implementation:

```python
#!/usr/bin/python3
"""
Determines the fewest num of coins needed to meet a given amount total
"""

def makeChange(coins, total):
    """
    Calculates the minimum num of coins needed to make change for a given total
    Returns:
    The minimum num of coins needed to make change, or -1 if it is not possible
    """
    if total <= 0:
        return 0

    remaining = total
    coins_count = 0
    coin_num = 0
    sorted_coins = sorted(coins, reverse=True)
    u = len(coins)

    while remaining > 0:
        if coin_num >= u:
            return -1
        if remaining - sorted_coins[coin_num] >= 0:
            remaining -= sorted_coins[coin_num]
            coins_count += 1
        else:
            coin_num += 1
    return coins_count
```

### How to Run:

1. Clone the repository:
   ```bash
   git clone https://github.com/your-repo/alx-interview.git
   ```

2. Navigate to the project directory:
   ```bash
   cd 0x08-making_change
   ```

3. Make sure the script is executable:
   ```bash
   chmod +x 0-making_change.py
   ```

4. Run the script:
   ```bash
   ./0-making_change.py
   ```

5. Alternatively, you can directly import the function in another Python script:
   ```python
   from 0-making_change import makeChange
   print(makeChange([1, 2, 25], 37))
   ```

### Evaluation:

- **Time Complexity**: The time complexity of the greedy approach is dominated by the sorting step, which is `O(n log n)`, where `n` is the number of coin denominations.
- **Space Complexity**: The space complexity is `O(n)` due to the storage of the sorted coin denominations.

### Resources:

- **GeeksforGeeks**:
  - [Coin Change | DP-7](https://www.geeksforgeeks.org/coin-change-dp-7/)
  - [Greedy Algorithm to find Minimum number of Coins](https://www.geeksforgeeks.org/greedy-algorithm-to-find-minimum-number-of-coins/)
  
- **YouTube Tutorials**:
  - [Dynamic Programming - Coin Change Problem](https://www.youtube.com/watch?v=frJ3R-G1yD4)

### Requirements:

- **Python**: 3.4.3 (Ubuntu 20.04 LTS)
- **Allowed Editors**: vi, vim, emacs
- **PEP 8 Style**: All files should adhere to Python’s PEP 8 style guide.
