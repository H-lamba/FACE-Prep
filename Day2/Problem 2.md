
# Middle of the Linked List - LeetCode Problem 876

This repository contains a C++ solution to **[LeetCode Problem 876: Middle of the Linked List](https://leetcode.com/problems/middle-of-the-linked-list/)** using the two-pointer technique.

## Problem Description

Given the `head` of a singly linked list, return the **middle node** of the linked list.

If there are **two middle nodes**, return **the second** middle node.

### Example 1:
```
Input: head = [1,2,3,4,5]
Output: [3,4,5]
Explanation: The middle node is 3.
```

### Example 2:
```
Input: head = [1,2,3,4,5,6]
Output: [4,5,6]
Explanation: There are two middle nodes (3 and 4), and we return the second one, which is 4.
```

---

## Approach: Fast and Slow Pointers

This solution uses the **two-pointer technique**:

- **Slow pointer (`slow`)** moves one step at a time.
- **Fast pointer (`fast`)** moves two steps at a time.
- When `fast` reaches the end of the list, `slow` will be at the middle.

### Code:

```cpp
class Solution {
public:
    ListNode* middleNode(ListNode* head) {
        ListNode* slow = head;
        ListNode* fast = head;
        while (fast != nullptr && fast->next != nullptr) {
            fast = fast->next->next;
            slow = slow->next;
        }
        return slow;
    }   
};
```

---

## Time and Space Complexity

- **Time Complexity:** O(n) — We traverse the list once.
- **Space Complexity:** O(1) — No extra space is used.

---

## Why the Second Middle Node is Returned

In the case of even-length lists, the slow pointer advances one node after the true middle due to how the loop is structured. This naturally returns the **second** middle node, as required by the problem.

---


Himanshu 
This is a concise and efficient solution using a classic linked list pattern.

---
