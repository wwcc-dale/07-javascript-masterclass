---
indent: 2
name: "Assignment: Student Data Loader"
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
  - json-files
  - promises
---

[lead]You have seen how fetch() works with local JSON files — now you will create your own data file and write the JavaScript to load it, filter it, and display the results.

# Assignment: Student Data Loader

In this assignment you will create a JSON file with student data and an HTML file that fetches that data, filters it, and logs the results to the console. You will use the `.then()` chain and add error handling with `.catch()`.

- stats
- 100 | Points | success
- online_upload | Submission | accent

---

## Why This Matters

Almost every web application loads data from an external source — a database, an API, a file. Fetch is the standard tool for doing that. Knowing how to create, load, and process JSON data is a fundamental skill for building real web apps.

---

## Skills You Need

Before you start, make sure you can answer these from Session 22:

- What does `fetch(url)` return?
- What is the difference between the Response object and the actual data?
- How do you parse JSON from a Response?
- What does `response.ok` tell you?
- What does `.catch()` do in a fetch chain?

If you are unsure, re-read the Key Concepts section of the Session 22 page.

---

## What You Will Build

You will create two files:

1. **`students.json`** — a JSON array with at least 5 student objects
2. **`student-loader.html`** — an HTML file that fetches the JSON and processes it

The HTML file will:
- Fetch `students.json` using `fetch()`
- Use `.then(response => response.json())` to parse the data
- Filter the array to only students with a grade of `"A"`
- Log the names of those students to the console
- Log the total count of A-grade students
- Handle fetch errors with `.catch()`

---

## Step-by-Step Instructions

- steps: Step-by-Step Instructions
- Step 1 — Create a file called `students.json` in the same folder as your HTML file. Create a JSON array with at least 5 student objects. Each object must have these three properties: `name` (string), `grade` (string — use letter grades like "A", "B", "C"), and `year` (number — the year of school, 1–4). Make sure at least 2 students have grade "A". Use double quotes for all keys and string values.
- Step 2 — Create a file called `student-loader.html` using the HTML skeleton at the bottom of this page.
- Step 3 — Inside the `<script>` tag, write a `fetch("students.json")` call that chains `.then(response => response.json())`. In the next `.then()`, receive the data as `students`.
- Step 4 — Inside the second `.then()`, use `.filter()` to create a new array called `aStudents` that contains only students where `grade === "A"`.
- Step 5 — Log the message `"A-grade students:"` followed by the count of `aStudents`.
- Step 6 — Use `.forEach()` on `aStudents` to log each student's name to the console.
- Step 7 — Add a `.catch()` at the end of the chain. In the catch handler, log `"Could not load student data:"` followed by `error.message`.
- Step 8 — Open `student-loader.html` in a browser (use a local server if needed). Open the console and confirm the A-grade students are displayed correctly.
- Step 9 — Double-check your JSON file is valid. A common mistake is using single quotes or leaving a trailing comma after the last item. You can paste your JSON into a text editor and look for red underlines.
- Step 10 — Upload both `students.json` and `student-loader.html` to Canvas.

**HTML skeleton:**

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Student Data Loader</title>
</head>
<body>
  <h1>Student Data Loader</h1>
  <p>Open the browser console to see the output.</p>

  <script>
    // Your JavaScript goes here

  </script>
</body>
</html>
```

**Example `students.json`:**

```json
[
  { "name": "Alex Rivera", "grade": "A", "year": 2 },
  { "name": "Jamie Chen",  "grade": "B", "year": 1 },
  { "name": "Sam Patel",   "grade": "A", "year": 3 },
  { "name": "Morgan Lee",  "grade": "C", "year": 2 },
  { "name": "Casey Kim",   "grade": "B", "year": 4 }
]
```

Use this as a starting point but change the data to your own made-up students.

---

## Success Criteria

- checklist: Success Criteria
- `students.json` is a valid JSON array with at least 5 student objects
- Each student object has `name` (string), `grade` (string), and `year` (number)
- At least 2 students have grade `"A"`
- `student-loader.html` opens in a browser without errors
- `fetch("students.json")` is called and chained with `.then(response => response.json())`
- The data is filtered with `.filter()` to find A-grade students
- The count of A-grade students is logged
- Each A-grade student's name is logged using `.forEach()`
- A `.catch()` handler is present and logs a useful error message
- Both files are uploaded to Canvas

---

- flow-accordion: Stretch Levels

###### Base — Required for everyone
Complete all steps as described. Create the JSON file, fetch and parse it, filter to A-grade students, log names and count, and handle errors with .catch().

###### Intermediate — More challenge
After logging A-grade students, also log the **average year** of all students (add up all the year values and divide by the total count). Format the result to two decimal places using `.toFixed(2)`. Also log the student with the highest year number using `.reduce()`.

###### Advanced — Push yourself
Instead of logging to the console, write the output to the HTML page. Create a `<div id="output">` element in your HTML. After fetching and filtering, build an HTML string using `.map()` and template literals (e.g., `<li>Alex Rivera — Year 2 — Grade A</li>`) and set `document.getElementById("output").innerHTML` to that string. Include a heading like "A-Grade Students" and a count below the list.

---

{{include:session-footer}}

{{include:completion-checklist}}
