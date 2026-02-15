
---
Status: solved with help
Difficulty: medium
Pattern: binary search
Last_attempt: 2026-02-15
Next_review: 2026-02-15
Attempts: 1
link:  [Time Based Key-Value Store](https://leetcode.com/problems/time-based-key-value-store/)



# Problem: Time Based Key-Value Store

## 💡 Intuition

- So the problem was about Creating a data structure.
- we have to search the in key value data in such a way that first is key and then in that key there are different states of data according to timestamps.
- Well for the key search we can use [[Unordered Hash maps]].
- and for storing the data according to time stamp we can use vectors or arrays to store that in the form of pairs (timestamp, value).
- So when we are asked to find a specific key we can look at the key and find the timestamp that has been asked in that array well the timestamps are going to be in order ( previous< new) so we can use binary search to find that particular data.
- Now the main problem that is if the timestamp doesn't exist then we have to find closest minimum timestamp data.
- To this we can either store the elements that has timestamp less or equal to our target timestamp so at the end we can have the minimum closest or the target.
- But there is a better way to do this if we use [[Binary Search]] collision. In this the right or end pointer always end up at minimum closest due to nature of binary search until we don't have any element minimum than target there right will be -1.
- So at the end we can just return element at the right position.

---
### 🧠 Insights And Structures

- [[Binary Search]]
- [[Unordered Hash maps]]

---
## ⏱️ Complexity
- **Time Complexity:** $O(logn)$
- **Space Complexity:** $O()$
---
## 🛡️ Attempt History
### Attempt 1: 2026-02-15
- **Outcome:** (e.g., TLE, Wrong Answer, Solved with Help)
- **What blocked me:** - **Improvement:** ---
---
## 💻 Implementation (C++)

```cpp
unordered_map<string,vector<pair<int, string>> > store;
    TimeMap() {
    }
    
    void set(string key, string value, int timestamp) {
        store[key].push_back({timestamp, value});
    }
    
    string get(string key, int timestamp) {
        
        if(!store.count(key)) return "";

        const auto &range =  store[key];

        int l = 0;

        int r =  range.size() - 1;

        while(l<=r)
        {
            int mid =  l + (r-l)/2;

            if(range[mid].first == timestamp)

            {
                return range[mid].second;
            }

            if(range[mid].first < timestamp)
            {
                l =  mid + 1;
            }

            else {
                r = mid - 1;
            }

        }

        if(r != -1) return range[r].second;

        else return "";

     }
```
