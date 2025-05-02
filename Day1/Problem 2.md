
# Reverse Linked List - LeetCode Problem 206

This repository contains a C++ implementation for **[LeetCode Problem 206: Reverse Linked List](https://leetcode.com/problems/reverse-linked-list/)**.

## Problem Description

Given the `head` of a singly linked list, reverse the list, and return the reversed list.

### Example 1:
```
Input: head = [1,2,3,4,5]  
Output: [5,4,3,2,1]
```

### Example 2:
```
Input: head = [1,2]  
Output: [2,1]
```

### Example 3:
```
Input: head = []  
Output: []
```

---

## Approach

This solution uses **iterative in-place reversal** with three pointers:

- `prev`: Initially set to `nullptr`
- `curr`: The current node being processed
- `nextTemp`: Temporarily stores the next node before changing pointers

The `next` pointer of each node is redirected to point to the previous node, effectively reversing the list.

---

## Solution Code (C++)

```cpp
class Solution {
public:
    ListNode* reverseList(ListNode* head) {
        ListNode* prev = nullptr;
        ListNode* curr = head;
        
        while (curr != nullptr) {
            ListNode* nextTemp = curr->next; 
            curr->next = prev;               
            prev = curr;                     
            curr = nextTemp;                 
        }
        return prev; 
    }
};
```

---

## Time and Space Complexity

- **Time Complexity:** O(n) — Each node is visited exactly once.
- **Space Complexity:** O(1) — Reversal is done in-place using constant space.

---

Himanshu
Feel free to fork, use, or contribute!

---
