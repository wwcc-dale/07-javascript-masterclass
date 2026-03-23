---
name: "Session 14: Scope and Closures"
published: true
outcomes:
  - 02-OOP
topics:
  - scope
  - closures
  - hoisting
---

[lead]Every variable you write has a "zone" where it can be used — and cannot be used. Understanding scope helps you avoid bugs and write code that works the way you expect. Closures take that idea further, giving you one of JavaScript's most powerful features.

# Session 14: Scope and Closures

You have been writing code that uses variables, functions, and blocks for several sessions now. But have you ever wondered: why can some variables be used anywhere in your program, while others only exist inside a specific function or block?

The answer is **scope**. Understanding scope means you know exactly where each variable lives and when it disappears. By the end of this session you will understand global scope, function scope, and block scope — and you will understand closures, which are a key feature of professional JavaScript.

---

## Video Tutorial

- video-tabs
- src: source/week 3/Day 2/Global scope.mp4 | Global Scope
- src: source/week 3/Day 2/Function scope.mp4 | Function Scope
- src: source/week 3/Day 2/Block scope.mp4 | Block Scope
- src: source/week 3/Day 2/Shadowing.mp4 | Variable Shadowing
- src: source/week 3/Day 2/Hoisting.mp4 | Hoisting
- src: source/week 3/Day 2/Closures.mp4 | Closures
- src: source/week 3/Day 2/The event loop.mp4 | The Event Loop
- src: source/week 3/Day 2/An issue with `var` variables and loops.mp4 | var and Loops

Estimated viewing time: 25–30 minutes. Scope and closures benefit from seeing them run — type every example and test it in your browser console as you go.

---

## Key Concepts Review

### What is Scope?

**Scope** is the region of your code where a variable can be accessed. If a variable is "in scope," you can read and use it. If it is "out of scope," your code cannot see it — and you will get a `ReferenceError` if you try.

---

### Global Scope

A variable declared **outside** all functions and blocks is in the **global scope**. It can be accessed from anywhere in your code — inside functions, inside loops, inside `if` statements, anywhere.

```javascript
const appName = "My App";  // global scope

function showName() {
  console.log(appName);   // can access it here
}

showName();               // "My App"
console.log(appName);     // "My App"
```

While global variables are convenient, using too many of them can cause problems in larger programs. Prefer keeping variables as local as possible.

---

### Function Scope

A variable declared with `var` inside a function is only accessible **inside that function**. It does not exist outside:

```javascript
function greet() {
  var message = "Hello!";
  console.log(message);   // "Hello!" — works inside the function
}

greet();
console.log(message);     // ReferenceError — message does not exist here
```

Function scope also applies to function parameters — they exist only inside the function.

---

### Block Scope

A **block** is any pair of curly braces `{}` — like the body of an `if` statement, a `for` loop, or a `while` loop.

Variables declared with `let` or `const` inside a block are only accessible **inside that block**:

```javascript
if (true) {
  let blockVar = "I am inside the block";
  const alsoBlock = "Me too";
  console.log(blockVar);     // works
}

console.log(blockVar);       // ReferenceError — not accessible here
```

`var` does NOT have block scope — it leaks out of blocks:

```javascript
if (true) {
  var leaked = "I escape the block";
}
console.log(leaked);   // "I escape the block" — this is why we avoid var
```

This is one of the main reasons you should use `let` and `const` instead of `var`.

---

### Nested Scope — Inner Access to Outer

A function or block can access variables from its surrounding (outer) scope. But the outer scope cannot access variables from the inner scope:

```javascript
const outerVar = "I am outer";

function inner() {
  const innerVar = "I am inner";
  console.log(outerVar);   // works — inner can see outer
}

inner();
console.log(innerVar);     // ReferenceError — outer cannot see inner
```

Think of it like a window. You can look outward from inside, but you cannot look inward from outside.

---

### Variable Shadowing

**Shadowing** happens when a variable in an inner scope has the **same name** as a variable in an outer scope. The inner variable "shadows" (hides) the outer one inside that scope:

```javascript
const color = "blue";   // outer

function paintIt() {
  const color = "red";  // inner — shadows the outer "color"
  console.log(color);   // "red" — sees the inner one
}

paintIt();
console.log(color);     // "blue" — outer is unchanged
```

The inner `color` is a completely separate variable that just happens to have the same name. The outer `color` is not changed.

Shadowing can make code confusing. As a habit, try to use unique names for variables in inner scopes.

---

### Hoisting

**Hoisting** is JavaScript's behavior of moving variable and function declarations to the top of their scope before the code runs.

**`var` is hoisted and initialized to `undefined`:**

```javascript
console.log(myVar);   // undefined — not an error, but not the real value
var myVar = 10;
console.log(myVar);   // 10
```

Behind the scenes, JavaScript treats this as:
```javascript
var myVar;            // hoisted to top, initialized as undefined
console.log(myVar);   // undefined
myVar = 10;
console.log(myVar);   // 10
```

**`let` and `const` are hoisted BUT NOT initialized (Temporal Dead Zone):**

```javascript
console.log(myLet);   // ReferenceError — cannot access before initialization
let myLet = 10;
```

`let` and `const` exist in the code from the very start of their scope, but you cannot use them before their declaration line. This "zone" before the declaration is called the **Temporal Dead Zone (TDZ)**.

**Rule:** Always declare variables at the top of the block or function where you need them. This avoids hoisting surprises.

