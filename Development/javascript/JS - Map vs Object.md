# JavaScript Map vs Object for Caching

When building a cache for [[JS - Memoization|Memoization]], we must decide between a plain JavaScript object `{}` and a built-in `Map`.

## Plain Object `{}`
* **Limitations**:
  * Keys can only be Strings or Symbols.
  * If you try to use an object or array as a key, it gets serialized to `"[object Object]"`, causing collisions.
  * Inherits prototype properties (like `toString`), which can pollute the cache.

## `Map`
* **Advantages**:
  * Keys can be **any value**, including objects, functions, arrays, and primitives.
  * Provides helpful built-in methods: `.has(key)`, `.get(key)`, `.set(key, value)`, and `.clear()`.
  * Preserves insertion order and is optimized for frequent additions/removals.

## Cache Key Serialization
In memoization, we often serialize arguments into a string key (e.g., using `JSON.stringify(args)`) to query the cache, but using a `Map` is still preferred for its clean API and avoidance of prototype pollution.

---
Related: [[JS - Memoization]]
