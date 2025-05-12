# Sign of the Product of an Array – LeetCode 1822

## Problem Statement

You are given an integer array `nums`. Let `product` be the product of all values in the array `nums`.

Implement a function `signFunc(x)` that returns:
- `1` if `x` is positive,
- `-1` if `x` is negative,
- `0` if `x` is equal to 0.

Return `signFunc(product)`.

---

## Examples

**Example 1:**
```

Input: nums = \[-1,-2,-3,-4,3,2,1]
Output: 1
Explanation: The product is 144, and signFunc(144) = 1.

```

**Example 2:**
```

Input: nums = \[1,5,0,2,-3]
Output: 0
Explanation: The product is 0, and signFunc(0) = 0.

```

**Example 3:**
```

Input: nums = \[-1,1,-1,1,-1]
Output: -1
Explanation: The product is -1, and signFunc(-1) = -1.

````

---

## Approach

### Key Insight:
- You **don’t need to compute the actual product**, which may cause integer overflow.
- The **sign** of the product depends only on:
  - Whether any number is 0 → if yes, return `0`.
  - The **count of negative numbers**:
    - Even count → positive product → return `1`.
    - Odd count → negative product → return `-1`.

### Steps:
1. Iterate through the array.
2. If a zero is encountered, return `0`.
3. Count the number of negative numbers and flip the sign accordingly.

---

## Code (C++)

```cpp
class Solution {
public:
    int arraySign(vector<int>& nums) {
        int ans = 1;
        for (int i : nums) {
            if (i == 0) return 0;
            if (i < 0) ans = -ans;
        }
        return ans;
    }
};
````

---

## Time and Space Complexity

* **Time Complexity**: O(n) — one pass through the array.
* **Space Complexity**: O(1) — constant extra space used.

---

## Tags

* Array
* Math
* Simulation

---

## Author

**Himanshu**
