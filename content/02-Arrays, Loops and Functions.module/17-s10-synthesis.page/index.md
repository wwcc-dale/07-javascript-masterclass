---
name: "Session 10: Credit 2 Synthesis — Arrays, Loops and Functions"
published: true
outcomes:
  - 03-ELEM
topics:
  - arrays
  - loops
  - functions
  - array-methods
  - higher-order-functions
---

[lead]This session brings together everything you have learned in Credit 2 — arrays, loops, functions, and higher-order methods — into one project that shows how these tools work together in a real program.

# Session 10: Credit 2 Synthesis

You have covered a lot of ground in Credit 2:

- **Session 6** — Arrays: storing and modifying lists
- **Session 7** — Loops: repeating code to work through lists
- **Session 8** — Functions: packaging code to reuse it
- **Session 9** — Higher-order methods: map, filter, reduce, find, sort

Now you will combine all four of these into a single program — a Student Grade Book. This is the kind of mini-application that could live inside a real school management system.

---

## Video Tutorial

No new videos for this session. If you want to review any concept, re-watch the relevant videos from the shared class drive:

- Arrays: `source/week 1/Day 2/`
- Loops: `source/week 1/Day 4/`
- Functions: `source/week 2/Day 1/`
- Higher-Order Methods: `source/week 2/Day 2/`

**Spend 10–15 minutes on any concept that feels unclear before you start the project.**

---

## Key Concepts Review

This section is a complete review of all Credit 2 topics. Read it even if you feel confident — it shows you how the pieces connect.

---

### Arrays — The Data Container

An **array** stores a list of values in one variable:

```javascript
const students = ["Alex", "Jordan", "Sam", "Taylor"];
```

You access items by index (starting at 0), check the length with `.length`, add with `push()`, and remove with `shift()` or `pop()`.

Arrays become much more useful when each item is an **object** (a set of related properties):

```javascript
const students = [
  { name: "Alex", scores: [85, 92, 78, 95] },
  { name: "Jordan", scores: [70, 68, 74, 80] },
  { name: "Sam", scores: [95, 98, 92, 100] }
];
```

Now each student has a name AND a set of scores. You can work with all students at once using loops and methods.

---

### Loops — Repeating Without Rewriting

A **for...of loop** steps through every item in an array:

```javascript
for (const student of students) {
  console.log(student.name);
}
```

A **for loop** is useful when you need the index:

```javascript
for (let i = 0; i < students.length; i++) {
  console.log(i + ": " + students[i].name);
}
```

Use loops when you need to do something **for each item** but the built-in array methods do not quite fit.

---

### Functions — Reusable Code Blocks

A **function** is a named block of code you can call many times:

```javascript
function average(scores) {
  const total = scores.reduce((sum, s) => sum + s, 0);
  return total / scores.length;
}

console.log(average([85, 92, 78, 95]));  // 87.5
```

Functions can call other methods inside them (like `reduce` above). Functions make your code readable — instead of seeing a pile of calculations, you see a meaningful name like `average`.

Arrow functions are a shorter form:

```javascript
const average = scores => scores.reduce((sum, s) => sum + s, 0) / scores.length;
```

---

### map — Transform Every Item

`map` returns a new array where each item has been transformed:

```javascript
const withAverages = students.map(student => ({
  name: student.name,
  average: average(student.scores)
}));
```

Here, `map` builds a new array where each item is an object with just the name and the calculated average. The original `students` array is unchanged.

---

### filter — Keep Only What You Need

`filter` returns a new array with only the items that pass a test:

```javascript
const passing = withAverages.filter(student => student.average >= 60);
```

This keeps only students whose average is 60 or above.

---

### reduce — Calculate a Single Value

`reduce` combines all items into one result:

```javascript
const classTotal = withAverages.reduce((sum, s) => sum + s.average, 0);
const classAverage = classTotal / withAverages.length;
```

---

### find — Get the First Match

`find` returns the first item that matches:

```javascript
const topStudent = withAverages.find(s => s.average >= 90);
```

---

### sort — Order the Array

`sort` reorders the array in place. For numbers, use a compare function:

```javascript
withAverages.sort((a, b) => b.average - a.average);  // highest first
```

---

### Putting It All Together — The Pattern

A common pattern in real JavaScript:

1. **Start with an array of data**
2. **Use map to compute derived values** (like averages)
3. **Use filter to narrow down** (like passing students)
4. **Use reduce to summarize** (like class average)
5. **Use a loop to output results** (like printing each student)

This is exactly what the Credit 2 project asks you to build.

---

## Practice Quiz

Take the **Session 10 Practice Quiz** in Canvas before you start the project. It is ungraded and you can take it as many times as you like.

The quiz covers all Credit 2 topics. If you miss questions, revisit the relevant session pages before taking the graded quiz.

---

## Wrap-Up

In Credit 2 you learned:

- **Arrays** store ordered lists and have powerful built-in methods.
- **Loops** let you repeat actions for every item in a list.
- **Functions** package code so you can reuse it with different inputs.
- **Higher-order methods** — map, filter, reduce, find, sort — let you work with arrays using functions as arguments.
- All four tools work together naturally in real programs.

The **Credit 2 Project** puts all of these skills to work. After the project you will take the **Credit 2 Graded Quiz** to confirm your understanding across all four sessions.

Next up in Credit 3 you will learn about **Objects, Classes, and the DOM** — and everything you learned in Credit 2 will be the foundation you build on.

You have done outstanding work. These are not beginner concepts — these are the real tools that professional JavaScript developers use every day. You are ready for the project.

{{include:session-footer}}

{{include:completion-checklist}}
