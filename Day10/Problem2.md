# LeetCode 2095: Delete the Middle Node of a Linked List 🧹🧠

## Problem Statement

You are given the head of a singly linked list. You must **delete the middle node**, and return the head of the modified list.

> The middle node is defined as the ⌊n / 2⌋-th node using 0-based indexing.

---

## Example
![image](https://github.com/user-attachments/assets/44bcdf73-cfc1-4a0e-a3c9-7c3e66de7969)

### Input:
```

head = \[1,3,4,7,1,2,6]

```

### Output:
```

\[1,3,4,1,2,6]

````

### Explanation:
- The original list has 7 nodes.
- The middle node (index 3, value `7`) is removed.

---

## 🔁 Brute-force Approach

This approach involves **two passes**:
1. Count the total number of nodes.
2. Traverse to the middle node and remove it.

```cpp
class Solution {
public:
    ListNode* deleteMiddle(ListNode* head) {
        if(head->next == nullptr) return head->next;

        ListNode* temp = head;
        int n = 0;

        // Count number of nodes
        while(temp) {
            n++;
            temp = temp->next;
        }

        int mid = n / 2;
        temp = head;

        // Traverse to (mid - 1)th node
        for(int i = 1; i < mid; i++) {
            temp = temp->next;
        }

        // Delete middle node
        ListNode* temp2 = temp->next;
        temp->next = temp2->next;

        return head;
    }
};
````

### 🟡 Drawbacks:

* Two full traversals of the list.
* O(n) time and O(1) space, but not the most efficient.

---

## ⚡ Optimal Two-Pointer Approach

This method uses the **slow and fast pointer** technique to find the middle in a **single pass**.

```cpp
class Solution {
public:
    ListNode* deleteMiddle(ListNode* head) {
        if(head->next == nullptr) return head->next;

        ListNode* slow = head;
        ListNode* fast = head;
        ListNode* prev = nullptr;

        while(fast && fast->next) {
            fast = fast->next->next;
            prev = slow;
            slow = slow->next;
        }

        if(prev) prev->next = slow->next;

        return head;
    }
};
```

### ✅ Advantages:

* **Single traversal** (O(n) time).
* **Constant space** (O(1)).
* Efficient and clean solution for large lists.

---

## Conclusion

* Both solutions are valid for interviews and practice.
* The two-pointer method is preferred for performance.
* This problem is a great example of using pointer manipulation for linked list problems.

---
