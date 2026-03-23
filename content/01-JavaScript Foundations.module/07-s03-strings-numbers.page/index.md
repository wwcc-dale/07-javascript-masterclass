---
name: "Session 3: Strings, Numbers, and Code Style"
published: false
outcomes:
  - 03-ELEM
topics:
  - strings
  - numbers
  - code-style
  - template-literals
---

[lead]Strings and numbers are the data you will work with most often — and JavaScript gives you a powerful set of built-in tools for slicing, shaping, and transforming them. Learn these tools now and your programs will start feeling genuinely useful.

# Session 3: Strings, Numbers, and Code Style

You know how to store values and do basic math. Now you will learn how to actually work with that data.

JavaScript has built-in methods that let you manipulate strings — trim whitespace, change case, find text inside text, and cut sections out. It also has math utilities for rounding numbers and finding maximums and minimums. And it has a powerful feature called **template literals** that makes building text messages from variables clean and easy.

---

## Reading Assignment

Read the following files from the course materials on the shared class drive:

- `source/week 1/Day 1/11-Strings.html`
- `source/week 1/Day 1/12-Numbers.html`
- `source/week 1/Day 1/13-Semicolons.html`
- `source/week 1/Day 1/14-White space.html`
- `source/week 1/Day 1/15-Case sensitivity.html`
- `source/week 1/Day 1/16-Comments.html`

Pay close attention to the template literal syntax in the Strings file — backtick strings with `${}` inside them.

---

## Video Tutorial

- video-tabs
- src: source/week 1/Day 1/Semicolons.mp4 | Semicolons
- src: source/week 1/Day 1/White space.mp4 | White Space
- src: source/week 1/Day 1/Case sensitivity.mp4 | Case Sensitivity
- src: source/week 1/Day 1/Comments.mp4 | Comments

Estimated viewing time: 15–20 minutes. String and number methods are best understood by trying them in the browser console — open F12 and experiment with the examples below as you watch.

---

## Key Concepts Review

### String Methods

A **method** is a built-in function attached to a value. You call it by putting a dot after the value, then the method name and parentheses.

**`.length`** — Returns the number of characters in a string. (Note: length is a property, not a method — no parentheses needed.)

```javascript
let word = "hello";
console.log(word.length);   // 5
```

**`.toUpperCase()` and `.toLowerCase()`** — Convert all letters to uppercase or lowercase.

```javascript
let name = "alex";
console.log(name.toUpperCase());   // "ALEX"
console.log(name.toLowerCase());   // "alex"
```

**`.trim()`** — Removes whitespace (spaces, tabs) from the beginning and end of a string.

```javascript
let input = "  hello  ";
console.log(input.trim());   // "hello"
```

**`.includes()`** — Returns `true` if the string contains the specified text, `false` if it does not.

```javascript
let sentence = "I love JavaScript";
console.log(sentence.includes("love"));       // true
console.log(sentence.includes("Python"));     // false
```

**`.slice(start, end)`** — Returns a portion of the string. The `start` is the index of the first character you want (counting from 0). The `end` is where to stop (not included in the result).

```javascript
let text = "Hello, World!";
console.log(text.slice(0, 5));    // "Hello"
console.log(text.slice(7));       // "World!" — no end means go to the end
```

**`.replace(old, new)`** — Replaces the first occurrence of one string with another.

```javascript
let message = "I love cats";
console.log(message.replace("cats", "dogs"));   // "I love dogs"
```

---

### Template Literals

