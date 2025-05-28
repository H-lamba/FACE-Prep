# 🌿 Sum of Left Leaves in a Binary Tree

This project provides a C++ solution to the problem of finding the **sum of all left leaves** in a given binary tree. A **left leaf** is defined as a leaf node that is the **left child** of its parent.

---

## 📘 Problem Statement

Given the root of a binary tree, return the sum of all **left leaves**.

- A **leaf** is a node with no children.
- A **left leaf** is a leaf node that is the left child of another node.

---

## 🧪 Example

### Input
```

```
  3
 / \
9  20
   / \
  15  7
```

```

**Input Array**: `[3,9,20,null,null,15,7]`

### Output
```

24

````

### Explanation
There are two left leaves:
- `9` is a left leaf of `3`
- `15` is a left leaf of `20`

Sum = 9 + 15 = **24**

---

## 💡 Approach

The solution uses **recursive traversal**:

- At each node, check if the **left child is a leaf** (i.e., has no children).
  - If yes, add its value to the result.
- Recursively call the function on both left and right children.

---

## 🔧 Code

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
    int sumOfLeftLeaves(TreeNode* root) {
        if (root == nullptr) return 0;
        
        int sum = 0;
        
        // Check if left child is a leaf
        if (root->left && !root->left->left && !root->left->right) {
            sum += root->left->val;
        } else {
            sum += sumOfLeftLeaves(root->left);
        }
        
        sum += sumOfLeftLeaves(root->right);
        
        return sum;
    }
};
````

---

## 🧠 Time and Space Complexity

* **Time Complexity**: O(n), where `n` is the number of nodes in the tree (each node is visited once).
* **Space Complexity**: O(h), where `h` is the height of the tree (due to recursion stack).
---

## 🔖 Tags

`Binary Tree` | `DFS` | `Recursion`

