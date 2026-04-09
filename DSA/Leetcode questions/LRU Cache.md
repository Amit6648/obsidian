
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
 - So we can use a double linked list here to link and remove elements cause whenever we need to remove a element from middle when it is used and add it to end we need to link the elements around but in a single linked list we can access next element but not the previous and it will be stuck at pointing to the element we want to remove.
 - and whenever we need to get a element by it's key we can use [[Unordered Hash maps]] to store the keys and which node does these keys points to, by doing this  can get to the nodes in O(1) time.
 - We also have to maintain a capacity and when there is a overflow we need to remove the last element in the 

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
