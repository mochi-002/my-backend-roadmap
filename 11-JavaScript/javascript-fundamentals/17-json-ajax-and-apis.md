## 1. JSON Overview

**What is JSON?**

- JavaScript Object Notation
    
- Format for sharing data between server and client
    
- Derived from JavaScript
    
- Alternative to XML
    
- File extension: `.json`
    

**Why JSON?**

- Easy to use and read
    
- Supported by most programming languages and frameworks
    
- Can convert JSON ↔ JS Object easily
    

**JSON vs XML**

|JSON|XML|
|---|---|
|Text-based format|Markup language|
|Lightweight|Heavier|
|No tags|Uses tags|
|Shorter|Not short|
|Can use arrays|Cannot use arrays|
|No comment support|Supports comments|

**Example JSON (`test.json`)**

```json
{
  "widget": {
    "debug": "on",
    "window": {
      "title": "Sample Konfabulator Widget",
      "name": "main_window",
      "width": 500,
      "height": 500
    },
    "image": {
      "src": "Images/Sun.png",
      "name": "sun1",
      "hOffset": 250,
      "vOffset": 250,
      "alignment": "center"
    },
    "text": {
      "data": "Click Here",
      "size": 36,
      "style": "bold",
      "name": "text1",
      "hOffset": 250,
      "vOffset": 100,
      "alignment": "center",
      "onMouseUp": "sun1.opacity = (sun1.opacity / 100) * 90;"
    }
  }
}
```

**Example XML (`test.xml`)**

```xml
<widget>
  <debug>on</debug>
  <window title="Sample Konfabulator Widget">
    <name>main_window</name>
    <width>500</width>
    <height>500</height>
  </window>
  <image src="Images/Sun.png" name="sun1">
    <hOffset>250</hOffset>
    <vOffset>250</vOffset>
    <alignment>center</alignment>
  </image>
  <text data="Click Here" size="36" style="bold">
    <name>text1</name>
    <hOffset>250</hOffset>
    <vOffset>100</vOffset>
    <alignment>center</alignment>
    <onMouseUp>
      sun1.opacity = (sun1.opacity / 100) * 90;
    </onMouseUp>
  </text>
</widget>
```

> **Tip:** To create multiple JSON objects, separate them with commas `,` and wrap in square brackets `[]`.

---

## 2. JSON Syntax & Data Types

**Syntax rules:**

- Use `{}` for objects
    
- Key: `"value"` pairs, keys must be double-quoted
    
- Separate data with commas `,`
    
- `[]` for arrays
    

**Data types:**

- String
    
- Number
    
- Object
    
- Array
    
- Boolean (`true` / `false`)
    
- `null`
    

**Example (`test.json`)**

```json
{
  "string": "Elzero",
  "number": 100,
  "object": { "EG": "Giza", "KSA": "Riyadh" },
  "array": ["HTML", "CSS", "JS"],
  "boolean": true,
  "null": null
}
```

---

## 3. JSON with JavaScript

**Key Methods:**

- `JSON.parse()` → Convert JSON string → JS Object
    
- `JSON.stringify()` → Convert JS Object → JSON string
    

**Example:**

```javascript
// From Server
const myJson = '{"Username": "Osama", "Age": 39}';
console.log(typeof myJson); // string

// Convert to JS Object
const myObj = JSON.parse(myJson);
console.log(typeof myObj); // object
console.log(myObj);

// Update Data
myObj.Username = "Elzero";
myObj.Age = 40;

// Send to Server
const newJson = JSON.stringify(myObj);
console.log(typeof newJson); // string
console.log(newJson);
```

**Useful Links:**

- [GitHub Main API](https://api.github.com/users/elzerowebschool)
    
- [GitHub Repos API](https://api.github.com/users/elzerowebschool/repos)
    
- [MyJSON](https://myjson.dit.upm.es/)
    

---

## 4. Asynchronous vs Synchronous

**Synchronous:**

- Runs operations in sequence
    
- Each operation waits for the previous one
    

**Asynchronous:**

- Runs operations in parallel
    
- Operations can occur while others are being processed
    

**Example:**

```javascript
// Synchronous
console.log("1");
console.log("2");
window.alert("Operation");
console.log("3");

// Asynchronous
console.log("1");
console.log("2");
setTimeout(() => console.log("Operation"), 3000);
console.log("3");
```

---

## 5. Call Stack & Web APIs

**Call Stack (Synchronous Execution)**

- LIFO principle (Last In, First Out)
    
- Functions are added to stack when called, removed after execution
    

**Web API (Browser Environment)**

- Handles asynchronous operations (e.g., `setTimeout`)
    
- Callback is sent to **Callback Queue**
    

**Example:**

```javascript
setTimeout(() => { console.log("Web API"); }, 0);

function one() { console.log("One"); }
function two() { one(); console.log("Two"); }
function three() { two(); console.log("Three"); }

three(); 
// Output: One Two Three Web API
```

---

## 6. Event Loop & Callback Queue

**Flow:**

1. JS is single-threaded
    
2. Call stack executes functions synchronously
    
3. Async functions sent to Web API
    
4. When complete, callbacks go to **Callback Queue**
    
5. Event loop checks stack → adds callbacks
    

**Example:**

```javascript
console.log("One");
setTimeout(() => console.log("Three"), 0);
setTimeout(() => console.log("Four"), 0);
console.log("Two");

// Output: One Two Three Four
```

---

## 7. AJAX (Asynchronous JS & XML)

**Definition:**

- Uses `XMLHttpRequest` to interact with server
    
- Fetch/send data without page refresh
    

**Ready States:**

|Ready State|Description|
|---|---|
|0|Not initialized|
|1|Connection established|
|2|Request received|
|3|Processing request|
|4|Request finished, response ready|

**Status Codes:**

- `200` → Success
    
- `404` → Not found
    

**Basic AJAX Example:**

```javascript
let req = new XMLHttpRequest();
req.open("GET", "https://api.github.com/users/elzerowebschool/repos");
req.send();

req.onreadystatechange = function () {
  if (this.readyState === 4 && this.status === 200) {
    let data = JSON.parse(this.responseText);
    for (let i = 0; i < data.length; i++) {
      let div = document.createElement("div");
      div.textContent = data[i].full_name;
      document.body.appendChild(div);
    }
  }
};
```

**Notes:**

- Handle CORS and API authentication if required
    
- Can loop through data and dynamically update DOM
    

---

## 8. Useful Tools & Links

- [JSON Editor](https://jsoneditoronline.org/)
    
- [MyJSON](https://myjson.dit.upm.es/)