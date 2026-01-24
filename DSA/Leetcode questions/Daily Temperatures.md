
---
Status: Solved with Help
Difficulty: medium
Pattern: stacks
Last_attempt: 2026-01-24
Next_review: 2026-01-24
Attempts: 1
link:  [Daily Temperatures](https://leetcode.com/problems/daily-temperatures/)

---

# Problem: Daily Temperatures

## 💡 Intuition

- So the problem tells us to find after how many indices can we find larger number than current number but we have to do this for each element.
- We can use two pointers one at current element and other will find next bigger but this will give use complexity of $O(N^2)$.
- We might be tempted to use hashmaps but hashmaps are good for searches but not good for structed or ordered search it can return any greater element in the array rather than next greatest.
- We can use a [[Monotonic Stack]] here cause we need structure also so we can maintain order.
- we can keep a element in stack until a element greater than it appears and then pop it when we find a greater.
- Also rather than storing elements directly we can [[store indices]] to access both distance and element at same time.

---
### 🧠 Insights And Structures

- [[Monotonic Stack]]
- [[store indices]]

---
## ⏱️ Complexity
- **Time Complexity:** $O(N)$
- **Space Complexity:** $O(N)$
---
## 💻 Implementation (C++)


```cpp
 vector<int> dailyTemperatures(vector<int>& temperatures) {
        stack<int> wait;
        vector<int> diff(temperatures.size(), 0);

        for(int i = 0; i<temperatures.size(); i++)
        {
           while(!wait.empty() && temperatures[i] > temperatures[wait.top()] )
           {
            diff[wait.top()] =  i - wait.top();
            wait.pop();
           }

           wait.push(i);
        }

        return diff;
    }
```
