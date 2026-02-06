
---
Status: Solved with Help
Difficulty: medium 
Pattern: stacks
Last_attempt: 2026-01-7
Next_review: 2026-02-9
Attempts: 2
link: [Min Stack](https://leetcode.com/problems/min-stack/)

---

# Problem: Min Stack

## 💡 Intuition

- So the questions asks about creating a stack and also giving a extra feature to get minimum element in the stack.
- So we only need to solve for minimum feature rest is just [[Stacks]].
- So the main problem for minimum function are storing when a number appeared we need to remember when a number was minimum so when popping we can also know this number was minimum at that time so we can decide whether to remove it or not.
- We can use one more stack to store minimum element by comparing with the top element in minimum we can update stack with new entry or we can just keep the previous one.
- So when we pop a element from main stack we will pop top element in minimum stack and we will have duplicate entries of same element if a new minimum doesn't appeared the duplicate will be popped. we are essentially maintaining a [[Monotonic Stack]].

- We can also save this space of using a extra stack by storing the differences of minimums in original stack.
- Well the main problem will be to how to know when minimum changed. we know that when a minimum number appeared and we decrease it from our current minimum we will get a negative number that will represent one part of our previous minimum.
- we can just check if we got a minimum number at top and use that to find what our previous number was.
- For example we cut a wooden log using cutter that can adapt to the size of the cut it made then when i need to know the original size of the log i can just tape log and cutter with each other and find it's full size.
---
### 🧠 Insights

---
## ⏱️ Complexity
- **Time Complexity:** $O(N)$
- **Space Complexity:** $O(N)$
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