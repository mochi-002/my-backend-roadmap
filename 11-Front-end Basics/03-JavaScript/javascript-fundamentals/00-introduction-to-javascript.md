# Development Setup & JavaScript Basics

---

## 1. VS Code Extensions

### Recommended Extensions

- Bracket Pair Colorizer 2
    
- EditorConfig
    
- ESLint
    
- GitLens
    
- Indent Rainbow
    
- Live Server
    
- Material Icon Theme
    
- Path Intellisense
    
- Prettier
    
- VS Code Icons
    

---

## 2. Developer Tools

### Chrome DevTools

- [Chrome DevTools — Official Docs](https://developer.chrome.com/docs/devtools/)
    
- [Chrome DevTools — Tips & Tricks](https://www.keycdn.com/blog/chrome-devtools)
    
- [Chrome DevTools — Main Concepts](https://www.bitdegree.org/learn/chrome-developer-tools)
    

---

## 3. Comments & Bad Practices

### JavaScript Comment Types

```javascript
// Wait The Window To Load
window.onload = function () {
  // Single Line Comment
  document.querySelector("h1").style.color = "Blue"; // Inline comment
};

// Single Line Comment
// Single Line Comment

/* Single Line Block Comment */

/*
  Multi-line
  Block
  Comment
*/

// Ctrl + /
```

### Notes

- Avoid excessive commenting of obvious code.
    
- Prefer self-documenting variable and function names.
    
- Use comments for **why**, not **what**.
    

---

## 4. Output to Screen

### Output Methods

```javascript
/*
  Output To Screen
  - window.alert()
  - document.write()
  - console.log()
*/

window.alert("Hello From JS File");

document.write("<h1>Hello <span>Page</span></h1>");

console.log("Hello From JS File");
```

|Method|Purpose|
|---|---|
|`alert()`|Popup message|
|`document.write()`|Writes directly to page (not recommended in production)|
|`console.log()`|Debug output|

---

## 5. Console Methods, Styling & Web API

```javascript
/*
  Console Methods
  - log
  - error
  - table

  Styling Console
  - Directive %c
*/

console.log("Log");
console.error("Error");
console.table(["Osama", "Ahmed", "Sayed"]);

console.log("%cStyled Message", "color: green; font-size: 20px;");
```

### Reference

- [Web API on MDN](https://developer.mozilla.org/en-US/docs/Web/API)
    

---

## 6. What Is ECMAScript?

**ECMAScript (ES)** is the standardized specification that JavaScript is based on.  
ES6 introduced major features like:

- `let` / `const`
    
- Arrow functions
    
- Template literals
    
- Modules
    
- Promises
    

### Example

```javascript
/*
  ES6 Example
*/

var myName = "Osama";

console.log("Hello " + myName);      // Old style
console.log(`Hello ${myName}`);     // Template literal (ES6)
```


### Reference

- [ECMA International](https://www.ecma-international.org/)
	
- [ES6 Features](http://es6-features.org/)
	
- [Babel](https://babeljs.io/repl/)
	
- [Wikipedia](https://en.wikipedia.org/wiki/ECMAScript)
---

## 7. Links
- [[020_Notes/tracks/Fullstack/02-Backend/02-JavaScript/javascript_fundamentals/00_introduction_to_javascript]]
- [[020_Notes/tracks/Fullstack/02-Backend/02-JavaScript/javascript_fundamentals/01_data_types_and_variables]]
- [[020_Notes/tracks/Fullstack/02-Backend/02-JavaScript/javascript_fundamentals/02_operators]]
- [[020_Notes/tracks/Fullstack/02-Backend/02-JavaScript/javascript_fundamentals/03_number_and_string]]
- [[020_Notes/tracks/Fullstack/02-Backend/02-JavaScript/javascript_fundamentals/04_conditions_and_switch]]
- [[020_Notes/tracks/Fullstack/02-Backend/02-JavaScript/javascript_fundamentals/05_arrays_and_methods]]
- [[020_Notes/tracks/Fullstack/02-Backend/02-JavaScript/javascript_fundamentals/06_loops]]
- [[020_Notes/tracks/Fullstack/02-Backend/02-JavaScript/javascript_fundamentals/07_functions]]
- [[020_Notes/tracks/Fullstack/02-Backend/02-JavaScript/javascript_fundamentals/08_objects_and_methods]]
- [[020_Notes/tracks/Fullstack/02-Backend/02-JavaScript/javascript_fundamentals/09_DOM]]
- [[020_Notes/tracks/Fullstack/02-Backend/02-JavaScript/javascript_fundamentals/10_BOM]]
- [[020_Notes/tracks/Fullstack/02-Backend/02-JavaScript/javascript_fundamentals/11_Destructuring & Spread]]
- [[020_Notes/tracks/Fullstack/02-Backend/02-JavaScript/javascript_fundamentals/12_Maps_and_Sets]]
- [[020_Notes/tracks/Fullstack/02-Backend/02-JavaScript/javascript_fundamentals/13_Regex]]
- [[020_Notes/tracks/Fullstack/02-Backend/02-JavaScript/javascript_fundamentals/14_OOP]]
- [[020_Notes/tracks/Fullstack/02-Backend/02-JavaScript/javascript_fundamentals/15_Date_,_Time_,_Generators_&_Modules]]
- [[020_Notes/tracks/Fullstack/02-Backend/02-JavaScript/javascript_fundamentals/16_modules]]
- [[020_Notes/tracks/Fullstack/02-Backend/02-JavaScript/javascript_fundamentals/17_JSON,_AJAX_&_APIs]]
- [[020_Notes/tracks/Fullstack/02-Backend/02-JavaScript/javascript_fundamentals/18_Promises_&_sync_Await]]