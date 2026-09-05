## 1. Data Types & `typeof`

### Data Types

- String
    
- Number
    
- Array → Object
    
- Object
    
- Boolean
    
- `undefined`
    
- `null`
    

```javascript
console.log("Osama Mohamed");
console.log(typeof "Osama Mohamed");
console.log(typeof 5000);
console.log(typeof 5000.99);
console.log(typeof [10, 15, 17]);
console.log(typeof { name: "Osama", age: 17, country: "Eg" });
console.log(typeof true);
console.log(typeof false);
console.log(typeof undefined);
console.log(typeof null);
```

---

## 2. Variables

Variables store data values so we can reuse and manipulate them.

```javascript
var user = "Sayed";
console.log(user);
```

---

## 3. Identifier Rules

Identifiers must follow naming rules (no spaces, no reserved words, no starting with numbers).

```javascript
var userName = "Sayed";
console.log(userName);
```

---

## 4. `var` vs `let` vs `const`
<table style="border-collapse: collapse; width: 100%;">
  <thead>
    <tr style="background-color: #e5e7eb;">
      <th style="border: 1px solid #ccc; padding: 8px;">Feature</th>
      <th style="border: 1px solid #ccc; padding: 8px;">var</th>
      <th style="border: 1px solid #ccc; padding: 8px;">let</th>
      <th style="border: 1px solid #ccc; padding: 8px;">const</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="border: 1px solid #ccc; padding: 8px;">Redeclare</td>
      <td style="border: 1px solid #ccc; padding: 8px;">Yes</td>
      <td style="border: 1px solid #ccc; padding: 8px;">No</td>
      <td style="border: 1px solid #ccc; padding: 8px;">No</td>
    </tr>
    <tr>
      <td style="border: 1px solid #ccc; padding: 8px;">Access before declare</td>
      <td style="border: 1px solid #ccc; padding: 8px;">undefined</td>
      <td style="border: 1px solid #ccc; padding: 8px;">Error</td>
      <td style="border: 1px solid #ccc; padding: 8px;">Error</td>
    </tr>
    <tr>
      <td style="border: 1px solid #ccc; padding: 8px;">Scope</td>
      <td style="border: 1px solid #ccc; padding: 8px;">Function</td>
      <td style="border: 1px solid #ccc; padding: 8px;">Block</td>
      <td style="border: 1px solid #ccc; padding: 8px;">Block</td>
    </tr>
    <tr>
      <td style="border: 1px solid #ccc; padding: 8px;">Reassign</td>
      <td style="border: 1px solid #ccc; padding: 8px;">Yes</td>
      <td style="border: 1px solid #ccc; padding: 8px;">Yes</td>
      <td style="border: 1px solid #ccc; padding: 8px;">No</td>
    </tr>
  </tbody>
</table>

---

## 5. String Syntax & Escape Sequences

Escape sequences allow special characters inside strings.

```javascript
console.log('Elzero Web "School"');
console.log("Elzero Web 'School'");
console.log("Elzero Web \"School\"");
console.log('Elzero \\ Web \'School\'');
console.log("Elzero \
Web \
School");
console.log("Elzero\nWeb\nSchool");
```

---

## 6. Concatenation

```javascript
let a = "We Love";
let b = "JavaScript";

document.write(a + " " + b);
console.log(a, b);
```

---

## 7. Template Literals

Template literals allow interpolation and multiline strings.

```javascript
let a = "We Love";
let b = "JavaScript";
let c = "And";
let d = "Programming";

console.log(a + " \"\" " + b + "\n" + c + " " + d);

console.log(`${a} "" '' \\ ${b}
${c} ${d}`);
```

---

## 8. Template Literals with HTML

```javascript
let title = "Elzero";
let desc = "Elzero Web School";

let markup = `
  <div class="card">
    <div class="child">
      <h2>${title}</h2>
      <p>${desc}</p>
    </div>
  </div>
`;

document.write(markup);
```

---
