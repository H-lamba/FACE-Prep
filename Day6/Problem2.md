## 📘 Problem 203: Remove Linked List Elements

### ✅ Status: Solved

### 🔍 Description

Given the head of a singly linked list and an integer `val`, remove all the nodes in the linked list that have `Node.val == val`, and return the new head.

---

### 🧠 Examples

#### Example 1:
![image](https://github.com/user-attachments/assets/962c535f-b381-4b2a-802a-abd76cb6475d)

```plaintext
Input: head = [1,2,6,3,4,5,6], val = 6  
Output: [1,2,3,4,5]
````

#### Example 2:

```plaintext
Input: head = [], val = 1  
Output: []
```

#### Example 3:

```plaintext
Input: head = [7,7,7,7], val = 7  
Output: []
```

---

### 💡 Approach

* Create a **dummy node** before the head to simplify edge cases (like removing the head node).
* Traverse through the linked list, checking if the current node's value equals `val`. If it doesn't, attach it to the result list.
* After the loop, return the node after the dummy (the new head).

✅ Time Complexity: `O(n)`
✅ Space Complexity: `O(1)` (in-place manipulation)

---

### 🧾 Code

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
    ListNode* removeElements(ListNode* head, int val) {
        ListNode* temp = head;
        ListNode* dummy = new ListNode(0);  // Create a dummy node
        ListNode* ans = dummy;              // Pointer to traverse result list

        while (temp != nullptr) {
            if (temp->val != val) {
                ans->next = temp;  // Add node to result
                ans = ans->next;
            }
            temp = temp->next;  // Move to the next node
        }
        
        ans->next = nullptr;  // Terminate the list
        return dummy->next;   // Return the head after dummy
    }
};
```

---

### 🛠️ Technologies Used

* Language: **C++**
* Concepts: **Linked List Manipulation**, **Dummy Node Technique**

---

### 📁 How to Use

1. Compile and run the code.
2. Pass the head node of a linked list and the integer `val` to the `removeElements()` function.

---
* **Himanshu**
