
---
Status: solved with help
Difficulty: medium
Pattern: Linked list
Last_attempt: 2026-04-09
Next_review: 2026-04-09
Attempts: 1
link: [LRU Cache](https://leetcode.com/problems/lru-cache/)

---

# Problem: LRU Cache

## 💡 Intuition

 - So the problem is about creating a data structure that is resembles "Least recently used".
 - So we have to create this using linked lists, so the rules are we have to create two functions one that will add metadata that will have "value and key". When we add this metadata it should be at top when we add the next one that will be at the top.
 - Now the get function that will be used to visit a element's value by using it's key and when a element is visited it will come at the top position meaning now it is the least recently used element.
 - So we can use a double linked list here to link and remove elements cause whenever we need to remove a element from middle when it is used and add it to end we need to link the elements around but in a single linked list we can access next element but not the previous and it will be stuck at pointing to the element we want to remove.
 - and whenever we need to get a element by it's key we can use [[Unordered Hash maps]] to store the keys and which node does these keys points to, by doing this  can get to the nodes in O(1) time.
 - We also have to maintain a capacity and when there is a overflow we need to remove the last element in the list.

---
### 🧠 Insights And Structures

---
## ⏱️ Complexity
- **Time Complexity:** $O(n)$
- **Space Complexity:** $O(n)$
---
## 🛡️ Attempt History
### Attempt 1: 2026-04-09
- **Outcome:** (e.g., TLE, Wrong Answer, Solved with Help)
- **What blocked me:** - **Improvement:** ---
---
## 💻 Implementation (C++)

```cpp
class LRUCache {
    private : 

    class Node {
        public :
        int key,val;

        Node *prev, *next;
        Node(int key,int val) 
        {
            this->key = key;
            this->val = val;

            prev = nullptr;
            next = nullptr;
        }
    };
    
    int cap;

    unordered_map<int, Node*> map;

    Node * head;
    Node * tail;

    void add (Node * newnode )
    {
        Node * temp = head->next;
        head->next = newnode;
        newnode->prev = head;
        newnode->next = temp;
        temp->prev = newnode;
    }

    void remove(Node * rneed)
    {
        Node * prev = rneed->prev;
        Node * next =  rneed->next;
        prev->next = next;
        next->prev = prev;
    }


public:
    LRUCache(int capacity) {
          cap = capacity;
          head = new Node(-1,-1);
          tail = new Node(-1,-1);
          head->next = tail;
          tail->prev =  head;
    }
    
    int get(int key) {
        if(map.count(key))
        {
            Node * temp = map[key];
            remove(temp);
            add(temp);

            return temp->val;
        }

        else {
            return -1;
        }

        
    }
    
    void put(int key, int value) {
        if(map.count(key))
        {
            Node * temp = map[key];
            remove(temp);
            add(temp);

            temp->val = value;
        }

      else {
         Node * newnode = new Node(key,value);
        map[key] = newnode;

        add(newnode);
      }

        if(map.size()>cap)
        {
            map.erase(tail->prev->key);
            remove(tail->prev);
        }
    }
};
```
