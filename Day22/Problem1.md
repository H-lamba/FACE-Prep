# Majority Element (LeetCode 169)

## Problem Statement

Given an array `nums` of size `n`, return the **majority element**.  
The majority element is the element that appears more than ⌊n / 2⌋ times.  
It is guaranteed that a majority element always exists in the array.

### Example 1:
```

Input: nums = \[3, 2, 3]
Output: 3

```

### Example 2:
```

Input: nums = \[2, 2, 1, 1, 1, 2, 2]
Output: 2

````

---

## Approach

### Technique: Hash Map Frequency Counting

I used an `unordered_map` (hash map) in C++ to count the frequency of each number in the input array. As we iterate through the array:

1. We increment the count of the current number in the map.
2. After updating the count, we check if it exceeds ⌊n / 2⌋.
3. If it does, we return that number immediately, leveraging early exit for efficiency.
4. Since the problem guarantees the existence of a majority element, we are always expected to find and return the result before the loop ends.

This approach ensures **O(n)** time complexity with **O(n)** space usage due to the hash map.

---

## Code

```cpp
#include <unordered_map>
#include <vector>

class Solution {
public:
    int majorityElement(std::vector<int>& nums) {
        std::unordered_map<int, int> freq;
        for (int num : nums) {
            freq[num]++;
            if (freq[num] > nums.size() / 2) {
                return num; // Early exit if majority element is found
            }
        }
        return -1; // Should never reach here as problem guarantees a majority element
    }
};
````

---

## Time and Space Complexity

* **Time Complexity:** O(n) — We traverse the array once.
* **Space Complexity:** O(n) — At most, we store `n` elements in the hash map in the worst case.

---

## Why This Approach?

* Straightforward and easy to understand.
* Efficient early exit ensures we don’t do unnecessary work once the majority is found.
* Takes advantage of C++ STL's `unordered_map` for constant-time lookups and insertions.

---

## Alternative Approaches

* **Boyer-Moore Voting Algorithm** (O(1) space) is a more optimized approach.
* This implementation is more intuitive and works well for interview situations where clarity matters.

