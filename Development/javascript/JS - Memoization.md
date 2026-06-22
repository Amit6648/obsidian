# JavaScript Memoization

**Memoization** is an optimization technique (caching) that speeds up slow, expensive functions by storing the results of function calls based on their inputs.

## How it Works
1. When a memoized function is called with inputs:
   * It checks its memory cache for those inputs.
   * If the inputs are found, it returns the cached result immediately.
   * If not, it runs the slow computation, saves the result to the cache, and returns it.
2. To build a memoized function, we use:
   * **[[JS - Closures|Closures]]** to keep the cache private and persistent.
   * A key-value store (see **[[JS - Map vs Object|Map vs Object]]**).
   * Rest and Spread operators to handle variable arguments (see **[[JS - Rest and Spread|Rest & Spread Operators]]**).

## Structure of a Memoized Function
```javascript
function memoize(fn) {
  const cache = new Map(); // Private cache stored in the closure
  return function(...args) {
    const key = JSON.stringify(args); // Simple serialization for cache key
    if (cache.has(key)) {
      return cache.get(key); // Fast path
    }
    const result = fn.apply(this, args); // Execute original function
    cache.set(key, result); // Save to cache
    return result;
  };
}
```

---
Related: [[JS - Closures]] | [[JS - Map vs Object]] | [[JS - Rest and Spread]]
