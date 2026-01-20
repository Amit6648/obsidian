
---
Status: 🟢 Mastered
Difficulty: #Medium 
Pattern: 
Last_attempt: 2026-01-4
Next_review: 2026-01-4
Attempts: 1
link: [Group Anagrams](https://leetcode.com/problems/group-anagrams/description/)

---

# Problem: Group Anagrams

## 💡 Intuition

- So the question is about Sorting all the anagrams in separate containers or arrays 
- This question is kind of similar to [[Valid Anagram]] cause same as before we have to check if this string is anagram of another string just that we have to compare multiple of them and put same ones in different container.
- The Brute force method can be same as [[Valid Anagram]] sort first string and then compare with all the other strings in the array while also sorting them this will be like way too much slow like $O(N^2.(KlogK))$. 
- So if we treat each string as  a element we can basically say that we have to find elements that are same. so rather than comparing elements normal way we can use a [[Unordered Hash maps]] we can use a element as a key and store all the elements in the value that match it. 
- but here we have strings we can simply sort a string and keep it as a key while storing itself and then for each element we can check if the element matches this key by sorting the element then the element 

---
### 🧠 Insights

---
## ⏱️ Complexity
- **Time Complexity:** $O()$
- **Space Complexity:** $O()$
---
## 🛡️ Attempt History
### Attempt 1: 2026-01-20
- **Outcome:** (e.g., TLE, Wrong Answer, Solved with Help)
- **What blocked me:** - **Improvement:** ---
---
## 💻 Implementation (C++)
