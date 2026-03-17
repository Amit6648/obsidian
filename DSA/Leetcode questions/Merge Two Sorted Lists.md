
---
Status: solved with help
Difficulty: easy
Pattern: linked list
Last_attempt: 2026-02-17
Next_review: 2026-02-17
Attempts: 1
link: [Merge Two Sorted Lists](https://leetcode.com/problems/merge-two-sorted-lists/)

---

# Problem: Merge Two Sorted Lists

## 💡 Intuition

- So the problem was about merging two sorted linked list.
- Well the problem is kind of simple we can just compare 

---
### 🧠 Insights And Structures

- [[linked list]]

---
## ⏱️ Complexity
- **Time Complexity:** $O(N + M)$
- **Space Complexity:** $O(1)$
---
## 🛡️ Attempt History
### Attempt 1: 2026-02-17
- **Outcome:** (e.g., TLE, Wrong Answer, Solved with Help)
- **What blocked me:** - **Improvement:** ---
---
## 💻 Implementation (C++)

```cpp
ListNode* mergeTwoLists(ListNode* list1, ListNode* list2) {
        ListNode* head = new ListNode(0) ;
        ListNode* curr = head;


        while(list1 != nullptr && list2 != nullptr)
        {
            if(list1->val <= list2->val)
            {
                head->next = list1;
                list1 = list1->next;
            }
            else {
                head->next = list2;
                list2 = list2->next;
            }

            head = head->next;
        }

        head->next = (list1 != nullptr) ? list1 : list2;

        return curr->next;

    }
```
