
---
Status: Mastered
Difficulty: Easy 
Pattern: 
Last_attempt: 2026-02-06
Next_review: 2026-02-27
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
- **Time Complexity:** $O(N)$
- **Space Complexity:** $O(N)$
---

## 💻 Implementation (C++)

```cpp
vector<int> twoSum(vector<int>& nums, int target) {
        unordered_map<int, int> pic;
        pic.reserve(nums.size());

        for (int i = 0; i < nums.size(); i++) {
            int find = target - nums[i];

            if (pic.count(find)) {
                return {pic[find], i};
            }

            pic.emplace(nums[i], i);
        }

        return {};
    }
```
