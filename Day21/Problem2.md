# Valid Parenthesis String

## Problem Description

Given a string `s` containing only three types of characters: `'('`, `')'`, and `'*'`, return `true` if the string is **valid**.

A string is considered valid if:
1. Every `'('` has a corresponding `')'`.
2. Every `')'` has a corresponding `'('`.
3. `'('` comes before its matching `')'`.
4. The `'*'` character can be treated as:
   - A `'('`
   - A `')'`
   - An empty string `""`

---

## Examples

### Example 1:
```

Input: s = "()"
Output: true

```

### Example 2:
```

Input: s = "(\*)"
Output: true

```

### Example 3:
```

Input: s = "(\*))"
Output: true

````

---

## Approach

We use a **greedy algorithm** to track the range of possible open parentheses.

### Explanation:
- `min`: Minimum number of open parentheses we might have (assuming `'*'` acts as `')'`)
- `max`: Maximum number of open parentheses we might have (assuming `'*'` acts as `'('`)

As we iterate through the string:
- For `'('`: Increment both `min` and `max`
- For `')'`: Decrement both `min` and `max`
- For `'*'`: Decrement `min` (if `'*'` is `')'`) and increment `max` (if `'*'` is `'('`)

We reset `min` to 0 if it drops below 0 because we can't have negative open brackets.

If `max` drops below 0 at any point, it means there are too many unmatched closing brackets — return `false`.

At the end, the string is valid only if `min == 0`.

---

## Code

```cpp
class Solution {
public:
    bool checkValidString(string s) {
        int min = 0;
        int max = 0;
        for (auto i : s) {
            if (i == '(') {
                max++;
                min++;
            }
            if (i == ')') {
                max--;
                min--;
            }
            if (i == '*') {
                min--;
                max++;
            }
            if (min < 0) min = 0;
            if (max < 0) return false;
        }
        return (min == 0);
    }
};
````

---

## Time and Space Complexity

* **Time Complexity:** O(n), where n is the length of the string.
* **Space Complexity:** O(1), only a constant amount of extra space is used.

---

## Tags

* Greedy
* String
* Stack

---

## Related Problems

* 20. Valid Parentheses
* 32. Longest Valid Parentheses
