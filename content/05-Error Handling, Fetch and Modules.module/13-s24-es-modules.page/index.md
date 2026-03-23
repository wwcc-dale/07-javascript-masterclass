---
name: "Session 24: ES Modules"
published: true
outcomes:
  - 04-MOD
topics:
  - es-modules
  - import-export
  - named-exports
  - default-exports
  - module-structure
---

[lead]As projects grow, keeping all your JavaScript in one file gets messy. ES Modules let you split your code into logical pieces that share with each other — and today you will learn exactly how.

# Session 24: ES Modules

Every file you have written so far has been one big script. That works fine for small projects. But real applications have dozens or hundreds of files, each with a clear job. ES Modules are how modern JavaScript organizes that code.

By the end of this session you will know how to export values from one file and import them in another, the difference between named and default exports, how to use modules in HTML, and how to structure a multi-file project.

---

## Video Tutorial

There are no recorded videos for this session. Work through the reading files on the shared class drive and use the Key Concepts section below as your primary reference.

> alert: tip
>
> The best way to understand modules is hands-on: create two `.js` files, export something from one, and import it in the other. Load the main file with `<script type="module">` and open the console to see it work. You will need to run your HTML through a local server (VS Code Live Server or similar) rather than opening the file directly — browsers block module imports over `file://`.

---

## Key Concepts Review

### What Is a Module?

A **module** is a JavaScript file that explicitly shares (exports) some of its values and can use (import) values from other modules. Without modules, every script on a page shares the same global scope — meaning any two scripts can accidentally overwrite each other's variables. Modules fix this: each module has its own private scope, and only the things you export are visible to others.

Benefits of modules:
- **Organization** — each file has a clear, focused job
- **No name collisions** — a variable `count` in one module does not conflict with `count` in another
- **Reusability** — a helper function written once can be imported anywhere it is needed

---

### Named Exports

A **named export** is when you export a specific value by name. Other files import it using the same name.

**In `math.js`:**
```javascript
export const PI = 3.14159;

export function add(a, b) {
  return a + b;
}

export function multiply(a, b) {
  return a * b;
}
```

**In `app.js`:**
```javascript
import { PI, add, multiply } from "./math.js";

console.log(PI);           // 3.14159
console.log(add(2, 3));    // 5
console.log(multiply(4, 5)); // 20
```

You can also export all at once at the bottom of the file:

```javascript
const PI = 3.14159;
function add(a, b) { return a + b; }

export { PI, add };  // named exports at the bottom
```

---

### Default Exports

A **default export** is a single value that represents the "main thing" a module provides. Each file can only have one default export.

**In `formatter.js`:**
```javascript
export default function formatName(first, last) {
  return last + ", " + first;
}
```

**In `app.js`:**
```javascript
import formatName from "./formatter.js";
// Note: no curly braces for default imports

console.log(formatName("Alex", "Rivera"));  // Rivera, Alex
```

When you import a default export, you can choose any name you like:

```javascript
import myFormatter from "./formatter.js";   // still works
```

---

### Named vs. Default — When to Use Each

| | Named Export | Default Export |
|---|---|---|
| How many per file | As many as you want | Only one |
| Import syntax | `import { name }` — curly braces required | `import name` — no curly braces |
| Rename on import | `import { add as sum }` | Any name you choose |
| Best for | Utilities, constants, multiple functions | The main purpose of the file |

Use **named exports** for utility files that export several things. Use a **default export** for the main function or class a module provides.

---

### Import All

You can import everything a module exports under a single namespace:

```javascript
import * as MathUtils from "./math.js";

console.log(MathUtils.PI);         // 3.14159
console.log(MathUtils.add(2, 3));  // 5
```

This is useful when you need many things from one module and do not want a long import list.

---

### Using Modules in HTML

To load a module in HTML, you must add `type="module"` to the script tag:

```html
<script type="module" src="app.js"></script>
```

Without `type="module"`, the browser will not treat the file as a module and `import` statements will throw an error.

**Important rules when using modules in the browser:**
- You must use `type="module"` on the entry-point script
- File paths in `import` statements must include the file extension (`.js`)
- Use relative paths starting with `./` for files in the same folder
- Modules only work over HTTP or HTTPS — not with `file://` in most browsers. Use a local server.

---

### Modules Are Strict Mode by Default

Any code inside a module automatically runs in **strict mode** — the same as putting `"use strict";` at the top. This means:

- Variables must be declared with `let`, `const`, or `var` — no accidental globals
- Some unsafe JavaScript behaviors are disabled
- Errors are thrown instead of silently failing

---

### A Typical Multi-File Project Structure

Here is a common way to organize a small JavaScript project with modules:

```
project/
├── index.html       — loads app.js as a module
├── app.js           — the main script; imports from utils and data
├── utils.js         — helper functions; exports named functions
└── data.js          — constants and data; exports named values
```

`utils.js` might look like:

```javascript
export function clamp(value, min, max) {
  return Math.max(min, Math.min(max, value));
}

export function randomInt(min, max) {
  return Math.floor(Math.random() * (max - min + 1)) + min;
}
```

`data.js` might look like:

```javascript
export const COLORS = ["red", "green", "blue"];

export default [
  { id: 1, name: "Widget A" },
  { id: 2, name: "Widget B" }
];
```

`app.js` imports from both:

```javascript
import { clamp, randomInt } from "./utils.js";
import products, { COLORS } from "./data.js";
// ^ imports the default export AND a named export from the same file

console.log(clamp(150, 0, 100));  // 100
console.log(COLORS[0]);           // red
console.log(products[0].name);    // Widget A
```

---

### Re-Exporting

You can re-export something from another module without using it yourself. This is useful for creating a single "barrel" file that collects exports from several files:

```javascript
// index.js — re-exports from multiple places
export { add, multiply } from "./math.js";
export { formatName } from "./formatter.js";
```

Now other files can import everything from `index.js` without knowing how many files are involved behind the scenes.

---

### Circular Imports — Avoid These

A **circular import** is when Module A imports from Module B, and Module B also imports from Module A. JavaScript can sometimes handle this, but it is a sign of poor organization and often causes confusing bugs. If you notice two files importing from each other, reorganize your code so the shared logic lives in a third file that both can import from.

---

### Quick Reference

```javascript
// Named export
export const PI = 3.14;
export function add(a, b) { return a + b; }

// Default export
export default function main() { }

// Named import
import { PI, add } from "./math.js";

// Default import
import main from "./main.js";

// Both at once
import main, { PI, add } from "./main.js";

// Import all as namespace
import * as MathUtils from "./math.js";

// HTML: load entry-point as module
// <script type="module" src="app.js"></script>
```

---

## Practice Quiz

Take the **Session 24 Practice Quiz** in Canvas before you start the assignment. It is ungraded and you can take it as many times as you like.

The quiz checks your understanding of named exports, default exports, import syntax, and module structure. If you miss a question, re-read the Key Concepts section above.

---

## Wrap-Up

In this session you learned:

- A module is a JavaScript file that explicitly exports and imports values
- **Named exports** can be many per file; imported with curly braces
- **Default export** is one per file; imported without curly braces
- `type="module"` on the `<script>` tag is required to use modules in HTML
- Modules run in strict mode automatically
- Multi-file projects use modules to keep code organized and prevent naming conflicts
- Re-exporting lets you collect exports from multiple files into one entry point
- Avoid circular imports

Next up is **Session 25: Credit 5 Synthesis**, where you will bring together error handling, fetch, and modules in one final project.

You now know how professional JavaScript applications are organized. That is a big deal.

{{include:session-footer}}

{{include:completion-checklist}}
