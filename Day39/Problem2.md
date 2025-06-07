
# Remove All Adjacent Duplicates in String

## Problem Statement

Given a string `s`, repeatedly remove adjacent duplicate characters until no more adjacent duplicates exist. Return the final string after all such duplicate removals.

### Example

**Input:**
`s = "abbaca"`
**Output:**
`"ca"`

**Explanation:**

* Remove the first pair of adjacent `bb`, `s = "aaca"`
* Then remove the pair `aa`, `s = "ca"`

---

## Approach

This solution uses a **stack-like behavior** with a string (`result`) to efficiently remove adjacent duplicates in one pass.

### Key Idea

* Traverse each character of the input string.
* Maintain a result string that simulates a stack:

  * If the current character is the same as the top (last character) of the result, **pop** it (i.e., remove the duplicate).
  * Otherwise, **push** the character into the result.

This approach ensures that only non-adjacent duplicates remain and works in **O(n)** time and **O(n)** space complexity.

---

## Code

```cpp
class Solution {
public:
    string removeDuplicates(string s) {
        string result;
        for(char c : s) {
            if(!result.empty() && result.back() == c) {
                result.pop_back(); 
            } else {
                result.push_back(c); 
            }
        }
        return result;
    }
};
```

---

## Complexity Analysis

* **Time Complexity:** `O(n)`
  We traverse the input string once and each character is pushed and popped at most once.

* **Space Complexity:** `O(n)`
  In the worst case, the result string may grow to the size of the input string.

---
