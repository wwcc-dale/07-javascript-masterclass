---
name: "Assignment: Greeting Generator"
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
  - strings
  - numbers
  - code-style
  - template-literals
---

[lead]Template literals and string methods turn raw data into real messages — and in this assignment you will build a greeting generator that takes a name and a favorite number and produces a personalized output using the tools you just learned.

# Assignment: Greeting Generator

In this assignment you will write a JavaScript program that uses string methods and a template literal to build and display a personalized greeting message.

- stats
- 100 | Points | success
- online_upload | Submission | accent

---

## Why This Matters

Almost every real web application creates messages by combining text with data. Login confirmations, email subjects, error messages, personalized dashboards — they all work this way. Learning to build dynamic text from variables is one of the most practical JavaScript skills you can have.

---

## Skills You Need

Before you start, make sure you can use these from Session 3:

- Template literals with `${}` — how to embed a variable in a string
- `.toUpperCase()` and `.toLowerCase()` — how to change the case of a string
- `.trim()` — how to remove extra spaces
- `.length` — how to find the length of a string
- `Math.round()` or `Math.floor()` — how to round a number

If you need a refresher, check the Session 3 Key Concepts section.

---

## What You Will Build

Create a file called `greeting-generator.html`. Inside the `<script>` tag, you will:

1. Declare a variable `userName` and assign it a name as a string (include some extra spaces at the start or end to practice `.trim()`)
2. Declare a variable `favoriteNumber` and assign it a decimal number (like `7.8`)
3. Use `.trim()` to clean up the name
4. Use `.toUpperCase()` to make the name all caps for one version of the greeting
5. Use `Math.round()` to round the favorite number to the nearest whole number
6. Use a template literal to build and log a personalized greeting message

Your final console output should look something like this:

```
Hello, JORDAN! Welcome to JavaScript.
Your favorite number is 7.8, which rounds to 8.
Your name has 6 characters.
```

(Values will vary based on your chosen name and number.)

---

## Step-by-Step Instructions

- steps: Step-by-Step Instructions
- Step 1 — Create a new file called `greeting-generator.html`. Copy the HTML skeleton from Session 1 (update the title).
- Step 2 — In the `<script>` section, declare `userName` with a string value that has at least one leading or trailing space. Example: `let userName = "  Jordan  ";`
- Step 3 — Declare `favoriteNumber` with a decimal value. Example: `let favoriteNumber = 7.8;`
- Step 4 — Create a new variable `cleanName` and assign it `userName.trim()` to remove the extra spaces.
- Step 5 — Create a variable `upperName` and assign it `cleanName.toUpperCase()`.
- Step 6 — Create a variable `roundedNumber` and assign it `Math.round(favoriteNumber)`.
- Step 7 — Create a variable `nameLength` and assign it `cleanName.length`.
- Step 8 — Use three template literals (one per line of output) to build the three greeting lines shown above and log them to the console.
- Step 9 — Save and open in a browser. Check the Console tab for your output.
- Step 10 — Confirm the output looks correct and all three lines appear. Upload to Canvas.

---

## Success Criteria

- checklist: Success Criteria
- File is named `greeting-generator.html` and opens without errors
- `userName` includes extra leading or trailing whitespace
- `.trim()` is used to clean the name before display
- `.toUpperCase()` is used to create an uppercase version of the name
- `Math.round()` is used on the favorite number
- `.length` is used to find the character count of the name
- Three template literals build and log the three output lines
- Output in the console matches the expected format
- Code has at least two comments explaining what the code does
- Code is indented neatly

---

- flow-accordion: Stretch Levels

###### Base — Required for everyone
Complete all the steps above: declare, trim, uppercase, round, find length, and log three template literal lines.

###### Intermediate — More challenge
Add a fourth line of output that uses `.includes()` to check whether the user's name contains a specific letter (for example, the letter "a") and logs a message like: `"Does your name contain the letter 'a'? true"`. Also add a fifth line that uses `.slice()` to log just the first three characters of the cleaned name.

###### Advanced — Push yourself
Add a "name report" section that logs six pieces of information about the name: the original (untrimmed), the trimmed version, the uppercase version, the lowercase version, the length, and the result of checking if the name includes at least one specific letter. Format all six lines using template literals. Then add `Number.parseFloat()` to convert a string like `"9.5 stars"` to a number, log the result, and explain in a comment what `.parseFloat()` does with the extra text.

---

{{include:session-footer}}

{{include:completion-checklist}}
