
---
Status: solved with help
Difficulty: medium
Pattern: sliding window
Last_attempt: 2026-01-30
Next_review: 2026-01-30
Attempts: 1
link: [Sliding Window Maximum](https://leetcode.com/problems/sliding-window-maximum/)

---

# Problem: Sliding Window Maximum

## 💡 Intuition

- So the problem  is about finding a maximum each time in a window of specific size.
- The main problem here is that we need to find maximum every time in window and store it in a separate array.
- We can use loops for each window but that would be slow we need to some store our elements in such way that we can find a maximum.
- Well this problem kind of links to [[Best Time to Buy and Sell Stock]]  just that the conditions are more complex.
- like [[Best Time to Buy and Sell Stock]] we have to find max each time while removing the previous max or keeping it if it is still max.
- Just that there is another condition that window also moves so we can't have a max that is out of window. this also gives us the problem of remembering numbers that are smaller than max cause if max is out of window that will be next max.
- if we look at the problem closely if a number that is greater than the elements in the window then the chance of previous numbers becoming greater is zero so will need to get rid of numbers that are smaller than new number.
- Well now if we look at it it is just a [[Monotonic Stack]] where we are maintaining number from greater to smaller.
- The only problem is that we have to update the lower numbers also to remove smaller older number.
- For this we can use a [[dequeue]] which is mix of queue and stack or a stack with two ends. this allows us to access both ends to update.
---
### 🧠 Insights And Structures

- [[Monotonic Stack]]
- [[dequeue]]
- [[Sliding Window]]
---
## ⏱️ Complexity
- **Time Complexity:** $O(n)$
- **Space Complexity:** $O(n)$
---
## 🛡️ Attempt History
### Attempt 1: 2026-01-30
- **Outcome:** (e.g., TLE, Wrong Answer, Solved with Help)
- **What blocked me:** - **Improvement:** ---
---
## 💻 Implementation (C++)


```cpp
vector<int> maxSlidingWindow(vector<int>& nums, int k) {
        deque<int> d;

        vector<int>ans;


        for(int i = 0; i<nums.size(); i++)
        {
           while(!d.empty() && nums[i]> nums[d.back()])
           {
            d.pop_back();
           }

           d.push_back(i);

           if(d.front() == i - k)
           {
            d.pop_front();
           }

           if(i + 1 >= k )
           {
            ans.push_back(nums[d.front()]);
           }
        }

        return ans;
    }
```
