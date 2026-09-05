
Functions are **reusable blocks of code**. They can accept **parameters**, return **values**, and be passed around like any variable.

---
## 1. Function Basics

### Syntax
```javascript
function functionName(parameters) {
  // Code block
}
```
### Example

```javascript
function sayHello(userName) {
  console.log(`Hi ${userName}`);
}

sayHello("Osama");
sayHello("Sayed");
sayHello("Ali");
```

- **Parameter** → Variable in function definition (`userName`)
    
- **Argument** → Value passed (`"Osama"`)
    

---

## 2. Function Advanced Example

```javascript
function sayHello(userName, age) {
  if (age < 20) {
    console.log(`App is Not Suitable For You`);
  } else {
    console.log(`Hello ${userName}, Your Age is ${age}`);
  }
}

sayHello("Osama", 38);
sayHello("Ali", 18);

function generateYears(start, end, exclude) {
  for (let i = start; i <= end; i++) {
    if (i === exclude) continue;
    console.log(i);
  }
}

generateYears(1982, 2021, 2020);
```

---

## 3. Return Statement

```javascript
function generate(start, end) {
  for (let i = start; i <= end; i++) {
    if (i === 15) return `Interrupted`;
    console.log(i);
  }
}

generate(10, 20);
```

> `return` stops the function and optionally returns a value.

---

## 4. Default Parameters

```javascript
function sayHello(username = "Unknown", age = "Unknown") {
  return `Hello ${username}, Your Age Is ${age}`;
}

console.log(sayHello());
console.log(sayHello("Osama", 38));
```

> Old strategy: use `age = age || "Unknown";`

---

## 5. Rest Parameters

```javascript
function calc(...numbers) {
  let result = 0;
  for (let num of numbers) {
    result += num;
  }
  return `Final Result Is ${result}`;
}

console.log(calc(10, 20, 10, 30, 50, 30));
```

- `...numbers` gathers all remaining arguments into an array.
    
- Only **one rest parameter allowed**, must be **last**.
    

---

## 6. Anonymous Functions

```javascript
let calculator = function (num1, num2) {
  return num1 + num2;
};

console.log(calculator(10, 20));

// Can pass as callback
setTimeout(function () {
  console.log("Good");
}, 2000);
```

- Functions without names are **anonymous**.
    
- Useful for **callbacks** and **event handlers**.
    

---

## 7. Nested Functions

```javascript
function sayMessage(fName, lName) {
  let message = `Hello`;

  function concatMsg() {
    function getFullName() {
      return `${fName} ${lName}`;
    }
    return `${message} ${getFullName()}`;
  }

  return concatMsg();
}

console.log(sayMessage("Osama", "Mohamed"));
```

- Functions can **return functions** or call **nested functions** internally.
    

---

## 8. Arrow Functions

```javascript
// No parameter
let print = () => 10;

// One parameter
let printOne = num => num;

// Multiple parameters
let sum = (num1, num2) => num1 + num2;

console.log(sum(100, 50));
```

- Arrow functions are **shorter syntax**.
    
- Useful for callbacks and functional programming.
    

---

## 9. Scope

### Global vs Local

```javascript
var a = 1; // Global
let b = 2; // Global

function showText() {
  var a = 10; // Local
  let b = 20; // Local
  console.log(a, b);
}

console.log(a, b);
showText();
```

### Block Scope

```javascript
var x = 10;
if (true) {
  let x = 50;
  console.log(x); // 50
}
console.log(x); // 10
```

### Lexical Scope

```javascript
function parent() {
  let a = 10;
  function child() {
    function grand() {
      let b = 100;
      console.log(a, b);
    }
    grand();
  }
  child();
}
parent();
```

- Functions access **variables from outer scopes** (lexical scope).
    

---

## 10. Higher-Order Functions

Functions that **accept other functions as parameters** or **return functions**.

---

### Map

```javascript
let myNums = [1, 2, 3, 4, 5, 6];
let doubled = myNums.map(ele => ele + ele);
console.log(doubled); // [2,4,6,8,10,12]
```

- Returns **new array**.
    
- Callback receives `(element, index, array)`.
    

---

### Filter

```javascript
let friends = ["Ahmed", "Sameh", "Sayed", "Asmaa", "Amgad", "Israa"];
let aFriends = friends.filter(el => el.startsWith("A"));
console.log(aFriends); // ["Ahmed","Asmaa","Amgad"]

let numbers = [11, 20, 2, 5, 17, 10];
let evenNumbers = numbers.filter(el => el % 2 === 0);
console.log(evenNumbers); // [20, 2, 10]
```

- Returns **new array** of elements that pass the condition.
    

---

### Reduce

```javascript
let nums = [10, 20, 15, 30];
let sum = nums.reduce((acc, current) => acc + current, 5);
console.log(sum); // 80
```

- Reduces array to a **single value**.
    
- Callback receives `(accumulator, current, index, array)`.
    

---

### forEach

```javascript
let allLis = document.querySelectorAll("ul li");
allLis.forEach(ele => {
  ele.onclick = function () {
    allLis.forEach(el => el.classList.remove("active"));
    this.classList.add("active");
  };
});
```

- Executes a function **for each element**.
    
- Returns `undefined`.
    
- **Cannot break** like `for` loop.
    

---