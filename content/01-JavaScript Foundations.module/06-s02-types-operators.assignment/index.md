---
indent: 2
name: "Assignment: Math and Types Explorer"
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
  - types
  - operators
  - expressions
---

[lead]Now that you understand types and operators, it is time to put them to work — write five calculations, check some types, and see exactly what JavaScript does with numbers and comparisons.

# Assignment: Math and Types Explorer

In this assignment you will write a JavaScript program that performs five math calculations, checks the types of some values, and uses comparison operators to produce true/false results. You will log everything to the console with clear labels.

- stats
- 100 | Points | success
- online_upload | Submission | accent

---

## Why This Matters

Real programs do math all the time — calculating totals, checking if a number is in range, converting units. Understanding how JavaScript handles numbers and types helps you write code that does what you actually intend.

---

## Skills You Need

Before you start, make sure you can answer these from Session 2:

- What does `typeof` return for a number? For a string?
- What is the difference between `==` and `===`?
- What does the `%` operator do?
- What is operator precedence, and how do parentheses change it?

If you are unsure, review the Session 2 Key Concepts section.

---

## What You Will Build

Create a file called `math-explorer.html`. Inside the `<script>` tag, write JavaScript that:

1. Performs five different arithmetic calculations and logs each result with a label
2. Uses `typeof` to check the type of at least three different values and logs each result
3. Uses at least three comparison operators (`===`, `<`, `>=`, etc.) and logs whether each comparison is `true` or `false`
4. Uses at least one expression with mixed operators to demonstrate operator precedence

---

## Step-by-Step Instructions

- steps: Step-by-Step Instructions
- Step 1 — Create a new file called `math-explorer.html`. Copy the HTML skeleton from Session 1 (change the title to "Math and Types Explorer").
- Step 2 — In the `<script>` section, write your five math calculations. Each should use a different operator. Store each result in a variable, then log it with a label. Example: `let sum = 45 + 17; console.log("Sum: " + sum);`
- Step 3 — Add three `typeof` checks. Pick three different types of values (a number, a string, and a boolean), use `typeof` on each, and log the results. Example: `console.log("Type of 42: " + typeof 42);`
- Step 4 — Write three comparisons using different comparison operators. Store each result in a variable and log it. Make at least one comparison use `===` instead of `==`. Example: `let isOldEnough = age >= 18; console.log("Old enough? " + isOldEnough);`
- Step 5 — Write one expression that uses at least two different operators without parentheses, then write the same expression with parentheses in a different order. Log both results to show how precedence changes the output. Example: `console.log(2 + 3 * 4);` vs `console.log((2 + 3) * 4);`
- Step 6 — Save the file and open it in a browser. Check the Console tab (F12) to see all your output.
- Step 7 — Review your output. Make sure every console.log has a readable label. Fix any errors you find.
- Step 8 — Submit your `math-explorer.html` file to Canvas.

---

## Success Criteria

- checklist: Success Criteria
- File is named `math-explorer.html` and opens without errors
- Five arithmetic calculations are performed and logged with labels
- All six arithmetic operators are represented across your five calculations (you may repeat one)
- At least three `typeof` checks are performed and results are logged
- At least three comparison expressions are written and logged
- At least one comparison uses `===`
- One operator precedence demonstration with and without parentheses is included
- All console output has clear text labels
- Code is neatly indented and easy to read

---

- flow-accordion: Stretch Levels

###### Base — Required for everyone
Complete all five calculations, three typeof checks, three comparisons, and one precedence demonstration as described above.

###### Intermediate — More challenge
Add a section that compares a string number to a real number using both `==` and `===`. Log both results and add a comment explaining why the results are different. Example: compare `"10"` and `10` with both operators.

###### Advanced — Push yourself
Create a "calculator summary" at the end of your script. Declare variables for `startingValue`, `afterAdd`, `afterMultiply`, and `finalResult`. Each variable should use the previous one in its calculation. Build a chain of operations and log a summary message at the end using string concatenation (e.g. `"Start: " + startingValue + " → After add: " + afterAdd`) that explains all four steps. Also log the type of each variable to confirm they are all numbers.

---

{{include:session-footer}}

{{include:completion-checklist}}
