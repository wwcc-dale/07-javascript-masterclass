---
name: "Solution: Project Part 2 — Multi-Question Quiz"
published: false
outcomes:
  - 03-ELEM
topics:
  - arrays
  - array-methods
  - functions
  - loops
  - dom
---

# Instructor Solution: Project Part 2 — Multi-Question Quiz

> alert: warning
>
> This page is for instructor reference only. Keep unpublished until after the assignment deadline.

---

## Student Hint

> alert: tip
>
> Start by building the `questions` array with just 3 questions to keep testing quick. Write `loadQuestion(index)` first and test it by calling `loadQuestion(0)` manually. Once that works, add `checkAnswer()`. Only add the shuffle and results screen once the core loop works.

---

## Full Solution (Core Logic)

The complete solution is an upgrade to the Credit 1 file. Below is the key JavaScript — the HTML structure stays the same as Credit 1 with a "Play Again" button added.

```javascript
// --- Question bank ---
// Format: [questionText, A, B, C, D, correctLetter]
const questions = [
  ["What does push() do to an array?", "Removes the last item", "Adds to the end", "Removes the first item", "Adds to the start", "B"],
  ["What does shift() return?", "The last item", "Nothing", "The first item (and removes it)", "The array length", "C"],
  ["What does indexOf() return if the item is not found?", "0", "null", "-1", "false", "C"],
  ["What does Array.isArray([]) return?", "false", "undefined", "null", "true", "D"],
  ["Which method does NOT modify the original array?", "push()", "pop()", "splice()", "map()", "D"],
  ["What does .filter() return?", "The first matching item", "A new shorter array", "The index of matches", "true or false", "B"],
  ["What does .reduce() do?", "Removes duplicates", "Combines all items into one value", "Filters the array", "Sorts the array", "B"],
  ["What does for...of loop through?", "Object keys", "Array indices", "The values in an array", "A range of numbers", "C"],
  ["What is a recursive function?", "A function with no parameters", "A function that calls itself", "A function stored in an array", "An arrow function", "B"],
  ["What does a default parameter do?", "Prevents the function from running", "Sets a fallback value when no argument is given", "Declares a constant", "Returns undefined", "B"]
];

// --- State ---
let activeQuestions = [];
let currentIndex = 0;
let score = 0;
let missed = [];

// --- Shuffle (returns a new shuffled array) ---
function shuffleQuestions() {
  return [...questions].sort(() => Math.random() - 0.5);
}

// --- Load a question by index ---
function loadQuestion(index) {
  const q = activeQuestions[index];
  document.getElementById("question-counter").textContent =
    "Question " + (index + 1) + " of " + activeQuestions.length;
  document.getElementById("question-text").textContent = q[0];
  document.getElementById("btn-a").textContent = "A: " + q[1];
  document.getElementById("btn-b").textContent = "B: " + q[2];
  document.getElementById("btn-c").textContent = "C: " + q[3];
  document.getElementById("btn-d").textContent = "D: " + q[4];
  document.getElementById("feedback").textContent = "";
  document.getElementById("next-btn").style.display = "none";
  document.getElementById("play-again-btn").style.display = "none";
  document.getElementById("results").textContent = "";
  enableButtons(true);
}

// --- Check answer ---
function checkAnswer(chosen) {
  const q = activeQuestions[currentIndex];
  const correct = q[5];
  const feedback = document.getElementById("feedback");

  if (chosen === correct) {
    score++;
    feedback.textContent = "Correct! ✓";
    feedback.style.color = "green";
  } else {
    feedback.textContent = "Wrong. The answer was " + correct + ": " + q[correct.charCodeAt(0) - 65 + 1] + ".";
    feedback.style.color = "red";
    missed.push(q[0]);  // save missed question text
  }

  document.getElementById("score").textContent = "Score: " + score;
  enableButtons(false);
  document.getElementById("next-btn").style.display = "block";
}

// --- Show results screen ---
function showResults() {
  const total = activeQuestions.length;
  const pct = ((score / total) * 100).toFixed(1);

  let html = `<strong>Quiz complete!</strong><br>
    Score: ${score} / ${total} (${pct}%)<br><br>`;

  if (missed.length > 0) {
    html += "<strong>Review these questions:</strong><ul>";
    missed.forEach(q => { html += "<li>" + q + "</li>"; });
    html += "</ul>";
  } else {
    html += "Perfect score! Well done.";
  }

  document.getElementById("results").innerHTML = html;
  document.getElementById("question-text").textContent = "";
  document.getElementById("question-counter").textContent = "";
  document.getElementById("answer-buttons").style.display = "none";
  document.getElementById("next-btn").style.display = "none";
  document.getElementById("play-again-btn").style.display = "block";
}

// --- Enable/disable buttons ---
function enableButtons(enabled) {
  ["btn-a", "btn-b", "btn-c", "btn-d"].forEach(id => {
    document.getElementById(id).disabled = !enabled;
  });
  document.getElementById("answer-buttons").style.display = enabled ? "block" : "none";
}

// --- Wire up buttons ---
document.getElementById("btn-a").onclick = () => checkAnswer("A");
document.getElementById("btn-b").onclick = () => checkAnswer("B");
document.getElementById("btn-c").onclick = () => checkAnswer("C");
document.getElementById("btn-d").onclick = () => checkAnswer("D");

document.getElementById("next-btn").onclick = function() {
  currentIndex++;
  if (currentIndex < activeQuestions.length) {
    loadQuestion(currentIndex);
  } else {
    showResults();
  }
};

document.getElementById("play-again-btn").onclick = function() {
  currentIndex = 0;
  score = 0;
  missed = [];
  activeQuestions = shuffleQuestions();
  document.getElementById("answer-buttons").style.display = "block";
  loadQuestion(0);
};

// --- Start ---
activeQuestions = shuffleQuestions();
loadQuestion(0);
```

---

## Instructor Notes

- **Core requirements:** 10+ questions in array-of-arrays format, `loadQuestion(index)` uses the index to read from `activeQuestions`, `checkAnswer(chosen)` compares to `q[5]`, `missed` array accumulates wrong question texts, `showResults()` uses `forEach` to build HTML list, shuffle uses spread + sort, Play Again resets all state.
- **Common mistake:** Calling `questions` directly instead of `activeQuestions` (the shuffled copy) — questions then always appear in the same order.
- **Common mistake:** Not resetting `missed = []` on Play Again — the second play shows previous session's misses.
- **Common mistake:** Using `innerHTML` to show results but forgetting to clear it before showing — results stack on repeated plays.
- **Intermediate stretch:** Look for a 7th element in each question array (difficulty string), two filter buttons pre-quiz, and correct use of `filter()` to select the question set.
- **Advanced stretch:** `highScores` array with push + sort descending + `splice(5)` to keep only top 5. `Date.now()` used for timing with subtraction to get elapsed seconds.
