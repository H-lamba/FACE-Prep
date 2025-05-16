# Min Stack - C++ Solution

## Problem Statement

Design a stack that supports the following operations **in constant time (O(1))**:

* `push(val)` — Pushes the element `val` onto the stack.
* `pop()` — Removes the element on the top of the stack.
* `top()` — Gets the top element.
* `getMin()` — Retrieves the **minimum element** in the stack.

You must implement a solution with O(1) time complexity for each function.

---

## Example

```
Input:
["MinStack","push","push","push","getMin","pop","top","getMin"]
[[],[-2],[0],[-3],[],[],[],[]]

Output:
[null,null,null,null,-3,null,0,-2]
```

**Explanation:**

```cpp
MinStack minStack = new MinStack();
minStack.push(-2);
minStack.push(0);
minStack.push(-3);
minStack.getMin(); // returns -3
minStack.pop();
minStack.top();    // returns 0
minStack.getMin(); // returns -2
```

---

## Approach

To support constant time retrieval of the minimum element, we use **two stacks**:

1. `Stack`: The main stack to store all elements.
2. `minimum`: An auxiliary stack to keep track of the **minimum element** at every level of the main stack.

Whenever we `push`:

* If the `minimum` stack is empty or the value is less than or equal to the current minimum, we also push it to the `minimum` stack.

When we `pop`:

* If the element being popped is equal to the top of the `minimum` stack, we also pop from the `minimum` stack.

---

## Time and Space Complexity

| Operation | Time Complexity | Space Complexity |
| --------- | --------------- | ---------------- |
| push      | O(1)            | O(n)             |
| pop       | O(1)            | O(n)             |
| top       | O(1)            | O(n)             |
| getMin    | O(1)            | O(n)             |

---

## Code

```cpp
class MinStack {
public:
    stack<int> Stack;   
    stack<int> minimum; 

    MinStack() {}

    void push(int val) {
        Stack.push(val);
        if (minimum.empty() || val <= minimum.top()) {
            minimum.push(val);
        }
    }

    void pop() {
        if (!Stack.empty()) {
            int x = Stack.top();
            Stack.pop();
            if (x == minimum.top()) {
                minimum.pop();
            }
        }
    }

    int top() {
        return Stack.top();
    }

    int getMin() {
        return minimum.top();
    }
};
```

---

## Notes

* The `minimum` stack always keeps the minimum elements aligned with the state of the main stack.
* This ensures that `getMin()` works in constant time without having to traverse the entire stack.

---
