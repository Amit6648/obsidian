
---
Status: 🟢 Mastered
Difficulty: #Easy
Pattern: 
Last_attempt: 2026-01-4
Next_review: 2026-01-4
Attempts: 1
link: [Valid Anagram](https://leetcode.com/problems/valid-anagram/description/)

---

# Problem: Valid Anagram

## 💡 Intuition

- So the problem is about checking if string a is anagram of string b. 
- The brute force method will to sort both strings and checking if they are equal but this approach will take $O(nLogn) + O(nLogn)$ to sort both strings.
- If we look closely a anagram of a string  is basically means both strings have same number of and exact same characters.
- If we just store all the characters and their frequencies in two [[Unordered Hash maps]] and then compare those we can achieve $O(N)$ time complexity.
---
### 🧠 Insights

 - [[Fast memory]]
---
## ⏱️ Complexity
- **Time Complexity:** $O()$
- **Space Complexity:** $O()$
---

## 💻 Implementation (C++)
