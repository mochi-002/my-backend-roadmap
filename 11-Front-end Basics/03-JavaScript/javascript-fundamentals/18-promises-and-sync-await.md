## 1. Callbacks & Callback Hell

### What is a Callback?

A **callback** is a function passed into another function to be executed later (usually after an async operation finishes).

### Simple Callback Examples

```javascript
function makeItRed(e) {
  e.target.style.color = "red";
}

let p = document.querySelector(".test");
p.addEventListener("click", makeItRed);

function iamACallback() {
  console.log("Iam A Callback Function");
}

setTimeout(iamACallback, 2000);
```

---

### Callback Hell (Pyramid of Doom)

Deeply nested callbacks become hard to read and maintain.

```javascript
setTimeout(() => {
  console.log("Download Photo From URL");
  setTimeout(() => {
    console.log("Resize Photo");
    setTimeout(() => {
      console.log("Add Logo To The Photo");
      setTimeout(() => {
        console.log("Show The Photo In Website");
      }, 1000);
    }, 1000);
  }, 1000);
}, 1000);
```

❌ Hard to debug  
❌ Hard to scale  
❌ Hard to handle errors

---

## 2. Promises

### Promise Concept

A **Promise** represents a future value.

**States:**

- `pending` → initial
    
- `fulfilled` → success
    
- `rejected` → failure
    

---

### Creating a Promise

```javascript
const myPromise = new Promise((resolve, reject) => {
  let connect = true;
  if (connect) {
    resolve("Connection Established");
  } else {
    reject(Error("Connection Failed"));
  }
});

myPromise.then(
  (res) => console.log(`Good ${res}`),
  (err) => console.log(`Bad ${err}`)
);
```

---

### Promise Chaining

```javascript
const myPromise = new Promise((resolve, reject) => {
  let employees = [];
  if (employees.length === 4) {
    resolve(employees);
  } else {
    reject(Error("Number Of Employees Is Not 4"));
  }
});

myPromise
  .then((data) => {
    data.length = 2;
    return data;
  })
  .then((data) => {
    data.length = 1;
    return data;
  })
  .then((data) => console.log(`Chosen Employee: ${data}`))
  .catch((err) => console.log(err))
  .finally(() => console.log("The Operation Is Done"));
```

---

## 3. Promises with XHR

```javascript
const getData = (apiLink) => {
  return new Promise((resolve, reject) => {
    let req = new XMLHttpRequest();
    req.onload = function () {
      if (this.readyState === 4 && this.status === 200) {
        resolve(JSON.parse(this.responseText));
      } else {
        reject(Error("No Data Found"));
      }
    };
    req.open("GET", apiLink);
    req.send();
  });
};

getData("https://api.github.com/users/elzerowebschool/repos")
  .then((data) => {
    data.length = 10;
    return data;
  })
  .then((data) => console.log(data[0].name))
  .catch((err) => console.log(err));
```

---

## 4. Fetch API

```javascript
fetch("https://api.github.com/users/elzerowebschool/repos")
  .then((res) => res.json())
  .then((data) => {
    data.length = 10;
    console.log(data[0].name);
  });
```

**Fetch returns:**

- A Promise resolving to a **Response object**
    
- `.json()` also returns a Promise
    

---

## 5. Promise Utilities

### `Promise.all`

Fails if **any promise fails**

```javascript
Promise.all([p1, p2, p3]).then(console.log).catch(console.log);
```

---

### `Promise.allSettled`

Returns results of all promises

```javascript
Promise.allSettled([p1, p2, p3]).then(console.log);
```

---

### `Promise.race`

Resolves/rejects with the first finished promise

```javascript
Promise.race([p1, p2, p3]).then(console.log).catch(console.log);
```

---

## 6. Async / Await

### Async Function

- Always returns a Promise
    
- `return` → resolves
    
- `throw` → rejects
    

```javascript
async function getData() {
  let users = [];
  if (users.length > 0) {
    return "Users Found";
  } else {
    throw new Error("No Users Found");
  }
}

getData().then(console.log).catch(console.log);
```

---

### Await

- Used only inside `async`
    
- Waits for a Promise result
    

```javascript
const myPromise = new Promise((resolve, reject) => {
  setTimeout(() => reject(Error("Bad Promise")), 3000);
});

async function readData() {
  console.log("Before Promise");
  console.log(await myPromise.catch((err) => err));
  console.log("After Promise");
}

readData();
```

---

### Async + Try / Catch / Finally

```javascript
async function fetchData() {
  console.log("Before Fetch");
  try {
    let res = await fetch("https://api.github.com/users/elzerowebschool/repos");
    console.log(await res.json());
  } catch (err) {
    console.log(`Reason: ${err}`);
  } finally {
    console.log("After Fetch");
  }
}

fetchData();
```

---

## ✅ Summary

- **Callback** → function executed later
    
- **Callback Hell** → nested callbacks → bad readability
    
- **Promise** → object for async results
    
- **Fetch** → modern API over XHR
    
- **Async/Await** → cleaner promise syntax
    
- **Try/Catch** → async error handling
    
