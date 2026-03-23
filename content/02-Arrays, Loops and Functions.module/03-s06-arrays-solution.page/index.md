---
name: "Solution: Session 6 — Arrays Basics"
published: false
outcomes:
  - 03-ELEM
topics:
  - arrays
  - array-methods
---

# Instructor Solution: Session 6 — Arrays Basics

> alert: warning
>
> This page is for instructor reference only. Keep unpublished until after the assignment deadline. You may share the hint section verbally or reveal this page to individual students as needed.

---

## Student Hint

> alert: tip
>
> Start by creating your array with a few items already in it. `push()` adds to the end, and `shift()` removes from the beginning — neither returns the array, they modify it directly. After your changes, log `array` to see the final list and `array.length` to see how many items are left.

---

## Full Solution

A shopping list array is built, modified with `push()` and `shift()`, inspected with `includes()`, and the final state is logged.

```javascript
<!DOCTYPE html>
<html lang="en">
<head><meta charset="UTF-8"><title>Session 6 — Arrays</title></head>
<body>
  <script>
    // Start with a shopping list
    const shoppingList = ["apples", "bread", "milk"];
    console.log("Starting list:", shoppingList);

    // Add 3 items using push()
    shoppingList.push("eggs");
    shoppingList.push("butter");
    shoppingList.push("cheese");
    console.log("After push × 3:", shoppingList);

    // Remove the first item using shift()
    const removed = shoppingList.shift();
    console.log("Removed:", removed);          // "apples"
    console.log("After shift:", shoppingList);

    // Check if an item is in the list
    console.log("Has 'milk'?", shoppingList.includes("milk"));     // true
    console.log("Has 'apples'?", shoppingList.includes("apples")); // false (we removed it)

    // Final state
    console.log("Final list:", shoppingList);
    console.log("Total items:", shoppingList.length);

    // Bonus: indexOf
    const milkIndex = shoppingList.indexOf("milk");
    console.log("'milk' is at index:", milkIndex);
  </script>
</body>
</html>
```

---

## Instructor Notes

- Core: original array with at least 3 items, 3 `push()` calls, 1 `shift()` call, `includes()` check, log of final array and length — all 6 must be present
- Common mistake: using `const` and then trying to reassign the array (`shoppingList = [...]`) — the variable is `const` but the contents can change via `push`/`shift`; only direct reassignment is blocked
- Common mistake: `push("eggs", "butter", "cheese")` in one call — valid JavaScript and should get credit, but show them the single-item version too
- Common mistake: confusing `push` (adds to end) with `unshift` (adds to beginning) — both add items but at different ends
- Intermediate: students who also used `pop()`, `splice()`, or `concat()` show exploration beyond the core task
- Advanced: students who built a function to manage the list demonstrate that function knowledge carries over from later sessions
