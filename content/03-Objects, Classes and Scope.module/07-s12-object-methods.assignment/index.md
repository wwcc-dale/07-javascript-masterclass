---
indent: 2
name: "Assignment: User Object with Methods"
published: true
points_possible: 100
grading_type: points
submission_types:
  - online_upload
allowed_extensions:
  - html
  - js
  - txt
due_at: null
outcomes:
  - 02-OOP
topics:
  - object-methods
  - this-keyword
  - destructuring
  - spread-operator
---

[lead]You know how to store data in objects — now you will make objects that can also do things. In this assignment you build a user object with methods, destructure its properties, clone it with spread, and merge two objects together.

# Assignment: User Object with Methods

In this assignment you will create a JavaScript object that holds information about a user AND includes functions (methods) the object can perform. You will then use destructuring and the spread operator to work with the object more efficiently.

- stats
- 100 | Points | success
- online_upload | Submission | accent

---

## Why This Matters

When you see `user.getName()` or `product.getPrice()` in real code, that is an object method in action. Methods are how objects "do things" rather than just "hold data." Destructuring saves you from writing the same property access over and over. These are patterns you will see in every professional codebase.

---

## Skills You Need

Before you start, make sure you can answer these from Session 12:

- How do you write a method inside an object?
- What does `this` refer to inside a method?
- Why should you NOT use an arrow function as a method?
- How does destructuring work? What is the syntax?
- What does the spread operator (`...`) do when used with an object?

If any of these are unclear, re-read the Key Concepts section of the Session 12 page.

---

## What You Will Build

You will create a file called `user-object.html`. Inside it, you will write a `<script>` tag with JavaScript that:

1. Creates a `user` object with at least 5 properties and 2 methods
2. Calls both methods and logs their output
3. Destructures at least 3 properties from the object into separate variables and logs them
4. Creates a clone of the object using the spread operator and verifies it is independent
5. Merges two objects using spread and logs the result

---

## Step-by-Step Instructions

- steps: Step-by-Step Instructions
- Step 1 — Create `user-object.html` using the HTML skeleton below.
- Step 2 — Create a `user` object with these properties: `firstName` (string), `lastName` (string), `age` (number), `email` (string), and `role` (string, e.g., "student" or "admin"). Add two methods: `getFullName()` — returns the full name by combining `this.firstName` and `this.lastName` — and `greet()` — returns a greeting message that uses `this.firstName` and `this.role`.
- Step 3 — Call both methods and log their return values to the console.
- Step 4 — Use destructuring to extract `firstName`, `email`, and `role` from the `user` object into three separate variables. Log all three.
- Step 5 — Create a `userCopy` by spreading the `user` object: `const userCopy = { ...user };`. Change the `email` property on `userCopy`. Log the email from both `user` and `userCopy` to prove they are independent objects.
- Step 6 — Create a second object called `extraInfo` with at least 2 properties (`city` and `country` are good choices). Use the spread operator to merge `user` and `extraInfo` into a new object called `fullProfile`. Log `fullProfile`.
- Step 7 — Save the file, open it in a browser, and check the console output.
- Step 8 — Upload `user-object.html` to Canvas.

**HTML skeleton:**

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>User Object</title>
</head>
<body>
  <h1>User Object with Methods</h1>
  <p>Open the console to see the output.</p>

  <script>
    // Your JavaScript goes here

  </script>
</body>
</html>
```

---

## Success Criteria

- checklist: Success Criteria
- The file is named `user-object.html` and opens in a browser without errors
- The `user` object has at least 5 properties and 2 methods written using method shorthand
- Both methods use `this` correctly and return meaningful strings
- Both methods are called and their return values are logged
- At least 3 properties are extracted from `user` using destructuring and logged
- A clone (`userCopy`) is created with spread and a property is changed on the clone; the original is not affected
- Two objects are merged using spread into a `fullProfile` object and logged
- Code is neatly indented and uses clear, descriptive names

---

- flow-accordion: Stretch Levels

###### Base — Required for everyone
Complete all steps as described: user object with 5 properties and 2 methods, destructuring, cloning, and merging. All output is correct.

###### Intermediate — More challenge
Add a third method called `isAdult()` that uses `this.age` to return `true` if the user is 18 or older, or `false` otherwise. Call it and log the result with a label. Also use destructuring with a default value — destructure a property called `nickname` from `user` with a default of `"No nickname"` (since `user` does not have that property) and log it.

###### Advanced — Push yourself
Refactor your merging step: instead of just merging two objects, write a function called `mergeProfiles(...objects)` that accepts any number of objects and returns one merged object using the spread operator inside a `reduce()` call. Call it with 3 separate objects. Also add a `summary()` method to `user` that uses a template literal to return a single string describing all five of the user's properties.

---

{{include:session-footer}}

{{include:completion-checklist}}
