---
name: "Session 8: Functions"
published: true
outcomes:
  - 03-ELEM
topics:
  - functions
  - arrow-functions
  - scope
---

[lead]Functions are the building blocks of every serious JavaScript program — they let you name a chunk of code, reuse it whenever you need it, and keep your programs clean and organized.

# Session 8: Functions

So far you have written code that runs from top to bottom, one line at a time. That works for small programs. But as soon as you need to do the same thing in multiple places — or break a big problem into smaller pieces — you need functions.

A function is like a recipe. You write it once. You can follow it any number of times, with different ingredients each time, and get a result back. By the end of this session you will know three ways to write functions, how to pass information in, and how to get information back out.

---

## Video Tutorial

- video-tabs
- src: source/week 2/Day 1/Functions.mp4 | Introduction to Functions
- src: source/week 2/Day 1/Function parameters.mp4 | Parameters
- src: source/week 2/Day 1/Returning values.mp4 | Return Values
- src: source/week 2/Day 1/Arrow functions.mp4 | Arrow Functions
- src: source/week 2/Day 1/Nesting functions.mp4 | Nesting Functions
- src: source/week 2/Day 1/Recursive functions.mp4 | Recursion
- src: source/week 2/Day 1/Immediately invoked functions.mp4 | Immediately-Invoked Functions

Estimated viewing time: 20–25 minutes. Type the examples yourself as you watch — functions are learned by doing, so the more you type, the better.

---

## Key Concepts Review

### What is a Function?

A **function** is a block of code with a name. You define it once and can run it (call it) as many times as you like. Every time you call it, it does the same job — possibly with different input values.

---

### Function Declaration

A **function declaration** uses the `function` keyword followed by a name:

```javascript
function greet(name) {
  return "Hello, " + name + "!";
}

console.log(greet("Alex"));   // "Hello, Alex!"
console.log(greet("Jordan")); // "Hello, Jordan!"
```

The parts of this function:

| Part | What it is |
|---|---|
| `function` | keyword that starts the declaration |
| `greet` | the function's name (an identifier) |
| `(name)` | the **parameter** — a variable that receives the input |
| `{ ... }` | the function body — the code that runs |
| `return` | sends a value back to wherever the function was called |

**Function declarations are hoisted** — the JavaScript engine reads them before it runs any code, so you can call a function declaration even before it appears in your file. (This is different from function expressions, as you will see below.)

---

### Parameters and Arguments

**Parameters** are the names listed in the function definition. They are like empty slots waiting to be filled.

**Arguments** are the actual values you pass when you call the function.

```javascript
function add(a, b) {   // a and b are parameters
  return a + b;
}

add(3, 5);             // 3 and 5 are arguments — result is 8
add(10, 20);           // 10 and 20 are arguments — result is 30
```

You can have as many parameters as you like, separated by commas.

---

### Return Values

`return` sends a value back to wherever the function was called. Without `return`, the function gives back `undefined`:

```javascript
function double(n) {
  return n * 2;
}

const result = double(7);
console.log(result);  // 14
```

When JavaScript reaches `return`, it stops running the function immediately and sends the value back.

---

### Default Parameters

If someone calls your function without providing an argument, you can supply a **default value**:

```javascript
function greet(name = "friend") {
  return "Hello, " + name + "!";
}

console.log(greet("Alex"));   // "Hello, Alex!"
console.log(greet());         // "Hello, friend!"
```

The default value is used only when the argument is missing or `undefined`.

---

### Function Expression

A **function expression** assigns a function to a variable. The function itself has no name (it is **anonymous**):

```javascript
const greet = function(name) {
  return "Hello, " + name + "!";
};

console.log(greet("Alex"));  // "Hello, Alex!"
```

Function expressions are NOT hoisted. You must define them before you call them. This is different from function declarations.

---

### Arrow Functions

An **arrow function** is a shorter way to write a function expression. It uses `=>` (an arrow):

```javascript
const greet = (name) => {
  return "Hello, " + name + "!";
};
```

If the function body is just one expression and you want to return it immediately, you can shorten it further:

```javascript
const greet = (name) => "Hello, " + name + "!";
```

These two versions do exactly the same thing. The second one works because when you leave out `{}` and `return`, the expression on the right is automatically returned.

If there is only one parameter, you can also leave out the parentheses:

```javascript
const double = n => n * 2;
console.log(double(5));  // 10
```

**Arrow functions do not have their own `this`** — this matters a lot in Credit 4 when you study objects and classes. For now, arrow functions are just a shorthand for writing small functions.

