
# LeetCode 1249 - Minimum Remove to Make Valid Parentheses

## Problem Statement

Given a string `s` consisting of `'('`, `')'`, and lowercase English characters, remove the minimum number of parentheses so that the resulting string is valid. A valid string is:

- Empty, or
- Contains only lowercase characters, or
- Can be written as a concatenation of valid strings, or
- Can be enclosed in parentheses `()` around a valid string

---

## Example

**Input:**  
`s = "a)b(c)d"`

**Output:**  
`"ab(c)d"`

---

## My Initial Approach

I used a `stack<pair<int, char>>` to track both the **index** and **character** of unmatched parentheses. After parsing the string:

1. I collected all unmatched parentheses' indices in a vector.
2. I sorted the vector of indices.
3. Finally, I reconstructed the string by skipping characters at those indices.

### Code (Initial Approach)
```cpp
class Solution {
public:
    string minRemoveToMakeValid(string s) {
        stack<pair<int,char>> st;
        for(int i = 0; i < s.size(); i++) {
            if(s[i] == '(') st.push({i, s[i]});
            else if(s[i] == ')') {
                if(!st.empty() && st.top().second == '(') st.pop();
                else st.push({i, s[i]});
            }
        }

        vector<int> indices;
        while(!st.empty()) {
            indices.push_back(st.top().first);
            st.pop();
        }

        sort(indices.begin(), indices.end());

        string ans = "";
        int idx = 0;
        for(int i = 0; i < s.size(); i++) {
            if(idx < indices.size() && indices[idx] == i) {
                idx++;
            } else {
                ans += s[i];
            }
        }

        return ans;
    }
};
````

---

## Disadvantages of My Approach

* **High Memory Usage:** Storing both index and character in the stack consumes more memory than needed.
* **Extra Sorting:** Using a vector and then sorting it adds extra `O(n log n)` time and space.
* **Can Cause MLE:** On large inputs (e.g., `s.size() > 10^5`), the memory footprint may exceed the limit.

---

## Optimized Solution

To improve performance and reduce memory, the following changes were made:

* Use a `stack<int>` to store **only indices**.
* Use an `unordered_set<int>` for constant-time lookup of unmatched parentheses.
* Avoid sorting altogether.
* Optionally use `string::reserve()` to preallocate memory.

### Code (Optimized Approach)

```cpp
class Solution {
public:
    string minRemoveToMakeValid(string s) {
        stack<int> st;
        unordered_set<int> toRemove;

        for (int i = 0; i < s.size(); i++) {
            if (s[i] == '(') {
                st.push(i);
            } else if (s[i] == ')') {
                if (!st.empty() && s[st.top()] == '(') {
                    st.pop();
                } else {
                    toRemove.insert(i);
                }
            }
        }

        while (!st.empty()) {
            toRemove.insert(st.top());
            st.pop();
        }

        string ans;
        ans.reserve(s.size());
        for (int i = 0; i < s.size(); i++) {
            if (toRemove.find(i) == toRemove.end()) {
                ans += s[i];
            }
        }

        return ans;
    }
};
```

---

## Time and Space Complexity

| Metric           | Value |
| ---------------- | ----- |
| Time Complexity  | O(n)  |
| Space Complexity | O(n)  |

* One pass to detect unmatched parentheses
* One pass to construct result
* No sorting required
* Memory optimized using `stack<int>` and `unordered_set`

---

## Conclusion

The optimized solution is faster and more memory-efficient than the initial implementation. It avoids unnecessary data storage and operations while maintaining clarity and correctness.
