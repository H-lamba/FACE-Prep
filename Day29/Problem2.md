# 📊 Kth Largest Element in an Array

This repository contains a C++ solution to the problem **"215. Kth Largest Element in an Array"** from LeetCode.

---

## 🧩 Problem Statement

Given an integer array `nums` and an integer `k`, return the **kth largest element** in the array.

> Note: It is the kth largest element in **sorted order**, not the kth distinct element.

---

## 🧪 Examples

### Example 1
**Input:**
```cpp
nums = [3, 2, 1, 5, 6, 4], k = 2
````

**Output:**

```
5
```

### Example 2

**Input:**

```cpp
nums = [3, 2, 3, 1, 2, 4, 5, 5, 6], k = 4
```

**Output:**

```
4
```

---

## 💡 Approach

This solution uses **sorting** to solve the problem in a straightforward way:

1. Sort the input array `nums` in **ascending order**.
2. The kth largest element will be at the index `nums.size() - k`.

### Why It Works

* Sorting arranges the elements in increasing order, so the largest element will be at the last index.
* The kth largest element is simply `nums[nums.size() - k]`.

### 🔧 Code

```cpp
class Solution {
public:
    int findKthLargest(vector<int>& nums, int k) {
        sort(nums.begin(), nums.end());
        return nums[nums.size() - k];
    }
};
```

---

## ⏱️ Time and Space Complexity

| Metric           | Complexity           |
| ---------------- | -------------------- |
| Time Complexity  | O(n log n)           |
| Space Complexity | O(1) (in-place sort) |

---

## ✅ Can This Be Improved?

Yes! The problem can also be solved in **O(n)** average time using:

* **Min-Heap** of size `k`, or
* **Quickselect** algorithm (based on QuickSort partitioning).

However, this solution is easy to implement and works well for moderate-sized arrays.

---

