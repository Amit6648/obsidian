
---
Status: 🟢 Mastered
Difficulty: #Medium 
Pattern: 
Last_attempt: 2026-01-4
Next_review: 2026-01-4
Attempts: 1
link: [Valid Sudoku](https://leetcode.com/problems/valid-sudoku/description/)           

---

# Problem: Valid Sudoku

## 💡 Intuition

- So the question is about checking whether a sudoku board i vailed or not.
- In a sudoku board we have to check if  a cell has a vailed number then there will not be same number in the same row, same column and also same 3X3 box that it is in.
- If we think about it we are trying to find duplicate of a element like problem [[Contains Duplicate]] just that the difference is that rather than find in 1D space we need to find it in 3 directions.
- For the first two directions which are  similar to [[Contains Duplicate]] we can just use [[Unordered Sets]] for each row and column and use the speed to sets to check if a element exists.
- but he problem here is that we have multiples of rows and columns. So we can just use [[Unordered Hash maps]] and use the each row number as key for each row in hash map and we can do same for columns.
- Now the main problem left is 3X3 box. So if we can somehow divide the whole sudoku into 9 parts or  9 of 3X3 boxes and if we can identify in which box does this element exists we can check for the element.
- so the sudoku is of 9 x 9 if we want to know where does a element  of this 9 x 9 box will be we can do simple maths like if i want  to where will 8 no house will be in a street of 9 house and each three houses out of 9 represent a block meaning we a have three block so if we want to know in which block will this house be we can just divide it by three and add 1 which will give us 3 meaning third block.
- here rather than having on only 3 we have a block of 3x3 meaning we have to check 
---
### 🧠 Insights

---
## ⏱️ Complexity
- **Time Complexity:** $O()$
- **Space Complexity:** $O()$
---
## 🛡️ Attempt History
### Attempt 1: 2026-01-21
- **Outcome:** (e.g., TLE, Wrong Answer, Solved with Help)
- **What blocked me:** - **Improvement:** ---
---
## 💻 Implementation (C++)
