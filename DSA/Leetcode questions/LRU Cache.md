
---
Status: solved with help
Difficulty: medium
Pattern: Linked list
Last_attempt: 2026-04-09
Next_review: 2026-04-09
Attempts: 1
link: [LRU Cache](https://leetcode.com/problems/lru-cache/)

---

# Problem: LRU Cache

## 💡 Intuition

 - So the problem is about creating a data structure that is resembles "Least recently used".
 - So we have to create this using linked lists, so the rules are we have to create two functions one that will add metadata that will have "value and key". When we add this metadata it should be at top when we add the next one that will be at the top.
 - Now the get function that will be used to visit a element's value by using it's key and when a element is visited it will come at the top position meaning now it is the least recently used element.
 - So we can use a double linked list here to 

---
### 🧠 Insights And Structures

---
## ⏱️ Complexity
- **Time Complexity:** $O()$
- **Space Complexity:** $O()$
---
## 🛡️ Attempt History
### Attempt 1: 2026-04-09
- **Outcome:** (e.g., TLE, Wrong Answer, Solved with Help)
- **What blocked me:** - **Improvement:** ---
---
## 💻 Implementation (C++)
