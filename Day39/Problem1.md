
# Insert into Binary Search Tree (Iterative Approach)

## 📌 Problem Statement

Given the `root` of a binary search tree (BST) and an integer `val`, insert the value into the BST and return the root of the updated tree. It is guaranteed that the new value does not exist in the original BST.

---

## 🚀 Approach: Iterative Method Using While Loop

### ✅ Key Concepts

- A Binary Search Tree (BST) maintains the property that:
  - Left child < Parent < Right child
- We traverse the tree starting from the root.
- At each step, we decide to move left or right depending on the value to insert.
- We stop when we find a `nullptr` (empty spot), and insert the new node there.

---

## 🧠 Algorithm Steps

1. **Create a new node** with the given value.
2. **Handle the base case**: If the tree is empty (`root == nullptr`), return the new node as the root.
3. Start from the root node and traverse using a `while(true)` loop:
   - If `val < current->val`, go to the left subtree:
     - If `current->left` is `nullptr`, insert the new node here.
   - Else, go to the right subtree:
     - If `current->right` is `nullptr`, insert the new node here.
4. Return the root node after insertion.

---

## 💻 Code Implementation

```cpp
class Solution {
public:
    TreeNode* insertIntoBST(TreeNode* root, int val) {
        TreeNode* newNode = new TreeNode(val);

        if (root == nullptr)
            return newNode;

        TreeNode* current = root;

        while (true) {
            if (val < current->val) {
                if (current->left == nullptr) {
                    current->left = newNode;
                    break;
                } else {
                    current = current->left;
                }
            } else {
                if (current->right == nullptr) {
                    current->right = newNode;
                    break;
                } else {
                    current = current->right;
                }
            }
        }

        return root;
    }
};
````

---

## 🧪 Example

Inserting `5` into the BST:

```
    4
   / \
  2   7
```

Result after insertion:

```
    4
   / \
  2   7
     /
    5
```

---

## 📈 Time and Space Complexity

* **Time Complexity:** O(h), where `h` is the height of the tree.

  * In the worst case (skewed tree), `h = n`, so complexity becomes O(n).
  * In the best/average case (balanced tree), `h = log n`, so O(log n).
* **Space Complexity:** O(1)

  * No recursion, no auxiliary stack — pure iterative method.

---

## ✅ Why Use Iterative?

* Avoids stack overflow for deep trees (unlike recursion).
* Better control over memory usage.
* Explicit flow makes it easier to debug or trace.

---

## 🛠️ Enhancements

* Can be modified to keep track of parent nodes.
* Can be extended to return the inserted node itself or the path of insertion.

---
