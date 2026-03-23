---
name: "Solution: Session 1 — Literals and Variables"
published: false
outcomes:
  - 03-ELEM
topics:
  - literals
  - identifiers
  - variables
---

# Instructor Solution: Session 1 — Literals and Variables

> alert: warning
>
> This page is for instructor reference only. Keep unpublished until after the assignment deadline. You may share the hint section verbally or reveal this page to individual students as needed.

---

## Student Hint

> alert: tip
>
> Remember that `const` is for values that won't change during the program — think about which of your five values could realistically change later and which could not. Each `console.log()` should include a descriptive label so the output is easy to read: `console.log("Name:", name)` is much clearer than `console.log(name)` on its own.

---

## Full Solution

This solution declares five variables using `const` and `let` as appropriate, then logs each one to the console with a descriptive label.

```javascript
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Session 1 — Variables</title>
</head>
<body>
  <script>
    // These values describe a person and won't change during the program,
    // so const is the right choice for all of them.
    const name = "Morgan";
    const city = "Walla Walla";
    const hobby = "hiking";
    const favoriteNumber = 7;

    // Age could change over time, but for this program it stays fixed.
    // Either const or let is acceptable here — const is preferred.
    const age = 22;

    // Log each variable with a descriptive label
    console.log("Name:", name);
    console.log("Age:", age);
    console.log("City:", city);
    console.log("Hobby:", hobby);
    console.log("Favorite number:", favoriteNumber);
  </script>
</body>
</html>
```

---

## Instructor Notes

- Full credit if all 5 variables are declared, appropriately typed (string/number), and logged with labels.
- `var` instead of `const`/`let`: acceptable for this first assignment but flag it — ask students to use `const` or `let` in all future work.
- Common mistake: forgetting quotes around string values produces a ReferenceError; point students to the exact line in the console error.
- Common mistake: `console.Log()` with a capital L produces a TypeError — case matters in JavaScript.
- Common mistake: mixing up which values need quotes (strings) versus which do not (numbers) — a missing quote on a string will throw a ReferenceError rather than a syntax error, which can confuse beginners.
- Intermediate and advanced stretch: students who added descriptive labels to `console.log()`, used template literals, or declared extra variables like `fullGreeting` and `nextBirthday` are ahead of the curve — acknowledge it.
