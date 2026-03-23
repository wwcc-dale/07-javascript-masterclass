---
name: "Project: Build a Quiz App — Part 4: Timed Quiz"
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
  - callbacks
  - timers
  - promises
  - async-await
  - built-in-objects
  - dom
---

[lead]You have a quiz. Now it needs pressure. A countdown timer, a leaderboard powered by Map and Set, a smooth "loading..." pause between questions — the quiz goes from functional to fun. This is where async skills make the difference.

# Project: Build a Quiz App — Part 4: Timed Quiz

Your quiz engine is solid. But there is no urgency. The user can sit on a question forever. Real quiz apps have timers — they create energy, they reward quick thinking, they make losing feel fair.

In Credit 4 you learned callbacks, timers, promises, async/await, and the built-in objects (Date, Map, Set, Math). Now you are going to wire those skills directly into your quiz.

Open your `quiz-app.html` from Credit 3 and start upgrading.

- stats
- 100 | Points | success
- online_upload | Submission | accent

---

## Why This Matters

Real-time UI updates — countdowns, animations, loading states — all depend on async patterns. Timers are the simplest version of this. If you can make a countdown work correctly, you understand the async event loop well enough to build anything.

---

## Skills You Need

This project builds on Credits 1–3 and adds Credit 4 skills:

- `setInterval` / `clearInterval`: countdown timer
- `setTimeout`: brief delay between questions for feedback
- `Promise` and `async/await`: simulate loading with a delay
- `Date.now()`: track total quiz time
- `Map`: store question statistics (time taken per question)
- `Set`: prevent duplicate entries in leaderboard names

---

## What You Will Build

Upgrade `quiz-app.html` with:

1. **A countdown timer** — 15 seconds per question. If time runs out, the question is marked wrong automatically.
2. **A question delay** — after answering, wait 1 second before loading the next question (so the user can read the feedback).
3. **Total time tracking** — record how long the whole quiz took using `Date.now()`.
4. **Per-question stats** — use a `Map` to record the time taken on each question.
5. **Results upgrade** — show total time, average time per question, and fastest/slowest questions.

---

## Timer Implementation

Add a timer display to your HTML:

```html
<p id="timer">Time: 15</p>
```

Then in your script, manage the timer like this:

```javascript
let timerId = null;
let timeLeft = 15;

function startTimer() {
  timeLeft = 15;
  document.getElementById("timer").textContent = "Time: " + timeLeft;
  timerId = setInterval(() => {
    timeLeft--;
    document.getElementById("timer").textContent = "Time: " + timeLeft;
    if (timeLeft <= 0) {
      clearInterval(timerId);
      timeExpired();   // auto-submit wrong when time runs out
    }
  }, 1000);
}

function stopTimer() {
  clearInterval(timerId);
}

function timeExpired() {
  // mark question wrong, show correct answer, move on
}
```

---

## Question Delay

After answering, pause briefly before loading the next question:

```javascript
async function nextWithDelay() {
  await new Promise(resolve => setTimeout(resolve, 1000));
  loadNextQuestion();
}
```

Call `nextWithDelay()` from your Next button handler instead of calling `loadQuestion()` directly.

---

## Tracking Stats with Map

```javascript
const questionTimes = new Map();  // key: question index, value: time taken (seconds)

// When a question loads:
const questionStartTime = Date.now();

// When answered:
const timeTaken = Math.round((Date.now() - questionStartTime) / 1000);
questionTimes.set(currentIndex, timeTaken);
```

On the results screen, use the Map to find:
- Average time: `[...questionTimes.values()].reduce((a, b) => a + b, 0) / questionTimes.size`
- Fastest question index: find the minimum value

---

## Step-by-Step Instructions

- steps: Step-by-Step Instructions
- Step 1 — Add `<p id="timer">Time: 15</p>` to your HTML, near the question area.
- Step 2 — Write `startTimer()` and `stopTimer()` as described above. Call `startTimer()` at the end of `loadQuestion()`. Call `stopTimer()` at the start of `checkAnswer()`.
- Step 3 — Write `timeExpired()`. It should: call `stopTimer()`, mark the question wrong (push to missed), increment index, then call `nextWithDelay()`.
- Step 4 — Write `nextWithDelay()` using `async/await` and `setTimeout`. It waits 1 second, then calls `loadQuestion()` or `showResults()` depending on whether the quiz is finished.
- Step 5 — Record `const quizStartTime = Date.now()` when the quiz begins. In `showResults()`, calculate total time: `Math.round((Date.now() - quizStartTime) / 1000)` seconds.
- Step 6 — Add `const questionTimes = new Map()`. In `checkAnswer()` and `timeExpired()`, record the time taken for that question using `Date.now()`.
- Step 7 — Upgrade `showResults()`: show total time, average time per question, and the text of the fastest-answered question (the one with the lowest value in the Map).
- Step 8 — Style the timer to turn red (using `style.color`) when `timeLeft <= 5`.
- Step 9 — Test: let the timer run out on one question, answer others quickly and slowly. Verify all stats are correct.

---

## Success Criteria

- checklist: Success Criteria
- Timer counts down from 15 for each question and displays in the DOM
- Timer stops when an answer is chosen
- `timeExpired()` fires at 0 and marks the question wrong with correct answer shown
- A 1-second delay between questions uses `async/await` + `setTimeout`
- Total quiz time is tracked using `Date.now()` and shown in results
- Per-question times stored in a `Map`
- Results screen shows total time, average time per question
- Timer turns red when 5 or fewer seconds remain
- All Credit 3 functionality (class, objects, private fields, categories) still works

---

## Stretch Levels

- accordion: Stretch Levels
- Base — Required for everyone
  - Countdown timer (auto-expire), question delay, total time tracking with Map, upgraded results screen showing time stats.
- Intermediate — More challenge
  - Add an **animated progress bar** below the timer. It starts full and shrinks each second. Use a `<div>` with a fixed-width container and change its `style.width` property each tick: `Math.round((timeLeft / 15) * 100) + "%"`. Change its color from green → orange → red as time decreases.
- Advanced — Push yourself
  - Add a **persistent leaderboard** using `localStorage`. After each quiz, save the top 10 scores as JSON: `localStorage.setItem("quizScores", JSON.stringify(scores))`. On page load, read them back with `JSON.parse(localStorage.getItem("quizScores") || "[]")`. Display the leaderboard before the quiz starts. Use a `Set` to ensure no duplicate player names (keep highest score if name already exists). The leaderboard should survive a page reload.

{{include:session-footer}}

{{include:completion-checklist}}
