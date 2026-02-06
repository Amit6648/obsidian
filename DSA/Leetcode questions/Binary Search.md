
---
Status: solved with help
Difficulty: easy
Pattern: binary search
Last_attempt: 2026-02-02
Next_review: 2026-02-16
Attempts: 1
link: [Binary Search](https://leetcode.com/problems/binary-search/)

---

# Problem: Binary Search

## 💡 Intuition

- So the question is about searching a element in array that is sorted.
- We can can use different data structures like hashmaps or set but still we have to store the elements that will be 0(N).
- To improve the efficiency there is a technique called [[divide and conquer]].
- We can simply divide the space into two part one side representing greater numbers and one side is representing smaller numbers it is similar to [[Two Sum II - Input Array Is Sorted]].
- In this technique we use a middle pointer that represents a the current element and according to what we have to search we have to manipulate the mid.
- So we basically use two more pointers start and end. these to pointers represent ends of the search space and mid find the target element so we can simply divide the search space as many times as want according to the element we want to find.
- Well it is like searching a page in book we can go to middle and check if the page we are finding is less than or greater and then change our search space.
---
### 🧠 Insights And Structures

- [[divide and conquer]]

---
## ⏱️ Complexity
- **Time Complexity:** $O(logn)$
- **Space Complexity:** $O(n)$
---
## 🛡️ Attempt History
### Attempt 1: 2026-02-02
- **Outcome:** (e.g., TLE, Wrong Answer, Solved with Help)
- **What blocked me:** - **Improvement:** ---
---
## 💻 Implementation (C++)

```cpp
 int search(vector<int>& nums, int target) {
        int s = 0;

        int e = nums.size() - 1;

        int  mid =  s + (e-s)/2;

        while(s<=e)
        {
            if(nums[mid] == target) return mid;

            if(nums[mid]> target) e = mid - 1;

            if (nums[mid]<target) s = mid + 1;

            mid = s + (e-s)/2;;
        }

        return -1;
    }
```
