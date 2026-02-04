
---
Status: solved with help
Difficulty: medium
Pattern: binary search
Last_attempt: 2026-02-04
Next_review: 2026-02-04
Attempts: 1
link: [Search a 2D Matrix](https://leetcode.com/problems/search-a-2d-matrix/)

---

# Problem: Search a 2D Matrix

## 💡 Intuition

- So the problem is same [[Binary Search]] just that we have to search a element in a 2d array.
- well the array is structed in a way that last element of each row is greatest element in that row.
- We can simply use that to our advantage we will use the last element to check if the element is smaller than this element if yes then we know this is the row we can find the element cause other rows will have elements that are bigger than last

---
### 🧠 Insights And Structures

---
## ⏱️ Complexity
- **Time Complexity:** $O()$
- **Space Complexity:** $O()$
---
## 🛡️ Attempt History
### Attempt 1: 2026-02-04
- **Outcome:** (e.g., TLE, Wrong Answer, Solved with Help)
- **What blocked me:** - **Improvement:** ---
---
## 💻 Implementation (C++)
