---
name: "Session 12: Object Methods and Destructuring"
published: true
outcomes:
  - 02-OOP
topics:
  - object-methods
  - this-keyword
  - destructuring
  - spread-operator
---

[lead]Objects become truly powerful when they can do things, not just store data. Today you learn how to add functions to objects, use the `this` keyword, and write cleaner code with destructuring and the spread operator.

# Session 12: Object Methods and Destructuring

In the last session you learned how to store data in objects. But objects can also contain functions — called **methods** — that work with that data. You also learn two shortcuts that make working with objects much faster: **destructuring** and the **spread operator**.

By the end of this session you will be able to write objects that both hold and process their own data, and you will write cleaner, shorter code when working with objects.

---

## Video Tutorial

- video-tabs
- src: source/week 2/Day 3/Methods.mp4 | Methods
- src: source/week 2/Day 3/Accessing a property of the object inside a method using `this`.mp4 | this Keyword
- src: source/week 2/Day 3/Object destructuring.mp4 | Destructuring
- src: source/week 2/Day 3/Passing objects as function arguments or returning objects from a function.mp4 | Objects in Functions
- src: source/week 2/Day 3/Cloning objects.mp4 | Cloning Objects
- src: source/week 2/Day 3/Merging two objects into one.mp4 | Merging Objects

Estimated viewing time: 20–25 minutes. The concepts in this session build directly on each other — follow along by typing the examples yourself.

---

## Key Concepts Review

### What is a Method?

A **method** is a function stored as a property of an object. It lets the object do something — not just hold data.

You write a method using a shorthand syntax inside the object:

```javascript
const person = {
  name: "Alex",
  age: 28,
  greet() {
    return "Hello, I am " + this.name;
  }
};

console.log(person.greet());   // "Hello, I am Alex"
```

Notice two things:
1. The method `greet` is written without the `function` keyword — just the name, parentheses, and curly braces.
2. Inside the method, `this.name` refers to the `name` property on the same object.

You can also write it the longer way using a function expression:

```javascript
const person = {
  name: "Alex",
  greet: function() {
    return "Hello, I am " + this.name;
  }
};
```

Both ways work. The shorthand is more common.

---

### The `this` Keyword

Inside a method, **`this`** refers to the object that the method belongs to. It is JavaScript's way of saying "the current object."

```javascript
const car = {
  make: "Toyota",
  model: "Camry",
  year: 2022,
  describe() {
    return this.year + " " + this.make + " " + this.model;
  }
};

console.log(car.describe());   // "2022 Toyota Camry"
```

`this.make` means "look at the `make` property of this same object."

---

### Arrow Functions and `this`

Arrow functions (`=>`) do NOT have their own `this`. If you use an arrow function as a method, `this` will not refer to the object — it will be `undefined` (in strict mode) or refer to the outer context.

```javascript
const person = {
  name: "Alex",
  greet: () => {
    return "Hello, I am " + this.name;  // BUG: this.name is undefined
  }
};
```

**Rule:** Use regular functions (or the shorthand method syntax) for object methods. Use arrow functions for other situations (like callbacks inside methods).

---

### Object Destructuring

**Destructuring** is a shortcut for extracting properties from an object into separate variables. Instead of writing `person.name`, `person.age`, and `person.city` three times, you can pull them all out at once:

```javascript
const person = { name: "Alex", age: 28, city: "Walla Walla" };

const { name, age, city } = person;

console.log(name);   // "Alex"
console.log(age);    // 28
console.log(city);   // "Walla Walla"
```

The variable names in `{}` must match the property names in the object.

---

### Renaming While Destructuring

You can give the extracted variable a different name using a colon:

```javascript
const person = { name: "Alex", age: 28 };

const { name: fullName, age: years } = person;

console.log(fullName);   // "Alex"
console.log(years);      // 28
// Note: "name" and "age" are NOT defined as variables here
```

Format: `{ propertyName: newVariableName }`

---

### Default Values in Destructuring

If a property does not exist in the object, you can provide a default value using `=`:

```javascript
const person = { name: "Alex" };

const { name, city = "Unknown" } = person;

console.log(name);   // "Alex"
console.log(city);   // "Unknown" — because city was not in the object
```

---

### The Spread Operator with Objects

The **spread operator** (`...`) lets you copy all properties from one object into another. It is written with three dots before the object name:

```javascript
const person = { name: "Alex", age: 28 };

const copy = { ...person };

console.log(copy);   // { name: "Alex", age: 28 }
```

`copy` is a new object with the same properties — not a reference to the same object. This is called a **shallow clone**.

---

### Cloning an Object

Using spread to clone solves the "pass by reference" problem from Session 11. The clone is independent:

```javascript
const original = { name: "Alex", age: 28 };
const clone = { ...original };

clone.name = "Sam";

console.log(original.name);   // "Alex" — not changed
console.log(clone.name);      // "Sam"
```

