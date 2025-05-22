# LeetCode Problem 35: Search Insert Position

## 🧠 Problem Statement

Given a **sorted array** of **distinct integers** and a `target` value, return the **index** if the target is found. If not, return the index **where it would be inserted** in order.

You must write an algorithm with **O(log n)** runtime complexity.

---

## 📥 Input

- `nums`: A list of distinct integers sorted in ascending order.
- `target`: An integer to search for or insert.

---

## 📤 Output

- The index where `target` is found, or
- The index where it should be inserted to maintain order.

---

## 🔍 Examples

### Example 1
```text
Input: nums = [1, 3, 5, 6], target = 5  
Output: 2
````

### Example 2

```text
Input: nums = [1, 3, 5, 6], target = 2  
Output: 1
```

### Example 3

```text
Input: nums = [1, 3, 5, 6], target = 7  
Output: 4
```

---

## 🛠️ Approach

We use **Binary Search** to achieve `O(log n)` time complexity:

1. Initialize `low = 0`, `high = nums.size() - 1`.
2. While `low <= high`:

   * Calculate `mid = low + (high - low) / 2`.
   * If `nums[mid] == target`, return `mid`.
   * If `nums[mid] < target`, move right: `low = mid + 1`.
   * If `nums[mid] > target`, move left: `high = mid - 1`.
3. Return `low`, which is the correct insert position.

---

## ✅ Code (C++)

```cpp
class Solution {
public:
    int searchInsert(vector<int>& nums, int target) {
        int low = 0;
        int high = nums.size() - 1;
        while (low <= high) {
            int mid = low + (high - low) / 2;
            if (nums[mid] == target) return mid;
            else if (nums[mid] < target) low = mid + 1;
            else high = mid - 1;
        }
        return low;
    }
};
```

---

## 🧮 Time and Space Complexity

* **Time Complexity**: `O(log n)` — Binary search
* **Space Complexity**: `O(1)` — Constant space

---

## 🏷️ Tags

* Binary Search
* Array

---
