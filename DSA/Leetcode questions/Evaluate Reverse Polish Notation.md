
---
Status:🟢 Mastered
Difficulty: #Medium 
Pattern: #Stacks
Last_attempt: 2026-01-7
Next_review: 2026-01-7
Attempts: 1
link: [Evaluate Reverse Polish Notation](https://leetcode.com/problems/evaluate-reverse-polish-notation/)

---

# Problem: Evaluate Reverse Polish Notation

## 💡 Intuition

- So problem asks us to create  a calculator we are given a array or strings and need to do operation in which order they are given.
- We can simply use [[Stacks]] and check if the it is a number or operation and when a operation appears we will just pop two number and see if we  


---
### 🧠 Insights And Structures

---
## ⏱️ Complexity
- **Time Complexity:** $O()$
- **Space Complexity:** $O()$
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