---
name: "Session 23: Advanced Fetch and Headers"
published: false
outcomes:
  - 04-MOD
topics:
  - fetch-api
  - status-codes
  - headers
  - async-await
  - post-requests
---

[lead]You know the basics of fetch — now take it further. Today you will check status codes, work with request headers, build a POST request, and rewrite your fetch calls using async/await for cleaner code.

# Session 23: Advanced Fetch and Headers

Session 22 got you started with fetch. Now you will learn to handle it like a professional. Real applications check whether the response was actually successful before trying to use the data. They send headers with requests. And most modern code uses async/await instead of chained `.then()` calls.

By the end of this session you will be able to check HTTP status codes, add headers to a fetch request, structure a POST request, and write async functions that fetch data using await with proper error handling.

---

## Video Tutorial

- video-tabs
- src: source/week 4/Day 1/Fetch, the Response object.mp4 | Response and Status
- src: source/week 4/Day 1/Fetch, setting the request headers.mp4 | Request Headers
- src: source/week 4/Day 1/Fetch POST requests.mp4 | POST Requests

Estimated viewing time: 20–25 minutes. Pay special attention to how async/await changes the shape of the code compared to .then() chains — type both versions to feel the difference.

---

## Key Concepts Review

### HTTP Status Codes

When a server (or the browser's file system) responds to a request, it sends back a **status code** — a number that tells you what happened.

| Code | Meaning |
|---|---|
| 200 | OK — the request worked |
| 201 | Created — a new resource was created (common for POST) |
| 400 | Bad Request — the request had invalid data |
| 401 | Unauthorized — login required |
| 403 | Forbidden — logged in but not allowed |
| 404 | Not Found — the file or resource does not exist |
| 500 | Internal Server Error — the server had a problem |

**Fetch does not automatically throw an error for 4xx and 5xx codes.** You have to check `response.ok` yourself and throw if it is false:

```javascript
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

This is important: if you fetch a file that does not exist, `response.ok` is `false` (status 404), but the Promise still resolves — you have to check it yourself.

---

### Request Headers

**Headers** are key-value pairs of metadata that travel with HTTP requests and responses. They tell the server (or the browser) things like:

- What format the data is in (`Content-Type`)
- What format the client can accept (`Accept`)
- Authentication tokens
- Cache preferences

You add headers to a fetch call by passing an options object as the second argument:

```javascript
fetch("data.json", {
  headers: {
    "Accept": "application/json"
  }
})
  .then(response => response.json())
  .then(data => console.log(data));
```

For most simple GET requests loading local JSON files, you do not need headers. They become essential for POST requests and real APIs.

---

### POST Requests with Fetch

A **GET** request reads data. A **POST** request sends data to a server (for example, submitting a form or creating a new record).

To make a POST request, pass an options object with `method`, `headers`, and `body`:

```javascript
const newStudent = { name: "Jordan Park", grade: "A", year: 1 };

fetch("api/students", {
  method: "POST",
  headers: {
    "Content-Type": "application/json"
  },
  body: JSON.stringify(newStudent)
})
  .then(response => {
    if (!response.ok) throw new Error("POST failed: " + response.status);
    return response.json();
  })
  .then(result => console.log("Server said:", result))
  .catch(error => console.log("Error:", error.message));
```

Key parts:
- `method: "POST"` — tells fetch to use POST instead of GET
- `headers: { "Content-Type": "application/json" }` — tells the server the body is JSON
- `body: JSON.stringify(newStudent)` — converts the JavaScript object to a JSON string

**Offline note:** Since this course runs on a local network without a live server, POST requests will not actually send anywhere. You can still write and log the full request configuration object to practice the syntax and understand how it works.

---

### async/await with Fetch

You already know async/await from Session 18. Fetch works perfectly with it — and most modern code uses this pattern instead of `.then()` chains because it reads more like regular step-by-step code.

```javascript
async function loadData(url) {
  try {
    const response = await fetch(url);

    if (!response.ok) {
      throw new Error("HTTP error: " + response.status);
    }

    const data = await response.json();
    return data;

  } catch (error) {
    console.log("Failed to load data:", error.message);
    return null;
  }
}

loadData("students.json").then(students => {
  if (students) console.log("Loaded:", students.length, "students");
});
```

Notice:
- `await fetch(url)` pauses until the response arrives
- `await response.json()` pauses until the JSON is parsed
- The `try/catch` wraps everything — no separate `.catch()` needed
- The function returns `null` on failure so callers can check for it

---

### Combining Status Check + async/await

Here is a full pattern you can reuse for almost any fetch situation:

```javascript
async function getStudents(url) {
  try {
    const response = await fetch(url);

    if (!response.ok) {
      if (response.status === 404) {
        throw new Error("File not found (404). Check the file name.");
      }
      throw new Error("Unexpected error: " + response.status);
    }

    const students = await response.json();
    console.log("Loaded", students.length, "students");
    return students;

  } catch (error) {
    console.log("getStudents failed:", error.message);
    return [];
  }
}
```

This pattern:
1. Awaits the response
2. Checks `response.ok` and throws a specific message for common errors
3. Awaits the JSON parse
4. Catches any errors from any step in one place
5. Returns a safe fallback value (empty array) on failure

---

### Quick Reference

```javascript
// Check status before parsing
if (!response.ok) throw new Error("HTTP error: " + response.status);

// POST request
fetch(url, {
  method: "POST",
  headers: { "Content-Type": "application/json" },
  body: JSON.stringify(data)
});

// async/await pattern
async function load(url) {
  try {
    const res = await fetch(url);
    if (!res.ok) throw new Error("Status: " + res.status);
    const data = await res.json();
    return data;
  } catch (e) {
    console.log(e.message);
    return null;
  }
}
```

---

## Practice Quiz

Take the **Session 23 Practice Quiz** in Canvas before you start the assignment. It is ungraded and you can take it as many times as you like.

The quiz checks your understanding of status codes, headers, POST requests, and async/await with fetch. If you miss a question, re-read the Key Concepts section above.

---

## Wrap-Up

In this session you learned:

- HTTP status codes tell you what happened: 200 = OK, 404 = Not Found, 500 = Server Error
- Fetch does NOT automatically throw for 4xx/5xx codes — you must check `response.ok`
- Headers are metadata attached to requests — use them for POST and when communicating with APIs
- A POST request uses `method: "POST"`, a JSON header, and a stringified body
- `async/await` with `try/catch` is the cleanest way to write fetch code
- A good async fetch function awaits the response, checks `response.ok`, awaits the JSON, and returns a safe fallback on failure

Next up is **Session 24: ES Modules**, where you will organize your code into multiple files that import and export from each other.

You are building real professional skills now. Keep it up.

{{include:session-footer}}

{{include:completion-checklist}}
