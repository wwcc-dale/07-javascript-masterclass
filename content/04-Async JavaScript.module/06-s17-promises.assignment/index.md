---
indent: 2
name: "Assignment: Promises"
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
  - promises
  - async-javascript
---

[lead]Callbacks nest; Promises chain. In this assignment you will write a reusable `delay` function that returns a Promise, chain three delays together with messages at each step, and handle errors with `.catch()`.

# Assignment: Promises

You will create an HTML file that demonstrates Promise creation, chaining, and error handling using only `setTimeout`-based Promises — no network required.

- stats
- 100 | Points | success
- online_upload | Submission | accent

---

## Why This Matters

Every modern JavaScript API — from fetching data to reading files — returns Promises. Knowing how to create, chain, and handle them is one of the most important skills in the language. The `delay` function pattern you write here is also the exact pattern behind real async libraries.

---

## Skills You Need

Before you start, make sure you can answer these questions from Session 17:

- What are the three states of a Promise?
- How do you call `resolve` and `reject` inside a Promise constructor?
- How do you chain `.then()` calls so the next step receives the result of the previous one?
- What does `.catch()` do, and where do you place it in a chain?

If you are unsure, go back to the Key Concepts section of the Session 17 page.

---

## What You Will Build

You will create a file called `promises.html`. Your script will:

1. Define a `delay(ms, label)` function that returns a Promise. The Promise resolves after `ms` milliseconds with the string `label + " complete"`.
2. Chain three `delay` calls together: 500 ms for "Step 1", 800 ms for "Step 2", and 600 ms for "Step 3". Log the result of each step inside its `.then()`.
3. Add a `.catch()` at the end of the chain that logs any error.
4. Add a `.finally()` that logs `"All steps finished."` when the chain completes.
5. Demonstrate a rejected Promise: create a second Promise that rejects with the message `"Simulated failure"` and attach a `.catch()` to log the error message.

---

## Step-by-Step Instructions

- steps: Step-by-Step Instructions
- Step 1 — Create `promises.html` using the HTML skeleton below.
- Step 2 — Inside the `<script>`, write the `delay` function. It takes `ms` (a number) and `label` (a string). Inside, return `new Promise(function(resolve) { setTimeout(function() { resolve(label + " complete"); }, ms); });`
- Step 3 — Write the chain. Start with `delay(500, "Step 1")`. In the `.then()`, log the result and return `delay(800, "Step 2")`. In the next `.then()`, log the result and return `delay(600, "Step 3")`. In the final `.then()`, just log the result.
- Step 4 — Add `.catch((error) => console.log("Error:", error))` at the end of the chain.
- Step 5 — Add `.finally(() => console.log("All steps finished."))` after the `.catch()`.
- Step 6 — Below the chain, create a rejected Promise: `const failPromise = new Promise(function(resolve, reject) { reject("Simulated failure"); });`. Attach `.catch((error) => console.log("Caught rejection:", error))` to it.
- Step 7 — Save and open the file in a browser. Open the console. You should see Step 1, Step 2, Step 3 results logged in order, then "All steps finished.", and then the rejection message.
- Step 8 — Fix any errors you see. When everything looks correct, upload `promises.html` to Canvas.

**HTML skeleton:**

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Promises</title>
</head>
<body>
  <h1>Promises</h1>
  <p>Open the browser console to see the output.</p>

  <script>
    // delay function

    // Promise chain

    // Rejected Promise demo

  </script>
</body>
</html>
```

---

## Success Criteria

- checklist: Success Criteria
- The file is named `promises.html` and opens in a browser without errors
- A `delay(ms, label)` function is defined that returns a Promise resolving after ms milliseconds
- Three `delay` calls are chained with `.then()` — each step logs its result before starting the next
- A `.catch()` is attached to handle any chain errors
- A `.finally()` logs "All steps finished." after the chain
- A second Promise is created that rejects, and its `.catch()` logs the rejection message
- Console shows all expected output in the correct order
- Code is commented to label each section

---

- flow-accordion: Stretch Levels

###### Base — Required for everyone
Define `delay`, chain three steps, add `.catch()` and `.finally()`, and demonstrate a rejected Promise as described above.

###### Intermediate — More challenge
Add a fourth part using `Promise.all`. Create three `delay` calls with different durations (e.g., 300 ms, 700 ms, 400 ms with labels "Alpha", "Beta", "Gamma"). Run them with `Promise.all` and log the results array. Add a timestamp log before and after so you can see how long `Promise.all` took compared to running them sequentially.

###### Advanced — Push yourself
Implement a `timeout(ms)` function that returns a Promise that rejects after `ms` milliseconds with the message `"Timed out!"`. Then use `Promise.race` to race a `delay(2000, "Slow task")` against `timeout(1000)`. The race should reject because the timeout wins. Handle the rejection with `.catch()`. Then race a `delay(500, "Fast task")` against `timeout(1000)` — this time the task should win. Log whether each race was won by the task or the timeout.

---

{{include:session-footer}}

{{include:completion-checklist}}
