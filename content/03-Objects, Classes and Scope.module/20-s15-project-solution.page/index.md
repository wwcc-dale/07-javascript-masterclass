---
indent: 2
name: "Solution: Project Part 3 — Smart Quiz Engine"
published: false
outcomes:
  - 02-OOP
topics:
  - objects
  - classes
  - scope
  - closures
  - dom
---

# Instructor Solution: Project Part 3 — Smart Quiz Engine

> alert: warning
>
> This page is for instructor reference only. Keep unpublished until after the assignment deadline.

---

## Student Hint

> alert: tip
>
> Copy the `Quiz` class from the assignment page exactly as given and get it working first. Then, one by one, replace your old `loadQuestion()`, `checkAnswer()`, and `showResults()` functions to use `quiz.currentQuestion`, `quiz.checkAnswer()`, etc. Test after each change. Do not try to rewrite everything at once.

---

## Full Solution (Core Logic)

New `questions` array format and the `Quiz` class, plus the updated glue functions:

```javascript
// --- Question bank (object format) ---
const questions = [
  { text: "What country has the most natural lakes?", options: { A: "Russia", B: "Canada", C: "USA", D: "Brazil" }, answer: "B", category: "geography" },
  { text: "Which ocean is the largest?", options: { A: "Atlantic", B: "Indian", C: "Arctic", D: "Pacific" }, answer: "D", category: "geography" },
  { text: "What is the capital of Australia?", options: { A: "Sydney", B: "Melbourne", C: "Canberra", D: "Brisbane" }, answer: "C", category: "geography" },
  { text: "What is the hardest natural substance on Earth?", options: { A: "Gold", B: "Iron", C: "Diamond", D: "Quartz" }, answer: "C", category: "science" },
  { text: "Which planet has the most moons?", options: { A: "Jupiter", B: "Saturn", C: "Uranus", D: "Neptune" }, answer: "B", category: "science" },
  { text: "How many bones does an adult human body have?", options: { A: "196", B: "206", C: "216", D: "226" }, answer: "B", category: "science" },
  { text: "What is the smallest country in the world?", options: { A: "Monaco", B: "Liechtenstein", C: "Vatican City", D: "San Marino" }, answer: "C", category: "geography" },
  { text: "Which element has the chemical symbol Au?", options: { A: "Silver", B: "Aluminum", C: "Gold", D: "Argon" }, answer: "C", category: "science" },
  { text: "How many sides does a dodecagon have?", options: { A: "10", B: "11", C: "12", D: "13" }, answer: "C", category: "math" },
  { text: "What is the fastest land animal?", options: { A: "Lion", B: "Cheetah", C: "Greyhound", D: "Pronghorn" }, answer: "B", category: "animals" }
];

// --- Quiz class ---
class Quiz {
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

  reset() {
    this.#score = 0;
    this.#index = 0;
    this.#missed = [];
    this.questions = [...questions].sort(() => Math.random() - 0.5);
  }
}

// --- Instantiate ---
let quiz = new Quiz(questions);

// --- Load question ---
function loadQuestion() {
  const { text, options } = quiz.currentQuestion;  // destructuring
  document.getElementById("question-counter").textContent =
    "Question " + (quiz.questions.indexOf(quiz.currentQuestion) + 1) + " of " + quiz.total;
  document.getElementById("question-text").textContent = text;
  document.getElementById("btn-a").textContent = "A: " + options.A;
  document.getElementById("btn-b").textContent = "B: " + options.B;
  document.getElementById("btn-c").textContent = "C: " + options.C;
  document.getElementById("btn-d").textContent = "D: " + options.D;
  document.getElementById("feedback").textContent = "";
  document.getElementById("next-btn").style.display = "none";
  enableButtons(true);
}

// --- Check answer ---
function checkAnswer(chosen) {
  const correct = quiz.checkAnswer(chosen);  // returns true/false
  const feedback = document.getElementById("feedback");
  feedback.textContent = correct ? "Correct! ✓" : "Wrong.";
  feedback.style.color = correct ? "green" : "red";
  document.getElementById("score").textContent = "Score: " + quiz.score;
  enableButtons(false);
  document.getElementById("next-btn").style.display = "block";
}

// --- Show results ---
function showResults() {
  let html = `Score: ${quiz.score} / ${quiz.total} (${quiz.percentage()}%)<br><br>`;
  const missed = quiz.missed;
  if (missed.length > 0) {
    html += "<strong>Missed:</strong><ul>";
    missed.forEach(q => { html += "<li>" + q + "</li>"; });
    html += "</ul>";
  } else {
    html += "Perfect score!";
  }
  document.getElementById("results").innerHTML = html;
  document.getElementById("question-counter").textContent = "Quiz Complete!";
  document.getElementById("question-text").textContent = "";
  document.getElementById("answer-buttons").style.display = "none";
  document.getElementById("next-btn").style.display = "none";
  document.getElementById("play-again-btn").style.display = "block";
}

function enableButtons(on) {
  ["btn-a","btn-b","btn-c","btn-d"].forEach(id => {
    document.getElementById(id).disabled = !on;
  });
  document.getElementById("answer-buttons").style.display = on ? "block" : "none";
}

// --- Wire up ---
document.getElementById("btn-a").onclick = () => checkAnswer("A");
document.getElementById("btn-b").onclick = () => checkAnswer("B");
document.getElementById("btn-c").onclick = () => checkAnswer("C");
document.getElementById("btn-d").onclick = () => checkAnswer("D");

document.getElementById("next-btn").onclick = function() {
  if (quiz.isFinished) showResults();
  else loadQuestion();
};

document.getElementById("play-again-btn").onclick = function() {
  quiz.reset();
  document.getElementById("results").textContent = "";
  document.getElementById("answer-buttons").style.display = "block";
  document.getElementById("play-again-btn").style.display = "none";
  loadQuestion();
};

loadQuestion();
```

---

## Instructor Notes

- **Core requirements:** questions as objects with `text`, `options`, `answer`, `category`. `Quiz` class with private `#score`, `#index`, `#missed`. `checkAnswer()` returns boolean. `percentage()` uses `toFixed(1)`. Destructuring used in `loadQuestion()`. `quiz.reset()` called on Play Again.
- **Verifying private fields:** ask students to open the console (F12) and type `quiz.#score` — it should give a SyntaxError. This confirms the private field is working.
- **Common mistake:** Using `quiz.score++` instead of relying on `quiz.checkAnswer()` — the private field prevents direct mutation which is the point of the exercise.
- **Common mistake:** Destructuring `const { text, options }` but then using `q.options.A` instead of `options.A` inside the same block — show how destructuring creates local variable aliases.
- **Intermediate stretch:** Look for `Quiz.byCategory(questions, cat)` as a static method, a `<select>` dropdown, and `new Quiz(Quiz.byCategory(questions, chosen))`.
- **Advanced stretch:** `makeLeaderboard()` closure returning an object with `add`, `top`, `clear` methods. The internal array is not accessible from outside (verify in console). Name input form before quiz starts.
