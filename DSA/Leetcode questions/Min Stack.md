
---
Status: 🟡 Solved with Help
Difficulty: #Medium 
Pattern: # e.g., Sliding Window, Two Pointers, Monotonic Stack
Last_attempt: 2026-01-22
Next_review: 2026-01-22
Attempts: 1
link: [Min Stack](https://leetcode.com/problems/min-stack/)

---

# Problem: Min Stack

## 💡 Intuition

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