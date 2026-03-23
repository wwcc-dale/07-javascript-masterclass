---
indent: 2
name: "Solution: Session 12 — Object Methods"
published: false
outcomes:
  - 02-OOP
topics:
  - object-methods
---

# Instructor Solution: Session 12 — Object Methods

> alert: warning
>
> This page is for instructor reference only. Keep unpublished until after the assignment deadline. You may share the hint section verbally or reveal this page to individual students as needed.

---

## Student Hint

> alert: tip
>
> Methods in an object use `this` to refer to the object they belong to — use `this.name` inside the greet method, not the variable name `user`. For destructuring, put the property names in curly braces on the left side of the assignment: `const { name, age } = user`. To verify the clone is independent, change a property on the clone and log the original to confirm it did not change.

---

## Full Solution

Create a user object with a method that uses `this`, extract properties with destructuring, clone and merge objects with spread, and verify that the clone is independent of the original.

```javascript
// User object with a method
const user = {
  name: "Alex",
  age: 28,
  city: "Portland",
  role: "designer",
  greet() {
    return `Hi, I am ${this.name} from ${this.city}. I work as a ${this.role}.`;
  }
};

console.log(user.greet());

// Destructuring — extract 3 properties
const { name, age, city } = user;
console.log(`Name: ${name}, Age: ${age}, City: ${city}`);

// Renaming during destructuring
const { role: jobTitle } = user;
console.log("Job title:", jobTitle);

// Default value in destructuring
const { email = "no email on file" } = user;
console.log("Email:", email);

// Clone with spread
const userClone = { ...user };
console.log("Clone:", userClone);

// Verify clone is independent
userClone.name = "Jamie";
console.log("Original name after clone change:", user.name);  // still "Alex"
console.log("Clone name:", userClone.name);                   // "Jamie"

// Merge two objects
const userPreferences = {
  theme: "dark",
  notifications: true,
  language: "en"
};

const fullUserProfile = { ...user, ...userPreferences };
console.log("Merged profile:", fullUserProfile);

// Note: if both objects have the same key, the second one wins
const overrideTest = { ...user, name: "Override Name" };
console.log("Override test name:", overrideTest.name); // "Override Name"
```

---

## Instructor Notes

- Core: object with `greet()` method using `this`, destructuring 3 properties, spread clone, spread merge, independence verification
- Common mistake: using the object variable name directly inside the method (`user.name`) instead of `this.name` — works in this example but breaks if the object is ever renamed or the method is extracted and called in a different context
- Common mistake: using an arrow function for a method — arrow functions do not have their own `this`, so `greet: () => { return this.name }` will return `undefined` or the outer scope's `this`
- Common mistake: not verifying independence — just cloning without proving the original did not change; the output demonstrating the original is unchanged is the whole point
- Intermediate: renaming with `const { role: jobTitle } = user` and providing default values with `const { email = "no email on file" } = user`
- Advanced: nested object spread showing the shallow clone limitation — `const obj = { a: 1, nested: { b: 2 } }; const copy = { ...obj }; copy.nested.b = 99;` — the original's `nested.b` also changes because the nested object is still shared
