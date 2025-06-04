# 🌳 Sum Root to Leaf Numbers

This project contains a C++ solution to the Leetcode problem **"Sum Root to Leaf Numbers"**.

## 📘 Problem Statement

Given the `root` of a binary tree containing digits from `0–9`, each root-to-leaf path represents a number. Return the total sum of all the numbers formed by root-to-leaf paths.

### 🧾 Example:

```

Input: \[1,2,3]

```
   1
  / \
 2   3
```

Output: 25
Explanation:
Root-to-leaf paths are:

* 1→2 = 12
* 1→3 = 13
  Total = 12 + 13 = 25

```

---

## ✅ Approach: Depth-First Search (DFS) with Accumulator

We use a **recursive DFS** approach with a running sum (`currsum`) that keeps track of the number formed so far as we traverse down the tree.

### 💡 Key Logic:

1. Traverse each node from root to leaf.
2. At each step, update the current number as:
```

currsum = currsum \* 10 + node->val

````
3. When a leaf node is reached, return the number formed.
4. Sum the numbers returned by the left and right subtrees.

---

## 🔍 Code

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
 int sumNumbers(TreeNode* root, int currsum = 0) {
     if (root == nullptr) return 0;

     currsum = currsum * 10 + root->val;

     if (root->left == nullptr && root->right == nullptr)
         return currsum;

     return sumNumbers(root->left, currsum) + sumNumbers(root->right, currsum);
 }
};
````

---

## ⏱️ Time & Space Complexity

* **Time Complexity:** `O(n)`
  Each node is visited once.

* **Space Complexity:** `O(h)`
  Where `h` is the height of the tree (due to recursion stack).

---

## 🧠 Why This Works

This approach ensures that as we move down each root-to-leaf path, we keep building the number correctly using place values, and only when we hit a leaf do we add the number to the total sum.

---

## 📌 Conclusion

This DFS-based solution is clean, efficient, and elegant — leveraging recursion and default parameters to reduce boilerplate. It handles both balanced and skewed trees gracefully.

