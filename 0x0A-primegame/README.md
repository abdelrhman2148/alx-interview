# 0x0A. Prime Game

## Description

The **Prime Game** is a Python-based algorithm project focusing on prime numbers, game theory, and efficient computation. The challenge involves a competitive game where two players, Maria and Ben, take turns removing prime numbers and their multiples from a set of integers. The goal is to determine the winner based on optimal play.

This project emphasizes algorithm optimization and mathematical reasoning while adhering to Python programming best practices.

---

## Learning Objectives

To successfully complete this project, you will leverage the following concepts:

### Prime Numbers
- Understand what prime numbers are.
- Develop efficient algorithms for identifying prime numbers.

### Sieve of Eratosthenes
- Utilize this algorithm to find all prime numbers up to a given limit efficiently.

### Game Theory
- Apply principles of optimal play and win conditions in competitive games.

### Dynamic Programming/Memoization
- Use previously computed results to optimize calculations for multiple game rounds.

### Python Programming
- Implement logic with loops, conditionals, and efficient data structures.

---

## Requirements

### General
- Allowed editors: `vi`, `vim`, `emacs`
- All files will be interpreted/compiled on **Ubuntu 20.04 LTS** using Python 3.4.3.
- All files must end with a new line.
- The first line of all scripts: `#!/usr/bin/python3`.
- Code must adhere to **PEP 8 style** (version 1.7.x).
- All files must be executable.
- A `README.md` file at the root of the project is mandatory.

---

## Implementation

The project involves implementing the `isWinner(x, nums)` function:

### Function Prototype
```python
def isWinner(x, nums):
```

### Parameters
- `x` (int): Number of rounds.
- `nums` (list of int): Array of `n` values, where each `n` specifies the range of numbers for the round.

### Return Value
- **Maria**: If Maria wins the most rounds.
- **Ben**: If Ben wins the most rounds.
- **None**: If neither player wins the majority.

### Constraints
- `1 <= x <= 10,000`
- `1 <= nums[i] <= 10,000`
- No external libraries may be used.

---

## Example

### Input:
```python
x = 3
nums = [4, 5, 1]
```

### Output:
```plaintext
Winner: Ben
```

### Explanation:
1. **Round 1 (n = 4):**
   - Maria picks 2 (removes 2, 4).
   - Ben picks 3 (removes 3).
   - Ben wins (no primes left for Maria).

2. **Round 2 (n = 5):**
   - Maria picks 2 (removes 2, 4).
   - Ben picks 3 (removes 3).
   - Maria picks 5.
   - Maria wins.

3. **Round 3 (n = 1):**
   - Ben wins (no primes available for Maria).

**Result:** Ben wins more rounds.

---

## Algorithm Overview

1. **Prime Number Identification**
   - Use the **Sieve of Eratosthenes** to precompute prime numbers up to the largest `n` in `nums`.

2. **Game Simulation**
   - Simulate each round using the precomputed primes.
   - Track the current set of integers and remove primes and their multiples during each turn.

3. **Determine the Winner**
   - Count the number of rounds won by each player.
   - Return the player with the most wins or `None` if tied.

---

## Example Code

```python
#!/usr/bin/python3

def is_prime(n):
    """Checks if a number is a prime."""
    for i in range(2, int(n**0.5) + 1):
        if n % i == 0:
            return False
    return True

def calculate_primes(n, primes):
    """Calculate all primes up to n."""
    top_prime = primes[-1]
    if n > top_prime:
        for i in range(top_prime + 1, n + 1):
            primes.append(i if is_prime(i) else 0)

def isWinner(x, nums):
    """Determine the winner of the prime game."""
    players_wins = {"Maria": 0, "Ben": 0}
    primes = [0, 0, 2]
    calculate_primes(max(nums), primes)

    for round in range(x):
        options = sum(1 for i in primes[:nums[round] + 1] if i)
        winner = "Maria" if options % 2 else "Ben"
        players_wins[winner] += 1

    if players_wins["Maria"] > players_wins["Ben"]:
        return "Maria"
    elif players_wins["Ben"] > players_wins["Maria"]:
        return "Ben"
    return None
```

---

## Resources

- **Prime Numbers and Sieve of Eratosthenes**
  - [Prime Numbers - Khan Academy](https://www.khanacademy.org)
  - [Sieve of Eratosthenes - GeeksforGeeks](https://www.geeksforgeeks.org)

- **Game Theory Basics**
  - [Game Theory Introduction](https://www.investopedia.com)

- **Dynamic Programming**
  - [Dynamic Programming Examples](https://www.programiz.com)

- **Python Official Documentation**
  - [Python Lists](https://docs.python.org)

---

## Project Repository

- **GitHub Repository:** `alx-interview`
- **Directory:** `0x0A-primegame`
- **File:** `0-prime_game.py`
