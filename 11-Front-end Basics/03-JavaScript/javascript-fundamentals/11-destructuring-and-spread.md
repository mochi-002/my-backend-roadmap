## 14. Destructuring Assignment

Modern way to **extract** values from arrays and objects into variables  
→ Cleaner, shorter, and more readable code

### 14.1 Basic Object Destructuring

```javascript
const person = {
  name: "Ahmed",
  age: 28,
  city: "Alexandria"
};

// Old way
const oldName = person.name;
const oldAge = person.age;

// New way (destructuring)
const { name, age, city } = person;

console.log(name);   // "Ahmed"
console.log(age);    // 28
```

### 14.2 Renaming Variables During Destructuring

```javascript
const user = {
  theName: "Osama",
  theAge: 39
};

// Rename while destructuring
const { theName: username, theAge: years } = user;

console.log(username);   // "Osama"
console.log(years);      // 39
```

### 14.3 Destructuring Nested Objects & Arrays (Mixed Content)

```javascript
const user = {
  theName: "Osama",
  theAge: 39,
  skills: ["HTML", "CSS", "JavaScript", "React"],
  addresses: {
    egypt: "Cairo",
    ksa: "Riyadh",
    uae: "Dubai"
  }
};

// Deep destructuring + renaming + skipping array items
const {
  theName: name,              // rename
  theAge: age,
  skills: [, , thirdSkill],   // skip first two → get third
  addresses: { egypt: country }  // nested + rename
} = user;

console.log(`Name: ${name}`);              // Name: Osama
console.log(`Age: ${age}`);                // Age: 39
console.log(`Third Skill: ${thirdSkill}`); // Third Skill: JavaScript
console.log(`Lives in: ${country}`);       // Lives in: Cairo
```

### 14.4 Quick Reference – Most Common Patterns

| Pattern                               | Example Code                                                                 | Result                   |
|---------------------------------------|------------------------------------------------------------------------------|--------------------------|
| Basic object                          | `const {name, age} = user`                                                   | `name`, `age` variables  |
| Rename                                | `const {name: fullName} = user`                                              | `fullName`               |
| Default value                         | `const {job = "Developer"} = user`                                           | `"Developer"` if missing |
| Nested object                         | `const {address: {city}} = user`                                             | `city`                   |
| Array destructuring                   | `const [first, , third] = skills`                                            | Skip second item         |
| Rest in object                        | `const {name, ...rest} = user`                                               | `rest` = remaining props |
| Rest in array                         | `const [head, ...tail] = numbers`                                            | `tail` = rest of array   |

### 14.5 Practical Use Case Example

```javascript
function showUserInfo({
  theName: name,
  theAge: age,
  skills: [, , mainSkill],
  addresses: { egypt: home }
} = {}) {
  console.log(`${name} (${age}) - Main Skill: ${mainSkill}`);
  console.log(`From: ${home}`);
}

showUserInfo(user);
// Output:
// Osama (39) - Main Skill: JavaScript
// From: Cairo
```

**Key Benefits of Destructuring**
- Cleaner function parameters
- Less repetitive code (`user.name` → just `name`)
- Easy to rename variables
- Great for working with APIs & JSON
- Makes nested data much more readable
