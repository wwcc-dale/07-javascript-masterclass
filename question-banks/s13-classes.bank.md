---
bank_name: "Session 13: Classes — Practice"
---

1. What is a class in JavaScript?
*a) A template for creating objects with shared properties and methods
b) A type of array that holds related values
c) A special kind of function that runs immediately
d) A way to group variables without creating an object

2. Which keyword is used to create a new instance from a class?
*a) `new`
b) `create`
c) `instance`
d) `make`

3. What is the naming convention for JavaScript class names?
*a) They start with a capital letter (PascalCase)
b) They use all lowercase letters
c) They start with an underscore
d) They use ALL_CAPS

4. What is the `constructor` method in a class?
*a) A special method that runs automatically when a new instance is created
b) A method that deletes the instance when it is no longer needed
c) A method that converts the object to a string
d) Any method you define inside a class

5. Inside a class constructor, what does `this` refer to?
*a) The new instance being created
b) The class itself
c) The global window object
d) The previous instance that was created

6. Given `class Dog { constructor(name) { this.name = name; } }`, what does `const d = new Dog("Rex")` create?
*a) A new Dog instance where `d.name` equals "Rex"
b) A new array with one element "Rex"
c) A class called "Rex" that extends Dog
d) An error because constructors do not use parameters

7. How do you add a method called `speak` to a class?
*a) Write `speak() { }` inside the class body, without the `function` keyword
b) Write `function speak() { }` inside the class body
c) Write `this.speak = function() { }` inside the constructor
d) Add it outside the class using `ClassName.speak = function() { }`

8. You create two instances: `const a = new Dog("Rex")` and `const b = new Dog("Bella")`. When you call `a.bark()`, what does `this` refer to?
*a) The `a` instance
b) The `b` instance
c) The Dog class
d) The global scope

9. Which of the following is the correct syntax for a complete class definition?
*a) `class Car { constructor(make) { this.make = make; } drive() { return "driving"; } }`
b) `class car { constructor(make) { car.make = make; } drive() { return "driving"; } }`
c) `Class Car { new(make) { this.make = make; } drive() { return "driving"; } }`
d) `class Car = { constructor(make) { this.make = make; } }`

10. What happens if you define the same method in a class twice?
*a) The second definition overwrites the first
b) Both run when the method is called
c) JavaScript throws an error
d) The first definition is used and the second is ignored

11. What does `instanceof` do?
*a) Checks whether an object was created from a specific class and returns true or false
b) Creates a new instance of a class
c) Returns the number of instances created from a class
d) Deletes an instance from memory

12. A `Rectangle` class has `width` and `height` properties. How would you write an `area()` method that returns the correct value?
*a) `area() { return this.width * this.height; }`
b) `area() { return width * height; }`
c) `area() { return Rectangle.width * Rectangle.height; }`
d) `area() { return area; }`

13. Why is using a class better than manually creating many similar objects?
*a) You write the structure once and create many consistent instances without repeating code
b) Classes run faster than objects
c) Classes allow you to store more data than plain objects
d) Classes automatically save data to a file

14. If you have a `Person` class and you want a person to have a `fullName` property that combines `firstName` and `lastName`, where is the best place to set it up?
*a) In the constructor, using `this.fullName = firstName + " " + lastName`
b) As a separate variable outside the class
c) In a separate `setName()` method that must always be called after `new`
d) Classes cannot combine two values into one property

15. Consider this code: `class Animal { speak() { return "..."; } }`. You create `const cat = new Animal()`. Which line calls the `speak` method on `cat`?
*a) `cat.speak()`
b) `Animal.speak(cat)`
c) `cat->speak()`
d) `speak(cat)`

16. What does this code log?
```javascript
class Rectangle {
  constructor(w, h) {
    this.width = w;
    this.height = h;
  }
  area() {
    return this.width * this.height;
  }
}
const r = new Rectangle(4, 5);
console.log(r.area());
```
a) 4
b) 5
*c) 20
d) undefined

17. What does this code log?
```javascript
class Animal {
  constructor(name) { this.name = name; }
  speak() { return this.name + " makes a sound."; }
}
class Dog extends Animal {
  speak() { return this.name + " barks."; }
}
const d = new Dog("Rex");
console.log(d.speak());
```
a) "Rex makes a sound."
*b) "Rex barks."
c) "Dog barks."
d) undefined

18. What does this code log?
```javascript
class Counter {
  #count = 0;
  increment() { this.#count++; }
  value() { return this.#count; }
}
const c = new Counter();
c.increment();
c.increment();
console.log(c.value());
```
a) 0
b) 1
*c) 2
d) An error — # fields are not valid

19. What does this code log?
```javascript
class Shape {
  constructor(color) { this.color = color; }
}
class Circle extends Shape {
  constructor(color, radius) {
    super(color);
    this.radius = radius;
  }
}
const c = new Circle("red", 5);
console.log(c.color);
```
*a) "red"
b) undefined
c) 5
d) An error — super must be called last

20. True or False: Every class in JavaScript must have a `constructor` method explicitly written.
True
*False
