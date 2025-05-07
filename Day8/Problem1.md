# Odd-Even Linked List

## Problem Statement

Given the head of a singly linked list, reorder the list such that all nodes at odd indices come before those at even indices. The relative order of nodes in each group (odd and even) should remain the same as the original list.

The first node is considered odd, and the second node is even, and so on.

### Requirements:

* Solve in **O(n)** time complexity.
* Solve in **O(1)** extra space complexity.

### Example 1:
![oddeven-linked-list](https://github.com/user-attachments/assets/b4d0a410-2959-4cee-aa0b-922ae1b6c184)

**Input**: `[1,2,3,4,5]`
**Output**: `[1, 3, 5, 2, 4]`

### Example 2:
![oddeven2-linked-list](https://github.com/user-attachments/assets/7f88e207-8b71-48ce-bc63-e6329d7d94e9)

**Input**: `[2,1,3,5,6,4,7]`
**Output**: `[2, 3, 6, 7, 1, 5, 4]`

## Approach

1. We begin by checking if the list is empty or has only one element, in which case no reordering is necessary.
2. We maintain two pointers: one (`odd`) for the odd-indexed nodes and another (`even`) for the even-indexed nodes.
3. We iterate through the list, adjusting the `next` pointers to separate the odd and even-indexed nodes.
4. Once the odd nodes are processed, we append the even nodes after the last odd node.
5. Finally, we return the reordered list.

## Code

```cpp
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode() : val(0), next(nullptr) {}
 *     ListNode(int x) : val(x), next(nullptr) {}
 *     ListNode(int x, ListNode *next) : val(x), next(next) {}
 * };
 */
class Solution {
public:
    ListNode* oddEvenList(ListNode* head) {
        if (!head || !head->next) return head;

        ListNode* odd = head;
        ListNode* even = head->next;
        ListNode* evenHead = even;

        while (even && even->next) {
            odd->next = odd->next->next;
            odd = odd->next;
            even->next = even->next->next;
            even = even->next;
        }    
        odd->next = evenHead;
        return head;
    }
};
```

## Explanation

1. **Initial Check**: If the linked list has fewer than two elements, we directly return the head.
2. **Pointer Setup**: We set two pointers, `odd` and `even`, starting from the first and second nodes respectively.
3. **Reordering**: In a loop, we modify the `next` pointers of the odd and even nodes, effectively separating them into two groups.
4. **Connecting Even Nodes**: After processing all odd nodes, we connect the last odd node to the first even node.
5. **Return the Reordered List**: We return the modified list with odd nodes first and even nodes afterward.

## Time and Space Complexity

* **Time Complexity**: O(n), where n is the number of nodes in the list. We iterate through the list once.
* **Space Complexity**: O(1), as we only use a constant amount of extra space.

## Usage

You can copy and paste the code into your C++ environment, providing the head of the linked list as input, and calling the `oddEvenList` function to reorder the list.

---
