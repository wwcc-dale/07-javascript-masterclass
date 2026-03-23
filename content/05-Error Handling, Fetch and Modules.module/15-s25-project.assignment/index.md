---
name: "Project: Build a Quiz App — Part 5: The Complete App"
published: false
points_possible: 100
grading_type: points
submission_types:
  - online_upload
allowed_extensions:
  - html
  - js
  - json
due_at: null
outcomes:
  - 03-ELEM
topics:
  - error-handling
  - fetch
  - es-modules
  - dom
---

[lead]This is it. You have built a working, structured, timed trivia quiz over five credits. Now you take the final step that separates a hobby project from professional code: load your questions from a real data file, handle every failure gracefully, and split your code into clean modules. The result is an app you can genuinely be proud of.

# Project: Build a Trivia Quiz App — Part 5: The Complete App

Look at how far you have come.

Credit 1: One trivia question on screen, answer checking, a score counter.
Credit 2: A full question bank on your topic, shuffle, results with missed questions.
Credit 3: Questions as objects, Quiz class, private state — professional structure.
Credit 4: Countdown timer, async delays, time stats, a leaderboard.

Credit 5: You make it real. Your trivia questions live in a proper `questions.json` data file. They load via `fetch` when the page opens. Every failure is handled gracefully. Your code is split into clean ES modules. The result is an app you could actually deploy and share.

Open your `quiz-app.html` from Credit 4 and do the final upgrade.

- stats
- 100 | Points | success
- online_upload | Submission | accent

---

## Why This Matters

Every professional web app fetches data from somewhere. And every professional app handles errors — because real networks fail, real files have bad data, and real users do unexpected things. What you are building in this project is the core pattern behind every data-driven app you will ever work on.

---

## Skills You Need

This project builds on Credits 1–4 and adds Credit 5 skills:

- `fetch()`: loading local JSON data
- `async/await` with error handling: `try/catch` around fetch
- `throw` and custom error messages: validate data before using it
- ES Modules: `export` and `import` to split code into files
- `finally`: guaranteed cleanup after fetch

---

## What You Will Build

The final upgrade to `quiz-app.html`:

1. **A JSON question file** — move all questions into `questions.json`
2. **A fetch loader** — loads questions from the file asynchronously on startup
3. **Full error handling** — graceful messages for every failure mode
4. **ES module split** — quiz logic in `quiz.js`, question loader in `loader.js`
5. **Data validation** — check the loaded JSON before using it

---

## Step 1: Create questions.json

Create a file called `questions.json` in the same folder as your HTML. Move all your trivia questions into it:

```json
[
  {
    "text": "What country has the most natural lakes?",
    "options": { "A": "Russia", "B": "Canada", "C": "USA", "D": "Brazil" },
    "answer": "B",
    "category": "geography"
  },
  {
    "text": "Which ocean is the largest?",
    "options": { "A": "Atlantic", "B": "Indian", "C": "Arctic", "D": "Pacific" },
    "answer": "D",
    "category": "geography"
  }
]
```

Include all your questions (at least 10). Valid JSON requires double-quoted strings everywhere and no trailing commas. Test by opening `questions.json` directly in a browser — it should display cleanly.

---

## Step 2: Create loader.js

```javascript
// loader.js
export async function loadQuestions(url) {
  const res = await fetch(url);
  if (!res.ok) throw new Error("Could not load questions: HTTP " + res.status);
  const data = await res.json();
  validateQuestions(data);
  return data;
}

function validateQuestions(data) {
  if (!Array.isArray(data)) throw new TypeError("Questions must be an array");
  if (data.length === 0) throw new RangeError("Question file is empty");
  for (const q of data) {
    if (!q.text || !q.options || !q.answer) {
      throw new TypeError("Question missing required fields: " + JSON.stringify(q));
    }
  }
}
```

---

## Step 3: Create quiz.js

Move your `Quiz` class into `quiz.js` and export it:

```javascript
// quiz.js
export class Quiz {
  // ... your Quiz class from Credit 3/4
}
```

---

## Step 4: Update quiz-app.html

Change the script tag to use modules:

