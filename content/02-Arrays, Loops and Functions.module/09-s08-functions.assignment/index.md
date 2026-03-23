---
indent: 2
name: "Assignment: Functions"
published: false
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
  - 03-ELEM
topics:
  - functions
  - arrow-functions
  - scope
---

[lead]Writing your own functions is one of the most important skills in programming — and today you will write three of them: a greeting function, a calculator, and a temperature converter.

# Functions Assignment

In this assignment you will write three functions and test them with different inputs. You will practice using parameters, return values, and all three function styles.

- stats
- 100 | Points | success
- online_upload | Submission | accent

## Why This Matters

Functions are how programmers avoid repeating themselves. Instead of writing the same code in five different places, you write it once as a function and call it whenever you need it. This makes code easier to fix, easier to read, and easier to build on. Every real JavaScript application is made up of dozens or hundreds of functions.

## Skills You Need

Before you start, make sure you understand:

- How to write a function declaration: `function name(param) { return value; }`
- How to write a function expression: `const name = function(param) { };`
- How to write an arrow function: `const name = (param) => expression;`
- What `return` does — it sends a value back to the caller
- What parameters are and how arguments fill them
- How to call a function: `name(argument)`

If any of these feel unclear, re-read the Session 8 Key Concepts section before you start.

## What You Will Build

Create a file called `functions.js` (or `functions.html` with a `<script>` block). It must contain three functions and test calls for each:

**Function 1 — Greeting:** A function called `greet` that takes a `name` parameter and returns a greeting string. For example, `greet("Sam")` should return `"Hello, Sam!"`. Give it a default parameter so that `greet()` with no argument returns `"Hello, friend!"`.

**Function 2 — Calculator:** A function called `calculate` that takes three parameters: `num1`, `num2`, and `operation`. Based on the operation string (`"add"`, `"subtract"`, `"multiply"`, `"divide"`), it should perform the correct math and return the result. Use `if` / `else if` statements (from Credit 1) to check the operation.

**Function 3 — Temperature Converter:** A function called `celsiusToFahrenheit` that takes a temperature in Celsius and returns the temperature in Fahrenheit. The formula is `(celsius * 9/5) + 32`.

## Step-by-Step Instructions

- steps: Step-by-Step Instructions
- Step 1 — Create your file. Name it `functions.js` or `functions.html`. Add a comment at the top with your name.
- Step 2 — Write the `greet` function. Use a function declaration: `function greet(name = "friend") { return "Hello, " + name + "!"; }`. Below it, call `console.log(greet("Sam"))` and `console.log(greet())` to test both paths.
- Step 3 — Write the `calculate` function. Use a function expression (assign to a `const`). Inside use `if (operation === "add") return num1 + num2;` and similar `else if` branches for subtract, multiply, and divide. For divide, add a check: if `num2 === 0`, return `"Cannot divide by zero"`. Test it: call `calculate(10, 5, "add")`, `calculate(10, 5, "multiply")`, and `calculate(10, 0, "divide")` and log each result.
- Step 4 — Write the `celsiusToFahrenheit` function. Use an arrow function: `const celsiusToFahrenheit = (celsius) => (celsius * 9/5) + 32;`. Test it with `console.log(celsiusToFahrenheit(0))` (should be 32), `console.log(celsiusToFahrenheit(100))` (should be 212), and one temperature of your choice.
- Step 5 — Add a comment above each function explaining what it does in one sentence. Good comments make code much easier to read.
- Step 6 — Test everything. Open your file in a browser (F12 for console) and confirm all three functions produce correct output with no errors.

## Success Criteria

- checklist: Success Criteria
- `greet` function is defined and returns the correct greeting string
- `greet()` called with no argument returns the default greeting using "friend"
- `calculate` function handles all four operations: add, subtract, multiply, divide
- `calculate` handles division by zero without crashing
- `celsiusToFahrenheit` function returns the correct number
- All three functions are tested with `console.log` calls showing results
- Three different function styles are used (declaration, expression, arrow)
- A comment describes what each function does
- Code runs without errors

- flow-accordion: Stretch Levels

###### Base — Required for everyone
Write all three functions as described and test each one. All students must reach this level.

###### Intermediate — If you finish Base with time remaining
Add a fourth function called `isEven` using an arrow function that takes a number and returns `true` if it is even and `false` if it is odd. Then write a fifth function called `countEvens` that takes an array of numbers and returns how many of them are even — it must call `isEven` inside it using a `for...of` loop. Test with an array of at least 6 numbers.

###### Advanced — Challenge yourself
Write a recursive function called `factorial` that takes a positive integer `n` and returns `n!` (n factorial — for example, `factorial(5)` returns 120 because 5 × 4 × 3 × 2 × 1 = 120). The base case is `factorial(0)` or `factorial(1)`, which both return 1. Test it with 0, 1, 5, and 10. Also add a function called `power(base, exp)` that uses recursion to calculate `base` raised to the power `exp` without using `Math.pow`. Test with `power(2, 8)` (should be 256).

---

{{include:session-footer}}

{{include:completion-checklist}}
