---
name: "Project: Build a Quiz App — Part 2: Multi-Question Quiz"
published: false
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
  - arrays
  - loops
  - functions
  - array-methods
  - dom
---

[lead]Your trivia quiz has two questions. Today you give it twenty. You will store all your questions in an array, loop through them automatically, use array methods to shuffle and score, and end with a proper results screen. By the end of this session your quiz is genuinely fun to play.

# Project: Build a Trivia Quiz App — Part 2: The Full Quiz

In Credit 1 you built the skeleton — two questions, four buttons, a score counter. It worked, but it was limited.

In Credit 2 you learned arrays, loops, functions, and higher-order array methods. Now you are going to use all of those to turn your trivia quiz into something real.

Open your `quiz-app.html` from Credit 1 and start upgrading. Keep your topic — just add a lot more questions about it.

- stats
- 100 | Points | success
- online_upload | Submission | accent

---

## Why This Matters

Almost every real app works with a list of data — users, products, messages, questions. Looping through that list, filtering it, sorting it, tracking progress through it — that is what your Credit 2 skills are for. This project is your chance to use all of them at once.

---

## Skills You Need

This project builds directly on Credit 1 and adds Credit 2 skills:

- Arrays: storing and accessing questions
- Loops: stepping through questions automatically
- Functions: reusable `loadQuestion()`, `checkAnswer()`, `showResults()`
- Array methods: `map()`, `filter()`, `forEach()`, `sort()`

---

## What You Will Build

Upgrade `quiz-app.html` into a full multi-question quiz:

1. **A question bank array** — at least 10 questions stored as arrays
2. **Automatic question progression** — the quiz moves through all questions
3. **Shuffle function** — questions appear in random order each time
4. **Results screen** — shows total score, percentage, and missed questions

---

## Question Format

Store each question as an array with 6 elements:

```javascript
const questions = [
  ["What country has the most natural lakes?", "Russia", "Canada", "USA", "Brazil", "B"],
  ["Which ocean is the largest?", "Atlantic", "Indian", "Arctic", "Pacific", "D"],
  ["What is the capital of Australia?", "Sydney", "Melbourne", "Canberra", "Brisbane", "C"],
  // ... more questions about YOUR topic
];
// Format: [questionText, optionA, optionB, optionC, optionD, correctLetter]
```

Write at least 10 questions about your trivia topic. If you need inspiration, think about:
- Facts you know well and want to test others on
- Things you had to look up yourself recently
- A topic you genuinely want people to learn about

The trivia content is yours — the JavaScript structure is what is being assessed.

---

## Functions to Write

- **`loadQuestion(index)`** — updates the DOM with that question's text and four options. Shows question counter (`"Question 3 of 10"`).
- **`checkAnswer(chosen)`** — compares chosen letter to correct answer. Updates feedback, score, disables buttons, shows Next button. Stores missed question texts.
- **`showResults()`** — called after the last question. Shows final score, percentage (`.toFixed(1)`), and list of missed questions.
- **`shuffleQuestions()`** — returns a shuffled copy: `[...questions].sort(() => Math.random() - 0.5)`.

---

## Step-by-Step Instructions

- steps: Step-by-Step Instructions
- Step 1 — Create your `questions` array with at least 10 questions in the format above.
- Step 2 — Declare at the top: `let currentIndex = 0`, `let score = 0`, `let missed = []`.
- Step 3 — Write `loadQuestion(index)`. Reads from `activeQuestions[index]` (shuffled copy) and updates the DOM including a question counter.
- Step 4 — Write `checkAnswer(chosen)`. Disables all buttons. If correct: increment score, update `#score`. If wrong: push the question text to `missed[]`. Show feedback. Show Next button.
- Step 5 — Wire up each button: `document.getElementById("btn-a").onclick = () => checkAnswer("A")` etc.
- Step 6 — Wire up the Next button: increment `currentIndex`. If more questions remain, call `loadQuestion(currentIndex)`. Otherwise call `showResults()`.
- Step 7 — Write `showResults()`. Show final score, percentage, and list any missed questions using `forEach()` to build an HTML string.
- Step 8 — Add a "Play Again" button in the results screen. When clicked, reset state variables, re-shuffle, and call `loadQuestion(0)`.
- Step 9 — Test: play through all questions, check results, check Play Again works.

---

## Success Criteria

- checklist: Success Criteria
- `questions` array contains at least 10 questions in the correct format
- `loadQuestion(index)` correctly displays any question by index
- Question counter shows current position and total (e.g., "Question 3 of 10")
- `checkAnswer()` correctly identifies right/wrong, updates score, disables buttons
- Missed questions are tracked in an array and shown in the results
- `showResults()` shows score, percentage (using `.toFixed()`), and missed question list
- Questions are shuffled each play using sort-based shuffle
- "Play Again" button resets and replays with a new shuffle
- Code uses named functions (not all inline), with at least 5 comments

---

## Stretch Levels

- accordion: Stretch Levels
- Base — Required for everyone
  - 10+ trivia questions on your chosen topic, automatic progression, score tracking, results screen showing missed questions, shuffle, Play Again.
- Intermediate — More challenge
  - Add a **difficulty filter**. Add a 7th element to each question: `"easy"` or `"hard"`. Add two buttons on a start screen: "Easy Mode" and "Hard Mode". Use `filter()` to pick the right questions. Show the selected difficulty in the heading. Write at least 5 questions at each level.
- Advanced — Push yourself
  - Add a **high score tracker**. Keep `const highScores = []`. After each quiz, push the score, sort descending, trim to 5 entries with `splice()`. Show the top scores on the results screen. Also show a fun **share message** using a template literal — e.g. `"I scored 8/10 on the Animal Kingdom Quiz! 🦁"` — so the player has something to screenshot and share.

{{include:session-footer}}

{{include:completion-checklist}}
