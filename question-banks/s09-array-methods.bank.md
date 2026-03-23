---
bank_name: "Session 9: Higher-Order Array Methods — Practice"
---

1. What is a callback function?
a) A function that returns an array
*b) A function passed as an argument to another function, to be called later
c) A function that calls the main program
d) A built-in function that runs at the end of the program

2. Which method runs a function for each item but does NOT return a new array?
*a) forEach
b) map
c) filter
d) reduce

3. Which method transforms each item and returns a NEW array of the same length?
a) forEach
*b) map
c) filter
d) reduce

4. What does `filter` return?
a) The first item that passes the test
*b) A new array with only the items that pass the test
c) A single combined value
d) The original array with failing items set to null

5. True or False: `filter` can return an array shorter than the original.
*True
False

6. What does `find` return?
a) All items that match the condition
*b) The first item that matches the condition, or `undefined` if none match
c) The index of the first matching item
d) A boolean indicating whether any item matched

7. What is the starting value in this `reduce` call? `arr.reduce((sum, n) => sum + n, 0)`
a) The first element of the array
*b) 0
c) undefined
d) The last element of the array

8. Short answer: What does `map` return?
* A new array where each item has been transformed by the callback function. The original array is unchanged.

9. True or False: `sort` changes the original array (it mutates it).
*True
False

10. What is the correct way to sort an array of numbers from smallest to largest?
a) `arr.sort()`
*b) `arr.sort((a, b) => a - b)`
c) `arr.sort((a, b) => b - a)`
d) `arr.sort("ascending")`

11. What does `arr.sort()` (with no compare function) sort by?
*a) Alphabetical order of the values converted to strings
b) Numeric order from smallest to largest
c) The order items were added to the array
d) It randomly shuffles the items

12. Which method would you use to calculate the total of all numbers in an array?
a) map
b) filter
c) find
*d) reduce

13. True or False: You can chain `map` and `filter` together because both return new arrays.
*True
False

14. Short answer: What is the difference between `filter` and `find`?
* filter returns a new array with ALL matching items. find returns only the FIRST matching item (not an array).

15. Given `const nums = [1, 2, 3, 4, 5]`, what does `nums.map(n => n * n)` return?
a) 55 (the sum of squares)
b) [1, 4, 9, 16, 25] and nums is changed
*c) [1, 4, 9, 16, 25] and nums is unchanged
d) [2, 4, 6, 8, 10]

16. What does this code log?
```javascript
const nums = [3, 1, 4, 1, 5, 9];
const doubled = nums.map(n => n * 2);
console.log(doubled[3]);
```
a) 1
b) 3
*c) 2
d) 4

17. What does this code log?
```javascript
const words = ["apple", "fig", "banana", "kiwi"];
const long = words.filter(w => w.length > 4);
console.log(long.length);
```
a) 4
b) 1
*c) 2
d) 3

18. What does this code log?
```javascript
const nums = [1, 2, 3, 4, 5];
const total = nums.reduce((acc, n) => acc + n, 0);
console.log(total);
```
a) 1
b) 5
*c) 15
d) [1, 2, 3, 4, 5]

19. What does this code log?
```javascript
const scores = [5, 3, 8, 1, 9, 2];
const top = scores.find(s => s > 7);
console.log(top);
```
*a) 8
b) 9
c) [8, 9]
d) undefined

20. What does this code log?
```javascript
const items = ["pen", "pencil", "paper"];
const sorted = [...items].sort();
console.log(sorted[0]);
```
*a) "paper"
b) "pen"
c) "pencil"
d) undefined
