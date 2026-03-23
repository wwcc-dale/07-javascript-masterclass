---
name: "Solution: Session 23 — Advanced Fetch"
published: false
outcomes:
  - 04-MOD
topics:
  - fetch-api
  - async-await
  - status-codes
  - post-requests
---

# Instructor Solution: Session 23 — Advanced Fetch

> alert: warning
>
> This page is for instructor reference only. Keep unpublished until after the assignment deadline.

---

## Student Hint

> alert: tip
>
> Replace `.then()` chains with `async function loadStudents()`. After `await fetch(url)`, check `response.ok` before calling `response.json()` — if not ok, throw an error using the status code. For the POST request, build the config object with `method`, `headers`, and `body` (use `JSON.stringify()` for the body), then log it instead of sending it.

---

## Full Solution

A single `index.html` file. It reuses the `students.json` from the previous assignment. It includes a reusable `fetchJSON` helper, `response.ok` checking, status code mapping, a simulated POST config, and an error path test.

### `index.html`

```html
<!DOCTYPE html>
<html lang="en">
<head><meta charset="UTF-8"><title>Session 23 — Advanced Fetch</title></head>
<body>
  <script>
    // Reusable fetch helper with error checking
    async function fetchJSON(url) {
      const response = await fetch(url);
      if (!response.ok) {
        const message = statusMessage(response.status);
        throw new Error(`HTTP ${response.status}: ${message}`);
      }
      return response.json();
    }

    function statusMessage(code) {
      switch (true) {
        case code === 400: return "Bad Request — check your request format";
        case code === 401: return "Unauthorized — you need to log in";
        case code === 403: return "Forbidden — you do not have permission";
        case code === 404: return "Not Found — the file or resource does not exist";
        case code >= 500:  return "Server Error — something went wrong on the server";
        default: return "Unexpected status";
      }
    }

    // Load and process students using async/await
    async function loadStudents() {
      try {
        const students = await fetchJSON("students.json");
        console.log("Loaded:", students.length, "students");

        const aStudents = students.filter(s => s.grade === "A");
        console.log("Grade A students:");
        aStudents.forEach(s => console.log(`  ${s.name}`));

        return students;
      } catch (error) {
        console.log("Failed to load students:", error.message);
        return [];
      }
    }

    // Simulate a POST request — build and log the config without sending
    function buildPostRequest(endpoint, data) {
      const config = {
        method:  "POST",
        headers: {
          "Content-Type": "application/json",
          "Accept":       "application/json"
        },
        body: JSON.stringify(data)
      };
      console.log(`\nSimulated POST to "${endpoint}":`);
      console.log("Config:", config);
      console.log("Body (parsed back):", JSON.parse(config.body));
      // In a real application: return fetch(endpoint, config);
      return config;
    }

    // Run
    loadStudents().then(students => {
      console.log("\n--- Simulated POST ---");
      buildPostRequest("/api/students", {
        name:  "Casey Nguyen",
        grade: "B",
        year:  1
      });
    });

    // Test error path: fetch a file that does not exist
    async function testErrorPath() {
      try {
        await fetchJSON("does-not-exist.json");
      } catch (error) {
        console.log("\nExpected error caught:", error.message);
      }
    }
    testErrorPath();
  </script>
</body>
</html>
```

---

## Instructor Notes

- **Core:** `async` function, `response.ok` check before `.json()`, `try/catch`, POST config object built and logged, status code handling
- **Common mistake:** calling `response.json()` even when `response.ok` is false — this may work but gives confusing error data; the check should come first
- **Common mistake:** throwing a string instead of an Error object: `throw "error"` — use `throw new Error("message")`
- **Common mistake:** `JSON.stringify(data)` missing from the POST body — the body must be a string, not an object
- **Common mistake:** actually trying to send the POST request with `fetch()` — on a local server with no API it will fail; the assignment asks to log the config only
- **Intermediate:** a reusable `fetchJSON(url)` helper function that handles status checking
- **Advanced:** `statusMessage()` function mapping codes to human-readable messages; retry logic on failure
