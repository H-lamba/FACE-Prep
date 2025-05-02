
# Add Digits - LeetCode Problem 258

This repository provides a C++ solution to **[LeetCode Problem 258: Add Digits](https://leetcode.com/problems/add-digits/)**, using both an **iterative digit-summing approach** and a **constant-time mathematical trick**.

## Problem Description

Given an integer `num`, repeatedly add all its digits until the result has only one digit, and return it.

### Example 1:
```
Input: num = 38  
Output: 2  
Explanation:
38 --> 3 + 8 = 11  
11 --> 1 + 1 = 2  
Return 2
```

### Example 2:
```
Input: num = 0  
Output: 0
```

---

## Approach 1: Iterative Digit Summing

We simulate the process step by step:

1. While `num` has more than one digit (`num > 9`), keep summing its digits.
2. Use a loop to break down `num` and compute the sum of its digits.
3. Repeat until a single-digit result is obtained.

### Code:

```cpp
class Solution {
public:
    int addDigits(int num) {
        while (num > 9) {
            int sum = 0;
            while (num > 0) {
                sum += num % 10;
                num /= 10;
            }
            num = sum;
        }
        return num;
    }
};
```

- **Time Complexity:** O(log₁₀n), because we process each digit in every iteration.
- **Space Complexity:** O(1)

---

## Approach 2: Constant-Time Digital Root Formula

This is a **math-based trick** based on the concept of **digital root**:

- Any non-zero number's digital root can be computed as:  
 digital root = 1 + (num - 1) \% 9
  

### Code:

```cpp
class Solution {
public:
    int addDigits(int num) {
        if (num == 0) return 0;
        return 1 + (num - 1) % 9;
    }
};
```

- **Time Complexity:** O(1)
- **Space Complexity:** O(1)

---

## Why the Formula Works

The digital root of a number is its value modulo 9, adjusted for edge cases (like 0). This method eliminates the need for iteration or recursion, making it highly efficient.

---
Himanshu 
This solution demonstrates both brute-force and optimal techniques to solve the same problem.

---
