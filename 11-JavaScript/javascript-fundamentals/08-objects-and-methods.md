Objects are **collections of key-value pairs**. Keys are called **properties** and values can be **data or functions (methods)**.

---
## 1. Object Basics
```javascript
let user = {
  theName: "Osama",
  theAge: 38,
  sayHello: function () {
    return `Hello`;
  },
};

console.log(user.theName); // Osama
console.log(user.theAge);  // 38
console.log(user.sayHello()); // Hello
```

- **Properties**: `theName`, `theAge`
    
- **Methods**: `sayHello()`
    

---

## 2. Dot Notation vs Bracket Notation

```javascript
let myVar = "country";

let user = {
  theName: "Osama",
  country: "Egypt",
};

console.log(user.theName); // Dot notation
console.log(user[myVar]);  // Bracket notation, dynamic property
```

- **Dot notation** → static property name
    
- **Bracket notation** → dynamic property name
    

---

## 3. Nested Objects

```javascript
let user = {
  name: "Osama",
  age: 38,
  skills: ["HTML", "CSS", "JS"],
  available: false,
  addresses: {
    ksa: "Riyadh",
    egypt: { one: "Cairo", two: "Giza" },
  },
  checkAv: function () {
    return this.available ? "Free For Work" : "Not Free";
  },
};

console.log(user.skills.join(" | ")); // HTML | CSS | JS
console.log(user.addresses.egypt.one); // Cairo
console.log(user.checkAv()); // Not Free
```

- Access nested objects via `obj.property1.property2` or `obj["property1"]["property2"]`.
    

---

## 4. Create Object with `new Object()`

```javascript
let user = new Object({ age: 20 });

user.age = 38;
user["country"] = "Egypt";
user.sayHello = function () { return `Hello`; };

console.log(user.age, user.country, user.sayHello());
```

- `new Object()` creates a **new empty object**.
    
- Properties and methods can be **added later**.
    

---

## 5. The `this` Keyword

- Refers to the **object that owns the method**.
    
- In **global context**, `this` refers to `window` (in browsers).
    

```javascript
console.log(this === window); // true

function sayHello() {
  console.log(this); // window
}

let user = {
  age: 38,
  ageInDays: function () {
    return this.age * 365;
  },
};

console.log(user.ageInDays()); // 13870
```

- In **event handlers**, `this` refers to the **element**.
    

---

## 6. Create Object with `Object.create()`

```javascript
let user = {
  age: 20,
  doubleAge: function () { return this.age * 2; },
};

let copyObj = Object.create(user);
copyObj.age = 50;

console.log(copyObj.age);        // 50
console.log(copyObj.doubleAge()); // 100
```

- `Object.create(proto)` creates a **new object with prototype `proto`**.
    

---

## 7. Create Object with `Object.assign()`

```javascript
let obj1 = { prop1: 1, meth1: function () { return this.prop1; } };
let obj2 = { prop2: 2, meth2: function () { return this.prop2; } };

let targetObject = { prop1: 100, prop3: 3 };

let finalObject = Object.assign(targetObject, obj1, obj2);
finalObject.prop4 = 4;
finalObject.prop1 = 200;

console.log(finalObject);
// { prop1: 200, prop3: 3, prop2: 2, meth1: [Function], meth2: [Function], prop4: 4 }

let newObject = Object.assign({}, obj1, { prop5: 5, prop6: 6 });
console.log(newObject);
```

- `Object.assign(target, ...sources)` **copies properties** from source objects to target.
    
- Useful for **merging objects** or **creating shallow copies**.
    

---
