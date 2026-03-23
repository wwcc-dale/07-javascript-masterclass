---
name: "Solution: Session 22 — Fetch Basics"
published: false
outcomes:
  - 04-MOD
topics:
  - fetch-api
  - json-files
  - promises
---

# Instructor Solution: Session 22 — Fetch Basics

> alert: warning
>
> This page is for instructor reference only. Keep unpublished until after the assignment deadline.

---

## Student Hint

> alert: tip
>
> Your JSON file must be valid JSON — all strings need double quotes (not single), and there can be no trailing comma after the last item. Use `.then(response => response.json())` to parse the response before you try to filter it. To fetch a local file, you must either use VS Code's Live Server extension or run a simple local server — a plain `file://` path may be blocked by the browser's security rules.

---

## Full Solution

Two files: a valid `students.json` data file and an `index.html` with the fetch chain, filter, and error handling.

### `students.json`

```json
[
  { "name": "Alex Chen",    "grade": "A",  "year": 2 },
  { "name": "Sam Torres",   "grade": "B",  "year": 1 },
  { "name": "Jordan Kim",   "grade": "A",  "year": 3 },
  { "name": "Taylor Reyes", "grade": "C",  "year": 2 },
  { "name": "Morgan Patel", "grade": "A",  "year": 1 }
]
```

### `index.html`

```html
<!DOCTYPE html>
<html lang="en">
<head><meta charset="UTF-8"><title>Session 22 — Fetch Basics</title></head>
<body>
  <script>
    // Fetch the local JSON file
    fetch("students.json")
      .then(response => {
        console.log("Status:", response.status, response.ok ? "OK" : "Not OK");
        return response.json();           // returns another Promise
      })
      .then(students => {
        console.log("All students:", students);

        // Filter for A students
        const aStudents = students.filter(s => s.grade === "A");
        console.log("Grade A students:", aStudents.length);
        aStudents.forEach(s => console.log(`  ${s.name} (Year ${s.year})`));

        // Bonus: count by grade
        const gradeCounts = students.reduce((counts, s) => {
          counts[s.grade] = (counts[s.grade] || 0) + 1;
          return counts;
        }, {});
        console.log("Grade distribution:", gradeCounts);
      })
      .catch(error => {
        console.log("Fetch failed:", error.message);
        console.log("Make sure you are running a local server (Live Server).");
      });
  </script>
</body>
</html>
```

---

## Instructor Notes

- **Core:** valid JSON file, `fetch()` call, `.then(r => r.json())` chain, filter for grade A, `forEach` log, `.catch()` present
- **Common mistake:** trying to use `response.json()` without `.then()` — it returns a Promise, not the data directly
- **Common mistake:** invalid JSON — single quotes, trailing commas, or missing quotes around keys — all cause parse errors
- **Common mistake:** opening `index.html` directly in the browser instead of through a server — fetch will fail with a CORS error on `file://`; show students how to use VS Code Live Server
- **Common mistake:** filtering with `==` instead of `===` — both work here but reinforce strict equality
- **Intermediate:** `reduce()` to count students by grade
- **Advanced:** chaining multiple `.then()` transformations and logging intermediate results
