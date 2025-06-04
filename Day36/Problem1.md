
# Reverse Vowels of a String

This project provides a C++ solution to the problem **"Reverse Vowels of a String"**, where we reverse only the vowels in a given string while keeping the positions of the other characters unchanged.

## 🧠 Problem Statement

Given a string `s`, reverse only the vowels of the string and return it.

**Example:**

```

Input:  s = "leetcode"
Output: "leotcede"

````

---

## ✅ Approach: Two Pointer Technique

We use a **two-pointer approach** to traverse the string from both ends and swap the vowels.

### 👨‍💻 Steps:
1. Initialize two pointers:
   - `a` at the start of the string.
   - `b` at the end of the string.
2. Move both pointers towards each other:
   - If `s[a]` is a vowel and `s[b]` is a vowel, swap them.
   - If `s[a]` is not a vowel, increment `a`.
   - If `s[b]` is not a vowel, decrement `b`.
3. Continue until `a >= b`.

### 💡 Vowel Check
We manually check if a character is a vowel by comparing it against both lowercase and uppercase vowel characters:  
`a, e, i, o, u` and `A, E, I, O, U`.

---

## 🧾 Code

```cpp
class Solution {
public:
    string reverseVowels(string s) {
        int b = s.size() - 1;
        int a = 0;
        while (a < b) {
            if (isVowel(s[a])) {
                if (isVowel(s[b])) {
                    swap(s[a], s[b]);
                    a++;
                    b--;
                } else {
                    b--;
                }
            } else {
                a++;
            }
        }
        return s;
    }

    bool isVowel(char c) {
        return c == 'a' || c == 'e' || c == 'i' || c == 'o' || c == 'u' ||
               c == 'A' || c == 'E' || c == 'I' || c == 'O' || c == 'U';
    }
};
````

---

## ⏱️ Time and Space Complexity

* **Time Complexity:** `O(n)`
  We traverse the string once using two pointers.

* **Space Complexity:** `O(1)`
  No extra space is used apart from variables.

---


## 📌 Conclusion

This solution efficiently reverses the vowels in a string using the two-pointer approach and constant space, making it suitable for performance-critical applications.

