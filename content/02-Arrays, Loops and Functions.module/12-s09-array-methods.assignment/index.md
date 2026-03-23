---
name: "Assignment: Higher-Order Array Methods"
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
  - 03-ELEM
topics:
  - array-methods
  - higher-order-functions
  - callbacks
---

[lead]You are going to work with an array of products — using filter, map, and reduce to answer real questions about the data, the same way a real JavaScript program would.

# Higher-Order Array Methods Assignment

In this assignment you will work with an array of product objects. You will use `filter` to get only the products you want, `map` to extract prices, and `reduce` to calculate a total. This pattern — filter, map, reduce — appears constantly in real-world JavaScript.

- stats
- 100 | Points | success
- online_upload | Submission | accent

## Why This Matters

Almost every application you use works with lists of data. A shopping site filters products by category, maps over them to build a display, and reduces a cart to a total. A finance app filters transactions by date, maps to extract amounts, and reduces to a balance. What you learn today is not a drill — it is the real pattern.

## Skills You Need

Before you start, make sure you can explain:

- How `filter` works — it takes a test function and keeps items that return `true`
- How `map` works — it transforms each item and returns a new array
- How `reduce` works — it accumulates items into a single value with a starting total
- How arrow functions work as callbacks: `item => item.price`
- How to access a property of an object: `product.price`

If any of these feel unclear, re-read the Session 9 Key Concepts section before you start.

## What You Will Build

Create a file called `products.js` (or `products.html` with a `<script>` block). It must:

1. Define a starting array called `products` with at least 6 product objects
2. Use `filter` to get only in-stock products
3. Use `map` on the filtered array to get an array of prices only
4. Use `reduce` on the prices array to calculate the total cost
5. Use `find` to locate one specific product by name
6. Log all results clearly with labels

Each product object must have at least these three properties:

```javascript
{ name: "Notebook", price: 4.99, inStock: true }
```

## Step-by-Step Instructions

- steps: Step-by-Step Instructions
- Step 1 — Create your file. Name it `products.js` or `products.html`. Add a comment at the top with your name.
- Step 2 — Create the products array. Write `const products = [ ... ]` with at least 6 objects. Give each one a `name` (string), `price` (number), and `inStock` (boolean). Make sure at least 2 products have `inStock: false` so your filter has something to remove.
- Step 3 — Filter for in-stock items. Write `const inStock = products.filter(p => p.inStock === true);` and log it with a label: `console.log("In-stock products:", inStock);`
- Step 4 — Map to get prices. Write `const prices = inStock.map(p => p.price);` and log it: `console.log("Prices:", prices);`
- Step 5 — Reduce to get total. Write `const total = prices.reduce((sum, price) => sum + price, 0);` and log it: `console.log("Total cost:", total);`
- Step 6 — Find a specific product. Pick one product name from your array. Write `const found = products.find(p => p.name === "YourProductName");` and log it: `console.log("Found:", found);` Then test what happens when you search for a name that does not exist — log that result too (it should be `undefined`).
- Step 7 — Test everything. Open in a browser (F12) and confirm all four steps produce the expected output with no errors.

## Success Criteria

- checklist: Success Criteria
- `products` array has at least 6 objects, each with `name`, `price`, and `inStock` properties
- At least 2 products have `inStock: false`
- `filter` is used to get only in-stock products and the result is logged with a label
- `map` is used on the filtered array to get prices and the result is logged with a label
- `reduce` is used on the prices to calculate the total and the result is logged with a label
- `find` is used to locate a product by name — both a found result and `undefined` are shown
- All variable names are meaningful
- Code runs without errors

## Stretch Levels

- accordion: Stretch Levels
- Base — Required for everyone
  - Complete all 7 steps above. All results must be logged with labels. Every student must reach this level.
- Intermediate — If you finish Base with time remaining
  - Add a `sort` step: sort the `inStock` array by price from lowest to highest using a compare function. Log the sorted array. Also use `forEach` to print a sentence for each in-stock product: `"Notebook costs $4.99"`. Use template literals (backtick strings from Credit 1) if you know them, or string concatenation if you prefer.
- Advanced — Challenge yourself
  - Write a function called `summarize(productList)` that accepts an array of product objects and logs: (1) total number of products, (2) number of products in stock, (3) total value of all in-stock products, and (4) the name and price of the most expensive in-stock product. Use `filter`, `map`, `reduce`, and `find` or a loop inside the function. Call `summarize(products)` at the end. All output must be clearly labelled.

{{include:session-footer}}

{{include:completion-checklist}}
