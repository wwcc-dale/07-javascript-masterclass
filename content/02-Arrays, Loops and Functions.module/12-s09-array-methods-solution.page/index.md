---
name: "Solution: Session 9 — Array Methods"
published: false
outcomes:
  - 03-ELEM
topics:
  - array-methods
  - higher-order-functions
---

# Instructor Solution: Session 9 — Array Methods

> alert: warning
>
> This page is for instructor reference only. Keep unpublished until after the assignment deadline. You may share the hint section verbally or reveal this page to individual students as needed.

---

## Student Hint

> alert: tip
>
> Remember that `filter()`, `map()`, and `reduce()` do not change the original array — they return new ones. Chain them or store each result in a new variable. For `reduce()`, the first argument to the callback is the accumulator (the running total) and the second is the current item; the second argument to `reduce()` itself is the starting value — use `0` for a sum.

---

## Full Solution

A product array is processed with `filter()` to isolate in-stock items, `map()` to extract prices, and `reduce()` to sum the total — shown both step-by-step and as a single chained expression.

```javascript
<!DOCTYPE html>
<html lang="en">
<head><meta charset="UTF-8"><title>Session 9 — Array Methods</title></head>
<body>
  <script>
    const products = [
      { name: "Notebook",     price: 4.99,  inStock: true  },
      { name: "Pen Set",      price: 12.50, inStock: true  },
      { name: "Desk Lamp",    price: 34.99, inStock: false },
      { name: "Stapler",      price: 8.75,  inStock: true  },
      { name: "Whiteboard",   price: 89.00, inStock: false },
      { name: "Sticky Notes", price: 3.25,  inStock: true  },
    ];

    // 1. filter() — only in-stock products
    const inStockProducts = products.filter(product => product.inStock);
    console.log("In-stock products:");
    inStockProducts.forEach(p => console.log(" -", p.name, `($${p.price})`));

    // 2. map() — extract just the prices of in-stock items
    const inStockPrices = inStockProducts.map(product => product.price);
    console.log("In-stock prices:", inStockPrices);

    // 3. reduce() — sum of all in-stock prices
    const total = inStockPrices.reduce((sum, price) => sum + price, 0);
    console.log("Total in-stock cost: $" + total.toFixed(2));

    // Chained version (same result, one expression)
    const chainedTotal = products
      .filter(p => p.inStock)
      .map(p => p.price)
      .reduce((sum, price) => sum + price, 0);
    console.log("Chained total: $" + chainedTotal.toFixed(2));

    // Bonus: find() — find the first product over $10
    const firstExpensive = products.find(p => p.price > 10);
    console.log("First product over $10:", firstExpensive?.name);

    // Bonus: sort() — sort by price ascending (spread copy to avoid mutation)
    const sortedByPrice = [...products].sort((a, b) => a.price - b.price);
    console.log("Sorted by price:", sortedByPrice.map(p => p.name));
  </script>
</body>
</html>
```

---

## Instructor Notes

- Core: a product array with at least 4 objects each having `name`, `price`, and `inStock` properties; `filter()` for in-stock items; `map()` for prices; `reduce()` for the total — all four pieces must be present
- Common mistake: arrow callback without a return: `products.filter(p => { p.inStock })` — the curly braces create a function body, so `p.inStock` is evaluated but nothing is returned; the fix is either remove the braces or add `return`
- Common mistake: `reduce()` called without the initial value `0` as the second argument — works when the array has items but throws on an empty array; always include the initial value
- Common mistake: calling `products.sort()` directly — `sort()` mutates the original array; teach `[...products].sort()` to work on a copy
- Intermediate: writing the chained `filter().map().reduce()` in a single expression shows conceptual depth
- Advanced: using `find()`, `some()`, `every()`, or `sort()` beyond the base requirements, or using optional chaining (`?.`) on the `find()` result
