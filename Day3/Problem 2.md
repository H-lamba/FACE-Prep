## 📘 Problem 21: Merge Two Sorted Lists

### ✅ Status: Solved

### 🔍 Description

You are given the heads of two sorted linked lists `list1` and `list2`.  
Merge the two lists into one sorted linked list by **splicing together the nodes** of the two lists.  
Return the head of the merged linked list.

---

### 🧠 Examples

#### Example 1:
![image](https://github.com/user-attachments/assets/052ea178-585a-4777-9ac0-b0d17464beda)

```plaintext
Input: list1 = [1,2,4], list2 = [1,3,4]  
Output: [1,1,2,3,4,4]
````

#### Example 2:

```plaintext
Input: list1 = [], list2 = []  
Output: []
```

#### Example 3:

```plaintext
Input: list1 = [], list2 = [0]  
Output: [0]
```

---

### 💡 Approach

* Use a **dummy node** to simplify list building.
* Compare values from `list1` and `list2`.
* Attach the smaller node to the result list.
* Continue until either list is exhausted.
* Attach the remaining non-empty list (if any).

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
    ListNode* mergeTwoLists(ListNode* list1, ListNode* list2) {
        ListNode* l1 = list1;
        ListNode* l2 = list2;
        ListNode dummy(0);
        ListNode* ans = &dummy;

        while (l1 != nullptr && l2 != nullptr) {
            if (l1->val > l2->val) {
                ans->next = l2;
                l2 = l2->next;
            } else {
                ans->next = l1;
                l1 = l1->next;
            }
            ans = ans->next;
        }

        ans->next = (l1 != nullptr) ? l1 : l2;
        return dummy.next;
    }
};
```

---

### 🛠️ Technologies Used

* Language: **C++**
* Concepts: **Linked Lists**, **Two-pointer technique**, **Dummy node**

---

### ✍️ Author

* **Himanshu**
