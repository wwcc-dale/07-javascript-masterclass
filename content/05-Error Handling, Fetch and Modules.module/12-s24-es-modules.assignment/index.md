---
name: "Assignment: Helper Module Project"
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
  - es-modules
  - import-export
  - named-exports
  - default-exports
---

[lead]You have learned how to export and import between JavaScript files — now you will build a real three-file project where each module has its own job and they all work together.

# Assignment: Helper Module Project

In this assignment you will create a three-file JavaScript project using ES Modules. One file exports utility functions, one exports a default data array, and the main script imports from both to process and display data.

- stats
- 100 | Points | success
- online_upload | Submission | accent

---

## Why This Matters

Real applications are not one giant file. They are organized into modules: utility helpers in one place, data in another, application logic in a third. Learning to work across multiple files — and import only what you need — is how you build code that other people (and future you) can actually understand and maintain.

---

## Skills You Need

Before you start, make sure you can answer these from Session 24:

- What is the difference between a named export and a default export?
- How do you import a named export vs. a default export?
- What attribute must a `<script>` tag have to use modules?
- Why do modules need to be served through a local server in most browsers?
- What does `import * as Name` do?

If you are unsure, re-read the Key Concepts section of the Session 24 page.

---

## What You Will Build

You will create four files in the same folder:

1. **`utils.js`** — exports three named helper functions: `formatName`, `clamp`, `randomInt`
2. **`data.js`** — exports a default array of person objects
3. **`app.js`** — imports from both `utils.js` and `data.js`, processes the data, and logs results
4. **`index.html`** — loads `app.js` as a module

---

## Step-by-Step Instructions

- steps: Step-by-Step Instructions
- Step 1 — Create a folder for this project. Inside it, create `index.html` using the skeleton at the bottom of this page. Make sure the `<script>` tag uses `type="module"` and points to `app.js`.
- Step 2 — Create `utils.js`. Export three named functions: `formatName(first, last)` that returns `last + ", " + first`; `clamp(value, min, max)` that returns `value` constrained to the range `[min, max]` (if value is less than min, return min; if greater than max, return max; otherwise return value); `randomInt(min, max)` that returns a random whole number between min and max (inclusive). Use `Math.floor(Math.random() * (max - min + 1)) + min` for randomInt.
- Step 3 — Create `data.js`. Define an array called `people` with at least 5 objects. Each person object must have: `firstName` (string), `lastName` (string), `age` (number), and `score` (number between 0 and 200). Export `people` as the **default export**.
- Step 4 — Create `app.js`. At the top, import the three utility functions from `./utils.js` using named imports. On the next line, import the `people` array from `./data.js` using a default import.
- Step 5 — In `app.js`, use `.map()` on the `people` array to create a new array called `formatted`. For each person, call `formatName(person.firstName, person.lastName)` and store the result. Log `"People:"` and then log the `formatted` array.
- Step 6 — Use `.map()` on `people` to create a new array called `clamped` where each person's `score` is passed through `clamp(person.score, 0, 100)`. Log `"Clamped scores:"` and log the `clamped` array.
- Step 7 — Call `randomInt(1, 10)` three times and log the results with the label `"Three random ints:"`. The results should be different each time the page refreshes.
- Step 8 — Add a comment at the top of each file describing what that file does (one sentence is enough).
- Step 9 — Serve the project through a local server (or use a browser that supports modules with file://). Open `index.html`, open the console, and verify all output appears correctly.
- Step 10 — Upload all four files (`utils.js`, `data.js`, `app.js`, `index.html`) to Canvas.

**HTML skeleton:**

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Helper Module Project</title>
</head>
<body>
  <h1>Helper Module Project</h1>
  <p>Open the browser console to see the output.</p>

  <script type="module" src="app.js"></script>
</body>
</html>
```

---

## Success Criteria

- checklist: Success Criteria
- All four files are present: `utils.js`, `data.js`, `app.js`, `index.html`
- `utils.js` uses named exports for all three functions (`formatName`, `clamp`, `randomInt`)
- `data.js` exports its `people` array as a default export
- `app.js` correctly imports named functions from `utils.js`
- `app.js` correctly imports the default export from `data.js`
- `index.html` uses `type="module"` on the script tag pointing to `app.js`
- `formatted` array uses `formatName` and is logged correctly
- `clamped` array uses `clamp` and is logged correctly
- Three random ints are logged using `randomInt`
- Each file has a comment describing its purpose
- No errors in the browser console
- All four files uploaded to Canvas

---

## Stretch Levels

- accordion: Stretch Levels
- Base — Required for everyone
  - Complete all steps as described. Create all four files, export and import correctly, and verify all output in the console.
- Intermediate — More challenge
  - Add a fourth named export to `utils.js` called `average(arr)` that takes an array of numbers and returns their average. Import it in `app.js` and use it to calculate and log the average score from the `people` array (using the original scores, not clamped ones). Also add a named export to `data.js` — a constant called `MAX_SCORE` set to `200`. Import it in `app.js` and log it.
- Advanced — Push yourself
  - Write a fifth utility function `groupBy(arr, key)` that takes an array of objects and a key name, and returns an object where each unique value of that key is a property containing an array of matching objects. For example, `groupBy(people, "age")` would group all people by their age. Export it from `utils.js`, import it in `app.js`, and use it to group the `people` array by a property of your choice. Log the resulting grouped object. This is the same pattern as `Array.prototype.reduce` for grouping, but as a reusable utility.

{{include:session-footer}}

{{include:completion-checklist}}
