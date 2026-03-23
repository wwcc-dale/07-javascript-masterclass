---
name: "Session 22: Fetch API Basics"
published: true
outcomes:
  - 04-MOD
topics:
  - fetch-api
  - response-object
  - json-files
  - promises
---

[lead]The Fetch API is how modern JavaScript loads data from files and servers. Today you will learn to use fetch() to load a local JSON file, read the Response object, and handle errors the right way.

# Session 22: Fetch API Basics

Websites do not load all their data at once. They fetch it — piece by piece, on demand. The Fetch API is the built-in JavaScript tool for doing exactly that. It is clean, Promise-based, and works great with local data files.

By the end of this session you will know how to call `fetch()`, work with the Response object, use `.json()` to parse data, and add error handling with `.catch()`.

---

## Video Tutorial

- video-tabs
- src: source/week 4/Day 1/Fetch.mp4 | Fetch Basics
- src: source/week 4/Day 1/Fetch, the Response object.mp4 | The Response Object
- src: source/week 4/Day 1/Fetch, getting the body content.mp4 | Getting Body Content

Estimated viewing time: 20–25 minutes. Create a small JSON file alongside your HTML and fetch it as you follow along — seeing real data come back makes the ideas click.

---

## Key Concepts Review

### What Is the Fetch API?

The **Fetch API** is the modern, built-in way to load data from a file or server using JavaScript. Before Fetch, developers used `XMLHttpRequest` — a much more complicated tool. Fetch replaced it with a cleaner, Promise-based approach.

You call `fetch(url)` and it returns a **Promise**. That Promise resolves to a **Response object** — which represents the raw response. The Response is not the data yet. You have to call a method on the Response to actually get the data.

---

### The Basic Fetch Pattern

```javascript
fetch("data/products.json")
  .then(response => response.json())
  .then(data => console.log(data))
  .catch(error => console.log("Error:", error));
```

Step by step:
1. `fetch("data/products.json")` — starts the request; returns a Promise
2. `.then(response => response.json())` — when the response arrives, parse it as JSON; this also returns a Promise
3. `.then(data => console.log(data))` — when parsing is done, use the data
4. `.catch(error => console.log("Error:", error))` — if anything in the chain fails, catch it here

---

### The Response Object

The object you receive in the first `.then()` is a **Response**. It is NOT the data yet — it is a description of the response. The most useful properties are:

| Property / Method | What it does |
|---|---|
| `response.ok` | `true` if the status code is between 200 and 299 |
| `response.status` | The numeric status code (200 = OK, 404 = Not Found, etc.) |
| `response.json()` | Returns a Promise that resolves to the parsed JSON object |
| `response.text()` | Returns a Promise that resolves to plain text |

```javascript
fetch("data/products.json")
  .then(response => {
    console.log(response.ok);      // true if successful
    console.log(response.status);  // 200
    return response.json();        // must return this to chain it
  })
  .then(data => console.log("Got data:", data))
  .catch(error => console.log("Fetch failed:", error));
```

Important: you must **return** `response.json()` inside the first `.then()` so the next `.then()` receives the parsed data.

---

### Creating a Local JSON File

In this course we work offline — there is no internet. That is fine! Fetch works perfectly with local JSON files. You just need to run your HTML through a local server (or use the `file://` protocol, depending on your browser and setup).

A JSON file is just a plain text file with structured data. Here is an example `students.json`:

```json
[
  { "name": "Alex Rivera", "grade": "A", "year": 2 },
  { "name": "Jamie Chen", "grade": "B", "year": 1 },
  { "name": "Sam Patel",  "grade": "A", "year": 3 }
]
```

Rules for valid JSON:
- Keys must be in double quotes
- Strings must be in double quotes (not single quotes)
- No trailing commas after the last item
- No comments allowed

---

### Parsing the Data After Fetching

Once you have the data, you can use it just like any JavaScript object or array:

```javascript
fetch("students.json")
  .then(response => response.json())
  .then(students => {
    // students is now a JavaScript array
    const aStudents = students.filter(s => s.grade === "A");
    console.log("A students:", aStudents.length);
    aStudents.forEach(s => console.log(s.name));
  })
  .catch(error => console.log("Could not load students:", error));
```

---

### Using .text() Instead of .json()

If your file contains plain text (not JSON), use `.text()` instead:

```javascript
fetch("notes.txt")
  .then(response => response.text())
  .then(text => console.log(text))
  .catch(error => console.log("Error:", error));
```

Use `.json()` for JSON data, `.text()` for plain text.

---

### Why .catch() Matters

The `.catch()` at the end of a fetch chain handles any error that happens anywhere in the chain:

- The file does not exist
- The JSON is malformed and cannot be parsed
- A network problem (when using a real server)

Without `.catch()`, a failed fetch throws an unhandled Promise rejection — and your code stops working silently.

```javascript
fetch("missing-file.json")
  .then(response => response.json())
  .then(data => console.log(data))
  .catch(error => {
    // This runs if anything above fails
    console.log("Something went wrong:", error.message);
  });
```

---

### Quick Reference

```javascript
// Load a local JSON file
fetch("data.json")
  .then(response => response.json())  // parse JSON
  .then(data => { /* use data */ })
  .catch(error => { /* handle error */ });

// Check the response before parsing
fetch("data.json")
  .then(response => {
    if (!response.ok) {
      throw new Error("HTTP error: " + response.status);
    }
    return response.json();
  })
  .then(data => console.log(data))
  .catch(error => console.log(error.message));
```

---

## Practice Quiz

Take the **Session 22 Practice Quiz** in Canvas before you start the assignment. It is ungraded and you can take it as many times as you like.

The quiz checks your understanding of fetch(), the Response object, JSON files, and error handling with .catch(). If you miss a question, re-read the Key Concepts section above.

---

## Wrap-Up

In this session you learned:

- `fetch(url)` returns a Promise that resolves to a Response object
- The Response is NOT the data — call `.json()` or `.text()` to get the data
- `response.ok` is `true` if the status code is between 200 and 299
- You can fetch local JSON files for offline projects
- JSON files must use double quotes, no trailing commas, no comments
- `.catch()` at the end of the chain handles any errors that occur

Next up is **Session 23: Advanced Fetch and Headers**, where you will add status code checking, work with headers, and combine fetch with async/await.

Nice work. Fetch is one of the most used tools in web development. You now know the fundamentals.

{{include:session-footer}}

{{include:completion-checklist}}
