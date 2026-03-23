---
indent: 2
name: "Solution: Project Part 5 — The Complete App"
published: false
outcomes:
  - 04-MOD
topics:
  - error-handling
  - fetch
  - es-modules
  - dom
---

# Instructor Solution: Project Part 5 — The Complete App

> alert: warning
>
> This page is for instructor reference only. Keep unpublished until after the assignment deadline.

---

## Student Hint

> alert: tip
>
> The most common problem is the browser blocking `fetch()` on local files due to CORS restrictions. Students must open the file through a local server — not by double-clicking `quiz-app.html`. In VS Code, the Live Server extension works. From the terminal: `python3 -m http.server 8000` then open `http://localhost:8000`. Make sure students know this before they start.

---

## File Structure

```
quiz-app/
├── quiz-app.html
├── quiz.js
├── loader.js
└── questions.json
```

---

## loader.js

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

## quiz.js

```javascript
// quiz.js
export class Quiz {
  #score = 0;
  #index = 0;
  #missed = [];

  constructor(qs) {
    this.questions = [...qs].sort(() => Math.random() - 0.5);
    this.total = this.questions.length;
  }

  get currentQuestion() { return this.questions[this.#index]; }
  get isFinished() { return this.#index >= this.total; }
  get score() { return this.#score; }
  get missed() { return [...this.#missed]; }

  checkAnswer(chosen) {
    const { answer, text } = this.currentQuestion;
    const correct = chosen === answer;
    if (correct) this.#score++;
    else this.#missed.push(text);
    this.#index++;
    return correct;
  }

  percentage() {
    return ((this.#score / this.total) * 100).toFixed(1);
  }

  reset(allQuestions) {
    this.#score = 0;
    this.#index = 0;
    this.#missed = [];
    this.questions = [...allQuestions].sort(() => Math.random() - 0.5);
    this.total = this.questions.length;
  }
}
```

---

## quiz-app.html (script section)

