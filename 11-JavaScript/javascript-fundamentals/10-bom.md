# JavaScript – BOM (Browser Object Model)

## 1. What is BOM?

- **BOM** = Browser Object Model  
- Allows JavaScript to **talk to the browser** (outside of the page content = outside of DOM)
- The heart of BOM is the **`window`** object

### Window is the global object in browser environment

```javascript
window === this   // true (in global scope)

// All of these are the same:
window.alert()
alert()
this.alert()
```

**Window contains:**

- The **document** object (DOM)
- All global variables
- All global functions
- History, location, navigator, screen, etc.

## 2. Dialog Boxes

| Method    | Description                          | Return value         |
|-----------|--------------------------------------|----------------------|
| `alert()`     | Simple message + OK button           | `undefined`          |
| `confirm()`   | Yes/No question                      | `true` / `false`     |
| `prompt()`    | Input request                        | `string` or `null`   |

```javascript
if (confirm("Really delete?")) {
  console.log("Deleted!");
}

let name = prompt("Your name?", "Guest");
console.log(name ?? "Cancelled");
```

## 3. Timing Functions

### setTimeout – Run once after delay

```javascript
setTimeout(() => console.log("Hi!"), 2000);

// With arguments + cancel
const id = setTimeout(showMessage, 3000, "Sara", 25);
clearTimeout(id); // cancel
```

### setInterval – Run repeatedly

```javascript
// Countdown example
let count = 10;
const id = setInterval(() => {
  console.log(count);
  count--;
  if (count < 0) clearInterval(id);
}, 1000);
```

## 4. Location Object

**Properties**

- location.href → full URL
- location.protocol → "https:"
- location.host → domain + port
- location.pathname → path
- location.search → ?query=string
- location.hash → `#section`

**Methods**

- location.reload()
- location.assign(url) → navigates + adds to history
- location.replace(url) → navigates without history entry

## 5. Opening & Closing Windows

```javascript
// Open new window
window.open();                            // blank new tab
window.open("https://google.com");        // new tab
window.open("https://google.com", "_blank", "width=400,height=300,left=200,top=100");

// Special targets
window.open("...", "_self");      // current tab
window.open("...", "_parent");
window.open("...", "_top");

// Close current window (only works if opened by script)
window.close();
```

## 6. History Object

**Navigation methods**

- history.back()
- history.forward()
- history.go(-2) ← two pages back
- history.go(0) ← refresh

**Property**

- history.length → number of entries

**Advanced** (look later): `history.pushState()`, `history.replaceState()`

## 7. Other Useful Window Methods

```javascript
window.print();         // open print dialog
window.stop();          // stop page loading (rarely used)
window.focus();         // bring window to front (limited modern browsers)

// Scrolling
window.scrollTo(x, y);
window.scrollTo({ top: 500, left: 0, behavior: "smooth" });
window.scrollBy(0, 300);           // relative scroll
window.scrollBy({ top: 200, behavior: "smooth" });
```

## 8. Scroll-to-Top Button (Classic Pattern)

```javascript
const toTopBtn = document.querySelector(".to-top");

window.addEventListener("scroll", () => {
  toTopBtn.style.display = window.scrollY > 400 ? "block" : "none";
});

toTopBtn.onclick = () => {
  window.scrollTo({ top: 0, behavior: "smooth" });
};
```

## 9. Local Storage

- **What is it?**  
  Browser's built-in key-value storage (strings only).  
  - Persists **forever** (no expiration).  
  - Shared across **all tabs/windows** for the same origin (domain/protocol/port).  
  - Works in HTTP/HTTPS, but **not in private/incognito tabs** (cleared on close).  
  - Capacity: ~5MB per origin (varies by browser).  
  - Synchronous (blocks execution, unlike cookies).  

- **Methods/Properties:**  
  ```javascript
  localStorage.setItem("key", "value");   // Set (overwrites if exists)
  localStorage.getItem("key");            // Get (null if missing)
  localStorage.removeItem("key");         // Delete one
  localStorage.clear();                   // Delete all
  localStorage.key(index);                // Get key at index (0-based)
  localStorage.length;                    // Number of items
  ```

- **Access styles:**  
  ```javascript
  // Set
  localStorage.setItem("color", "#F00");
  localStorage.fontWeight = "bold";       // Dot notation
  localStorage["fontSize"] = "20px";      // Bracket notation

  // Get
  console.log(localStorage.getItem("color"));
  console.log(localStorage.color);
  console.log(localStorage["color"]);

  // Log all
  console.log(localStorage);              // Storage object
  console.log(typeof localStorage);       // "object"
  ```

### Practice: Color Picker with Local Storage

