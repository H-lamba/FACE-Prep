
# LeetCode Problem 832: Flipping an Image

## Problem Description

Given an `n x n` binary matrix `image`, you need to:

1. **Flip the image horizontally**: Reverse each row.
2. **Invert the image**: Replace `0` with `1` and `1` with `0`.

### Example 1

**Input**:
```

image = \[\[1,1,0],
\[1,0,1],
\[0,0,0]]

```

**Output**:
```

\[\[1,0,0],
\[0,1,0],
\[1,1,1]]

````

**Explanation**:
- Flip horizontally: `[[0,1,1],[1,0,1],[0,0,0]]`
- Invert: `[[1,0,0],[0,1,0],[1,1,1]]`

---

## Approach

This solution is implemented in C++. The algorithm involves two main steps performed **in-place**:

### Step 1: Flip Each Row Horizontally

- Use the `reverse()` function from the STL to reverse each row.
```cpp
reverse(i.begin(), i.end());
````

### Step 2: Invert the Binary Values

* Loop through each element and use a simple condition to invert:

```cpp
if (i[j] == 0)
    i[j] = 1;
else
    i[j] = 0;
```

Alternatively, this could be optimized using `i[j] ^= 1;` (XOR with 1).

---

## Code

```cpp
class Solution {
public:
    vector<vector<int>> flipAndInvertImage(vector<vector<int>>& image) {
        for (auto &i : image) {
            reverse(i.begin(), i.end());
            for (int j = 0; j < i.size(); j++) {
                if (i[j] == 0)
                    i[j] = 1;
                else
                    i[j] = 0;
            }
        }
        return image;
    }
};
```

---

## Time and Space Complexity

* **Time Complexity**: O(n × m), where `n` is the number of rows and `m` is the number of columns.
* **Space Complexity**: O(1), since the operations are performed in-place without using extra memory.

---

## Optimization Notes

* The inversion step can be shortened using XOR:

  ```cpp
  i[j] ^= 1;
  ```
