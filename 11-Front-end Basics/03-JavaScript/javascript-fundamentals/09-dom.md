
The **DOM (Document Object Model)** is a **programmatic representation of HTML**. It allows JavaScript to **access, modify, and manipulate HTML elements, attributes, styles, and events**.

---

## 1. What is DOM and Selecting Elements

### DOM Selectors
```javascript
let myIdElement = document.getElementById("my-div");      // By ID
let myTagElements = document.getElementsByTagName("p");   // By Tag Name (HTMLCollection)
let myClassElement = document.getElementsByClassName("my-span"); // By Class Name
let myQueryElement = document.querySelector(".my-span");       // First element matching CSS selector
let myQueryAllElement = document.querySelectorAll(".my-span"); // NodeList of all matching elements

console.log(myIdElement);
console.log(myTagElements[1]);
console.log(myClassElement[1]);
console.log(myQueryElement);
console.log(myQueryAllElement[1]);
```

### Special DOM Properties

```javascript
console.log(document.title);            // Page title
console.log(document.body);             // Body element
console.log(document.forms[0].one.value); // First form, input named 'one'
console.log(document.links[1].href);    // Second link's href
```

> **Tip:** `getElementsByTagName` & `getElementsByClassName` return **live HTMLCollections**. `querySelectorAll` returns a **static NodeList**.

---

## 2. Get / Set Element Content and Attributes

```javascript
let myElement = document.querySelector(".js");

console.log(myElement.innerHTML);   // HTML content
console.log(myElement.textContent); // Plain text

myElement.innerHTML = "Text From <span>Main.js</span>";
myElement.textContent = "Text From <span>Main.js</span>"; // Shows literally

// Manipulate image attributes
document.images[0].src = "https://google.com";
document.images[0].alt = "Alternate";
document.images[0].title = "Picture";
document.images[0].id = "pic";
document.images[0].className = "img";

// Get / Set attributes
let myLink = document.querySelector(".link");
console.log(myLink.getAttribute("href"));
myLink.setAttribute("href", "https://twitter.com");
```

> **Extra Tip:** Use `innerText` to get the visible text, ignoring hidden elements.

---

## 3. Check Attributes

```javascript
let myP = document.getElementsByTagName("p")[0];

console.log(myP.attributes);          // All attributes
console.log(myP.hasAttribute("data-src")); // true/false
console.log(myP.hasAttributes());     // true if any attribute exists

// Update or remove attribute
if (myP.hasAttribute("data-src")) {
  if (myP.getAttribute("data-src") === "") {
    myP.removeAttribute("data-src");
  } else {
    myP.setAttribute("data-src", "New Value");
  }
}
```

---

## 4. Create and Append Elements

```javascript
let myElement = document.createElement("div");
let myText = document.createTextNode("Product One");
let myComment = document.createComment("This Is Div");

// Attributes
myElement.className = "product";
myElement.setAttribute("data-test", "Testing");

// Append content
myElement.appendChild(myComment);
myElement.appendChild(myText);

// Add element to DOM
document.body.appendChild(myElement);
```

> **Extra:** You can also use `insertBefore`, `prepend`, and `append` for flexible placement.

---

## 5. Dealing with Children

```javascript
let myElement = document.querySelector("div");

console.log(myElement.children);          // HTMLCollection of element children
console.log(myElement.childNodes);        // NodeList including text & comment nodes
console.log(myElement.firstChild);        // First node (text, comment, or element)
console.log(myElement.firstElementChild); // First element only
console.log(myElement.lastElementChild);  // Last element only
```

---

## 6. DOM Events

### Basic Events

```javascript
let myBtn = document.getElementById("btn");

myBtn.onclick = () => console.log("Clicked");
myBtn.onmouseleave = () => console.log("Mouse Left");

window.onresize = () => console.log("Window resized");
```

### Form Validation and Prevent Default

```javascript
document.forms[0].onsubmit = function(e) {
  let userInput = this.username.value;
  let ageInput = this.age.value;

  if (!userInput || !ageInput) e.preventDefault(); // Stop submission
};
```

### Event Simulation

```javascript
let one = document.querySelector(".one");
let two = document.querySelector(".two");

window.onload = () => two.focus();

one.onblur = () => document.links[0].click(); // simulate click
```

---

## 7. ClassList Methods

```javascript
let element = document.getElementById("my-div");

element.classList.add("active");
element.classList.remove("old");
element.classList.toggle("show");
console.log(element.classList.contains("show"));
```

---

## 8. CSS Styling

```javascript
element.style.color = "red";
element.style.fontWeight = "bold";

element.style.cssText = "font-weight:bold; color:green; opacity:0.9";
element.style.removeProperty("color");
element.style.setProperty("font-size","40px","important");

// Access stylesheets
document.styleSheets[0].rules[0].style.setProperty("background-color","red","important");
```

---

## 9. Before, After, Prepend, Append, Remove

```javascript
let element = document.getElementById("my-div");
let p = document.createElement("p");

element.append(p);      // Add as last child
element.prepend(p);     // Add as first child
element.before(p);      // Add before element
element.after(p);       // Add after element
// element.remove();    // Remove element
```

---

## 10. DOM Traversing

```javascript
let span = document.querySelector(".two");

console.log(span.parentElement);
console.log(span.nextSibling);
console.log(span.previousElementSibling);

span.onclick = () => span.parentElement.remove();
```

---

## 11. DOM Cloning

```javascript
let myP = document.querySelector("p").cloneNode(true);
myP.id = `${myP.id}-clone`;
document.body.appendChild(myP);
```

- `cloneNode(true)` → deep copy with children
    
- `cloneNode(false)` → shallow copy (no children)
    

---

## 12. addEventListener

```javascript
let myP = document.querySelector("p");

myP.addEventListener("click", () => console.log("Clicked!"));
myP.addEventListener("mouseenter", () => console.log("Mouse Entered"));

// Dynamic event for cloned elements
document.addEventListener("click", e => {
  if(e.target.className === "clone") console.log("I am a cloned element");
});
```

> **Extra Tip:** Prefer `addEventListener` over `onclick` because:
> 
> 1. You can attach multiple handlers.
>     
> 2. Avoid overwriting existing events.
>     
> 3. Offers **capture vs bubbling** phase control.
>     

---
