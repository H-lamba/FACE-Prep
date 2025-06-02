
# Length of Last Word – C++ Solution

## Problem Statement

Given a string `s` consisting of words and spaces, return the **length of the last word** in the string.

A **word** is defined as a maximal substring consisting of non-space characters only.

---

### Examples

**Example 1:**

```
Input:  s = "Hello World"
Output: 5
Explanation: The last word is "World" with length 5.
```

**Example 2:**

```
Input:  s = "   fly me   to   the moon  "
Output: 4
Explanation: The last word is "moon" with length 4.
```

**Example 3:**

```
Input:  s = "luffy is still joyboy"
Output: 6
Explanation: The last word is "joyboy" with length 6.
```

---

## Approach

This C++ solution efficiently calculates the length of the last word in the input string by iterating backward:

### Steps:

1. **Trim Trailing Spaces**:

   * Start from the end of the string and skip all the spaces to avoid counting empty space after the last word.

2. **Count Characters of Last Word**:

   * Iterate backwards from the last non-space character.
   * Count characters until another space is encountered or the beginning of the string is reached.

3. **Return the Count**:

   * The counter represents the length of the last word.

---

## C++ Code

```cpp
class Solution {
public:
    int lengthOfLastWord(string s) {
        int len = 0;
        int n = s.size() - 1;

        // Step 1: Skip trailing spaces
        while (n >= 0 && s[n] == ' ') {
            n--;
        }

        // Step 2: Count characters of last word
        for (int i = n; i >= 0; i--) {
            if (s[i] == ' ') return len;
            len++;
        }

        return len;
    }
};
```

---

## Time and Space Complexity

* **Time Complexity:** `O(n)` – In the worst case, we scan the entire string once from the end.
* **Space Complexity:** `O(1)` – We use a constant amount of extra space.

---

## Conclusion

This is a clean and efficient approach that avoids unnecessary splitting of the string or use of additional data structures, making it optimal for large input sizes.
