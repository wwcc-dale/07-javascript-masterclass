---
name: "Assignment: Scope and Closures Explorer"
published: false
points_possible: 100
grading_type: points
submission_types:
  - online_upload
allowed_extensions:
  - html
  - js
  - txt
due_at: null
outcomes:
  - 02-OOP
topics:
  - scope
  - closures
  - hoisting
---

[lead]Scope and closures become real when you write code that proves them. In this assignment you will build three working examples — one for block scope, one for variable shadowing, and one for a closure — and add comments that explain what is happening and why.

# Assignment: Scope and Closures Explorer

In this assignment you will write three separate JavaScript examples that demonstrate your understanding of scope and closures. Each example includes comments that explain the behavior — this shows that you understand what is happening, not just that it runs.

- stats
- 100 | Points | success
- online_upload | Submission | accent

---

## Why This Matters

Scope bugs are some of the most common and confusing bugs in JavaScript. Knowing exactly where a variable lives helps you avoid them and fix them faster. Closures appear in almost every JavaScript library and framework. Understanding them makes you a much stronger developer.

---

## Skills You Need

Before you start, make sure you can answer these from Session 14:

- What is the difference between global scope and block scope?
- What happens when a variable in an inner scope has the same name as one in an outer scope?
- What is a closure? How does an inner function "remember" a variable?
- What does `let`/`const` versus `var` have to do with block scope?

If any of these are unclear, re-read the Key Concepts section of the Session 14 page.

---

## What You Will Build

You will create a file called `scope-closures.html` with three distinct sections in the `<script>` tag:

1. **Example 1 — Global vs. Block Scope:** Show that `let` is block-scoped but `var` leaks out of blocks
2. **Example 2 — Variable Shadowing:** Show that an inner variable with the same name hides the outer one
3. **Example 3 — Closure:** Create a private counter using a closure, with `increment` and `reset` functions

---

## Step-by-Step Instructions

- steps: Step-by-Step Instructions
- Step 1 — Create `scope-closures.html` using the HTML skeleton below.
- Step 2 — **Example 1 (Global vs. Block Scope):** Declare a `const` variable called `globalMessage` outside any block and log it. Then open an `if (true)` block and inside it, declare a `let` variable called `blockMessage`. Log `blockMessage` from inside the block. After the block closes, try to reference `blockMessage` in a `try...catch` so you can demonstrate it is out of scope without crashing the page. Also declare a `var` variable inside the block and log it from outside the block to show it leaks. Add a comment above each section explaining what you expect to happen and why.
- Step 3 — **Example 2 (Variable Shadowing):** Declare a `const` called `animal` with the value `"cat"` in the outer scope. Write a function called `showAnimal()` that declares its own `const animal = "dog"` inside it, then logs `animal`. Call `showAnimal()` and then log the outer `animal` too. Add a comment explaining what shadowing means.
- Step 4 — **Example 3 (Closure):** Write a function called `makeCounter()` that declares a `let count = 0` inside it, and returns an object with two methods: `increment()` (adds 1 to count and returns the new value) and `reset()` (sets count back to 0 and returns 0). Call `makeCounter()` to create a counter, call `increment()` three times, log the value, call `reset()`, and log again. Add a comment explaining how the closure works — why does `count` still exist after `makeCounter()` has finished?
- Step 5 — Save the file, open it in a browser, open the console, and check all output is correct.
- Step 6 — Upload `scope-closures.html` to Canvas.

**HTML skeleton:**

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Scope and Closures</title>
</head>
<body>
  <h1>Scope and Closures</h1>
  <p>Open the console to see the output.</p>

  <script>
    // ===== Example 1: Global vs. Block Scope =====


    // ===== Example 2: Variable Shadowing =====


    // ===== Example 3: Closure =====

  </script>
</body>
</html>
```

---

## Success Criteria

- checklist: Success Criteria
- The file is named `scope-closures.html` and opens in a browser without errors
- Example 1 demonstrates `const` in global scope and `let` in block scope, with `var` leaking correctly
- A `try...catch` or labeled comment shows `blockMessage` is not accessible outside its block
- Example 2 shows a function with a shadowed variable; both the inner and outer values are logged correctly
- Example 3 defines a `makeCounter()` function that returns an object with `increment()` and `reset()` methods
- Calling `increment()` three times produces 1, 2, 3 and `reset()` returns 0
- Each example has comments explaining the scoping behavior
- Code is neatly organized with section headers and is easy to read

---

## Stretch Levels

- accordion: Stretch Levels
- Base — Required for everyone
  - Complete all three examples with correct behavior and comments as described.
- Intermediate — More challenge
  - Add a fourth example demonstrating hoisting. Create a `var` variable and log it **before** its declaration line — this will print `undefined` because `var` declarations are hoisted to the top of their scope (but not the value). Then add a `var`-declared function expression and a regular function declaration, and demonstrate that the function declaration is also hoisted (can be called before the line it is written). Add a comment block explaining the difference between how `var` and `let`/`const` are hoisted — mention that `let`/`const` also hoist but are in the Temporal Dead Zone (TDZ) until their declaration line, meaning accessing them early would cause a ReferenceError (do not attempt to trigger this — just explain it in the comment).
- Advanced — Push yourself
  - Extend your closure counter from Example 3 to also support a `decrement()` method, a `getCount()` method, and a minimum value of 0 (decrement should not go below 0). Then create two separate counters using `makeCounter()` and show that their `count` variables are completely independent — incrementing one does not affect the other. Log both counters' values after several calls to prove this.

{{include:session-footer}}

{{include:completion-checklist}}
