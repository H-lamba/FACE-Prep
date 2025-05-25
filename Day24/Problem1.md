# Basic Calculator

## Problem Statement

Implement a basic calculator to evaluate a given string expression containing only:
- Non-negative integers
- Operators: `+` and `-`
- Parentheses: `(` and `)`
- Whitespaces

**Note:** You are **not allowed** to use built-in functions like `eval()` to evaluate the expression.

### Examples

```

Input:  s = "1 + 1"
Output: 2

Input:  s = " 2-1 + 2 "
Output: 3

Input:  s = "(1+(4+5+2)-3)+(6+8)"
Output: 23

````

---

## Approach: Stack-Based Evaluation

This solution uses a **stack-based approach** to evaluate the expression while handling operator precedence and parentheses.

### Key Concepts

1. **Operators Handled**: Only `+` and `-` are used, so precedence is straightforward.
2. **Sign Tracking**: We track the current sign using a variable (`+1` or `-1`).
3. **Parentheses Handling**:
   - On encountering `(`, push the current result and sign to the stack.
   - On encountering `)`, pop the last result and sign, and combine with the current result.

---

## Algorithm

1. **Initialize**:
   - `result = 0`
   - `sign = 1` (for `+`)
   - `stack = []`

2. **Iterate over the string**:
   - If a digit is found, parse the complete number and add it to the result with the current sign.
   - If `+` or `-` is found, update the sign accordingly.
   - If `(` is found, push the current result and sign onto the stack, then reset both.
   - If `)` is found, pop the sign and previous result from the stack, and compute the combined result.

3. **Return the final result**.

---

## C++ Implementation

```cpp
class Solution {
public:
    int calculate(string s) {
        int result = 0;
        int sign = 1;
        stack<int> stk;
        int n = s.length();
        
        for (int i = 0; i < n; ++i) {
            char c = s[i];

            if (isdigit(c)) {
                int num = 0;
                while (i < n && isdigit(s[i])) {
                    num = num * 10 + (s[i] - '0');
                    i++;
                }
                i--; // backtrack after reading the full number
                result += sign * num;
            }
            else if (c == '+') {
                sign = 1;
            }
            else if (c == '-') {
                sign = -1;
            }
            else if (c == '(') {
                stk.push(result);
                stk.push(sign);
                result = 0;
                sign = 1;
            }
            else if (c == ')') {
                int prevSign = stk.top(); stk.pop();
                int prevResult = stk.top(); stk.pop();
                result = prevResult + prevSign * result;
            }
        }

        return result;
    }
};
````

---

## Complexity Analysis

* **Time Complexity**: O(n) — each character in the string is processed once.
* **Space Complexity**: O(n) — stack holds intermediate results and signs.

---
