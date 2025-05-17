# Queue Using Stacks

## Problem Statement

Implement a **first-in-first-out (FIFO)** queue using only two stacks. The implemented queue should support all standard operations:

- `push(int x)` – Pushes element `x` to the back of the queue.
- `pop()` – Removes the element from the front of the queue and returns it.
- `peek()` – Returns the element at the front of the queue without removing it.
- `empty()` – Returns `true` if the queue is empty, otherwise `false`.

**Constraints:**
- You may only use standard stack operations: `push`, `pop`, `top`, `size`, and `empty`.
- All `pop` and `peek` operations are guaranteed to be valid.
- At most 100 calls will be made to any operation.

---

## Approach

We use **two stacks** to simulate the behavior of a queue:

- `stack_in`: Used to enqueue elements.
- `stack_out`: Used to dequeue elements.

### How it works:

- **Push:** Simply push the element onto `stack_in`.
- **Pop/Peek:**
  - If `stack_out` is empty, transfer all elements from `stack_in` to `stack_out`. This reverses the order.
  - Then pop/peek from `stack_out`.
- **Empty:** Queue is empty only if both stacks are empty.

This ensures amortized **O(1)** time complexity for all operations.

---

## Code (C++)

```cpp
#include <stack>
using namespace std;

class MyQueue {
private:
    stack<int> stack_in;
    stack<int> stack_out;

    void transferIfNeeded() {
        if (stack_out.empty()) {
            while (!stack_in.empty()) {
                stack_out.push(stack_in.top());
                stack_in.pop();
            }
        }
    }

public:
    MyQueue() {
        // Constructor initializes empty stacks
    }

    void push(int x) {
        stack_in.push(x);
    }

    int pop() {
        transferIfNeeded();
        int val = stack_out.top();
        stack_out.pop();
        return val;
    }

    int peek() {
        transferIfNeeded();
        return stack_out.top();
    }

    bool empty() {
        return stack_in.empty() && stack_out.empty();
    }
};
````

---

## Example Usage

```cpp
MyQueue myQueue;
myQueue.push(1);       // queue: [1]
myQueue.push(2);       // queue: [1, 2]
myQueue.peek();        // returns 1
myQueue.pop();         // returns 1, queue becomes [2]
myQueue.empty();       // returns false
```

---

## Time and Space Complexity

| Operation | Time (Amortized) | Space Complexity |
| --------- | ---------------- | ---------------- |
| push      | O(1)             | O(n)             |
| pop       | O(1)             | O(n)             |
| peek      | O(1)             | O(n)             |
| empty     | O(1)             | O(1)             |

---
