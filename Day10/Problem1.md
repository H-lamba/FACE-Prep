# LeetCode 319: Bulb Switcher 💡

## Problem Statement

There are `n` bulbs that are initially off. You perform `n` rounds of operations. On each i-th round, you toggle every i-th bulb (turning it on if it's off, or off if it's on). You must determine how many bulbs are on after all n rounds.

### Example
![image](https://github.com/user-attachments/assets/d310a066-612a-484e-b5b2-24e875cb4c1b)

#### Input:
```

n = 3

```

#### Process:
- Initial state: [off, off, off]
- Round 1: Toggle every bulb → [on, on, on]
- Round 2: Toggle every 2nd bulb → [on, off, on]
- Round 3: Toggle every 3rd bulb → [on, off, off]

#### Output:
```

1 (Only the first bulb is on)

````

---

## Brute-force Solution 🚫

```cpp
class Solution {
public:
    int bulbSwitch(int n) {
        unordered_map<long long , long long> r;
        int ans = 0;
        for(long long  i = 1; i<=n; i++) // Each round
        {
            for(long long j = i; j<=n; j = j+i) // Toggle every i-th bulb
            {
                r[j] = !r[j];
            }
        }
        for(auto i : r)
        {
            if(i.second==1)
                ans++;
        }
        return ans;
    }
};
````

### 🔍 Issue with this Approach

* Time Complexity: O(n²) — Inefficient for large inputs.
* Uses `unordered_map` to track toggle states — adds extra space overhead.
* Not optimal for competitive programming or large values of `n`.

---

## Optimal Solution 💡 (Math-based)

```cpp
class Solution {
public:
    int bulbSwitch(int n) {
        return sqrt(n);
    }
};
```

### ✅ Why This Works

* A bulb ends up **on** only if it is toggled **odd** number of times.
* Bulbs are toggled in rounds that are **divisors** of their position.
* Only **perfect squares** have an **odd number of divisors**.
* Therefore, the number of bulbs that remain on = Number of perfect squares ≤ n = `floor(sqrt(n))`.

---

## Final Notes

* This is a great example of reducing a brute-force simulation to a mathematical insight.
* The optimal solution drastically improves performance and is easy to implement.

---
