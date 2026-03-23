---
name: "Solution: Session 18 — Async/Await"
published: false
outcomes:
  - 04-MOD
topics:
  - async-await
  - promises
---

# Instructor Solution: Session 18 — Async/Await

> alert: warning
>
> This page is for instructor reference only. Keep unpublished until after the assignment deadline.

---

## Student Hint

> alert: tip
>
> Mark your function with `async` and then use `await` before each `delay()` call. For the parallel version, start all the `delay()` calls at the same time and pass them to `Promise.all()` — do NOT `await` them one at a time in sequence, because that would still be sequential. Use `Date.now()` before and after each function to measure elapsed time.

---

## Full Solution

Rewrites the session 17 delay chain using `async`/`await`, contrasts sequential and parallel execution with `Promise.all`, and adds `try/catch/finally` error handling inside an async function.

```javascript
// Reuse delay() from previous session
function delay(ms, label = "") {
  return new Promise((resolve) => {
    setTimeout(() => {
      if (label) console.log(`  [${label}]`);
      resolve(label);
    }, ms);
  });
}

// Sequential — each step waits for the previous
async function runSequential() {
  const start = Date.now();
  console.log("Sequential: starting");

  await delay(300, "Step 1");
  await delay(300, "Step 2");
  await delay(300, "Step 3");

  const elapsed = Date.now() - start;
  console.log(`Sequential: done in ~${elapsed}ms (expected ~900ms)`);
}

// Parallel — all steps start at the same time
async function runParallel() {
  const start = Date.now();
  console.log("Parallel: starting");

  // Start all three at once, then wait for all to finish
  await Promise.all([
    delay(300, "A"),
    delay(300, "B"),
    delay(300, "C"),
  ]);

  const elapsed = Date.now() - start;
  console.log(`Parallel: done in ~${elapsed}ms (expected ~300ms)`);
}

// Error handling with try/catch
function riskyDelay(ms, shouldFail = false) {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      shouldFail ? reject(new Error("Simulated failure")) : resolve("ok");
    }, ms);
  });
}

async function runWithError() {
  try {
    const result = await riskyDelay(100, false);
    console.log("Success:", result);

    await riskyDelay(100, true);   // this will throw
    console.log("This line never runs");
  } catch (error) {
    console.log("Caught in async function:", error.message);
  } finally {
    console.log("Finally block ran");
  }
}

// Run all three
runSequential();
// Note: runParallel will start while runSequential is in progress
// because we do not await runSequential() here
setTimeout(() => runParallel(), 1000);
setTimeout(() => runWithError(), 2200);
```

---

## Instructor Notes

- **Core requirements:** An `async` function using `await`, a sequential version, a parallel version with `Promise.all`, and timing logged with `Date.now()`.
- **Common mistake:** Attempting to parallelize by removing `await` from individual calls — without `await`, the Promise is created but its result is discarded and there is no guarantee of ordering.
- **Common mistake:** Writing the parallel version as successive `await delay()` calls — this is still sequential. The student must create all Promises before awaiting them; `Promise.all` is the right tool.
- **Common mistake:** Wrapping `try/catch` around the async function call site rather than inside the function — both patterns work, but the idiomatic placement is inside the async function.
- **Intermediate stretch:** `try/catch/finally` inside an async function covering both success and failure paths (included in solution above).
- **Advanced stretch:** `Promise.allSettled()` to run parallel tasks and collect all results regardless of whether any individual task rejected.
