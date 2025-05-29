
# Find the Duplicate Number - LeetCode Problem 287

## Problem Statement

Given an array of integers `nums` containing `n + 1` integers where each integer is in the range `[1, n]` (inclusive), **there is only one repeated number**, return this repeated number.

You **must solve the problem**:

- Without modifying the input array `nums`.
- Using only **constant extra space**.

---

## Examples

### Example 1
```

Input: nums = \[1,3,4,2,2]
Output: 2

```

### Example 2
```

Input: nums = \[3,1,3,4,2]
Output: 3

```

### Example 3
```

Input: nums = \[3,3,3,3,3]
Output: 3

````

---

## Constraints

- `1 <= n <= 10^5`
- `nums.length == n + 1`
- `1 <= nums[i] <= n`
- There is only **one repeated number**, but it could be repeated more than once.

---

## My Approaches

### ✅ Approach 1: Brute Force (Nested Loop) — ❌ Not Optimal

```cpp
for (int i = 0; i < nums.size(); i++) {
    for (int j = i + 1; j < nums.size(); j++) {
        if (nums[i] == nums[j])
            return nums[i];
    }
}
````

* **Time Complexity**: O(n²)
* **Space Complexity**: O(1)
* **Why it fails**: This is straightforward but extremely inefficient for large inputs (can lead to TLE — Time Limit Exceeded).

---

### ✅ Approach 2: Sorting Based 
```cpp
sort(nums.begin(), nums.end());
for (int i = 0; i < nums.size() - 1; i++) {
    if (nums[i] == nums[i + 1])
        return nums[i];
}
```

* **Time Complexity**: O(n log n)
* **Space Complexity**: Depends on sorting implementation (can be O(log n))
* **Why I used this**:

  * It’s **much more efficient** than the brute-force solution.
  * Easy to implement and **works well on small to medium-sized datasets**.
  * While it does modify the array (via `sort()`), it helped me get a correct and quick solution during practice.
---

## Summary

| Approach        | Time Complexity | Space Complexity | Constraint-Compliant | Notes                               |
| --------------- | --------------- | ---------------- | -------------------- | ----------------------------------- |
| Brute Force     | O(n²)           | O(1)             | ✅ Yes                | Too slow for large inputs           |
| Sorting         | O(n log n)      | O(1)/O(log n)    | ❌ No                 | Fast and simple, but modifies input |
