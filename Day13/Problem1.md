# Remove Duplicates from Sorted List II – LeetCode 82

## Problem Statement

Given the head of a **sorted** linked list, delete all nodes that have duplicate numbers, leaving only distinct numbers from the original list. Return the linked list **sorted** as well.

### Examples

**Example 1:**
```

Input: head = \[1,2,3,3,4,4,5]
Output: \[1,2,5]

```

**Example 2:**
```

Input: head = \[1,1,1,2,3]
Output: \[2,3]

````

---

## Approach

The key to solving this problem is recognizing that we need to **completely remove all duplicate values**, not just the second or later occurrences. So, if a value appears more than once, **none** of the nodes with that value should remain in the list.

### Steps:

1. **Use a Dummy Node**:  
   A dummy node is initialized before the head to simplify edge cases like removing the head itself.

2. **Traverse the List**:
   - If the current node has a duplicate (`head->val == head->next->val`), skip all nodes with this value.
   - Otherwise, move `prev` forward to include the node.

3. **Return `dummy->next`**:
   - This ensures the correct new head is returned, even if the original head was removed.

---

## Code (C++)

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
    ListNode* deleteDuplicates(ListNode* head) {
        if (!head) return nullptr;

        ListNode *dummy = new ListNode(head->val - 1, head);
        ListNode *prev = dummy;

        while (head) {
            if (head->next && head->val == head->next->val) {
                int same = head->val;
                while (head && head->val == same) {
                    head = head->next;
                }
                prev->next = head;
            } else {
                prev = prev->next;
                head = head->next;
            }
        }

        return dummy->next;
    }
};
````

---

## Time and Space Complexity

* **Time Complexity**: O(n), where n is the number of nodes in the list.
* **Space Complexity**: O(1), since no extra space is used apart from a few pointers.

---

## Tags

* Linked List
* Two Pointers

---

## Author

**Himanshu**
