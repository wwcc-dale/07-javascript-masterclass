---
name: "Session 20: Credit 4 Synthesis — Async JavaScript"
published: true
outcomes:
  - 04-MOD
topics:
  - callbacks
  - promises
  - async-await
  - math-object
  - date-object
  - json
  - set
  - map
---

[lead]You have covered four sessions of async JavaScript and built-in objects. This session ties it all together and sets you up for the Credit 4 project — a Task Timer application that uses everything you have learned.

# Session 20: Credit 4 Synthesis — Async JavaScript

You made it through the async JavaScript credit. This session is a review and launch pad. There is no new material — just a clear summary of what you know, and the project brief for the Credit 4 assignment.

Take your time with this page. If any part of the review feels shaky, go back to the session that covers it before starting the project.

---

## Video Tutorial

No new videos for this session. If you need a refresher on any topic, the videos are on the shared class drive in `source/week 3/Day 1/` (async topics) and `source/week 3/Day 3/` (built-in objects).

---

## Key Concepts Review

This is a full review of Credit 4. Read through it before starting the project.

---

### Callbacks (Session 16)

A **callback** is a function passed as an argument to another function and called later.

```javascript
function greet(name, callback) {
  callback("Hello, " + name);
}
greet("Alex", msg => console.log(msg));
```

`setTimeout(fn, ms)` — runs `fn` once after `ms` milliseconds.
`setInterval(fn, ms)` — runs `fn` every `ms` milliseconds. Use `clearInterval(id)` to stop it.

**Callback hell** happens when callbacks are deeply nested. Promises and async/await solve this.

---

### Promises (Session 17)

A **Promise** is an object representing a future value. It is pending, then fulfilled or rejected.

```javascript
function delay(ms) {
  return new Promise(resolve => setTimeout(resolve, ms));
}
```

- `.then(fn)` — runs when fulfilled; returns a new Promise so you can chain
- `.catch(fn)` — runs when rejected
- `.finally(fn)` — runs either way

`Promise.all([p1, p2])` — waits for all Promises; fastest approach for independent tasks.
`Promise.race([p1, p2])` — settles as soon as the first Promise settles.

---

### Async/Await (Session 18)

`async` functions always return a Promise. `await` pauses the function until a Promise settles.

```javascript
async function run() {
  const result = await delay(500);
  console.log(result);
}
```

Use `try/catch/finally` for error handling.

Sequential (slower): multiple `await` calls run one after another.
Parallel (faster): use `await Promise.all([...])` for independent operations.

---

### Math (Session 19)

```javascript
Math.random()          // random decimal [0, 1)
Math.floor(n)          // round down
Math.ceil(n)           // round up
Math.round(n)          // round to nearest
Math.max(a, b, c)      // largest
Math.min(a, b, c)      // smallest
Math.abs(n)            // absolute value
Math.sqrt(n)           // square root

// Random integer 1 to N:
Math.floor(Math.random() * N) + 1
```

---

### Date (Session 19)

```javascript
const d = new Date();
d.getFullYear()         // e.g., 2026
d.getMonth() + 1        // 1–12 (add 1 — getMonth() is 0-based)
d.getDate()             // day of month
d.getDay()              // 0 = Sunday, 6 = Saturday
d.toLocaleDateString()  // human-readable date string
```

Use `Date.now()` to get the current timestamp as a number (milliseconds since 1970). Subtract two `Date.now()` calls to measure elapsed time.

---

### JSON (Session 19)

```javascript
const obj = { name: "Alex", score: 95 };
const str = JSON.stringify(obj);   // '{"name":"Alex","score":95}'
const back = JSON.parse(str);      // { name: "Alex", score: 95 }
```

JSON stores data as text. Use it to save data, log structured output, or prepare data for transfer.

---

### String and Number Methods (Session 19)

Strings: `split()`, `join()`, `repeat()`, `startsWith()`, `endsWith()`, `padStart()`, `padEnd()`
Numbers: `toFixed(n)`, `parseInt()`, `parseFloat()`, `Number.isNaN()`, `Number.isFinite()`

---

### Set (Session 19)

```javascript
const unique = [...new Set([1, 2, 2, 3])];   // [1, 2, 3]
const s = new Set();
s.add("a"); s.has("a"); s.delete("a"); s.size;
```

---

### Map (Session 19)

```javascript
const m = new Map();
m.set("key", "value");
m.get("key");    // "value"
m.has("key");    // true
m.size;
```

Map keys can be any type. Map is ideal for counting, grouping, or fast lookups.

---

### Putting It All Together — The Task Timer Project

The Credit 4 project asks you to build a **Task Timer** application that combines all of these skills:

- An array of task objects (plain JS objects)
- A `runTask(task)` async function that uses a `setTimeout`-based Promise to simulate work, logging start and end with a `Date` timestamp
- A `runAllSequential(tasks)` async function that runs tasks one after another
- A `runAllParallel(tasks)` async function that uses `Promise.all`
- Timing both approaches with `Date.now()`
- Logging the final task list with `JSON.stringify`

The full project brief is in the Credit 4 Project Assignment. Read it carefully before you write any code — understanding the whole picture first saves time.

---

## Practice Quiz

Take the **Session 20 Project Practice Quiz** in Canvas to check your readiness for the project. It is ungraded and you can take it as many times as you like.

---

## Wrap-Up

In Credit 4 you learned:

- **Callbacks** — the foundation: functions passed to other functions and called later
- **Timers** — `setTimeout` and `setInterval` for delayed and repeated execution
- **Promises** — a cleaner async model with `.then()/.catch()/.finally()` and chaining
- **Async/Await** — syntax that makes Promises read like synchronous code
- **Built-in Objects** — Math, Date, JSON, String/Number methods, Set, and Map

You are ready for the project. Take your time, re-read the assignment, and build it step by step.

After this credit comes Credit 5: DOM and Events — where your JavaScript will interact with real web pages.

You have come a long way. Go build something great.

{{include:session-footer}}

{{include:completion-checklist}}
