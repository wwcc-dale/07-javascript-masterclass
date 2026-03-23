---
indent: 2
name: "Solution: Session 7 — Loops"
published: false
outcomes:
  - 03-ELEM
topics:
  - loops
  - for-loop
  - while-loop
---

# Instructor Solution: Session 7 — Loops

> alert: warning
>
> This page is for instructor reference only. Keep unpublished until after the assignment deadline. You may share the hint section verbally or reveal this page to individual students as needed.

---

## Student Hint

> alert: tip
>
> For the `for...of` with index, you can use a separate counter variable that you increment each iteration, or look at the `entries()` method on arrays (`for (const [i, item] of array.entries())`). For the `while` countdown, declare your counter variable before the loop, decrease it inside the loop body, and make sure the condition will eventually become false — otherwise the loop runs forever.

---

## Full Solution

Three loops demonstrate the `for`, `for...of`, and `while` constructs: counting 1–10, iterating an array with index, and counting down from 10.

```javascript
<!DOCTYPE html>
<html lang="en">
<head><meta charset="UTF-8"><title>Session 7 — Loops</title></head>
<body>
  <script>
    // 1. for loop — numbers 1 through 10
    console.log("--- for loop: 1 to 10 ---");
    for (let i = 1; i <= 10; i++) {
      console.log(i);
    }

    // 2. for...of — each item with its index
    const fruits = ["apple", "banana", "cherry", "date", "elderberry"];
    console.log("\n--- for...of with index ---");

    // Option A: manual counter
    let index = 0;
    for (const fruit of fruits) {
      console.log(`[${index}] ${fruit}`);
      index++;
    }

    // Option B: array.entries() — elegant alternative
    console.log("\n--- using .entries() ---");
    for (const [i, fruit] of fruits.entries()) {
      console.log(`[${i}] ${fruit}`);
    }

    // 3. while loop — countdown from 10 to 1
    console.log("\n--- while countdown ---");
    let count = 10;
    while (count >= 1) {
      console.log(count);
      count--;
    }
    console.log("Liftoff!");
  </script>
</body>
</html>
```

---

## Instructor Notes

- Core: one `for` loop printing 1–10, one `for...of` with index, one `while` countdown — all three constructs must be present
- Common mistake: `for (let i = 0; i <= 10; i++)` starts at 0 instead of 1 — output includes a stray 0 at the top
- Common mistake: `while (count > 0)` stops at 1 correctly, but `while (count >= 1)` makes the intent clearer; accept either
- Common mistake (critical): forgetting `count--` in the `while` loop body — this creates an infinite loop that freezes the tab; if it happens, the student must force-close the browser tab
- Common mistake: using `for...in` instead of `for...of` — `for...in` iterates keys (indices as strings like `"0"`, `"1"`), not values
- Intermediate: using `array.entries()` for the index shows initiative and comfort with destructuring
- Advanced: students who demonstrated `break` or `continue` inside a loop to show those keywords show depth beyond the base requirements
