---
indent: 2
name: "Assignment: Grade Calculator"
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
  - conditionals
  - if-else
  - logical-operators
---

[lead]Conditional logic is what makes programs smart — and your grade calculator will use if/else chains to turn a number into a decision, just like a real grading system does.

# Assignment: Grade Calculator

In this assignment you will write a JavaScript program that takes a score (a number from 0 to 100) and uses conditional logic to determine and display the corresponding letter grade.

- stats
- 100 | Points | success
- online_upload | Submission | accent

---

## Why This Matters

If/else chains are at the heart of almost every real-world program. Pricing rules, eligibility checks, game logic, form validation — they all work by evaluating conditions and choosing a path. Building a grade calculator gives you a concrete, working example you can understand completely.

---

## Skills You Need

Before you start, make sure you can use:

- `if`, `else if`, and `else` — how to chain multiple conditions
- Comparison operators: `>=`, `<`, `===`
- Logical operators: `&&`, `||` (for stretch levels)
- `console.log()` with template literals

Review the Session 4 Key Concepts if anything is unclear.

---

## What You Will Build

Create a file called `grade-calculator.html`. In the `<script>` section, you will:

1. Declare a variable `score` and assign it a number from 0 to 100
2. Use if/else if/else to determine the letter grade based on these rules:
   - A: score is 90 or above
   - B: score is 80 or above (but less than 90)
   - C: score is 70 or above (but less than 80)
   - D: score is 60 or above (but less than 70)
   - F: score is below 60
3. Store the letter grade in a variable called `grade`
4. Log a message using a template literal, like: `"Score: 85 — Grade: B"`

Test your program with at least three different score values to make sure all branches work correctly. You only need to submit one version, but comment out the other test values so your instructor can see you tested multiple scores.

---

## Step-by-Step Instructions

- steps: Step-by-Step Instructions
- Step 1 — Create a new file called `grade-calculator.html`. Copy the HTML skeleton from Session 1 (update the title to "Grade Calculator").
- Step 2 — In the `<script>` section, declare `let score = 85;` (or any number you want to test with first).
- Step 3 — Declare `let grade;` below the score (no value yet — you will assign it in the if/else chain).
- Step 4 — Write the if/else if/else chain. For each condition, assign the correct letter to `grade`. Check from highest to lowest: start with `if (score >= 90)`.
- Step 5 — After the if/else chain, log the result: `console.log(\`Score: ${score} — Grade: ${grade}\`);`
- Step 6 — Save and open in a browser. Check the Console tab.
- Step 7 — Change the score to a different value (for example, 72) and reload. Confirm the grade changes correctly. Test at least three scores: one in each of the A, C, and F ranges.
- Step 8 — Add comments above your extra test values so your instructor can see you tested multiple scenarios. You can comment out the other test values with `//` so only one runs at a time.
- Step 9 — Upload your final `grade-calculator.html` to Canvas.

---

## Success Criteria

- checklist: Success Criteria
- File is named `grade-calculator.html` and opens without errors
- `score` is declared with a numeric value
- `grade` is declared and assigned inside the if/else chain
- All five letter grades (A, B, C, D, F) are handled with correct score boundaries
- A template literal logs the score and grade in one message
- Comments show evidence of testing with at least three different score values
- The if/else chain checks from highest to lowest (A first, F last)
- Code is neatly indented and easy to read

---

- flow-accordion: Stretch Levels

###### Base — Required for everyone
Implement the five-grade if/else chain and log the result. Test with at least three different scores.

###### Intermediate — More challenge
Add a second variable `passFail` that is `"Pass"` if the grade is A, B, or C and `"Fail"` otherwise. Use the `||` operator to combine conditions. Log a second message like: `"Result: Pass"`. Then add a ternary operator that assigns a short feedback message — `"Great job!"` for A or B, `"Keep working"` for anything else — and log it too.

###### Advanced — Push yourself
Add input validation using a nested conditional. Before running the grade logic, check if `score` is a number between 0 and 100. If it is less than 0 or greater than 100, log `"Invalid score — please enter a number between 0 and 100."` and do not run the grade logic. Then add a `switch` statement that, based on the letter grade, logs a specific tip message (for example: grade A gets "Outstanding work!", grade B gets "Good job — push for that A next time!", etc.).

---

{{include:session-footer}}

{{include:completion-checklist}}
