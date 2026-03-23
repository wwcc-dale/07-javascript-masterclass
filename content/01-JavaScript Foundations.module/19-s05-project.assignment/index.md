---
indent: 2
name: "Project: Build a Quiz App — Part 1: Hello, Quiz!"
published: true
points_possible: 100
grading_type: points
submission_types:
  - online_upload
allowed_extensions:
  - html
due_at: null
outcomes:
  - 03-ELEM
topics:
  - literals
  - variables
  - types
  - operators
  - strings
  - conditionals
  - dom
---

[lead]This is the first step in a project you will build all the way to the end of the course — a fully working Trivia Quiz App. Pick any topic you love: movies, sport, animals, food, history, gaming. By the end of Credit 5 you will have something genuinely fun to show people. Today you build the foundation: one question, one answer, one score.

# Project: Build a Trivia Quiz App — Part 1: Hello, Quiz!

You are starting something big today.

Over the next five credits, you will build a complete, interactive Trivia Quiz App — one that loads questions, tracks scores, runs on a timer, and eventually pulls its questions from a data file. Each credit adds a new layer of real functionality.

**Your topic is up to you.** Movies. Animals. Sport. Music. Geography. Food. Whatever you find interesting — that is what your quiz will be about.

Today's goal: get one trivia question on the screen, let the user pick an answer, and show whether they got it right.

- stats
- 100 | Points | success
- online_upload | Submission | accent

---

## Why This Matters

Every interactive web app responds to user input and updates what is on screen. Checking an answer and showing a result is exactly that pattern — just at its simplest. Master this and you understand the core loop of every UI you will ever build.

---

## Skills You Need

This project uses skills from all four Credit 1 sessions:

- Session 1: Variables (`const`, `let`), string literals, comments, `document.getElementById`, `.textContent`
- Session 2: Types, arithmetic, compound assignment (`+=`)
- Session 3: String methods, template literals
- Session 4: `if/else` conditional logic

---

## What You Will Build

A single HTML file called `quiz-app.html` with:

1. A **question** displayed on the page
2. **Four answer buttons**, one of which is correct
3. A **feedback message** that says "Correct! ✓" or "Wrong. The answer was [correct answer]."
4. A **score counter** that increases when the user gets the answer right
5. A **Next Question button** (Base: it shows a second hardcoded question; it resets the page for a new attempt)

Here is an example of what the page could look like in the browser (using an animal trivia topic — yours can be anything):

```
Question 1 of 2

Which animal is the fastest land mammal?

  [ Lion ]   [ Cheetah ]   [ Greyhound ]   [ Pronghorn ]

Score: 1 / 1
```

---

## HTML Starter Structure

Copy this into your `quiz-app.html` file to get started:

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Quiz App</title>
  <style>
    body { font-family: sans-serif; max-width: 600px; margin: 40px auto; padding: 0 20px; }
    button { margin: 6px; padding: 10px 18px; font-size: 1em; cursor: pointer; }
    #feedback { font-size: 1.2em; font-weight: bold; margin: 16px 0; min-height: 28px; }
    #score { color: #444; }
  </style>
</head>
<body>
  <h1>Quiz App</h1>
  <p id="question-text">Loading question...</p>

  <div id="answer-buttons">
    <button id="btn-a"></button>
    <button id="btn-b"></button>
    <button id="btn-c"></button>
    <button id="btn-d"></button>
  </div>

  <p id="feedback"></p>
  <p id="score">Score: 0</p>
  <button id="next-btn" style="display:none;">Next Question →</button>

  <script>
    // Your JavaScript goes here
  </script>
</body>
</html>
```

---

## Step-by-Step Instructions

- steps: Step-by-Step Instructions
- Step 1 — Choose your trivia topic and write two questions. Each question needs: the question text, four options (A, B, C, D), and the correct answer letter. Here are examples to inspire you — but write your OWN about a topic you like:
  - Example (animals): "Which animal is the fastest land mammal?" A) Lion  B) Cheetah  C) Greyhound  D) Pronghorn. Answer: B
  - Example (geography): "What is the capital of Japan?" A) Beijing  B) Seoul  C) Tokyo  D) Bangkok. Answer: C
  - Your questions can be about literally anything — movies, sport, food, games, science, music. Pick something you know!
- Step 2 — Write a `loadQuestion(q)` function. It takes a question object (or a set of variables you group yourself) and updates the DOM: sets `#question-text` to the question, sets each button's `textContent` to the matching option.
- Step 3 — Wire up the answer buttons. Add an `onclick` to each button. When clicked, compare the button's letter to the correct answer. If correct: set `#feedback` text to `"Correct! ✓"`, increment `score`, update `#score` text. If wrong: show `"Wrong. The answer was [correct answer]."`.
- Step 4 — Show the Next Question button after an answer is chosen. Set its `display` to `"block"`. Disable the answer buttons so the user cannot change their answer.
- Step 5 — Wire up the Next Question button. When clicked, load Q2. After Q2 is answered, show a final "Quiz complete! You scored X / 2." message in `#feedback` and hide the Next Question button.
- Step 6 — Test your quiz end-to-end: answer both questions correctly, then both incorrectly, then mixed. Check that the score is always right.
- Step 7 — Add at least three comments explaining what key sections of your code do.

---

## Success Criteria

- checklist: Success Criteria
- File is named `quiz-app.html` and opens in a browser without errors
- At least two questions are displayed one at a time
- All four answer buttons show the correct option text for the current question
- Clicking correct answer shows "Correct! ✓" and increments the score
- Clicking wrong answer shows the correct answer in the feedback
- Score counter in `#score` updates correctly throughout
- Answer buttons are disabled after selection (can't change answer)
- Next Question button appears after answering and loads the next question
- A final "Quiz complete!" message appears after the last question
- At least three `//` comments in the code

---

- flow-accordion: Stretch Levels

###### Base — Required for everyone
Build the quiz exactly as described: two trivia questions on your chosen topic, four buttons, correct/wrong feedback, score counter, Next Question button. Everything works end-to-end.

###### Intermediate — More challenge
Add a third question. After the quiz ends, show a letter grade based on score: "A — Quiz Master!" for 3/3, "B — Nice Work!" for 2/3, and "C — Keep Studying!" for 1 or less. Use `if/else if/else`. Also give your quiz a proper title in the `<h1>` that describes the topic (e.g. "Animal Kingdom Trivia" or "Premier League Quiz").

###### Advanced — Push yourself
Style your quiz to look polished: after an answer is chosen, turn the correct answer button green and any wrong button clicked red. Use `.style.backgroundColor`. Display the question number and total ("Question 2 of 3") in a `<p id="question-counter">`. Reset button colors when loading the next question. Also add a topic image or emoji banner at the top using `document.getElementById("banner").textContent`.

---

{{include:session-footer}}

{{include:completion-checklist}}
