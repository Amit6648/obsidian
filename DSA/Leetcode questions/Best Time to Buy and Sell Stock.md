
---
Status: solved with help
Difficulty: easy
Pattern: sliding window
Last_attempt: 2026-01-27
Next_review: 2026-02-13
Attempts: 1
link:  [Best Time to Buy and Sell Stock](https://leetcode.com/problems/best-time-to-buy-and-sell-stock/)

---

# Problem: Best Time to Buy and Sell Stock

## 💡 Intuition

- So the problem is asking to find maximum difference between two elements in array. Just that the  i(min) < j(max).
- Or if we have to take real life example we can say that if we go to market to buy a shirt and then sell it to next shop. Just that you can't sell the shirt of shop to the shop that was before it.
- You must buy and sell to shops after that shop.
- We can use [[Sliding Window]] approach in which we can have two pointers left pointer will stay at the minimum element so far and right will move to find next minimum while calculating the current results.

---
### 🧠 Insights And Structures

- [[Sliding Window]]


---
## ⏱️ Complexity
- **Time Complexity:** $O(N)$
- **Space Complexity:** $O(1)$
---
## 🛡️ Attempt History

---
## 💻 Implementation (C++)


```cpp
int maxProfit(vector<int>& prices) {
        
        int profit =0;

        int buy = 0;
        int sell = buy+1;

        while(sell<prices.size())
        {
            if(prices[sell]<prices[buy])
            {
                buy = sell;
                sell++;
            }
            else {
                profit = max(profit, prices[sell] - prices[buy]);
                sell++;
            }
        }

        return profit;
    }
```
