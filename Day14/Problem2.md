
# 86. Partition List

## 🧩 Problem Statement

Given the `head` of a linked list and a value `x`, partition it such that all nodes less than `x` come **before** nodes greater than or equal to `x`.

📌 You **must preserve** the original relative order of the nodes in each of the two partitions.

---

## 📝 Example

### Example 1:
**Input:**  
`head = [1, 4, 3, 2, 5, 2]`, `x = 3`  
**Output:**  
`[1, 2, 2, 4, 3, 5]`

### Example 2:
**Input:**  
`head = [2, 1]`, `x = 2`  
**Output:**  
`[1, 2]`

---

## 💡 Approach

- We use two dummy linked lists:
  - One (`par1`) for nodes with values **less than x**.
  - Another (`par2`) for nodes with values **greater than or equal to x**.
- Traverse the original list:
  - Append nodes with `val < x` to `par1`.
  - Append others to `par2`.
- Connect the end of `par1` list to the start of `par2` list.
- Return the merged list starting from `par1->next`.

---

## 🚀 Code (C++)

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
    ListNode* partition(ListNode* head, int x) {
        ListNode *par1 = new ListNode(0);
        ListNode *ans = par1;
        ListNode *par2 = new ListNode(0);
        ListNode *link = par2;
        
        while (head) {
            if (head->val < x) {
                ListNode *temp = new ListNode(head->val);
                par1->next = temp;
                par1 = par1->next;
            } else {
                ListNode *temp = new ListNode(head->val);
                par2->next = temp;
                par2 = par2->next;
            }
            head = head->next;
        }
        
        par1->next = link->next;
        return ans->next;
    }
};
````

---

## 🧠 Complexity

* **Time Complexity:** `O(n)` — Each node is visited once.
* **Space Complexity:** `O(n)` — New nodes are created for each value.

---

## ✅ Features

* Maintains the relative order of nodes.
* Uses two-pass technique with two dummy lists.
* Easy to understand and implement.

---

## 📚 Topics

* Linked List
* Two Pointer
* Partitioning
* Dummy Nodes

---

## 📌 Note

This solution creates **new nodes**, which is acceptable and works correctly. For a more space-efficient version that **reuses existing nodes**, check the optimized in-place version.

---

## 👨‍💻 Author

Himanshu
