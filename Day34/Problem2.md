# Flatten Binary Tree to Linked List – C++ Solution

## 🧩 Problem Statement

Given the root of a binary tree, flatten the tree into a "linked list" in-place:

* The linked list should use the **same `TreeNode` class**.
* The **right child** pointer points to the **next node** in the list.
* The **left child** pointer is always **null**.
* The linked list should follow the **pre-order traversal** of the binary tree.

---

## 🧪 Examples

### Example 1:

**Input:**
`root = [1,2,5,3,4,null,6]`
**Output:**
`[1,null,2,null,3,null,4,null,5,null,6]`

**Tree View Before:**

```
      1
     / \
    2   5
   / \    \
  3   4    6
```

**Flattened Tree (Right-Skewed Linked List):**

```
1 -> 2 -> 3 -> 4 -> 5 -> 6
```

### Example 2:

**Input:** `root = []`
**Output:** `[]`

### Example 3:

**Input:** `root = [0]`
**Output:** `[0]`

---

## 💡 Approach

This solution performs **in-place flattening** of the binary tree using an **iterative approach** that mimics pre-order traversal without using recursion or a stack.

### ✅ Steps:

1. Initialize a pointer `curr` to the root.
2. While `curr` is not null:

   * If `curr->left` exists:

     * Find the **rightmost node** (`pre`) of the left subtree.
     * Link `pre->right` to `curr->right`.
     * Move the left subtree to the right (`curr->right = curr->left`) and set `curr->left` to null.
   * Move `curr` to `curr->right`.

This ensures the left subtree is placed in between the current node and its original right subtree, maintaining pre-order order.

---

## 🔧 C++ Code

```cpp
class Solution {
public:
    void flatten(TreeNode* root) {
        TreeNode* curr = root;
        while (curr) {
            if (curr->left) {
                TreeNode* pre = curr->left;
                while (pre->right) {
                    pre = pre->right;
                }
                pre->right = curr->right;
                curr->right = curr->left;
                curr->left = nullptr;
            }
            curr = curr->right;
        }
    }
};
```

---

## ⏱️ Complexity Analysis

| Metric           | Value                                           |
| ---------------- | ----------------------------------------------- |
| Time Complexity  | `O(n)` — Each node is visited once.             |
| Space Complexity | `O(1)` — No recursion or stack used (in-place). |

---