**Important — shallow copy:** Spread only copies one level deep. If a property's value is itself an object, the copy will still share that inner object by reference:

```javascript
const person = { name: "Alex", address: { city: "Walla Walla" } };
const copy = { ...person };

copy.address.city = "Portland";   // This changes original.address.city too!
console.log(person.address.city); // "Portland"
```

For this course, shallow copies are fine for most uses.

---

### Merging Objects

You can merge two objects by spreading both into a new object:

```javascript
const defaults = { theme: "light", language: "en", fontSize: 14 };
const userSettings = { theme: "dark", fontSize: 16 };

const settings = { ...defaults, ...userSettings };

console.log(settings);
// { theme: "dark", language: "en", fontSize: 16 }
```

If both objects have the same key, the one spread **later** wins. Here `userSettings.theme` ("dark") overwrites `defaults.theme` ("light").

---

### Object.assign() — An Alternative Approach

`Object.assign()` is another way to copy or merge objects. It copies properties into the first argument:

```javascript
const merged = Object.assign({}, defaults, userSettings);
```

The spread syntax `{ ...obj }` is newer and more commonly used today. You may see `Object.assign()` in older code.

---

### bind(), call(), and apply()

You already know that `this` inside a method refers to the object the method belongs to. But what if you have a standalone function and you want it to use a specific object as `this`? JavaScript gives you three tools for that: `bind()`, `call()`, and `apply()`.

**bind()** — returns a NEW function with `this` permanently set to the object you specify:

```javascript
const car = { maker: "Ford", model: "Fiesta" };

const drive = function() {
  console.log("Driving a " + this.maker + " " + this.model);
};

const boundDrive = drive.bind(car);
boundDrive();  // "Driving a Ford Fiesta"
```

You call `drive.bind(car)` and get back a new function — `boundDrive` — that always uses `car` as `this`.

**call()** — calls the function IMMEDIATELY with `this` set to the object you specify:

```javascript
const car = { maker: "Toyota", model: "Corolla" };

const describe = function(speed) {
  console.log("Driving a " + this.maker + " at " + speed + " km/h");
};

describe.call(car, 80);  // "Driving a Toyota at 80 km/h"
```

The first argument to `call()` sets `this`. Any extra arguments are passed to the function normally.

**apply()** — exactly like `call()`, but you pass extra arguments as an **array**:

```javascript
describe.apply(car, [80]);  // same result: "Driving a Toyota at 80 km/h"
```

**When to use which:**
- `bind()` — when you want to save the function for later use (like an event handler).
- `call()` — when you want to run the function now and pass arguments individually.
- `apply()` — when you want to run it now and your arguments are already in an array.

---

### Quick Reference Table

| Feature | Syntax | What it does |
|---|---|---|
| Method shorthand | `greet() { }` | Defines a function on the object |
| `this` in method | `this.name` | Refers to the current object |
| Destructure | `const { a, b } = obj` | Extract properties to variables |
| Rename on destructure | `const { a: x } = obj` | Extract `a` into a variable named `x` |
| Default on destructure | `const { a = 0 } = obj` | Use `0` if `a` is missing |
| Spread to clone | `const copy = { ...obj }` | Shallow copy of an object |
| Spread to merge | `const m = { ...a, ...b }` | Merge two objects (b wins conflicts) |
| `fn.bind(obj)` | `drive.bind(car)` | Returns a new function with `this` locked to `obj` |
| `fn.call(obj, args…)` | `drive.call(car, 100)` | Calls immediately with `this` = `obj` |
| `fn.apply(obj, [args])` | `drive.apply(car, [100])` | Same as `call`, but arguments in an array |

---

## Practice Quiz

Take the **Session 12 Practice Quiz** in Canvas before you start the assignment. It pulls questions from the Session 12 question bank. It is ungraded and you can take it as many times as you like.

---

## Wrap-Up

In this session you learned:

- A **method** is a function stored as a property on an object.
- Inside a method, **`this`** refers to the object the method belongs to.
- **Arrow functions** do NOT have their own `this` — do not use them as methods.
- **Destructuring** lets you extract multiple properties into variables in one line.
- You can **rename** and set **default values** while destructuring.
- The **spread operator** (`...`) creates a shallow copy of an object.
- You can **merge** two objects with `{ ...a, ...b }`.
- `Object.assign()` does the same thing as spread for merging.
- **`bind()`** returns a new function with `this` locked to a specific object.
- **`call()`** and **`apply()`** invoke a function immediately with a specific `this` — `call` takes arguments individually, `apply` takes them as an array.

Next up is **Session 13: Classes**, where you will learn how to create a template for making many objects with the same structure — one of the most powerful tools in JavaScript.

You are making great progress. Object methods and destructuring appear in professional JavaScript code every single day.

{{include:session-footer}}

{{include:completion-checklist}}
