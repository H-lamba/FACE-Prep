
# Insert into Binary Search Tree (BST)

## 📌 Problem Statement

Given the `root` of a binary search tree (BST) and an integer `val`, insert the value into the BST and return the root of the updated tree. The new value is guaranteed to be unique (not already present in the BST).

---

## 🌳 What is a Binary Search Tree?

A **Binary Search Tree (BST)** is a binary tree where each node follows these rules:

- The value of every node in the **left subtree** is **less than** the node's value.
- The value of every node in the **right subtree** is **greater than** the node's value.

---

## 🧠 Two Approaches

We can solve this problem using:

1. ✅ Recursive Approach  
2. ✅ Iterative Approach (using `while` loop)

---

## 🔁 1. Recursive Approach

### 📌 Idea

We use the **call stack** to traverse the tree. At each recursive step:
- If the node is `nullptr`, insert the new value there.
- Otherwise, recurse into the left or right subtree based on the comparison.

### 💻 Code

```cpp
class Solution {
public:
    TreeNode* insertIntoBST(TreeNode* root, int val) {
        if (root == nullptr)
            return new TreeNode(val);  // base case: insert here

        if (val < root->val)
            root->left = insertIntoBST(root->left, val);
        else
            root->right = insertIntoBST(root->right, val);

        return root;
    }
};
````

### 📈 Time and Space Complexity

* **Time:** O(h), where h is the height of the tree.
* **Space:** O(h) due to recursive call stack.

---

## 🔁 2. Iterative Approach

### 📌 Idea

We simulate the recursion using a loop. Traverse the tree using a pointer until you find an empty left or right spot, then insert the new node there.

### 💻 Code

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
                }
                current = current->left;
            } else {
                if (current->right == nullptr) {
                    current->right = newNode;
                    break;
                }
                current = current->right;
            }
        }

        return root;
    }
};
```

### 📈 Time and Space Complexity

* **Time:** O(h)
* **Space:** O(1) (no recursion)

---

## 🔍 Example

Insert `5` into this BST:

```
    4
   / \
  2   7
```

After insertion:

```
    4
   / \
  2   7
     /
    5
```

---

## 🆚 Comparison

| Feature         | Recursive                    | Iterative                    |
| --------------- | ---------------------------- | ---------------------------- |
| Code Simplicity | Short and elegant            | Slightly longer, more manual |
| Stack Usage     | Uses call stack (O(h) space) | Constant space (O(1))        |
| Risk            | Stack overflow in deep trees | No stack overflow risk       |
| Performance     | Same time complexity (O(h))  | Same, but can save space     |

---

## 🧑‍💻 Author

* **Himanshu Lamba**
* Part of the **#DrGVishwanathan 50 Days Coding Challenge**
* Topic: Binary Search Tree Insertion – Recursive & Iterative Solutions

---
