---
bank_name: "Session 6: Arrays Basics — Practice"
---

1. Which of the following creates an array in JavaScript?
*a) `const list = ["a", "b", "c"];`
b) `const list = ("a", "b", "c");`
c) `const list = {"a", "b", "c"};`
d) `const list = "a", "b", "c";`

2. What index does the first item in a JavaScript array have?
a) 1
*b) 0
c) -1
d) It depends on how the array was created

3. Given `const colors = ["red", "green", "blue"];`, what does `colors[2]` return?
a) "red"
b) "green"
*c) "blue"
d) undefined

4. What does `colors.length` return for an array with 4 items?
a) 3
*b) 4
c) 5
d) The index of the last item

5. Which method adds an item to the END of an array?
*a) `push()`
b) `unshift()`
c) `concat()`
d) `append()`

6. Which method adds an item to the START of an array?
a) `push()`
*b) `unshift()`
c) `prepend()`
d) `shift()`

7. What does `pop()` do?
*a) Removes and returns the last item in the array
b) Removes and returns the first item in the array
c) Adds an item to the end of the array
d) Returns the last item without removing it

8. What does `shift()` do?
a) Removes and returns the last item
*b) Removes and returns the first item
c) Shifts all items one index to the right
d) Adds an item to the start of the array

9. True or False: `concat()` returns a new array without changing the original arrays.
*True
False

10. Given `const a = [1, 2];` and `const b = [3, 4];`, what does `a.concat(b)` return?
a) [1, 2, 3, 4] and it changes `a`
*b) [1, 2, 3, 4] and `a` is unchanged
c) [[1, 2], [3, 4]]
d) [3, 4, 1, 2]

11. What does `includes()` return?
a) The index of the item
*b) `true` or `false`
c) The item itself
d) The number of times the item appears

12. What does `indexOf()` return if the item is NOT found?
a) 0
b) null
c) false
*d) -1

13. What does `splice(1, 2)` do to an array?
a) Inserts 2 items at index 1
*b) Removes 2 items starting at index 1
c) Splits the array at index 1 into 2 arrays
d) Copies items from index 1 to index 2

14. Short answer: If `const fruits = ["apple", "banana", "cherry"]`, what is `fruits[fruits.length - 1]`?
* "cherry" — the last item, because length is 3 and 3-1 is index 2

15. True or False: An array in JavaScript can hold items of different types (strings, numbers, booleans) in the same array.
*True
False

16. What does `Array.isArray("hello")` return?
a) true — "hello" is a sequence of characters, like an array
*b) false — "hello" is a string, not an array
c) undefined
d) An error

17. What does `Array.isArray([1, 2, 3])` return?
*a) true
b) false
c) 3
d) undefined

18. Given `const grid = [[1, 2], [3, 4]];`, what does `grid[1][0]` return?
a) 1
b) 2
*c) 3
d) 4

19. Which line correctly uses array destructuring to put "red" into `first` and "blue" into `second`?
```javascript
const palette = ["red", "blue", "green"];
```
*a) `const [first, second] = palette;`
b) `const {first, second} = palette;`
c) `const first = palette, second = palette;`
d) `const [first][second] = palette;`

20. What does `fill()` do to an array?
a) Returns a new array with all items doubled
*b) Replaces items in the array with a given value — it modifies the original
c) Empties the array
d) Sorts the array alphabetically

21. What does this code log?
```javascript
const nums = [10, 20, 30];
const [a, , c] = nums;
console.log(c);
```
a) 10
b) 20
*c) 30
d) undefined

22. What does this code log?
```javascript
const list = [5, 3, 8, 1];
list.push(list.shift());
console.log(list);
```
a) [5, 3, 8, 1]
b) [3, 8, 1]
*c) [3, 8, 1, 5]
d) [5, 3, 8]

23. What does this code log?
```javascript
const arr = [1, 2, 3, 4, 5];
arr.fill(0, 2, 4);
console.log(arr);
```
a) [0, 0, 0, 0, 0]
b) [1, 2, 3, 4, 5]
*c) [1, 2, 0, 0, 5]
d) [0, 0, 1, 2, 3]

24. What does this code log?
```javascript
const matrix = [[1, 2, 3], [4, 5, 6], [7, 8, 9]];
console.log(matrix[2][1]);
```
a) 6
b) 7
*c) 8
d) 9
