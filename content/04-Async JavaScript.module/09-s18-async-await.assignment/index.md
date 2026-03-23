---
name: "Assignment: Async/Await"
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
  - async-await
  - async-javascript
---

[lead]You chained Promises in Session 17 — now rewrite that logic using async/await. You will also demonstrate the real difference between running async operations one at a time versus all at once.

# Assignment: Async/Await

You will create an HTML file that rewrites the Session 17 delay-chain using async/await, then writes two async functions — one that runs operations sequentially and one that runs them in parallel — and logs the timing difference.

- stats
- 100 | Points | success
- online_upload | Submission | accent

---

## Why This Matters

Most modern JavaScript code you read in the real world uses async/await. Job listings for web developers specifically mention it. Being able to write it clearly — and knowing when to use sequential vs. parallel — is a skill that sets you apart.

---

## Skills You Need

Before you start, make sure you can answer these questions from Session 18:

- What does adding `async` before a function do?
- What does `await` do, and where can you use it?
- How do you handle errors in an async function?
- What is the difference between running two `await` expressions one after another versus wrapping them in `Promise.all`?

If you are unsure, go back to the Key Concepts section of the Session 18 page.

---

## What You Will Build

You will create a file called `async-await.html`. Your script will:

1. Define the same `delay(ms, label)` function from Session 17 (returns a Promise that resolves after `ms` ms with `label + " complete"`).
2. Write an `async function runSequential()` that awaits three delays in order: 400 ms "Alpha", 400 ms "Beta", 400 ms "Gamma". Log the result of each with `console.log`. Before the first await, log the start time. After the last await, log how long it took (`Date.now()` difference).
3. Write an `async function runParallel()` that uses `Promise.all` to run the same three delays at the same time. Log the results array. Log timing the same way.
4. Add error handling: write an `async function riskyTask()` that awaits a Promise that rejects with `"Oops!"`. Wrap the await in a `try/catch` and log the error message in the catch block.
5. Call `runSequential()`, then `runParallel()`, then `riskyTask()` at the bottom of the script.

---

## Step-by-Step Instructions

- steps: Step-by-Step Instructions
- Step 1 — Create `async-await.html` using the HTML skeleton shown below.
- Step 2 — Inside the `<script>`, write the `delay(ms, label)` function (same as Session 17). It returns a new Promise that resolves after `ms` milliseconds with the string `label + " complete"`.
- Step 3 — Write `async function runSequential()`. At the top, write `const start = Date.now();`. Then write three `await delay(...)` calls for Alpha (400 ms), Beta (400 ms), and Gamma (400 ms). After each await, log the resolved value. After all three, log `"Sequential time: " + (Date.now() - start) + " ms"`.
- Step 4 — Write `async function runParallel()`. At the top, write `const start = Date.now();`. Then write `const results = await Promise.all([delay(400, "Alpha"), delay(400, "Beta"), delay(400, "Gamma")]);`. Log the results array. After the await, log `"Parallel time: " + (Date.now() - start) + " ms"`.
- Step 5 — Write `async function riskyTask()`. Inside, write `try { await new Promise((resolve, reject) => reject("Oops!")); console.log("This line is skipped"); } catch (error) { console.log("Caught error:", error); }`.
- Step 6 — At the bottom of the script, call all three functions: `runSequential(); runParallel(); riskyTask();`
- Step 7 — Save and open the file. Open the browser console. You should see Alpha, Beta, Gamma logged in order from `runSequential`, then the results array from `runParallel`, the timing logs for both, and the caught error from `riskyTask`.
- Step 8 — Observe the timing numbers. Sequential should take about 1200 ms; parallel should take about 400 ms. Fix any errors, then upload `async-await.html` to Canvas.

**HTML skeleton:**

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Async/Await</title>
</head>
<body>
  <h1>Async/Await</h1>
  <p>Open the browser console to see the output.</p>

  <script>
    // delay helper

    // runSequential

    // runParallel

    // riskyTask

    // Call all three
    runSequential();
    runParallel();
    riskyTask();
  </script>
</body>
</html>
```

---

## Success Criteria

- checklist: Success Criteria
- The file is named `async-await.html` and opens in a browser without errors
- `delay(ms, label)` function is defined and returns a Promise
- `runSequential()` is an async function that awaits three delays in order and logs each result
- `runSequential()` logs the total time taken
- `runParallel()` is an async function that uses `Promise.all` with the same three delays
- `runParallel()` logs the results array and the total time taken
- Sequential time is noticeably longer than parallel time in the console output
- `riskyTask()` wraps an awaited rejected Promise in try/catch and logs the error
- All three functions are called at the bottom of the script
- Console shows no unhandled errors

---

- flow-accordion: Stretch Levels

###### Base — Required for everyone
Complete all four parts as described: delay helper, runSequential with timing, runParallel with timing, and riskyTask with try/catch.

###### Intermediate — More challenge
Modify `runSequential` so that the result of each step is passed as part of the label for the next step. For example, after awaiting `delay(400, "Alpha")`, pass the result string to the next delay as part of its label: `delay(400, result + " → Beta")`. Chain all three this way so the final logged value shows the full history: `"Alpha complete → Beta complete → Gamma complete"`.

###### Advanced — Push yourself
Write an async function called `runWithTimeout(task, ms)` that accepts a Promise-returning function `task` and a number `ms`. It should race `task()` against a timeout Promise that rejects after `ms` milliseconds. If the timeout wins, log `"Task timed out"`. If the task wins, log `"Task completed: " + result`. Demonstrate it twice: once where the task finishes in time (`delay(300, "Quick")`  with a 500 ms timeout) and once where it does not (`delay(800, "Slow")` with a 500 ms timeout).

---

{{include:session-footer}}

{{include:completion-checklist}}
