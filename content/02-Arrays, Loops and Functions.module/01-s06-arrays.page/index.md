---
name: "Session 6: Arrays Basics"
published: false
outcomes:
  - 03-ELEM
topics:
  - arrays
  - array-methods
---

[lead]Arrays are one of the most useful tools in JavaScript — they let you store a whole list of values in a single variable, and work with all of them at once.

# Session 6: Arrays Basics

You already know how to store one value in a variable. But what if you need to store ten values — like a shopping list, a set of scores, or a group of names?

That is exactly what arrays are for. By the end of this session you will know how to create arrays, access items in them, add and remove items, and check what is inside. These skills show up in almost every JavaScript program.

---

## Video Tutorial

- video-tabs
- src: source/week 1/Day 2/Arrays.mp4 | Arrays
- src: source/week 1/Day 2/Number of items in the array.mp4 | Array Length
- src: source/week 1/Day 2/Create a new array from an existing array.mp4 | Creating from Existing
- src: source/week 1/Day 2/Adding an item to an existing array.mp4 | Adding Items
- src: source/week 1/Day 2/Adding at the beginning of an array.mp4 | Adding at Start
- src: source/week 1/Day 2/Adding multiple items to the array.mp4 | Adding Multiple Items

Estimated viewing time: 15–20 minutes. Type the code examples yourself as you watch — typing what you see helps you remember it far better than just watching.

---

## Key Concepts Review

### What is an Array?

An **array** is an ordered list of values stored in a single variable. Each value in the list is called an **element** or **item**.

You create an array using square brackets `[]`, with items separated by commas:

```javascript
const colors = ["red", "green", "blue"];
const scores = [85, 92, 78, 95];
const mixed = ["Alice", 42, true];  // arrays can hold any type
```

The name `colors` holds all three color strings at once. Think of it like a row of labeled boxes — all under one name.

---

### Accessing Items: Index Numbers

Every item in an array has a position number called an **index**. The first item is at index `0`, the second at index `1`, and so on.

```javascript
const fruits = ["apple", "banana", "cherry"];

console.log(fruits[0]);  // "apple"
console.log(fruits[1]);  // "banana"
console.log(fruits[2]);  // "cherry"
```

This is called **zero-based indexing** — counting starts at 0, not 1.

To get the last item, you can use `array.length - 1`:

```javascript
console.log(fruits[fruits.length - 1]);  // "cherry"
```

---

### Array Length

The `.length` property tells you how many items are in the array:

```javascript
const fruits = ["apple", "banana", "cherry"];
console.log(fruits.length);  // 3
```

Note: the length is always one more than the last index. If there are 3 items, the indices are 0, 1, 2 — and the length is 3.

---

### Adding Items to the End: push

`push()` adds one or more items to the **end** of an array. It modifies the original array:

```javascript
const fruits = ["apple", "banana"];
fruits.push("cherry");
console.log(fruits);  // ["apple", "banana", "cherry"]

fruits.push("date", "elderberry");  // you can push multiple at once
console.log(fruits);  // ["apple", "banana", "cherry", "date", "elderberry"]
```

---

### Adding Items to the Start: unshift

`unshift()` adds one or more items to the **beginning** of an array. It also modifies the original array:

```javascript
const fruits = ["banana", "cherry"];
fruits.unshift("apple");
console.log(fruits);  // ["apple", "banana", "cherry"]
```

---

### Removing Items: pop and shift

`pop()` removes and returns the **last** item:

```javascript
const fruits = ["apple", "banana", "cherry"];
const removed = fruits.pop();
console.log(removed);  // "cherry"
console.log(fruits);   // ["apple", "banana"]
```

`shift()` removes and returns the **first** item:

```javascript
const fruits = ["apple", "banana", "cherry"];
const removed = fruits.shift();
console.log(removed);  // "apple"
console.log(fruits);   // ["banana", "cherry"]
```

---

### Combining Arrays: concat

`concat()` joins two or more arrays together and **returns a new array**. It does NOT change the originals:

```javascript
const first = ["a", "b"];
const second = ["c", "d"];
const combined = first.concat(second);

console.log(combined);  // ["a", "b", "c", "d"]
console.log(first);     // ["a", "b"] — unchanged
```

---

### Removing Items at Any Position: splice

`splice()` removes items from anywhere in the array. It takes two arguments: where to start, and how many items to remove:

```javascript
const colors = ["red", "green", "blue", "yellow"];
colors.splice(1, 1);  // start at index 1, remove 1 item
console.log(colors);  // ["red", "blue", "yellow"]
```

`splice()` modifies the original array.

---

### Checking if an Item Exists: includes

`includes()` returns `true` if the item is in the array, or `false` if it is not:

