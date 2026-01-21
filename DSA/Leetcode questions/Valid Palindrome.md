
---
Status: 🟢 Mastered
Difficulty: #Easy 
Pattern:  #Two_Pointers
Last_attempt: 2026-01-8
Next_review: 2026-01-8
Attempts: 1
link: [Valid Palindrome](https://leetcode.com/problems/valid-palindrome/)

---

# Problem: Valid Palindrome

## 💡 Intuition

- SO the problem is about checking if a string is a palindrome.
- We can use [[Two pointers]] approach. One pointer left and other Right will check until they are equal if not then we will return false.
---
### 🧠 Insights

---
## ⏱️ Complexity
- **Time Complexity:** $O(n)$
- **Space Complexity:** $O(1)$
---

## 💻 Implementation (C++)


```cpp
bool isPalindrome(string s) {
        
        int i =0 ;

        int j = s.length()-1;

        while(i<=j)
        { 
            while((i<j) && !(s[i]>='a'&& s[i]<='z') && !(s[i]>='0'&& s[i]<='9') && !(s[i]>='A'&& s[i]<='Z'))
            {
               i++;
            }

             while( (i<j) && !(s[j]>='a'&& s[j]<='z') && !(s[j]>='0'&& s[j]<='9') && !(s[j]>='A'&& s[j]<='Z'))
            {
               j--;
            }

           if(tolower(s[j]) != tolower(s[i]))
           {
            return false;
           }

           i++;
           j--;
        }

        return true;


    }
```