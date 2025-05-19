# Leetcode 150: Evaluate Reverse Polish Notation

## 🧮 Problem Statement

You are given an array of strings `tokens` representing an arithmetic expression in **Reverse Polish Notation (RPN)**. Your task is to evaluate the expression and return the result as an integer.

- Valid operators are: `"+"`, `"-"`, `"*"`, and `"/"`.
- Each operand can be an integer or another expression.
- Division between two integers truncates toward zero.
- The expression is guaranteed to be valid and results fit within a 32-bit signed integer.

### 📘 Examples

#### Example 1:
```

Input: tokens = \["2","1","+","3","\*"]
Output: 9
Explanation: ((2 + 1) \* 3) = 9

```

#### Example 2:
```

Input: tokens = \["4","13","5","/","+"]
Output: 6
Explanation: (4 + (13 / 5)) = 6

```

#### Example 3:
```

Input: tokens = \["10","6","9","3","+","-11","*","/","*","17","+","5","+"]
Output: 22

````

---

## 🚀 My Approach

### ✅ Core Idea

The Reverse Polish Notation (RPN) is evaluated using a **stack**. Whenever we see an operand, we **push it** onto the stack. When we see an operator, we **pop the last two operands**, apply the operator, and **push the result** back onto the stack.

### ⚙️ Implementation Steps

1. Initialize an empty `stack<int>`.
2. Iterate through each token in the input:
   - If the token is an **operator** (`+`, `-`, `*`, `/`):
     - Pop the top two elements from the stack.
     - Apply the operator in **correct order**: `num2 op num1`.
     - Push the result back to the stack.
   - If the token is an **operand**:
     - Convert the string to an integer using `stoi()` and push it onto the stack.
3. After processing all tokens, the result is the only element left on the stack.

---

## 🧠 Code Explanation (C++)

```cpp
class Solution {
public:
    int evalRPN(vector<string>& tokens) {
        stack<int> st;
        for (auto& i : tokens) {
            if (i == "+" || i == "-" || i == "*" || i == "/") {
                int num1 = st.top(); st.pop();
                int num2 = st.top(); st.pop();
                if (i == "+") st.push(num2 + num1);
                else if (i == "-") st.push(num2 - num1);
                else if (i == "*") st.push(num2 * num1);
                else st.push(num2 / num1); // Division truncates toward zero
            } else {
                st.push(stoi(i)); // Convert operand string to integer
            }
        }
        return st.top();
    }
};
````

---

## 💡 Why This Works

* Stack ensures **Last-In-First-Out (LIFO)** behavior for operands.
* Integer division truncates correctly due to default C++ behavior.
* The algorithm efficiently processes each token in **O(n)** time where `n` is the number of tokens.

---

## 📊 Time and Space Complexity

* **Time Complexity:** `O(n)` — One pass through the `tokens` array.
* **Space Complexity:** `O(n)` — Stack can hold up to `n` elements in the worst case (when all are operands).

---

## 🏁 Conclusion

This approach is efficient, concise, and leverages the stack data structure to naturally solve the RPN problem. By correctly managing the order of operands and handling integer parsing, we meet all problem constraints with minimal overhead.

```
