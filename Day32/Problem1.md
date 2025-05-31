
## 📘 Rotate Image - LeetCode Problem 48

### 🧩 Problem Statement

You are given an `n x n` 2D matrix representing an image. Rotate the image **in-place** by 90 degrees clockwise.

* **Do not** allocate another 2D matrix to perform the rotation.
* Modify the input 2D matrix directly.

---

### ✅ Examples

#### Example 1:

```cpp
Input:  [[1,2,3],
         [4,5,6],
         [7,8,9]]
Output: [[7,4,1],
         [8,5,2],
         [9,6,3]]
```

#### Example 2:

```cpp
Input:  [[5,1,9,11],
         [2,4,8,10],
         [13,3,6,7],
         [15,14,12,16]]
Output: [[15,13,2,5],
         [14,3,4,1],
         [12,6,8,9],
         [16,7,10,11]]
```

---

## 🧠 Approaches Implemented

### 🟠 Approach 1: Using Extra Space (Commented Code)

> ✅ **Status:** Correct but does **not** satisfy the "in-place" constraint.

#### 🔍 Logic:

1. Reverse the entire matrix (row-wise).
2. Create a new matrix `ans`.
3. Traverse columns one by one, collect values from the reversed matrix into a new row of `ans`.
4. Assign `ans` back to `matrix`.

#### 🔄 Code:

```cpp
int n = matrix.size();
vector<vector<int>> ans;
reverse(matrix.begin(), matrix.end());
for (int j = 0; j < n; j++) {
    vector<int> temp;
    for (auto i : matrix) {
        temp.push_back(i[j]);
    }
    ans.push_back(temp);
}
matrix = ans;
```

#### 📉 Time Complexity: `O(n^2)`

#### 🗂️ Space Complexity: `O(n^2)` (Not in-place)

---

### 🟢 Approach 2: In-place Transpose + Reverse (Used in Final Code)

> ✅ **Status:** Optimal and satisfies the **in-place** constraint.

#### 🔍 Logic:

1. **Transpose the matrix**: Swap elements at `(i, j)` with `(j, i)` for all `i < j`.
2. **Reverse each row**: This results in a 90° clockwise rotation.

#### 🔄 Code:

```cpp
int n = matrix.size();
// Transpose
for (int i = 0; i < n; i++) {
    for (int j = i + 1; j < n; j++) {
        swap(matrix[i][j], matrix[j][i]);
    }
}
// Reverse each row
for (int i = 0; i < n; i++) {
    reverse(matrix[i].begin(), matrix[i].end());
}
```

#### 📉 Time Complexity: `O(n^2)`

#### 🗂️ Space Complexity: `O(1)` (In-place)

---

## 📌 Conclusion

* **Approach 1** is intuitive but not in-place.
* **Approach 2** is optimal and meets all constraints of the problem.
