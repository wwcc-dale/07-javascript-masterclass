---
name: "Session 7: Loops"
published: true
outcomes:
  - 03-ELEM
topics:
  - loops
  - iteration
---

[lead]Loops are the reason computers never get tired — they can repeat the same action thousands of times in less than a second, and you only have to write the code once.

# Session 7: Loops

Imagine you have an array with 100 items and you need to print each one. You could write `console.log(array[0])`, then `console.log(array[1])`, all the way to `console.log(array[99])`. That would take forever.

Or you could write a loop — and let the computer do the repeating.

By the end of this session you will know how to write every major loop in JavaScript and choose the right one for each situation.

---

## Video Tutorial

- video-tabs
- src: source/week 1/Day 4/for.mp4 | for Loop
- src: source/week 1/Day 4/while.mp4 | while Loop
- src: source/week 1/Day 4/do..while.mp4 | do…while Loop
- src: source/week 1/Day 4/for..of.mp4 | for…of Loop

Estimated viewing time: 15–20 minutes. Type the code examples yourself as you watch — pay special attention to the conditions in each loop, since a single mistake can cause an infinite loop.

---

## Key Concepts Review

### What is a Loop?

A **loop** is a block of code that runs over and over until a condition says to stop. Every loop needs:

1. A **starting point** — where it begins
2. A **condition** — when to stop
3. An **action** — what to do each time through

---

### The for Loop

The **for loop** is the most common loop. Use it when you know exactly how many times you want to repeat.

```javascript
for (let i = 0; i < 5; i++) {
  console.log(i);
}
// prints: 0, 1, 2, 3, 4
```

The three parts inside the parentheses are separated by semicolons:

| Part | What it does | Example |
|---|---|---|
| `let i = 0` | Starting point — runs once at the beginning | Set counter to 0 |
| `i < 5` | Condition — checked before each loop | Stop when i reaches 5 |
| `i++` | Update — runs after each loop | Add 1 to i each time |

**Looping through an array with a for loop:**

```javascript
const colors = ["red", "green", "blue"];

for (let i = 0; i < colors.length; i++) {
  console.log(colors[i]);
}
// prints: red, green, blue
```

Using `colors.length` in the condition means the loop works no matter how long the array is.

---

### The while Loop

The **while loop** repeats as long as a condition is true. Use it when you do not know ahead of time how many times you will loop.

```javascript
let count = 0;

while (count < 5) {
  console.log(count);
  count++;
}
// prints: 0, 1, 2, 3, 4
```

**Important:** You must update the variable inside the loop (here, `count++`). If you forget, the condition never becomes false and the loop runs forever — this is called an **infinite loop**. The browser will freeze.

---

### The do...while Loop

The **do...while loop** is just like a while loop — but it always runs at least once. The condition is checked AFTER the first run.

```javascript
let count = 0;

do {
  console.log(count);
  count++;
} while (count < 5);
// prints: 0, 1, 2, 3, 4
```

Even if the condition starts as false, the code inside `do { }` runs one time:

```javascript
let x = 10;

do {
  console.log("This runs once even though x is 10");
} while (x < 5);
```

---

### The for...of Loop

The **for...of loop** is the cleanest way to loop through every item in an array. You do not need an index variable:

```javascript
const fruits = ["apple", "banana", "cherry"];

for (const fruit of fruits) {
  console.log(fruit);
}
// prints: apple, banana, cherry
```

On each pass through the loop, `fruit` holds the current item. The loop stops automatically when it runs out of items.

Use `const` for the loop variable since you are not reassigning it — `fruit` gets a fresh value each iteration.

**When you need the index too**, you can use the array's `entries()` method:

```javascript
const fruits = ["apple", "banana", "cherry"];

for (const [index, fruit] of fruits.entries()) {
  console.log(index, fruit);
}
// prints: 0 apple, 1 banana, 2 cherry
```

---

### The for...in Loop

The **for...in loop** iterates over the **keys** of an object. You will use it more in Credit 3 when you study objects, but here is what it looks like:

```javascript
const person = { name: "Alex", age: 25, city: "Auckland" };

for (const key in person) {
  console.log(key, person[key]);
}
// prints: name Alex, age 25, city Auckland
```

**Do not use for...in on arrays** — it is designed for objects. Use for...of for arrays.

---

### break and continue

**`break`** exits the loop immediately, even if the condition is still true:

```javascript
for (let i = 0; i < 10; i++) {
  if (i === 5) break;
  console.log(i);
}
// prints: 0, 1, 2, 3, 4  (stops when i hits 5)
```

**`continue`** skips the rest of the current iteration and moves to the next one:

```javascript
for (let i = 0; i < 6; i++) {
  if (i === 3) continue;
  console.log(i);
}
// prints: 0, 1, 2, 4, 5  (skips 3)
```

---

### Choosing the Right Loop

| Loop | Use when... |
|---|---|
| `for` | You know how many times to repeat |
| `while` | You do not know how many times — loop until a condition changes |
| `do...while` | You need the loop to run at least once no matter what |
| `for...of` | You want to visit every item in an array simply |
| `for...in` | You want to visit every key in an object |

---

## Practice Quiz

Take the **Session 7 Practice Quiz** in Canvas before you start the assignment. It is ungraded and you can take it as many times as you like.

If you miss a question, re-read the Key Concepts section above, then try again.

---

## Wrap-Up

In this session you learned:

- A **for loop** uses a counter and is great when you know how many times to repeat.
- A **while loop** keeps going as long as a condition is true.
- A **do...while loop** always runs at least once before checking the condition.
- A **for...of loop** is the cleanest way to step through every item in an array.
- A **for...in loop** steps through the keys of an object.
- `break` exits a loop early; `continue` skips one iteration.

Next up is **Session 8: Functions**, where you will learn how to wrap code in a reusable package so you can run it whenever you need it.

You are making great progress. Loops are something every programmer uses every single day — you now speak their language.

{{include:session-footer}}

{{include:completion-checklist}}
