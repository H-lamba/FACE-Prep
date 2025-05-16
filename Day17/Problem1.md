# Two Sum - C++ Solution

## Problem Statement

Given an array of integers `nums` and an integer `target`, return **indices** of the **two numbers** such that they add up to `target`.

You **may assume** that each input would have **exactly one solution**, and you **may not use** the same element twice.

You can return the answer in **any order**.

---

## Example

### Example 1:

```
Input:  nums = [2,7,11,15], target = 9  
Output: [0,1]  
Explanation: nums[0] + nums[1] == 9
```

### Example 2:

```
Input:  nums = [3,2,4], target = 6  
Output: [1,2]
```

### Example 3:

```
Input:  nums = [3,3], target = 6  
Output: [0,1]
```

---

## Approach

This solution uses a **hash map** (implemented using `unordered_map` in C++) to store previously seen numbers and their indices. The goal is to find, for each number, if the **complement** (i.e., `target - num`) exists in the map.

### Time Complexity:

* **O(n)** — where `n` is the number of elements in the array.

### Space Complexity:

* **O(n)** — for storing elements in the hash map.

---

## Code

```cpp
class Solution {
public:
    vector<int> twoSum(vector<int>& nums, int target) {
        unordered_map<int, int> mp;
        int n = nums.size();
        for (int i = 0; i < n; i++) { 
            int num = nums[i];
            int remain = target - num;
            if (mp.find(remain) != mp.end()) {
                return {mp[remain], i};
            }
            mp[num] = i;
        }
        return {-1, -1}; 
    }
};
```

---

## Notes

* Make sure to use `i < n` in the `for` loop instead of `i <= n` to avoid out-of-bounds errors.
* The `unordered_map` ensures constant-time lookups for checking if the complement exists.

