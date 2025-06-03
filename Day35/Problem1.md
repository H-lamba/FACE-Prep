# Count Segments in a String

This C++ program implements a function to count the number of **segments** (or words) in a given string. A segment is defined as a contiguous sequence of non-space characters.

## Problem Description

Given a string `s`, return the number of segments in the string. A segment is defined to be a contiguous sequence of non-space characters.

### Example

```cpp
Input:  "   Hello   world!  "
Output: 2
````

---

## Approach

### ✅ Optimized One-Pass Solution (O(n) Time, O(1) Space)

We iterate through the string **once**, using a flag to track whether we are currently **inside a segment** or not.

### Logic

* Initialize a counter `count = 0` and a boolean flag `inSegment = false`.
* Traverse each character in the string:

  * If the character is **not a space**:

    * If `inSegment` is `false`, we have entered a new segment. Increment `count` and set `inSegment = true`.
  * If the character is a space:

    * Set `inSegment = false` because the segment has ended.
* Return the value of `count`.

### Code

```cpp
class Solution {
public:
    int countSegments(string s) {
        int count = 0;
        bool inSegment = false;

        for (char c : s) {
            if (c != ' ') {
                if (!inSegment) {
                    count++;
                    inSegment = true;
                }
            } else {
                inSegment = false;
            }
        }

        return count;
    }
};
```

### Time and Space Complexity

* **Time Complexity:** O(n) — where n is the length of the string. Each character is visited once.
* **Space Complexity:** O(1) — constant space usage, no extra memory allocation.

---

## Alternative Solutions

### Using `istringstream` (C++ Standard Library)

A more readable but slightly less performant solution:

```cpp
#include <sstream>

class Solution {
public:
    int countSegments(string s) {
        istringstream ss(s);
        string word;
        int count = 0;
        while (ss >> word) count++;
        return count;
    }
};
```

* Easier to write and understand.
* Still O(n) time, but uses more space internally.

---

## Conclusion

The provided one-pass solution is optimal in terms of both performance and memory efficiency. It avoids extra library calls and works directly on the input string using basic logic to detect segment transitions.

