
---
Status:  solved with Help
Difficulty: hard
Pattern: sliding window
Last_attempt: 2026-01-30
Next_review: 2026-01-30
Attempts: 1
link: [Minimum Window Substring](https://leetcode.com/problems/minimum-window-substring/)

---

# Problem: Minimum Window Substring

## 💡 Intuition

- Well this problem is similar to [[Permutation in String]] just that a window is valid until we have all the characters and their frequencies.
- It doesn't matter if we have lot of unnecessary elements in it.
- But the condition here is that we have to find a window that have least of these unnecessary elements.
- Well the main problem is that we can ignore other characters but we can't ignore the character that we need to count.
- like we know that we need 2 a's and we have 4 a's in our window our window is valid and then we want to shrink the window to check if the window can be made smaller. So we a removed one a from window.
- Now how are we going to know if this a window is valid we can compare the element in both maps but what about shrinking logic.
- We have to shrink the window until it is not valid meaning we have to check every time if the window is valid then we shrink but to check manually if all the element in map2 are greater than or equal to map1 then we have to loop on both maps to check if they satisfy the condition
- To optimize this we can just create separate goals or needs if a character satisfy this need we increase the count and when all the needs are satisfied we will start to shrink the window.
- When we remove a element from window we will check if this character still satisfy that character frequency if not we will just decrease the count  and we will know that the window is invalid.
- SO basically problem is different from previous problems like [[Permutation in String]] rather than having a fixed target we have a quota that we have to reach 
---
### 🧠 Insights And Structures

---
## ⏱️ Complexity
- **Time Complexity:** $O()$
- **Space Complexity:** $O()$
---
## 🛡️ Attempt History
### Attempt 1: 2026-01-30
- **Outcome:** (e.g., TLE, Wrong Answer, Solved with Help)
- **What blocked me:** - **Improvement:** ---
---
## 💻 Implementation (C++)
