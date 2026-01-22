
---
Status: Mastered
Difficulty: medium     
Pattern: 
Last_attempt: 2026-01-4
Next_review: 2026-01-4
Attempts: 1
link: [Products of Array Except Self](https://leetcode.com/problems/product-of-array-except-self/submissions/)               

---

# Problem: Products of Array Except Self

## 💡 Intuition

- So the question is about find the product of all the elements except it self and we have to do this for each element.
- So the brute force method will be to just multiply all elements in the except itself and then store the result in another array. This will give us $O(N^2)$ time complexity.
- If we look at the question closely we can see it is similar to finding [[Prefix Sum]] but the difference is that rather than finding the prefix of one side we have to find prefix of both sides meaning first from left the normal one and then from right.
- The only difference is that when we are going to find prefix till a certain index we need to exclude the current element.
- After doing this on both sides we can simply multiply the same index cause they will hold the product of all the elements except themselves one is right and one is left.

---
### 🧠 Insights

- [[Breaking down problem into subproblems]]
---
## ⏱️ Complexity
- **Time Complexity:** $O(N)$
- **Space Complexity:** $O(N)$
---
## 💻 Implementation (C++)

```cpp
vector<int> productExceptSelf(vector<int>& nums) {

        vector<int> ans;
        ans.reserve(nums.size());
        int left = 1;

        for (int i = 0; i < nums.size(); i++) {
            ans.push_back(left);

            left *= nums[i];
        }

        int right = 1;
        for (int i = nums.size() - 1; i >= 0; i--) {
            ans[i] = ans[i] * right;

            right *= nums[i];
        }

        return ans;
    }
```
