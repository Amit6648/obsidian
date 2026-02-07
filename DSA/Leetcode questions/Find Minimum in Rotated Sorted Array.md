
---
Status: solved with help
Difficulty: medium
Pattern: binary search
Last_attempt: 2026-02-07
Next_review: 2026-02-07
Attempts: 1
link: [Find Minimum in Rotated Sorted Array](https://leetcode.com/problems/find-minimum-in-rotated-sorted-array/)

---

# Problem: Find Minimum in Rotated Sorted Array

## 💡 Intuition

- So the problem is about finding minimum element in a rotated or non rotated array.
- Well if we look at the rotation it is right rotation meaning either the minimum element is going to be on right side or it is going to be  a normal array.
- Well if we look at the question we can divide the array into two sides one which has higher slope and one which has smaller slope.
- if the array is normal the slope is going to be only one and at the end or right side of array.
- Now if we look closely what we need to find it is the side with smaller slope cause there will be minimum.
- so we can use binary search here just that we can only compare our mid with right most or the smaller slope to check if we are on smaller slope side or bigger one.
- It will work for minimum also cause the normal slope end or smaller slope bi

---
### 🧠 Insights And Structures

---
## ⏱️ Complexity
- **Time Complexity:** $O()$
- **Space Complexity:** $O()$
---
## 🛡️ Attempt History
### Attempt 1: 2026-02-07
- **Outcome:** (e.g., TLE, Wrong Answer, Solved with Help)
- **What blocked me:** - **Improvement:** ---
---
## 💻 Implementation (C++)
