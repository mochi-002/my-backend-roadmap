---
Content: Browsers
Description: Web browsers request and display websites by interpreting HTML, CSS, and JavaScript. Use rendering engines (Blink, Gecko) for display and JavaScript engines (V8) for code execution. Handle security, bookmarks, history, and user interactions for web navigation.
Resources: 
- "[How The Web Works - The Big Picture](https://www.youtube.com/watch?v=hJHvdBlSxug)"
- "[ACADEMIND || How The Web Works](https://academind.com/tutorials/how-the-web-works)"
---
#### How the **Web** Works – Overview
The web enables **browsers** to request data from **servers** and display it to users in a readable, interactive way.

When you enter a **URL** (e.g., `https://academind.com`) in your browser, a chain of steps happens behind the scenes to fetch, process, and render the website.

---
##### Step 1: **URL Resolution** (DNS Lookup)
- The **domain name** part of the URL (e.g., `academind.com`) must be translated into an **IP address** (e.g., `104.18.26.123`).
- **DNS servers** (Domain Name System) act like internet phonebooks / dictionaries → they map human-readable domain names to numerical IP addresses.
- The browser (or OS/resolver) queries a **DNS server** to resolve the domain → gets the IP before any real request can be sent.

---
##### Step 2: **Sending a Request**
- Once the IP is known, the browser establishes a connection and sends an **HTTP** (or **HTTPS**) request to the server at that IP.
- Requests are structured packets containing:
	- **Method** (e.g., GET, POST)
	- **URL path** (e.g., `/blog/post-1`)
	- **Headers** (e.g., User-Agent, Accept, Authorization)
	- Optional body/data (for POST/PUT/etc.)
- **HTTPS** = encrypted/safe version of HTTP → uses TLS/SSL to protect data in transit (padlock icon!).

---
##### Step 3: **Server Response & Parsing**
- The **server** receives the request, processes it (runs code, queries database, etc.), and sends back an **HTTP response**.
- Response includes:
	- **Status code** (e.g., 200 OK, 404 Not Found, 500 Error)
	- **Headers** (e.g., Content-Type: text/html, Cache-Control)
	- **Body** (the actual content: HTML, JSON, image binary, etc.)
- Browser reads the **Content-Type** header → knows how to handle the body:
	- `text/html` → parse as HTML document
	- `application/json` → treat as data (for APIs)
	- `image/jpeg` → display as image

---
##### Step 4: **Rendering the Page**
- Browser parses the **HTML** to build the DOM (Document Object Model) → defines structure (headings, paragraphs, links, etc.).
- HTML alone has no style → browser looks for linked **CSS** files (via `<link>` tags) and fetches them → applies visual styling (colors, layouts, fonts).
- Additional requests are made for:
	- Images (`<img>`), fonts, videos, etc.
	- JavaScript files (`<script>`) → executed to add interactivity/dynamic behavior.
- JavaScript can run after initial load → fetch more data (AJAX/Fetch), update DOM, handle events, etc.

Modern browsers optimize this heavily (parallel downloads, caching, preloading, etc.).

---
#### **Server-side** vs **Browser-side** (Client-side)
Web apps involve two main environments:

- **Server-side** (Backend):
	- Code runs on the server (e.g., Node.js, PHP, Python/Django/Flask, Ruby, Java, Go).
	- Handles logic, databases, authentication, file storage.
	- Generates responses (HTML, JSON, etc.).

- **Browser-side** (Frontend / Client-side):
	- Core trio: **HTML** (structure) + **CSS** (presentation) + **JavaScript** (behavior).
	- Runs entirely in the user's browser.
	- Parses HTML/CSS/JS, renders visuals, handles user interactions.

Server-side code creates what the browser receives → browser-side code brings it to life on your screen.

---
#### Beyond Static Webpages: **Requests & APIs**
- Not every request returns a full HTML page.
- Many modern sites/apps use **API calls** (often JSON) → return data only (no layout).
- Examples:
	- Mobile apps fetch data via APIs.
	- Single-Page Applications (React/Vue/Angular/Svelte) load once → then use Fetch/AJAX to update parts dynamically without full reloads.
	- Background requests for likes, comments, live updates, search autocomplete, etc.

This is why sites feel fast/responsive today — less full-page reloads, more targeted data exchanges.
