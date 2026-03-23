---
name: "Assignment: Async Student Loader"
published: false
points_possible: 100
grading_type: points
submission_types:
  - online_upload
allowed_extensions:
  - html
  - js
  - json
  - txt
due_at: null
outcomes:
  - 04-MOD
topics:
  - fetch-api
  - async-await
  - status-codes
  - post-requests
---

[lead]Time to level up your fetch skills. You will rewrite the Session 22 loader using async/await, add response status checking with custom error messages, and build a simulated POST request.

# Assignment: Async Student Loader

In this assignment you will take your Session 22 student loader and rewrite it using async/await. You will add proper `response.ok` checking with different messages for different status codes. You will also build a POST request configuration object and log it — simulating what a real POST would look like.

- stats
- 100 | Points | success
- online_upload | Submission | accent

---

## Why This Matters

Most professional JavaScript code uses async/await instead of raw `.then()` chains. It reads like regular code, handles errors more cleanly, and is easier to debug. Adding proper status code checks is the difference between code that silently fails and code that tells you exactly what went wrong.

---

## Skills You Need

Before you start, make sure you can answer these from Session 23:

- How do you write an `async` function?
- How do you `await` a fetch response and then `await` the JSON?
- Why does fetch NOT automatically throw for 404 errors?
- What does `response.ok` check?
- What are the three parts of a POST request config object?

If you are unsure, re-read the Key Concepts section of the Session 23 page.

---

## What You Will Build

You will create a file called `async-loader.html`. You can reuse your `students.json` from Session 22. Your HTML file will:

1. Define an `async` function called `loadStudents(url)` that fetches and returns the student data
2. Inside `loadStudents`, check `response.ok` and throw custom error messages for 404 and other errors
3. Use `try/catch` inside the async function for all error handling
4. Call `loadStudents("students.json")` and use the returned data to filter and log A-grade students
5. Build a POST request configuration object (do not send it — log it to the console)

---

## Step-by-Step Instructions

- steps: Step-by-Step Instructions
- Step 1 — Create a file called `async-loader.html` using the HTML skeleton at the bottom of this page. Copy your `students.json` from Session 22 into the same folder (or create a new one).
- Step 2 — Inside the `<script>` tag, write an `async` function called `loadStudents(url)`. Use `const response = await fetch(url)` to get the response.
- Step 3 — After the await, check `response.ok`. If it is `false`, check if `response.status === 404` — if so, throw `new Error("File not found (404): " + url)`. For any other bad status, throw `new Error("HTTP error: " + response.status)`.
- Step 4 — After the status check, use `const students = await response.json()` to parse the data. Return `students`.
- Step 5 — Wrap all of the above in a `try/catch`. In the catch block, log `"loadStudents failed: " + error.message` and return an empty array `[]`.
- Step 6 — After the function definition, call it: `const students = await loadStudents("students.json")`. Because you are using `await` outside an async function, wrap this in an immediately invoked async function expression (IIFE): `(async () => { ... })();`
- Step 7 — Inside the IIFE, after getting `students`, filter for A-grade students and log their names (same as Session 22). Also log the total count.
- Step 8 — Still inside the IIFE, build a POST request config object. Create a variable called `newStudent` with a name, grade, and year. Create a variable called `postConfig` with `method`, `headers`, and `body` (use `JSON.stringify(newStudent)` for the body). Log the message `"POST request config:"` and then log `postConfig`. Add a comment: `// In a real app, this would be passed to fetch() as the second argument`.
- Step 9 — Test the error handling: temporarily change `"students.json"` to `"missing.json"` and confirm the 404 error message appears in the console. Then change it back.
- Step 10 — Upload both `async-loader.html` and `students.json` to Canvas.

**HTML skeleton:**

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Async Student Loader</title>
</head>
<body>
  <h1>Async Student Loader</h1>
  <p>Open the browser console to see the output.</p>

  <script>
    // Your JavaScript goes here

  </script>
</body>
</html>
```

**IIFE pattern reference:**

```javascript
(async () => {
  const students = await loadStudents("students.json");
  // use students here
})();
```

---

## Success Criteria

- checklist: Success Criteria
- `async-loader.html` opens in a browser without errors
- `loadStudents(url)` is declared as an `async` function
- The function uses `await fetch(url)` and `await response.json()`
- The function checks `response.ok` and throws a 404-specific error message
- The function has a `try/catch` block that catches errors and returns `[]`
- The function is called inside an async IIFE
- A-grade students are filtered, their names logged, and count logged
- A POST config object is built with `method`, `headers`, and `body`
- The POST config is logged with a comment explaining it is not actually sent
- Both files are uploaded to Canvas

---

## Stretch Levels

- accordion: Stretch Levels
- Base — Required for everyone
  - Complete all steps as described. Write the async loadStudents function with status checking, call it in an IIFE, filter results, and build and log a POST config object.
- Intermediate — More challenge
  - Write a second async function called `loadJSON(url)` that is a generic version of loadStudents — it can load any JSON file, not just students. It should have the same status checking and error handling. Refactor loadStudents to call loadJSON internally. Test it by also loading a second JSON file you create called `courses.json` with at least 3 course objects (each with a title, code, and credits property). Log both sets of data.
- Advanced — Push yourself
  - Write a function called `retryFetch(url, attempts)` that tries to fetch a URL up to `attempts` times before giving up. On each failure, log `"Attempt N failed: [message]"`. Use a loop with async/await. After all attempts fail, throw a final error `"All N attempts failed for: [url]"`. Test it with a file name that does not exist and attempts = 3. This retry pattern is widely used in production code.

{{include:session-footer}}

{{include:completion-checklist}}
