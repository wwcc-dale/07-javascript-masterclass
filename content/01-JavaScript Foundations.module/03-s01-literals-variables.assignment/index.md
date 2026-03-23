---
name: "Assignment: My First Variables"
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
  - literals
  - identifiers
  - variables
---

[lead]You have read about variables and watched them in action — now it is time to write your first real JavaScript code and see it run in a browser.

# Assignment: My First Variables

In this assignment you will create an HTML file with a JavaScript section. You will declare five variables, assign values to them, and print those values to the browser console.

This is the first code you write in this course. Keep it simple, follow the steps, and enjoy seeing your output appear on screen.

- stats
- 100 | Points | success
- online_upload | Submission | accent

---

## Why This Matters

Every JavaScript program stores data in variables. Whether you are building a game, a form, or a web app — variables hold the information your program works with. Writing your first variables is not just an exercise; it is the foundation of everything you will build in this course.

---

## Skills You Need

Before you start, make sure you can answer these questions from Session 1:

- What is the difference between `let` and `const`?
- What are the rules for naming a variable (identifier)?
- How do you use `console.log()` to print a value?

If you are unsure, go back to the Key Concepts section of the Session 1 page.

---

## What You Will Build

You will create a file called `my-variables.html`. Inside it, you will write a `<script>` tag with JavaScript code that:

1. Declares five variables using the correct keyword (`let` or `const`)
2. Assigns a real value to each variable
3. Prints each variable to the console using `console.log()`

Your five variables must be:

| Variable name | Suggested value type | Example |
|---|---|---|
| `name` | string | `"Jordan"` |
| `age` | number | `17` |
| `city` | string | `"Wellington"` |
| `hobby` | string | `"skateboarding"` |
| `favoriteNumber` | number | `7` |

You decide whether each variable uses `let` or `const`. Think about whether the value could change and choose the right keyword.

---

## Step-by-Step Instructions

- steps: Step-by-Step Instructions
- Step 1 — Open your text editor (VS Code or Notepad). Create a new file and save it as `my-variables.html` in a folder you can find later.
- Step 2 — Type the HTML skeleton below exactly as shown. This is the minimum structure every HTML file needs.
- Step 3 — Inside the `<script>` tags, declare your five variables. Use `const` for values that will not change; use `let` for values that might change.
- Step 4 — After your variable declarations, add five `console.log()` statements — one for each variable.
- Step 5 — Save the file. Open it in a web browser (double-click the file or drag it into Chrome or Firefox).
- Step 6 — Open the browser console. In Chrome: right-click the page, choose Inspect, then click the Console tab. You should see your five values printed.
- Step 7 — If any values are missing or you see an error, re-read your code and fix the issue. Compare your code to the Key Concepts examples.
- Step 8 — Once all five values appear correctly in the console, upload your `my-variables.html` file to Canvas.

**HTML skeleton to start with:**

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>My First Variables</title>
</head>
<body>
  <h1>My First Variables</h1>
  <p>Open the console to see the output.</p>

  <script>
    // Your JavaScript goes here

  </script>
</body>
</html>
```

---

## Success Criteria

- checklist: Success Criteria
- The file is named `my-variables.html` and opens in a browser without errors
- Five variables are declared — `name`, `age`, `city`, `hobby`, and `favoriteNumber`
- Each variable uses `let` or `const` (not `var`)
- Each variable holds a real value of the correct type (strings in quotes, numbers without quotes)
- Each variable is printed using `console.log()` and the value appears in the browser console
- Variable names follow camelCase and are spelled correctly
- The code is indented neatly and easy to read

---

- flow-accordion: Stretch Levels

###### Base — Required for everyone
Declare and log all five required variables as described above. Use `let` or `const` correctly. All five values appear in the console.

###### Intermediate — More challenge
Add a label to each `console.log()` so the output reads like `"Name: Jordan"` instead of just `"Jordan"`. Use string concatenation (joining strings with `+`) to combine the label and the value. Example: `console.log("Name: " + name);`

###### Advanced — Push yourself
Declare two additional variables: `fullGreeting` (a string that combines your name and city — for example, `"Jordan from Wellington"`) and `nextBirthday` (your age plus one). Log both. Then add a comment block at the top of your `<script>` explaining what each variable stores and why you chose `let` or `const` for it.

---

{{include:session-footer}}

{{include:completion-checklist}}
