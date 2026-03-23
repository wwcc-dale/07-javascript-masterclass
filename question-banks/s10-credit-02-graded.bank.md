---
bank_name: "Credit 2: Arrays, Loops and Functions — Graded"
---

1. Which of the following correctly creates an array with three items?
*a) `const items = ["a", "b", "c"];`
b) `const items = ("a", "b", "c");`
c) `const items = {0: "a", 1: "b", 2: "c"};`
d) `const items = "a" + "b" + "c";`

2. What index does the LAST item of a 5-item array have?
a) 5
*b) 4
c) -1
d) 6

3. Given `const nums = [10, 20, 30]`, what does `nums[1]` return?
a) 10
*b) 20
c) 30
d) undefined

4. What does `array.length` return?
*a) The number of items in the array
b) The index of the last item
c) The value of the first item
d) The sum of all numeric items

5. Which method adds one or more items to the END of an array?
*a) push()
b) unshift()
c) concat()
d) splice()

6. Which method removes and returns the FIRST item of an array?
a) pop()
*b) shift()
c) splice()
d) delete()

7. What does `concat()` do?
a) Adds an item to the middle of an array
b) Removes items from two arrays
*c) Joins two or more arrays and returns a new array
d) Copies one array into another, changing both

8. True or False: `includes()` returns the index of the item if found.
True
*False

9. What does `indexOf()` return when the item is not found?
a) 0
b) null
*c) -1
d) false

10. True or False: `splice()` modifies the original array.
*True
False

11. Which loop runs its code block at least once before checking the condition?
a) for loop
b) while loop
*c) do...while loop
d) for...of loop

12. What is the correct structure of a `for` loop?
a) `for (condition; update; start)`
*b) `for (start; condition; update)`
c) `for (update; start; condition)`
d) `for (start; update; condition)`

13. What does `break` do inside a loop?
*a) Exits the loop immediately
b) Skips the current iteration
c) Pauses the loop
d) Resets the loop counter to zero

14. What does `continue` do inside a loop?
a) Exits the loop immediately
*b) Skips the rest of the current iteration and moves to the next
c) Breaks out of all nested loops
d) Continues to the next statement after the loop

15. Which loop is best for iterating over every item in an array when you do not need the index?
a) for loop
b) while loop
*c) for...of loop
d) for...in loop

16. True or False: `for...in` is designed for iterating over the keys of an object.
*True
False

17. What causes an infinite loop?
a) Using `const` inside the loop
b) Using a `for...of` loop on an empty array
*c) A condition that never becomes false
d) Forgetting to declare the loop variable

18. Short answer: What is the output of `for (let i = 2; i <= 6; i += 2) { console.log(i); }`?
* 2, 4, 6 — one per line (counts by 2 from 2 to 6 inclusive)

19. What is a function in JavaScript?
*a) A named block of code you define once and can call many times
b) A type of array that stores code
c) A loop that runs automatically when the page loads
d) A special variable that holds a boolean

20. What does `return` do in a function?
a) Starts the function
*b) Sends a value back to whoever called the function and stops the function
c) Logs the value to the console
d) Declares a variable inside the function

21. What is a parameter?
*a) A named variable in the function definition that receives a value when the function is called
b) The actual value passed when calling the function
c) A global variable used inside a function
d) A function with no arguments

22. True or False: Function declarations are hoisted and can be called before they appear in the code.
*True
False

23. Which of the following is an arrow function?
a) `function add(a, b) { return a + b; }`
b) `const add = function(a, b) { return a + b; };`
*c) `const add = (a, b) => a + b;`
d) `add => (a, b) { return a + b; }`

24. What is a default parameter?
*a) A fallback value used when an argument is missing
b) The required first argument of every function
c) A parameter that cannot be reassigned
d) A parameter shared between multiple functions

25. What does a function return if it has no `return` statement?
*a) undefined
b) null
c) 0
d) An empty string

26. True or False: Variables declared inside a function with `let` or `const` are accessible outside that function.
True
*False

27. What is recursion?
a) A loop that runs at least once
*b) A function that calls itself, with a base case to stop
c) A method that reverses an array
d) A way to declare multiple variables at once

