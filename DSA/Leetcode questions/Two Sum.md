
---
Status: 🟢 Mastered
Difficulty: #Easy 
Pattern: 
Last_attempt: 2026-01-4
Next_review: 2026-01-4
Attempts: 1
link: [Two sum](https://leetcode.com/problems/two-sum/description/)     

---

# Problem: Two Sum

## 💡 Intuition

- The problem is about finding a target element that is sum of two distinct elements from array.
- Brute force method will be to compare each element with every other element in the array and see if they add up to target this will give us $O(n^2)$ time complexity.
- If we think about if we can store all this elements are access them all in $O(1)$ time then for whole array we can do this in $O(N)$.
- So we can basically use [[Unordered Hash maps]] to store elements and their indexes as we will add a element we will check if we have seen this element's left over part or **Target - current element** this approach is similar to [[Contains Duplicate]] where we find if we find the partner of it. 

---
### 🧠 Insights

- [[Fast memory]]

---
## ⏱️ Complexity
- **Time Complexity:** $O()$
- **Space Complexity:** $O()$
---
## 🛡️ Attempt History
### Attempt 1: 2026-01-20
- **Outcome:** (e.g., TLE, Wrong Answer, Solved with Help)
- **What blocked me:** - **Improvement:** ---
---
## 💻 Implementation (C++)
