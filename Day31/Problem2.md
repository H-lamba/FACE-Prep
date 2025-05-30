# LeetCode Problem 104: Maximum Depth of Binary Tree

## Problem Description

Given the `root` of a binary tree, return its **maximum depth**.

The **maximum depth** is defined as the number of nodes along the longest path from the **root** node down to the **farthest leaf** node.

---

### Example 1

**Input**:
```

root = \[3,9,20,null,null,15,7]

```

**Output**:
```

3

```

**Explanation**:
The maximum depth path is 3 → 20 → 15 or 3 → 20 → 7.

---

### Example 2

**Input**:
```

root = \[1,null,2]

```

**Output**:
```

2

````

---

## Approach

This solution uses a **recursive Depth-First Search (DFS)** approach to calculate the maximum depth.

### Key Idea:
For each node:
- Recursively compute the depth of the left and right subtrees.
- The depth at the current node is 1 + the maximum of the left and right subtree depths.

---

## Code

```cpp
class Solution {
public:
    int maxDepth(TreeNode* root) {
        if (root == nullptr)
            return 0;
        return 1 + max(maxDepth(root->left), maxDepth(root->right));
    }
};
````

---

## Time and Space Complexity

* **Time Complexity**: O(n), where `n` is the number of nodes in the binary tree. Each node is visited once.
* **Space Complexity**: O(h), where `h` is the height of the tree due to recursion stack. In the worst case (skewed tree), it can go up to O(n).

---

## Conclusion

This recursive DFS solution is clean and efficient for computing the maximum depth of a binary tree. It leverages the natural tree structure and recursion to traverse all paths and find the longest one.

