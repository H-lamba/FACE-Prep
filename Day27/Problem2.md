
# Maximum Subarray - Kadane's Algorithm

This repository contains a solution to the classic **Maximum Subarray** problem from LeetCode, which asks to find the contiguous subarray with the largest sum within a given integer array.

## 🧠 Problem Statement

Given an integer array `nums`, find the **subarray with the largest sum**, and return its sum.

### Examples

#### Example 1:
```text
Input: nums = [-2,1,-3,4,-1,2,1,-5,4]
Output: 6
Explanation: The subarray [4,-1,2,1] has the largest sum = 6.
````

#### Example 2:

```text
Input: nums = [1]
Output: 1
```

#### Example 3:

```text
Input: nums = [5,4,-1,7,8]
Output: 23
```

---

## ✅ Approach

### Algorithm: **Kadane’s Algorithm**

The key idea is to iterate through the array and keep track of:

* A running `sum` of the current subarray.
* A global maximum `maxi` which stores the maximum sum found so far.

### Step-by-step:

1. Initialize `sum` as 0 and `maxi` as the first element of the array (to handle all-negative arrays).
2. Iterate through each element in the array:

   * Add the current element to `sum`.
   * If `sum` becomes negative, reset it to 0 (as any subarray with a negative cumulative sum won't contribute to the maximum).
   * Update `maxi` with the maximum of current `sum` and `maxi`.
3. Return `maxi` as the result.

### Code:

```cpp
class Solution {
public:
    int maxSubArray(vector<int>& nums) {
        int n = nums.size();
        int maxi = nums[0];
        int sum = 0;
        for (int i = 0; i < n; i++) {
            sum += nums[i];
            if (sum < 0) {
                maxi = max(maxi, sum);
                sum = 0;
                continue;
            }
            maxi = max(sum, maxi);
        }
        return maxi;
    }
};
```

---

## 🕒 Time & Space Complexity

* **Time Complexity:** O(n)
* **Space Complexity:** O(1)

Kadane's Algorithm provides an optimal linear time solution with constant space usage.

---

## 💡 Notes

* This solution handles both positive and negative numbers.
* The reset to 0 ensures that we discard subarrays that would reduce the sum of future subarrays.

---
