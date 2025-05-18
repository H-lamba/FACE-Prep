
# 📈 LeetCode Problem 121: Best Time to Buy and Sell Stock

## 🚀 Problem Statement

You are given an array `prices` where `prices[i]` is the price of a given stock on the `i`-th day.

You want to maximize your profit by choosing **a single day to buy** one stock and **a different day in the future to sell** that stock.

Return the **maximum profit** you can achieve from this transaction.  
If no profit can be made, return `0`.

---

## 🧠 Examples

### ✅ Example 1:
**Input:**  
`prices = [7,1,5,3,6,4]`  
**Output:**  
`5`  
**Explanation:** Buy on day 2 (price = 1) and sell on day 5 (price = 6), profit = 6 - 1 = 5.

### ✅ Example 2:
**Input:**  
`prices = [7,6,4,3,1]`  
**Output:**  
`0`  
**Explanation:** No profitable transaction is possible.

---

## 💡 Approach

We track:
- The **minimum price** seen so far (`buy`).
- The **maximum profit** we can make if we sell on the current day.

At each step:
- Update the `profit` as the max of current `profit` and `current_price - buy`.
- Update `buy` as the min of current `buy` and `current_price`.

This ensures:
- We buy at the lowest price so far.
- We check the max possible profit at each day if sold then.

---

## 🧾 Code

```cpp
class Solution {
public:
    int maxProfit(vector<int>& prices) {
        int buy = prices[0];
        int profit = 0;
        for (auto i : prices) {
            profit = max(profit, i - buy);
            buy = min(buy, i);
        }
        return profit;
    }
};
````

---

## 🛠️ Time and Space Complexity

* **Time Complexity:** O(n), where `n` is the length of `prices`.
* **Space Complexity:** O(1), as only constant extra space is used.

---

## 📚 Topics

* Array
* Dynamic Programming
* Greedy

