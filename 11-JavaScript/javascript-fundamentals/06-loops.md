Loops are used to **repeat code multiple times**. JavaScript supports `for`, `while`, `do...while`, and nested loops with loop control (`break`, `continue`, `labels`).

---

## 1. The `for` Loop

### Syntax
```javascript
for (initialization; condition; increment) {
  // Code block
}

Example

for (let i = 0; i < 10; i++) {
  console.log(i);
}
```

- `initialization` → Set starting value (e.g., `let i = 0`)
    
- `condition` → Runs loop while true
    
- `increment` → Changes value each iteration (e.g., `i++`)
    

---

## 2. Looping Over Arrays / Sequences

### Example: Filtering Strings from Mixed Array

```javascript
let myFriends = [1, 2, "Osama", "Ahmed", 3, 4, "Sayed", 6, "Ali"];
let onlyNames = [];

for (let i = 0; i < myFriends.length; i++) {
  if (typeof myFriends[i] === "string") {
    onlyNames.push(myFriends[i]);
  }
}

console.log(onlyNames); // ["Osama", "Ahmed", "Sayed", "Ali"]
```

> **Tip:** Use `for` to iterate when you need **index access**.

---

## 3. Nested Loops

Loops inside loops are **nested loops**.

### Example: Products, Colors, and Models

```javascript
let products = ["Keyboard", "Mouse", "Pen", "Pad", "Monitor"];
let colors = ["Red", "Green", "Black"];
let models = [2020, 2021];

for (let i = 0; i < products.length; i++) {
  console.log("#".repeat(15));
  console.log(`# ${products[i]}`);
  console.log("#".repeat(15));

  console.log("Colors:");
  for (let j = 0; j < colors.length; j++) {
    console.log(`- ${colors[j]}`);
  }

  console.log("Models:");
  for (let k = 0; k < models.length; k++) {
    console.log(`- ${models[k]}`);
  }
}
```

---

## 4. Loop Control: `break`, `continue`, `label`

- **`break`** → Exit the current loop immediately
    
- **`continue`** → Skip to next iteration
    
- **`label`** → Name a loop to control nested loops
    

### Example: Labeled `break`

```javascript
let products = ["Keyboard", "Mouse", "Pen", "Pad", "Monitor"];
let colors = ["Red", "Green", "Black"];

mainLoop: for (let i = 0; i < products.length; i++) {
  console.log(products[i]);
  
  nestedLoop: for (let j = 0; j < colors.length; j++) {
    console.log(`- ${colors[j]}`);
    
    if (colors[j] === "Green") {
      break mainLoop; // Exit the outer loop
    }
  }
}
```

---

## 5. Advanced `for` Loop

You can omit initialization, condition, or increment:

```javascript
let products = ["Keyboard", "Mouse", "Pen", "Pad", "Monitor", "iPhone"];
let i = 0;

for (;;) { // Infinite loop
  console.log(products[i]);
  i++;
  if (i === products.length) break; // Stop condition
}
```

---

## 6. The `while` Loop

Runs **while a condition is true**.

```javascript
let products = ["Keyboard", "Mouse", "Pen", "Pad", "Monitor", "iPhone"];
let index = 0;

while (index < products.length) {
  console.log(products[index]);
  index += 1;
}
```

---

## 7. The `do...while` Loop

Runs **at least once**, then checks the condition.

```javascript
let i = 0;

do {
  console.log(i);
  i++;
} while (false); // Condition false, loop runs only once

console.log(i); // 1
```

> **Tip:** Use `do...while` when the loop must execute **at least once**, regardless of the condition.

---
