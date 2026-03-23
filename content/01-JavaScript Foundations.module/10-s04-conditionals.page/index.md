---
name: "Session 4: Conditional Logic"
published: false
outcomes:
  - 03-ELEM
topics:
  - conditionals
  - if-else
  - switch
  - logical-operators
---

[lead]Every useful program makes decisions — show this page if the user is logged in, display a warning if the score is too low, greet the user by name if we know who they are. Conditional logic is how you give your programs the ability to choose, and today you will learn to write it.

# Session 4: Conditional Logic

Up to now your programs have run the same code every time. That changes today.

**Conditional logic** means your program can look at a value, ask a question about it, and run different code depending on the answer. This is one of the most powerful ideas in all of programming. Master it here and you will use it in every project you ever build.

---

## Video Tutorial

- video-tabs
- src: source/week 1/Day 3/Comparison operators.mp4 | Comparison Operators
- src: source/week 1/Day 3/`if` statements.mp4 | if Statements
- src: source/week 1/Day 3/How to use `else` .mp4 | Using else
- src: source/week 1/Day 3/Switch.mp4 | Switch
- src: source/week 1/Day 3/Nesting if statements.mp4 | Nesting if
- src: source/week 1/Day 3/More complex conditions.mp4 | Complex Conditions
- src: source/week 1/Day 3/The ternary operator.mp4 | Ternary Operator

Estimated viewing time: 20–25 minutes. Pause and try each example in the browser console — conditional logic clicks fastest when you run the code and watch which branch executes.

---

## Key Concepts Review

### The if Statement

An **if statement** runs a block of code only if a condition is `true`.

```javascript
let age = 20;

if (age >= 18) {
  console.log("You are an adult.");
}
```

The condition goes inside the parentheses `()`. The code to run goes inside the curly braces `{}`. If the condition is `false`, the block is skipped entirely.

---

### The else Clause

**else** runs when the `if` condition is `false`.

```javascript
let age = 15;

if (age >= 18) {
  console.log("You are an adult.");
} else {
  console.log("You are a minor.");
}
```

Only one of these two blocks will ever run — either the `if` block or the `else` block, never both.

---

### The else if Clause

Use **else if** to check multiple conditions in sequence.

```javascript
let score = 75;

if (score >= 90) {
  console.log("Grade: A");
} else if (score >= 80) {
  console.log("Grade: B");
} else if (score >= 70) {
  console.log("Grade: C");
} else {
  console.log("Grade: F");
}
```

JavaScript checks each condition from top to bottom and runs the first one that is `true`. Once a match is found, the rest are skipped.

---

### Nested if Statements

A **nested if** is an if statement inside another if statement. Use it when you need to check a second condition only after the first one passes.

```javascript
let age = 20;
let hasTicket = true;

if (age >= 18) {
  if (hasTicket) {
    console.log("Welcome in!");
  } else {
    console.log("You need a ticket.");
  }
} else {
  console.log("You must be 18 or older.");
}
```

Nesting works, but keep it shallow — too many levels deep becomes hard to read.

---

### Logical Operators

**Logical operators** let you combine conditions.

**`&&` (AND)** — Both conditions must be `true` for the whole expression to be `true`.

```javascript
let age = 20;
let hasTicket = true;

if (age >= 18 && hasTicket) {
  console.log("Welcome in!");
}
```

**`||` (OR)** — At least one condition must be `true`.

```javascript
let isAdmin = false;
let isOwner = true;

if (isAdmin || isOwner) {
  console.log("Access granted.");
}
```

**`!` (NOT)** — Flips a boolean. `true` becomes `false`, and `false` becomes `true`.

```javascript
let isLoggedIn = false;

if (!isLoggedIn) {
  console.log("Please log in.");
}
```

---

### The switch Statement

A **switch statement** is a clean alternative to long chains of `else if`. Use it when you are comparing one variable against many specific values.

```javascript
let day = "Monday";

switch (day) {
  case "Monday":
    console.log("Start of the week.");
    break;
  case "Friday":
    console.log("Almost the weekend!");
    break;
  case "Saturday":
  case "Sunday":
    console.log("It is the weekend!");
    break;
  default:
    console.log("It is a regular weekday.");
}
```

Each `case` is a value to match. The `break` keyword stops the switch after the matching case runs. The `default` case runs if no case matches — it is like the `else` at the end.

**Always remember the `break` keyword.** Without it, JavaScript will "fall through" and run the next case too.

---

### The Ternary Operator

The **ternary operator** is a one-line shortcut for a simple if/else.

Syntax: `condition ? valueIfTrue : valueIfFalse`

```javascript
let age = 20;
let status = age >= 18 ? "adult" : "minor";
console.log(status);   // "adult"
```

This is the same as:

```javascript
let status;
if (age >= 18) {
  status = "adult";
} else {
  status = "minor";
}
```

Use the ternary operator for simple, single-value decisions. Use a full if/else for anything more complex.

---

### Comparison Operators — Quick Review

You learned these in Session 2. Here is a quick reminder for use in conditions:

| Operator | Meaning |
|---|---|
| `===` | Strictly equal |
| `!==` | Strictly not equal |
| `<` | Less than |
| `>` | Greater than |
| `<=` | Less than or equal |
| `>=` | Greater than or equal |

Always use `===` instead of `==` in your conditions.

---

## Practice Quiz

Take the **Session 4 Practice Quiz** in Canvas before you start the assignment. It is ungraded and you can take it as many times as you like.

Focus on `&&` vs `||`, the `switch` structure, and the ternary operator — these are the trickiest parts of this session.

---

## Wrap-Up

In this session you learned:

- **if** runs a block only when a condition is true
- **else** runs when the condition is false
- **else if** chains multiple conditions — only the first matching block runs
- **Nested if** puts one if statement inside another
- **Logical operators**: `&&` (AND), `||` (OR), `!` (NOT) combine or flip conditions
- **switch** is a clean way to check one variable against many specific values — always use `break`
- **Ternary operator** is a one-line shortcut for simple if/else decisions

Next up is **Session 5: Credit 1 Synthesis**, where you bring all four sessions together in a single project. You have learned every concept you need. Now you get to show what you can do.

Excellent work making it through Credit 1 content. Conditional logic is a major milestone — keep it up.

{{include:session-footer}}

{{include:completion-checklist}}
