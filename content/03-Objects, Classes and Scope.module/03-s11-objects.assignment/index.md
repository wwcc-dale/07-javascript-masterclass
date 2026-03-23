---
indent: 2
name: "Assignment: Contact Card Object"
published: false
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
  - objects
  - properties
  - pass-by-reference
---

[lead]You have read about objects and seen how they work — now it is time to build one from scratch, add and remove properties, loop through its data, and see pass-by-reference in action.

# Assignment: Contact Card Object

In this assignment you will create an HTML file that uses JavaScript to build a "contact card" object. You will start with five properties, add two more, delete one, iterate over all of them, and then demonstrate that objects are passed by reference — not copied.

- stats
- 100 | Points | success
- online_upload | Submission | accent

---

## Why This Matters

Almost every web application stores information in objects. A contact in your phone, a product on a shopping site, a post on social media — all of these are objects behind the scenes. Knowing how to create, modify, and read objects is one of the most useful skills you will build in this course.

---

## Skills You Need

Before you start, make sure you can answer these from Session 11:

- How do you create an object with curly braces?
- What is the difference between dot notation and bracket notation?
- How do you add a property? Delete a property?
- What does `"key" in obj` check?
- What does "pass by reference" mean for objects?

If you are unsure about any of these, re-read the Key Concepts section of the Session 11 page.

---

## What You Will Build

You will create a file called `contact-card.html`. Inside it, you will write a `<script>` tag with JavaScript that:

1. Creates a contact object with 5 properties
2. Adds 2 more properties to the object
3. Deletes 1 property from the object
4. Uses `for...in` to loop over and log all remaining properties
5. Demonstrates pass-by-reference by creating a second variable pointing to the same object and changing a value

---

## Step-by-Step Instructions

- steps: Step-by-Step Instructions
- Step 1 — Create a new file called `contact-card.html`. Use the HTML skeleton below to get started.
- Step 2 — Inside the `<script>` tag, create an object called `contact` with these five properties: `firstName` (string), `lastName` (string), `phone` (string), `email` (string), and `age` (number). Use real-looking but made-up values.
- Step 3 — After the object, add two new properties using dot notation: `city` (a string) and `country` (a string). Log the object to the console to see the updated version.
- Step 4 — Delete the `age` property from the object using the `delete` keyword. Log the object again to confirm it is gone.
- Step 5 — Use a `for...in` loop to iterate over all remaining properties. Inside the loop, log each key and its value on the same line. Example output: `firstName Alex`.
- Step 6 — Create a second variable called `contact2` and assign `contact` to it (do NOT create a new object — just do `const contact2 = contact;`). Change one property through `contact2` (for example, change the phone number). Then log the same property from the original `contact` to show that it was also changed. Add a comment in the code explaining why this happened.
- Step 7 — Save and open the file in a browser. Open the browser console and check that all output is correct.
- Step 8 — Upload `contact-card.html` to Canvas.

**HTML skeleton:**

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Contact Card</title>
</head>
<body>
  <h1>Contact Card</h1>
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
- The file is named `contact-card.html` and opens in a browser without errors
- A `contact` object is created with exactly 5 initial properties
- Two properties are added after creation using dot notation
- One property is deleted using the `delete` keyword
- A `for...in` loop logs every remaining property and its value
- A second variable (`contact2`) is created pointing to the same object
- A property is changed through `contact2` and the original `contact` shows the same change
- A comment in the code explains why both variables reflect the change (pass by reference)
- Code is neatly indented and easy to read

---

- flow-accordion: Stretch Levels

###### Base — Required for everyone
Complete all steps as described. Create the contact object, add and delete properties, loop and log, and demonstrate pass-by-reference with a comment explaining it.

###### Intermediate — More challenge
After the `for...in` loop, add three separate `console.log()` calls using `Object.keys()`, `Object.values()`, and `Object.entries()`. Label each one so the console output is clear (e.g., `"Keys: " + Object.keys(contact)`). Also use `"email" in contact` and `"age" in contact` to check which properties exist after deletion, and log the results.

###### Advanced — Push yourself
Write a function called `printContact(obj)` that takes any object as a parameter and logs a neatly formatted summary of all its properties to the console. Call it with your `contact` object. Then create a second object called `workContact` with different properties and call `printContact` with that one too. Your function should work for any object, not just contacts.

---

{{include:session-footer}}

{{include:completion-checklist}}
