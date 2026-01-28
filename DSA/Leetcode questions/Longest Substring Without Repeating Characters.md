
---
Status: 🔴 Not Solved  # Options: 🔴 Not Solved, Solved with Help, Mastered
Difficulty: #Easy     # Options: #Easy, medium, #Hard
Pattern: # e.g., Sliding Window, Two Pointers, Monotonic Stack
Last_attempt: 2026-01-28
Next_review: 2026-01-28
Attempts: 1
link: [Longest Substring Without Repeating Characters](https://leetcode.com/problems/longest-substring-without-repeating-characters/)

---

# Problem: Longest Substring Without Repeating Characters

## 💡 Intuition

- So the problem asks to find a area that has all unique elements and it should be largest in the array.
- So if we look at the problem it is similar to [[Best Time to Buy and Sell Stock]] cause in that problem the constraint was that previous element must be smaller than next element or we will throw that element out of window.
- Same we have to do here if a element appeared again we will remove it's previous occurrence.
- Just that the difference is that we need to keep track of multiple elements rather than a single element.
- So when we need to keep track of multiple elements and need to access them quickly we use [[Unordered Hash maps]].
- We have to use hash maps rather than sets cause we also need to track when a element appeared so we can know where we should move our starting pointer to get new vailed window.
---
### 🧠 Insights And Structures

- [[Sliding Window]]
- [[Unordered Hash maps]]
- [[Converting the complex problem into easy problem]]


---
## ⏱️ Complexity
- **Time Complexity:** $O(n)$
- **Space Complexity:** $O(n)$
---
## 🛡️ Attempt History
### Attempt 1: 2026-01-28
- **Outcome:** (e.g., TLE, Wrong Answer, Solved with Help)
- **What blocked me:** - **Improvement:** ---
---
## 💻 Implementation (C++)

```cpp
int lengthOfLongestSubstring(string s) {
        int left = 0;

        int right = 0;

        unordered_map<char,int> win;

        int maxi = 0;

        while(right<s.length())
        {
            if(win.count(s[right]) && win[s[right]]>=left)
            {
                maxi = max(maxi, right-left);
                left = win[s[right]] +1;
            }

               maxi = max(maxi,right-left +1);
               win[s[right]] = right; 

               right++;
        }

       

        return maxi;
    }
```

