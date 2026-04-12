
---
Status: not solved
Difficulty: Hard
Pattern: Binary search
Last_attempt: 2026-04-12
Next_review: 2026-04-12
Attempts: 1
link: [Median of Two Sorted Arrays](https://leetcode.com/problems/median-of-two-sorted-arrays/)

---

# Problem: Median of Two Sorted Arrays

## 💡 Intuition

- So the problem asks us to find median of a sorted array but rather than one array we have to find it according to two arrays and both are sorted.
- both arrays have unique values meaning other will not have the same elements as the other one.
- Well we are not allowed to merge the both arrays cause that will increase the time complexity.
- So here is how we solve this problem so we divide the both arrays in two parts one will contain the smaller elements than the other part and to do that we will use binary search on smaller array it is like having two wooden planks one is shorter and we have to move them so the matching line on both planks will connect to each other.
- So we know that bigger plank is heavy and will require more energy to move so we will basically move the smaller to save the energy.
- So same here we will use binary search on smaller array and divide it and then according the elements we have on our left side we will decide how many to take from the left side of the larger array.
- Now we have divided both arrays equally so to see if the partition that we have created is right we will compare them in cross meaning small left  with large right  and large left with smaller right.
- but why do we only compare these , well cause the arrays are sorted if we divide the larger array then the left side will always have small elements than right.

---
### 🧠 Insights And Structures

---
## ⏱️ Complexity
- **Time Complexity:** $O()$
- **Space Complexity:** $O()$
---
## 🛡️ Attempt History
### Attempt 1: 2026-04-12
- **Outcome:** (e.g., TLE, Wrong Answer, Solved with Help)
- **What blocked me:** - **Improvement:** ---
---
## 💻 Implementation (C++)
