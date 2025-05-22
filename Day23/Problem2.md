# Longest Valid Parentheses

## 🧩 Problem Statement

Given a string containing just the characters `'('` and `')'`, return the length of the **longest valid (well-formed)** parentheses substring.

---

## 🧪 Examples

### Example 1:
```

Input: s = "(()"
Output: 2
Explanation: The longest valid parentheses substring is "()".

```

### Example 2:
```

Input: s = ")()())"
Output: 4
Explanation: The longest valid parentheses substring is "()()".

```

### Example 3:
```

Input: s = ""
Output: 0

````

---

## 💡 Approach: Stack-Based Solution

We use a **stack** to store indices of characters. The main idea is to keep track of unmatched parentheses and use the indices to calculate valid substring lengths.

### ✅ Steps:
1. **Initialize** a stack with `-1` (acts as a base for the first valid substring).
2. Traverse the string:
   - If you see `'('`, push its index.
   - If you see `')'`, pop from the stack:
     - If the stack becomes empty, push the current index as the new base.
     - Otherwise, calculate the current valid substring length using:
       ```
       length = current_index - top_of_stack
       ```
3. Keep track of the **maximum length** seen so far.

---

## 📦 C++ Code

```cpp
#include <iostream>
#include <stack>
#include <string>
#include <algorithm>
using namespace std;

class Solution {
public:
    int longestValidParentheses(string s) {
        stack<int> st;
        st.push(-1);  // base index
        int maxLen = 0;

        for (int i = 0; i < s.length(); ++i) {
            if (s[i] == '(') {
                st.push(i);
            } else {
                st.pop();
                if (st.empty()) {
                    st.push(i);  // reset base
                } else {
                    maxLen = max(maxLen, i - st.top());
                }
            }
        }

        return maxLen;
    }
};
````

---

## 🧠 Dry Run

Input: `")()())"`

| Index | Char | Stack           | Action                             | maxLen |
| ----- | ---- | --------------- | ---------------------------------- | ------ |
| 0     | `)`  | `[-1] -> []`    | Stack empty → push 0 as new base   | 0      |
| 1     | `(`  | `[0, 1]`        | Push index of `'('`                | 0      |
| 2     | `)`  | `[0, 1] -> [0]` | Valid match → length = `2 - 0 = 2` | 2      |
| 3     | `(`  | `[0, 3]`        | Push index of `'('`                | 2      |
| 4     | `)`  | `[0, 3] -> [0]` | Valid match → length = `4 - 0 = 4` | 4      |
| 5     | `)`  | `[0] -> []`     | Stack empty → push 5 as new base   | 4      |

---

## ⏱️ Time & Space Complexity

* **Time Complexity:** `O(n)` — One pass through the string.
* **Space Complexity:** `O(n)` — Stack space for storing indices.

---

## 🧠 Alternate Approaches

* **Dynamic Programming** — Use a dp array to track valid lengths ending at each index.
* **Two-pass Left-to-Right & Right-to-Left** — Count open and close brackets.

---

## 📌 Tags

* Stack
* Dynamic Programming
* String
* Two Pointers

---

## 🏁 Output


```cpp
int main() {
    Solution sol;
    cout << sol.longestValidParentheses(")()())") << endl;  // Output: 4
    return 0;
}
```
