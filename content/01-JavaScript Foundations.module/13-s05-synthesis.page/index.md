---
name: "Session 5: Credit 1 Synthesis — Variables and Conditionals Project"
published: false
outcomes:
  - 03-ELEM
topics:
  - literals
  - variables
  - types
  - operators
  - strings
  - conditionals
---

[lead]You have covered four sessions of JavaScript foundations — now it is time to pull all of it together in one project that shows you can use variables, string methods, arithmetic, and conditional logic as a team.

# Session 5: Credit 1 Synthesis

This session is different from the others.

There is no new reading material and no new concepts. Instead, this session reviews everything from Sessions 1 through 4 and gives you a project that uses all of it in one place. You also have a graded quiz — the Credit 1 quiz — that counts toward your grade.

Take your time, use your notes, and review any Key Concepts sections you feel unsure about before you start.

---

## Video Tutorial

There is no new video for this session. If you want to review any concept, rewatch the relevant videos from Sessions 1–4 on the shared class drive.

---

## Key Concepts Review

This section summarizes every major idea from Credit 1. Use it as a study guide before the graded quiz and as a reference while you build the project.

---

### From Session 1 — Literals, Identifiers, and Variables

A **literal** is a value written directly in code: `42`, `"hello"`, `true`.

An **identifier** is a name. It must start with a letter, `$`, or `_`. Use camelCase: `firstName`, `totalScore`.

A **variable** is a named container declared with `let`, `const`, or `var`:

```javascript
const name = "Alex";   // const — won't change
let score = 0;         // let — will change
```

Use `const` by default. Switch to `let` only when the value needs to change. Avoid `var`.

`console.log()` prints values to the browser console.

---

### From Session 2 — Types and Operators

JavaScript's seven types: `number`, `string`, `boolean`, `undefined`, `null`, `object`, `symbol`.

`typeof` returns the type of a value as a string: `typeof 42` returns `"number"`.

**Arithmetic operators**: `+`, `-`, `*`, `/`, `%` (remainder), `**` (power).

**Operator precedence**: parentheses first, then `**`, then `*`, `/`, `%`, then `+`, `-`.

**Comparison operators** return `true` or `false`: use `===` and `!==` (not `==` and `!=`).

**Assignment shortcut operators**: `+=`, `-=`, `*=`, `/=`.

---

### From Session 3 — Strings, Numbers, and Code Style

**String methods**:

| Method | What it does |
|---|---|
| `.length` | Number of characters |
| `.toUpperCase()` | All uppercase |
| `.toLowerCase()` | All lowercase |
| `.trim()` | Remove leading and trailing spaces |
| `.includes(text)` | Returns true if text is found |
| `.slice(start, end)` | Returns a portion of the string |
| `.replace(old, new)` | Replaces first occurrence |

**Template literals**: backtick strings with `${}` for embedded expressions:

```javascript
let name = "Jordan";
console.log(`Hello, ${name}!`);   // "Hello, Jordan!"
```

**Math utilities**: `Math.round()`, `Math.floor()`, `Math.ceil()`, `Math.max()`, `Math.min()`.

**Code style rules**: semicolons end statements; JavaScript ignores extra white space; names are case-sensitive; use `//` for single-line comments and `/* */` for multi-line.

---

### From Session 4 — Conditional Logic

**if / else if / else** runs different code depending on a condition:

```javascript
if (score >= 90) {
  grade = "A";
} else if (score >= 80) {
  grade = "B";
} else {
  grade = "F";
}
```

**Logical operators**: `&&` (AND), `||` (OR), `!` (NOT).

**switch** compares one variable against multiple specific values — always use `break`:

```javascript
switch (color) {
  case "red":   console.log("Stop");  break;
  case "green": console.log("Go");    break;
  default:      console.log("Wait");
}
```

**Ternary operator**: `condition ? valueIfTrue : valueIfFalse`

```javascript
let label = age >= 18 ? "adult" : "minor";
```

---

## Practice Quiz

Take the **Session 5 Practice Quiz** in Canvas. It draws questions from all four Credit 1 sessions and is a good warm-up before the graded quiz.

After you finish the practice quiz, review any topics where you lost points — then take the **Credit 1 Graded Quiz** (item 16 in the module). You have one attempt on the graded quiz, so prepare carefully.

---

## Wrap-Up

Credit 1 has covered:

- Storing data in variables with literals and identifiers
- Understanding JavaScript types and using operators
- Manipulating strings and numbers with built-in methods
- Writing conditional logic that makes real decisions

In **Credit 2** you will learn about arrays (lists of data), loops (repeating code), and functions (reusable code blocks). These tools will let you write programs that handle real amounts of data.

You have made it through the foundations. That is a real accomplishment. The project for this session is your chance to show what you know — take your time and do it well.

{{include:session-footer}}

{{include:completion-checklist}}
