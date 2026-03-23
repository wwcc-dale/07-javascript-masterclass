---
name: "Solution: Session 11 — Objects"
published: false
outcomes:
  - 02-OOP
topics:
  - objects
---

# Instructor Solution: Session 11 — Objects

> alert: warning
>
> This page is for instructor reference only. Keep unpublished until after the assignment deadline. You may share the hint section verbally or reveal this page to individual students as needed.

---

## Student Hint

> alert: tip
>
> Use `Object.entries()` or a `for...in` loop to iterate through all properties. To demonstrate pass-by-reference, create a second variable pointing to the same object, change a property through the second variable, and log the original to show it changed. Adding a property is as simple as `object.newProperty = value`.

---

## Full Solution

Create a contact card object, manipulate its properties, iterate over them, and demonstrate that objects are passed by reference rather than by value.

```javascript
// Contact card object — 5 initial properties
const contact = {
  firstName: "Sam",
  lastName:  "Torres",
  phone:     "509-555-0142",
  email:     "sam.torres@example.com",
  city:      "Walla Walla"
};
console.log("Initial contact:", contact);

// Add 2 more properties
contact.company = "Northwest Design Co.";
contact.notes   = "Prefers email over phone";
console.log("\nAfter adding 2 properties:", contact);

// Delete one property
delete contact.notes;
console.log("\nAfter deleting 'notes':", contact);

// Iterate and log all properties
console.log("\nAll contact fields:");
for (const key in contact) {
  console.log(`  ${key}: ${contact[key]}`);
}

// Object.entries() version
console.log("\nUsing Object.entries():");
for (const [key, value] of Object.entries(contact)) {
  console.log(`  ${key} → ${value}`);
}

// Demonstrate pass-by-reference
const contactAlias = contact;          // NOT a copy — same object
contactAlias.phone = "509-555-9999";   // change through the alias
console.log("\nOriginal contact phone (changed via alias):", contact.phone);
// 509-555-9999 — the original changed because both variables point to the same object

// How to make a real copy (spread)
const contactCopy = { ...contact };
contactCopy.phone = "000-000-0000";
console.log("Original after copy change:", contact.phone); // still 509-555-9999
console.log("Copy phone:", contactCopy.phone);             // 000-000-0000
```

---

## Instructor Notes

- Core: 5-property object, add 2, delete 1, iterate with `for...in` or `Object.entries()`, pass-by-reference demo
- Common mistake: `delete` on the object variable itself instead of a property — `delete contact` does nothing in non-strict mode; the correct form is `delete contact.notes`
- Common mistake: pass-by-reference demo without showing the original changed — the key is logging the original *after* the alias modification so the output proves the point
- Common mistake: confusing `contact.phone = "..."` (dot notation) with `contact["phone"] = "..."` (bracket notation) — both are valid and worth noting as equivalent
- Intermediate: using both `for...in` AND `Object.entries()` to show two approaches side by side
- Advanced: demonstrating shallow clone vs. deep clone — nested objects still share references after spread, so `const obj = { a: { b: 1 } }; const copy = { ...obj }; copy.a.b = 99;` changes the original's `a.b` as well
