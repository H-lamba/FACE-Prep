
# 🔍 Binary Search Tree (BST) Search - Recursive Approach

This project contains a C++ implementation of a recursive algorithm to search for a value in a **Binary Search Tree (BST)**. If the value exists, the function returns the subtree rooted at the node with that value; otherwise, it returns `nullptr`.

---

## 🧠 Problem Statement

Given the root node of a Binary Search Tree (BST) and an integer value `val`, return the node in the BST that has the value equal to `val`. If such a node doesn't exist, return `nullptr`.

---

## ✅ Example

### Input:
```text
       4
      / \
     2   7
    / \
   1   3
````

Search value: `2`

### Output:

```text
     2
    / \
   1   3
```

---

## 💡 Approach

This solution uses **recursion** to efficiently search the BST.

### Why This Works:

Binary Search Tree property:

* Left subtree contains nodes with values less than the current node.
* Right subtree contains nodes with values greater than the current node.

### Steps:

1. If the current node is `nullptr`, return `nullptr` (base case).
2. If `val == root->val`, return the current node.
3. If `val < root->val`, recurse into the left subtree.
4. If `val > root->val`, recurse into the right subtree.

---

## 🔁 Time and Space Complexity

* **Time Complexity:** `O(h)` where `h` is the height of the tree.

  * Worst case: `O(n)` for a skewed tree.
  * Best case: `O(log n)` for a balanced tree.
* **Space Complexity:** `O(h)` due to recursion stack.

---

## 🧩 Code

```cpp
/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode() : val(0), left(nullptr), right(nullptr) {}
 *     TreeNode(int x) : val(x), left(nullptr), right(nullptr) {}
 *     TreeNode(int x, TreeNode *left, TreeNode *right) : val(x), left(left), right(right) {}
 * };
 */
class Solution {
public:
    TreeNode* searchBST(TreeNode* root, int val) {
        if (!root || root->val == val) return root;
        if (val > root->val) return searchBST(root->right, val);
        else return searchBST(root->left, val);
    }
};
```

---

## 📌 Notes

* This is a classic example of leveraging **BST properties** to reduce search space.
* An **iterative version** can also be implemented using a loop to avoid recursion stack.

