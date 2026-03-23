---
indent: 2
name: "Solution: Session 17 — Promises"
published: false
outcomes:
  - 04-MOD
topics:
  - promises
  - async
---

# Instructor Solution: Session 17 — Promises

> alert: warning
>
> This page is for instructor reference only. Keep unpublished until after the assignment deadline.

---

## Student Hint

> alert: tip
>
> Inside `delay(ms)`, use `new Promise((resolve) => setTimeout(resolve, ms))` — when the timer fires, it resolves the Promise. You do not need to reject for the basic version. Chain the delays by returning the next `delay()` call inside each `.then()` callback — the return value of `.then()` becomes the next Promise in the chain.

---

## Full Solution

Builds a `delay(ms)` utility, chains three steps with `.then()`, adds a reject-capable variant, demonstrates `.finally()`, and shows `Promise.all` and `Promise.race`.

```javascript
// delay(ms) — returns a Promise that resolves after ms milliseconds
function delay(ms, label = "") {
  return new Promise((resolve) => {
    setTimeout(() => {
      if (label) console.log(`[${label}] after ${ms}ms`);
      resolve(label);
    }, ms);
  });
}

// Chain 3 delays
console.log("Starting chain...");
delay(500, "Step 1")
  .then(() => {
    console.log("Step 1 complete — starting Step 2");
    return delay(500, "Step 2");
  })
  .then(() => {
    console.log("Step 2 complete — starting Step 3");
    return delay(500, "Step 3");
  })
  .then(() => {
    console.log("Step 3 complete — all done!");
  })
  .catch((error) => {
    console.log("Something went wrong:", error.message);
  });

// Promise that can reject
function delayOrFail(ms, shouldFail = false) {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      if (shouldFail) {
        reject(new Error("Simulated failure after " + ms + "ms"));
      } else {
        resolve("Success after " + ms + "ms");
      }
    }, ms);
  });
}

delayOrFail(300, false)
  .then(result => console.log("Result:", result))
  .catch(err => console.log("Caught error:", err.message));

delayOrFail(300, true)
  .then(result => console.log("Won't see this:", result))
  .catch(err => console.log("Caught expected error:", err.message));

// .finally() — runs regardless
delayOrFail(200, false)
  .then(r => console.log("Finally test:", r))
  .catch(e => console.log("Error:", e.message))
  .finally(() => console.log("Finally always runs"));

// Promise.all — wait for multiple at once
console.log("Starting Promise.all...");
Promise.all([delay(300, "A"), delay(200, "B"), delay(400, "C")])
  .then(results => console.log("All resolved:", results));

// Promise.race — first one wins
Promise.race([delay(500, "slow"), delay(100, "fast"), delay(300, "medium")])
  .then(winner => console.log("Race winner:", winner));
```

---

## Instructor Notes

- **Core requirements:** `delay(ms)` using `new Promise` + `setTimeout`, a 3-step `.then()` chain, and a `.catch()` handler present.
- **Common mistake:** Calling `resolve()` outside the `setTimeout` callback — the Promise resolves immediately rather than after the delay.
- **Common mistake:** Not returning the next `delay()` call inside `.then()` — without `return`, the chain breaks and subsequent steps start immediately instead of sequentially.
- **Common mistake:** Using `async/await` syntax instead of `.then()` chains — conceptually correct but the assignment specifically targets `.then()` chaining; flag it and ask the student to rewrite.
- **Intermediate stretch:** A `delayOrFail` variant that can reject, plus `.finally()` usage (included in solution above).
- **Advanced stretch:** `Promise.all` waiting for multiple concurrent delays; `Promise.race` returning the first resolved value.
