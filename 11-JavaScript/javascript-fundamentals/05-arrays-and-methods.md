Arrays are **ordered collections** of elements that can hold any type of data. This guide covers array creation, manipulation, searching, sorting, slicing, and joining.

---

## 1. Array Basics

### Creating Arrays
Two ways to create arrays:

```javascript
let arr1 = new Array(); // Using constructor
let arr2 = [];          // Using literal notation
```
### Accessing Elements

```javascript
let myFriends = ["Ahmed", "Mohamed", "Sayed", ["Marwan", "Ali"]];

console.log(`Hello ${myFriends[0]}`); // Ahmed
console.log(`Hello ${myFriends[2]}`); // Sayed
console.log(`Hello ${myFriends[3][1]}`); // Ali
```

### Modifying Elements

```javascript
myFriends[1] = "Gamal";          // Change element
myFriends[3] = ["Sameh", "Ameer"]; // Change nested array
```

### Checking for Arrays

```javascript
console.log(Array.isArray(myFriends)); // true
```

---

## 2. Array Length

```javascript
let myFriends = ["Ahmed", "Mohamed", "Sayed", "Alaa"];
myFriends.length = 2; // Truncate array
console.log(myFriends); // ["Ahmed", "Mohamed"]
```

> **Note:** Array indices start from `0`.

---

## 3. Adding and Removing Elements

### Methods

|Method|Description|
|---|---|
|`unshift()`|Add elements to the **start**|
|`push()`|Add elements to the **end**|
|`shift()`|Remove **first** element|
|`pop()`|Remove **last** element|

```javascript
let myFriends = ["Ahmed", "Mohamed", "Sayed", "Alaa"];

myFriends.unshift("Osama", "Nabil"); // Add to start
myFriends.push("Samah", "Eman");     // Add to end

let first = myFriends.shift();       // Remove first
let last = myFriends.pop();          // Remove last
```

---

## 4. Searching Arrays

### Methods

|Method|Description|
|---|---|
|`indexOf()`|Returns first index of element|
|`lastIndexOf()`|Returns last index of element|
|`includes()`|Checks if element exists (ES7)|

```javascript
let myFriends = ["Ahmed", "Mohamed", "Sayed", "Alaa", "Ahmed"];

myFriends.indexOf("Ahmed");          // 0
myFriends.indexOf("Ahmed", 2);       // 4
myFriends.lastIndexOf("Ahmed");      // 4
myFriends.includes("Ahmed");         // true

if (myFriends.lastIndexOf("Osama") === -1) {
  console.log("Not Found");
}
```

---

## 5. Sorting Arrays

### Methods

- `sort()` → Sort elements (lexicographically by default)
    
- `reverse()` → Reverse the array
    

```javascript
let myFriends = [10, "Sayed", "Mohamed", "90", 9000, 100, 20, "10", -20, -10];
console.log(myFriends.sort().reverse());
```

> **Note:** For numeric sorting, provide a compare function:  
> `arr.sort((a, b) => a - b);`

---

## 6. Slicing Arrays

### `slice()`

- Returns a **new array**
    
- Syntax: `slice(start?, end?)`
    
- Negative indices count from the **end**
    

```javascript
let myFriends = ["Ahmed", "Sayed", "Ali", "Osama", "Gamal", "Ameer"];

myFriends.slice();      // All elements
myFriends.slice(1);     // From index 1 to end
myFriends.slice(1, 3);  // From 1 to 2
myFriends.slice(-3);    // Last 3 elements
myFriends.slice(1, -2); // From index 1 to third last
```

### `splice()`

- Used for **modifying array**: remove, replace, or add elements
    
- Syntax: `splice(start, deleteCount?, item1?, item2?, ...)`
    

```javascript
myFriends.splice(1, 2, "Sameer", "Samara"); 
// Replace 2 elements starting from index 1
```

---

## 7. Joining Arrays

### `concat()`

- Combine arrays (returns new array)
    

```javascript
let myFriends = ["Ahmed", "Sayed", "Ali", "Osama"];
let newFriends = ["Samar", "Sameh"];
let schoolFriends = ["Haytham", "Shady"];

let allFriends = myFriends.concat(newFriends, schoolFriends, "Gameel", [1, 2]);
```

### `join()`

- Join array elements into a string with a separator
    

```javascript
console.log(allFriends.join());      // Comma-separated
console.log(allFriends.join(""));    // No separator
console.log(allFriends.join(" @ ")); // Custom separator
console.log(allFriends.join("|").toUpperCase()); // Uppercase
```

---
