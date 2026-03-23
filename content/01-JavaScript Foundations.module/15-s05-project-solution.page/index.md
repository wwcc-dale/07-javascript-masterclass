---
name: "Solution: Project Part 1 — Hello, Quiz!"
published: false
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

# Instructor Solution: Project Part 1 — Hello, Quiz!

> alert: warning
>
> This page is for instructor reference only. Keep unpublished until after the assignment deadline.

---

## Student Hint

> alert: tip
>
> Start by just getting the question text and buttons to appear on the page — forget the logic for now. Once you can see the question, then wire up `onclick` for each button. Check the answer inside the click handler using `if/else`. After that, tackle the score counter and Next button. Build it one piece at a time.

---

## Full Solution

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
  <p id="question-counter">Question 1 of 2</p>
  <p id="question-text">Loading...</p>

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
    // --- Question data (trivia — students use their own topic) ---
    // Each question: [text, optionA, optionB, optionC, optionD, correctLetter]
    const q1 = ["Which animal is the fastest land mammal?",
                "Lion", "Cheetah", "Greyhound", "Pronghorn", "B"];
    const q2 = ["What is the capital of Japan?",
                "Beijing", "Seoul", "Tokyo", "Bangkok", "C"];

    const allQuestions = [q1, q2];
    let currentQuestion = 0;
    let score = 0;

    // --- Load a question into the DOM ---
    function loadQuestion(index) {
      const q = allQuestions[index];
      document.getElementById("question-counter").textContent =
        "Question " + (index + 1) + " of " + allQuestions.length;
      document.getElementById("question-text").textContent = q[0];
      document.getElementById("btn-a").textContent = "A: " + q[1];
      document.getElementById("btn-b").textContent = "B: " + q[2];
      document.getElementById("btn-c").textContent = "C: " + q[3];
      document.getElementById("btn-d").textContent = "D: " + q[4];
      document.getElementById("feedback").textContent = "";
      document.getElementById("next-btn").style.display = "none";
      // Re-enable all buttons
      enableButtons(true);
    }

    // --- Check the chosen answer ---
    function checkAnswer(chosen) {
      const correct = allQuestions[currentQuestion][5];
      const feedback = document.getElementById("feedback");

      if (chosen === correct) {
        score++;
        feedback.textContent = "Correct! ✓";
        feedback.style.color = "green";
      } else {
        feedback.textContent = "Wrong. The answer was " + correct + ".";
        feedback.style.color = "red";
      }

      document.getElementById("score").textContent = "Score: " + score;
      enableButtons(false);   // disable after answering
      document.getElementById("next-btn").style.display = "block";
    }

    // --- Enable or disable all answer buttons ---
    function enableButtons(enabled) {
      ["btn-a", "btn-b", "btn-c", "btn-d"].forEach(id => {
        document.getElementById(id).disabled = !enabled;
      });
    }

    // --- Wire up answer buttons ---
    document.getElementById("btn-a").onclick = () => checkAnswer("A");
    document.getElementById("btn-b").onclick = () => checkAnswer("B");
    document.getElementById("btn-c").onclick = () => checkAnswer("C");
    document.getElementById("btn-d").onclick = () => checkAnswer("D");

    // --- Next button ---
    document.getElementById("next-btn").onclick = function() {
      currentQuestion++;
      if (currentQuestion < allQuestions.length) {
        loadQuestion(currentQuestion);
      } else {
        // Quiz complete
        document.getElementById("question-text").textContent =
          "Quiz complete! You scored " + score + " / " + allQuestions.length + ".";
        document.getElementById("answer-buttons").style.display = "none";
        document.getElementById("next-btn").style.display = "none";
        document.getElementById("feedback").textContent = "";
      }
    };

    // --- Start ---
    loadQuestion(0);
  </script>
</body>
</html>
```

---

## Instructor Notes

- **Core requirements:** Two questions displayed one at a time, correct/wrong feedback, score counter increments only on correct answers, buttons disabled after answering, Next button moves to Q2, final "Quiz complete!" message appears.
- **Common mistake:** Putting the answer check logic directly inline rather than in a function — this leads to four near-identical click handlers. The solution above uses one `checkAnswer(chosen)` function, which is the right pattern.
- **Common mistake:** Not disabling buttons after the answer — students then click again and score goes up multiple times. Verify `disabled = true` is set.
- **Common mistake:** Forgetting to re-enable buttons when loading the next question.
- **Intermediate stretch:** A third question + letter grade using `if/else if/else`. Look for the ternary or `if/else` grading logic and correct use of score/total ratio.
- **Advanced stretch:** Button color changes (green for correct button, red for wrong buttons after answer). Requires setting `style.backgroundColor` on the clicked button and the correct button. Also a question counter `<p>` element. Reset colors by setting `style.backgroundColor = ""` on all buttons during `loadQuestion()`.
