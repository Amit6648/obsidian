
---
Status:🟢 Mastered
Difficulty: medium 
Pattern: stacks
Last_attempt: 2026-01-7
Next_review: 2026-01-7
Attempts: 1
link: [Evaluate Reverse Polish Notation](https://leetcode.com/problems/evaluate-reverse-polish-notation/)

---

# Problem: Evaluate Reverse Polish Notation

## 💡 Intuition

- So problem asks us to create  a calculator we are given a array or strings and need to do operation in which order they are given.
- We can simply use [[Stacks]] and check if the it is a number or operation and when a operation appears we will just pop two numbers and see and do the operation given on those numbers.
- we can use [[Unordered Hash maps]] to store operations as key and the operation as value when ever  a operation appeared we can just use hash map.
- after performing a operation we will push the result back to stack cause we at least need two numbers to do a operation.

---
### 🧠 Insights And Structures

- [[Unordered Hash maps]]

---
## ⏱️ Complexity
- **Time Complexity:** $O(N)$
- **Space Complexity:** $O(2N)$
---
## 💻 Implementation (C++)


```cpp
int evalRPN(vector<string>& tokens) {
        stack<int> op;

        unordered_map < string, function<int(int, int)>> opm =
        { {"+", plus<int>()},
          {"-", minus<int>()},
          {"*", multiplies<int>()},
          {"/", divides<int>()}

        };

          for (const string &ele : tokens) {
            if (opm.count(ele)) {
                int var2 = op.top();
                op.pop();

                int var1 = op.top();
                op.pop();

                var1 = opm[ele](var1, var2);

                op.push(var1);

            }

            else {
                op.push(stoi(ele));
            }
        }

        return op.top();

    }
```