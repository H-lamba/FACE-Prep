
## 🌳 Binary Tree Level Order Traversal - LeetCode Problem 102

### 🧩 Problem Statement

Given the `root` of a binary tree, return the **level order traversal** of its nodes' values.
That is, return the values **level by level**, from left to right.

---

### ✅ Examples

#### Example 1:

```
Input:  root = [3,9,20,null,null,15,7]
Output: [[3],[9,20],[15,7]]
```

#### Example 2:

```
Input:  root = [1]
Output: [[1]]
```

#### Example 3:

```
Input:  root = []
Output: []
```

---

## 🧠 Approach: BFS Using Queue

> ✅ **Status:** Efficient and correct
> 🔁 **Technique:** Breadth-First Search (Level Order Traversal)

### 🔍 Logic

1. Use a queue to process nodes level by level.
2. For each level:

   * Record the number of nodes at the current level (`size` of the queue).
   * Traverse all nodes at that level and store their values.
   * Push their children (if any) into the queue for the next level.
3. Append the current level's list of values to the final answer.

---

### 🧾 Code Walkthrough

```cpp
vector<vector<int>> levelOrder(TreeNode* root) {
    vector<vector<int>> ans;
    if (root == nullptr) return ans;

    queue<TreeNode*> q;
    q.push(root);

    while (!q.empty()) {
        int size = q.size();
        vector<int> level;

        for (int i = 0; i < size; i++) {
            TreeNode* node = q.front();
            q.pop();

            if (node->left != nullptr) q.push(node->left);
            if (node->right != nullptr) q.push(node->right);

            level.push_back(node->val);
        }

        ans.push_back(level);
    }

    return ans;
}
```

---

### ⏱️ Time & Space Complexity

| Complexity | Analysis                          |
| ---------- | --------------------------------- |
| ⌛ Time     | O(n) – Each node is visited once  |
| 💾 Space   | O(n) – For queue + result storage |

Where `n` is the total number of nodes in the binary tree.

---

### 📌 Conclusion

* Uses a **queue** to efficiently implement BFS.
* Returns the desired **level-wise** node values as required.
* This is the most optimal and standard approach for level order traversal.
