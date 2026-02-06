
---
Status: Mastered
Difficulty: Easy
Pattern:  
Last_attempt: 2026-01-4
Next_review: 2026-02-30
Attempts: 1
link:  [Contains Duplicate](https://leetcode.com/problems/contains-duplicate/)

---
# Problem: Contains Duplicate

## 💡Intuition : 

   -  So the problem is about finding duplicates in a array if there is a duplicate then we will return true else false.
   - The brute force method will be using comparing each element with every element in the array that will give us  $O(N^2)$  time complexity.
   - Rather than checking for each element we can use a [[Unordered Sets]] to search elements fast in array
   - When inserting a element we can check if this element have already exist if it does then we will return true.

---
### 🧠 Insights :

- [[Fast memory]]

---

## ⏱️ Complexity

- **Time Complexity:** $O(N)$
- **Space Complexity:** $O(N)$
---
## 💻 Implementation (C++)

```cpp
bool containsDuplicate(vector<int>& nums) {

        unordered_set<int> set;

        set.reserve(nums.size());
        
       for(const  int &ele : nums)
       {
        if(!set.insert(ele).second)
        {
            return true;
        }

       }


       return false;

    
    }
```
