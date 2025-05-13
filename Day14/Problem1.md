# 🧮 Reverse Integer – LeetCode Problem #7

This repository contains a C++ solution to the [LeetCode Problem #7: Reverse Integer](https://leetcode.com/problems/reverse-integer/), a common coding challenge often asked in technical interviews.

## 📌 Problem Statement

Given a signed 32-bit integer `x`, return `x` with its digits reversed.  
If reversing `x` causes the value to go outside the **signed 32-bit integer range** `[-2³¹, 2³¹ − 1]`, return `0`.

### Example 1
```

Input: x = 123
Output: 321

```

### Example 2
```

Input: x = -123
Output: -321

```

### Example 3
```

Input: x = 120
Output: 21

````

### Constraints
- The environment does not allow the use of 64-bit integers.
- Time Complexity: `O(log₁₀(x))`
- Space Complexity: `O(1)`

---

## ✅ Solution Approach

- We extract each digit using modulo (`% 10`).
- Check for overflow **before** multiplying the current result by 10.
- Return `0` immediately if the reversed number goes out of bounds.

---

## 🚀 Code

```cpp
class Solution {
public:
    int reverse(int x) {
        int ans = 0;
        while (x != 0) {
            int digit = x % 10;

            // Check for overflow before multiplying and adding
            if (ans < INT_MIN / 10 || ans > INT_MAX / 10)
                return 0;

            ans = ans * 10 + digit;
            x /= 10;
        }
        return ans;
    }
};
````

---

## 💡 Author

**Himanshu**
