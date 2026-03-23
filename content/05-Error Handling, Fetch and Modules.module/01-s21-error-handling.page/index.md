---
name: "Session 21: Error Handling"
published: true
outcomes:
  - 05-DEBUG
topics:
  - error-handling
  - try-catch-finally
  - custom-errors
  - error-types
---

[lead]Things go wrong in code — and that is okay. JavaScript gives you a powerful set of tools to catch problems before they crash your program. Today you will learn how to handle errors gracefully using try, catch, and finally.

# Session 21: Error Handling

Every program eventually runs into something unexpected — a missing value, a bad input, a file that does not exist. Without error handling, these problems crash your entire program. With error handling, you can catch the problem, respond to it, and keep going.

By the end of this session you will know the four main error types in JavaScript, how to use `try/catch/finally` to handle errors, how to throw your own custom errors, and how to nest try/catch blocks for fine-grained control.

---

## Video Tutorial

- video-tabs
- src: source/week 3/Day 4/Handling exceptions.mp4 | Handling Exceptions
- src: source/week 3/Day 4/Creating exceptions.mp4 | Creating Exceptions

Estimated viewing time: 20–25 minutes. Deliberately causing an error and then catching it is the best way to understand what is happening — type every example yourself.

---

## Key Concepts Review

### The Four Main Error Types

JavaScript has several built-in error types. Knowing the name tells you what went wrong.

| Error Type | When it happens | Example |
|---|---|---|
| `SyntaxError` | Code cannot be parsed — there is a typo in the code itself | Missing closing brace `}` |
| `ReferenceError` | You used a variable that does not exist | `console.log(myVar)` before declaring `myVar` |
| `TypeError` | You used a value in the wrong way for its type | Calling a number like a function: `(5)()` |
| `RangeError` | A value is outside the allowed range | `new Array(-1)` |

```javascript
// ReferenceError — variable does not exist
console.log(undeclaredVariable);  // ReferenceError

// TypeError — null has no property called length
const x = null;
console.log(x.length);  // TypeError

// RangeError — array size cannot be negative
const arr = new Array(-1);  // RangeError
```

---

### try / catch / finally

The `try/catch/finally` block is how you handle errors in JavaScript. Each part has a job:

- **try** — the code that might fail goes here
- **catch** — if something fails inside try, this block runs
- **finally** — this block ALWAYS runs, whether or not there was an error

```javascript
try {
  const result = riskyOperation();
  console.log("Result:", result);
} catch (error) {
  console.log("Something went wrong:", error.message);
} finally {
  console.log("This always runs — use it for cleanup.");
}
```

The `catch` block receives the **error object**, which has three useful properties:

| Property | What it contains |
|---|---|
| `error.name` | The type of error (e.g., `"TypeError"`) |
| `error.message` | A human-readable description |
| `error.stack` | A stack trace showing where the error happened |

```javascript
try {
  null.toUpperCase();  // TypeError
} catch (error) {
  console.log(error.name);     // "TypeError"
  console.log(error.message);  // "Cannot read properties of null..."
}
```

---

### Throwing Your Own Errors

You are not limited to catching errors that JavaScript creates. You can throw your own errors using the `throw` keyword.

```javascript
function divide(a, b) {
  if (b === 0) {
    throw new Error("Cannot divide by zero");
  }
  return a / b;
}

try {
  console.log(divide(10, 2));   // 5
  console.log(divide(10, 0));   // throws Error
} catch (error) {
  console.log("Error caught:", error.message);
}
```

You can throw any of the built-in error types to be more specific:

```javascript
function requireNumber(value) {
  if (typeof value !== "number") {
    throw new TypeError("Expected a number, got " + typeof value);
  }
  return value * 2;
}

try {
  requireNumber("hello");
} catch (error) {
  console.log(error.name);    // "TypeError"
  console.log(error.message); // "Expected a number, got string"
}
```

This is helpful because the error name tells the caller exactly what kind of mistake was made.

---

### Nested try / catch

Sometimes you need finer control — you want to handle errors in one step differently from errors in another step. You can put a try/catch inside another try block:

```javascript
function processInput(rawInput) {
  try {
    // Outer try — handles the whole function
    let parsed;

    try {
      // Inner try — handles just the parsing step
      parsed = JSON.parse(rawInput);
    } catch (parseError) {
      console.log("Could not parse input:", parseError.message);
      parsed = {};  // fall back to empty object
    }

    // Continue with parsed (even if it fell back to {})
    console.log("Name:", parsed.name || "unknown");

  } catch (outerError) {
    // This catches anything the inner try/catch did not handle
    console.log("Unexpected error:", outerError.message);
  }
}

processInput('{"name": "Alex"}');  // Name: Alex
processInput("not valid json");    // Could not parse input: ... then Name: unknown
```

Use nested try/catch when:
- One part of a function is especially risky
- You want a fallback for that one part but still want to handle other errors differently
- You are calling several different functions that each might fail for different reasons

---

### When to Use Error Handling

Not every line of code needs a try/catch. Use error handling when:

- You are parsing JSON (it throws if the string is not valid)
- You are dividing by a value that might be zero
- You are accessing a property that might not exist on a deep object
- You are calling code that throws custom errors (like your own library functions)

Do not wrap everything in try/catch. That makes bugs hard to find. Be specific about which operations might fail and why.

---

### Quick Reference

```javascript
// Basic try/catch
try { /* risky code */ } catch (e) { console.log(e.message); }

// With finally
try { /* code */ } catch (e) { /* handle */ } finally { /* cleanup */ }

// Throw a generic error
throw new Error("Something went wrong");

// Throw a specific error type
throw new TypeError("Expected a string");
throw new RangeError("Value must be between 0 and 100");

// Check error type
if (error instanceof TypeError) { /* handle type error */ }
```

---

## Practice Quiz

Take the **Session 21 Practice Quiz** in Canvas before you start the assignment. It is ungraded and you can take it as many times as you like.

The quiz checks your understanding of error types, try/catch/finally, throwing errors, and nested error handling. If you miss a question, re-read the Key Concepts section above.

---

## Wrap-Up

In this session you learned:

- The four main error types: `SyntaxError`, `ReferenceError`, `TypeError`, `RangeError`
- `try` wraps risky code; `catch` runs if it fails; `finally` always runs
- The error object has `name`, `message`, and `stack` properties
- `throw new Error("message")` lets you create your own errors
- Nested try/catch gives you fine control over specific steps
- Use error handling for operations that might genuinely fail — not for everything

Next up is **Session 22: Fetch API Basics**, where you will use try/catch to handle errors when loading data from a file.

You are doing great. Error handling is one of those skills that separates beginner code from professional code — and now you have it.

{{include:session-footer}}

{{include:completion-checklist}}
