---
name: "Session 13: Classes"
published: false
outcomes:
  - 02-OOP
topics:
  - classes
  - constructor
  - instances
---

[lead]Classes are templates for creating objects. Instead of writing the same object structure over and over, you write it once as a class — and then use it to stamp out as many objects as you need, all with the same shape and built-in methods.

# Session 13: Classes

You already know how to create objects by hand. But what if you need ten objects that all have the same structure — like ten products in a store, or ten students in a class? Writing each one by hand would be slow and error-prone.

A **class** solves this problem. You write the structure once, and then use the `new` keyword to create as many objects as you need. Each object created from a class is called an **instance**. By the end of this session you will know how to write a class, use its constructor, add methods, and create multiple instances.

---

## Video Tutorial

There are no recorded videos for this session. Work through the reading files on the shared class drive and use the Key Concepts section below as your primary reference. Type every example in the Key Concepts section yourself in the browser console — classes click fastest when you see instances being created in real code.

> alert: tip
>
> Open the browser console (F12), paste in a class definition, then call `new ClassName()` to create instances. You will see exactly how the constructor runs and how methods attach to each instance.

---

## Key Concepts Review

### What is a Class?

A **class** is a template — a blueprint — for creating objects. All objects created from the same class will have the same structure: the same properties and the same methods.

Think of a class like a cookie cutter. The cutter itself is the class. Each cookie you cut is an instance — a real object made from that template. All cookies have the same shape, but each one has its own dough.

---

### Class Syntax

You define a class using the `class` keyword, followed by the class name and a pair of curly braces:

```javascript
class Dog {
  constructor(name, breed) {
    this.name = name;
    this.breed = breed;
  }

  bark() {
    return this.name + " says: Woof!";
  }
}
```

Key parts:
- `class Dog` — defines the class
- `constructor(name, breed)` — a special method that runs when you create a new instance
- `this.name = name` — stores the value as a property on the new instance
- `bark()` — a method available on every instance; no `function` keyword needed

---

### The `constructor` Method

The **constructor** is a special method that runs automatically when you use `new` to create an object from the class. It sets up the initial properties of the new instance.

```javascript
class Person {
  constructor(firstName, lastName, age) {
    this.firstName = firstName;
    this.lastName = lastName;
    this.age = age;
  }
}
```

When you call `new Person("Alex", "Kim", 28)`:
- JavaScript creates a new empty object
- The constructor runs with `firstName = "Alex"`, `lastName = "Kim"`, `age = 28`
- `this` inside the constructor refers to the new object being created
- `this.firstName = firstName` stores "Alex" as the `firstName` property of the new object

---

### Creating Instances with `new`

To create an object from a class, use the `new` keyword followed by the class name and the arguments for the constructor:

```javascript
const myDog = new Dog("Rex", "Labrador");
const yourDog = new Dog("Bella", "Poodle");

console.log(myDog.name);      // "Rex"
console.log(yourDog.name);    // "Bella"
console.log(myDog.bark());    // "Rex says: Woof!"
console.log(yourDog.bark());  // "Bella says: Woof!"
```

Each instance has its own property values but shares the same methods. `myDog` and `yourDog` are separate objects — changing one does not affect the other.

---

### `this` in Classes

Inside any method in a class, `this` refers to the specific instance the method is being called on. When you call `myDog.bark()`, `this` refers to `myDog`. When you call `yourDog.bark()`, `this` refers to `yourDog`.

This is the same `this` you learned about in Session 12, just in the context of a class.

---

### Class Methods

You add methods to a class by writing them inside the class body, just like the `bark()` example. Methods are written using the shorthand syntax — no `function` keyword:

```javascript
class Rectangle {
  constructor(width, height) {
    this.width = width;
    this.height = height;
  }

  area() {
    return this.width * this.height;
  }

  perimeter() {
    return 2 * (this.width + this.height);
  }

  describe() {
    return `Rectangle: ${this.width} x ${this.height}`;
  }
}

const rect = new Rectangle(5, 3);
console.log(rect.area());       // 15
console.log(rect.perimeter());  // 16
console.log(rect.describe());   // "Rectangle: 5 x 3"
```

All instances of `Rectangle` will have `area()`, `perimeter()`, and `describe()` available.

---

### Naming Convention — Capital Letter

By strong convention in JavaScript, class names always start with a **capital letter** (PascalCase). This helps you tell apart a class from a regular variable or function at a glance.

```javascript
class Dog { }         // class — capital D
class ShoppingCart { } // class — PascalCase
class BookLibrary { }  // class — PascalCase

const myDog = new Dog();  // instance — lowercase variable
```

If you see `new Foo()` in code, you know `Foo` is a class. If you see `foo()`, it is a regular function call.

---

### Why Use Classes?

Without classes, creating ten products might look like this:

```javascript
const product1 = { name: "Pen", price: 1.50, inStock: true };
const product2 = { name: "Notebook", price: 3.00, inStock: true };
const product3 = { name: "Ruler", price: 2.00, inStock: false };
// ... seven more ...
```

With a class:

```javascript
class Product {
  constructor(name, price, inStock) {
    this.name = name;
    this.price = price;
    this.inStock = inStock;
  }

  describe() {
    const status = this.inStock ? "in stock" : "out of stock";
    return `${this.name} — $${this.price} (${status})`;
  }
}

const product1 = new Product("Pen", 1.50, true);
const product2 = new Product("Notebook", 3.00, true);
const product3 = new Product("Ruler", 2.00, false);

console.log(product1.describe());  // "Pen — $1.5 (in stock)"
console.log(product3.describe());  // "Ruler — $2 (out of stock)"
```

The class approach is shorter, more consistent, and much easier to update. If you need to add a new method, you add it once to the class and every instance gets it automatically.

---

### Checking the Type of an Instance

You can use `instanceof` to check whether an object was created from a particular class:

```javascript
const rex = new Dog("Rex", "Labrador");

console.log(rex instanceof Dog);    // true
console.log(rex instanceof Person); // false
```

---

### Quick Reference

| Concept | Syntax / Example |
|---|---|
| Define a class | `class Animal { }` |
| Constructor | `constructor(name) { this.name = name; }` |
| Create an instance | `const a = new Animal("Leo");` |
| Access property | `a.name` |
| Call a method | `a.speak()` |
| Check type | `a instanceof Animal` |
| Naming rule | Class names start with a capital letter |

---

## Practice Quiz

Take the **Session 13 Practice Quiz** in Canvas before you start the assignment. It pulls questions from the Session 13 question bank. It is ungraded and you can take it as many times as you like.

---

## Wrap-Up

In this session you learned:

- A **class** is a template for creating objects with the same structure.
- The **constructor** method sets up the initial properties of a new instance.
- Use `new ClassName()` to create an **instance** of a class.
- `this` inside a class refers to the specific instance being used.
- **Methods** are written inside the class without the `function` keyword.
- Class names always start with a **capital letter** by convention.
- Classes prevent repetition — write the structure once, use it many times.

Next up is **Session 14: Scope and Closures**, where you will learn exactly where variables can and cannot be used in your code — and discover closures, one of JavaScript's most powerful and interesting features.

Excellent work. Classes are a key skill for building real applications. You are now thinking like a JavaScript developer.

{{include:session-footer}}

{{include:completion-checklist}}
