
---
Status: 🟡 Solved with Help
Difficulty: #Medium 
Pattern: # e.g., Sliding Window, Two Pointers, Monotonic Stack
Last_attempt: 2026-01-7
Next_review: 2026-01-7
Attempts: 2
link: [Min Stack](https://leetcode.com/problems/min-stack/)

---

# Problem: Min Stack

## 💡 Intuition

- So the questions asks about creating a stack and also giving a extra feature to get minimum element in the stack.
- So we only need to solve for minimum feature rest is just a stack.
- So the main problem for minimum function are storing when a number appeared we need to remember when a number was minimum so when popping we can also know this number was minimum at that time so we can decide whether to remove it or not.
- We can use one more stack to store minimum element by comparing with the top element in minimum we can update stack with new entry or we can just keep the previous one.
- So when we pop a element from main stack we will pop top element in minimum stack and we will have duplicate entries of same element if a new minimum doesn't appeared the duplicate will be popped.

- We can also save this space of using a extra space
---
### 🧠 Insights

---
## ⏱️ Complexity
- **Time Complexity:** $O()$
- **Space Complexity:** $O()$
---
## 🛡️ Attempt History
### Attempt 1: 2026-01-22
- **Outcome:** (e.g., TLE, Wrong Answer, Solved with Help)
- **What blocked me:** - **Improvement:** ---
---
## 💻 Implementation (C++)

```cpp
class MinStack {
public:
    long long min;

    stack<long long> st;

    MinStack() {}

    void push(int val) {

        if (st.empty()) {
            min = val;
        }
        long long temp = val - min;
        if (temp < 0) {
            st.push(temp);
            min = val;
        } else {
            st.push(temp);
        }
    }

    void pop() {
        if (st.top() < 0) {
            min = min - st.top();
            st.pop();
        }

        else {
            st.pop();
        }
    }

    int top() {
        if (st.top() < 0) {
            return min;
        }

        else {
            return st.top() + min;
        }
    }

    int getMin() { return min; }
};
```