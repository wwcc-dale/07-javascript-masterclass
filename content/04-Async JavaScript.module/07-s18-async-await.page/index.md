---
name: "Session 18: Async/Await"
published: false
outcomes:
  - 04-MOD
topics:
  - async-await
  - async-javascript
---

[lead]Promises are cleaner than callbacks — but async/await makes async code look almost like the synchronous code you already know. Two keywords, `async` and `await`, let you write step-by-step async logic without a single `.then()` in sight.

# Session 18: Async/Await

You built Promise chains in Session 17. Today you learn a syntax layer that sits on top of Promises. `async` functions and the `await` keyword do not replace Promises — they are Promises underneath. But they let you write async code that reads from top to bottom, like a recipe.

By the end of this session you will be able to write `async` functions, use `await` to wait for Promises, handle errors with `try/catch`, and choose between sequential and parallel execution.

---

## Video Tutorial

- video-tabs
- src: source/week 3/Day 1/Async functions.mp4 | Async Functions
- src: source/week 3/Day 1/Async functions.mp4 | Await and try/catch

Estimated viewing time: 20–25 minutes. Type the examples as you watch and run them in a browser — seeing async code execute step by step makes it much clearer.

---

## Key Concepts Review

### The async Keyword

Adding `async` before a function declaration changes two things:
1. The function always returns a Promise, even if you return a plain value.
2. You can use `await` inside it.

```javascript
async function greet() {
  return "Hello!";
}

greet().then(msg => console.log(msg));   // Hello!
```

Even though `greet()` just returns a string, it is wrapped in a fulfilled Promise automatically.

You can also write async arrow functions:

```javascript
const greet = async () => "Hello!";
```

---

### The await Keyword

`await` pauses execution inside an async function until a Promise settles. It then gives you the resolved value.

```javascript
function delay(ms) {
  return new Promise(resolve => setTimeout(resolve, ms));
}

async function run() {
  console.log("Start");
  await delay(1000);          // pauses here for 1 second
  console.log("After 1 second");
  await delay(500);           // pauses again for 0.5 seconds
  console.log("After 0.5 more seconds");
}

run();
```

The code reads top to bottom — no callbacks, no `.then()`. But underneath, it is still async. Other code can run while `run()` is waiting.

**Important:** You can only use `await` inside an `async` function. Using it anywhere else is a syntax error.

---

### Error Handling: try/catch/finally

With `.then()` chains you used `.catch()`. With async/await you use standard `try/catch` blocks:

```javascript
function failingDelay(ms) {
  return new Promise((resolve, reject) => {
    setTimeout(() => reject(new Error("Something went wrong")), ms);
  });
}

async function run() {
  try {
    await failingDelay(500);
    console.log("This line is skipped");
  } catch (error) {
    console.log("Caught:", error.message);   // Caught: Something went wrong
  } finally {
    console.log("Cleanup — always runs");
  }
}

run();
```

`try` wraps the code that might fail. `catch` runs if any `await` inside `try` rejects. `finally` runs no matter what — just like `.finally()` on a Promise chain.

---

### Sequential vs. Parallel Execution

By default, multiple `await` expressions run one after another — **sequentially**. Each one waits for the previous to finish before starting.

```javascript
async function sequential() {
  const start = Date.now();
  await delay(500);
  await delay(500);
  await delay(500);
  console.log("Sequential took:", Date.now() - start, "ms");  // ~1500 ms
}
```

To run multiple Promises at the **same time** (in parallel), use `Promise.all` with `await`:

```javascript
async function parallel() {
  const start = Date.now();
  await Promise.all([delay(500), delay(500), delay(500)]);
  console.log("Parallel took:", Date.now() - start, "ms");    // ~500 ms
}
```

The parallel version is about three times faster for this example. Use parallel execution when the operations do not depend on each other's results.

---

### Returning Values from async Functions

An `async` function can return a value that the caller can await:

```javascript
async function fetchData(id) {
  await delay(300);
  return { id: id, name: "Item " + id };
}

async function main() {
  const item = await fetchData(42);
  console.log(item);   // { id: 42, name: "Item 42" }
}

main();
```

Calling `fetchData(42)` returns a Promise. The `await` in `main` unwraps it.

---

### When to Use Sequential vs. Parallel

Use **sequential** when:
- Step B needs the result from Step A
- The order matters for correctness

Use **parallel** (Promise.all) when:
- Operations are independent of each other
- You want the fastest possible total time

```javascript
async function example() {
  // Sequential — step2 needs result of step1
  const user = await getUser(1);
  const profile = await getProfile(user.profileId);

  // Parallel — these two are independent
  const [posts, friends] = await Promise.all([
    getPosts(user.id),
    getFriends(user.id)
  ]);
}
```

---

### Async Functions Always Return Promises

This is worth repeating. Even this async function that throws an error:

```javascript
async function broken() {
  throw new Error("Oops!");
}
```

Returns a **rejected Promise**. You handle it with `.catch()` or `try/catch` in the calling function.

---

## Practice Quiz

Take the **Session 18 Practice Quiz** in Canvas before you start the assignment. It is ungraded and you can take it as many times as you like.

The quiz checks your understanding of `async`, `await`, `try/catch` with async functions, and sequential vs. parallel execution. If you miss a question, re-read the Key Concepts section above.

---

## Wrap-Up

In this session you learned:

- `async` functions always return a Promise and allow the use of `await` inside them.
- `await` pauses an async function until a Promise settles and gives you the resolved value.
- Use `try/catch/finally` for error handling in async functions.
- Multiple `await` calls run **sequentially** by default — one after another.
- Use `await Promise.all([...])` to run independent operations in **parallel**.

Next up is **Session 19: Built-in Objects**, where you shift gears and explore JavaScript's built-in tools like `Math`, `Date`, `JSON`, `Set`, and `Map`.

You now know three generations of async JavaScript — callbacks, Promises, and async/await. That is a huge achievement.

{{include:session-footer}}

{{include:completion-checklist}}
