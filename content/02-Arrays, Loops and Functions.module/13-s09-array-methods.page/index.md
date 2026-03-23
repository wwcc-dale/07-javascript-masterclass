---
name: "Session 9: Higher-Order Array Methods"
published: true
outcomes:
  - 03-ELEM
topics:
  - array-methods
  - higher-order-functions
  - callbacks
---

[lead]Higher-order array methods are some of the most powerful tools in JavaScript — they let you transform, filter, and summarize arrays in just one or two lines of code that would otherwise take a whole loop.

# Session 9: Higher-Order Array Methods

You now know how to create arrays, how to write functions, and how to loop. This session brings all three together.

JavaScript has built-in array methods that take a **function** as an argument and apply it to every item in the array. These are called **higher-order methods** because they accept functions as input. They replace many common loop patterns with cleaner, more readable code.

By the end of this session you will know how to use `forEach`, `map`, `filter`, `find`, `reduce`, and `sort`.

---

## Video Tutorial

- video-tabs
- src: source/week 2/Day 2/map().mp4 | map()
- src: source/week 2/Day 2/filter().mp4 | filter()
- src: source/week 2/Day 2/reduce().mp4 | reduce()
- src: source/week 2/Day 2/find().mp4 | find()
- src: source/week 2/Day 2/sort().mp4 | sort()

Estimated viewing time: 20–25 minutes. Copy the code examples and run them yourself as you watch — these methods can feel abstract until you see them produce output in real code.

---

## Key Concepts Review

### What is a Higher-Order Function?

A **higher-order function** is a function that accepts another function as an argument. The function you pass in is called a **callback** — because the method "calls it back" for each item in the array.

You already know how to write functions. Passing them as arguments is the only new idea here.

```javascript
const numbers = [1, 2, 3, 4, 5];

// Traditional loop
for (const n of numbers) {
  console.log(n);
}

// Higher-order method — same result, less code
numbers.forEach(n => console.log(n));
```

---

### forEach

`forEach` runs a function once for each item in the array. It does NOT return a new array. It is used for **side effects** like logging or updating something outside the array.

```javascript
const fruits = ["apple", "banana", "cherry"];

fruits.forEach(fruit => {
  console.log("I have a " + fruit);
});
// I have a apple
// I have a banana
// I have a cherry
```

The callback receives three arguments: the current item, its index, and the full array. Most of the time you only need the first:

```javascript
fruits.forEach((fruit, index) => {
  console.log(index + ": " + fruit);
});
// 0: apple
// 1: banana
// 2: cherry
```

---

### map

`map` transforms each item and **returns a new array** with the transformed values. The original array is NOT changed.

```javascript
const numbers = [1, 2, 3, 4, 5];
const doubled = numbers.map(n => n * 2);

console.log(doubled);  // [2, 4, 6, 8, 10]
console.log(numbers);  // [1, 2, 3, 4, 5] — unchanged
```

`map` is useful any time you want to create a new version of an array:

```javascript
const names = ["alice", "bob", "charlie"];
const upper = names.map(name => name.toUpperCase());
console.log(upper);  // ["ALICE", "BOB", "CHARLIE"]
```

The new array always has the same number of items as the original.

---

### filter

`filter` returns a **new array** containing only the items that pass a test. The test is a function that returns `true` or `false`. Items that return `true` are kept; items that return `false` are left out.

```javascript
const numbers = [1, 2, 3, 4, 5, 6, 7, 8];
const evens = numbers.filter(n => n % 2 === 0);

console.log(evens);  // [2, 4, 6, 8]
```

The original array is NOT changed. The new array may be shorter than the original:

```javascript
const scores = [45, 72, 88, 55, 91, 63];
const passing = scores.filter(score => score >= 60);
console.log(passing);  // [72, 88, 91, 63]
```

---

### find

`find` returns the **first item** that passes the test. If no item passes, it returns `undefined`. It does not return an array — just a single value.

