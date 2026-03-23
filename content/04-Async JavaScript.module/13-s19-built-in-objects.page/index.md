---
name: "Session 19: Built-in Objects"
published: true
outcomes:
  - 04-MOD
topics:
  - math-object
  - date-object
  - json
  - set
  - map
  - string-methods
  - number-methods
---

[lead]JavaScript comes with a set of built-in objects that handle common tasks — math, dates, data storage, and more. You do not need to install anything or write these from scratch. They are already there, waiting for you to use them.

# Session 19: Built-in Objects

You already know strings, arrays, and objects from earlier credits. Today you go deeper into the tools JavaScript gives you for free: `Math`, `Date`, `JSON`, advanced string and number methods, `Set`, and `Map`.

By the end of this session you will be able to generate random numbers, work with dates, convert data to and from JSON, use string and number utility methods, and store unique values or key-value pairs with `Set` and `Map`.

---

## Video Tutorial

There are no recorded videos for this session. Work through the reading files on the shared class drive and use the Key Concepts section below as your primary reference. The browser console (F12) is your best tool for experimenting with each built-in object as you read.

This is a longer set of videos — take breaks as needed. Type each example as you watch.

---

## Key Concepts Review

### The Math Object

`Math` is a built-in object with mathematical constants and functions. You do not create an instance of it — you just use it directly.

**Commonly used Math methods:**

```javascript
Math.PI                     // 3.141592653589793
Math.abs(-7)                // 7 (absolute value)
Math.round(4.6)             // 5 (rounds to nearest integer)
Math.floor(4.9)             // 4 (rounds down)
Math.ceil(4.1)              // 5 (rounds up)
Math.max(3, 7, 2)           // 7 (largest value)
Math.min(3, 7, 2)           // 2 (smallest value)
Math.sqrt(16)               // 4 (square root)
Math.random()               // a random decimal between 0 and 1 (never equals 1)
```

**Generating a random integer between 1 and N:**

```javascript
function randomInt(max) {
  return Math.floor(Math.random() * max) + 1;
}

console.log(randomInt(6));   // random number from 1 to 6 (like a dice roll)
```

The formula `Math.floor(Math.random() * max) + 1` is one of the most common patterns in JavaScript.

---

### The Date Object

`new Date()` creates a Date object representing the current date and time.

```javascript
const now = new Date();
console.log(now);   // something like: Mon Mar 23 2026 09:15:00 GMT+1300
```

**Getting parts of a date:**

```javascript
const d = new Date();
d.getFullYear()      // e.g., 2026
d.getMonth()         // 0 to 11 — January is 0, December is 11 (watch out!)
d.getDate()          // 1 to 31 — the day of the month
d.getDay()           // 0 to 6 — Sunday is 0, Saturday is 6
d.getHours()         // 0 to 23
d.getMinutes()       // 0 to 59
```

**Formatting a date for display:**

```javascript
const d = new Date();
console.log(d.toLocaleDateString());    // e.g., "3/23/2026"
console.log(d.toLocaleTimeString());    // e.g., "9:15:00 AM"
console.log(d.toLocaleString());        // date and time together
```

**Warning:** `getMonth()` returns 0-based numbers. January is `0`, not `1`. Always add 1 if you need to display the month number.

```javascript
const month = d.getMonth() + 1;   // now January = 1, December = 12
```

---

### JSON — JavaScript Object Notation

JSON is a text format for storing and sharing data. It looks like JavaScript objects and arrays, but it is a string.

**`JSON.stringify(value)`** — converts a JavaScript value to a JSON string:

```javascript
const person = { name: "Alex", age: 20 };
const jsonString = JSON.stringify(person);
console.log(jsonString);         // '{"name":"Alex","age":20}'
console.log(typeof jsonString);  // "string"
```

**`JSON.parse(string)`** — converts a JSON string back to a JavaScript value:

```javascript
const data = JSON.parse('{"name":"Alex","age":20}');
console.log(data.name);   // "Alex"
console.log(data.age);    // 20
```

**Why JSON matters:** You will use JSON constantly when saving data (to localStorage, files, or a server) and when receiving data back. It is the most common data exchange format on the web.

**Pretty-print JSON** (easier to read):

```javascript
console.log(JSON.stringify(person, null, 2));
// {
//   "name": "Alex",
//   "age": 20
// }
```

---

### String Methods Deep Dive

