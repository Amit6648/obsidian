
---
Status: solved with help
Difficulty: medium
Pattern: linked list
Last_attempt: 2026-04-07
Next_review: 2026-04-07
Attempts: 1
link: [Copy List with Random Pointer](https://leetcode.com/problems/copy-list-with-random-pointer/)

---

# Problem: Copy List with Random Pointer

## 💡 Intuition

- We in this problem we need to create a exact copy of a linked list.
- As we know that there are two main attributes of a single linked list  " a value and a data" but in this problem we also have one more attribute "random".
- Random is a pointer that can point to any element.
- So now we need to create exact copy but the problem is that lets say we created a new copy element now it's random points to some element but in our copied list that element still has not been created then how can we even point to it.
- Well we can use [[Unordered Hash maps]] to store each element and their copy so after we have created the copy we can loop through "map" and for each original element we can check it's random in hash map and by doing this we can simply link elements.
- But we can improve space complexity by removing "hash map".  So by analysing the hash map method we know that we have to ea

---
### 🧠 Insights And Structures

---
## ⏱️ Complexity
- **Time Complexity:** $O()$
- **Space Complexity:** $O()$
---
## 🛡️ Attempt History
### Attempt 1: 2026-04-07
- **Outcome:** (e.g., TLE, Wrong Answer, Solved with Help)
- **What blocked me:** - **Improvement:** ---
---
## 💻 Implementation (C++)
