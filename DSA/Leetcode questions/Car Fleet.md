
---
Status: Solved with Help
Difficulty: medium
Pattern: stacks
Last_attempt: 2026-01-24
Next_review: 2026-01-24
Attempts: 1
link: 

---

# Problem: Car Fleet

## 💡 Intuition

- So the problem is about if elements catches up or collide before reaching a certain end target.
- So rather than calculating one by one and checking if they matches at the end we can use Math's of [[catchup]] and find about if a element will catches up with others.
- But we also need to short the array of starting distance according to [[catchup]] rule.
- Then the problem is simply about checking if a certain element satisfies previous element and in a order, for which we can use [[Monotonic Stack]].
- We can check if current element is less or equal to previous element that means it will catch up with the element and forms a fl

---
### 🧠 Insights And Structures 

---
## ⏱️ Complexity
- **Time Complexity:** $O()$
- **Space Complexity:** $O()$
---
## 🛡️ Attempt History
### Attempt 1: 2026-01-24
- **Outcome:** (e.g., TLE, Wrong Answer, Solved with Help)
- **What blocked me:** - **Improvement:** ---
---
## 💻 Implementation (C++)