You already know `.length`, `.toUpperCase()`, `.toLowerCase()`, `.trim()`, `.includes()`, `.indexOf()`, `.slice()`. Here are more:

```javascript
const str = "hello world";

// Split a string into an array
str.split(" ")               // ["hello", "world"]
str.split("")                // ["h", "e", "l", "l", "o", " ", "w", "o", "r", "l", "d"]

// Join an array into a string (Array method, but pairs with split)
["hello", "world"].join("-")  // "hello-world"

// Repeat a string
"ha".repeat(3)               // "hahaha"

// Check start or end
"hello".startsWith("he")     // true
"hello".endsWith("lo")       // true

// Pad a string to a fixed length
"7".padStart(3, "0")         // "007"
"hi".padEnd(5, ".")          // "hi..."
```

---

### Number Methods

```javascript
const n = 3.14159;
n.toFixed(2)                  // "3.14" — rounds to 2 decimal places, returns a string

parseInt("42px")              // 42 — extracts the integer from a string
parseFloat("3.14abc")         // 3.14 — extracts the float from a string

Number.isNaN(NaN)             // true — checks if a value is NaN (not a number)
Number.isNaN(42)              // false
Number.isFinite(100)          // true
Number.isFinite(Infinity)     // false
```

**Note:** `parseInt` and `parseFloat` are global functions, not methods on a number. Use them to turn strings into numbers safely.

---

### Set — Unique Values Only

A `Set` is a collection of values where every value must be unique. Duplicates are silently ignored.

```javascript
const mySet = new Set([1, 2, 2, 3, 3, 3]);
console.log(mySet);      // Set { 1, 2, 3 }
console.log(mySet.size); // 3

mySet.add(4);            // Set { 1, 2, 3, 4 }
mySet.has(2);            // true
mySet.delete(2);         // Set { 1, 3, 4 }
```

**Common use case — removing duplicates from an array:**

```javascript
const numbers = [1, 2, 2, 3, 3, 3, 4];
const unique = [...new Set(numbers)];
console.log(unique);   // [1, 2, 3, 4]
```

The spread operator (`...`) converts the Set back to an array.

---

### Map — Any Type as a Key

A `Map` stores key-value pairs, just like a regular object. The big difference: **Map keys can be any type** — numbers, objects, functions, or strings.

```javascript
const myMap = new Map();

myMap.set("name", "Alex");
myMap.set(42, "the answer");
myMap.set(true, "yes");

myMap.get("name");     // "Alex"
myMap.get(42);         // "the answer"
myMap.has("name");     // true
myMap.size;            // 3
myMap.delete(42);
```

**Iterating over a Map:**

```javascript
myMap.forEach((value, key) => {
  console.log(key, "→", value);
});
```

**Common use case — word frequency counter:**

```javascript
const words = ["cat", "dog", "cat", "bird", "dog", "cat"];
const freq = new Map();

for (const word of words) {
  freq.set(word, (freq.get(word) || 0) + 1);
}

console.log(freq.get("cat"));   // 3
console.log(freq.get("dog"));   // 2
```

---

## Practice Quiz

Take the **Session 19 Practice Quiz** in Canvas before you start the assignment. It is ungraded and you can take it as many times as you like.

The quiz covers `Math`, `Date`, `JSON`, string methods, number methods, `Set`, and `Map`. If you miss a question, re-read the Key Concepts section above.

---

## Wrap-Up

In this session you learned:

- **Math**: `Math.random()`, `Math.floor()`, `Math.round()`, `Math.max/min/abs/sqrt`, `Math.PI`
- **Date**: `new Date()`, `.getFullYear/Month/Date()` (month is 0-indexed!), `.toLocaleDateString()`
- **JSON**: `JSON.stringify()` converts object to string; `JSON.parse()` converts string back to object
- **String methods**: `split()`, `repeat()`, `startsWith()`, `endsWith()`, `padStart()`, `padEnd()`
- **Number methods**: `toFixed()`, `parseInt()`, `parseFloat()`, `Number.isNaN()`, `Number.isFinite()`
- **Set**: stores unique values; perfect for removing duplicates
- **Map**: stores key-value pairs where keys can be any type

Next up is **Session 20: Credit 4 Synthesis**, where you will put everything from this credit together into a single project.

You have covered a lot of ground this credit. You are well prepared for the project.

{{include:session-footer}}

{{include:completion-checklist}}
