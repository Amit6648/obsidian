
---
Status: Solved with 
Difficulty: #Hard 
Pattern: #Two_Pointers 
Last_attempt: 2026-01-9
Next_review: 2026-01-9
Attempts: 1
link: [Trapping Rain Water](https://leetcode.com/problems/trapping-rain-water/)

---

# Problem: Trapping Rain Water

## 💡 Intuition

- So the problem asks us to find how much water we can hold between two walls but unlike [[Container With Most Water]] we have to find water between multiples walls like a swimming pool with lot of walls in it.
- So if we just tried to check from one side like calculating water until we find a larger wall it will work if we get a larger wall but if we didn't get a greater wall then we will get wrong result cause we are finding according to greater wall
- We can look at it like this if we have two wall we can't tell how much water we can hold by just looking at one wall. So that means we have to look at know walls on both sides.
- we know that we can find maximum water a container can hold by looking at the smaller wall. so to check for multiple walls we only need to find a smaller wall cause the result only depends on that even if one wall is 100 and other is 2 and we just know that wall A is greater than b that means result depends on wall b.
- So according to this intuition we don't need to know absolute value of greater wall we just need to know that it exists.
- We can use the same approach as [[Container With Most Water]] just that we need to remember for each side what
---
### 🧠 Insights

---
## ⏱️ Complexity
- **Time Complexity:** $O()$
- **Space Complexity:** $O()$
---
## 🛡️ Attempt History
### Attempt 1: 2026-01-22
- **Outcome:** (e.g., TLE, Wrong Answer, Solved with Help)
- **What blocked me:** - **Improvement:** ---
---
## 💻 Implementation (C++)
