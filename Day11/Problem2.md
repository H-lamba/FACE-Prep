
# LeetCode Problem: Factorial Trailing Zeroes

## 🧠 Problem Statement

Given an integer `n`, return the number of **trailing zeroes** in `n!`.

> Note: `n!` means `n * (n - 1) * (n - 2) * ... * 3 * 2 * 1`.

---

## 🧪 Examples

### Example 1:
```

Input: n = 3
Output: 0
Explanation: 3! = 6 → No trailing zero

```

### Example 2:
```

Input: n = 5
Output: 1
Explanation: 5! = 120 → One trailing zero

```

### Example 3:
```

Input: n = 0
Output: 0
Explanation: 0! = 1 → No trailing zero

````

---

## ✅ Approach: Count Factors of 5

### Why It Works:
Trailing zeroes are created by multiplying 10s, and 10 = 2 × 5.  
In a factorial, there are **more 2s than 5s**, so we count how many times 5 is a factor in numbers up to `n`.

We count:
- How many multiples of 5 are there?
- How many multiples of 25 (since 25 adds an extra 5)?
- How many multiples of 125? etc.

---

## 💻 Code:

```cpp
class Solution {
public:
    int trailingZeroes(int n) {
        int ans = 0;
        while (n >= 5) {
            n = n / 5;
            ans += n;
        }
        return ans;
    }
};
````

---

## 🕒 Time and Space Complexity

* **Time Complexity:** O(log₅ n) — each division by 5 reduces `n`
* **Space Complexity:** O(1) — constant space

---

## 🔍 Commented Out (Inefficient) Approach

Originally, a brute-force method was considered:

1. Compute full factorial using recursion
2. Count how many trailing zeroes by dividing the number by 10 repeatedly

But this is highly inefficient for large `n` due to integer overflow and is thus **not used**.

```cpp
/*
long long fac(int n) {
    if (n == 0) return 1;
    return fac(n - 1) * n;
}

int trailingZeroes(int n) {
    long long fact = fac(n);
    int ans = 0;
    while (fact > 0) {
        if (fact % 10 != 0) break;
        ans++;
        fact /= 10;
    }
    return ans;
}
*/
```

---

## 📌 Summary

| Approach     | Time Complexity | Space Complexity | Handles Large `n` |
| ------------ | --------------- | ---------------- | ----------------- |
| Brute Force  | Exponential     | High             | ❌ No              |
| Factor Count | O(log n)        | O(1)             | ✅ Yes             |

---
