---
name: "Session 11: Objects Basics"
published: true
outcomes:
  - 02-OOP
topics:
  - objects
  - properties
  - pass-by-reference
---

[lead]Objects are the most important data structure in JavaScript. Almost everything in a real program — a user, a product, a message — is stored as an object. Today you learn how to create objects, read and change their data, and work through them with loops.

# Session 11: Objects Basics

You already know how to store a single value in a variable and a list of values in an array. But what if you need to store a whole bundle of related information — a person's name, age, and city all together, labeled and organized?

That is exactly what an **object** does. By the end of this session you will know how to create objects, get data out of them, add and remove properties, check whether a property exists, and loop through all the data inside. These skills are used in nearly every JavaScript program ever written.

---

## Video Tutorial

- video-tabs
- src: source/week 2/Day 3/How to create an object.mp4 | Creating Objects
- src: source/week 2/Day 3/Object properties.mp4 | Properties
- src: source/week 2/Day 3/Getting the value of a property.mp4 | Getting Values
- src: source/week 2/Day 3/Setting the value of a property.mp4 | Setting Values
- src: source/week 2/Day 3/Adding new properties to an object.mp4 | Adding Properties
- src: source/week 2/Day 3/Deleting a property from an object.mp4 | Deleting Properties
- src: source/week 2/Day 3/Objects are passed by reference.mp4 | Pass by Reference
- src: source/week 2/Day 3/Defining multiple properties.mp4 | Multiple Properties

Estimated viewing time: 25–30 minutes. This is one of the most important topics in the whole course — type every example yourself and take your time.

---

## Key Concepts Review

### What is an Object?

An **object** is a collection of related key-value pairs. Think of it like a form you fill out — each field has a label (the **key**) and a value you fill in.

```javascript
const person = {
  name: "Alex",
  age: 28,
  city: "Walla Walla"
};
```

- Each key-value pair is called a **property**.
- The key is always a string (the label).
- The value can be any type — a string, number, boolean, array, or even another object.
- Properties are separated by commas.
- The whole object sits inside curly braces `{}`.

---

### Creating an Object

The most common way is an **object literal** — you write the object directly in your code using `{}`:

```javascript
const car = {
  make: "Toyota",
  model: "Camry",
  year: 2022,
  electric: false
};
```

You can also create an empty object and add properties later:

```javascript
const car = {};
car.make = "Toyota";
car.model = "Camry";
```

---

### Accessing Properties

There are two ways to read a property from an object.

**Dot notation** — use a dot followed by the property name. This is the most common way:

```javascript
const person = { name: "Alex", age: 28 };

console.log(person.name);   // "Alex"
console.log(person.age);    // 28
```

**Bracket notation** — use square brackets with the property name as a string. Use this when the property name is stored in a variable, or when the name has spaces or special characters:

```javascript
console.log(person["name"]);   // "Alex"

const key = "age";
console.log(person[key]);      // 28
```

If you access a property that does not exist, you get `undefined` — not an error:

```javascript
console.log(person.email);   // undefined
```

---

### Adding a Property

You can add a new property to an object at any time by assigning to a key that does not exist yet:

```javascript
const person = { name: "Alex", age: 28 };

person.email = "alex@example.com";
person.city = "Walla Walla";

console.log(person);
// { name: "Alex", age: 28, email: "alex@example.com", city: "Walla Walla" }
```

This works even if the object was created with `const`. The `const` means you cannot reassign the variable to a different object — but you CAN still change the object's contents.

---

### Deleting a Property

Use the `delete` keyword to remove a property from an object:

```javascript
const person = { name: "Alex", age: 28, city: "Walla Walla" };

delete person.city;

console.log(person);   // { name: "Alex", age: 28 }
```

After deletion, accessing that property returns `undefined`.

---

### Checking if a Property Exists

Use the `in` operator to check whether a property exists in an object. It returns `true` or `false`:

