---
name: "Project: Build a Quiz App — Part 3: Smart Quiz Engine"
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
  - objects
  - classes
  - scope
  - closures
  - dom
---

[lead]Your trivia quiz works and people are playing it. Now you are going to make the code behind it clean. Real-world JavaScript structures data as objects, uses classes for consistency, and uses closures to protect state. By the end of this credit your quiz engine looks like code a professional would be proud of — and the trivia is still just as fun.

# Project: Build a Trivia Quiz App — Part 3: Smart Quiz Engine

You have a working multi-question trivia quiz. But look at your code — the question data is a pile of arrays, the score is a loose variable in the global scope, and the logic is scattered everywhere.

In Credit 3 you learned objects, classes, scope, and closures. Now you are going to use those tools to refactor your quiz into a well-structured engine. The quiz will look and play exactly the same to the user. The code underneath will be far better.

Open your `quiz-app.html` from Credit 2 and start refactoring.

- stats
- 100 | Points | success
- online_upload | Submission | accent

---

## Why This Matters

Refactoring — improving code structure without changing what it does — is one of the most important skills a developer has. Every professional codebase goes through it constantly. This project gives you a real experience of taking working code and making it better.

---

## Skills You Need

This project builds on Credits 1 and 2 and adds Credit 3 skills:

- Objects: questions as structured data objects
- Classes: `Quiz` class to manage state and logic
- Destructuring: extracting question fields cleanly
- Closures: hiding quiz state from the global scope
- `this`: using class methods correctly

---

## What You Will Build

Refactor `quiz-app.html` so that:

1. **Each question is an object** with named properties
2. **A `Quiz` class** manages all quiz state (current index, score, missed questions)
3. **Class methods** handle loading, checking, and showing results
4. **Destructuring** is used when pulling question data into the DOM
5. The quiz behavior is **identical** to Credit 2 — same gameplay, cleaner code

---

## New Question Format

Replace your array-of-arrays with an **array of objects**. Keep your existing trivia questions — just convert them to this shape:

```javascript
const questions = [
  {
    text: "What country has the most natural lakes?",
    options: { A: "Russia", B: "Canada", C: "USA", D: "Brazil" },
    answer: "B",
    category: "geography"
  },
  {
    text: "Which ocean is the largest?",
    options: { A: "Atlantic", B: "Indian", C: "Arctic", D: "Pacific" },
    answer: "D",
    category: "geography"
  },
  // ...all your questions from Credit 2
];
```

---

## The Quiz Class

Write a `Quiz` class with:

```javascript
class Quiz {
  #score = 0;          // private — outside code cannot change it
  #index = 0;          // current question index
  #missed = [];        // missed question texts

  constructor(questions) {
    this.questions = [...questions].sort(() => Math.random() - 0.5);
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
```

---

## Step-by-Step Instructions

- steps: Step-by-Step Instructions
- Step 1 — Convert your questions array to the new object format with `text`, `options`, `answer`, and `category` fields.
- Step 2 — Copy the `Quiz` class above into your script. Read through it carefully — make sure you understand what each part does.
- Step 3 — Create one instance: `const quiz = new Quiz(questions);`
- Step 4 — Rewrite `loadQuestion()`. Use destructuring to pull fields: `const { text, options } = quiz.currentQuestion;`. Then set DOM elements using those variables.
- Step 5 — Rewrite your answer button handlers to call `quiz.checkAnswer(letter)`. Use the return value (true/false) to set the feedback text.
- Step 6 — Rewrite the Next button handler. Check `quiz.isFinished` — if true, call `showResults()`, if false call `loadQuestion()`.
- Step 7 — Rewrite `showResults()`. Use `quiz.score`, `quiz.total`, `quiz.percentage()`, and `quiz.missed` to build the results display.
- Step 8 — Rewrite the "Play Again" button to call `quiz.reset()` then `loadQuestion()`.
- Step 9 — Test: play through the whole quiz. Verify score, percentage, and missed questions are all correct.
- Step 10 — Verify: try accessing `quiz.#score` from the console (F12). It should throw an error — the private field is working.

---

## Success Criteria

- checklist: Success Criteria
- All questions use the object format with `text`, `options`, `answer`, and `category`
- `Quiz` class is defined with at least the methods and private fields listed
- `quiz.checkAnswer()` correctly returns true/false and tracks missed questions
- `quiz.percentage()` returns a percentage string with one decimal place
- `loadQuestion()` uses destructuring to extract question fields
- Answer buttons call `quiz.checkAnswer()` and use the return value for feedback
- `showResults()` uses `quiz.score`, `quiz.total`, `quiz.percentage()`, and `quiz.missed`
- Play Again calls `quiz.reset()`
- Private field `#score` cannot be accessed directly from outside the class (verify in console)
- At least 5 comments explaining key design decisions

---

## Stretch Levels

- accordion: Stretch Levels
- Base — Required for everyone
  - Refactor using the Question object format and Quiz class. All quiz functionality from Credit 2 is preserved. Private fields work correctly.
- Intermediate — More challenge
  - Add a **category filter** to the Quiz class. Add a static method `Quiz.byCategory(questions, cat)` that returns only questions matching the given `category`. Add a `<select>` dropdown above the quiz showing all available categories (plus "All"). When the quiz starts, pass the filtered set to `new Quiz(...)`. This works great if your topic has natural sub-categories — e.g. a movie quiz could have "Action", "Comedy", "Animation".
- Advanced — Push yourself
  - Implement a **leaderboard** using a closure. Write a `makeLeaderboard()` function that returns an object with `add(name, score)`, `top(n)`, and `clear()` methods. The scores array is private inside the closure — nothing outside can access it directly. Add a name input form before the quiz starts. Show the top 3 on the results screen with a trophy emoji: 🥇 🥈 🥉. Display the player's name and score in the final "Quiz complete" message.

{{include:session-footer}}

{{include:completion-checklist}}