```html
<script type="module">
  import { loadQuestions } from "./loader.js";
  import { Quiz } from "./quiz.js";

  let quiz = null;
  let allQuestions = [];
  let timerId = null;
  let timeLeft = 15;
  const questionTimes = new Map();
  let questionStartTime = 0;
  let quizStartTime = 0;

  function showStatus(msg) {
    document.getElementById("status").textContent = msg;
    document.getElementById("status").style.color = "black";
  }
  function showError(msg) {
    document.getElementById("status").textContent = msg;
    document.getElementById("status").style.color = "red";
  }
  function hideStatus() {
    document.getElementById("status").textContent = "";
  }

  async function initQuiz() {
    showStatus("Loading questions...");
    try {
      allQuestions = await loadQuestions("./questions.json");
      hideStatus();
      quiz = new Quiz(allQuestions);
      quizStartTime = Date.now();
      loadQuestion();
      startTimer();
    } catch (e) {
      showError("Could not start quiz: " + e.message);
    } finally {
      // Could hide a loading spinner here if one existed
    }
  }

  function loadQuestion() {
    const { text, options } = quiz.currentQuestion;
    const idx = quiz.questions.indexOf(quiz.currentQuestion) + 1;
    document.getElementById("question-counter").textContent =
      "Question " + idx + " of " + quiz.total;
    document.getElementById("question-text").textContent = text;
    document.getElementById("btn-a").textContent = "A: " + options.A;
    document.getElementById("btn-b").textContent = "B: " + options.B;
    document.getElementById("btn-c").textContent = "C: " + options.C;
    document.getElementById("btn-d").textContent = "D: " + options.D;
    document.getElementById("feedback").textContent = "";
    document.getElementById("next-btn").style.display = "none";
    enableButtons(true);
    questionStartTime = Date.now();
  }

  function startTimer() {
    timeLeft = 15;
    const el = document.getElementById("timer");
    el.textContent = "Time: " + timeLeft;
    el.style.color = "black";
    timerId = setInterval(() => {
      timeLeft--;
      el.textContent = "Time: " + timeLeft;
      if (timeLeft <= 5) el.style.color = "red";
      if (timeLeft <= 0) { stopTimer(); timeExpired(); }
    }, 1000);
  }

  function stopTimer() {
    clearInterval(timerId);
    const taken = Math.round((Date.now() - questionStartTime) / 1000);
    const idx = quiz.questions.indexOf(quiz.currentQuestion);
    if (idx >= 0) questionTimes.set(idx, taken);
  }

  function timeExpired() {
    document.getElementById("feedback").textContent = "Time's up!";
    document.getElementById("feedback").style.color = "orange";
    quiz.checkAnswer("");
    enableButtons(false);
    setTimeout(() => {
      if (quiz.isFinished) showResults();
      else { loadQuestion(); startTimer(); }
    }, 1500);
  }

  function checkAnswer(chosen) {
    stopTimer();
    const correct = quiz.checkAnswer(chosen);
    const fb = document.getElementById("feedback");
    fb.textContent = correct ? "Correct! ✓" : "Wrong.";
    fb.style.color = correct ? "green" : "red";
    document.getElementById("score").textContent = "Score: " + quiz.score;
    enableButtons(false);
    nextWithDelay();
  }

  async function nextWithDelay() {
    await new Promise(r => setTimeout(r, 1000));
    if (quiz.isFinished) showResults();
    else { loadQuestion(); startTimer(); }
  }

  function showResults() {
    const total = Math.round((Date.now() - quizStartTime) / 1000);
    const vals = [...questionTimes.values()];
    const avg = vals.length ? (vals.reduce((a, b) => a + b, 0) / vals.length).toFixed(1) : "N/A";
    let html = `Score: ${quiz.score} / ${quiz.total} (${quiz.percentage()}%)<br>
      Total: ${total}s | Avg: ${avg}s/question<br>`;
    const missed = quiz.missed;
    if (missed.length) {
      html += "<br><strong>Missed:</strong><ul>" + missed.map(q => "<li>" + q + "</li>").join("") + "</ul>";
    }
    document.getElementById("results").innerHTML = html;
    document.getElementById("timer").textContent = "";
    document.getElementById("question-counter").textContent = "Quiz Complete!";
    document.getElementById("question-text").textContent = "";
    document.getElementById("answer-buttons").style.display = "none";
    document.getElementById("play-again-btn").style.display = "block";
  }

  function enableButtons(on) {
    ["btn-a","btn-b","btn-c","btn-d"].forEach(id => {
      document.getElementById(id).disabled = !on;
    });
    document.getElementById("answer-buttons").style.display = on ? "block" : "none";
  }

  document.getElementById("btn-a").onclick = () => checkAnswer("A");
  document.getElementById("btn-b").onclick = () => checkAnswer("B");
  document.getElementById("btn-c").onclick = () => checkAnswer("C");
  document.getElementById("btn-d").onclick = () => checkAnswer("D");

  document.getElementById("play-again-btn").onclick = function() {
    quiz.reset(allQuestions);
    questionTimes.clear();
    document.getElementById("results").textContent = "";
    document.getElementById("answer-buttons").style.display = "block";
    document.getElementById("play-again-btn").style.display = "none";
    quizStartTime = Date.now();
    loadQuestion();
    startTimer();
  };

  initQuiz();
</script>
```

---

## Instructor Notes

- **Running locally:** students MUST use a local server (`python3 -m http.server 8000` or VS Code Live Server) — `fetch()` fails with a CORS error on `file://` URLs. This is the most common issue. Post a note on the Canvas assignment page.
- **Core requirements:** `questions.json` valid, `loader.js` with `export async function loadQuestions`, `quiz.js` with `export class Quiz`, `type="module"` on script tag, error message shown in DOM (not just console), `validateQuestions` throws on missing fields, `finally` present.
- **Common mistake:** `import` paths without `./` — `import { Quiz } from "quiz.js"` fails; must be `"./quiz.js"`.
- **Common mistake:** Testing error handling by just looking at the console instead of verifying the `#status` element shows the message on screen.
- **Intermediate stretch:** Two separate JSON files, filename passed as argument to `loadQuestions()`, specific error if file missing.
- **Advanced stretch:** `stats.js` with `QuizStats` class, `localStorage` read/write with `try/catch`, history displayed on results screen.
