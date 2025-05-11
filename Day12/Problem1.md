# Leetcode Problem 2807: Insert Greatest Common Divisors in Linked List

## 🧠 Problem Statement

Given the head of a singly linked list where each node contains an integer value, insert a new node between every pair of adjacent nodes. The new node's value should be the **greatest common divisor (GCD)** of the values of the two adjacent nodes.

Return the modified linked list after all insertions.

### Example 1:
![image](https://github.com/user-attachments/assets/395a074e-9d0a-46db-b422-7616c869e3f3)
**Input:**
```

\[18, 6, 10, 3]

```

**Output:**
```

\[18, 6, 6, 2, 10, 1, 3]

```

### Example 2:
![image](https://github.com/user-attachments/assets/70d9856c-fb6d-4169-82fe-ca8664965d1a)
**Input:**
```

\[7]

```

**Output:**
```

\[7]

````

---

## ✅ Approach

This solution follows these main steps:

1. **Traverse the list** node-by-node using two pointers: `first` and `second`.
2. For each pair of adjacent nodes (`first`, `second`):
   - Compute the **GCD** of `first->val` and `second->val` using the **Euclidean algorithm**.
   - Create a new node with the GCD value.
   - Insert this new node between `first` and `second`.
3. Update the pointers and repeat until the end of the list is reached.

---

## 🔧 Implementation (C++)

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
    int gcd(int a, int b)
    {
        /*int low = a;
        int high = b;
        if(a>b)
        {
            low = b;
            high = a;
        }
        int ans = 0;
        for(int i = 1; i<=high; i++)
        {
            if(a%i == 0 && b %i==0)
            ans = i;
        }
        return ans;*/
        while (b != 0) {
            int temp = b;
            b = a % b;
            a = temp;
        }
        return a;
    }
    ListNode* insertGreatestCommonDivisors(ListNode* head) {
        if(head->next == nullptr) return head;
        ListNode * first = head;
        ListNode * second = head->next;
        while(second)
        {
            int insert = gcd(first->val, second->val);
            ListNode *temp = new ListNode(insert);
            first->next = temp;
            temp->next = second;
            first = second;
            second = second->next;
        }
        return head;
    }
};
````

---

## 📌 Key Concepts

* **Linked List Manipulation**: Efficient node insertion using pointers.
* **Greatest Common Divisor (GCD)**: Used to calculate the value for each new node.
* **Memory Management**: Nodes are dynamically allocated with `new`.

---

## ⏱️ Time & Space Complexity

* **Time Complexity**: `O(N * log(min(a, b)))`, where `N` is the number of nodes and `log(min(a, b))` is for GCD calculation.
* **Space Complexity**: `O(1)` extra space (excluding new nodes).

---

## 🛠️ Enhancements

* Replace the brute-force GCD with the Euclidean algorithm (already done ✅).
* Avoid memory leaks by ensuring nodes are properly managed if extended.

---

## 📥 Example Walkthrough

For input `[18, 6, 10, 3]`:

* GCD(18, 6) = 6 → insert between 18 and 6
* GCD(6, 10) = 2 → insert between 6 and 10
* GCD(10, 3) = 1 → insert between 10 and 3

Final output: `[18, 6, 6, 2, 10, 1, 3]`

---

