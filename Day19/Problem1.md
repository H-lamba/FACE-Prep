
# 🧩 LeetCode Problem 20: Valid Parentheses

## 🚀 Problem Statement

Given a string `s` containing just the characters `'('`, `')'`, `'{'`, `'}'`, `'['`, and `']'`, determine if the input string is **valid**.

An input string is valid if:

- Open brackets must be closed by the same type of brackets.
- Open brackets must be closed in the correct order.
- Every closing bracket has a corresponding open bracket of the same type.

---

## 🧠 Examples

### ✅ Example 1:
**Input:**  
`s = "()"`  
**Output:**  
`true`

### ✅ Example 2:
**Input:**  
`s = "()[]{}"`  
**Output:**  
`true`

### ❌ Example 3:
**Input:**  
`s = "(]"`  
**Output:**  
`false`

### ✅ Example 4:
**Input:**  
`s = "([])"`  
**Output:**  
`true`

---

## 💡 Approach

We use a **stack** to keep track of opening brackets. For each character in the string:
- If it's an opening bracket (`'('`, `'{'`, `'['`), we push it to the stack.
- If it's a closing bracket:
  - If the stack is empty, it's invalid.
  - Otherwise, we check if the top of the stack matches the corresponding opening bracket. If it does, we pop it; otherwise, it's invalid.

Finally, we check if the stack is empty:
- If it is, the string is valid.
- If not, it means there are unmatched opening brackets.

---

## 🧾 Code

```cpp
class Solution {
public:
    bool isValid(string s) {
        stack<char> st;
        for (char c : s) {
            if (c == '(' || c == '{' || c == '[')
                st.push(c);
            else {
                if (st.empty()) return false;
                if ((st.top() == '(' && c == ')') ||
                    (st.top() == '[' && c == ']') ||
                    (st.top() == '{' && c == '}')) {
                    st.pop();
                } else {
                    return false;
                }
            }
        }
        return st.empty();
    }
};
````

---

## 🛠️ Time and Space Complexity

* **Time Complexity:** O(n), where `n` is the length of the input string.
* **Space Complexity:** O(n), for the stack used to store opening brackets.

---

## 📚 Topics

* Stack
* String
* Simulation

