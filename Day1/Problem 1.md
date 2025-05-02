
# Missing Number - LeetCode Problem 268

This repository contains a solution to the LeetCode problem **[268. Missing Number](https://leetcode.com/problems/missing-number/)** using C++.

## Problem Description

Given an array `nums` containing `n` distinct numbers in the range `[0, n]`, return the only number in the range that is missing from the array.

### Example 1:
```
Input: nums = [3,0,1]  
Output: 2  
Explanation: n = 3, so the range is [0, 3]. 2 is missing.
```

### Example 2:
```
Input: nums = [0,1]  
Output: 2  
Explanation: n = 2, so the range is [0, 2]. 2 is missing.
```

### Example 3:
```
Input: nums = [9,6,4,2,3,5,7,0,1]  
Output: 8  
Explanation: n = 9, so the range is [0, 9]. 8 is missing.
```

---

## Approach

This solution uses the **sum formula for the first n natural numbers**.  

The expected sum of numbers from 0 to n is:
```
expected = n * (n + 1) / 2
```

We subtract the actual sum of elements in the array from the expected sum to find the missing number.

---

## Solution Code (C++)

```cpp
class Solution {
public:
    int missingNumber(vector<int>& nums) {
        int n = nums.size();
        int expected = n * (n + 1) / 2;
        int actual = 0;
        for(int i = 0; i < n; i++) {
            actual += nums[i];
        }
        return expected - actual;
    }
};
```

---

## Time and Space Complexity

- **Time Complexity:** O(n) — One pass through the array.
- **Space Complexity:** O(1) — No extra space used apart from variables.

---

Himanshu  
Feel free to fork or contribute!

---
