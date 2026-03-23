---
indent: 2
name: "Solution: Session 4 — Conditionals"
published: false
outcomes:
  - 03-ELEM
topics:
  - conditionals
  - if-else
  - logical-operators
---

# Instructor Solution: Session 4 — Conditionals

> alert: warning
>
> This page is for instructor reference only. Keep unpublished until after the assignment deadline. You may share the hint section verbally or reveal this page to individual students as needed.

---

## Student Hint

> alert: tip
>
> Order your `if/else if` chain from highest to lowest — check for A first, then B, then C, then D, and use a final `else` for F. You do not need to check both ends of a range (like `score >= 80 && score < 90`) because once JavaScript finds a true condition it stops checking the rest of the chain. A final bare `else` with no condition handles everything that did not match above.

---

## Full Solution

This solution uses a top-down `if/else if/else` chain to assign a letter grade, then demonstrates the same logic as a ternary (for pass/fail) and as a `switch` statement.

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Session 4 — Grade Calculator</title>
</head>
<body>
  <script>
    const score = 78; // change this value to test different grades

    let grade;

    if (score >= 90) {
      grade = "A";
    } else if (score >= 80) {
      grade = "B";
    } else if (score >= 70) {
      grade = "C";
    } else if (score >= 60) {
      grade = "D";
    } else {
      grade = "F";
    }

    console.log(`Score: ${score} → Grade: ${grade}`);

    // Bonus: ternary for a simple pass/fail check
    const result = score >= 60 ? "Passing" : "Failing";
    console.log(`Status: ${result}`);

    // Bonus: switch version — shows an alternative way to write the same logic
    let switchGrade;
    switch (true) {
      case score >= 90: switchGrade = "A"; break;
      case score >= 80: switchGrade = "B"; break;
      case score >= 70: switchGrade = "C"; break;
      case score >= 60: switchGrade = "D"; break;
      default: switchGrade = "F";
    }
    console.log(`Switch version → Grade: ${switchGrade}`);
  </script>
</body>
</html>
```

---

## Instructor Notes

- Core requirement: a correct `if/else if/else` chain that produces the right letter grade for all five possible outcomes (A, B, C, D, F).
- Common mistake: using `&&` range checks like `score >= 80 && score < 90` — this works, but it is unnecessarily verbose and shows the student has not yet internalized the early-exit behavior of `else if`. Point this out and explain that the chain stops as soon as a condition is true.
- Common mistake: using `=` (assignment) instead of `===` or `>=` inside a condition — produces unexpected results because assignment in a condition evaluates to the assigned value, which may be truthy.
- Common mistake: no `else` at the end — scores below 60 will leave `grade` as `undefined`, which then appears literally as "undefined" in the log. Ask the student what happens when `score = 45`.
- Common mistake: conditions ordered from lowest to highest — a score of 95 matches `score >= 60` first and gets a D. This is a great debugging exercise.
- Intermediate: students who added a ternary expression for pass/fail status show they understood the ternary concept from the session.
- Advanced: students who used a `switch` statement or tested several different score values (edge cases like 90, 80, 60, 59, 0) demonstrate deeper understanding of conditional logic and testing habits.
