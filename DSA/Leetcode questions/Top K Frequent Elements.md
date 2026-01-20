
---
Status: 🟢 Mastered
Difficulty: #Medium 
Pattern: 
Last_attempt: 2026-01-4
Next_review: 2026-01-4
Attempts: 1
link: [Top K Frequent Elements](https://leetcode.com/problems/top-k-frequent-elements/description/)

---

# Problem: Top K Frequent Elements

## 💡 Intuition

- So the question is about find greatest times a number have appeared in a array but the catch is rather than finding a single number we have to find **K** of them.
- So the question basically tell use to find frequencies of all the elements in the arrays and then return k Greatest frequencies.
- Well for frequencies we can basically use [[Unordered Hash maps]]. But the problem is that how can we pick only top k elements.
- We can use a minimum [[priority queue]]. Where we can maintain push all the elements in our hash map and when the size of queue is more than k we can pop element that is at the top.
- After all this we can just return the left over elements.

---
### 🧠 Insights
[[f]]

---
## ⏱️ Complexity
- **Time Complexity:** $O(NLogK)$
- **Space Complexity:** $O(N)$
---
## 💻 Implementation (C++)

```cpp
vector<int> topKFrequent(vector<int>& nums, int k) {
        priority_queue<pair<int, int>, vector<pair<int, int>>,greater<pair<int, int>>> max;

        unordered_map<int, int> map;

        map.reserve(nums.size());

        vector<int> ans;

        ans.reserve(k);

        for (const int& ele : nums) {
            map[ele]++;
        }

        for (const auto& ele : map) {
            max.push({ele.second, ele.first});

            if (max.size() > k) {
                max.pop();
            }
        }

        while (!max.empty()) {
            ans.push_back(max.top().second);

            max.pop();
        }

        return ans;
    }
```
