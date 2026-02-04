
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
- We can simply use that to our advantage we will use the last element to check if the element is smaller than this element if yes then we know this is the row we can find the element cause other rows will have elements that are bigger than last element.
- if the last element is smaller than target than we can move to next row and do same.
- When we found the correct row we can just simply use binary search on that row to find the target.

---
### 🧠 Insights And Structures
- [[Binary Search]]
---
## ⏱️ Complexity
- **Time Complexity:** $O(nlogn)$
- **Space Complexity:** $O(1)$
---
## 🛡️ Attempt History
### Attempt 1: 2026-02-04
- **Outcome:** (e.g., TLE, Wrong Answer, Solved with Help)
- **What blocked me:** - **Improvement:** ---
---
## 💻 Implementation (C++)


```cpp
bool searchMatrix(vector<vector<int>>& matrix, int target) {
        int r = 0;
        int c = matrix[0].size();

        while (r < matrix.size() && matrix[r][c - 1] < target) {
            r++;
        }
       
        if(r == matrix.size()) return false;

        if (matrix[r][c - 1] == target) {
            return true;
        }

        int s = 0;

        int e = c-1;

        int mid = s + (e - s) / 2;

        while (s <= e) {
            if (matrix[r][mid] == target) {
                return true;
            }

            if (matrix[r][mid] < target) {
                s = mid + 1;
            }

            if (matrix[r][mid] > target) {
                e = mid - 1;
            }

             mid = s + (e - s) / 2;
        }

        return false;
    }
```
