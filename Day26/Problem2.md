# 34. Find First and Last Position of Element in Sorted Array

## Problem Statement

Given an array of integers `nums` sorted in non-decreasing order, find the **starting and ending position** of a given `target` value.

If the target is not found in the array, return `[-1, -1]`.

### Constraints
- Time complexity must be **O(log n)**.
- The array may contain duplicates.

---

## My Approach

### Language: C++

### Strategy:
To satisfy the O(log n) time constraint, I used **binary search** twice:

1. **First Binary Search** to find the **first occurrence** of the target.
2. **Second Binary Search** to find the **last occurrence** of the target.

Both binary searches run in O(log n) time.

### Key Observations:
- Since the array is sorted, binary search is efficient and ensures logarithmic time complexity.
- Once we find the target, we continue searching in the **left half** for the first occurrence and the **right half** for the last occurrence.

---

## Code

```cpp
class Solution {
public:
    int first(vector<int> &arr, int target) {
        int n = arr.size();
        int low = 0, high = n - 1;
        int first = -1;
        while (low <= high) {
            int mid = low + (high - low) / 2;
            if (arr[mid] == target) {
                first = mid;
                high = mid - 1; // look on the left side
            } else if (arr[mid] > target) {
                high = mid - 1;
            } else {
                low = mid + 1;
            }
        }
        return first;
    }

    int last(vector<int> &arr, int target) {
        int n = arr.size();
        int low = 0, high = n - 1;
        int last = -1;
        while (low <= high) {
            int mid = low + (high - low) / 2;
            if (arr[mid] == target) {
                last = mid;
                low = mid + 1; // look on the right side
            } else if (arr[mid] > target) {
                high = mid - 1;
            } else {
                low = mid + 1;
            }
        }
        return last;
    }

    vector<int> searchRange(vector<int>& nums, int target) {
        int f = first(nums, target);
        if (f == -1) return {-1, -1}; // target not found
        int l = last(nums, target);
        return {f, l};
    }
};
````

---

## Time and Space Complexity

* **Time Complexity:** O(log n)
  Each binary search operation (for first and last) takes O(log n).

* **Space Complexity:** O(1)
  No additional space is used other than variables.

---

## Example Walkthroughs

### Example 1:

**Input:** `nums = [5,7,7,8,8,10]`, `target = 8`
**Output:** `[3,4]`

### Example 2:

**Input:** `nums = [5,7,7,8,8,10]`, `target = 6`
**Output:** `[-1,-1]`

### Example 3:

**Input:** `nums = []`, `target = 0`
**Output:** `[-1,-1]`

---

