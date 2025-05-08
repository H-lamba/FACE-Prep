
## 🔁 Swap Nodes in a Linked List

### ✅ Problem Statement

Given the `head` of a singly linked list and an integer `k`, **swap the `k`th node from the beginning with the `k`th node from the end**, and return the modified list.

* The list is **1-indexed**.
* You must **swap the nodes themselves** (not just their values).
* Nodes may be adjacent or at the ends of the list.

---

### 💡 Example

**Example 1:**

```
Input:  head = [1,2,3,4,5], k = 2  
Output: [1,4,3,2,5]
```

**Example 2:**

```
Input:  head = [7,9,6,6,7,8,3,0,9,5], k = 5  
Output: [7,9,6,6,8,7,3,0,9,5]
```

---

### 🧠 Approach

1. **Count the length `n`** of the list.
2. Determine the position of the `k`th node from the end using `n - k + 1`.
3. Traverse the list twice to find:

   * `node1`: The `k`th node from the beginning
   * `node2`: The `k`th node from the end
   * Also store `prev1` and `prev2`: the previous nodes of `node1` and `node2` respectively
4. **Swap the actual nodes** by adjusting the `next` pointers:

   * If the nodes are adjacent, handle that case separately.
   * If one of the nodes is the head, update the `head` pointer accordingly.

---

### 🧩 Edge Cases Handled

* Nodes to be swapped are adjacent.
* Either `node1` or `node2` is the `head`.
* `node1 == node2`: no swap needed (already in place).
* Very short lists (length 1 or 2).

---

### 📎 Code (C++)

```cpp
class Solution {
public:
    ListNode* swapNodes(ListNode* head, int k) {
        int n = 0;
        ListNode* temp = head;

        // Step 1: Count the total number of nodes
        while(temp) {
            n++;
            temp = temp->next;
        }

        int end = n - k + 1;
        ListNode* prev1 = nullptr;
        ListNode* prev2 = nullptr;
        ListNode* node1 = head;
        ListNode* node2 = head;

        // Step 2: Locate node1 and its previous node
        temp = head;
        for(int i = 1; i < k; i++) {
            prev1 = temp;
            temp = temp->next;
        }
        node1 = temp;

        // Step 3: Locate node2 and its previous node
        temp = head;
        for(int i = 1; i < end; i++) {
            prev2 = temp;
            temp = temp->next;
        }
        node2 = temp;

        // Step 4: Swap logic
        if (node1 == node2) return head;

        if (node1->next == node2) {
            if (prev1) prev1->next = node2;
            else head = node2;
            node1->next = node2->next;
            node2->next = node1;
        }
        else if (node2->next == node1) {
            if (prev2) prev2->next = node1;
            else head = node1;
            node2->next = node1->next;
            node1->next = node2;
        }
        else {
            ListNode* tempNext = node2->next;
            if (prev1) prev1->next = node2;
            else head = node2;
            if (prev2) prev2->next = node1;
            else head = node1;
            node2->next = node1->next;
            node1->next = tempNext;
        }

        return head;
    }
};
```

---

### 🧪 Time & Space Complexity

| Metric           | Value           |
| ---------------- | --------------- |
| Time Complexity  | O(n)            |
| Space Complexity | O(1) (in-place) |

---

### 📌 Notes

* This implementation **does not swap values** — it swaps the actual node links.
* All pointer updates are handled carefully to avoid dangling pointers or memory errors.

---
