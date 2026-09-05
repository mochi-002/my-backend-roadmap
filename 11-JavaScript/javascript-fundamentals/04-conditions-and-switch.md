## Comparison Operators

<table border="1" cellpadding="6" cellspacing="0">
  <thead style="background-color:#f0f0f0;">
    <tr>
      <th>Operator</th>
      <th>Description</th>
    </tr>
  </thead>
  <tbody>
    <tr><td>==</td><td>Equal (value only)</td></tr>
    <tr><td>!=</td><td>Not equal (value only)</td></tr>
    <tr><td>===</td><td>Identical (value + type)</td></tr>
    <tr><td>!==</td><td>Not identical (value + type)</td></tr>
    <tr><td>&gt;</td><td>Larger than</td></tr>
    <tr><td>&gt;=</td><td>Larger than or equal</td></tr>
    <tr><td>&lt;</td><td>Smaller than</td></tr>
    <tr><td>&lt;=</td><td>Smaller than or equal</td></tr>
  </tbody>
</table>

```javascript
console.log(10 == "10");
console.log(-100 == "-100");
console.log(10 != "10");

console.log(10 === "10");
console.log(10 !== "10");
console.log(10 !== 10);

console.log(10 > 20);
console.log(10 >= 10);
console.log(10 < 20);
console.log(10 <= 10);

console.log(typeof "Osama" === typeof "Ahmed");
```
---
## Logical Operators

<table border="1" cellpadding="6" cellspacing="0">
	<thead style="background-color:#f0f0f0;"> <tr> <th>Operator</th> <th>Description</th> </tr> </thead> <tbody> <tr><td>!</td><td>Not</td></tr> <tr><td>&&</td><td>And</td></tr> <tr><td>||</td><td>Or</td></tr> </tbody>
</table>

```javascript
console.log(!true);
console.log(!(10 == "10"));
console.log(10 == "10" && 10 > 8 && 10 > 50);
console.log(10 == "10" || 10 > 80 || 10 > 50);
```

---

## If Conditions

```javascript
let price = 100;
let discount = true;
let discountAmount = 30;
let country = "KSA";

if (discount === true) {
  price -= discountAmount;
} else if (country === "Egypt") {
  price -= 40;
} else if (country === "Syria") {
  price -= 50;
} else {
  price -= 10;
}

console.log(price);
```

---

## Nested If Conditions

```javascript
let price = 100;
let discount = false;
let discountAmount = 30;
let country = "Egypt";
let student = true;

if (discount === true) {
  price -= discountAmount;
} else if (country === "Egypt") {
  if (student === true) {
    price -= discountAmount + 30;
  } else {
    price -= discountAmount + 10;
  }
} else {
  price -= 10;
}

console.log(price);
```

---

## Conditional (Ternary) Operator

```javascript
let theName = "Mona";
let theGender = "Female";
let theAge = 30;

theGender === "Male" ? console.log("Mr") : console.log("Mrs");

let result = theGender === "Male" ? "Mr" : "Mrs";
document.write(result);

console.log(`Hello ${theGender === "Male" ? "Mr" : "Mrs"} ${theName}`);

theAge < 20
  ? console.log(20)
  : theAge > 20 && theAge < 60
  ? console.log("20 To 60")
  : theAge > 60
  ? console.log("Larger Than 60")
  : console.log("Unknown");
```

---

## Nullish Coalescing Operator & Logical Or

```javascript
let price = 0;

console.log(`The Price Is ${price || 200}`);
console.log(`The Price Is ${price ?? 200}`);
```

---
## Switch Statement

- **Syntax:**

```javascript
switch(expression) {
    case value1:
        // Code Block
        break;
    case value2:
        // Code Block
        break;
    default:
        // Code Block
}
```

- **Notes:**
    
    - Default ordering: can appear anywhere, usually last
        
    - Multiple cases can share the same code block
        
    - Comparison uses ===
        

```javascript
let day = "A";

switch (day) {
    default:
        console.log("Unknown Day");
        break;
    case 0:
        console.log("Saturday");
        break;
    case 1:
        console.log("Sunday");
        break;
    case 2:
    case 3:
        console.log("Monday");
        break;
}
```

<table> <tr style="background-color:#f0f0f0"> <th>Case</th> <th>Output</th> </tr> <tr> <td>0</td> <td>Saturday</td> </tr> <tr> <td>1</td> <td>Sunday</td> </tr> <tr> <td>2, 3</td> <td>Monday</td> </tr> <tr> <td>default</td> <td>Unknown Day</td> </tr> </table>
