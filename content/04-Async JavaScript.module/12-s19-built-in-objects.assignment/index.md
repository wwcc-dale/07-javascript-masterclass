---
indent: 2
name: "Assignment: Built-in Objects"
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
  - 04-MOD
topics:
  - math-object
  - date-object
  - json
  - set
  - map
---

[lead]JavaScript's built-in objects are tools you will reach for constantly. In this assignment you will use Math, Date, JSON, Set, and Map in one file to see how naturally they fit together.

# Assignment: Built-in Objects

You will create an HTML file that demonstrates five of the built-in tools covered in Session 19. Each part is short — the goal is to use each tool at least once so it becomes familiar.

- stats
- 100 | Points | success
- online_upload | Submission | accent

---

## Why This Matters

You will use `Math.random` every time you write a game or simulation. `Date` is in every dashboard and log. `JSON` is how data moves between a web page and a server. `Set` and `Map` are cleaner alternatives to plain objects for many data tasks. These are everyday tools, not one-time demos.

---

## Skills You Need

Before you start, make sure you can answer these questions from Session 19:

- How do you generate a random integer between 1 and 100?
- What does `getMonth()` return for January, and what do you need to do to get a human-readable month number?
- What is the difference between `JSON.stringify()` and `JSON.parse()`?
- How does a `Set` handle duplicate values?
- How do you use a `Map` to count occurrences of items?

If you are unsure, go back to the Key Concepts section of the Session 19 page.

---

## What You Will Build

You will create a file called `built-in-objects.html`. Your script will have five clearly labeled parts:

**Part 1 — Math:** Generate an array of 10 random integers between 1 and 100. Log the array. Then log the maximum value, minimum value, and sum of the array.

**Part 2 — Date:** Create a `Date` object for today. Log today's full date in a readable format. Log the year, the month number (1-based, not 0-based), and the day of the month separately.

**Part 3 — JSON:** Create a JavaScript object with at least three properties (your choice). Convert it to a JSON string with `JSON.stringify`. Log the string. Then parse it back to an object with `JSON.parse`. Log one property from the parsed object to prove it worked.

**Part 4 — Set:** Start with an array that contains duplicate values (e.g., `[3, 1, 4, 1, 5, 9, 2, 6, 5, 3]`). Create a Set from it to remove duplicates. Convert the Set back to an array. Log the original array and the deduplicated array.

**Part 5 — Map:** Take the string `"the quick brown fox jumps over the lazy dog"`. Split it into an array of words. Use a `Map` to count how many times each word appears. Log the Map. Then log just the counts for `"the"` and `"fox"`.

---

## Step-by-Step Instructions

- steps: Step-by-Step Instructions
- Step 1 — Create `built-in-objects.html` using the HTML skeleton shown below.
- Step 2 — Part 1: Declare `const numbers = [];`. Use a `for` loop to push 10 random integers (1–100) into the array. Log the array. Log `Math.max(...numbers)`, `Math.min(...numbers)`, and the sum (use `reduce` or a for loop).
- Step 3 — Part 2: Write `const today = new Date();`. Log `today.toLocaleDateString()`. Log `today.getFullYear()`. Log `today.getMonth() + 1` (add 1 to convert from 0-based). Log `today.getDate()`.
- Step 4 — Part 3: Create an object like `const student = { name: "Alex", grade: 11, subject: "JavaScript" };`. Write `const json = JSON.stringify(student);` and log it. Write `const parsed = JSON.parse(json);` and log `parsed.name` to verify.
- Step 5 — Part 4: Declare `const withDuplicates = [3, 1, 4, 1, 5, 9, 2, 6, 5, 3];`. Write `const unique = [...new Set(withDuplicates)];`. Log both arrays with labels.
- Step 6 — Part 5: Declare the sentence string. Write `const words = sentence.split(" ");`. Create `const freq = new Map();`. Loop through `words` and for each word, write `freq.set(word, (freq.get(word) || 0) + 1);`. Log `freq`. Log `freq.get("the")` and `freq.get("fox")`.
- Step 7 — Save and open the file in a browser. Check the console for all five parts. Fix any errors.
- Step 8 — Upload `built-in-objects.html` to Canvas.

**HTML skeleton:**

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Built-in Objects</title>
</head>
<body>
  <h1>Built-in Objects</h1>
  <p>Open the browser console to see the output.</p>

  <script>
    // Part 1: Math

    // Part 2: Date

    // Part 3: JSON

    // Part 4: Set

    // Part 5: Map

  </script>
</body>
</html>
```

---

## Success Criteria

- checklist: Success Criteria
- The file is named `built-in-objects.html` and opens in a browser without errors
- Part 1: An array of 10 random integers (1–100) is generated and logged; max, min, and sum are logged
- Part 2: Today's date is logged in readable format; year, month (1-based), and day are logged separately
- Part 3: An object is converted to a JSON string and logged; it is parsed back and a property is logged
- Part 4: A Set removes duplicates from an array; both the original and deduplicated arrays are logged
- Part 5: A Map counts word frequency; the full Map and counts for "the" and "fox" are logged
- All five parts are labeled with comments
- Console shows no JavaScript errors

---

- flow-accordion: Stretch Levels

###### Base — Required for everyone
Complete all five parts as described above.

###### Intermediate — More challenge
Extend Part 1: after generating the 10 random numbers, also log the median value (sort the array first, then find the middle element). Extend Part 2: log the full day name (Monday, Tuesday, etc.) using an array of day names and `getDay()` as the index.

###### Advanced — Push yourself
Extend Part 5: after building the word frequency Map, find and log the word that appears most often (the mode). Then filter the words array to only unique words (use a Set) and log how many unique words are in the sentence. Finally, use `JSON.stringify` to convert the frequency counts to a plain object and log the result so you can see the full word count in JSON format.

---

{{include:session-footer}}

{{include:completion-checklist}}
