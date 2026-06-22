# JavaScript Floating-Point Math

JavaScript stores numbers in double-precision float format (IEEE 754). This leads to rounding errors in decimal math.

## The Problem
```javascript
console.log(0.1 + 0.2); // 0.30000000000000004
```
This is a critical issue when dealing with financial ledgers, currency calculations, or precise reports.

## Solutions
1. **Rounding for Display**: Use `.toFixed(2)` to convert the final number to a string rounded to two decimal places.
2. **Integer Math**: Perform all calculations in cents (integers) rather than dollars, and convert back to dollars at the end:
   `Math.round((0.1 * 100) + (0.2 * 100)) / 100 === 0.3`
3. **Precision Rounding**: Use `Math.round()` or custom rounding utilities for totals before displaying them to users.

---
Related: [[JS - Array Methods]]
