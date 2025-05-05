## 📘 Problem 202: Happy Number

### ✅ Status: Solved

### 🔍 Description

A **happy number** is defined by the following process:

1. Starting with any positive integer, replace the number with the **sum of the squares of its digits**.
2. Repeat the process until the number equals `1` (where it will stay), or **it loops endlessly in a cycle** that does not include `1`.
3. A number is happy **if it ends in 1** after repeating the process.

Return `true` if `n` is a happy number, otherwise return `false`.

---

### 🧠 Examples

#### Example 1:
```plaintext
Input: n = 19  
Output: true  
Explanation:  
1² + 9² = 82  
8² + 2² = 68  
6² + 8² = 100  
1² + 0² + 0² = 1
````

#### Example 2:

```plaintext
Input: n = 2  
Output: false  
Explanation: Loops infinitely and never reaches 1.
```

---

### 💡 Approach

* Use a `set` to keep track of previously seen values to detect cycles.
* In each iteration, compute the **sum of the squares of digits**.
* If you reach 1, return `true`.
* If a value repeats (cycle), return `false`.

✅ Time Complexity: `O(log n)` per iteration (for digit-sum computation)
✅ Space Complexity: `O(n)` for the `unordered_set`

---

### 🧾 Code

```cpp
class Solution {
public:
    bool isHappy(int n) {
        if (n < 0) return false;

        unordered_set<int> seen;
        int sum = n;

        while (sum != 1 && seen.find(n) == seen.end()) {
            seen.insert(sum);
            sum = 0;

            while (n > 0) {
                sum += (n % 10) * (n % 10);
                n = n / 10;
            }

            n = sum;
        }

        return n == 1;
    }
};
```

---

### 🛠️ Technologies Used

* Language: **C++**
* Concepts: **HashSet**, **Cycle Detection**, **Mathematical Simulation**

---

### 📁 How to Use

1. Compile the code using a C++ compiler.
2. Create an instance of `Solution` and call `isHappy(n)` with any positive integer.

---
* **Himanshu**
