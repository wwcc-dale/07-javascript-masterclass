---
indent: 2
name: "Solution: Session 2 — Types and Operators"
published: false
outcomes:
  - 03-ELEM
topics:
  - types
  - operators
  - expressions
---

# Instructor Solution: Session 2 — Types and Operators

> alert: warning
>
> This page is for instructor reference only. Keep unpublished until after the assignment deadline. You may share the hint section verbally or reveal this page to individual students as needed.

---

## Student Hint

> alert: tip
>
> Make sure each calculation uses a different operator — aim to include all five: `+`, `-`, `*`, `/`, and `%`. The modulus operator `%` gives you the remainder after division, so `24 % 7` gives `3`. Use template literals (backtick strings with `${}`) to build labels that show both the expression and its result in one `console.log()` call.

---

## Full Solution

This solution declares two operands and uses all five arithmetic operators, logging each result with a template literal that shows the full expression.

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Session 2 — Types and Operators</title>
</head>
<body>
  <script>
    const a = 24;
    const b = 7;

    // Addition
    const sum = a + b;
    console.log(`${a} + ${b} = ${sum}`);         // 24 + 7 = 31

    // Subtraction
    const difference = a - b;
    console.log(`${a} - ${b} = ${difference}`);  // 24 - 7 = 17

    // Multiplication
    const product = a * b;
    console.log(`${a} * ${b} = ${product}`);     // 24 * 7 = 168

    // Division
    const quotient = a / b;
    console.log(`${a} / ${b} = ${quotient}`);    // 24 / 7 ≈ 3.4285...

    // Modulus — the remainder after dividing
    const remainder = a % b;
    console.log(`${a} % ${b} = ${remainder}`);   // 24 % 7 = 3

    // Bonus: check types with typeof
    console.log("Type of sum:", typeof sum);          // "number"
    console.log("Type of 'hello':", typeof "hello");  // "string"
  </script>
</body>
</html>
```

---

## Instructor Notes

- Full credit if 5 different operators are used and every result is logged with a label that identifies what it is.
- Common mistake: using only `+` five times with different numbers — check that different operators are actually present.
- Common mistake: `console.log("Result: " + a + b)` produces `"Result: 247"` (string concatenation) rather than `31` — this is a great teaching moment about how `+` behaves when the left operand is a string. Encourage template literals to avoid this.
- Template literals are preferred but string concatenation is acceptable at this stage.
- Common mistake: dividing two integers and being surprised by a decimal result — this is a good opportunity to mention `Math.floor()` as a preview.
- Intermediate: students who used `**` (exponentiation) or chained multiple operators in a single expression show depth and curiosity.
- Advanced: students who used `typeof` to inspect the types of their results demonstrate they are connecting the session's concept to code.
