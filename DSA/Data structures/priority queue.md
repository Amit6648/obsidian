 So priority queue is of two types Maximum and minimum and it follows FIFO(first in first out).

- Maximum Priority Queue -
  This is default structure of priority queue. In maximum priority queue it will always maintain maximum number at the top. Underneath it uses Max heap tree to maintain it's order.
- Minimum priority Queue - 
  In minimum the top element will always be smallest. Underneath it maintains a min heap tree.

---
# Syntax

- Creation

  ```cpp
  priority_queue<type> queue_name; // This is for maximum queue
  ```

```cpp
priority_queue<type, vector<type>, greater<int>> queue_name; // minimum
```

---
# Rest of the functions are same as [[Stacks]]
