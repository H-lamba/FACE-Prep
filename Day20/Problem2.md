# 🧮 Find Greatest Common Divisor of Array

## Problem Statement

Given an integer array `nums`, return the **greatest common divisor (GCD)** of the **smallest number** and **largest number** in `nums`.

> The **greatest common divisor** of two numbers is the largest positive integer that evenly divides both numbers.

### Examples

#### Example 1:

```
Input:  nums = [2, 5, 6, 9, 10]
Output: 2
Explanation: The smallest number is 2, the largest is 10, and gcd(2, 10) = 2.
```

#### Example 2:

```
Input:  nums = [7, 5, 6, 8, 3]
Output: 1
Explanation: The smallest number is 3, the largest is 8, and gcd(3, 8) = 1.
```

#### Example 3:

```
Input:  nums = [3, 3]
Output: 3
Explanation: The smallest and largest number is 3, and gcd(3, 3) = 3.
```

---

## ✅ Approach

1. **Sort the Array**:

   * First, the array is sorted in ascending order to easily access the smallest and largest elements.
   * `nums[0]` gives the smallest, and `nums[n-1]` gives the largest number.

2. **Calculate GCD**:

   * The GCD is calculated using the **Euclidean algorithm**, which repeatedly replaces the larger number with the remainder of dividing the two until the remainder becomes zero.
   * This is implemented in the `gcd(int a, int b)` function.

3. **Return the GCD**:

   * The final GCD value between the smallest and largest number is returned.

---

## 💻 Code

```cpp
class Solution {
public:
    int gcd(int a, int b) {
        while (b != 0) {
            int temp = b;
            b = a % b;
            a = temp;
        }
        return a;
    }

    int findGCD(vector<int>& nums) {
        sort(nums.begin(), nums.end());
        int n = nums.size();
        return gcd(nums[0], nums[n - 1]);
    }
};
```

---

## 🧠 Time & Space Complexity

* **Time Complexity**:

  * Sorting: `O(n log n)`
  * GCD (Euclidean Algorithm): `O(log(min(a, b)))`
  * Overall: `O(n log n)`

* **Space Complexity**:

  * `O(1)` (in-place sorting and constant extra space)

---

## 📌 Notes

* The solution is straightforward due to the limited scope — we only care about the smallest and largest numbers.
* An optimization could be to find the min and max values manually in a single loop instead of sorting the entire array (to improve to `O(n)` time). However, the current implementation is clear and easy to understand.

---
