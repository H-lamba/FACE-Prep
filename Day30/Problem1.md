# Diameter of Binary Tree - LeetCode Problem 543

## Problem Statement

Given the `root` of a binary tree, return the **length of the diameter** of the tree.

The **diameter** of a binary tree is the length of the **longest path** between any two nodes in the tree. This path **may or may not pass through the root**.

The length is measured by the **number of edges** between the two nodes.

---

## Examples

### Example 1

```

Input: root = \[1,2,3,4,5]

```
   1
  / \
 2   3
/ \
```

4   5

Output: 3
Explanation: The longest path is \[4,2,1,3] or \[5,2,1,3], which contains 3 edges.

```

### Example 2

```

Input: root = \[1,2]

```
1
```

/
2

Output: 1

````

---

## Constraints

- The number of nodes in the tree is in the range `[1, 10^4]`.
- `-100 <= Node.val <= 100`

---

## My Approach

To solve this problem, I used a **recursive depth-first search (DFS)** approach to calculate the height of the left and right subtrees for each node.

Here’s how the solution works:

1. **Recursive Function (`height`)**:
   - This function computes the height of a node's left and right children.
   - The **height** of a node is defined as `1 + max(left height, right height)`.

2. **Tracking Diameter**:
   - At each node, I calculate `left height + right height`, which represents the number of edges in the longest path that passes through that node.
   - I maintain a global `diameter` variable and update it with the maximum value found at each node.

3. **Final Answer**:
   - After the recursive traversal, the global `diameter` variable holds the length of the longest path between any two nodes.

### Time Complexity

- **O(n)** where `n` is the number of nodes in the binary tree — each node is visited once.

### Space Complexity

- **O(h)** where `h` is the height of the tree (due to recursion stack). Worst case: `O(n)` if the tree is skewed.

---

## Code

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
    int diameter = 0;

    int height(TreeNode* root) {
        if (root == nullptr) return 0;

        int leftHeight = height(root->left);
        int rightHeight = height(root->right);

        // Update the diameter if the path through root is longer
        diameter = std::max(diameter, leftHeight + rightHeight);

        return 1 + std::max(leftHeight, rightHeight);
    }

    int diameterOfBinaryTree(TreeNode* root) {
        height(root);
        return diameter;
    }
};
````

---

## Summary

This approach efficiently computes the diameter of a binary tree using a post-order traversal pattern. It ensures each node is only visited once, making it optimal for large trees.
