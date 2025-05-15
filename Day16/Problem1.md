# LeetCode Problem 633: Sum of Square Numbers

## Problem Statement

Given a non-negative integer `c`, determine whether there exist two integers `a` and `b` such that:

```

a² + b² = c

````

### Examples

- **Input:** `c = 5`  
  **Output:** `true`  
  **Explanation:** 1² + 2² = 5

- **Input:** `c = 3`  
  **Output:** `false`

---

## Solution Approaches

### ✅ Approach 1: Binary Search (Commented Out in Code)

**Idea:**  
For every possible value of `a` such that `a² < c`, calculate the required value `b² = c - a²`. Then, perform a binary search in the range `[0, c]` to check whether `b²` is a perfect square.

**Time Complexity:** O(√c * log c)  
**Space Complexity:** O(1)

```cpp
for(long long i = 0; i*i < c; i++) {
    long long req = c - i*i;
    int low = 0, high = c;
    while(low <= high) {
        long long mid = low + (high - low) / 2;
        if(mid*mid == req) return true;
        else if(mid*mid > req) high = mid - 1;
        else low = mid + 1;
    }
}
return false;
````

---

### ✅ Approach 2: Square Root Check (Optimized and Used in Code)

**Idea:**
Loop through possible values of `a` such that `a² < c`. For each `a`, compute `b² = c - a²`. Take the integer square root of `b²` and check if squaring it again gives back `b²`.

**Advantages:**

* Avoids binary search.
* More efficient in practice using built-in `sqrt()`.

**Time Complexity:** O(√c)
**Space Complexity:** O(1)

```cpp
for(long long i = 0; i*i < c; i++) {
    long long b = c - i*i;
    long long check = sqrt(b);
    if(check*check == b) return true;
}
return false;
```

---

## Summary

Both approaches iterate over potential values for `a`, but the optimized approach improves performance by avoiding binary search and directly checking if the remainder is a perfect square using `sqrt()`. This results in cleaner and faster execution, especially for large values of `c`.

---
Solution by **Himanshu**
