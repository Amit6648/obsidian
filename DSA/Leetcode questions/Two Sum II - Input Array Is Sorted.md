
---
Status:Mastered
Difficulty: medium 
Pattern: Two_Pointers
Last_attempt: 2026-02-06
Next_review: 2026-02-
Attempts: 1
link: [Two Sum II - Input Array Is Sorted](https://leetcode.com/problems/two-sum-ii-input-array-is-sorted/)

---

# Problem: Two Sum II - Input Array Is Sorted

## 💡 Intuition

- So the question is same as [[Two Sum]] just that this time the array is sorted.
- Rather than taking a extra space using Sets we can use [[Two pointers]] approach here.
- So we know that array is sorted that means left side of array will have smaller elements and right side will have larger elements.
- we can use two pointers left and right and then check if sum of them is equal to the target if not then we can compare if sum was bigger or smaller and move left and right pointer accordingly.
---
### 🧠 Insights

---
## ⏱️ Complexity
- **Time Complexity:** $O(N)$
- **Space Complexity:** $O(1)$
---
## 💻 Implementation (C++)

```cpp
vector<int> twoSum(vector<int>& numbers, int target) {
       
      int left  = 0;

      int right  = numbers.size() -1;

      while(left<right)
      {
        int sum =  numbers[left] + numbers[right];

        if(target == sum)
        {
            return {left+1, right+1};
        }

        else if(target<sum)
        {
            right--;
        }

        else if(target>sum)
        {
            left++;
        }
      }


      return {};
    }
```