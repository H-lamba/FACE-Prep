# 217. Contains Duplicate

## Problem Statement

Given an integer array `nums`, return `true` if any value appears **at least twice** in the array, and return `false` if **every element is distinct**.

### Example 1:
```

Input: nums = \[1,2,3,1]
Output: true
Explanation: The element 1 appears more than once.

```

### Example 2:
```

Input: nums = \[1,2,3,4]
Output: false
Explanation: All elements are unique.

```

### Example 3:
```

Input: nums = \[1,1,1,3,3,4,3,2,4,2]
Output: true

````

---

## Approach

We use a **hash set** (`unordered_set` in C++) to store elements as we iterate through the array:

- For each number, check if it already exists in the set.
  - If yes, return `true` (duplicate found).
  - If no, insert it into the set.
- If we reach the end of the array without finding duplicates, return `false`.

This approach ensures an efficient time complexity of **O(n)** with space complexity also **O(n)**.

---

## Code (C++)

```cpp
#include <bits/stdc++.h>
using namespace std;

class Solution {
public:
    bool containsDuplicate(vector<int>& nums) {
        unordered_set<int> seen;
        for (int num : nums) {
            if (seen.find(num) != seen.end()) {
                return true;  // Duplicate found
            }
            seen.insert(num);
        }
        return false;  // No duplicates
    }
};
````

---

## Time and Space Complexity

| Operation        | Complexity |
| ---------------- | ---------- |
| Time Complexity  | O(n)       |
| Space Complexity | O(n)       |

* `n` is the number of elements in the input array.

---

## Edge Cases

* Empty array: returns `false`
* Array with one element: returns `false`
* Array with all same elements: returns `true`

---

## Usage

You can use this class as follows:

```cpp
int main() {
    Solution sol;
    vector<int> nums = {1, 2, 3, 1};
    cout << boolalpha << sol.containsDuplicate(nums) << endl;  // Output: true
    return 0;
}
```

---

