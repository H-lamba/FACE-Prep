
### 🔍 Problem:

Given a binary tree and two nodes `p` and `q`, return their **lowest common ancestor (LCA)** — the deepest node in the tree that has both `p` and `q` as descendants.

---

## 💡 Approach

The algorithm uses a **recursive post-order traversal** to find the LCA:

### Steps:

1. **Base Case:**

   * If `root` is `NULL`, return `NULL`.
   * If `root` equals `p` or `q`, return `root`.

2. **Recursive Search:**

   * Search the left subtree for LCA of `p` and `q`.
   * Search the right subtree for LCA of `p` and `q`.

3. **Determine the LCA:**

   * If **both** left and right are non-null, then `root` is the LCA.
   * If **only one** is non-null, return that one.
   * If **none** is non-null, return `NULL`.


### Key Ideas:

1. If the current `root` is `NULL`, return `NULL`.
2. If the current `root` is either `p` or `q`, return `root`.
3. Recursively search the left and right subtrees.
4. If both left and right recursive calls return non-null values, it means `p` and `q` are found in different subtrees — hence `root` is their LCA.
5. Otherwise, return the non-null value among the left or right.

---

## Time and Space Complexity

- **Time Complexity:** O(n), where n is the number of nodes in the tree.
- **Space Complexity:** O(h), where h is the height of the tree, due to the call stack.

---

## Code

```cpp
class Solution {
public:
    TreeNode* lowestCommonAncestor(TreeNode* root, TreeNode* p, TreeNode* q) {
        if (!root || root == p || root == q)
            return root;
        
        TreeNode* left = lowestCommonAncestor(root->left, p, q);
        TreeNode* right = lowestCommonAncestor(root->right, p, q);
        
        if (left && right)
            return root;
        return left ? left : right;
    }
};
````

---

## Example

```text
        3
       / \
      5   1
     / \ / \
    6  2 0  8

Input: root = 3, p = 5, q = 1
Output: 3

Input: root = 3, p = 5, q = 4
Output: 5
```

---

## Notes

* This approach works for **any binary tree**, not just Binary Search Trees.
* If you're working with a BST, a more optimized approach using BST properties exists.

```
