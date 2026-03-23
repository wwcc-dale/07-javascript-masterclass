---
indent: 2
name: "Solution: Session 8 — Functions"
published: false
outcomes:
  - 03-ELEM
topics:
  - functions
  - arrow-functions
---

# Instructor Solution: Session 8 — Functions

> alert: warning
>
> This page is for instructor reference only. Keep unpublished until after the assignment deadline. You may share the hint section verbally or reveal this page to individual students as needed.

---

## Student Hint

> alert: tip
>
> Your calculator function needs to handle at least 4 operations (add, subtract, multiply, divide) — a `switch` statement or an `if/else` chain on the operation string works well here. For the temperature converter, the formula is `(celsius × 9/5) + 32`. Make sure every function uses `return` to send back its result rather than logging inside it, so the caller can decide what to do with the value.

---

## Full Solution

Three functions cover greetings, arithmetic operations via a `switch`, and Celsius-to-Fahrenheit conversion, each returning a value that is then logged by the caller.

```javascript
<!DOCTYPE html>
<html lang="en">
<head><meta charset="UTF-8"><title>Session 8 — Functions</title></head>
<body>
  <script>
    // 1. Greeting function
    function greet(name, timeOfDay = "day") {
      return `Good ${timeOfDay}, ${name}! Welcome.`;
    }
    console.log(greet("Alex"));
    console.log(greet("Sam", "morning"));

    // Arrow function version (equivalent)
    const greetArrow = (name, timeOfDay = "day") => `Good ${timeOfDay}, ${name}! Welcome.`;
    console.log(greetArrow("Jordan", "evening"));

    // ---

    // 2. Calculator function
    function calculate(a, b, operation) {
      switch (operation) {
        case "add":      return a + b;
        case "subtract": return a - b;
        case "multiply": return a * b;
        case "divide":
          if (b === 0) return "Cannot divide by zero";
          return a / b;
        default:
          return `Unknown operation: ${operation}`;
      }
    }
    console.log("10 + 3 =", calculate(10, 3, "add"));       // 13
    console.log("10 - 3 =", calculate(10, 3, "subtract"));   // 7
    console.log("10 * 3 =", calculate(10, 3, "multiply"));   // 30
    console.log("10 / 3 =", calculate(10, 3, "divide"));     // 3.333...
    console.log("÷ by 0:", calculate(5, 0, "divide"));        // error message

    // ---

    // 3. Temperature converter
    function celsiusToFahrenheit(celsius) {
      return (celsius * 9 / 5) + 32;
    }
    console.log("0°C =", celsiusToFahrenheit(0), "°F");      // 32
    console.log("100°C =", celsiusToFahrenheit(100), "°F");  // 212
    console.log("37°C =", celsiusToFahrenheit(37), "°F");    // 98.6

    // Bonus: reverse converter
    const fahrenheitToCelsius = f => (f - 32) * 5 / 9;
    console.log("98.6°F =", fahrenheitToCelsius(98.6).toFixed(1), "°C"); // 37.0
  </script>
</body>
</html>
```

---

## Instructor Notes

- Core: three working functions that each `return` a value, called at least once each — all three must be present
- Common mistake: `console.log()` inside the function body instead of `return` — the student may not yet understand the difference between printing a result and returning it to the caller
- Common mistake: calling the function but not storing or logging the return value — the call runs but nothing is visible in the console
- Common mistake: calculator handles only 2–3 operations — the specification requires at least add, subtract, multiply, and divide; flag if any are missing
- Common mistake: division by zero not guarded — acceptable at Base level but worth flagging for a follow-up improvement
- Intermediate: default parameter (`timeOfDay = "day"`) and the divide-by-zero guard show awareness of edge cases
- Advanced: arrow function syntax, method chaining (`.toFixed()`), or a reverse Fahrenheit-to-Celsius converter demonstrate strong understanding
