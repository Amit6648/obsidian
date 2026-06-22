# JavaScript Array Methods (Ledger Processing)

In processing data (such as financial records), we chain core array tools to filter, transform, and aggregate data cleanly.

## The Core Array Tools
Think of an array as a conveyor belt carrying boxes of data:

1. **`filter()` (The Security Guard)**
   * **Role**: Evaluates each item against a condition and returns a new array containing only matching items.
   * **Analogy**: *"Only let boxes through if they are marked 'completed' and arrived in 2026."*
2. **`map()` (The Factory Worker)**
   * **Role**: Transforms every item in the array, putting the modified versions into a new array.
   * **Analogy**: *"Take each box, convert its Euro price to Dollars, and stamp the new price on the box."*
3. **`reduce()` (The Accountant)**
   * **Role**: Combines all items in the array into a single result (e.g., total sum, counts, or a grouped object).
   * **Analogy**: *"Go through all the boxes, sum up the prices, and write down the total spend for each category."*

## Method Chaining
We link these methods so the output of one flows directly into the input of the next:
`Array` ➔ `filter()` ➔ `Filtered Array` ➔ `map()` ➔ `Transformed Array` ➔ `reduce()` ➔ `Final Result`

Chaining keeps code readable and eliminates temporary variables.

## Gotchas & Best Practices
* **Floating-Point Math**: Due to binary decimal storage in JS, math isn't always exact (e.g., `0.1 + 0.2 === 0.30000000000000004`).
  * *Connection*: See [[JS - Floating-Point Math]] for solutions.
* **Deferred Calculations (Performance)**: When calculating averages, do **not** perform division on every iteration. Sum totals and counts first, then divide once at the end.

---
Related: [[JS - Core Concepts]] | [[JS - Floating-Point Math]]
