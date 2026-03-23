---
indent: 2
name: "Solution: Session 21 — Error Handling"
published: false
outcomes:
  - 05-DEBUG
topics:
  - error-handling
  - try-catch-finally
  - custom-errors
---

# Instructor Solution: Session 21 — Error Handling

> alert: warning
>
> This page is for instructor reference only. Keep unpublished until after the assignment deadline.

---

## Student Hint

> alert: tip
>
> Inside `safeDivide`, check if `b === 0` and use `throw new Error("message")` to throw a custom error. Inside `parseNumber`, use `isNaN(Number(str))` to check if the string is not a valid number — if it is not, throw a `new TypeError("message")`. In your try/catch blocks, log `error.message` (not just `error`) so you see the actual message.

---

## Full Solution

A single `safe-math.html` file with both functions, multiple try/catch blocks, and a nested try/catch demonstration.

```javascript
// safeDivide — throws if divisor is zero
function safeDivide(a, b) {
  if (typeof a !== "number" || typeof b !== "number") {
    throw new TypeError(`Expected numbers, got ${typeof a} and ${typeof b}`);
  }
  if (b === 0) {
    throw new Error("Division by zero is not allowed.");
  }
  return a / b;
}

// Test safeDivide
console.log("=== safeDivide ===");
try {
  console.log("10 / 2 =", safeDivide(10, 2));    // 5
  console.log("9 / 3 =", safeDivide(9, 3));       // 3
} catch (error) {
  console.log("Unexpected error:", error.message);
}

try {
  console.log("5 / 0 =", safeDivide(5, 0));       // should throw
} catch (error) {
  console.log(`Caught: ${error.name}: ${error.message}`);  // Error: Division by zero
}

try {
  safeDivide("ten", 2);                            // TypeError — wrong types
} catch (error) {
  console.log(`Caught: ${error.name}: ${error.message}`);
}

// parseNumber — throws TypeError if input is not a valid number string
function parseNumber(str) {
  if (typeof str !== "string") {
    throw new TypeError(`Expected a string, got ${typeof str}`);
  }
  const trimmed = str.trim();
  if (trimmed === "" || isNaN(Number(trimmed))) {
    throw new TypeError(`"${str}" cannot be converted to a number`);
  }
  return Number(trimmed);
}

console.log("\n=== parseNumber ===");
// Valid inputs
try {
  console.log(`parseNumber("42") =`, parseNumber("42"));      // 42
  console.log(`parseNumber(" 3.14 ") =`, parseNumber(" 3.14 ")); // 3.14
} catch (error) {
  console.log("Unexpected error:", error.message);
}

// Invalid inputs
const invalidInputs = ["abc", "", "  ", "12abc", null];
for (const input of invalidInputs) {
  try {
    const result = parseNumber(input);
    console.log(`parseNumber(${JSON.stringify(input)}) =`, result);
  } catch (error) {
    console.log(`Caught ${error.name}: ${error.message}`);
  }
}

// Nested try/catch — use safeDivide inside a larger operation
console.log("\n=== Nested try/catch ===");
function computeRatio(aStr, bStr) {
  try {
    const a = parseNumber(aStr);  // may throw TypeError
    const b = parseNumber(bStr);  // may throw TypeError
    try {
      const ratio = safeDivide(a, b);  // may throw Error
      return `${a} / ${b} = ${ratio.toFixed(4)}`;
    } catch (divError) {
      return `Division failed: ${divError.message}`;
    }
  } catch (parseError) {
    return `Parse failed: ${parseError.message}`;
  }
}

console.log(computeRatio("10", "3"));   // valid
console.log(computeRatio("10", "0"));   // division by zero
console.log(computeRatio("abc", "3"));  // parse error
```

---

## Instructor Notes

- **Core:** both functions exist and throw appropriate errors; at least one try/catch wrapping each function; valid AND invalid inputs tested
- **Common mistake:** `throw "message"` instead of `throw new Error("message")` — a string thrown is not an Error object and has no `.message` or `.name` property
- **Common mistake:** checking `b == 0` instead of `b === 0` — fine here but reinforce strict equality
- **Common mistake:** `isNaN("abc")` is true but `isNaN(" ")` is false — the whitespace case is tricky; `.trim()` first handles it correctly
- **Common mistake:** not using `error.name` and `error.message` to show the type — just logging `error` is less clear
- **Intermediate:** `typeof` guards for argument types, nested try/catch
- **Advanced:** custom Error class extending `Error`: `class DivisionError extends Error { constructor(msg) { super(msg); this.name = "DivisionError"; } }`
