# Pascal's Triangle II

## Problem Description

Given an integer `rowIndex`, return the `rowIndex`<sup>th</sup> (0-indexed) row of Pascal's Triangle.

In Pascal's Triangle, each number is the sum of the two numbers directly above it.

### Examples

#### Example 1:
```

Input: rowIndex = 3
Output: \[1, 3, 3, 1]

```

#### Example 2:
```

Input: rowIndex = 0
Output: \[1]

```

#### Example 3:
```

Input: rowIndex = 1
Output: \[1, 1]

```

---

## Approach

We use a single vector to compute the required row of Pascal's Triangle in-place. The idea is to start with a row filled with 1s and update it from the back to avoid overwriting values that are yet to be used.

### Algorithm:
1. Initialize a vector `ans` of size `rowIndex + 1` filled with 1s.
2. Iterate `i` from 2 to `rowIndex`.
3. For each `i`, update `ans[j]` from right to left using the relation:
```

ans\[j] = ans\[j] + ans\[j - 1]

````

This ensures that each element is computed using the values from the previous iteration of the row.

---

## Code

```cpp
class Solution {
public:
 vector<int> getRow(int rowIndex) {
     vector<int> ans(rowIndex + 1, 1);
     for (int i = 2; i <= rowIndex; i++) {
         for (int j = i - 1; j > 0; j--) {
             ans[j] = ans[j] + ans[j - 1];
         }
     }
     return ans;
 }
};
````

---

## Time and Space Complexity

* **Time Complexity:** O(rowIndex²)
* **Space Complexity:** O(rowIndex)

Only one vector of size `rowIndex + 1` is used to store the result in-place.

---

## Tags

* Dynamic Programming
* Math
* Pascal's Triangle
