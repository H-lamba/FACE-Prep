
## 📘 Problem 507: Perfect Number

### ✅ Status: Solved

### 🔍 Description

A **perfect number** is a **positive integer** that is equal to the **sum of its positive divisors**, excluding itself.  
A divisor of an integer `x` is a number that divides `x` evenly (i.e., with no remainder).

Given an integer `num`, return `true` if `num` is a perfect number, otherwise return `false`.

---

### 🧠 Examples

#### Example 1:
```plaintext
Input: num = 28  
Output: true  
Explanation: 1 + 2 + 4 + 7 + 14 = 28  
````

#### Example 2:

```plaintext
Input: num = 7  
Output: false  
Explanation: The sum of divisors less than 7 is only 1.  
```

---

### 💡 Approach

* Iterate from `1` to `num - 1`
* For each number `i`, check if it divides `num` evenly
* If it does, add it to a running sum
* After the loop, compare the sum to `num`
* If equal, it’s a perfect number

---

### 🧾 Code

```cpp
class Solution {
public:
    bool checkPerfectNumber(int num) {
        int sum = 0;
        for (int i = 1; i < num; i++) {
            if (num % i == 0) {
                cout << i; // Optional: for debugging
                sum += i;
            }
        }
        cout << sum; // Optional: for debugging
        return sum == num;
    }
};
```

---

### 🛠️ Technologies Used

* Language: **C++**
* Concepts: **Mathematics**, **Divisors**

---


### ✍️ Author

* **Himanshu**
