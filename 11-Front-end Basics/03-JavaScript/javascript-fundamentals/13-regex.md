### 16.1 Creation Syntax

```javascript
// Literal syntax (most common)
let re = /pattern/flags;

// Constructor syntax
let re = new RegExp("pattern", "flags");
```

**Common Flags (Modifiers)**

| Flag | Description                        | Example             |
|------|------------------------------------|---------------------|
| `i`  | Case-insensitive                   | `/hello/i`          |
| `g`  | Global (find all matches)          | `/a/g`              |
| `m`  | Multiline (^ $ match line starts)  | `/^hello/m`         |

### 16.2 Basic Search Methods

- `string.match(regex)` → returns array of matches or `null`
- `regex.test(string)` → returns `true`/`false`

```javascript
let text = "Hello Elzero Web School I love elzero";
let re = /elzero/ig;

console.log(text.match(re));      // ["elzero", "elzero"]
console.log(re.test(text));       // true
```

### 16.3 Character Ranges & Alternatives

| Pattern    | Meaning              | Example       |
| ---------- | -------------------- | ------------- |
| `(X \| Y)` | X **or** Y           | `/(2 \| 3)/g` |
| `[0-9]`    | Any digit 0–9        | `/[0-9]/g`    |
| `[^0-9]`   | **Not** a digit      | `/[^0-9]/g`   |
| `[a-z]`    | Any lowercase letter | `/[a-z]/g`    |
| `[^a-z]`   | Not lowercase        | `/[^a-z]/g`   |
| `[A-Z]`    | Any uppercase        | `/[A-Z]/g`    |
| `[abc]`    | Only a, b, or c      | `/[abc]/g`    |

**Examples**
```javascript
let str = "AaBbCc123!@#";

console.log(str.match(/[a-z]/g));         // lowercase letters
console.log(str.match(/[^a-z]/g));        // everything except lowercase
console.log(str.match(/[ace]/g));         // only a,c,e
console.log(str.match(/[^a-zA-Z0-9]/g));  // special characters only
```

### 16.4 Character Classes

| Pattern | Description                              |
|---------|------------------------------------------|
| `.`     | Any character except newline             |
| `\w`    | Word character `[a-zA-Z0-9_]`            |
| `\W`    | Non-word character                       |
| `\d`    | Digit `[0-9]`                            |
| `\D`    | Non-digit                                |
| `\s`    | Whitespace (space, tab, newline...)      |
| `\S`    | Non-whitespace                           |

### 16.5 Word Boundaries

| Pattern | Meaning                                   |
|---------|-------------------------------------------|
| `\b`    | Word boundary (start or end of word)      |
| `\B`    | **Not** a word boundary                   |

```javascript
let text = "1Spam Spam2 Spam Spam4";

console.log(text.match(/\bspam\b/gi));     // only "Spam" as whole word
```

### 16.6 Quantifiers

| Quantifier | Meaning                        | Example               |
|------------|--------------------------------|-----------------------|
| `n+`       | 1 or more                      | `/go+/` → "go", "goo" |
| `n*`       | 0 or more                      | `/go*/` → "g", "go"   |
| `n?`       | 0 or 1                         | `/colou?r/`           |
| `n{x}`     | Exactly x times                | `/\d{3}/`             |
| `n{x,y}`   | Between x and y times          | `/\d{2,4}/`           |
| `n{x,}`    | At least x times               | `/\d{4,}/`            |

### 16.7 Anchors & Lookahead

| Symbol   | Meaning                              |
|----------|--------------------------------------|
| `^`      | Start of string/line                 |
| `$`      | End of string/line                   |
| `(?=...)`| Positive lookahead (followed by)     |
| `(?!...)`| Negative lookahead (not followed by) |

```javascript
let names = "1OsamaZ 2AhmedZ 3Mohammed 4MoustafaZ";

console.log(names.match(/\d\w{5}(?=Z)/g));   // names ending with Z
console.log(names.match(/\d\w{8}(?!Z)/g));   // names NOT ending with Z
```

### 16.8 Practical Patterns (Common Use Cases)

```javascript
// Emails (simple version)
const emailRe = /\w+@\w+\.(com|net|org|info)/ig;

// URLs (very basic)
const urlRe = /(https?:\/\/)?(www\.)?\w+\.\w+(\/\S*)?/ig;

// Phone (Egypt example)
const phoneRe = /^(01[0-2,5]\d{8})$/;

// Numbers with exactly 3 digits
const threeDigits = /\b\d{3}\b/g;
```

### 16.9 Replace & ReplaceAll

```javascript
let txt = "We love @ because @ is great";

txt.replace("@", "JS");           // replaces first only
txt.replaceAll("@", "JS");        // replaces all

// With regex
txt.replace(/@/g, "JavaScript");
txt.replaceAll(/@/gi, "JavaScript");
```

### 16.10 Form Validation Example (Phone)

```html
<form id="register">
  <input type="text" id="phone" placeholder="(1234) 567-8910" />
  <input type="submit" value="Register" />
</form>
```

```javascript
document.getElementById("register").onsubmit = function () {
  const phone = document.getElementById("phone").value;
  const phoneRe = /^\(\d{4}\)\s\d{3}-\d{4}$/;
  
  if (!phoneRe.test(phone)) {
    alert("Invalid phone format! Use: (1234) 567-8910");
    return false;
  }
  
  return true;
};
```

**Quick Reference – Most Used Patterns**

| Purpose          | Pattern Example                          | Description                       |
|------------------|------------------------------------------|-----------------------------------|
| Email (simple)   | `\w+@\w+\.\w+`                           | Basic email                       |
| URL              | `(https?:\/\/)?(www\.)?\w+\.\w+`         | http(s), www optional             |
| Digits only      | `\d+`                                    | One or more digits                |
| Word boundary    | `\bword\b`                               | Exact word match                  |
| Starts with      | `^hello`                                 | String starts with "hello"        |
| Ends with        | `world$`                                 | String ends with "world"          |
