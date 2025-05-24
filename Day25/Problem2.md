
# Implement Stack using Queues - LeetCode Problem 225

This repository contains an efficient solution to the LeetCode problem [225. Implement Stack using Queues](https://leetcode.com/problems/implement-stack-using-queues/), where the objective is to simulate a **stack (LIFO)** using standard **queue (FIFO)** operations.

---

## Problem Statement

Design a stack that supports:
- `push(x)`: Pushes element `x` to the top of the stack.
- `pop()`: Removes and returns the top element.
- `top()`: Returns the top element.
- `empty()`: Returns `true` if the stack is empty, else `false`.

Constraints:
- Only **standard queue operations** are allowed:
  - `push to back`
  - `peek/pop from front`
  - `size`
  - `isEmpty`

---

## Approach: Using a Single Queue

### Key Idea

To simulate **Last-In-First-Out (LIFO)** using a **First-In-First-Out (FIFO)** structure, we rotate the queue after every `push`:

1. Push the new element at the back.
2. Rotate all previous elements to the back of the queue.

This ensures that the most recently added element is always at the front, allowing `top()` and `pop()` to work in O(1) time.

---

## Class Implementation

```cpp
class MyStack {
private:
    queue<int> q;

public:
    MyStack() { }
    
    void push(int x) {
        q.push(x);
        for (int i = 0; i < q.size() - 1; i++) {
            q.push(q.front());
            q.pop();
        }
    }
    
    int pop() {
        int topelement = q.front();
        q.pop();
        return topelement;
    }
    
    int top() {
        return q.front();
    }
    
    bool empty() {
        return q.empty();
    }
};
````

---

## Time & Space Complexity

| Operation | Time Complexity | Space Complexity |
| --------- | --------------- | ---------------- |
| `push(x)` | O(n)            | O(n)             |
| `pop()`   | O(1)            | O(1)             |
| `top()`   | O(1)            | O(1)             |
| `empty()` | O(1)            | O(1)             |

---

## Example Usage

```cpp
MyStack myStack;
myStack.push(1);
myStack.push(2);
myStack.top();    // returns 2
myStack.pop();    // returns 2
myStack.empty();  // returns false
```

---

## Summary

✅ Simulates stack behavior using a single queue
✅ Efficient `pop()` and `top()` in O(1) time
✅ Complies with problem constraint: **only uses queue operations**

---

## Author

Solution implemented in C++ by Himanshu.

