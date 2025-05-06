

## ✅ Problem: Plus One (LeetCode #66)

### 🧾 Description

You are given a large integer represented as an array of digits. Each element in the array represents a digit, and the digits are in order from most significant to least significant.

Increment the integer by one and return the resulting array of digits.

---

### 💡 Intuition and Approach

* Start from the **last digit** and move backward.
* If the current digit is **less than 9**, just increment it and return the result.
* If it’s **9**, set it to 0 and continue (since 9 + 1 = 10, carry the 1).
* If all digits are 9 (like `[9, 9, 9]`), you’ll end up with all 0s and a leading 1: `[1, 0, 0, 0]`.

⏱ Time Complexity: **O(n)**
📦 Space Complexity: **O(1)** (excluding the result vector if new space is required)

---

### ✅ Code (C++)

```cpp
class Solution {
public:
    vector<int> plusOne(vector<int>& digits) {
        int n = digits.size();

        // Traverse the digits from the end
        for (int i = n - 1; i >= 0; i--) {
            // If digit is less than 9, increment and return
            if (digits[i] != 9) {
                digits[i]++;
                return digits;
            }
            // Set current digit to 0 if it was 9
            digits[i] = 0;
        }

        // All digits were 9, so insert 1 at the front
        digits.insert(digits.begin(), 1);
        return digits;
    }
};
```

---

### 🔁 Example Walkthrough

#### Input: `[9, 9, 9]`

* After loop: `[0, 0, 0]`
* Insert `1` at the front → Output: `[1, 0, 0, 0]`

#### Input: `[2, 3, 9]`

* Last digit 9 → becomes 0
* Previous digit (3) < 9 → becomes 4
* Output: `[2, 4, 0]`