A **template literal** is a special kind of string written with backticks (`` ` ``) instead of quotes. Template literals can contain **embedded expressions** using `${}`.

Regular string concatenation (old way):

```javascript
let name = "Sam";
let age = 20;
console.log("My name is " + name + " and I am " + age + " years old.");
```

Template literal (better way):

```javascript
let name = "Sam";
let age = 20;
console.log(`My name is ${name} and I am ${age} years old.`);
```

Both produce the same output, but template literals are easier to read and write. You can put any expression inside `${}`:

```javascript
let a = 5;
let b = 3;
console.log(`The sum of ${a} and ${b} is ${a + b}.`);
// "The sum of 5 and 3 is 8."
```

---

### Number Methods and Math Object

JavaScript has built-in utilities for working with numbers.

**`Number.isInteger(value)`** — Returns `true` if the value is a whole number.

```javascript
Number.isInteger(42);     // true
Number.isInteger(3.14);   // false
```

**`Number.parseFloat(value)`** — Converts a string to a decimal number.

```javascript
Number.parseFloat("3.14");   // 3.14
Number.parseFloat("10px");   // 10 — stops at the first non-number character
```

**`Math.round(value)`** — Rounds to the nearest whole number.

```javascript
Math.round(4.6);   // 5
Math.round(4.4);   // 4
```

**`Math.floor(value)`** — Rounds down (toward negative infinity).

```javascript
Math.floor(4.9);   // 4
Math.floor(-2.1);  // -3
```

**`Math.ceil(value)`** — Rounds up (toward positive infinity).

```javascript
Math.ceil(4.1);    // 5
Math.ceil(-2.9);   // -2
```

**`Math.max(a, b, ...)`** — Returns the largest of the given numbers.

```javascript
Math.max(3, 7, 2, 9, 1);   // 9
```

**`Math.min(a, b, ...)`** — Returns the smallest of the given numbers.

```javascript
Math.min(3, 7, 2, 9, 1);   // 1
```

---

### Semicolons

Semicolons (`;`) end a JavaScript statement. They are **optional** in most cases — JavaScript can usually figure out where a statement ends. However, using semicolons is a good habit because:

- It makes your intent clear
- It prevents rare edge-case bugs
- Most professional JavaScript code uses them

Put a semicolon at the end of each statement:

```javascript
let x = 5;
let y = 10;
console.log(x + y);
```

---

### White Space

JavaScript ignores extra spaces and blank lines. These two blocks of code do exactly the same thing:

```javascript
let x=5;let y=10;console.log(x+y);
```

```javascript
let x = 5;
let y = 10;
console.log(x + y);
```

The second version is much easier to read. Use spaces around operators, indent inside blocks, and add blank lines between sections of code.

---

### Case Sensitivity

JavaScript is **case-sensitive**. This means `myVar`, `MyVar`, and `MYVAR` are three completely different variables.

```javascript
let myName = "Alex";
console.log(myname);   // ERROR — "myname" is not defined
console.log(myName);   // "Alex" — exact case required
```

This is a very common source of bugs. Always double-check the case of your variable names.

---

### Comments

Comments are notes in your code that JavaScript ignores. Use them to explain what your code does.

**Single-line comment** — starts with `//`

```javascript
// This calculates the total price
let total = price * quantity;
```

**Multi-line comment** — wrapped in `/* */`

```javascript
/*
  This section handles the greeting message.
  It uses a template literal to combine the name and city.
*/
let greeting = `Hello from ${city}!`;
```

Write comments for anything that is not immediately obvious. Your future self will thank you.

---

## Practice Quiz

Take the **Session 3 Practice Quiz** in Canvas before you start the assignment. It is ungraded and you can take it as many times as you like.

Pay particular attention to template literal syntax and string methods — these come up in the assignment.

---

## Wrap-Up

In this session you learned:

- String methods: `.length`, `.toUpperCase()`, `.toLowerCase()`, `.trim()`, `.includes()`, `.slice()`, `.replace()`
- Template literals: backtick strings with `${}` to embed expressions
- Number utilities: `Math.round()`, `Math.floor()`, `Math.ceil()`, `Math.max()`, `Math.min()`
- Semicolons end statements — use them for clarity
- JavaScript is case-sensitive — `myVar` and `myvar` are different
- Comments (`//` and `/* */`) explain your code and are ignored by JavaScript

Next up is **Session 4: Conditional Logic**, where you will teach your programs to make decisions — one of the most powerful things a program can do.

You are getting comfortable with the tools. Keep practicing and things will click faster each session.

{{include:session-footer}}

{{include:completion-checklist}}
