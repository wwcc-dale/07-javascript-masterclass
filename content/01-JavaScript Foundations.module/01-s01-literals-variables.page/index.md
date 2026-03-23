---
name: "Session 1: Literals, Identifiers, and Variables"
published: false
outcomes:
  - 03-ELEM
topics:
  - literals
  - identifiers
  - variables
---

[lead]Every program you will ever write starts with data — and data starts with literals, identifiers, and variables. Master these three ideas today and you have the foundation for everything else in JavaScript.

# Session 1: Literals, Identifiers, and Variables

You are writing your first real JavaScript today.

By the end of this session you will know how to store information in a program, give that information a name, and read it back. These are the building blocks of every JavaScript program ever written — no matter how big or complex.

---

## Reading Assignment

Read the following files from the course materials on the shared class drive. They are short HTML pages you can open in a browser:

- `source/week 1/Day 1/01-Literals.html`
- `source/week 1/Day 1/02-Identifiers.html`
- `source/week 1/Day 1/03-Variables.html`
- `source/week 1/Day 1/04-Declaring variables.html`
- `source/week 1/Day 1/05-The difference with let, const, var.html`
- `source/week 1/Day 1/13-Semicolons.html`
- `source/week 1/Day 1/14-White space.html`
- `source/week 1/Day 1/15-Case sensitivity.html`
- `source/week 1/Day 1/16-Comments.html`

Read each page once. Do not worry if everything does not click right away. The Key Concepts section below explains everything in plain language.

---

## Video Tutorial

- video-tabs
- src: source/week 1/Day 1/Literals.mp4 | Literals
- src: source/week 1/Day 1/Variables.mp4 | Variables
- src: source/week 1/Day 1/Declaring variables.mp4 | Declaring Variables
- src: source/week 1/Day 1/Difference let-const-var.mp4 | let vs const vs var

Estimated viewing time: 15–20 minutes. As you watch, follow along by typing the code examples yourself in the browser console — watching and typing together helps you remember much better than watching alone.

---

## Key Concepts Review

### What is a Literal?

A **literal** is a value you write directly in your code. It is not stored anywhere yet — it is just a raw value sitting right there in the program.

Examples of literals:

```javascript
42          // a number literal
"hello"     // a string literal (text in quotes)
true        // a boolean literal (true or false)
```

Think of a literal like writing a number on a sticky note. You have the value, but you have not labeled the note yet.

---

### What is an Identifier?

An **identifier** is a name. You use identifiers to label things in your code — like naming a variable, a function, or a class.

Rules for identifiers:
- Must start with a letter, a dollar sign (`$`), or an underscore (`_`)
- Cannot start with a number
- Cannot contain spaces
- Cannot be a reserved word (like `let`, `if`, `return`)

Valid identifiers:

```javascript
age
firstName
_count
$price
myFavoriteColor
```

Invalid identifiers:

```javascript
1stPlace     // starts with a number — not allowed
my name      // spaces not allowed
let          // reserved word — not allowed
```

**Naming convention:** JavaScript programmers use **camelCase** — start with a lowercase letter, and capitalize the first letter of each new word. Example: `myFavoriteColor`, `firstName`, `totalScore`.

---

### What is a Variable?

A **variable** is a named container for a value. You give it a name (identifier) and put a value (literal or expression) inside it. You can refer to that name later to get the value back.

Think of a variable like a labeled box. You write a name on the outside, put something inside, and you can open the box later to see what is in it.

---

### Declaring Variables: let, const, and var

There are three keywords for declaring a variable in JavaScript. You will use two of them regularly.

**`let`** — Use this when the value might change later.

```javascript
let score = 0;
score = 10;    // this is fine — let allows reassignment
```

**`const`** — Use this when the value will NOT change.

```javascript
const pi = 3.14159;
pi = 3;        // ERROR — const does not allow reassignment
```

**`var`** — The old way. You will see it in older code, but you should avoid it in new code. Use `let` or `const` instead.

**When to use which:**
- Use `const` by default.
- Switch to `let` only if you know the value will need to change.
- Avoid `var`.

---

### Declaring and Assigning

**Declaring** a variable means creating it and giving it a name.
**Assigning** means giving it a value.

You can do both at the same time:

```javascript
let age = 25;
```

Or separately:

```javascript
let age;       // declared, but no value yet (it is "undefined")
age = 25;      // now it has a value
```

With `const`, you must assign a value when you declare it:

