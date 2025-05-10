# LeetCode Problem #19: Remove Nth Node From End of List

## 🧠 Problem Statement

Given the head of a singly linked list, remove the `n`th node from the **end** of the list and return its head.

---

## 🧪 Examples

### Example 1:
![image](https://github.com/user-attachments/assets/20028301-f1d3-41ed-864c-6297ae9486fb)

```

Input: head = \[1,2,3,4,5], n = 2
Output: \[1,2,3,5]

```

### Example 2:
```

Input: head = \[1], n = 1
Output: \[]

```

### Example 3:
```

Input: head = \[1,2], n = 1
Output: \[1]

````

---

## ✅ Approach: Two-Pass Iterative Solution

### Description:
1. First, traverse the list to count the total number of nodes.
2. If the node to remove is the head (`n == size`), adjust the head.
3. Otherwise, traverse again to the node before the target and remove the target by updating pointers.

---

## 💻 Code:

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
    ListNode* removeNthFromEnd(ListNode* head, int n) {
        int s = 0;
        ListNode* temp = head;

        // Count total number of nodes
        while (temp) {
            s++;
            temp = temp->next;
        }

        // If head needs to be removed
        if (s == n) {
            head = head->next;
            return head;
        }

        // Traverse to the node before the target
        int step = s - n;
        temp = head;
        for (int i = 1; i < step; i++) {
            temp = temp->next;
        }

        // Remove the nth node from the end
        ListNode* next = temp->next;
        temp->next = next->next;

        return head;
    }
};
````

---

## ⏱️ Time and Space Complexity

* **Time Complexity:** O(N) — two passes through the linked list.
* **Space Complexity:** O(1) — constant space usage.

---

## 📌 Notes

* This solution is straightforward and easy to implement using two traversals.
* A more efficient **one-pass** solution can be done using two pointers (fast and slow), which you can consider for further optimization.

