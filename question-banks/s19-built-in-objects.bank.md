---
bank_name: "Session 19: Built-in Objects — Practice"
---

1. What does `Math.random()` return?
a) A random integer between 1 and 100
*b) A random decimal number between 0 (inclusive) and 1 (exclusive)
c) A random integer between 0 and 9
d) A random boolean value

2. What does `Math.floor(4.9)` return?
*a) 4
b) 5
c) 4.9
d) 0

3. Which formula generates a random integer between 1 and 6 (like a dice roll)?
*a) `Math.floor(Math.random() * 6) + 1`
b) `Math.round(Math.random() * 6)`
c) `Math.ceil(Math.random() * 6) - 1`
d) `Math.random() * 6`

4. What does `new Date().getMonth()` return for the month of January?
a) 1
*b) 0
c) 12
d) "January"

5. True or False: `new Date().getDay()` returns 0 for Sunday.
*a) True
b) False

6. What does `JSON.stringify({ name: "Alex", age: 20 })` return?
*a) `'{"name":"Alex","age":20}'`
b) `{ name: "Alex", age: 20 }`
c) `["name", "Alex", "age", 20]`
d) `"name: Alex, age: 20"`

7. What does `JSON.parse('{"score":95}')` return?
*a) A JavaScript object with a `score` property equal to 95
b) The string `'{"score":95}'`
c) The number 95
d) An error because JSON must be an array

8. What does `"hello".split("")` return?
*a) `["h", "e", "l", "l", "o"]`
b) `["hello"]`
c) `"h,e,l,l,o"`
d) 5

9. What does `"7".padStart(3, "0")` return?
a) `"700"`
b) `"007."`
*c) `"007"`
d) `"777"`

10. What does `new Set([1, 2, 2, 3, 3, 3])` contain?
a) `[1, 2, 2, 3, 3, 3]`
*b) `{1, 2, 3}` — only unique values
c) `{1, 2, 3, 3, 3}` — only the first duplicate is removed
d) An error because Sets cannot contain numbers

11. How do you convert a Set back to an array?
*a) `[...mySet]` using the spread operator
b) `mySet.toArray()`
c) `Array(mySet)`
d) `mySet.values()`

12. What is the main advantage of a Map over a plain object for storing key-value pairs?
*a) Map keys can be any type (numbers, objects, booleans) — not just strings
b) Maps are faster than objects for all operations
c) Maps allow duplicate keys
d) Maps automatically sort their keys

13. What does `(3.14159).toFixed(2)` return?
*a) `"3.14"` (a string)
b) `3.14` (a number)
c) `3` (a number)
d) `"3.14159"`

14. What does `parseInt("42px")` return?
*a) `42`
b) `"42"`
c) `NaN`
d) `0`

15. True or False: `Number.isNaN("hello")` returns `true`.
a) True
*b) False — `Number.isNaN` only returns true for the actual value `NaN`, not for strings that cannot be converted to numbers

16. What does this code log?
```javascript
const s = new Set([1, 2, 3, 2, 1]);
console.log(s.size);
```
a) 5
*b) 3
c) 2
d) undefined

17. What does this code log?
```javascript
const m = new Map();
m.set("a", 1);
m.set("b", 2);
console.log(m.get("b"));
```
a) "b"
b) 1
*c) 2
d) undefined

18. What does this code log?
```javascript
const data = { name: "Alex", age: 30 };
const str = JSON.stringify(data);
console.log(typeof str);
```
a) "object"
*b) "string"
c) "json"
d) "number"

19. What does this code log?
```javascript
const now = new Date(2000, 0, 1);
console.log(now.getFullYear());
```
a) 0
b) 1
*c) 2000
d) 2001 — months are 0-indexed so January shifts the year

20. What does this code log?
```javascript
console.log(Math.max(3, 1, 4, 1, 5, 9, 2, 6));
```
a) 3
b) 6
*c) 9
d) undefined
