
# Move Zeroes (Problem 283)

## Problem Statement

Given an integer array `nums`, move all `0`'s to the end of it while maintaining the relative order of the non-zero elements.

**Note:** The goal is to do this in-place without making a copy of the array.

---

## Your Approach (With Auxiliary Vector)

### Overview

This approach solves the problem by:
1. Counting the number of zeroes in the input array.
2. Pushing all non-zero elements into a new vector.
3. Appending `count` number of zeroes at the end of the new vector.
4. Assigning the new vector back to the original one.

### C++ Code

```cpp
class Solution {
public:
    void moveZeroes(vector<int>& nums) {
        int count = 0;
        vector<int> ans;

        for (int i = 0; i < nums.size(); i++) {
            if (nums[i] == 0) {
                count++;
            } else {
                ans.push_back(nums[i]);
            }
        }

        for (int i = 0; i < count; i++) {
            ans.push_back(0);
        }

        nums = ans; // Overwrite original array with result
    }
};
````

---

## Example

**Input:**
`nums = [0, 1, 0, 3, 12]`

**Processing Steps:**

* Non-zero elements added to `ans`: `[1, 3, 12]`
* Number of zeros counted: `2`
* Final vector after adding zeros: `[1, 3, 12, 0, 0]`
* Assigned back to `nums`

**Output:**
`[1, 3, 12, 0, 0]`

---

## Complexity Analysis

* **Time Complexity:** O(n)

  * One pass to collect non-zero elements
  * One pass to append zeros
* **Space Complexity:** O(n)

  * Due to creation of the auxiliary vector `ans`

---

## Limitation

This approach **violates the in-place constraint** because it creates a new vector `ans` and reassigns it to `nums`. While it produces the correct result, it's not the most optimal solution in terms of space.

---
