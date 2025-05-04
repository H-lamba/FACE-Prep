
# Palindrome Number - LeetCode Problem 9

## ✅ Problem Status: Solved

### 📘 Problem Description

Given an integer `x`, return `true` if `x` is a **palindrome**, and `false` otherwise.

A palindrome is a number that reads the same backward as forward.

---

### 🧠 Examples

#### Example 1:
```plaintext
Input: x = 121  
Output: true  
Explanation: 121 reads the same forward and backward.
````

#### Example 2:

```plaintext
Input: x = -121  
Output: false  
Explanation: From left to right, it reads -121. From right to left, it becomes 121-. Not a palindrome.
```

#### Example 3:

```plaintext
Input: x = 10  
Output: false  
Explanation: Reads 01 from right to left. Not a palindrome.
```

---

### 💡 Approach

* Negative numbers are immediately discarded.
* Each digit of the number is extracted and stored in both a `stack` and a `queue`.
* The number is compared from front (using `queue`) and back (using `stack`).
* If all digits match from both ends, the number is a palindrome.

---

### 🧾 Code

```cpp
class Solution {
public:
    bool isPalindrome(int x) {
        if (x < 0) return false;
        stack<int> q;
        queue<int> s;
        while (x != 0) {
            s.push(x % 10);
            q.push(x % 10);
            x = x / 10;
        }
        while (!q.empty()) {
            if (q.top() != s.front())
                return false;
            q.pop();
            s.pop();
        }
        return true;
    }
};
```

---

### 🛠️ Technologies Used

* Language: **C++**
* Concepts: **Stacks**, **Queues**, **Mathematics**

---

### ✍️ Author

* **Himanshu**
