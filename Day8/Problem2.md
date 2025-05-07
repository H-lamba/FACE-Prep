# Excel Sheet Column Number

## Problem Statement

Given a string `columnTitle` that represents the column title as it appears in an Excel sheet, return its corresponding column number.

For example:

* A -> 1
* B -> 2
* C -> 3
* ...
* Z -> 26
* AA -> 27
* AB -> 28
* ...

### Example 1:

**Input**: `"A"`
**Output**: `1`

### Example 2:

**Input**: `"AB"`
**Output**: `28`

### Example 3:

**Input**: `"ZY"`
**Output**: `701`

## Approach

The problem follows a similar structure to a base-26 numbering system, where:

* The last letter represents a "unit" in base-26 (similar to how we use units, tens, hundreds in decimal).
* For example:

  * `"A"` represents 1 (i.e., 1 × 26^0).
  * `"B"` represents 2 (i.e., 2 × 26^0).
  * `"Z"` represents 26 (i.e., 26 × 26^0).
  * `"AA"` represents 27 (i.e., 1 × 26^1 + 1 × 26^0).

### Steps:

1. Initialize a result variable to 0.
2. For each character in the string (from left to right):

   * Convert the character to a numeric value by subtracting the ASCII value of 'A' and adding 1 (so that 'A' becomes 1, 'B' becomes 2, etc.).
   * Multiply the result by 26 (shifting the previous result one place to the left in base-26).
   * Add the numeric value of the current character to the result.
3. Return the final result.

## Code

```cpp
class Solution {
public:
    int titleToNumber(string columnTitle) {
        int result = 0;
        for (char c : columnTitle) {
            result = result * 26 + (c - 'A' + 1);
        }
        return result;
    }
};
```

## Explanation

1. **Initialize Result**: We start by initializing the result variable to 0, which will hold the final column number.
2. **Iterate Through Each Character**: We process each character in the string. For each character:

   * Calculate its corresponding numerical value by subtracting 'A' and adding 1.
   * Multiply the current result by 26 to account for the positional shift in base-26.
   * Add the value of the current character.
3. **Final Output**: After processing all characters, the result contains the column number corresponding to the input column title.

## Time and Space Complexity

* **Time Complexity**: O(n), where `n` is the length of the input string. We loop through the string once.
* **Space Complexity**: O(1), as we are only using a constant amount of extra space.

## Usage

You can use this solution to convert any Excel sheet column title into its corresponding column number by calling the `titleToNumber` function.

---
