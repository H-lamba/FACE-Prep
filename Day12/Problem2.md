# Leetcode Problem 1523: Count Odd Numbers in an Interval Range

## 🧠 Problem Statement

Given two non-negative integers `low` and `high`, return the **count of odd numbers** in the interval `[low, high]` (inclusive).

### 📌 Example 1:
**Input:**  
```

low = 3, high = 7

```

**Output:**  
```

3

```

**Explanation:**  
Odd numbers between 3 and 7 are: `[3, 5, 7]`

---

### 📌 Example 2:
**Input:**  
```

low = 8, high = 10

```

**Output:**  
```

1

````

**Explanation:**  
Odd number between 8 and 10 is: `[9]`

---

## ✅ Approach

The number of odd numbers in an inclusive range `[low, high]` can be calculated with simple math:

1. **If both `low` and `high` are even:**  
   The count is `(high - low) / 2`

2. **If at least one of them is odd:**  
   We add 1 extra to the count because the odd endpoints extend the range.

This logic is implemented using:
```cpp
int c = (high - low) / 2;
if (low % 2 != 0 || high % 2 != 0)
    return c + 1;
return c;
````

---

## 🔧 Implementation (C++)

```cpp
class Solution {
public:
    int countOdds(int low, int high) {
        int c = (high - low) / 2;
        if (low % 2 != 0 || high % 2 != 0) {
            return c + 1;
        }
        return c;
    }
};
```

---

## 🧮 Dry Run

**Input:** `low = 3`, `high = 7`

* `(high - low) / 2` = `(7 - 3) / 2` = `2`
* Since `low` is odd, add 1 → `2 + 1 = 3`
* ✅ Output is `3`

---

## ⏱️ Time and Space Complexity

* **Time Complexity:** `O(1)` – Purely arithmetic
* **Space Complexity:** `O(1)` – No extra space used

---

## ✨ Simpler Alternative (Optional)

This entire logic can also be written in one line:

```cpp
return (high + 1) / 2 - (low) / 2;
```
