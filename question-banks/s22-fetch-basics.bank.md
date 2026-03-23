---
bank_name: "Session 22: Fetch API Basics — Practice"
---

1. What does `fetch(url)` return?
a) The parsed data from the URL
b) A Response object
*c) A Promise that resolves to a Response object
d) A string containing the raw response body

2. After calling `fetch("data.json")`, what must you do with the Response object to get the actual JSON data?
a) Access `response.data`
b) Call `response.parse()`
*c) Call `response.json()`, which also returns a Promise
d) Pass the response directly to `JSON.parse()`

3. What does `response.ok` tell you?
a) Whether the server is reachable
b) Whether the response body is empty
*c) Whether the status code is between 200 and 299
d) Whether the JSON was parsed successfully

4. Which method on the Response object returns the body as plain text?
a) `response.string()`
b) `response.data()`
*c) `response.text()`
d) `response.body()`

5. True or false: In a `.then()` fetch chain, you must `return` the result of `response.json()` inside the first `.then()` so the next `.then()` receives the parsed data.
*a) True
b) False

6. What is the purpose of `.catch()` at the end of a fetch chain?
a) It runs after every `.then()` regardless of success or failure
b) It only handles network failures, not JSON parse errors
*c) It handles any error that occurs anywhere in the Promise chain
d) It cancels the fetch request if something goes wrong

7. Which of the following is NOT a valid JSON rule?
a) Keys must be in double quotes
b) Strings must be in double quotes
c) No trailing comma after the last item
*d) Comments starting with // are allowed

8. What status code means the request was successful?
*a) 200
b) 201
c) 404
d) 500

9. True or false: `fetch()` automatically throws an error if the server returns a 404 status code.
a) True
*b) False

10. In the following code, what does the second `.then()` receive?
```js
fetch("data.json")
  .then(response => response.json())
  .then(data => console.log(data))
```
a) The raw Response object
b) A Promise
*c) The parsed JavaScript object or array from the JSON file
d) The URL that was fetched

11. Which of the following is a correctly formatted JSON array?
a) `[{ name: 'Alex', age: 20 }]`
b) `[{ "name": "Alex", "age": 20, }]`
*c) `[{ "name": "Alex", "age": 20 }]`
d) `[{ "name": "Alex"; "age": 20 }]`

12. True or false: `response.json()` and `response.text()` both return Promises.
*a) True
b) False

13. What does a status code of 404 mean?
a) The server had an internal error
b) The request was unauthorized
*c) The file or resource was not found
d) The request was successful

14. In this offline course, how does fetch work if there is no internet connection?
a) Fetch does not work at all without internet
b) Fetch only works if you use `response.text()` instead of `response.json()`
*c) Fetch works with local JSON files served from a local server or via the file:// protocol
d) Fetch works but only for files smaller than 10 KB

15. You want to log "Fetch failed: [message]" if a fetch request encounters any error. Where should this logic go?
a) In the first `.then()` after the fetch
b) In the second `.then()` where you receive the data
*c) In a `.catch()` handler at the end of the chain
d) In a `finally()` handler

16. What does `fetch()` return?
a) The response body as a string
b) A JSON object
*c) A Promise
d) undefined

17. What does this code log if the fetch succeeds?
```javascript
fetch("data.json")
  .then(res => res.json())
  .then(data => console.log(typeof data));
```
a) "string"
b) "Promise"
*c) "object"
d) "json"

18. What does `response.ok` tell you?
*a) Whether the HTTP status code is in the 200–299 range
b) Whether the JSON was parsed without errors
c) Whether the network connection is active
d) Whether the response body is non-empty

19. What does this code log if the server returns `{ score: 88 }`?
```javascript
fetch("score.json")
  .then(res => res.json())
  .then(data => console.log(data.score));
```
a) "{ score: 88 }"
b) "data.score"
*c) 88
d) undefined — you must use data["score"] not dot notation

20. What does this code do?
```javascript
fetch("items.json")
  .then(res => {
    if (!res.ok) throw new Error("Not found");
    return res.json();
  })
  .then(data => console.log(data))
  .catch(err => console.log(err.message));
```
a) Logs an error regardless of the response
b) Only works if the status is exactly 200
*c) Checks the response status and throws if not OK, then logs the data or the error message
d) Crashes — you cannot throw inside a .then()
