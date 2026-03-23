---
indent: 2
name: "Solution: Project Part 4 — Timed Quiz"
published: false
outcomes:
  - 04-MOD
topics:
  - callbacks
  - timers
  - promises
  - async-await
  - built-in-objects
  - dom
---

# Instructor Solution: Project Part 4 — Timed Quiz

> alert: warning
>
> This page is for instructor reference only. Keep unpublished until after the assignment deadline.

---

## Student Hint

> alert: tip
>
> Add the timer last — get everything else from Credit 3 still working first. Then add `startTimer()` and `stopTimer()` calls at the right places. A common mistake is calling `startTimer()` twice (both at load and at next-question). Use `stopTimer()` defensively at the start of both `checkAnswer()` and `timeExpired()` to prevent double-timers.

---

## Key New Code (additions to Credit 3 solution)

```javascript
// --- Timer state ---
let timerId = null;
let timeLeft = 15;
const questionTimes = new Map();  // index -> seconds taken
let questionStartTime = 0;
let quizStartTime = 0;

// --- Timer functions ---
function startTimer() {
  timeLeft = 15;
  const timerEl = document.getElementById("timer");
  timerEl.textContent = "Time: " + timeLeft;
  timerEl.style.color = "black";
  questionStartTime = Date.now();

  timerId = setInterval(() => {
    timeLeft--;
    timerEl.textContent = "Time: " + timeLeft;
    if (timeLeft <= 5) timerEl.style.color = "red";
    if (timeLeft <= 0) {
      stopTimer();
      timeExpired();
    }
  }, 1000);
}

function stopTimer() {
  clearInterval(timerId);
  timerId = null;
  // Record time taken for this question
  const taken = Math.round((Date.now() - questionStartTime) / 1000);
  const idx = quiz.questions.indexOf(quiz.currentQuestion);
  if (idx >= 0) questionTimes.set(idx, taken);
}

function timeExpired() {
  // Force a wrong answer
  const feedback = document.getElementById("feedback");
  feedback.textContent = "Time's up! The answer was " + quiz.currentQuestion.answer + ".";
  feedback.style.color = "orange";
  quiz.checkAnswer("");   // empty string = always wrong
  document.getElementById("score").textContent = "Score: " + quiz.score;
  enableButtons(false);
  // Auto-advance after 1.5s
  setTimeout(() => {
    if (quiz.isFinished) showResults();
    else { loadQuestion(); startTimer(); }
  }, 1500);
}

// --- Updated checkAnswer to stop timer and add delay ---
function checkAnswer(chosen) {
  stopTimer();
  const correct = quiz.checkAnswer(chosen);
  const feedback = document.getElementById("feedback");
  feedback.textContent = correct ? "Correct! ✓" : "Wrong.";
  feedback.style.color = correct ? "green" : "red";
  document.getElementById("score").textContent = "Score: " + quiz.score;
  enableButtons(false);
  // Delay before next question
  nextWithDelay();
}

async function nextWithDelay() {
  document.getElementById("next-btn").style.display = "none";
  await new Promise(resolve => setTimeout(resolve, 1000));
  if (quiz.isFinished) showResults();
  else { loadQuestion(); startTimer(); }
}

// --- Updated loadQuestion: call startTimer() at end ---
// (same as Credit 3, just add startTimer() at the end)

// --- Updated showResults: add time stats ---
function showResults() {
  const totalTime = Math.round((Date.now() - quizStartTime) / 1000);
  const timeValues = [...questionTimes.values()];
  const avgTime = timeValues.length
    ? (timeValues.reduce((a, b) => a + b, 0) / timeValues.length).toFixed(1)
    : "N/A";

  // Find fastest question
  let fastestIdx = -1, fastestTime = Infinity;
  questionTimes.forEach((t, idx) => {
    if (t < fastestTime) { fastestTime = t; fastestIdx = idx; }
  });

  let html = `Score: ${quiz.score} / ${quiz.total} (${quiz.percentage()}%)<br>
    Total time: ${totalTime}s | Avg per question: ${avgTime}s<br>`;
  if (fastestIdx >= 0) {
    html += `Fastest: "${quiz.questions[fastestIdx].text}" (${fastestTime}s)<br>`;
  }

  const missed = quiz.missed;
  if (missed.length > 0) {
    html += "<br><strong>Missed:</strong><ul>";
    missed.forEach(q => { html += "<li>" + q + "</li>"; });
    html += "</ul>";
  }

  document.getElementById("results").innerHTML = html;
  document.getElementById("timer").textContent = "";
  document.getElementById("question-counter").textContent = "Quiz Complete!";
  document.getElementById("question-text").textContent = "";
  document.getElementById("answer-buttons").style.display = "none";
  document.getElementById("play-again-btn").style.display = "block";
}

// --- Start quiz ---
quizStartTime = Date.now();
loadQuestion();
startTimer();
```

---

## Instructor Notes

- **Core requirements:** `setInterval` countdown from 15 visible in DOM, `clearInterval` called in `stopTimer()`, `timeExpired()` fires at 0 and marks wrong, `async/await` + `setTimeout` for the 1-second delay, `Date.now()` for both question and total timing, `Map` used for per-question times, red timer at ≤5 seconds, all Credit 3 features preserved.
- **Common mistake:** Double timers — student calls `startTimer()` in both `loadQuestion()` and the Next button handler. Fix: only call it in `loadQuestion()`.
- **Common mistake:** Not clearing the old `timerId` before starting a new one — this causes multiple overlapping intervals. `stopTimer()` must always call `clearInterval(timerId)`.
- **Common mistake:** `quiz.checkAnswer("")` in `timeExpired()` but forgetting it increments the index — the auto-advance then skips a question. This is correct behavior; make sure students understand `checkAnswer` increments `#index`.
- **Intermediate stretch:** `<div>` progress bar with `style.width` changing each tick. Color change from green → orange → red (use two thresholds, e.g. ≤10 → orange, ≤5 → red).
- **Advanced stretch:** `localStorage.setItem("quizScores", JSON.stringify(...))` on results, read back with `JSON.parse(localStorage.getItem(...) || "[]")`. `Set` used to detect duplicate player names (keep highest score). Leaderboard rendered on page load.
