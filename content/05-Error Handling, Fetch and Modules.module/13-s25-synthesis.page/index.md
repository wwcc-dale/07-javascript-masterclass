---
name: "Session 25: Credit 5 Synthesis"
published: false
outcomes:
  - 04-MOD
topics:
  - error-handling
  - fetch-api
  - es-modules
  - course-review
---

[lead]You have come a long way. This session brings together everything from Credit 5 — and the entire course — into one final project and one final exam. Take a breath, look back at how much you have learned, and get ready to show what you know.

# Session 25: Credit 5 Synthesis

This is it — the last session of the course. Before the final exam and final project, let us take a moment to look at the full road you have traveled.

---

## Video Tutorial

There are no new videos for Session 25.

If you want to review, revisit any videos from `source/week 3/Day 4/` (error handling) or `source/week 4/` (fetch and modules) on the shared class drive.

---

## Credit 5 Review: What You Learned

### Session 21 — Error Handling

JavaScript has four main error types: `SyntaxError` (bad code syntax), `ReferenceError` (variable not declared), `TypeError` (wrong type for an operation), and `RangeError` (value out of range).

The `try/catch/finally` pattern lets you handle errors without crashing your program. The `catch` block receives an error object with `name`, `message`, and `stack` properties. `finally` always runs — even if there was no error — making it perfect for cleanup.

You can throw your own errors with `throw new Error("message")` or throw a specific type like `throw new TypeError("Expected a number")`. Nested try/catch gives you fine control over individual steps inside a larger operation.

### Session 22 — Fetch API Basics

`fetch(url)` returns a Promise that resolves to a **Response object** — not the data itself. To get the data, you call `response.json()` (for JSON) or `response.text()` (for plain text), which also returns a Promise.

`response.ok` is `true` when the status code is between 200 and 299. The `.catch()` at the end of a fetch chain handles any error that occurs anywhere in the chain, including network failures and JSON parse errors.

For this course, you work with local JSON files. A valid JSON file uses double quotes for all keys and string values, has no trailing commas, and has no comments.

### Session 23 — Advanced Fetch and Headers

Fetch does NOT automatically throw for 4xx or 5xx status codes. You must check `response.ok` and throw manually if it is false. You can provide specific messages for specific codes (like 404) to make debugging easier.

Headers are metadata that travel with requests. POST requests require `method: "POST"`, a `Content-Type: application/json` header, and a `body` of `JSON.stringify(data)`.

Combining fetch with `async/await` and `try/catch` gives you the cleanest and most readable pattern for loading data. The pattern: `async function load(url) { try { const res = await fetch(url); if (!res.ok) throw ...; const data = await res.json(); return data; } catch(e) { ... return null; } }`

### Session 24 — ES Modules

A module is a JavaScript file that explicitly exports and imports values. Named exports (`export const x`) can be many per file; they are imported with curly braces. Default exports (`export default`) are one per file; they are imported without curly braces.

To use modules in HTML, the entry-point `<script>` must have `type="module"`. Import paths must include the `.js` extension and start with `./`. Modules run in strict mode automatically.

The typical structure for a small module project: `utils.js` (helper functions, named exports), `data.js` (data, default export), `app.js` (main logic, imports from both), `index.html` (loads app.js as module).

---

## Full Course Review: Five Credits of JavaScript

Look at how far you have come.

### Credit 1 — JavaScript Foundations (Sessions 1–5)
You started with the basics: variables with `let`, `const`, and `var`; data types (strings, numbers, booleans, null, undefined); arithmetic and comparison operators; string methods and template literals; and conditionals with `if/else` and `switch`. You learned how JavaScript programs represent and reason about information.

### Credit 2 — Arrays, Loops and Functions (Sessions 6–10)
You learned to work with collections of data using arrays and loops. `for`, `while`, `for...of`, and `for...in` gave you ways to repeat work. Functions — with parameters, return values, arrow syntax, and default parameters — let you package logic for reuse. Array methods like `.map()`, `.filter()`, `.reduce()`, and `.find()` gave you powerful tools to transform data without manual loops.

### Credit 3 — Objects, Classes and Scope (Sessions 11–15)
You learned how JavaScript organizes complex data in objects. Object methods, `this`, and the prototype chain showed how objects know what they are. Classes gave you a clean syntax for creating many objects with the same shape. Scope (global, function, block) and closures showed you how variables live and die in JavaScript. Destructuring and spread/rest gave you shortcuts for working with objects and arrays.

### Credit 4 — Async JavaScript (Sessions 16–20)
You tackled asynchronous programming — one of the hardest ideas in JavaScript. Callbacks showed you the original approach; callback hell showed you why it needed to change. Promises (`then`, `catch`, `finally`, `Promise.all`) gave you a cleaner way to handle async operations. Async/await let you write async code that reads like synchronous code. Built-in objects (Date, Math, JSON, localStorage) rounded out your practical toolkit.

### Credit 5 — Error Handling, Fetch and Modules (Sessions 21–25)
You learned to write defensive code: catching errors before they crash programs, throwing useful error messages, and nesting try/catch for fine control. You fetched real data from local files using the Fetch API, checking status codes and handling failures properly. You organized multi-file projects using ES Modules with named and default exports. And now, in this final session, you are putting it all together.

---

## The Final Project

The final project for Credit 5 is the **Movie Review App**. You will build a complete multi-file application that uses fetch, modules, error handling, array methods, and DOM manipulation all at once.

See the project assignment for full details. The key files you will build:

| File | Purpose |
|---|---|
| `movies.json` | Data — array of 10 movie objects |
| `utils.js` | Module — exports `average`, `formatRating`, `filterByGenre` |
| `app.js` | Main — fetches data, imports utils, processes and displays |
| `index.html` | Entry point — loads app.js as a module |

---

## Preparing for the Final Exam

The Final Examination covers **all 25 sessions** — everything from Credit 1 through Credit 5. Here is how to prepare:

1. **Review your practice quiz results** from all five credits. The questions that were hardest for you are worth spending time on.
2. **Re-read the Key Concepts** sections of any sessions you felt shaky on.
3. **Look at your code** from your assignments. Understanding the code you wrote yourself is the best preparation.
4. **Know these topics well**: variable declarations and scope, array methods (map/filter/reduce), object methods and `this`, Promises vs. async/await, try/catch, fetch patterns, and import/export syntax.

The exam has 120 minutes and one attempt. There is no partial credit. Read each question carefully — sometimes the right answer is close to a wrong answer.

---

## Practice Quiz

Take the **Session 25 Practice Quiz** in Canvas before you start the project. It is ungraded and you can take it as many times as you like.

This quiz covers Credit 5 topics (sessions 21–24). After completing the project, take the Final Examination.

---

## Wrap-Up

You started this course not knowing what a variable was. Now you can:

- Write functions that handle errors gracefully
- Load data from files using async/await
- Build multi-file applications organized with modules
- Use array methods to transform and analyze data
- Create objects with methods, prototype chains, and classes
- Work with Promises and asynchronous code
- Control scope and use closures

That is real JavaScript. The kind that gets used in production applications every day.

The final project and final exam are your chance to show everything you know. You are ready. Take your time, read carefully, and trust the skills you have built.

Good luck — you have earned it.

{{include:session-footer}}

{{include:completion-checklist}}
