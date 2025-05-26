
# Path Sum – Binary Tree

This project solves the classic **Path Sum** problem using a recursive depth-first search approach in C++.

---

## 🧠 Problem Statement

Given the `root` of a binary tree and an integer `targetSum`, return `true` if the tree has a **root-to-leaf path** such that adding up all the values along the path equals `targetSum`.

A **leaf** is a node with no children.

---

## ✅ Approach (Recursive DFS)

The algorithm performs a **depth-first search (DFS)** from the root down to the leaf nodes while tracking the remaining sum needed. 

### 🔍 Steps:

1. **Base Case**:
   - If the node is `nullptr`, return `false`.
2. **Update Target**:
   - Subtract the current node’s value from `targetSum`.
3. **Check for Leaf Node**:
   - If it’s a leaf (no left or right child), return `true` if `targetSum == 0`.
4. **Recursive Calls**:
   - Recur on the left and right subtrees.
   - Return `true` if either subtree returns `true`.

---

## 💻 C++ Code

```cpp
class Solution {
public:
    bool hasPathSum(TreeNode* root, int targetSum) { 
        if (!root) return false;

        targetSum -= root->val;

        cout << "At node " << root->val << ", remaining sum: " << targetSum << endl;

        if (!root->left && !root->right) {
            return targetSum == 0;
        }

        return hasPathSum(root->left, targetSum) || hasPathSum(root->right, targetSum);
    }
};
````

---

## 📝 Dry Run Example

### Tree:

```
       5
      / \
     4   8
    /   / \
   11 13  4
  /  \
 7    2
```

### Target Sum: `22`

### Traversal:

1. Start at node `5`:
   `targetSum = 22 - 5 = 17`

2. Move to node `4`:
   `targetSum = 17 - 4 = 13`

3. Move to node `11`:
   `targetSum = 13 - 11 = 2`

4. Move to node `7`:
   `targetSum = 2 - 7 = -5` (not a valid path)

5. Backtrack and move to node `2`:
   `targetSum = 2 - 2 = 0` ✅
   It's a **leaf node**, and `targetSum == 0` → **return true**

### Final Result: `true` ✅

---

## 📦 Time & Space Complexity

* **Time Complexity**: `O(n)` where `n` is the number of nodes (visit each node once)
* **Space Complexity**: `O(h)` where `h` is the height of the tree (due to recursion stack)

---

## 📌 Notes

* The `cout` line is used for debugging and can be removed.
