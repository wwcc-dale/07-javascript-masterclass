---
indent: 2
name: "Solution: Session 24 — ES Modules"
published: false
outcomes:
  - 04-MOD
topics:
  - es-modules
  - import-export
  - named-exports
  - default-exports
---

# Instructor Solution: Session 24 — ES Modules

> alert: warning
>
> This page is for instructor reference only. Keep unpublished until after the assignment deadline.

---

## Student Hint

> alert: tip
>
> In `utils.js`, put `export` before each function declaration. In `data.js`, put `export default` before the array. In `app.js`, use `import { functionName } from "./utils.js"` for named imports and `import data from "./data.js"` for the default import. In `index.html`, the script tag must use `type="module"`: `<script type="module" src="app.js"></script>`. Run through Live Server — modules do not work over `file://`.

---

## Full Solution

Four files are required. Each is shown separately below.

### `utils.js`

```javascript
// Named exports — each function can be imported by name

export function formatName(first, last) {
  return last + ", " + first;
}

export function clamp(value, min, max) {
  if (value < min) return min;
  if (value > max) return max;
  return value;
}

export function randomInt(min, max) {
  return Math.floor(Math.random() * (max - min + 1)) + min;
}
```

### `data.js`

```javascript
// Default export — array of person objects

const people = [
  { firstName: "Alex",   lastName: "Rivera",  age: 22, score: 178 },
  { firstName: "Jamie",  lastName: "Chen",    age: 19, score: 95  },
  { firstName: "Sam",    lastName: "Patel",   age: 25, score: 210 },
  { firstName: "Morgan", lastName: "Kim",     age: 21, score: 50  },
  { firstName: "Taylor", lastName: "Santos",  age: 23, score: 160 }
];

export default people;
```

### `app.js`

```javascript
// Main script — imports from utils.js and data.js, processes and logs data

import { formatName, clamp, randomInt } from "./utils.js";
import people from "./data.js";

// Step 5 — formatted names using map
const formatted = people.map(person => formatName(person.firstName, person.lastName));
console.log("People:");
console.log(formatted);
// Expected: ["Rivera, Alex", "Chen, Jamie", "Patel, Sam", "Kim, Morgan", "Santos, Taylor"]

// Step 6 — clamped scores (scores above 100 get clamped to 100)
const clamped = people.map(person => clamp(person.score, 0, 100));
console.log("Clamped scores:");
console.log(clamped);
// Expected: [100, 95, 100, 50, 100]

// Step 7 — three random ints
const r1 = randomInt(1, 10);
const r2 = randomInt(1, 10);
const r3 = randomInt(1, 10);
console.log("Three random ints:", r1, r2, r3);
```

### `index.html`

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Session 24 — ES Modules</title>
</head>
<body>
  <h1>ES Modules Demo</h1>
  <p>Open the browser console (F12) to see the output.</p>

  <!-- type="module" is required for import/export to work -->
  <script type="module" src="app.js"></script>
</body>
</html>
```

---

## Intermediate Stretch Solution

Add to `utils.js`:

```javascript
export function average(arr) {
  if (arr.length === 0) return 0;
  return arr.reduce((sum, n) => sum + n, 0) / arr.length;
}
```

Update `data.js` to add a named export alongside the default:

```javascript
export const MAX_SCORE = 200;

const people = [ /* ... same as above ... */ ];
export default people;
```

Update the import line in `app.js` and add:

```javascript
import { formatName, clamp, randomInt, average } from "./utils.js";
import people, { MAX_SCORE } from "./data.js";

// ... existing code ...

const avgScore = average(people.map(p => p.score));
console.log("Average score:", avgScore.toFixed(1));  // 138.6
console.log("Max possible score:", MAX_SCORE);        // 200
```

---

## Advanced Stretch Solution

Add to `utils.js`:

```javascript
export function groupBy(arr, key) {
  return arr.reduce((groups, item) => {
    const groupKey = item[key];
    if (!groups[groupKey]) groups[groupKey] = [];
    groups[groupKey].push(item);
    return groups;
  }, {});
}
```

In `app.js`:

```javascript
import { formatName, clamp, randomInt, average, groupBy } from "./utils.js";

const byAge = groupBy(people, "age");
console.log("People grouped by age:");
console.log(byAge);
// { '19': [{...}], '21': [{...}], '22': [{...}], '23': [{...}], '25': [{...}] }
```

---

## Instructor Notes

- **Core:** 4 files present (`utils.js`, `data.js`, `app.js`, `index.html`); `utils.js` uses named exports for `formatName`, `clamp`, `randomInt`; `data.js` default-exports the `people` array; `app.js` imports correctly; `type="module"` on the script tag; all three outputs logged correctly
- **Common mistake:** forgetting `type="module"` on the script tag — produces a SyntaxError on the import statement
- **Common mistake:** `import people from "./data.js"` written as `import { people } from "./data.js"` — curly braces are for named imports only
- **Common mistake:** file paths without `./` — `import { ... } from "utils.js"` may work in bundlers but fails in vanilla browser modules; must use `./utils.js`
- **Common mistake:** opening directly in browser over `file://` — modules block; must use Live Server
- **Intermediate:** `average()` handles empty array (returns 0), computes correctly for non-empty; `MAX_SCORE` exported as named export alongside the default; import line in `app.js` updated to `import people, { MAX_SCORE } from "./data.js"`
- **Advanced:** `groupBy(arr, key)` uses `reduce` with an object accumulator; result is a properly nested object; generic (any key, not hard-coded)

{{include:session-footer}}

{{include:completion-checklist}}
