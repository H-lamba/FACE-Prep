
# Zigzag Level Order Traversal of a Binary Tree

This project contains a C++ implementation of the **Zigzag Level Order Traversal** algorithm for a binary tree using Breadth-First Search (BFS). This type of traversal alternates between left-to-right and right-to-left at each level of the tree.

---

## 🧠 Problem Description

Given the `root` of a binary tree, return the zigzag level order traversal of its nodes' values.
(i.e., from left to right, then right to left for the next level, and alternate between).

---

## 📘 Example

Input Tree:

```
        1
       / \
      2   3
     / \   \
    4   5   6
```

Output:

```
[
 [1],
 [3,2],
 [4,5,6]
]
```

---

## ✅ Approach

This solution uses **Breadth-First Search (BFS)** with a `queue` to process each level of the tree. A `string` flag (`"left"` or `"right"`) is used to determine the direction of traversal for each level.

### Steps:

1. **Base Case**: If the root is null, return an empty result.
2. **Queue Initialization**: Use a queue to hold nodes of the current level.
3. **Level-wise Processing**:

   * Extract all nodes at the current level.
   * Store their values in a temporary vector.
   * Enqueue the child nodes for the next level.
4. **Direction Check**:

   * If the direction is `"right"`, reverse the temporary vector.
   * Alternate the direction after each level.
5. **Store Results**: Append the level vector to the final result.

---

## 🛠️ Code Structure

* **TreeNode Structure**: Defines a basic binary tree node.
* **Solution Class**:

  * `zigzagLevelOrder(TreeNode* root)`: Main function that returns the zigzag traversal.

---

## 📦 Data Structures Used

* `vector<vector<int>>` – To store the final output.
* `queue<TreeNode*>` – For BFS traversal.
* `string` – To manage direction state ("left" or "right").

---

## ⏱️ Time and Space Complexity

* **Time Complexity**: `O(N)` – where `N` is the number of nodes in the binary tree.
* **Space Complexity**: `O(N)` – due to queue and result vector.

---

## 🔁 Alternate Improvements

* Instead of using a `string` to manage direction, a `bool` flag can be used for better performance.
* For even more optimized memory usage, a **deque** can be used to push elements from both ends instead of reversing the vector each time.

---