**Function declarations are fully hoisted:**

```javascript
greet();   // "Hello!" — works even before the declaration

function greet() {
  console.log("Hello!");
}
```

Function declarations are hoisted completely — both the name and the body. Function expressions (stored in variables) are not.

---

### Closures

A **closure** is a function that "remembers" the variables from its surrounding scope, even after that outer function has finished running.

This sounds complex, but here is the key idea: when a function is defined inside another function, the inner function keeps a connection to the outer function's variables — even after the outer function returns.

```javascript
function makeCounter() {
  let count = 0;        // this variable is in makeCounter's scope

  return function() {   // the inner function is the closure
    count++;
    return count;
  };
}

const counter = makeCounter();   // makeCounter has finished, but count lives on

console.log(counter());   // 1
console.log(counter());   // 2
console.log(counter());   // 3
```

What is happening here:
1. `makeCounter()` runs and creates a `count` variable.
2. It returns the inner function without running it.
3. `makeCounter()` finishes — but the inner function still holds a reference to `count`.
4. Each time you call `counter()`, it increments that same `count` variable.

The inner function and its "captured" variables together form the **closure**. The variable `count` is private — no other code can change it directly.

---

### Why Closures Matter

Closures give you **private state** in JavaScript without needing classes:

```javascript
function makeCounter() {
  let count = 0;
  return {
    increment() { count++; },
    reset()     { count = 0; },
    value()     { return count; }
  };
}

const myCounter = makeCounter();
myCounter.increment();
myCounter.increment();
myCounter.increment();
console.log(myCounter.value());   // 3
myCounter.reset();
console.log(myCounter.value());   // 0
```

The `count` variable is completely hidden from the outside world. The only way to change it is through the returned methods.

---

### The Classic `var` in a Loop Bug

This is a famous JavaScript gotcha that trips up many developers. Understanding it will help you avoid it — and help you understand why `let` exists.

**The problem:**

```javascript
const operations = [];

for (var i = 0; i < 5; i++) {
  operations.push(() => {
    console.log(i);
  });
}

for (const op of operations) {
  op();
}
```

You might expect this to log: `0 1 2 3 4`

But what actually logs is: `5 5 5 5 5`

**Why?** Because `var` is function-scoped (not block-scoped). The `for` loop does not create a new `i` for each iteration — there is only ONE `i`, shared by all five functions. By the time the functions run, the loop has finished and `i` is `5`.

**The fix — use `let`:**

```javascript
for (let i = 0; i < 5; i++) {
  operations.push(() => {
    console.log(i);
  });
}
```

With `let`, each loop iteration gets its **own copy** of `i`. Now the functions each remember their own value.

This is one of the most important reasons to always use `let` or `const` instead of `var`.

---

### Event Loop — A First Look

JavaScript runs **one thing at a time**. When it runs your code, it processes one statement, then the next, in order. It cannot do two things simultaneously.

But sometimes code needs to wait — like loading a file or waiting for a button click. JavaScript handles this with an **event loop**: while your code is waiting, other code can run. When the waiting is done, the callback goes into a **queue** and runs when JavaScript is free.

You will explore this properly in Credit 4. For now, just know:
- JavaScript is single-threaded (one thing at a time).
- Async operations use a queue so the program does not freeze.
- Closures are important for async code — they help callback functions remember the data they need.

---

### Quick Reference Table

| Concept | Key Idea |
|---|---|
| Global scope | Variable is accessible everywhere |
| Function scope | `var` inside a function — only accessible in that function |
| Block scope | `let`/`const` inside `{}` — only accessible inside that block |
| Shadowing | Inner variable with same name hides the outer one |
| Hoisting (`var`) | Moved to top, initialized as `undefined` |
| Hoisting (`let`/`const`) | Moved to top but NOT usable before declaration (TDZ) |
| Closure | Inner function that remembers outer function's variables |
| `var` in loops | Only one `i` shared by all iterations — use `let` instead |

---

## Practice Quiz

Take the **Session 14 Practice Quiz** in Canvas before you start the assignment. It pulls questions from the Session 14 question bank. It is ungraded and you can take it as many times as you like.

---

## Wrap-Up

In this session you learned:

- **Scope** is the region of code where a variable can be used.
- **Global scope** means accessible everywhere; **function scope** means `var` inside a function; **block scope** means `let`/`const` inside `{}`.
- Inner scopes can see outer scopes, but not the other way around.
- **Shadowing** happens when an inner variable has the same name as an outer one.
- **Hoisting** moves declarations to the top — `var` becomes `undefined`, `let`/`const` enter the TDZ.
- A **closure** is a function that remembers its surrounding variables even after the outer function returns.
- Closures give you **private state** — variables hidden from the outside world.
- Using `var` in a `for` loop creates ONE shared variable — all closures inside the loop see the same value after the loop ends. Use `let` to give each iteration its own copy.
- JavaScript's **event loop** lets it handle waiting without freezing — more on this in Credit 4.

Next up is **Session 15**, where you will put everything from Credit 3 together in a real project: a Library Catalog that uses objects, classes, and array methods all at once. Then you will take the Midterm Exam covering everything from Sessions 1 through 15.

Scope and closures are concepts that take time to sink in fully. If they feel tricky right now, that is completely normal. Doing the assignment will help a great deal.

{{include:session-footer}}

{{include:completion-checklist}}
