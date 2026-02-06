
---
Status: Mastered
Difficulty: medium
Pattern: sliding window
Last_attempt: 2026-01-28
Next_review: 2026-03-05
Attempts: 1
link: [Longest Repeating Character Replacement](https://leetcode.com/problems/longest-repeating-character-replacement/)

---

# Problem: Longest Repeating Character Replacement

## 💡 Intuition

-  So the problem asks us to find longest sequence of same character with k other allowed characters.
- So the problem is similar to previous [[Sliding Window]] problems just that constraints are different.
- unlike [[Longest Substring Without Repeating Characters]] we have to maintain a max frequent element and then use it to check if the window is valid.
- we can use [[Unordered Hash maps]] to store frequency.
- When window will be invalid we can simply increase the start and then check again if it is valid.
---
### 🧠 Insights And Structures

- [[Unordered Hash maps]]
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
int characterReplacement(string s, int k) {

     vector<int>fre(128,0);

     int maxf = 0;
     int maxi = 0;
     int l = 0;

     for(int r = 0; r<s.length(); r++)
     {
        fre[s[r]]++;

        maxf= max(maxf, fre[s[r]]);

        if(r - l + 1 - maxf <= k)
        {
           maxi =  max(maxi, r-l+1);
        }

        else {
            fre[s[l]]--;
            l++;
        }
     }

     return maxi;
    }
```