```javascript
const city = "Auckland";   // correct
const name;                // ERROR — const must be initialized
```

---

### Reading Variable Values

Once a variable is declared, you can use its name anywhere you would use the value:

```javascript
let color = "blue";
console.log(color);      // prints: blue

let a = 5;
let b = 3;
let total = a + b;
console.log(total);      // prints: 8
```

`console.log()` is how you print values to the browser console so you can see what is happening in your code.

---

### Adding Labels to console.log()

When you log several values, it helps to include a label so you know which value is which. You can join a text label and a variable together using `+`:

```javascript
let score = 95;
let subject = "Math";

console.log("Subject: " + subject);  // prints: Subject: Math
console.log("Score: " + score);      // prints: Score: 95
```

The `+` symbol joins things together when one of them is text. This is called **concatenation**. You will learn much more about it in Session 3 — for now, just know that `"Label: " + variableName` is a handy way to make your console output readable.

---

### Code Style: Comments, Semicolons, and Whitespace

Good code is easy to read — for your teammates, and for future-you. A few simple habits make a big difference.

**Comments** let you leave notes in your code. JavaScript ignores them completely — they are just for people.

```javascript
// This is a single-line comment. Everything after // is ignored.

let price = 9.99;  // you can put a comment at the end of a line too

/*
  This is a multi-line comment.
  Useful for longer explanations.
  Everything between the slash-star markers is ignored.
*/
```

**Semicolons** are optional in JavaScript. The interpreter is smart enough to add them for you in most cases. You will see code both with and without them — either style works. Pick one and stay consistent.

```javascript
let x = 5    // no semicolon — fine
let y = 10;  // with semicolon — also fine
```

**Whitespace** (spaces, blank lines, indentation) does not affect how JavaScript runs. But consistent indentation makes code far easier to read. Convention: use 2 spaces to indent inside a block.

**Case sensitivity** — JavaScript treats capital and lowercase letters as completely different. A variable named `score` is NOT the same as `Score` or `SCORE`. Always be consistent with your naming.

```javascript
let score = 100;
let Score = 200;   // this is a completely different variable
console.log(score);  // 100
console.log(Score);  // 200
```

---

### Putting It in a Web Page

So far you have been using `console.log()` to see your results. You can also display JavaScript output directly on a web page using the **DOM** (Document Object Model) — the browser's way of letting JavaScript interact with HTML.

Here is the simplest way. In your HTML file:

```html
<p id="output">Result goes here</p>

<script>
  const name = "Alex";
  document.getElementById("output").textContent = "Hello, " + name + "!";
</script>
```

What happens:
1. The HTML creates a `<p>` tag with the id `"output"`.
2. `document.getElementById("output")` finds that element on the page.
3. `.textContent = ...` replaces whatever text is inside it.

The page now shows: **Hello, Alex!**

You will use this pattern throughout the course. For now, `console.log()` is fine — but try the DOM version when you feel ready.

---

### Quick Summary Table

| Keyword | Can be reassigned? | Must be initialized? | Use when... |
|---|---|---|---|
| `const` | No | Yes | Value stays the same |
| `let` | Yes | No | Value may change |
| `var` | Yes | No | Old code only — avoid |

---

## Practice Quiz

Take the **Session 1 Practice Quiz** in Canvas before you start the assignment. It pulls questions from the Session 1 question bank and is ungraded — you can take it as many times as you like.

The quiz checks your understanding of literals, identifiers, and variable declarations. If you miss a question, re-read the Key Concepts section above, then try again.

---

## Wrap-Up

In this session you learned:

- A **literal** is a raw value written directly in code — like `42` or `"hello"`.
- An **identifier** is a name — it follows rules like starting with a letter and using camelCase.
- A **variable** is a named container — declared with `let`, `const`, or `var`.
- `const` is for values that do not change; `let` is for values that do.
- `console.log()` prints values so you can see them.
- **Comments** (`//` and `/* */`) annotate your code — JavaScript ignores them.
- **Semicolons** are optional; **whitespace** is flexible; **JavaScript is case sensitive**.
- You can display JavaScript output in a web page using `document.getElementById()` and `.textContent`.

Next up is **Session 2: Types and Operators**, where you will learn what kinds of values JavaScript understands and how to combine and compare them.

You are off to a great start. Every professional JavaScript developer knows exactly what you just learned. Keep going.

{{include:session-footer}}

{{include:completion-checklist}}
