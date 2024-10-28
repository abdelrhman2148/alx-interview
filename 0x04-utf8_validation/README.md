# 0x04. UTF-8 Validation

## Project Overview
This project is focused on creating a Python method to validate whether a given dataset represents a valid UTF-8 encoding. It requires a strong understanding of bitwise operations, the UTF-8 encoding scheme, and Python list manipulation. This project is designed to help reinforce your understanding of low-level data handling, particularly bitwise manipulations, as well as Boolean logic within Python.

---

## Requirements
- **Python Version**: All code will be interpreted/compiled on **Ubuntu 20.04 LTS** using **Python 3.4.3**.
- **PEP 8**: Code should adhere to PEP 8 style guidelines (version 1.7.x).
- **File Requirements**:
  - All files must end with a new line.
  - The first line of each file should be `#!/usr/bin/python3`.
  - A `README.md` file is mandatory.
  - All files must be executable.

## Key Concepts
1. **Bitwise Operations in Python**:
   - Using bitwise operators (AND `&`, OR `|`, shifts `<<` and `>>`) to manipulate individual bits of data.
2. **UTF-8 Encoding**:
   - UTF-8 encoding allows for 1 to 4 bytes per character.
   - For a dataset to be valid UTF-8, each byte must follow specific patterns:
     - 1-byte character: `0xxxxxxx`
     - 2-byte character: `110xxxxx 10xxxxxx`
     - 3-byte character: `1110xxxx 10xxxxxx 10xxxxxx`
     - 4-byte character: `11110xxx 10xxxxxx 10xxxxxx 10xxxxxx`
3. **List Manipulation in Python**:
   - Understanding how to iterate, access, and modify lists, and applying boolean logic.
4. **Data Representation**:
   - Working with byte-level data by handling the least significant bits (LSB) of integers.

## Task: UTF-8 Validation

### Objective
Write a method, `validUTF8(data)`, that determines if a given dataset represents a valid UTF-8 encoding.

### Prototype
```python
def validUTF8(data):
    """
    Determines if the dataset represents a valid UTF-8 encoding.
    
    Args:
    data (list): List of integers, each representing 1 byte of data.
    
    Returns:
    bool: True if data is valid UTF-8 encoding, False otherwise.
    """
```

### Instructions
1. A character in UTF-8 can be 1 to 4 bytes long.
2. The dataset contains multiple characters, with each byte represented by an integer.
3. Only the 8 least significant bits of each integer should be considered.
4. Your method should return `True` if the data is valid UTF-8 encoding, and `False` otherwise.

### Example Usage
```python
data = [65]
print(validUTF8(data))  # Output: True

data = [80, 121, 116, 104, 111, 110, 32, 105, 115, 32, 99, 111, 111, 108, 33]
print(validUTF8(data))  # Output: True

data = [229, 65, 127, 256]
print(validUTF8(data))  # Output: False
```

---

## Additional Resources
- [Python Bitwise Operators](https://docs.python.org/3/library/stdtypes.html#bitwise-operations)
- [UTF-8 Encoding Scheme (Wikipedia)](https://en.wikipedia.org/wiki/UTF-8)
- [Characters, Symbols, and the Unicode Miracle](https://www.joelonsoftware.com/2003/10/08/the-absolute-minimum-every-software-developer-absolutely-positively-must-know-about-unicode-and-character-sets-no-excuses/)

---

## Author
Abdelrhman Fikri