```javascript
const numbers = [1, 2, 3, 4, 5];
const firstBig = numbers.find(n => n > 3);

console.log(firstBig);  // 4  (the first number greater than 3)
```

Use `filter` when you want ALL matching items. Use `find` when you want only the FIRST one.

---

### reduce

`reduce` accumulates the entire array down to a **single value**. It is the most powerful and most complex of these methods.

It takes a callback with two parameters: an **accumulator** (the running total) and the **current item**. The second argument to `reduce` is the starting value of the accumulator.

```javascript
const numbers = [1, 2, 3, 4, 5];
const total = numbers.reduce((sum, n) => sum + n, 0);

console.log(total);  // 15
```

What happens on each step:

| Step | sum (accumulator) | n (current) | Result |
|---|---|---|---|
| Start | 0 | — | 0 |
| 1 | 0 | 1 | 1 |
| 2 | 1 | 2 | 3 |
| 3 | 3 | 3 | 6 |
| 4 | 6 | 4 | 10 |
| 5 | 10 | 5 | 15 |

`reduce` can do more than addition — you can use it to multiply, find a maximum, or build objects. But summing is the most common use.

---

### sort

`sort` reorders the items **in place** (it mutates the original array). By default it sorts alphabetically — which gives wrong results for numbers:

```javascript
const numbers = [10, 1, 5, 3];
numbers.sort();
console.log(numbers);  // [1, 10, 3, 5]  — WRONG for numbers!
```

For numbers, always provide a **compare function**:

```javascript
numbers.sort((a, b) => a - b);   // ascending (smallest first)
console.log(numbers);  // [1, 3, 5, 10]  — correct

numbers.sort((a, b) => b - a);   // descending (largest first)
console.log(numbers);  // [10, 5, 3, 1]
```

The compare function should return:
- A **negative number** if `a` should come before `b`
- A **positive number** if `b` should come before `a`
- **Zero** if they are equal

For strings, the default sort (no compare function) works correctly in most cases:

```javascript
const fruits = ["cherry", "apple", "banana"];
fruits.sort();
console.log(fruits);  // ["apple", "banana", "cherry"]
```

---

### Chaining Methods

Because `map` and `filter` return new arrays, you can chain them one after the other:

```javascript
const numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];

const result = numbers
  .filter(n => n % 2 === 0)   // keep evens: [2, 4, 6, 8, 10]
  .map(n => n * 3);            // triple each: [6, 12, 18, 24, 30]

console.log(result);  // [6, 12, 18, 24, 30]
```

---

### Method Summary

| Method | Returns | Changes original? | Use for... |
|---|---|---|---|
| `forEach` | undefined | No | Running side effects for each item |
| `map` | New array (same length) | No | Transforming every item |
| `filter` | New array (shorter or same) | No | Keeping only some items |
| `find` | Single item or undefined | No | Finding the first match |
| `reduce` | Single value | No | Calculating a total or combined result |
| `sort` | Same array (reordered) | YES | Sorting the array |

---

## Practice Quiz

Take the **Session 9 Practice Quiz** in Canvas before you start the assignment. It is ungraded and you can take it as many times as you like.

If you miss a question, re-read the Key Concepts section above and try again.

---

## Wrap-Up

In this session you learned:

- **forEach** runs a callback for each item — no return value.
- **map** transforms each item and returns a new array.
- **filter** keeps only items that pass a test and returns a new array.
- **find** returns the first item that passes a test (not an array).
- **reduce** combines all items into a single value.
- **sort** reorders items in place — use a compare function for numbers.
- These methods take **callback functions** as arguments.
- `map` and `filter` can be **chained** together.

Next up is **Session 10: Credit 2 Synthesis**, where you will bring arrays, loops, functions, and higher-order methods together into one project.

You are nearly there. These methods are used constantly in professional JavaScript code — and you now know how they all work.

{{include:session-footer}}

{{include:completion-checklist}}
