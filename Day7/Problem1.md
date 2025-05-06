## 🔁 Problem 61: Rotate List

### ✅ Status: Solved

### 🔍 Problem Description

Given the head of a linked list, rotate the list to the right by `k` places.

---

### 🧠 Examples

#### Example 1:
```plaintext
Input: head = [1,2,3,4,5], k = 2  
Output: [4,5,1,2,3]
````

#### Example 2:

```plaintext
Input: head = [0,1,2], k = 4  
Output: [2,0,1]
```

---

### 💡 Approach

* First, find the **length** of the list.
* If `k` is greater than the list length, use `k = k % length` to reduce unnecessary rotations.
* Traverse the list to find the **new tail** (at position `n - k`).
* Break the list at this position and make the next node the new head.
* Finally, reconnect the original tail to the original head to complete the rotation.

✅ Time Complexity: `O(n)`
✅ Space Complexity: `O(1)`

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
    ListNode* rotateRight(ListNode* head, int k) {
        if (!head || !head->next || k == 0) return head;

        int n = 1;
        ListNode* temp = head;

        // Count the length of the list
        while (temp->next) {
            temp = temp->next;
            n++;
        }

        // Optimize k
        k = k % n;
        if (k == 0) return head;

        // Traverse to the new tail
        int steps = n - k;
        ListNode* T = head;
        for (int i = 1; i < steps; i++) {
            T = T->next;
        }

        // Update pointers
        ListNode* H = T->next;
        T->next = nullptr;
        temp->next = head; // reconnect tail to old head

        return H;
    }
};
```

---

### 🛠️ Technologies Used

* Language: **C++**
* Concepts: **Linked List**, **Modular Arithmetic**, **Pointer Manipulation**

---

### 📁 How to Use

1. Compile and run the code in any C++ environment.
2. Call the `rotateRight()` function by passing the head of the list and the integer `k`.
* **Himanshu**
