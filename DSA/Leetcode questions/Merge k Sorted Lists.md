
---
Status: solved with help
Difficulty: hard
Pattern: 
Last_attempt: 2026-04-27
Next_review: 2026-04-27
Attempts: 1
link: [Merge k Sorted Lists](https://leetcode.com/problems/merge-k-sorted-lists/)

---

# Problem: Merge k Sorted Lists

## 💡 Intuition

-  So the problem is about merging k number of sorted linked lists and the output should also be sorted.
- So this problem is kind of similar to [[Merge Two Sorted Lists]] but we just can have any number of linked list rather than two.
- So the thing is that unlike [[Merge Two Sorted Lists]] we can't store linked lists nodes and just compare them one by one cause here we don't know how many of them we have.
- So to solve this problem we can use a [[priority queue]] or specifically a "min queue".
- Well we can store the pointers of each linked list and when we are done pushing all of them we can pop a pointer and then add it to the new linked list.
- then we can move that pointer and add it again in the queue.

---
### 🧠 Insights And Structures

- [[Linked List]]
- [[priority queue]]

---
## ⏱️ Complexity
- **Time Complexity:** $O(n * k)$
- **Space Complexity:** $O(k)$
---
## 🛡️ Attempt History
### Attempt 1: 2026-04-27
- **Outcome:** (e.g., TLE, Wrong Answer, Solved with Help)
- **What blocked me:** - **Improvement:** ---
---
## 💻 Implementation (C++)

```cpp
class Solution {
    struct compareNode {
        bool operator()(ListNode* const& p1, ListNode* const& p2) {
            return p1->val > p2->val;
        }
    };

public:
    ListNode* mergeKLists(vector<ListNode*>& lists) {
        priority_queue<ListNode*, vector<ListNode*>, compareNode> maxlink;

        for (ListNode* node : lists) {
            if (node)
                maxlink.push(node);
        }

        if (maxlink.empty())
            return nullptr;

        ListNode* head = new ListNode(0);

        ListNode* curr = head;

        while (maxlink.size() > 1) {
            ListNode* top = maxlink.top();

            maxlink.pop();

            curr->next = top;

            curr = curr->next;

            if (top->next) {
                maxlink.push(top->next);
            }
        }

        curr->next = maxlink.top();

        return head->next;
    }
};
```

