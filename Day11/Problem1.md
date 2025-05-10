# Remove Nth Node From End of List (LeetCode Problem #19)

## Problem Statement

Given the head of a linked list, remove the nth node from the end of the list and return its head.

### Example 1:

```
Input: head = [1,2,3,4,5], n = 2  
Output: [1,2,3,5]
```

### Example 2:

```
Input: head = [1], n = 1  
Output: []
```

### Example 3:

```
Input: head = [1,2], n = 1  
Output: [1]
```

> 📝 **Note:** While the problem statement is about removing the Nth node from the end of a linked list, the code included here solves **a different problem** — counting trailing zeroes in a factorial number. The README explains the approaches used in that factorial-related logic.

---

# Trailing Zeroes in Factorial

The code provided calculates the number of trailing zeroes in `n!` (n factorial). There are two approaches:

## ✅ Optimized Approach (Used in Final Code)

```cpp
int trailingZeroes(int n) {
    int ans = 0;
    while(n >= 5) {
        n = n / 5;
        ans = ans + n;
    }
    return ans;
}
```

### 🔍 Explanation:

* A trailing zero is created with each pair of multiples of 2 and 5.
* Since factorials have more 2s than 5s, we count how many times 5 is a factor.
* This is done by dividing `n` by 5, 25, 125, etc., adding all the quotients.

**Time Complexity:** `O(log₅n)`
**Space Complexity:** `O(1)`

---

## ❌ Brute-Force (Commented Out in Code)

```cpp
long long fac(int n) {
    if(n == 0) return 1;
    return fac(n - 1) * n;
}

int trailingZeroes(int n) {
    long long fact = fac(n);
    int ans = 0;
    while(fact > 0) {
        if(fact % 10 != 0) break;
        ans++;
        fact = fact / 10;
    }
    return ans;
}
```

### 🔍 Explanation:

* First calculates the factorial using recursion.
* Then counts the number of trailing zeroes by dividing by 10 until the last digit is not 0.

**Problems with this approach:**

* Recursive factorial quickly overflows for large `n` (even for `n > 20`).
* Very inefficient in terms of time and space.

---

## Summary

| Approach    | Time Complexity         | Space Complexity | Suitable for Large `n`? |
| ----------- | ----------------------- | ---------------- | ----------------------- |
| Brute-Force | Exponential (recursive) | High             | ❌ No                    |
| Optimized   | `O(log₅n)`              | Constant         | ✅ Yes                   |

---