```javascript
const fruits = ["apple", "banana", "cherry"];
console.log(fruits.includes("banana"));  // true
console.log(fruits.includes("grape"));   // false
```

---

### Finding the Index of an Item: indexOf

`indexOf()` returns the index (position number) of the first matching item. If the item is not found, it returns `-1`:

```javascript
const fruits = ["apple", "banana", "cherry"];
console.log(fruits.indexOf("banana"));  // 1
console.log(fruits.indexOf("grape"));   // -1
```

---

### Arrays of Arrays (2D Arrays)

An array can hold other arrays as items. This is called a **two-dimensional array** or a **nested array**. It is useful for grids, tables, and any data with rows and columns.

```javascript
const grid = [
  [1, 2, 3],
  [4, 5, 6],
  [7, 8, 9]
];

console.log(grid[0]);     // [1, 2, 3]  — the first row
console.log(grid[1][2]);  // 6          — row 1, column 2
```

You use two sets of square brackets: the first picks the row, the second picks the item within that row.

---

### Array Destructuring

**Destructuring** lets you pull items out of an array and store them in individual variables in one line:

```javascript
const colors = ["red", "green", "blue"];

const [first, second, third] = colors;

console.log(first);   // "red"
console.log(second);  // "green"
console.log(third);   // "blue"
```

You can skip items by leaving a gap:

```javascript
const [top, , bottom] = ["gold", "silver", "bronze"];
console.log(top);     // "gold"
console.log(bottom);  // "bronze"
```

---

### Checking if a Value is an Array

Use `Array.isArray()` to check whether a value is actually an array. It returns `true` or `false`.

```javascript
const numbers = [1, 2, 3];
const name = "Alex";

console.log(Array.isArray(numbers));  // true
console.log(Array.isArray(name));     // false
```

This is helpful when you are not sure what type of value you are working with.

---

### Filling an Array: fill

`fill()` sets all (or some) items in an array to the same value. It modifies the original array.

```javascript
const scores = [0, 0, 0, 0, 0];
scores.fill(10);
console.log(scores);  // [10, 10, 10, 10, 10]
```

You can also fill a specific range by passing start and end positions:

```javascript
const arr = [1, 2, 3, 4, 5];
arr.fill(0, 1, 3);  // fill with 0, from index 1 up to (not including) index 3
console.log(arr);   // [1, 0, 0, 4, 5]
```

---

### Displaying an Array in a Web Page

You can use JavaScript to show array contents in HTML. One common approach is to use `.innerHTML` to write a list:

```html
<ul id="fruit-list"></ul>

<script>
  const fruits = ["apple", "banana", "cherry"];
  let html = "";
  for (const fruit of fruits) {
    html += "<li>" + fruit + "</li>";
  }
  document.getElementById("fruit-list").innerHTML = html;
</script>
```

This creates a bullet list on the page from your array. You will use this pattern in the assignment.

---

### Quick Method Summary

| Method | What it does | Changes original? |
|---|---|---|
| `push(item)` | Add to end | Yes |
| `unshift(item)` | Add to start | Yes |
| `pop()` | Remove from end | Yes |
| `shift()` | Remove from start | Yes |
| `concat(array)` | Combine arrays | No — returns new |
| `splice(i, n)` | Remove n items at index i | Yes |
| `fill(value)` | Set all items to value | Yes |
| `includes(item)` | Check if item exists | No — returns true/false |
| `indexOf(item)` | Find position of item | No — returns index |
| `Array.isArray(x)` | Check if x is an array | No — returns true/false |

---

## Practice Quiz

Take the **Session 6 Practice Quiz** in Canvas before you start the assignment. It pulls questions from the Session 6 question bank. It is ungraded and you can take it as many times as you like.

If you miss a question, re-read the Key Concepts section above, then try again.

---

## Wrap-Up

In this session you learned:

- An **array** stores a list of values in one variable, using `[]`.
- Items are accessed by **index** starting at `0`.
- `.length` tells you how many items are in the array.
- `push()` and `unshift()` add items; `pop()` and `shift()` remove them.
- `concat()` combines arrays without changing the originals.
- `splice()` removes items at any position; `fill()` fills with a value.
- `includes()` checks if an item exists; `indexOf()` finds its position.
- `Array.isArray()` checks whether a value is an array.
- **2D arrays** (arrays of arrays) store grid-like data.
- **Array destructuring** lets you unpack items into variables in one line.

Next up is **Session 7: Loops**, where you will learn how to repeat actions automatically — including how to step through every item in an array without writing the same code over and over.

Great work today. Arrays are everywhere in real JavaScript code, and you now know how they work.

{{include:session-footer}}

{{include:completion-checklist}}
