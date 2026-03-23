---
indent: 2
name: "Assignment: Loops"
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
  - 03-ELEM
topics:
  - loops
  - iteration
---

[lead]You have learned about every major loop in JavaScript — now you will put them to work printing numbers, stepping through arrays, and counting down from ten.

# Loops Assignment

In this assignment you will write three separate loops, each one doing something a little different. By the time you finish, you will have used a `for` loop, a `for...of` loop, and a `while` loop all in the same program.

- stats
- 100 | Points | success
- online_upload | Submission | accent

## Why This Matters

Loops are how programs handle repetition without requiring you to write the same code dozens of times. Whenever a program processes a list, counts through a range, or waits for something to happen, it is using a loop. Knowing which loop to use — and how to write it — is an everyday skill in JavaScript.

## Skills You Need

Before you start, make sure you are comfortable with:

- The structure of a `for` loop: `for (let i = 0; i < limit; i++)`
- The structure of a `while` loop: `while (condition) { }`
- The structure of a `for...of` loop: `for (const item of array)`
- How `break` and `continue` work
- How to access an array item by its index

If any of these feel shaky, re-read the Session 7 Key Concepts section before you begin.

## What You Will Build

You will create a file called `loops.js` (or `loops.html` with a `<script>` block) that includes three loop tasks:

**Task 1 — Count to ten:** Use a `for` loop to print the numbers 1 through 10, one per line.

**Task 2 — Print an array with index:** Create an array of at least 5 items (your choice of theme — colours, foods, cities, etc.). Use a `for...of` loop with `.entries()` to print each item along with its index number. Each line should look like: `0: apple`.

**Task 3 — Count down:** Use a `while` loop to count down from 10 to 1. Print each number. After the loop ends, print "Blastoff!" on a new line.

## Step-by-Step Instructions

- steps: Step-by-Step Instructions
- Step 1 — Create your file. Name it `loops.js` or `loops.html`. Add a comment at the top with your name and the date.
- Step 2 — Task 1: for loop. Write `for (let i = 1; i <= 10; i++)` and inside the loop, write `console.log(i)`. Test that it prints 1 through 10.
- Step 3 — Task 2: create your array. Pick a theme and create a `const` array with at least 5 items. Give the array a meaningful name.
- Step 4 — Task 2: for...of with entries. Write `for (const [index, item] of yourArray.entries())` and inside the loop, log `index + ": " + item`. Test that each line shows the index and the item.
- Step 5 — Task 3: while loop. Declare `let countdown = 10` before the loop. Write `while (countdown >= 1)` and inside the loop, log `countdown`, then do `countdown--` to subtract 1 each time.
- Step 6 — After the while loop, add `console.log("Blastoff!")` outside the loop (not inside it).
- Step 7 — Test everything. Open your file in a browser (F12 for console) and make sure all three tasks print correctly with no errors.

## Success Criteria

- checklist: Success Criteria
- Task 1: `for` loop prints the numbers 1 through 10, one per line
- Task 2: Array has at least 5 items and a meaningful name
- Task 2: `for...of` with `.entries()` prints each item with its index on the same line
- Task 3: `while` loop counts down from 10 to 1 (not 0), one number per line
- Task 3: "Blastoff!" is printed after the countdown ends
- Code runs without errors
- Variable names are meaningful (not `a`, `i2`, `x`)

- flow-accordion: Stretch Levels

###### Base — Required for everyone
Complete all three tasks as described. All output must appear in the console with no errors. Every student must reach this level.

###### Intermediate — If you finish Base with time remaining
Add a fourth task using a `for` loop that prints only the **even** numbers between 1 and 20. Use the `continue` keyword to skip odd numbers. Also add a fifth task: use a `for` loop that starts at 1, prints numbers, and uses `break` to stop as soon as it reaches a number that is greater than 7.

###### Advanced — Challenge yourself
Create an array of 10 numbers (mix of positive and negative). Write a `for...of` loop that adds up only the positive numbers and logs the total. Then write a second loop that finds the largest number in the array without using any built-in Math methods — just a loop and an `if` statement. Log the largest number at the end.

---

{{include:session-footer}}

{{include:completion-checklist}}
