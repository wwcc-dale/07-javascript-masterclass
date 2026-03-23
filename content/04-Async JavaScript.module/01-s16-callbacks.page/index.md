---
name: "Session 16: Callbacks and Timers"
published: false
outcomes:
  - 04-MOD
topics:
  - callbacks
  - timers
  - callback-hell
---

[lead]JavaScript does one thing at a time — but the web is full of waiting. Callbacks are how you tell JavaScript "when this finishes, do that." Learn callbacks and timers today and you will understand the foundation that Promises and async/await are built on.

# Session 16: Callbacks and Timers

You already know how to write functions. Today you will learn how to pass a function as an argument to another function and let it be called later. That idea — a **callback** — is the original way JavaScript handled anything that takes time.

By the end of this session you will be able to use `setTimeout`, `setInterval`, and `clearInterval`, write your own functions that accept callbacks, and explain why deeply nested callbacks are a problem worth solving.

---

## Video Tutorial

- video-tabs
- src: source/week 3/Day 1/Timers.mp4 | Timers and Callbacks

Estimated viewing time: 20–25 minutes. Type the code examples yourself as you watch — running the code in a browser console helps the ideas stick.

---

## Key Concepts Review

### What Is a Callback?

A **callback** is a function you pass as an argument to another function. The receiving function calls your function at the right moment — often after some work is done.

Here is the simplest possible callback:

```javascript
function greet(name, callback) {
  const message = "Hello, " + name + "!";
  callback(message);
}

greet("Alex", function(msg) {
  console.log(msg);   // prints: Hello, Alex!
});
```

You can also pass an arrow function as the callback:

```javascript
greet("Sam", (msg) => console.log(msg));
```

The key insight: `greet` does not know what the callback will do with `message`. That is on purpose. It makes `greet` flexible — any caller can decide what happens next.

---

### Why Does JavaScript Use Callbacks?

JavaScript runs in a single thread. That means it can only do one thing at a time. When something takes time — like waiting for a file to load, a timer to fire, or a network response to arrive — JavaScript cannot just freeze and wait. Other code needs to keep running.

Callbacks solve this. Instead of waiting, you say: "Start this task, and when it is done, call this function." JavaScript registers your callback, continues doing other work, and calls your function when the time comes.

---

### setTimeout — Run Something Once After a Delay

`setTimeout(callback, milliseconds)` schedules a function to run once after a delay.

```javascript
console.log("Start");

setTimeout(function() {
  console.log("This runs 2 seconds later");
}, 2000);

console.log("End");
```

Output order:
```
Start
End
This runs 2 seconds later
```

Notice: "End" prints before the delayed message. JavaScript did not wait — it moved on and came back when the timer fired.

**Cancelling a timeout:**

```javascript
const timerId = setTimeout(() => console.log("Never runs"), 5000);
clearTimeout(timerId);   // cancels the timeout before it fires
```

---

### setInterval — Run Something Repeatedly

`setInterval(callback, milliseconds)` calls a function repeatedly, every N milliseconds.

```javascript
let count = 0;

const intervalId = setInterval(function() {
  count++;
  console.log("Tick:", count);

  if (count === 5) {
    clearInterval(intervalId);   // stop after 5 ticks
    console.log("Done!");
  }
}, 1000);
```

This logs `Tick: 1` through `Tick: 5`, one per second, then stops.

**Always save the return value** of `setInterval` so you can stop it with `clearInterval`. An interval that never stops is a common bug.

---

### Writing Your Own Callback-Accepting Functions

You can write any function that accepts a callback. This is the same pattern that `setTimeout` and `setInterval` use:

```javascript
function processData(data, onSuccess, onError) {
  if (data) {
    onSuccess("Processed: " + data);
  } else {
    onError("No data provided");
  }
}

processData(
  "hello",
  (result) => console.log(result),   // prints: Processed: hello
  (err) => console.log("Error:", err)
);
```

Notice the function accepts two callbacks — one for success, one for error. This pattern was very common before Promises existed.

---

### Callback Hell

When one async operation depends on the result of another, you start nesting callbacks inside callbacks. This is called **callback hell** (sometimes "the pyramid of doom"):

```javascript
setTimeout(function() {
  console.log("Step 1 done");
  setTimeout(function() {
    console.log("Step 2 done");
    setTimeout(function() {
      console.log("Step 3 done");
      // imagine 3 more levels...
    }, 1000);
  }, 1000);
}, 1000);
```

Problems with this code:
- Hard to read — indentation grows to the right
- Hard to handle errors — each level needs its own error check
- Hard to maintain — changing the order of steps means restructuring everything

This is exactly why **Promises** (Session 17) and **async/await** (Session 18) were invented. They solve callback hell while keeping the single-threaded model.

---

### Showing Output on the Page

So far you have used `console.log()` to see results. You can also write text directly to the page using the DOM (Document Object Model) — the browser's way of representing the HTML structure as JavaScript objects.

Two lines are all you need:

```javascript
// Get a reference to an element by its id attribute
const output = document.getElementById("output");

// Set its HTML content
output.innerHTML = "Counter: 3";
```

In your HTML file, add an element with a matching id:

```html
<p id="output">Waiting...</p>
```

When JavaScript runs `output.innerHTML = "Counter: 3"`, the paragraph text on the page changes instantly.

You can call `document.getElementById("output")` as many times as you need — each time it grabs the current reference. Updating `innerHTML` inside a `setInterval` callback makes the page update on a live timer.

---

### Quick Reference

| Tool | What it does |
|---|---|
| `setTimeout(fn, ms)` | Calls `fn` once after `ms` milliseconds |
| `clearTimeout(id)` | Cancels a pending timeout |
| `setInterval(fn, ms)` | Calls `fn` every `ms` milliseconds |
| `clearInterval(id)` | Stops a running interval |
| `document.getElementById("id")` | Gets an HTML element by its id |
| `element.innerHTML = "text"` | Sets the HTML content of an element |

---

## Practice Quiz

Take the **Session 16 Practice Quiz** in Canvas before you start the assignment. It is ungraded and you can take it as many times as you like.

The quiz checks your understanding of callbacks, `setTimeout`, `setInterval`, and callback hell. If you miss a question, re-read the Key Concepts section above.

---

## Wrap-Up

In this session you learned:

- A **callback** is a function passed as an argument to another function and called later.
- JavaScript is single-threaded, so callbacks let other code run while waiting for something to finish.
- `setTimeout(fn, ms)` runs a function once after a delay; `clearTimeout(id)` cancels it.
- `setInterval(fn, ms)` runs a function repeatedly; `clearInterval(id)` stops it.
- **Callback hell** is deeply nested callbacks that are hard to read — Promises and async/await solve this.
- `document.getElementById("id")` gets an HTML element; setting `element.innerHTML` updates what the page displays.

Next up is **Session 17: Promises**, where you will learn the cleaner way to handle async operations.

Great work today. Understanding callbacks is how you understand everything that comes after.

{{include:session-footer}}

{{include:completion-checklist}}
