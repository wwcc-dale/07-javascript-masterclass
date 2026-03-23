---
name: "Solution: Session 16 — Callbacks and Timers"
published: false
outcomes:
  - 04-MOD
topics:
  - callbacks
  - timers
---

# Instructor Solution: Session 16 — Callbacks and Timers

> alert: warning
>
> This page is for instructor reference only. Keep unpublished until after the assignment deadline.

---

## Student Hint

> alert: tip
>
> For `setInterval`, you need to keep track of how many times it has run — use a counter variable outside the interval, increment it each time, and call `clearInterval(id)` when the counter reaches 5. For your custom callback function, the function should do some work (like computing a result) and then call your callback with that result as the argument.

---

## Full Solution

Demonstrates `setTimeout`, a self-stopping `setInterval`, a custom higher-order function that accepts a callback, and a nested-callback preview of callback hell.

```javascript
// 1. setTimeout — delayed message
console.log("Starting...");

setTimeout(() => {
  console.log("This message appears after 2 seconds!");
}, 2000);

// 2. setInterval — count up to 5, then stop
let count = 0;
const intervalId = setInterval(() => {
  count++;
  console.log(`Tick: ${count}`);
  if (count >= 5) {
    clearInterval(intervalId);
    console.log("Interval stopped at count:", count);
  }
}, 500);  // fires every 500ms

// 3. Custom function that accepts a callback
function processData(data, onComplete) {
  // Simulate doing some work
  const result = data.trim().toUpperCase();
  // Call the callback with the result
  onComplete(result);
}

// Pass an arrow function as the callback
processData("  hello world  ", (processed) => {
  console.log("Processed result:", processed);  // "HELLO WORLD"
});

// Pass a named function as the callback
function handleResult(result) {
  console.log("Named callback received:", result);
}
processData("  open sesame  ", handleResult);

// 4. Demonstrate nested callbacks (callback hell preview)
setTimeout(() => {
  console.log("Step 1 complete");
  setTimeout(() => {
    console.log("Step 2 complete");
    setTimeout(() => {
      console.log("Step 3 complete (this nesting is callback hell)");
    }, 300);
  }, 300);
}, 300);
```

---

## Instructor Notes

- **Core requirements:** `setTimeout` with a delayed message, `setInterval` that self-stops at 5, and a custom function that accepts and calls a callback.
- **Common mistake:** Calling `setInterval` without storing the return value — the student cannot call `clearInterval` without the ID.
- **Common mistake:** Counter check logic errors — `count === 5` works but `count >= 5` is safer; either is acceptable.
- **Common mistake:** Confusing the callback invocation pattern — `onComplete(result)` calls the callback correctly; `return onComplete(result)` also works but shifts emphasis to the return value.
- **Note on output order:** Because of how the event loop schedules timers, the `setTimeout` and `setInterval` outputs will interleave in the console — this is expected and worth discussing with students.
- **Intermediate stretch:** Nested `setTimeout` chain demonstrating callback hell (included in solution above).
- **Advanced stretch:** Using `clearTimeout()` to cancel a pending timeout based on a runtime condition.
