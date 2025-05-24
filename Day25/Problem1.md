# Rotate Array - LeetCode Problem 189

This repository contains two approaches to solve the LeetCode problem [189. Rotate Array](https://leetcode.com/problems/rotate-array/), where the task is to rotate an array `nums` to the right by `k` steps.

## Problem Statement

Given an integer array `nums`, rotate the array to the right by `k` steps, where `k` is non-negative.

### Example 1
```

Input: nums = \[1,2,3,4,5,6,7], k = 3
Output: \[5,6,7,1,2,3,4]

```

### Example 2
```

Input: nums = \[-1,-100,3,99], k = 2
Output: \[3,99,-1,-100]

````

---

## Approach 1: Brute Force Using Extra Space

### Description

This method creates two temporary vectors:
- One to store the last `k` elements of the array.
- Another to store the remaining elements.

These are then merged to get the rotated array.

### Time Complexity
- **O(n)**: One pass to create subarrays, one pass to merge.

### Space Complexity
- **O(n)**: Uses extra space for two vectors.

### Code
```cpp
int movements = k % nums.size();
vector<int> ans;
vector<int> temp;

for (int i = 0; i < nums.size(); i++) {
    if (i >= nums.size() - movements)
        ans.push_back(nums[i]);
    else
        temp.push_back(nums[i]);
}

for (auto i : temp) {
    ans.push_back(i);
}

nums = ans;
````

---

## Approach 2: Optimal In-Place Reversal

### Description

This approach rotates the array in-place using three reverse operations:

1. Reverse the entire array.
2. Reverse the first `k` elements.
3. Reverse the remaining `n-k` elements.

### Time Complexity

* **O(n)**: Each reverse operation takes linear time.

### Space Complexity

* **O(1)**: Does not use extra space.

### Code

```cpp
k = k % nums.size();
reverse(nums.begin(), nums.end());
reverse(nums.begin(), nums.begin() + k);
reverse(nums.begin() + k, nums.end());
```

---

## Summary

| Approach                  | Time Complexity | Space Complexity | In-Place |
| ------------------------- | --------------- | ---------------- | -------- |
| Brute Force (Extra Space) | O(n)            | O(n)             | ❌        |
| Optimal In-Place Reversal | O(n)            | O(1)             | ✅        |

---

## Author

Solution implemented in C++ by Himanshu.

```
