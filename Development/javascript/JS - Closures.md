# JavaScript Closures

A **closure** is a function that "remembers" its lexical environment (variables in its outer scope) even after the outer function has finished executing.

## Analogy
Imagine a chef (outer function) who writes down a secret recipe in a notebook (local variable) and leaves the kitchen. The chef's assistant (inner function) still has access to that notebook and can read the recipe anytime they make a dish, even though the chef is gone.

## Code Example
```javascript
function createCounter() {
  let count = 0; // The inner function "captures" this variable
  return function() {
    count++;
    return count;
  };
}
const myCounter = createCounter();
console.log(myCounter()); // 1
console.log(myCounter()); // 2
```

## Real-World Applications
Closures are essential for:
* Creating private variables (like `count` above).
* Factory functions.
* **[[JS - Memoization|Memoization]]**: Retaining a private cache object across multiple function executions.

---
Related: [[JS - Core Concepts]] | [[JS - Memoization]]
