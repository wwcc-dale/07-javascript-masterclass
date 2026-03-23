---
name: "Assignment: Callbacks and Timers"
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
  - callbacks
  - timers
---

[lead]You have read about callbacks and timers — now write them yourself. In this assignment you will use `setTimeout`, `setInterval`, and a custom callback function to see how JavaScript schedules and responds to work over time.

# Assignment: Callbacks and Timers

In this assignment you will create an HTML file with a `<script>` section that uses all three callback tools you learned today: `setTimeout`, `setInterval`, and a custom function that accepts a callback.

- stats
- 100 | Points | success
- online_upload | Submission | accent

---

## Why This Matters

Nearly every real-world JavaScript program does something that takes time — loading data, waiting for a user action, updating a display on a schedule. Callbacks are the foundation of all of that. You will use `setTimeout` and `setInterval` in games, animations, clocks, and data loading — so getting comfortable with them now pays off immediately.

---

## Skills You Need

Before you start, make sure you can answer these questions from Session 16:

- What is a callback function? How do you pass one to another function?
- What is the difference between `setTimeout` and `setInterval`?
- How do you stop a running `setInterval`?

If you are unsure, go back to the Key Concepts section of the Session 16 page.

---

## What You Will Build

You will create a file called `callbacks-timers.html`. Inside it you will write a `<script>` with three parts:

1. **Part 1 — Delayed message:** Use `setTimeout` to log a message to the console exactly 3 seconds after the page loads.
2. **Part 2 — Counting interval:** Use `setInterval` to count up from 1, logging each number to the console once per second. Stop automatically when you reach 5 using `clearInterval`.
3. **Part 3 — Custom callback function:** Write a function called `calculate` that accepts two numbers and a callback. Inside `calculate`, add the two numbers together and pass the result to the callback. Call `calculate` with two numbers and a callback that logs the result.

---

## Step-by-Step Instructions

- steps: Step-by-Step Instructions
- Step 1 — Create a new file called `callbacks-timers.html`. Start with the HTML skeleton shown below.
- Step 2 — Inside the `<script>` tag, add a comment that says `// Part 1: setTimeout`. Below it, write a `setTimeout` call with a 3000 ms delay. The callback should log the message `"3 seconds have passed!"` to the console.
- Step 3 — Add a comment that says `// Part 2: setInterval`. Declare a variable `let count = 0;`. Write a `setInterval` that runs every 1000 ms. Inside the interval callback: increment `count` by 1, log `"Count: " + count`, and check if `count === 5`. If it is, call `clearInterval` to stop the interval and log `"Interval stopped."`.
- Step 4 — Add a comment that says `// Part 3: Custom callback`. Write a function called `calculate(a, b, callback)`. Inside the function, compute `const result = a + b;` and then call `callback(result)`.
- Step 5 — Call your `calculate` function. Pass in two numbers of your choice and an arrow function callback that logs `"The result is: " + result` to the console.
- Step 6 — Save the file and open it in a browser. Open the browser console (right-click the page, choose Inspect, then Console). You should see the result from `calculate` appear immediately, the counting interval tick once per second for 5 seconds, and then the delayed message from `setTimeout` appear at 3 seconds.
- Step 7 — Check the console for any errors. Fix any issues you find.
- Step 8 — When everything works correctly, upload `callbacks-timers.html` to Canvas.

**HTML skeleton:**

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Callbacks and Timers</title>
</head>
<body>
  <h1>Callbacks and Timers</h1>
  <p>Open the browser console to see the output.</p>

  <script>
    // Part 1: setTimeout

    // Part 2: setInterval

    // Part 3: Custom callback

  </script>
</body>
</html>
```

---

## Success Criteria

- checklist: Success Criteria
- The file is named `callbacks-timers.html` and opens in a browser without errors
- Part 1: A `setTimeout` with a 3000 ms delay logs a message after 3 seconds
- Part 2: A `setInterval` counts from 1 to 5, logging each number once per second
- Part 2: `clearInterval` is called when count reaches 5 and the interval stops
- Part 3: A function named `calculate` is defined that accepts two numbers and a callback
- Part 3: `calculate` adds the numbers and passes the result to the callback
- Part 3: `calculate` is called and the result appears in the console
- Console shows no JavaScript errors
- Code uses comments to label each part

---

- flow-accordion: Stretch Levels

###### Base — Required for everyone
Complete all three parts as described above. The setTimeout fires at 3 seconds, the interval counts to 5 and stops, and the custom callback function works correctly.

###### Intermediate — More challenge
Modify Part 2 so the interval also displays the current count on the page inside a `<p>` element (use `document.getElementById` or `document.querySelector`). The page text should update live as the counter ticks. When the counter reaches 5, the page should display "Done!" instead of the count.

###### Advanced — Push yourself
Add a fourth part: write a function called `repeatTask(task, times, delayMs)` that accepts a callback function `task`, a number `times`, and a delay `delayMs`. The function should call `task` exactly `times` times, spaced `delayMs` apart, using `setTimeout` (not `setInterval`). Each call should pass the current call number (1, 2, 3…) to `task`. Demonstrate it by calling `repeatTask` with a callback that logs `"Task run #" + n` and settings of your choice.

---

{{include:session-footer}}

{{include:completion-checklist}}