28. What happens if a recursive function has no base case?
a) It returns undefined after one call
*b) It calls itself forever until the program crashes
c) It automatically adds a base case
d) It throws a syntax error on the first call

29. Which array method runs a callback for each item but returns no new array?
*a) forEach
b) map
c) filter
d) reduce

30. Which method returns a NEW array where every item has been transformed?
a) forEach
*b) map
c) filter
d) find

31. Which method returns a NEW array with only items that pass a test?
a) map
*b) filter
c) find
d) reduce

32. What does `find` return?
*a) The first item that passes the test, or undefined if none pass
b) All items that pass the test as an array
c) The index of the first matching item
d) A boolean indicating if any item matched

33. Which method is best for calculating a total from an array of numbers?
a) map
b) filter
*c) reduce
d) find

34. What is the starting value in `arr.reduce((total, n) => total + n, 0)`?
a) The first element of arr
*b) 0
c) undefined
d) null

35. True or False: `sort()` with no compare function correctly sorts numbers by numeric value.
True
*False

36. What compare function sorts an array of numbers from largest to smallest?
a) `(a, b) => a - b`
*b) `(a, b) => b - a`
c) `(a, b) => a + b`
d) `(a, b) => 1`

37. True or False: `map` changes the original array.
True
*False

38. True or False: You can chain `filter` and `map` together because both return new arrays.
*True
False

39. Short answer: What is the difference between `map` and `filter`?
* map transforms every item and returns a new array of the same length. filter keeps only items that pass a test and returns a shorter (or same-length) array.

40. Short answer: In the pattern `students.map(s => ({ name: s.name, avg: average(s.scores) }))`, what does `map` do here?
* It creates a new array where each student object is replaced with a new object containing just the student's name and their calculated average.

41. What does this code log?
```javascript
const nums = [3, 1, 4, 1, 5, 9, 2, 6];
console.log(nums.filter(n => n > 4).length);
```
a) 3
*b) 3
c) 4
d) 2

42. What does this code log?
```javascript
const names = ["Charlie", "Alice", "Bob"];
names.sort();
console.log(names[0]);
```
*a) "Alice"
b) "Bob"
c) "Charlie"
d) undefined

43. What does this code log?
```javascript
const nums = [1, 2, 3, 4, 5];
const sum = nums.reduce((acc, n) => acc + n, 10);
console.log(sum);
```
a) 15
*b) 25
c) 10
d) 1

44. What does this code log?
```javascript
function makeMultiplier(factor) {
  return n => n * factor;
}
const triple = makeMultiplier(3);
console.log(triple(7));
```
a) 3
b) 7
*c) 21
d) undefined

45. What does this code log?
```javascript
const fruits = ["apple", "banana", "cherry"];
const [, second] = fruits;
console.log(second);
```
a) "apple"
*b) "banana"
c) "cherry"
d) undefined

46. What does this code log?
```javascript
const grid = [[1,2],[3,4],[5,6]];
const flat = grid.map(row => row[1]);
console.log(flat);
```
a) [1, 3, 5]
*b) [2, 4, 6]
c) [[1,2],[3,4],[5,6]]
d) undefined

47. What does this code log?
```javascript
const scores = [85, 90, 78, 92, 88];
const passing = scores.filter(s => s >= 80);
const avg = passing.reduce((a, b) => a + b, 0) / passing.length;
console.log(avg);
```
a) 86.6
*b) 88.75
c) 85
d) 80

48. What does this code log?
```javascript
(function() {
  const secret = 99;
  console.log(secret * 2);
})();
```
a) An error — IIFE syntax is wrong
b) 99
*c) 198
d) undefined

49. What does this code log?
```javascript
const words = ["banana", "apple", "cherry", "date"];
const found = words.findIndex(w => w.length === 5);
console.log(found);
```
a) "apple"
*b) 1
c) 0
d) -1

50. What does this code log?
```javascript
const arr = [1, 2, 3];
arr.push(arr.shift() + arr.pop());
console.log(arr);
```
a) [1, 2, 3]
b) [2, 4]
*c) [2, 4]
d) [2, 1, 3]
