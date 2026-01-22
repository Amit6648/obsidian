
---
Status: Mastered
Difficulty: medium 
Pattern: Two_Pointers 
Last_attempt: 2026-01-9
Next_review: 2026-01-9
Attempts: 1
link: [3Sum](https://leetcode.com/problems/3sum/)

---

# Problem: 3Sum

## 💡 Intuition

- So the problem is similar to [[Two Sum]] but the thing is we have to find sum of three elements and but the problem is that we can use a set here to check if the elements are match cause we have to do 3 comparisons which i going to be complex and less optimized.
- But we can convert this problem into [[Two Sum II - Input Array Is Sorted]]. Meaning if we can short the whole array and then lock one element and then rest is [[Two Sum II - Input Array Is Sorted]] cause we only have to compare two element and we can take the advantage of sorted array.
---
### 🧠 Insights

- [[Converting the complex problem into easy problem]]

---
## ⏱️ Complexity
- **Time Complexity:** $O(n^2)$
- **Space Complexity:** $O(1)$
---
## 💻 Implementation (C++)

```cpp
vector<vector<int>> threeSum(vector<int>& nums) {
        vector<vector<int>> ans;

        sort(nums.begin(), nums.end());

        for (int i = 0; i < nums.size(); i++) {

            if (i > 0 && (nums[i] > 0 || nums[i] == nums[i - 1]))
                continue;
            int left = i + 1;
            int right = nums.size() - 1;

            while (left < right) {
                int sum = nums[i] + nums[left] + nums[right];

                if (sum == 0) {
                    ans.push_back({nums[i], nums[left], nums[right]});

                    while (left < right && nums[left] == nums[left + 1])
                        left++;

                    while (left < right && nums[right] == nums[right - 1])
                        right--;

                    right--;
                    left++;

                }

                else if (sum < 0) {
                    left++;
                }

                else if (sum > 0) {
                    right--;
                }
            }
        }

        return ans;
    }
};
```
