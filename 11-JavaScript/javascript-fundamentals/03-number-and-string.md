# Number

## Basics

- JavaScript numbers are **double-precision floating point**
    
- `_` is numeric separator (visual only)
    
- `e` means exponent (`1e6 = 1 × 10⁶`)
    
- `**` is exponentiation operator
    

```javascript
console.log(1_000_000);
console.log(1e6);
console.log(10 ** 6);

console.log(Number.MAX_SAFE_INTEGER);
console.log(Number.MAX_VALUE);
```

---

## Number Methods

<table border="1" cellpadding="8" cellspacing="0">
  <thead style="background-color: #f0f0f0;">
    <tr>
      <th>Method</th>
      <th>Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><code>toString()</code></td>
      <td>Convert number to string</td>
    </tr>
    <tr>
      <td><code>toFixed(n)</code></td>
      <td>Round to <code>n</code> decimals</td>
    </tr>
    <tr>
      <td><code>parseInt()</code></td>
      <td>Extract integer</td>
    </tr>
    <tr>
      <td><code>parseFloat()</code></td>
      <td>Extract float</td>
    </tr>
    <tr>
      <td><code>Number.isInteger()</code></td>
      <td>Check integer</td>
    </tr>
    <tr>
      <td><code>Number.isNaN()</code></td>
      <td>Check NaN</td>
    </tr>
  </tbody>
</table>

```javascript
console.log((100).toString());
console.log(100.555.toFixed(2));

console.log(parseInt("100 Osama"));
console.log(parseFloat("100.5 Osama"));

console.log(Number.isInteger(100));
console.log(Number.isNaN("Osama" / 2));
```

---

## Math Object

<table border="1" cellpadding="8" cellspacing="0">
  <thead style="background-color: #f0f0f0;">
    <tr>
      <th>Method</th>
      <th>Purpose</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><code>round()</code></td>
      <td>Round normally</td>
    </tr>
    <tr>
      <td><code>ceil()</code></td>
      <td>Round up</td>
    </tr>
    <tr>
      <td><code>floor()</code></td>
      <td>Round down</td>
    </tr>
    <tr>
      <td><code>min()</code></td>
      <td>Minimum</td>
    </tr>
    <tr>
      <td><code>max()</code></td>
      <td>Maximum</td>
    </tr>
    <tr>
      <td><code>pow()</code></td>
      <td>Power</td>
    </tr>
    <tr>
      <td><code>random()</code></td>
      <td>Random number</td>
    </tr>
    <tr>
      <td><code>trunc()</code></td>
      <td>Remove decimals</td>
    </tr>
  </tbody>
</table>

```javascript
console.log(Math.round(99.5));
console.log(Math.ceil(99.1));
console.log(Math.floor(99.9));

console.log(Math.min(10, -5, 100));
console.log(Math.max(10, -5, 100));

console.log(Math.pow(2, 4));
console.log(Math.trunc(99.9));
```

---

# String 
## String Methods — Basic

<table border="1" cellpadding="8" cellspacing="0">
  <thead style="background-color: #f0f0f0;">
    <tr>
      <th>Method</th>
      <th>Purpose</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><code>length</code></td>
      <td>Length of string</td>
    </tr>
    <tr>
      <td><code>trim()</code></td>
      <td>Remove spaces</td>
    </tr>
    <tr>
      <td><code>toUpperCase()</code></td>
      <td>Uppercase</td>
    </tr>
    <tr>
      <td><code>toLowerCase()</code></td>
      <td>Lowercase</td>
    </tr>
    <tr>
      <td><code>charAt()</code></td>
      <td>Character at index</td>
    </tr>
  </tbody>
</table>

```javascript
let name = "  Ahmed  ";

console.log(name.trim());
console.log(name.length);
console.log(name.trim().charAt(0).toUpperCase());
```

---

## String Methods — Search & Slice

<table border="1" cellpadding="8" cellspacing="0">
  <thead style="background-color: #f0f0f0;">
    <tr>
      <th>Method</th>
      <th>Purpose</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><code>indexOf()</code></td>
      <td>First match</td>
    </tr>
    <tr>
      <td><code>lastIndexOf()</code></td>
      <td>Last match</td>
    </tr>
    <tr>
      <td><code>slice()</code></td>
      <td>Extract part</td>
    </tr>
    <tr>
      <td><code>repeat()</code></td>
      <td>Repeat string</td>
    </tr>
    <tr>
      <td><code>split()</code></td>
      <td>Convert to array</td>
    </tr>
  </tbody>
</table>

```javascript
let text = "Elzero Web School";

console.log(text.indexOf("Web"));
console.log(text.lastIndexOf("o"));

console.log(text.slice(2, 6));
console.log(text.repeat(2));
console.log(text.split(" "));
```

---

## String Methods — Advanced

<table border="1" cellpadding="8" cellspacing="0">
  <thead style="background-color: #f0f0f0;">
    <tr>
      <th>Method</th>
      <th>Purpose</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><code>substring()</code></td>
      <td>Extract with index swap</td>
    </tr>
    <tr>
      <td><code>substr()</code></td>
      <td>Extract by length</td>
    </tr>
    <tr>
      <td><code>includes()</code></td>
      <td>Contains</td>
    </tr>
    <tr>
      <td><code>startsWith()</code></td>
      <td>Starts with</td>
    </tr>
    <tr>
      <td><code>endsWith()</code></td>
      <td>Ends with</td>
    </tr>
  </tbody>
</table>

```javascript
let text = "Elzero Web School";

console.log(text.substring(2, 6));
console.log(text.substr(0, 6));

console.log(text.includes("Web"));
console.log(text.startsWith("El"));
console.log(text.endsWith("l"));
```

---
