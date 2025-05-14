# Add Two Numbers (Linked List)

This project implements a C++ solution to the classic **"Add Two Numbers"** problem from LeetCode. It involves adding two numbers represented by linked lists where digits are stored in reverse order.

## 🧩 Problem Description

You are given two **non-empty linked lists** representing two **non-negative integers**. The digits are stored in **reverse order**, and each node contains a **single digit**. Add the two numbers and return the sum as a **linked list**, also in reverse order.

You may assume:
- The two numbers do not contain any leading zero, except the number 0 itself.

### ✅ Example

#### Example 1
![image](https://github.com/user-attachments/assets/a5f9d209-58cf-431b-bd48-0a5854fbce36)

```

Input:  l1 = \[2,4,3], l2 = \[5,6,4]
Output: \[7,0,8]
Explanation: 342 + 465 = 807

```

#### Example 2
```

Input:  l1 = \[0], l2 = \[0]
Output: \[0]

```

#### Example 3
```

Input:  l1 = \[9,9,9,9,9,9,9], l2 = \[9,9,9,9]
Output: \[8,9,9,9,0,0,0,1]

````

## 💡 Approach

- Use a dummy node to build the resulting linked list.
- Traverse both lists while handling digits and carry.
- At each step, calculate the sum of the two digits and the carry.
- Create a new node with `sum % 10`, and update carry as `sum / 10`.
- After the loop, if any carry remains, append it as a new node.

## 🛠️ Code

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
    ListNode* addTwoNumbers(ListNode* l1, ListNode* l2) {
        ListNode *store = new ListNode(0);
        ListNode *ans = store;
        int carry = 0;
        
        while (l1 || l2 || carry != 0) {
            int sum = carry;
            if (l1) {
                sum += l1->val;
                l1 = l1->next;
            }
            if (l2) {
                sum += l2->val;
                l2 = l2->next;
            }
            carry = sum / 10;
            store->next = new ListNode(sum % 10);
            store = store->next;
        }
        return ans->next;
    }
};
````

