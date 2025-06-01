# Lexicographically Smallest Palindrome

## Problem Statement

You are given a string `s` consisting of lowercase English letters. You are allowed to perform operations on it. In one operation, you can **replace a character in `s` with another lowercase English letter**.

Your task is to **make `s` a palindrome** with the **minimum number of operations possible**. If there are **multiple palindromes** that can be made using the minimum number of operations, return the **lexicographically smallest** one.

---

## Example

**Input:** `"egcfe"`  
**Output:** `"efcfe"`  
**Explanation:**  
- To make it a palindrome, change `'g'` to `'f'`, resulting in `"efcfe"`.
- This uses the minimum number of operations and is the lexicographically smallest among all valid palindromes.

---

## Approach

This C++ solution solves the problem using a **two-pointer** approach. Here's the logic:

1. **Initialize Two Pointers:**
   - `a` starts at the beginning (`0`)
   - `b` starts at the end (`s.size() - 1`)

2. **Loop Until the Pointers Meet:**
   - If `s[a] == s[b]`, no operation is needed; move both pointers inward.
   - If they are **not equal**, then:
     - To make them equal with **minimum change** and get the **smallest lexicographic result**, set the **larger character** to the **smaller one**.
       - i.e., if `s[a] < s[b]`, assign `s[b] = s[a]`
       - else assign `s[a] = s[b]`

3. **Return the Modified String**

---

## Code

```cpp
class Solution {
public:
    string makeSmallestPalindrome(string s) {
        int a = 0; 
        int b = s.size()-1;
        while(a < b) {
            if(s[a] != s[b]) {
                if(s[a] < s[b])
                    s[b] = s[a];
                else
                    s[a] = s[b];
            }
            a++;
            b--;
        }
        return s;
    }
};
````

---

## Time and Space Complexity

* **Time Complexity:** `O(n)`
  Each character is visited at most once from both ends.

* **Space Complexity:** `O(1)`
  The string is modified in place without using any extra space.

---

## Key Concepts Used

* Two-pointer technique
* Palindrome construction
* Lexicographic string comparison
* In-place string manipulation

---

## Notes

* Lexicographically smaller means appearing earlier in the dictionary.
* The approach ensures **minimum operations** and the **smallest lexicographical** result by always copying the smaller character.

---

## Related Topics

* String
* Greedy
* Two Pointers

