# JavaScript Rest, Spread, and `.apply()`

To build generic wrapper functions (like the one in [[JS - Memoization]]), we must handle arguments dynamically without knowing how many parameters the target function accepts.

## 1. Rest Parameter (`...args`)
* **What it does**: Bundles multiple separate arguments passed to a function into a single array.
* **Usage in wrapper**:
  ```javascript
  function wrapper(...args) {
    // args is an array containing all passed arguments
  }
  ```

## 2. Spread Operator (`...args`)
* **What it does**: Unpacks an array of items into separate, individual arguments.
* **Usage**:
  ```javascript
  const numbers = [1, 2, 3];
  sum(...numbers); // equivalent to sum(1, 2, 3)
  ```

## 3. Function Context and `.apply()`
* **`.apply(thisContext, argsArray)`**: A built-in function method that executes a function, sets its internal `this` context, and passes arguments from an array.
* **Why it is critical**: It allows us to pass a list of dynamic arguments received from a rest parameter straight into the target function without losing the context of the caller.
  ```javascript
  const result = fn.apply(this, args);
  ```

---
Related: [[JS - Memoization]] | [[JS - Closures]]
