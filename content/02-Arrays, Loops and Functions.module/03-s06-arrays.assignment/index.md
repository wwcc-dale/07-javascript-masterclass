---
indent: 2
name: "Assignment: Arrays Basics"
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
  - 03-ELEM
topics:
  - arrays
  - array-methods
---

[lead]You have learned how arrays work — now you will build one from scratch, add and remove items, and inspect what is inside. This is a skill you will use in every JavaScript program you ever write.

# Arrays Basics Assignment

You are going to build a shopping list in JavaScript. Along the way you will practice creating arrays, adding items, removing items, and checking what is inside.

- stats
- 100 | Points | success
- online_upload | Submission | accent

## Why This Matters

Nearly every real-world JavaScript program works with lists of data — lists of users, lists of products, lists of messages. Arrays are how JavaScript stores those lists. If you can create and modify arrays, you can handle real data in real programs.

## Skills You Need

Before you start, make sure you can answer yes to each of these:

- I know how to create an array with `[]`
- I know how to access an item by its index number
- I know what `.length` returns
- I know how `push()`, `unshift()`, `pop()`, and `shift()` work
- I know the difference between `includes()` and `indexOf()`

If you are unsure about any of these, re-read the Session 6 Key Concepts section before you begin.

## What You Will Build

You will create a file called `shopping-list.js` (or `shopping-list.html` with a `<script>` block inside) that:

1. Creates an array called `shoppingList` with at least 3 items already in it
2. Adds 3 more items using `push()`
3. Removes the first item using `shift()`
4. Checks if a specific item is in the list using `includes()` and logs the result
5. Logs the final array using `console.log()`
6. Logs the final length of the array using `console.log()`

All output goes to the browser console (open with F12) or the terminal if you are running Node.js.

## Step-by-Step Instructions

- steps: Step-by-Step Instructions
- Step 1 — Create your file. Name it `shopping-list.js` or `shopping-list.html`. If you use HTML, add a `<script>` tag and write your JavaScript inside it.
- Step 2 — Create your starting array. Use `const shoppingList = ["item1", "item2", "item3"];` with real grocery items like "milk", "bread", and "eggs".
- Step 3 — Add three items to the end. Use `shoppingList.push()` three times (or once with three arguments) to add three more groceries.
- Step 4 — Remove the first item. Use `shoppingList.shift()` to remove the first item. Save the result in a variable and log it so you can see what was removed.
- Step 5 — Check for an item. Pick one of the items in your list. Use `shoppingList.includes("yourItem")` and log the result. Then check for an item that is NOT in the list, so you see both `true` and `false`.
- Step 6 — Log the final array. Use `console.log(shoppingList)` to print the whole array.
- Step 7 — Log the length. Use `console.log("Items in list:", shoppingList.length)` to print how many items are left.
- Step 8 — Test your code. Open your file in a browser and press F12 to see the console output. Make sure all 7 steps produced output.

## Success Criteria

- checklist: Success Criteria
- Array named `shoppingList` is created with at least 3 starting items
- Three additional items are added using `push()`
- First item is removed using `shift()` and the removed item is logged
- `includes()` is used and the result is logged — once for a present item (true) and once for a missing item (false)
- Final array is logged with `console.log()`
- Final length is logged with `console.log()`
- Variable names are meaningful (not `a`, `b`, `x`)
- Code runs without errors in the browser console

- flow-accordion: Stretch Levels

###### Base — Required for everyone
Complete all 8 steps above. Your array should have at least 5 items after the push calls and 1 shift. All console output should be visible. Every student must reach this level.

###### Intermediate — If you finish Base with time remaining
Add a second array called `pantryItems` with 3 items already stocked at home. Use `concat()` to combine `shoppingList` and `pantryItems` into a new array called `fullList`. Log `fullList` and its length. Also use `indexOf()` to find the position of one specific item in `fullList` and log it.

###### Advanced — Challenge yourself
Use `indexOf()` to find one item in `fullList`, then use `splice()` to remove it and log the updated `fullList`. Then create a third array `urgentItems` with 2 items you need today, and use `concat()` to place it at the front of a new array called `prioritized` (put `urgentItems` first, then the rest of `fullList`). Log `prioritized`. Use `includes()` to check whether three specific items are in `prioritized` and log a message like `"Has milk: true"` for each. Finally, log the total number of unique items using `.length`.

---

{{include:session-footer}}

{{include:completion-checklist}}
