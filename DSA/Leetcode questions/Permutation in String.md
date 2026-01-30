
---
Status: solved with help
Difficulty: medium
Pattern:  sliding window
Last_attempt: 2026-01-28
Next_review: 2026-01-28
Attempts: 1
link: [Permutation in String](https://leetcode.com/problems/permutation-in-string/)

---

# Problem: Permutation in String

## 💡 Intuition

- So the problem asks use to find same number of frequencies of s1 string in larger string s2's certain window.
- In problem we use [[Sliding Window]] approach. So the constraints are that the length of window is equal to s1 and the window should have same character frequencies as s1.
- as we know we have to remember frequencies so we can use [[Unordered Hash maps]] to store those frequencies and match them everytime.

---
### 🧠 Insights And Structures
- [[Unordered Hash maps]]
- [[Sliding Window]]
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
bool checkInclusion(string s1, string s2) {
     vector<int> st1(26,0);
     vector<int> st2(26,0);

     int n1 = s1.length();

     int n2 =  s2.length();

     if(n1>n2) return false;

     for(int i  =0 ; i<n1; i++)
     {
        st1[s1[i] - 'a']++;
        st2[s2[i] - 'a']++;
     }

     if(st1 == st2) return true;


     for(int i = n1; i<n2; i++)
     {
        st2[s2[i - n1] - 'a']--;

        st2[s2[i] - 'a']++;

     if(st1 == st2) return true;
     }


return false;

    }
```
