
# Find Nth Digit - Optimized C++ Solution

This repository contains an efficient C++ solution for the **"Find Nth Digit"** problem, where the goal is to find the `n`th digit in the infinite integer sequence:

```

123456789101112131415...

````

## 🧠 Problem Statement

Given an integer `n`, return the `n`th digit in the sequence formed by concatenating all the positive integers.

### Example:
- Input: `n = 15`
- Output: `2` (The 15th digit in the sequence is from number `12`)

## ✅ Optimized Approach

This solution efficiently finds the digit without constructing the full sequence or using string concatenation, and it works even for large inputs (`n ≤ 10^9`).

### Key Concepts:
- Determine the **digit length** group the digit falls into (1-digit, 2-digit, etc.).
- Compute the **actual number** that contains the digit.
- Extract the digit using **math only**, avoiding string conversions.

## 🚀 Time & Space Complexity

- **Time Complexity:** `O(log n)`
- **Space Complexity:** `O(1)`

## 📄 Code

```cpp
class Solution {
public:
    int findNthDigit(int n) {
        long long digitLength = 1;
        long long count = 9;
        long long start = 1;

        while (n > digitLength * count) {
            n -= digitLength * count;
            digitLength++;
            count *= 10;
            start *= 10;
        }

        start += (n - 1) / digitLength;

        int digitIndex = (n - 1) % digitLength;
        for (int i = 0; i < digitLength - digitIndex - 1; ++i) {
            start /= 10;
        }

        return start % 10;
    }
};
````

## 📌 Notes

* This approach avoids unnecessary memory usage and is ideal for coding challenges like LeetCode and GFG where performance matters.
* Works for input sizes up to `10^9` efficiently.

