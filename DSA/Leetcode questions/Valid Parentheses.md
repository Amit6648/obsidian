
---
Status:🟡 Solved with Help
Difficulty: #Easy
Pattern: #Stacks
Last_attempt: 2026-01-7
Next_review: 2026-01-7
Attempts: 1
link: [Valid Parentheses](https://leetcode.com/problems/valid-parentheses/)

---

# Problem: Valid Parentheses

## 💡 Intuition

- So the problem is about checking if a string consisting of Parentheses is valid or not. 
- So we know that  Parentheses  are used to contain something meaning if a Parentheses starts it has to have a end.
- So we have to basically check if a Parentheses have a valid end and start.
- We can take Loops as example if a loop starts then it has to have a end but if a loop starts and then rather than it's end we replace it by a start of another loop. Does this statement make sense.
- well we can have loop in only two way either a single loops or branches of loops. in both condition a loop will always have a end or in branches the first the inner loops will end and then the outer ones.
- So now if we return back to Parentheses we need to check if one starts then it has to end and if second one started the second one must end first before first like loops.
- We can take one more example of debt if i take debt then i have to repay it but if i take debt and then try to repay a debt that i haven't taken will that be valid.
- Well that means we have to keep track of most recent open and when it's close appears we will check for previous open and see if it's close appear next.
- we also need to consider if a new open appear we need to close that.
- Well can simply use [[Stacks]] in the form of a [[Monotonic Stack]] where we will only maintain opens and when a corresponding open appear we will pop that open.
- If we are the structure is right we will be left with a empty stack or the structure was wrong.
- And to know open of each close we can use [[Unordered Hash maps]] to use close as a key and open as a value.
---
### 🧠 Insights

---
## ⏱️ Complexity
- **Time Complexity:** $O(N)$
- **Space Complexity:** $O(N)$
---
## 💻 Implementation (C++)


```cpp
bool isValid(string s) {
        if(s.length()%2 == 1) return false;
        
        stack<char> st;

        unordered_map<char, char> cto = {
            {')', '('},
            {'}', '{'},
            {']', '['}
        };


        for(const char ele: s)
        {
            if(cto.count(ele))
            {
                if(!st.empty()&&(st.top() == cto[ele]))
                {
                    st.pop();
                }

                else {
                    return false;
                }
            }

            else {
                st.push(ele);
            }
        }

        return st.empty();

        

    }
```