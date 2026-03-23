---
name: "Session 17: Promises"
published: true
outcomes:
  - 04-MOD
topics:
  - promises
  - async-javascript
---

[lead]Callbacks work, but deeply nested callbacks become a mess. Promises give you a cleaner way to handle async operations — you describe what to do when something succeeds, what to do when it fails, and what to do either way, all in a readable chain.

# Session 17: Promises

In the last session you saw how callback hell happens. Today you meet the solution. A **Promise** is an object that represents a value that is not available yet but will be in the future. It has a built-in way to handle both success and failure, and you can chain them instead of nesting them.

By the end of this session you will be able to create a Promise, consume it with `.then()`, `.catch()`, and `.finally()`, chain multiple Promises together, and use `Promise.all` and `Promise.race`.

---

## Video Tutorial

- video-tabs
- src: source/week 3/Day 1/Promises.mp4 | Promises
- src: source/week 3/Day 1/Chaining promises.mp4 | Chaining
- src: source/week 3/Day 1/Promise.all().mp4 | Promise.all()
- src: source/week 3/Day 1/Promise.race().mp4 | Promise.race()

Estimated viewing time: 25–30 minutes. Type the examples as you watch and run them in a browser console or small HTML file.

---

## Key Concepts Review

### What Is a Promise?

A **Promise** is an object that will eventually hold a value. When you create a Promise, you do not know the value yet — but you know you will get it (or an error) sometime in the future.

A Promise is always in one of three states:

| State | Meaning |
|---|---|
| **Pending** | The work is still in progress |
| **Fulfilled** | The work succeeded — a value is available |
| **Rejected** | The work failed — an error is available |

Once a Promise moves from pending to fulfilled or rejected, it stays that way forever.

---

### Creating a Promise

You create a Promise with `new Promise(executor)`. The executor is a function that receives two arguments: `resolve` and `reject`. Call `resolve(value)` when the work succeeds. Call `reject(error)` when it fails.

```javascript
const myPromise = new Promise(function(resolve, reject) {
  const success = true;

  if (success) {
    resolve("It worked!");
  } else {
    reject("Something went wrong.");
  }
});
```

In real async work you would put a timer or a network call inside instead of a simple `if`. Here is a Promise that resolves after a delay:

```javascript
function delay(ms) {
  return new Promise(function(resolve) {
    setTimeout(function() {
      resolve("Done after " + ms + " ms");
    }, ms);
  });
}
```

This `delay` function is your async simulation tool for all the exercises in this credit since there is no network available.

---

### Consuming a Promise: .then(), .catch(), .finally()

Once you have a Promise, you use these methods to react to it:

**`.then(callback)`** — runs when the Promise is fulfilled. Receives the resolved value.

```javascript
delay(1000).then(function(message) {
  console.log(message);   // prints: Done after 1000 ms
});
```

**`.catch(callback)`** — runs when the Promise is rejected. Receives the error.

```javascript
const failingPromise = new Promise(function(resolve, reject) {
  reject("Network error");
});

failingPromise.catch(function(error) {
  console.log("Error:", error);   // prints: Error: Network error
});
```

**`.finally(callback)`** — runs when the Promise settles, whether fulfilled or rejected. Useful for cleanup (like hiding a loading spinner).

```javascript
delay(500)
  .then((msg) => console.log(msg))
  .catch((err) => console.log("Error:", err))
  .finally(() => console.log("All done!"));
```

---

### Chaining Promises

`.then()` returns a new Promise. That means you can chain calls instead of nesting them. Each `.then` receives the value returned by the previous one.

```javascript
delay(500)
  .then(function(msg) {
    console.log("Step 1:", msg);
    return delay(500);       // return a new Promise
  })
  .then(function(msg) {
    console.log("Step 2:", msg);
    return delay(500);
  })
  .then(function(msg) {
    console.log("Step 3:", msg);
  })
  .catch(function(error) {
    console.log("Something failed:", error);
  });
```

Compare this to the callback hell version from Session 16. Much easier to read. One `.catch` at the end handles errors from any step in the chain.

---

### Promise.all — Wait for Everything

`Promise.all([p1, p2, p3])` takes an array of Promises and returns a new Promise that:
- **Fulfills** when ALL Promises in the array fulfill. The result is an array of all the values.
- **Rejects** immediately if ANY Promise rejects.

```javascript
const p1 = delay(300);
const p2 = delay(500);
const p3 = delay(200);

Promise.all([p1, p2, p3]).then(function(results) {
  console.log(results);
  // ["Done after 300 ms", "Done after 500 ms", "Done after 200 ms"]
});
```

All three run at the same time (in parallel). The result arrives after the slowest one — 500 ms total instead of 300 + 500 + 200 = 1000 ms.

---

### Promise.race — First One Wins

`Promise.race([p1, p2, p3])` returns a new Promise that settles as soon as the **first** Promise in the array settles — whether fulfilled or rejected.

```javascript
const fast = delay(200);
const slow = delay(1000);

Promise.race([fast, slow]).then(function(result) {
  console.log("Winner:", result);   // "Done after 200 ms"
});
```

`Promise.race` is useful for setting a timeout: race the real operation against a delay that rejects — if the real operation takes too long, the timeout wins.

---

### Error Handling in Chains

A single `.catch()` at the end of a chain catches errors from any `.then()` before it:

```javascript
delay(300)
  .then(() => {
    throw new Error("Something broke in step 1");
  })
  .then(() => {
    console.log("This step is skipped");
  })
  .catch((error) => {
    console.log("Caught:", error.message);   // Caught: Something broke in step 1
  });
```

When an error is thrown inside `.then()`, the Promise chain skips to the nearest `.catch()`.

---

## Practice Quiz

Take the **Session 17 Practice Quiz** in Canvas before you start the assignment. It is ungraded and you can take it as many times as you like.

The quiz checks your understanding of Promise states, `.then()/.catch()/.finally()`, chaining, `Promise.all`, and `Promise.race`. If you miss a question, re-read the Key Concepts section above.

---

## Wrap-Up

In this session you learned:

- A **Promise** is an object representing a future value — it is pending, then fulfilled or rejected.
- Create a Promise with `new Promise((resolve, reject) => { ... })`.
- Consume it with `.then()` (success), `.catch()` (error), and `.finally()` (always).
- **Chain** Promises by returning a new Promise from `.then()`.
- `Promise.all([...])` waits for all Promises; rejects if any fail.
- `Promise.race([...])` settles as soon as the first Promise settles.

Next up is **Session 18: Async/Await**, where you will learn a syntax that makes Promises look almost like synchronous code.

You are mastering async JavaScript step by step. Well done.

{{include:session-footer}}

{{include:completion-checklist}}
