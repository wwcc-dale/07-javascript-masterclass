---
indent: 2
name: "Solution: Session 3 — Strings and Numbers"
published: false
outcomes:
  - 03-ELEM
topics:
  - strings
  - numbers
  - code-style
  - template-literals
---

# Instructor Solution: Session 3 — Strings and Numbers

> alert: warning
>
> This page is for instructor reference only. Keep unpublished until after the assignment deadline. You may share the hint section verbally or reveal this page to individual students as needed.

---

## Student Hint

> alert: tip
>
> `prompt()` always returns a string, even when the user types a number — so you need `Number()` or `parseInt()` to convert the favorite number before you do any math with it, otherwise you will get `NaN` or unexpected string concatenation. Use `.trim()` on the name to remove any accidental spaces the user might have typed, then build your message with a template literal using `${}` to drop your values in.

---

## Full Solution

This solution collects user input with `prompt()`, cleans and converts the values, applies several string methods, and builds a personalized greeting using a template literal.

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Session 3 — Greeting Generator</title>
</head>
<body>
  <script>
    // Get input — prompt() always returns a string
    const rawName = prompt("What is your name?");
    const rawNumber = prompt("What is your favorite number?");

    // Clean and convert
    const name = rawName.trim();  // remove accidental leading/trailing spaces
    const formattedName = name.charAt(0).toUpperCase() + name.slice(1).toLowerCase();
    const favoriteNumber = Number(rawNumber);  // convert string to number
    const doubled = favoriteNumber * 2;

    // Build the message using a template literal
    const greeting = `Hello, ${formattedName}! Your favorite number is ${favoriteNumber}. Did you know that ${favoriteNumber} doubled is ${doubled}?`;

    console.log(greeting);

    // Extra: demonstrate additional string methods
    console.log("Name in all caps:", formattedName.toUpperCase());
    console.log("Name length:", formattedName.length, "characters");
    console.log("Contains 'a'?", formattedName.toLowerCase().includes("a"));
  </script>
</body>
</html>
```

---

## Instructor Notes

- Core requirement: the solution must use `prompt()` to collect input, at least one string method, and a template literal to build the output message.
- Common mistake: skipping `Number()` — when a student tries to double the favorite number without converting it, JavaScript concatenates the string instead: `"7" * 2` actually works (implicit coercion), but `"7" + 2` gives `"72"`. The safest habit is always to convert explicitly.
- Common mistake: not calling `.trim()` — extra spaces in a name cause subtle display bugs and will also break capitalization logic if the first character is a space.
- Common mistake: using regular single or double quotes instead of backticks for the template literal — the `${}` syntax only works inside backticks.
- Intermediate: proper name capitalization using `.charAt(0).toUpperCase() + .slice(1).toLowerCase()` is the target for intermediate work — acknowledge students who got this right.
- Advanced: students who handle empty input (checking `if (!rawName)`) or non-numeric favorite numbers (checking `isNaN(favoriteNumber)`) before running the main logic show strong understanding of defensive programming.
