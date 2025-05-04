
# Linked List Cycle - LeetCode Problem 141

## ✅ Problem Status: Solved

### 📘 Problem Description

Given the `head` of a linked list, determine if the linked list contains a **cycle**.

A cycle occurs when a node's `next` pointer points back to a previous node in the list, forming a loop.

> Internally, the variable `pos` is used to denote the index of the node that the tail is connected to. This information is only for understanding the input format and is not part of the function parameters.

---

### 🧠 Examples

#### Example 1:

```plaintext
Input: head = [3,2,0,-4], pos = 1  
Output: true  
Explanation: Tail connects to node at index 1, forming a cycle.
````

#### Example 2:

```plaintext
Input: head = [1,2], pos = 0  
Output: true  
Explanation: Tail connects to node at index 0.
```

#### Example 3:

```plaintext
Input: head = [1], pos = -1  
Output: false  
Explanation: No cycle in the list.
```

---

### 💡 Approach

The algorithm uses **Floyd’s Cycle Detection Algorithm (Tortoise and Hare)**:

* Initialize two pointers: `slow` and `fast`, both starting at `head`.
* Move `slow` by 1 step and `fast` by 2 steps in each iteration.
* If there is a cycle, `fast` and `slow` will eventually meet.
* If `fast` reaches the end (`nullptr`), then there is no cycle.

---

### 🧾 Code

```cpp
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode(int x) : val(x), next(NULL) {}
 * };
 */
class Solution {
public:
    bool hasCycle(ListNode *head) {
        ListNode* slow = head;
        ListNode* fast = head;
        while (fast != nullptr && fast->next != nullptr) {
            slow = slow->next;
            fast = fast->next->next;
            if (slow == fast)
                return true;
        }
        return false;
    }
};
```

---

### 🛠️ Technologies Used

* Language: **C++**
* Concept: **Floyd’s Cycle Detection (Tortoise and Hare Algorithm)**

---

### ✍️ Author

* **Himanshu**
