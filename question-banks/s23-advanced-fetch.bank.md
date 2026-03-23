---
bank_name: "Session 23: Advanced Fetch and Headers — Practice"
---

1. What HTTP status code means "the resource was not found"?
a) 200
b) 403
*c) 404
d) 500

2. If a fetch request returns a 500 status code, what will happen by default (without any manual checking)?
a) fetch() will throw an error automatically
b) The Promise will reject
*c) The Promise will resolve to a Response object with ok set to false
d) The .catch() handler will run automatically

3. How do you check if a fetch response had a bad status code and throw an error manually?
a) `if (response.status) throw new Error(...)`
b) `if (response.error) throw new Error(...)`
*c) `if (!response.ok) throw new Error("HTTP error: " + response.status)`
d) `if (response.fail) throw new Error(...)`

4. What is the purpose of request headers in a fetch call?
a) They replace the request body
*b) They send metadata with the request, such as the content type or authentication token
c) They tell fetch to ignore errors
d) They set the timeout for the request

5. Which header value tells the server that the request body contains JSON?
a) `"Accept": "application/json"`
b) `"Data-Type": "json"`
*c) `"Content-Type": "application/json"`
d) `"Body-Format": "json"`

6. What are the three required parts of a POST request configuration object passed to fetch?
a) url, data, format
b) action, payload, type
*c) method, headers, body
d) type, content, send

7. How do you convert a JavaScript object to a JSON string for use in a POST request body?
a) `JSON.parse(data)`
b) `data.toString()`
*c) `JSON.stringify(data)`
d) `String(data)`

8. True or false: In an async function, you need two `await` expressions to fetch and parse JSON — one for the fetch and one for `.json()`.
*a) True
b) False

9. What is the advantage of using `async/await` with fetch over using `.then()` chains?
a) async/await is faster than .then() chains
b) async/await handles 404 errors automatically
*c) async/await makes async code read like step-by-step synchronous code and is easier to debug
d) async/await does not require try/catch

10. In an async fetch function that returns `null` on failure, what should the caller check before using the returned value?
a) Check that the value is not `undefined`
b) Check that the value is not `false`
*c) Check that the value is not `null` (or falsy) before processing it
d) No check is needed — null is a safe default value to process

11. What HTTP status code means "the client sent a request with invalid data"?
a) 200
b) 401
*c) 400
d) 403

12. True or false: A status code of 201 means a new resource was successfully created (common for POST requests).
*a) True
b) False

13. In a try/catch inside an async fetch function, which of the following errors will the catch block handle?
a) Only network errors
b) Only errors from response.json()
c) Only errors you throw manually with `throw`
*d) Any error thrown in the try block, including network errors, manual throws, and JSON parse errors

14. What does a status code of 401 mean?
a) The file was not found
*b) Authentication is required — the user is not logged in
c) The server had an internal error
d) The request method is not allowed

15. You want to write a fetch function that returns an empty array if the request fails. What should the `catch` block return?
a) `return false`
b) `return null`
*c) `return []`
d) `return {}`

16. Which fetch option sends a POST request?
a) `{ type: "POST" }`
b) `{ request: "POST" }`
*c) `{ method: "POST" }`
d) `{ send: "POST" }`

17. What does this code do?
```javascript
fetch("api/items", {
  method: "POST",
  headers: { "Content-Type": "application/json" },
  body: JSON.stringify({ name: "Widget" })
});
```
a) Fetches a list of items from the server
*b) Sends a new item to the server as JSON
c) Updates an existing item on the server
d) Deletes an item named "Widget"

18. What does this code log?
```javascript
async function load() {
  const res = await fetch("data.json");
  const data = await res.json();
  return data.length;
}
load().then(n => console.log(n));
```
Assume data.json contains `[1, 2, 3, 4, 5]`
a) "[1, 2, 3, 4, 5]"
b) undefined
*c) 5
d) A Promise

19. What is the purpose of `JSON.stringify()` in a POST request body?
a) To parse JSON text into a JavaScript object
b) To validate that the data is correct
*c) To convert a JavaScript object into a JSON string the server can read
d) To compress the data for faster transfer

20. What does this code log if fetch throws a network error?
```javascript
async function getData() {
  try {
    const res = await fetch("missing.json");
    const data = await res.json();
    console.log(data);
  } catch (e) {
    console.log("Error: " + e.message);
  }
}
getData();
```
a) undefined
b) null
*c) "Error: " followed by the network error message
d) The code crashes — fetch errors cannot be caught with try/catch
