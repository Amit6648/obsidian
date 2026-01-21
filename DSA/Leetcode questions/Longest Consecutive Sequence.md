
---
Status: 🟢 Mastered
Difficulty: #Medium
Pattern: 
Last_attempt: 2026-01-4
Next_review: 2026-01-4
Attempts: 1
link: [Longest Consecutive Sequence](https://leetcode.com/problems/longest-consecutive-sequence/)

---

# Problem: Longest Consecutive Sequence

## 💡 Intuition

- So the problem is about finding the longest sequence in the array.
- Well if we look at problem it is simply telling us to find elements in array so when we need to find something we always use something that can allow us to search fast.
- We can simply use a set to store all the elements in [[Unordered Sets]] and for each element we can check if we can find it's next element and count the chain until it breaks.
- But we can make it more optimized so chain or sequence must have a head meaning a starting element so we can only try to form a sequence from elements that doesn't have any element before them for example in the sequence 12345 we know our head is 1 so it is not wise to check sequence from 3 cause we know we can get a much bigger sequence.

---
### 🧠 Insights

- [[Fast memory]]
- [[Greater or shorter ignore]] 
---
## ⏱️ Complexity
- **Time Complexity:** $O(N)$
- **Space Complexity:** $O(N)$
---

---
## 💻 Implementation (C++)
