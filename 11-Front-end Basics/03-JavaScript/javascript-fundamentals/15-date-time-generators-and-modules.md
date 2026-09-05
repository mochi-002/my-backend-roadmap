## 1. Date and Time

### 1.1 Basics – Current Date & Epoch Time

**Concept:**

- `new Date()` → Current date & time
    
- `Date.now()` → Milliseconds since Jan 1, 1970 (Epoch time / Unix time)
    
- Convert ms → seconds, minutes, hours, days, years
    

```javascript
let dateNow = new Date();
console.log(dateNow);
console.log(Date.now()); // milliseconds since 1970

let seconds = Date.now() / 1000;
let minutes = seconds / 60;
let hours = minutes / 60;
let days = hours / 24;
let years = days / 365;

console.log(`Seconds: ${seconds}`);
console.log(`Minutes: ${minutes}`);
console.log(`Hours: ${hours}`);
console.log(`Days: ${days}`);
console.log(`Years: ${years}`);
```

---

### 1.2 Getting Date Components

**Methods:**

- `.getTime()` → milliseconds
    
- `.getDate()` → day of month
    
- `.getFullYear()`, `.getMonth()` (0-11), `.getDay()` (0=Sunday)
    
- `.getHours()`, `.getMinutes()`, `.getSeconds()`
    

```javascript
let dateNow = new Date();
let birthday = new Date("Oct 25, 82");
let diff = dateNow - birthday;

console.log(diff); // ms difference
console.log(diff / 1000 / 60 / 60 / 24 / 365); // years difference
console.log(dateNow.getFullYear());
console.log(dateNow.getMonth());
console.log(dateNow.getDay());
console.log(dateNow.getHours());
console.log(dateNow.getMinutes());
console.log(dateNow.getSeconds());
```

---

### 1.3 Setting Date Components

**Methods:**

- `.setTime(ms)` → set timestamp
    
- `.setDate(day)` → day of month (supports overflow & negatives)
    
- `.setFullYear(year, month?, day?)`
    
- `.setMonth(month, day?)`
    
- `.setHours(hour, min?, sec?, ms?)`
    
- `.setMinutes(min, sec?, ms?)`
    
- `.setSeconds(sec, ms?)`
    

```javascript
let dateNow = new Date();
console.log(dateNow);

// Example: Overflowing month
dateNow.setMonth(15); // automatically updates year
console.log(dateNow);
```

---

### 1.4 Creating Dates in Different Ways

```javascript
console.log(Date.parse("Oct 25 1982"));  // ms
console.log(new Date(0));                // Epoch
console.log(new Date(404344800000));     // ms timestamp
console.log(new Date("10-25-1982"));     // string
console.log(new Date("1982-10-25"));     // ISO string
console.log(new Date("1982-10"));        // year + month
console.log(new Date(82));               // year 1982
console.log(new Date(1982, 9, 25, 2, 10, 0)); // y,m,d,h,m,s
console.log(new Date(1982, 9, 25));      // y,m,d
console.log(new Date("1982-10-25T06:10:00Z")); // ISO
```

---

### 1.5 Measuring Execution Time

**Concept:**

- Record start & end time using `new Date()`
    
- Subtract to get duration
    

```javascript
let start = new Date();

// Example operation
for (let i = 0; i < 100000; i++) {
  let div = document.createElement("div");
  div.appendChild(document.createTextNode(i));
  document.body.appendChild(div);
}

let end = new Date();
console.log("Duration (ms):", end - start);
```

---

## 2. Generators

---

### 2.1 Basic Generator + `yield`

**Concept:**

- Pause & resume execution with `yield`
    
- Returns **generator object**
    
- Iterables: `.next()` or `for...of`
    

```javascript
function* generateNumbers() {
  yield 1;
  console.log("Hello after yield 1");
  yield 2;
  yield 3;
  yield 4;
}

let gen = generateNumbers();
console.log(gen.next()); // {value:1, done:false}
console.log(gen.next()); // {value:2, done:false}

for (let val of generateNumbers()) {
  console.log(val);
}
```

---

### 2.2 Delegating Generators (`yield*`)

**Concept:**

- Combine multiple generators using `yield*`
    
- Can yield arrays directly
    
- `.return(value)` stops generator early
    

```javascript
function* nums() { yield 1; yield 2; yield 3; }
function* letters() { yield "A"; yield "B"; yield "C"; }
function* all() {
  yield* nums();
  yield* letters();
  yield* [4, 5, 6];
}

let gen = all();
console.log(gen.next());
console.log(gen.next());
console.log(gen.return("Z")); // stops generator
console.log(gen.next());
```

---

### 2.3 Infinite Generator

**Concept:**

- `while(true)` allows infinite sequence
    
- Each `.next()` gives next value
    

```javascript
function* generateNumbers() {
  let i = 0;
  while (true) yield i++;
}

let gen = generateNumbers();
console.log(gen.next()); // 0
console.log(gen.next()); // 1
console.log(gen.next()); // 2
```

---

### ✅ Key Points Recap

- **Date:** `.getFullYear()`, `.getMonth()`, `.getDate()`, `.setMonth()`, `.setFullYear()`
    
- **Epoch time:** `Date.now()`
    
- **Generators:** `function*`, `yield`, `yield*`, `.next()`, `.return()`
    
- **Infinite sequence:** `while(true)` inside generator