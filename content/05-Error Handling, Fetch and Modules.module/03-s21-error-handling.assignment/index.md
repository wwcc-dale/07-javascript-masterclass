---
indent: 2
name: "Assignment: Safe Math Functions"
published: true
points_possible: 100
grading_type: points
submission_types:
  - online_upload
allowed_extensions:
  - html
  - js
  - txt
due_at: null
outcomes:
  - 05-DEBUG
topics:
  - error-handling
  - try-catch-finally
  - custom-errors
---

[lead]You have learned how errors work and how to catch them — now it is time to write functions that throw useful errors and wrap them in try/catch blocks to handle the unexpected.

# Assignment: Safe Math Functions

In this assignment you will write two functions that throw custom errors when given bad input. You will then test each function with both valid and invalid inputs, wrapping all calls in try/catch blocks so your program handles problems gracefully.

- stats
- 100 | Points | success
- online_upload | Submission | accent

---

## Why This Matters

Real programs deal with bad input all the time. A user types letters when you expect numbers. A calculation tries to divide by zero. A value falls outside a valid range. Without error handling, one bad input can crash the whole program. With good error handling, your program catches the problem, explains it clearly, and keeps running.

---

## Skills You Need

Before you start, make sure you can answer these from Session 21:

- How do you use `try`, `catch`, and `finally`?
- What does `throw new Error("message")` do?
- What is a `TypeError`? A `RangeError`?
- What properties does the error object have?
- How do you check the type of an error with `instanceof`?

If you are unsure, re-read the Key Concepts section of the Session 21 page.

---

## What You Will Build

You will create a file called `safe-math.html`. Inside a `<script>` tag you will:

1. Write a `safeDivide(a, b)` function that throws a custom `Error` if `b` is zero
2. Write a `parseNumber(str)` function that throws a `TypeError` if the input is not a valid number string
3. Test `safeDivide` with at least two valid calls and one invalid call — all wrapped in try/catch
4. Test `parseNumber` with at least two valid calls and one invalid call — all wrapped in try/catch
5. Add a `finally` block to at least one of the try/catch blocks

---

## Step-by-Step Instructions

- steps: Step-by-Step Instructions
- Step 1 — Create a new file called `safe-math.html` using the HTML skeleton at the bottom of this page.
- Step 2 — Inside the `<script>` tag, write a function called `safeDivide(a, b)`. If `b` is exactly `0`, throw `new Error("Cannot divide by zero")`. Otherwise return `a / b`. Log the result when it works.
- Step 3 — Write a function called `parseNumber(str)`. Use `Number(str)` to convert the string. If the result is `NaN`, throw `new TypeError("Expected a number string, got: " + str)`. Otherwise return the converted number.
- Step 4 — Call `safeDivide(10, 2)` — this should work and log the result. Wrap it in a try/catch. In the catch block, log `"safeDivide error: " + error.message`.
- Step 5 — Call `safeDivide(10, 0)` in a second try/catch. Add a `finally` block that logs `"safeDivide attempt complete"`. Confirm the catch block runs and finally always runs.
- Step 6 — Call `parseNumber("42")` and `parseNumber("3.14")` in try/catch blocks — both should succeed and log the result.
- Step 7 — Call `parseNumber("hello")` in a try/catch. In the catch block, log both `error.name` and `error.message` to show the TypeError was thrown correctly.
- Step 8 — Add a comment above each function explaining what it does and what error it throws.
- Step 9 — Save the file and open it in a browser. Check the console to confirm all expected output appears and no unhandled errors occur.
- Step 10 — Upload `safe-math.html` to Canvas.

**HTML skeleton:**

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Safe Math Functions</title>
</head>
<body>
  <h1>Safe Math Functions</h1>
  <p>Open the browser console to see the output.</p>

  <script>
    // Your JavaScript goes here

  </script>
</body>
</html>
```

---

## Success Criteria

- checklist: Success Criteria
- The file is named `safe-math.html` and opens without errors
- `safeDivide(a, b)` throws `new Error("Cannot divide by zero")` when `b === 0`
- `safeDivide` returns the correct quotient for valid inputs
- `parseNumber(str)` throws a `TypeError` when the input is not a number string
- `parseNumber` returns the correct number for valid inputs
- At least three try/catch blocks are used (one for each failing call and one for a passing call)
- At least one try/catch includes a `finally` block
- The catch block for `parseNumber` logs both `error.name` and `error.message`
- Each function has a comment describing what it does
- Code is neatly indented and easy to read

---

- flow-accordion: Stretch Levels

###### Base — Required for everyone
Complete all steps as described. Write both functions, test each with valid and invalid inputs, use try/catch with finally, and log the error name and message for the TypeError.

###### Intermediate — More challenge
Write a third function called `clampedValue(value, min, max)`. If `value` is less than `min` or greater than `max`, throw a `RangeError` with a message like `"Value 150 is out of range [0, 100]"`. Test it with values inside and outside the range. In the catch block, use `error instanceof RangeError` to check the error type and log a specific message for that case.

###### Advanced — Push yourself
Write a function called `safeRun(fn, ...args)` that accepts any function and its arguments, wraps the call in try/catch, and returns an object `{ ok: true, value: result }` on success or `{ ok: false, error: error.message }` on failure. Test it with `safeDivide`, `parseNumber`, and `clampedValue`. Log each result object so the structure is clear. This pattern — returning a result object instead of throwing — is used in many real-world libraries.

---

{{include:session-footer}}

{{include:completion-checklist}}
