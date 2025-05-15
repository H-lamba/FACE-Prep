# LeetCode Problem 237: Delete Node in a Linked List

## Problem Statement

You are given a node in a **singly linked list**, and you must delete this node. The challenge is that:

- You are **not given access to the head** of the list.
- The node to delete is **not the last node**.
- The list contains **unique values**.

You must delete the given node by:
- Making sure its value no longer appears in the list.
- Reducing the total number of nodes by one.
- Maintaining the order of all nodes before and after the deleted node.

---

## Example 1

![image](https://github.com/user-attachments/assets/8208d69f-dd5d-409e-9b09-41c5c2d0ed08)

**Input:**  
`head = [4,5,1,9]`, `node = 5`  
**Output:**  
`[4,1,9]`  

**Explanation:**  
You're given the second node with value `5`. After deletion, the list becomes `4 -> 1 -> 9`.

---

## Approach

### ✅ Concept

Since we **don't have access to the head** of the list or the previous node, we **cannot actually delete** the node from memory in the traditional sense.

Instead, the trick is to:
1. **Copy the data** from the next node into the current node.
2. **Delete the next node** by adjusting the `next` pointer.

This effectively removes the "identity" of the current node by overwriting it, and skips the actual next node — achieving the same effect as deleting the current node.

### ✅ Your Implementation Details

```cpp
class Solution {
public:
    void deleteNode(ListNode* node) {
        ListNode* prev = nullptr;
        while (node->next) {
            node->val = node->next->val;  // Copy next node's value
            prev = node;
            node = node->next;
        }
        prev->next = nullptr;  // Disconnect the last node (now duplicate)
    }
};
````

### ✅ Explanation

* You iterate through the list from the given node.
* At each step, copy the value of the next node into the current one.
* Keep track of the previous node (`prev`).
* At the end, set `prev->next` to `nullptr` to remove the duplicate tail node.

### ⚠️ Note

This is an extended version of the most optimal solution, which typically stops right after copying the next node’s value and pointer:

```cpp
node->val = node->next->val;
node->next = node->next->next;
```

However, your loop-based approach simulates deletion in a more general way, making it easier to understand what's happening behind the scenes.

---

## Time and Space Complexity

* **Time Complexity:** O(n) in your approach (due to traversal from the node to the end)
* **Space Complexity:** O(1)

---

## Summary

My approach correctly handles the deletion without access to the head by propagating values forward and trimming the last duplicate node. It's a clear and understandable method, although not as optimal as the constant-time version.

