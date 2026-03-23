---
name: "Session 15: Credit 3 Synthesis — Objects, Classes, and Scope"
published: false
outcomes:
  - 02-OOP
topics:
  - objects
  - classes
  - scope
  - closures
  - synthesis
---

[lead]You have covered a lot of ground in Credit 3. This session brings it all together — reviewing what you have learned about objects, classes, and scope, showing how it connects to what came before, and preparing you for both the Library Catalog project and the Midterm Exam.

# Session 15: Credit 3 Synthesis

Before you build the Library Catalog project and sit the Midterm Exam, take time to look back at everything you have covered across all three credits. This session is your review, your checklist, and your launch pad.

---

## Reading Assignment

There is no new source material for this session. Review your notes, re-read any Key Concepts sections you feel less confident about, and look back at your completed assignments from Sessions 11–14.

If you want to review specific topics from Credits 1 and 2, revisit the pages for Sessions 1–9 as needed.

---

## Video Tutorial

There are no new videos for this session. If any topic from Sessions 11–14 is still unclear, rewatch the relevant videos from the shared class drive:

- `source/week 2/Day 3/` — Objects (s11, s12)
- `source/week 2/Day 4/` — Classes (s13)
- `source/week 3/Day 2/` — Scope and Closures (s14)

**Use this time to patch any gaps before the project and exam.**

---

## Key Concepts Review

### Credit 3 at a Glance

Here is everything you have learned in Credit 3, compressed for quick review.

---

#### Objects (Session 11)

An object stores related data as key-value pairs:

```javascript
const person = { name: "Alex", age: 28, city: "Walla Walla" };
```

- **Access:** `person.name` or `person["name"]`
- **Add property:** `person.email = "alex@example.com";`
- **Delete property:** `delete person.email;`
- **Check existence:** `"name" in person`  — returns `true`/`false`
- **Iterate:** `for (const key in person) { console.log(key, person[key]); }`
- **Get arrays:** `Object.keys(person)`, `Object.values(person)`, `Object.entries(person)`
- **Pass by reference:** When you assign an object to a new variable, both point to the same object. Changing one changes both.

---

#### Object Methods and Destructuring (Session 12)

A **method** is a function stored as a property:

```javascript
const dog = {
  name: "Rex",
  bark() { return this.name + " says: Woof!"; }
};
```

- `this` inside a method refers to the object the method belongs to.
- Arrow functions do NOT have their own `this` — do not use them as methods.

**Destructuring** pulls out properties into variables:

```javascript
const { name, age } = person;
```

**Spread** creates a shallow copy or merge:

```javascript
const copy = { ...person };
const merged = { ...a, ...b };
```

---

#### Classes (Session 13)

A class is a template for creating objects:

```javascript
class Rectangle {
  constructor(width, height) {
    this.width = width;
    this.height = height;
  }
  area() {
    return this.width * this.height;
  }
}

const r = new Rectangle(5, 3);
console.log(r.area());   // 15
```

- Class names start with a **capital letter**.
- `constructor` sets up instance properties using `this`.
- `new ClassName()` creates an instance.
- Methods are shared across all instances.

---

#### Scope and Closures (Session 14)

**Scope** determines where a variable can be accessed:

| Scope type | Keyword | Where accessible |
|---|---|---|
| Global | any | Everywhere |
| Function | `var` | Inside the function only |
| Block | `let`, `const` | Inside the `{}` block only |

**Shadowing:** An inner variable with the same name as an outer variable hides the outer one inside its scope.

**Hoisting:** `var` is hoisted and becomes `undefined`. `let`/`const` are in the TDZ and cannot be accessed before their declaration.

**Closure:** A function that remembers variables from its outer scope after that outer scope has finished:

```javascript
function makeCounter() {
  let count = 0;
  return {
    increment() { count++; return count; },
    reset()     { count = 0; return count; }
  };
}
const counter = makeCounter();
counter.increment(); // 1
counter.increment(); // 2
counter.reset();     // 0
```

---

### How Credit 3 Connects to Credits 1 and 2

Everything you learned in Credits 1 and 2 is a building block for Credit 3.

| Credit 1 & 2 topic | How it appears in Credit 3 |
|---|---|
| Variables (`let`, `const`) | Object properties, class fields, scope examples |
| Template literals | `describe()` and `summary()` methods |
| Conditionals | Inside methods (e.g., `isSquare()`, `isAdult()`) |
| Arrays | `Object.keys()`, arrays of instances, `filter`/`map` in project |
| Loops (`for...in`, `forEach`) | Iterating over objects and arrays of instances |
| Functions and parameters | Methods, constructors, closures |
| Array methods (`map`, `filter`, `forEach`) | The Library Catalog project uses all three |

---

### Credit 3 Project — Library Catalog Overview

In the assignment for this session, you will build a **Library Catalog** that combines:

- A `Book` **class** with properties and methods
- An **array** of Book instances
- **filter**, **map**, and **forEach** to work with the array
- An optional `Library` class (Intermediate) and a closure-based counter (Advanced)

Here is the class you will build:

```javascript
class Book {
  constructor(title, author, year, available) {
    this.title = title;
    this.author = author;
    this.year = year;
    this.available = available;
  }

  checkout() {
    this.available = false;
  }

  returnBook() {
    this.available = true;
  }

  describe() {
    const status = this.available ? "Available" : "Checked Out";
    return `"${this.title}" by ${this.author} (${this.year}) — ${status}`;
  }
}
```

Make sure you understand each part of this class before starting the assignment.

---

### Midterm Exam Overview

After the project, you will take the **Midterm Examination**, which covers Sessions 1–15. Here is what the exam includes:

| Topic | Sessions | Approx. questions |
|---|---|---|
| Literals, Variables, Types, Operators | 1–2 | 6 |
| Strings, Numbers, Conditionals | 3–4 | 6 |
| Arrays, Loops | 6–7 | 6 |
| Functions, Array Methods | 8–9 | 6 |
| Objects, Object Methods | 11–12 | 8 |
| Classes | 13 | 4 |
| Scope and Closures | 14 | 4 |
| Synthesis (mixed) | 15 | 8 |

**Total: 50 questions, 150 points, 90 minutes, 1 attempt.**

---

### How to Prepare

1. **Review your notes** from Sessions 1–14.
2. **Retake the practice quizzes** for any sessions where you feel shaky.
3. **Re-read** the Key Concepts sections for topics that are still unclear.
4. **Look at your past assignments** — the patterns you used there will show up on the exam.
5. **Focus extra time** on objects (Session 11), destructuring and spread (Session 12), classes (Session 13), and closures (Session 14) — these are the Credit 3 topics that carry the most exam weight.

---

## Practice Quiz

Take the **Session 15 Practice Quiz** in Canvas. It draws from the Session 15 synthesis bank and covers Credit 3 topics. It is ungraded and you can take it as many times as you like.

---

## Wrap-Up

In this credit you learned:

- How to create, modify, iterate, and reason about **objects** in JavaScript
- How to write **methods** and use `this` to connect a function to its object
- How to write cleaner, shorter code with **destructuring** and the **spread operator**
- How to use **classes** to create multiple objects from a shared template
- How **scope** controls where variables live — global, function, and block
- How **closures** let a function remember and protect variables from its outer scope

You are now more than halfway through this course. The Library Catalog project shows just how much you can do with what you know.

Take the Midterm Exam when you feel ready. Trust what you have practiced.

{{include:session-footer}}

{{include:completion-checklist}}
