
---
Status: solved with help
Difficulty: medium
Pattern: binary search
Last_attempt: 2026-02-05
Next_review: 2026-02-05
Attempts: 1
link: [Koko Eating Bananas](https://leetcode.com/problems/koko-eating-bananas/)

---

# Problem: Koko Eating Bananas

## 💡 Intuition

- So the problem is about find the minimum possible time koko will take to eat her bananas.
- well the problem is just a generic [[Binary Search]] .
- well we know to get least bananas for the given time constraint. we know at least the largest element will be the possible speed.
- Well we can simply use the largest element to form a range 0 to largest.
- Now the only work left is to find the smallest possible element that satisfies that condition.
- and when we have to find something in sorted array the binary search is best for that we can compare the result if we go more time then we can look at the higher side cause at least there will be the number that can do it in time constraint.
- If we got the less time then we should look at lower side to check for element that may be able to do it in time.

---
### 🧠 Insights And Structures

- [[own invention]]
- [[Binary Search]]

---
## ⏱️ Complexity
- **Time Complexity:** $O(nlog(max(p)))$
- **Space Complexity:** $O(1)$
---
## 🛡️ Attempt History
### Attempt 1: 2026-02-05
- **Outcome:** (e.g., TLE, Wrong Answer, Solved with Help)
- **What blocked me:** - **Improvement:** ---
---
## 💻 Implementation (C++)


```cpp
int minEatingSpeed(vector<int>& piles, int h) {
        int max = *max_element(piles.begin(), piles.end());
        int hours = 0;

        int s = 1;
        int e = max;
        int mid = s + (e - s) / 2;

        int mini = max;
        while (s <= e) {
            long long hours = 0;
            for (const int p : piles) {
                hours += ((long long)p + mid - 1) / mid;
            }

            if (hours <= h) {
                e = mid - 1;

                mini = min(mid, mini);
            }

            if (hours > h) {
                s = mid + 1;
            }

            mid = s + (e - s) / 2;
        }

        return mini;
    }
```

