
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
- here rather than having on only 3 we have a block of 3x3 meaning we have to check two directions so we can use row and column as key and divide them by 3 to find out in which block they are in but rather than using [[Unordered Hash maps]] we  will use Standard Map where we can use pair as a key.
---
### 🧠 Insights

- [[Fast memory]]
- 

---
## ⏱️ Complexity
- **Time Complexity:** $O(N)$
- **Space Complexity:** $O(N)$
---
## 💻 Implementation (C++)

```cpp
bool isValidSudoku(vector<vector<char>>& board) {

        unordered_map<int, unordered_set<int>> rows;

        unordered_map<int, unordered_set<int>> cols;

        map<pair<int, int>, unordered_set<int>> box;

        for(int row =0; row<board.size(); row++)
        {
            for(int col = 0; col<board.size(); col++)
            {

                if(board[row][col] == '.') continue;
                if(!rows[row].insert(board[row][col]).second)
                {
                    return false;
                }

                 if(!cols[col].insert(board[row][col]).second)
                {
                    return false;
                }

                 if(!box[{row/3,col/3}].insert(board[row][col]).second)
                {
                    return false;
                }
            }
        }

        return true;
    }
```
