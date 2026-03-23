---
name: "Session 2: Types and Operators"
published: true
outcomes:
  - 03-ELEM
topics:
  - types
  - operators
  - expressions
---

[lead]JavaScript needs to know what kind of data it is working with — and it needs tools to combine and compare that data. Types and operators are those tools, and understanding them will stop a whole category of bugs before they start.

# Session 2: Types and Operators

You already know how to store values in variables. Now you will learn what JavaScript does with those values.

Every value in JavaScript has a **type** — a category that tells JavaScript how to treat it. And **operators** are the symbols you use to do math, make comparisons, and combine values. These two ideas work together constantly in real programs.

---

## Video Tutorial

- video-tabs
- src: source/week 1/Day 1/Types.mp4 | Types
- src: source/week 1/Day 1/Operators.mp4 | Operators
- src: source/week 1/Day 1/Expressions.mp4 | Expressions
- src: source/week 1/Day 1/Operators precedence.mp4 | Precedence

Estimated viewing time: 15–20 minutes. Pause and type the examples yourself — open a browser, press F12, go to the Console tab, and try each snippet as you go.

---

## Key Concepts Review

### The Seven Types

JavaScript has seven basic data types. Every value belongs to exactly one of them.

| Type | What it is | Example |
|---|---|---|
| `number` | Any number, including decimals | `42`, `3.14`, `-7` |
| `string` | Text surrounded by quotes | `"hello"`, `'world'` |
| `boolean` | True or false only | `true`, `false` |
| `undefined` | A variable that has no value yet | `let x;` — x is undefined |
| `null` | Intentionally empty | `let result = null;` |
| `object` | A collection of key-value pairs | `{ name: "Alex" }` |
| `symbol` | A unique identifier (advanced — you will use this later) | — |

---

### The typeof Operator

`typeof` tells you what type a value is. It returns a string.

```javascript
typeof 42           // "number"
typeof "hello"      // "string"
typeof true         // "boolean"
typeof undefined    // "undefined"
typeof null         // "object"  ← this is a known JavaScript quirk
typeof { }          // "object"
```

> **Note:** `typeof null` returns `"object"` — this is a historical bug in JavaScript that was never fixed. Just remember it.

Use `typeof` when you are not sure what type a variable holds:

```javascript
let x = 99;
console.log(typeof x);   // "number"
```

---

### Arithmetic Operators

These operators do math on numbers.

| Operator | Name | Example | Result |
|---|---|---|---|
| `+` | Addition | `5 + 3` | `8` |
| `-` | Subtraction | `10 - 4` | `6` |
| `*` | Multiplication | `3 * 4` | `12` |
| `/` | Division | `15 / 3` | `5` |
| `%` | Modulus (remainder) | `10 % 3` | `1` |
| `**` | Exponentiation (power) | `2 ** 3` | `8` |

**Modulus** is especially useful for checking whether a number is even or odd:

```javascript
10 % 2   // 0 — no remainder, so 10 is even
7 % 2    // 1 — remainder of 1, so 7 is odd
```

---

### Operator Precedence (Order of Operations)

When an expression has multiple operators, JavaScript follows an order — just like math class.

The order is: **Parentheses → Exponentiation → Multiplication / Division / Modulus → Addition / Subtraction**

A handy way to remember: **PEMDAS** (Parentheses, Exponents, Multiplication, Division, Addition, Subtraction).

```javascript
2 + 3 * 4      // 14 — multiplication happens first: 3*4=12, then 2+12
(2 + 3) * 4   // 20 — parentheses first: 2+3=5, then 5*4
```

When in doubt, use parentheses to make your intent clear.

---

### Comparison Operators

Comparison operators compare two values and return a boolean (`true` or `false`).

| Operator | Meaning | Example | Result |
|---|---|---|---|
| `==` | Equal (value only) | `"5" == 5` | `true` |
| `===` | Strictly equal (value AND type) | `"5" === 5` | `false` |
| `!=` | Not equal (value only) | `"5" != 5` | `false` |
| `!==` | Strictly not equal | `"5" !== 5` | `true` |
| `<` | Less than | `3 < 5` | `true` |
| `>` | Greater than | `3 > 5` | `false` |
| `<=` | Less than or equal | `5 <= 5` | `true` |
| `>=` | Greater than or equal | `6 >= 5` | `true` |

**`==` vs `===` — this is important:**

- `==` checks if the values are equal but will convert types to compare. This can cause unexpected results.
- `===` checks if the values AND types are both equal. This is safer.

```javascript
"5" == 5    // true  — JavaScript converts "5" to a number before comparing
"5" === 5   // false — one is a string, the other is a number
```

**Rule of thumb: always use `===` and `!==` instead of `==` and `!=`.**

---

### Assignment Operators

You already know `=` (assign a value). There are also shortcut operators:

| Operator | Meaning | Example | Same as |
|---|---|---|---|
| `=` | Assign | `x = 5` | — |
| `+=` | Add and assign | `x += 3` | `x = x + 3` |
| `-=` | Subtract and assign | `x -= 2` | `x = x - 2` |
| `*=` | Multiply and assign | `x *= 4` | `x = x * 4` |
| `/=` | Divide and assign | `x /= 2` | `x = x / 2` |

```javascript
let score = 100;
score -= 10;
console.log(score);   // 90
```

---

### What is an Expression?

An **expression** is any piece of code that produces a value.

- `5 + 3` is an expression — it produces `8`
- `"hello" + " world"` is an expression — it produces `"hello world"`
- `age > 18` is an expression — it produces `true` or `false`

You can assign the result of any expression to a variable:

```javascript
let total = 10 + 5;         // 15
let isAdult = age >= 18;    // true or false
let greeting = "Hi " + name; // "Hi Alex"
```

---

## Practice Quiz

Take the **Session 2 Practice Quiz** in Canvas before you start the assignment. It is ungraded and you can take it as many times as you like.

Focus especially on the difference between `==` and `===`, and on operator precedence. These are common sources of confusion.

---

## Wrap-Up

In this session you learned:

- JavaScript has seven types: number, string, boolean, undefined, null, object, and symbol.
- `typeof` tells you what type a value is.
- Arithmetic operators (`+`, `-`, `*`, `/`, `%`, `**`) do math.
- Operator precedence follows PEMDAS — use parentheses when you want to control the order.
- Comparison operators return `true` or `false` — always prefer `===` over `==`.
- Assignment operators like `+=` are shortcuts for updating variable values.

Next up is **Session 3: Strings, Numbers, and Code Style**, where you will learn how to work with text and numbers using built-in JavaScript tools.

You are building real programming knowledge. Keep it up.

{{include:session-footer}}

{{include:completion-checklist}}