---

### Calling a Function

Calling a function means running it. You call a function by writing its name followed by parentheses:

```javascript
greet("Alex");   // calls the function and throws away the result
const msg = greet("Alex");  // calls it and saves the result
```

If you write the name without parentheses, you are just referring to the function itself — not running it:

```javascript
console.log(greet);    // prints the function definition (not its result)
console.log(greet());  // runs the function and prints the result
```

---

### Scope

**Scope** means which code can see which variables.

Variables declared **inside** a function can only be seen inside that function:

```javascript
function makeMessage() {
  const text = "Hello inside";
  console.log(text);  // works fine
}

makeMessage();
console.log(text);  // ERROR — text does not exist out here
```

Variables declared **outside** all functions are **global** and can be seen everywhere:

```javascript
const greeting = "Hi there";

function showGreeting() {
  console.log(greeting);  // works — greeting is global
}
```

Keeping variables inside functions is usually better — it avoids naming conflicts and bugs.

---

### Recursion Basics

A function can call **itself**. This is called **recursion**. It is useful for problems that repeat in a similar pattern.

Every recursive function needs a **base case** — a condition that stops the recursion. Without it, the function calls itself forever and crashes:

```javascript
function countdown(n) {
  if (n <= 0) {
    console.log("Done!");
    return;
  }
  console.log(n);
  countdown(n - 1);  // calls itself with a smaller number
}

countdown(5);
// prints: 5, 4, 3, 2, 1, Done!
```

Recursion can replace loops for some problems — but for most everyday tasks, loops are simpler.

---

### Immediately-Invoked Function Expressions (IIFE)

An **IIFE** (say "iffy") is a function that runs the moment it is defined — you do not call it separately. The syntax wraps the function in parentheses, then immediately calls it with `()`.

```javascript
(function() {
  console.log("I run immediately!");
})();
```

Arrow function version:

```javascript
(() => {
  console.log("Also runs immediately!");
})();
```

**Why use an IIFE?**
- To run setup code once without polluting the global scope with extra variables.
- To create a private scope: variables inside the IIFE are not accessible outside it.

```javascript
const result = (function() {
  const secret = 42;  // not accessible outside
  return secret * 2;
})();

console.log(result);  // 84
console.log(secret);  // ReferenceError — secret is private
```

IIFEs are one situation where a semicolon before the expression is a good habit, to prevent JavaScript from misreading the previous line.

---

### Functions and the DOM: Click Handlers

Functions work perfectly as **event handlers** — code that runs when a user does something like click a button.

```html
<button id="greet-btn">Say Hello</button>
<p id="message"></p>

<script>
  function sayHello() {
    document.getElementById("message").textContent = "Hello there!";
  }

  document.getElementById("greet-btn").onclick = sayHello;
</script>
```

What happens:
1. `sayHello` is a regular function — it finds the `<p>` and changes its text.
2. `document.getElementById("greet-btn").onclick = sayHello` tells the browser: "when this button is clicked, call `sayHello`."

Notice there are NO parentheses after `sayHello` in the last line — you are handing the function itself to the browser, not calling it right away.

---

### Three Ways to Write a Function — Summary

```javascript
// Declaration
function add(a, b) {
  return a + b;
}

// Expression
const add = function(a, b) {
  return a + b;
};

// Arrow
const add = (a, b) => a + b;
```

All three create a function that takes two numbers and returns their sum. Choose the style that fits the situation — but be consistent within a project.

---

## Practice Quiz

Take the **Session 8 Practice Quiz** in Canvas before you start the assignment. It is ungraded and you can take it as many times as you like.

If you miss a question, re-read the Key Concepts section above, then try again.

---

## Wrap-Up

In this session you learned:

- A **function declaration** uses the `function` keyword and is hoisted.
- A **function expression** assigns a function to a variable and is not hoisted.
- An **arrow function** is a short form: `(param) => expression`.
- **Parameters** receive input values when the function is called.
- **Return** sends a value back to the caller.
- **Default parameters** provide a fallback when an argument is missing.
- **Scope** means variables inside a function are not visible outside it.
- **Recursion** means a function calling itself — always needs a base case.
- An **IIFE** runs immediately when defined — useful for setup code and private scope.
- Functions can be attached to DOM events like `onclick` to respond to user actions.

Next up is **Session 9: Higher-Order Array Methods**, where you will combine your array and function skills into some of the most powerful tools in JavaScript.

You are more than halfway through Credit 2. The best is yet to come.

{{include:session-footer}}

{{include:completion-checklist}}
