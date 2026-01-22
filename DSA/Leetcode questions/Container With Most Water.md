
---
Status:🟢 Mastered
Difficulty: #Medium 
Pattern: Two_Pointers
Last_attempt: 2026-01-9
Next_review: 2026-01-9
Attempts: 1
link: [Container With Most Water](https://leetcode.com/problems/container-with-most-water/)

---

# Problem: Container With Most Water

## 💡 Intuition

- So the Question is asking about Finding maximum water we can hold in between walls 
- The maximum water capacity can determined by two factor minimum between two walls or elements and the difference between the indices of elements 
- We can use [[Two pointers]] approach we have one pointer at left and one at right and then calculate the area between them.
- Now to decide which pointer to move well we need maximum that mean in such a way that we can have possibility of having a bigger wall on both sides.
- That means we can move the smaller wall pointer and calculate for next wall.

---
### 🧠 Insights

- [[Greater or shorter ignore]]

---
## ⏱️ Complexity
- **Time Complexity:** $O(N)$
- **Space Complexity:** $O(1)$
---
## 💻 Implementation (C++)

```cpp
int maxArea(vector<int>& height) {
        int maxw = 0;

        int left = 0;
        int right = height.size()-1;

        while(left<right)
        {
            int area = (right - left) * min(height[left], height[right]);

            maxw = max(maxw,area);

            if(height[left]<=height[right]) left++;

            else if(height[left]>height[right]) right--;

        }

        return maxw;
    }
```
