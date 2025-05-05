## 📘 Problem 234: Palindrome Linked List

### ✅ Status: Solved

### 🔍 Description

Given the head of a singly linked list, return `true` if the linked list is a **palindrome**, otherwise return `false`.

A **palindrome** is a sequence that reads the same forward and backward.

---

### 🧠 Examples

#### Example 1:
```plaintext
Input: head = [1,2,2,1]  
Output: true
````

#### Example 2:

```plaintext
Input: head = [1,2]  
Output: false
```

---

### 💡 Approach

* Use **two-pointer technique** (`slow` and `fast`) to find the midpoint.
* **Reverse the second half** of the list in-place.
* Compare values from the first half and the reversed second half.
* If all corresponding values match, it's a palindrome.

✅ Time Complexity: `O(n)`
✅ Space Complexity: `O(1)` – in-place reversal, no extra space used.

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
    bool isPalindrome(ListNode* head) {
        ListNode* slow = head;
        ListNode* fast = head;

        // Step 1: Find the middle using slow/fast pointers
        while (fast != nullptr && fast->next != nullptr) {
            fast = fast->next->next;
            slow = slow->next;
        }

        // Step 2: Reverse second half
        ListNode* prev = nullptr;
        ListNode* curr = slow;
        while (curr) {
            ListNode* temp = curr->next;
            curr->next = prev;
            prev = curr;
            curr = temp;
        }

        // Step 3: Compare both halves
        ListNode* first = head;
        ListNode* second = prev;
        while (second) {
            if (first->val != second->val)
                return false;
            first = first->next;
            second = second->next;
        }

        return true;
    }
};
```

---

### 🛠️ Technologies Used

* Language: **C++**
* Concepts: **Linked List**, **Two-pointer technique**, **In-place reversal**

---

### 📁 How to Use

1. Create a linked list using the `ListNode` structure.
2. Pass the head node to the `isPalindrome()` function.
3. The function will return `true` or `false`.

---

* **HImanshu**
