---
bank_name: "Session 24: ES Modules — Practice"
---

1. What attribute must a `<script>` tag have to load a JavaScript module in HTML?
a) `type="script"`
b) `type="import"`
*c) `type="module"`
d) `module="true"`

2. How many default exports can a single JavaScript module file have?
a) Unlimited
b) Two
*c) One
d) Zero

3. Which syntax correctly imports a named export called `add` from a file `math.js`?
a) `import add from "./math.js"`
b) `import (add) from "./math.js"`
*c) `import { add } from "./math.js"`
d) `import * as add from "./math.js"`

4. Which syntax correctly imports a default export from a file `formatter.js`?
*a) `import formatName from "./formatter.js"`
b) `import { formatName } from "./formatter.js"`
c) `import * formatName from "./formatter.js"`
d) `import default formatName from "./formatter.js"`

5. True or false: In a module, you can rename a named import using `as`. For example: `import { add as sum } from "./math.js"`.
*a) True
b) False

6. What does `import * as MathUtils from "./math.js"` do?
a) Imports only the default export of math.js
b) Creates a copy of the math.js file
*c) Imports all exports from math.js and makes them available as properties of the MathUtils object
d) Imports all files in the same folder as math.js

7. True or false: Modules automatically run in strict mode — you do not need to add `"use strict"` yourself.
*a) True
b) False

8. Why do most browsers require modules to be served through a local server rather than opened directly with the file:// protocol?
a) Because modules cannot read JSON files locally
b) Because modules are always encrypted
*c) Because browsers restrict cross-origin requests for file:// URLs, which breaks module loading
d) Because type="module" is not supported without an internet connection

9. What is a "circular import"?
a) An import that is used in a loop
b) An import that loads the same function twice
*c) A situation where Module A imports from Module B, and Module B also imports from Module A
d) An import that re-exports everything from another module

10. In a module file, which keyword marks a function or variable as available to other files?
a) `public`
b) `share`
*c) `export`
d) `module`

11. Which of the following correctly defines and exports a named constant in a module?
a) `module.exports.PI = 3.14`
b) `public const PI = 3.14`
*c) `export const PI = 3.14`
d) `exports PI = 3.14`

12. True or false: A module can have both named exports AND a default export at the same time.
*a) True
b) False

13. You want to import a file's default export AND one of its named exports in the same import statement. Which syntax is correct?
a) `import default, { PI } from "./math.js"`
*b) `import main, { PI } from "./math.js"` (where main is the default export name)
c) `import { default, PI } from "./math.js"`
d) `import * as math, { PI } from "./math.js"`

14. In a re-export statement, what does the following line do?
`export { add } from "./math.js"`
a) It imports add from math.js and uses it in the current file
b) It creates a copy of the add function in the current file
*c) It re-exports add from math.js without importing it for use in the current file
d) It deletes the add export from math.js

15. What is the correct path format required in an import statement when importing from a file in the same folder?
a) `"math.js"` (just the file name)
b) `"/math.js"` (absolute from root)
*c) `"./math.js"` (relative, starting with ./)
d) `"../math.js"` (parent directory)

16. Which syntax exports a single default value from a module?
a) `module.exports = myFunction`
b) `export myFunction`
*c) `export default myFunction`
d) `exports.default = myFunction`

17. Which syntax correctly imports a named export called `add` from `math.js`?
*a) `import { add } from "./math.js"`
b) `import add from "./math.js"`
c) `import { add } from "math"`
d) `require("./math.js").add`

18. What does this code log?
```javascript
// utils.js
export const PI = 3.14159;

// main.js
import { PI } from "./utils.js";
console.log(PI * 2);
```
a) 3.14159
b) PI * 2
*c) 6.28318
d) undefined — you cannot export constants

19. What does this code do?
```javascript
import * as math from "./math.js";
console.log(math.add(2, 3));
```
a) Imports only the `add` function from math.js
*b) Imports everything exported from math.js into one object, then calls the `add` function
c) Causes an error — you cannot use * in imports
d) Imports the default export from math.js

20. True or False: ES modules are loaded automatically in all `<script>` tags without any extra attributes.
True
*False — you must add `type="module"` to the script tag for ES module syntax to work
