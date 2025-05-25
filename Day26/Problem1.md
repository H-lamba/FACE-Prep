# 94. Binary Tree Inorder Traversal

## Problem Statement

Given the `root` of a binary tree, return the inorder traversal of its nodes' values.

**Inorder traversal** visits nodes in the following order:
1. Traverse the left subtree.
2. Visit the root node.
3. Traverse the right subtree.

### Example 1:
![image](https://github.com/user-attachments/assets/20ca9b6b-5471-452f-9a25-650bb3662fc5)

**Input:** `root = [1,null,2,3]`  
**Output:** `[1,3,2]`

### Example 2:
![image](https://github.com/user-attachments/assets/d8c94f85-a159-47b1-bc5b-4c76be0836f1)

**Input:** `root = [1,2,3,4,5,null,8,null,null,6,7,9]`  
**Output:** `[4,2,6,5,7,1,3,9,8]`

### Example 3:
**Input:** `root = []`  
**Output:** `[]`

---

## My Approach

### Language: C++

### Strategy:
I used a **recursive approach** to perform an inorder traversal. The recursive function visits each node following the "Left -> Node -> Right" pattern and appends node values to a result vector.

### Key Steps:
1. **Base Case:** If the current node is `nullptr`, return the current result vector.
2. Recursively traverse the **left** subtree.
3. **Add** the current node’s value to the result.
4. Recursively traverse the **right** subtree.

### Code:
```cpp
class Solution {
public:
    vector<int> ans;
    
    vector<int> inorderTraversal(TreeNode* root) {
        if (root == nullptr)
            return ans;
        
        inorderTraversal(root->left);
        ans.push_back(root->val);
        inorderTraversal(root->right);
        
        return ans;
    }
};
````

---

## Time and Space Complexity

* **Time Complexity:** O(n)
  Each node is visited exactly once, where `n` is the number of nodes in the binary tree.

* **Space Complexity:** O(n)
  In the worst case (skewed tree), the recursive call stack may go as deep as `n` levels. The result vector also stores `n` node values.

---