```html
<script type="module">
  import { loadQuestions } from "./loader.js";
  import { Quiz } from "./quiz.js";

  async function initQuiz() {
    showStatus("Loading questions...");
    try {
      const questions = await loadQuestions("./questions.json");
      hideStatus();
      const quiz = new Quiz(questions);
      startQuiz(quiz);
    } catch (e) {
      showError("Could not start quiz: " + e.message);
    }
  }

  function showStatus(msg) {
    document.getElementById("status").textContent = msg;
  }
  function hideStatus() {
    document.getElementById("status").textContent = "";
  }
  function showError(msg) {
    document.getElementById("status").textContent = msg;
    document.getElementById("status").style.color = "red";
  }

  initQuiz();
</script>
```

Add `<p id="status"></p>` near the top of your `<body>`.

---

## Step-by-Step Instructions

- steps: Step-by-Step Instructions
- Step 1 — Create `questions.json` with all your questions in valid JSON format. Test by opening it in the browser directly — it should display without errors.
- Step 2 — Create `loader.js` with the `loadQuestions` async function and `validateQuestions` function as shown above. Export `loadQuestions`.
- Step 3 — Create `quiz.js`. Move your `Quiz` class into it and add `export` before `class Quiz`. Move any helper functions (like shuffle) that the class needs into the same file.
- Step 4 — Update your `<script>` tag to `type="module"`. Import `loadQuestions` and `Quiz`. Write the `initQuiz()` async function.
- Step 5 — Add `<p id="status"></p>` to your HTML. Wire up `showStatus()`, `hideStatus()`, and `showError()`.
- Step 6 — Wrap the entire quiz startup in `try/catch/finally`. In the `finally` block, always hide any loading spinner (a nice touch: briefly show "Loading..." then hide it).
- Step 7 — Test the happy path: everything works normally.
- Step 8 — Test error handling: temporarily rename `questions.json` to something else and verify the error message appears on screen instead of crashing.
- Step 9 — Test validation: temporarily remove the `answer` field from one question in the JSON and verify the validation error appears.
- Step 10 — Final check: restore everything, play through the complete quiz from start to results. Verify all Credit 4 features (timer, leaderboard) still work.

---

## Success Criteria

- checklist: Success Criteria
- `questions.json` is valid JSON and contains at least 10 questions in the correct format
- `loader.js` exports an `async loadQuestions(url)` function
- `quiz.js` exports the `Quiz` class
- `quiz-app.html` uses `type="module"` and imports from both files
- Questions load successfully from the JSON file on startup
- A "Loading questions..." message is shown while fetching
- A clear error message appears on screen (not just in the console) if the file cannot be loaded
- `validateQuestions()` throws a useful error for missing fields — and this error is caught and displayed
- `finally` block is used for cleanup after the fetch
- All Credit 4 features (timer, delay, time stats, leaderboard) still work

---

## Stretch Levels

- accordion: Stretch Levels
- Base — Required for everyone
  - Questions load from `questions.json` via `fetch`. Three-file structure (`quiz-app.html`, `quiz.js`, `loader.js`). Full error handling displayed on screen. Validation catches missing fields. All Credit 4 features preserved.
- Intermediate — More challenge
  - Add **multiple question sets** as separate JSON files — e.g. `questions-easy.json` and `questions-hard.json`, or two different topic files (e.g. `questions-animals.json` and `questions-geography.json`). Add a start screen where the player picks which set to play. Pass the chosen filename to `loadQuestions()`. Handle the case where a chosen file is missing with a friendly on-screen error message.
- Advanced — Push yourself
  - Add a **statistics module**. Create `stats.js` that exports a `QuizStats` class. It stores all completed quiz sessions (score, total, time taken, date using `new Date().toLocaleDateString()`) in `localStorage` as JSON. Methods: `record(session)`, `allSessions()`, `average()` (average % across all plays), `best()` (highest-scoring session). Show a "Your History" section on the results screen. Handle `localStorage` being unavailable (some browsers block it) with a `try/catch` that silently skips saving — your app should never crash because of this.

{{include:session-footer}}

{{include:completion-checklist}}
