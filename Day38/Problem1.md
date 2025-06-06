# Valid Palindrome Checker

This C++ program checks whether a given string is a **valid palindrome**, considering only alphanumeric characters and ignoring cases.

## Problem Statement

Given a string `s`, determine if it is a palindrome, considering only alphanumeric characters and ignoring cases.

### Example
```text
Input: "A man, a plan, a canal: Panama"
Output: true

Input: "race a car"
Output: false
````

## Approach

The solution uses a **two-pointer technique** to check for palindrome validity efficiently.

### Key Concepts Used:

* **Two-pointer method**: One pointer starts from the beginning (`a`), and the other from the end (`b`) of the string.
* **Character validation**: Non-alphanumeric characters are skipped using `isalnum()` function.
* **Case insensitivity**: Characters are converted to lowercase using `tolower()` before comparison.

### Step-by-step Logic:

1. Initialize two pointers: `a = 0` (start) and `b = s.size() - 1` (end).
2. While `a < b`:

   * Skip non-alphanumeric characters using `isalnum()`.
   * Convert both characters to lowercase and compare:

     * If they don’t match, return `false`.
     * If they match, move both pointers inward.
3. If all corresponding characters match, return `true`.

### Time and Space Complexity

* **Time Complexity**: `O(n)`, where `n` is the length of the string.
* **Space Complexity**: `O(1)`, since the comparison is done in-place without using any extra memory.

## Code

```cpp
class Solution {
public:
    bool isPalindrome(string s) {
        int a  = 0;
        int b = s.size()-1;
        while(a<b)
        {
            if(!isalnum(s[a])) 
            {
                a++;
                continue;
            }
            if(!isalnum(s[b])) 
            {
                b--;
                continue;
            }
            if(tolower(s[a])!=tolower(s[b])) return false;
            a++;
            b--;
        }
        return true;
    }
};
```

## Usage

This function can be used in any C++ environment. Simply call `isPalindrome(s)` where `s` is the input string.

---

### Author

Himanshu Lamba

```

