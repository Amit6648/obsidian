
---
Status: solved with help
Difficulty: easy
Pattern: binary search
Last_attempt: 2026-02-02
Next_review: 2026-02-02
Attempts: 1
link: [Binary Search](https://leetcode.com/problems/binary-search/)

---

# Problem: Binary Search

## 💡 Intuition

- So the question is about searching a element in array that is sorted.
- We can can use different data structures like hashmaps or set but still we have to store the elements that will be 0(N).
- To improve the efficiency there is a technique called [[divide and conquer].
- We can simply divide the space into two part one side representing greater numbers and one side is representing smaller numbers it is similar to [[Two Sum II - Input Array Is Sorted]].
- In this technique we use a middle pointer that represents a the current element and according to what we have to search we have to manipulate the mid.
- So we basically use two more pointers start and end. these to pointers represent ends of the search space and mid find the target element so we can simply divide the search space as many times as want according to the element we want to find.
- Well it is like searching a page in book we can 
---
### 🧠 Insights And Structures

---
## ⏱️ Complexity
- **Time Complexity:** $O()$
- **Space Complexity:** $O()$
---
## 🛡️ Attempt History
### Attempt 1: 2026-02-02
- **Outcome:** (e.g., TLE, Wrong Answer, Solved with Help)
- **What blocked me:** - **Improvement:** ---
---
## 💻 Implementation (C++)