```javascript
const person = { name: "Alex", age: 28 };

console.log("name" in person);    // true
console.log("email" in person);   // false
```

Note: the property name goes in quotes (as a string) on the left side of `in`.

---

### Pass by Reference

This is one of the most important — and tricky — ideas about objects.

With regular values like numbers and strings, when you assign one variable to another, you get a **copy**:

```javascript
let a = 10;
let b = a;
b = 20;
console.log(a);   // 10 — a was not changed
```

But objects work differently. When you assign an object to a variable, you are storing a **reference** — a pointer to where the object lives in memory. When you assign that variable to another variable, both variables point to the **same object**:

```javascript
const person = { name: "Alex", age: 28 };
const person2 = person;   // person2 points to the SAME object

person2.age = 99;

console.log(person.age);    // 99 — the original was changed!
console.log(person2.age);   // 99
```

Both `person` and `person2` are looking at the same object. Changing one changes both.

This is called **pass by reference**. You will learn how to make a real copy (clone) in the next session.

---

### Iterating Over an Object

To loop through all the properties in an object, use a `for...in` loop. Each time through the loop, the variable holds the name of the next key:

```javascript
const person = { name: "Alex", age: 28, city: "Walla Walla" };

for (const key in person) {
  console.log(key, person[key]);
}
// name Alex
// age 28
// city Walla Walla
```

Notice that you use bracket notation inside the loop — `person[key]` — because `key` is a variable holding the property name as a string.

---

### Object Helper Methods

JavaScript gives you three useful methods for getting arrays from an object's data:

**`Object.keys(obj)`** — returns an array of all the property names (keys):

```javascript
const person = { name: "Alex", age: 28, city: "Walla Walla" };
console.log(Object.keys(person));
// ["name", "age", "city"]
```

**`Object.values(obj)`** — returns an array of all the values:

```javascript
console.log(Object.values(person));
// ["Alex", 28, "Walla Walla"]
```

**`Object.entries(obj)`** — returns an array of `[key, value]` pairs:

```javascript
console.log(Object.entries(person));
// [["name", "Alex"], ["age", 28], ["city", "Walla Walla"]]
```

These are handy when you want to use array methods (like `map` or `filter` from Credit 2) on the data inside an object.

---

### Quick Reference Table

| Task | How to do it |
|---|---|
| Create an object | `const obj = { key: value };` |
| Read a property | `obj.key` or `obj["key"]` |
| Add a property | `obj.newKey = value;` |
| Delete a property | `delete obj.key;` |
| Check if property exists | `"key" in obj` |
| Loop through all properties | `for (const key in obj) { }` |
| Get all keys as array | `Object.keys(obj)` |
| Get all values as array | `Object.values(obj)` |
| Get all key-value pairs | `Object.entries(obj)` |

---

## Practice Quiz

Take the **Session 11 Practice Quiz** in Canvas before you start the assignment. It pulls questions from the Session 11 question bank. It is ungraded and you can take it as many times as you like.

If you miss a question, re-read the Key Concepts section above, then try again.

---

## Wrap-Up

In this session you learned:

- An **object** is a collection of key-value pairs stored in `{}`.
- Use **dot notation** or **bracket notation** to access properties.
- You can **add** properties at any time with `obj.key = value`.
- Use `delete obj.key` to **remove** a property.
- Use `"key" in obj` to **check** if a property exists.
- Objects are **passed by reference** — two variables can point to the same object.
- Use `for...in` to **iterate** over all properties.
- `Object.keys()`, `Object.values()`, and `Object.entries()` give you arrays of an object's data.

Next up is **Session 12: Object Methods and Destructuring**, where you will learn how to add functions to objects, use the `this` keyword, and write cleaner code with destructuring and the spread operator.

You are working with one of the most powerful tools in JavaScript. Keep going — this is where things get really interesting.

{{include:session-footer}}

{{include:completion-checklist}}