**HTML Structure:**
```html
<!DOCTYPE html>
<html lang="en">
<head>
  <!-- ... meta tags ... -->
  <style>
    body { background-color: #eee; }
    ul {
      padding: 0; margin: 20px auto; padding: 20px; width: 400px;
      list-style: none; display: flex; justify-content: space-between;
      background-color: #ddd;
    }
    ul li {
      width: 60px; height: 60px; border: 2px solid transparent;
      opacity: 0.4; cursor: pointer; transition: 0.3s;
    }
    ul li.active, ul li:hover { opacity: 1; }
    ul li:first-child { background-color: red; }
    ul li:nth-child(2) { background-color: green; }
    ul li:nth-child(3) { background-color: blue; }
    ul li:nth-child(4) { background-color: black; }
    .experiment {
      background-color: red; /* Default */
      width: 600px; height: 300px; margin: 20px auto;
    }
  </style>
</head>
<body>
  <ul>
    <li class="active" data-color="red"></li>
    <li data-color="green"></li>
    <li data-color="blue"></li>
    <li data-color="black"></li>
  </ul>
  <div class="experiment"></div>
  <script src="main.js"></script>
</body>
</html>
```

**JavaScript (main.js):**
```javascript
const lis = document.querySelectorAll("ul li");
const exp = document.querySelector(".experiment");

// Load from storage on page load
if (localStorage.getItem("color")) {
  // Apply saved color
  exp.style.backgroundColor = localStorage.getItem("color");
  
  // Update active class
  lis.forEach(li => li.classList.remove("active"));
  document.querySelector(`[data-color="${localStorage.getItem("color")}"]`)
    .classList.add("active");
}

// Click handler for each li
lis.forEach(li => {
  li.addEventListener("click", (e) => {
    // Remove active from all
    lis.forEach(l => l.classList.remove("active"));
    
    // Add to current
    e.currentTarget.classList.add("active");
    
    // Save & apply color
    const color = e.currentTarget.dataset.color;
    localStorage.setItem("color", color);
    exp.style.backgroundColor = color;
  });
});
```

- **How it works:**  
  - On load: Check `localStorage`, apply color, highlight active `<li>`.  
  - On click: Update UI + save to storage.  
  - Persists across refreshes/reopens.

## 10. Session Storage

- **What is it?**  
  Similar to localStorage, but **session-only**.  
  - Cleared when **tab closes**.  
  - **New tab = new session** (separate storage).  
  - **Duplicate tab** (Ctrl+D) copies current session.  
  - Same origin rules, ~5MB, synchronous.  
  - Use for temp data (e.g., form drafts during session).

- **Methods:** Identical to localStorage!  
  ```javascript
  sessionStorage.setItem("key", "value");
  sessionStorage.getItem("key");
  // ... removeItem, clear, key, length ...
  ```

### Practice: Form Input Persistence

**HTML Snippet:**
```html
<form action="">
  <input type="text" class="name" placeholder="Your name" />
</form>
```

**JavaScript:**
```javascript
const input = document.querySelector(".name");

// Save on blur (focus lost)
input.onblur = function () {
  localStorage.setItem("input-name", this.value);  // Or sessionStorage
};

// Optional: Load on page load
if (localStorage.getItem("input-name")) {
  input.value = localStorage.getItem("input-name");
}

// Compare:
localStorage.setItem("color", "red");   // Persists forever
sessionStorage.setItem("color", "blue"); // Gone on tab close
```

- **Key Differences:**  
	- **Expiration**
	    - Local Storage: Never expires
	    - Session Storage: Cleared when tab is closed
	- **New Tab**
	    - Local Storage: Shared across all tabs (same origin)
	    - Session Storage: Separate for each new tab
	- **Duplicate Tab** (Ctrl+D / Cmd+D)
	    - Local Storage: Shared (same as other tabs)
	    - Session Storage: Copies the data from the original tab
	- **Incognito/Private Mode**
	    - Both: Blocked or cleared when session ends
## Tips & Best Practices

- **Security:** Never store sensitive data (use server-side or encrypted alternatives).  
- **JSON for Objects/Arrays:**  
  ```javascript
  // Save object
  const user = { name: "Osama", age: 38 };
  localStorage.setItem("user", JSON.stringify(user));
  
  // Load
  const savedUser = JSON.parse(localStorage.getItem("user"));
  ```
- **Events:** Listen for changes in other tabs:  
  ```javascript
  window.addEventListener("storage", (e) => {
    console.log(`Key ${e.key} changed from ${e.oldValue} to ${e.newValue}`);
  });
  ```
- **Check Support:**  
  ```javascript
  if (typeof localStorage !== "undefined") {
    // Safe to use
  }
  ```
- **Debug:** DevTools > Application > Storage > Local/Session Storage.