
# 🧩 First Palindromic String in an Array

This project implements a simple C++ solution to find the **first palindrome** in a given vector of strings. The solution checks each word in the list and returns the first one that reads the same forwards and backwards.

---

## 📘 Problem Statement

Given a list of strings, return the **first string** in the list that is a **palindrome**.
If no such string exists, return an empty string `""`.

---

## 🧠 Example

**Input**:

```cpp
words = {"abc", "car", "ada", "racecar", "cool"};
```

**Output**:

```
"ada"
```

---

## ✅ Approach

The solution defines a helper function `palindorm` to check whether a given string is a palindrome. It then iterates through the vector and returns the first string that satisfies the condition.

### 🔍 Steps:

1. **Palindrome Check (`palindorm`)**:

   * Use two pointers (`a` at the start, `b` at the end).
   * Move the pointers toward each other while comparing characters.
   * If all corresponding characters match, return `true`; otherwise, `false`.

2. **Main Function (`firstPalindrome`)**:

   * Iterate over each string in the input vector.
   * Call `palindorm()` on each string.
   * Return the first string where `palindorm()` returns `true`.
   * If no palindrome is found, return an empty string.

---

## 🛠️ Code Structure

* **`bool palindorm(string s)`**: Checks if the string is a palindrome.
* **`string firstPalindrome(vector<string>& words)`**: Main function that finds the first palindrome.

---

## ⏱️ Time and Space Complexity

* **Time Complexity**: `O(N * M)`,
  where `N` is the number of strings and `M` is the average length of a string (each string is checked for being a palindrome).

* **Space Complexity**: `O(1)` extra space (excluding input and output).

---

## 💡 Improvements

* The function name `palindorm` might be a typo. Consider renaming it to `isPalindrome` for clarity.
* Add edge-case handling (e.g., empty vector).

---

## ✍️ Author

Himanshu Lamba
