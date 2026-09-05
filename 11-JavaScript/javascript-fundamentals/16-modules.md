## 1. Basic Named Export & Import

**Concept:**

- Export variables or functions from one file (`main.js`)
    
- Import them into another (`app.js`)
    
- Can rename imports using `as`
    

**HTML Setup:**

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <link rel="stylesheet" href="main.css" />
    <title>Learn JavaScript</title>
  </head>
  <body>
    <script src="main.js" type="module"></script>
    <script src="app.js" type="module"></script>
  </body>
</html>
```

**main.js**

```javascript
// Named Exports
let a = 10;
let arr = [1, 2, 3, 4];

function saySomething() {
  return `Something`;
}

// Export variables and function
export { a, arr, saySomething };
```

**app.js**

```javascript
// Import named exports
import { a, arr, saySomething as s } from "./main.js";

console.log(a);       // 10
console.log(arr);     // [1, 2, 3, 4]
console.log(s());     // Something
```

---

## 2. Named + Default Export + Aliases + Import All

**Concept:**

- Use **named exports** (`export { ... }`)
    
- Use **default export** (`export default`)
    
- Use **aliases** (`as`)
    
- Import everything at once with `import * as all`
    

**main.js**

```javascript
// Named export with alias + default export
let a = 10;
let arr = [1, 2, 3, 4];

function saySomething() {
  return `Something`;
}

// Named exports with alias
export { a as myNumber, arr, saySomething };

// Default export
export default function () {
  return `Hello`;
}
```

**app.js**

```javascript
// Way 1: Import default + named exports with alias
// import elzero, { myNumber, arr, saySomething as s } from "./main.js";
// console.log(myNumber);   // 10
// console.log(arr);        // [1,2,3,4]
// console.log(s());        // Something
// console.log(elzero());   // Hello

// Way 2: Import everything at once
import * as all from "./main.js";

console.log(all);          // {myNumber: 10, arr: [...], saySomething: f, default: f}
console.log(all.myNumber); // 10
console.log(all.arr);      // [1,2,3,4]
```

---

### ✅ Key Points Recap

- **Named Export:** `export { variable, function }`
    
- **Default Export:** `export default function()`
    
- **Alias:** `export { a as myNumber }`
    
- **Import:**
    
    - Specific: `import { myNumber } from "./file.js"`
        
    - With default: `import def, { myNumber } from "./file.js"`
        
    - All: `import * as all from "./file.js"`
