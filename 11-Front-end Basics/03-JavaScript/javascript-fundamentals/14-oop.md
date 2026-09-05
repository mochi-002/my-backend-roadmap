## 1. What Is OOP?

OOP (Object-Oriented Programming) is a programming style where we organize our program using **objects** instead of only functions and variables.

**An object groups:**

- **Data** → properties
- **Behavior** → methods

This approach makes large programs easier to reason about, extend, and maintain.

> **Note:** Think of objects as real-world entities. A "User" object might have properties like name and age, and behaviors like login() or logout().

---

## 2. Why We Use OOP?

We use OOP to:

- Build large systems in a structured way
- Hide internal complexity (encapsulation)
- Reuse code (inheritance)
- Reduce bugs and improve maintainability

> OOP exists to solve problems of scale and complexity.

|Problem|OOP Solution|
|---|---|
|Code duplication|Inheritance & composition|
|Hard to maintain code|Encapsulation|
|Spaghetti logic|Clear object responsibilities|
|Unsafe data access|Private fields|

**Key Benefit:** As your application grows, OOP helps you organize code into logical, manageable pieces rather than having thousands of scattered functions.

---

## 3. Creating Objects with a Constructor Function

Before `class` syntax, JavaScript used constructor functions.

```js
function User(id, username, salary) {
  this.i = id;
  this.u = username;
  this.s = salary + 1000;
}

let userOne = new User(100, "Elzero", 5000);
let userTwo = new User(101, "Hassan", 6000);
let userThree = new User(102, "Sayed", 7000);

console.log(userOne.i);        // 100
console.log(userOne.u);        // "Elzero"
console.log(userOne.s);        // 6000
```

**How it works:**

- The `new` keyword creates a new empty object
- Binds `this` to that new object
- Executes the constructor function
- Returns the new object

> **Historical Note:** This was the traditional way before ES6 introduced the `class` keyword in 2015.

---

## 4. Using Classes (Modern Syntax)

`class` is a cleaner way to write constructor functions. It's syntactic sugar over the prototype-based approach.

```js
class User {
  constructor(id, username, salary) {
    this.i = id;
    this.u = username;
    this.s = salary + 1000;
  }
}

let userOne = new User(100, "Elzero", 5000);

console.log(userOne instanceof User);        // true
console.log(userOne.constructor === User);   // true
```

**Why use classes?**

- Cleaner, more readable syntax
- Familiar to developers from other languages (Java, C++, Python)
- Makes inheritance easier to understand

---

## 5. Properties vs Methods

**Understanding the Difference**

There are two ways to define functions in classes, and they have different memory implications:

|Type|Stored where|Memory|When to use|
|---|---|---|---|
|Method (`writeMsg`)|Prototype|Shared across all instances|Default choice|
|Function in constructor (`this.msg`)|Instance|Duplicated for each object|When you need closure over constructor variables|

**Rule of thumb:**  
Put methods on the prototype unless you need access to constructor-scoped variables.

```js
class User {
  constructor(id, username, salary) {
    this.i = id;
    this.u = username || "Unknown";
    this.s = salary < 6000 ? salary + 500 : salary;
    
    // ❌ This function is duplicated for EVERY instance
    this.msg = function () {
      return `Hello ${this.u} Your Salary Is ${this.s}`;
    };
  }

  // ✅ This method is shared across ALL instances (better!)
  writeMsg() {
    return `Hello ${this.u} Your Salary Is ${this.s}`;
  }
}

let userOne = new User(100, "Elzero", 5000);
console.log(userOne.msg());       // Works, but less efficient
console.log(userOne.writeMsg());  // Works, and more efficient
```

**Performance Impact:** If you create 1000 User objects, the `msg` function gets duplicated 1000 times in memory, while `writeMsg` exists only once on the prototype.

---

## 6. Updating Object Data

Objects are mutable — we can change their properties after creation.

```js
class User {
  constructor(id, username, salary) {
    this.i = id;
    this.u = username;
    this.s = salary;
  }

  updateName(newName) {
    this.u = newName;
  }
}

let userOne = new User(100, "Elzero", 5000);
console.log(userOne.u);  // "Elzero"

userOne.updateName("Osama");
console.log(userOne.u);  // "Osama"
```

**Best Practice:** Create methods to update properties rather than modifying them directly. This allows you to add validation or trigger side effects when data changes.

---

## 7. Static Properties and Methods

Static members belong to the **class itself**, not to instances.

**Use static when:**

- The behavior is related to the concept, not to one object
- You need shared counters, utilities, or factories
- You want to create helper functions related to the class

**Example uses:**

- Tracking created instances
- Utility functions
- Validation helpers
- Factory methods

```js
class User {
  static count = 0;

  constructor(id, username, salary) {
    this.i = id;
    this.u = username;
    this.s = salary;
    User.count++;  // Increment the static counter
  }

  static sayHello() {
    return `Hello From Class`;
  }

  static countMembers() {
    return `${this.count} Members Created`;
  }
}

let userOne = new User(100, "Elzero", 5000);
let userTwo = new User(101, "Ahmed", 5000);

console.log(User.count);           // 2
console.log(User.sayHello());      // "Hello From Class"
console.log(User.countMembers());  // "2 Members Created"
```

**Important:** You call static methods on the class itself (`User.sayHello()`), not on instances (`userOne.sayHello()` won't work).

---

## 8. Inheritance

**Understanding Inheritance**

Inheritance models an _is-a_ relationship:

- `Admin` **is a** `User`
- `Superman` **is an** `Admin`

JavaScript uses prototype chaining for inheritance:

```text
admin → Admin.prototype → User.prototype → Object.prototype
```

Method lookup climbs this chain until the method is found.

```js
class User {
  constructor(id, username) {
    this.i = id;
    this.u = username;
  }

  sayHello() {
    return `Hello ${this.u}`;
  }
}

class Admin extends User {
  constructor(id, username, permissions) {
    super(id, username);  // Call parent constructor
    this.p = permissions;
  }
}

class Superman extends Admin {
  constructor(id, username, permissions) {
    super(id, username, permissions);
  }
}

let adminOne = new Admin(110, "Mahmoud", 1);
console.log(adminOne.sayHello());  // "Hello Mahmoud" - inherited from User!

let superOne = new Superman(120, "Clark", 2);
console.log(superOne.sayHello());  // Also works - inheritance chain!
```

**Key Points:**

- `extends` creates the inheritance relationship
- `super()` calls the parent class constructor (must be called first in child constructor)
- Child classes inherit all methods and properties from parent classes

---

## 9. Encapsulation (Private Fields)

**What is Encapsulation?**

Encapsulation hides internal data and exposes only controlled interfaces.

**Private fields (`#field`) prevent:**

- Accidental modification
- External misuse
- Tight coupling

This makes systems safer and easier to refactor.

```js
class User {
  #e;  // Private field - cannot be accessed outside the class

  constructor(id, username, eSalary) {
    this.i = id;
    this.u = username;
    this.#e = eSalary;
  }

  getSalary() {
    return parseInt(this.#e);
  }
}

let userOne = new User(100, "Elzero", "5000 Gneh");
console.log(userOne.getSalary());  // 5000
// console.log(userOne.#e);        // ❌ SyntaxError: Private field '#e' must be declared in an enclosing class
```

**Real-World Example:** Think of an ATM. You can check your balance (public interface), but you can't directly access the bank's database (private data). The ATM encapsulates the complexity and only exposes safe operations.

---

## 10. Prototype

**Understanding Prototypes**

Every object has a hidden `Prototype` pointer that enables:

- Method lookup through the prototype chain
- Avoiding method duplication per instance
- Dynamic extension of behavior

```js
class User {
  constructor(id, username) {
    this.i = id;
    this.u = username;
  }

  sayHello() {
    return `Hello ${this.u}`;
  }
}

let userOne = new User(100, "Elzero");
console.log(User.prototype);  // Shows all methods available on User instances

// The prototype chain
console.log(userOne.__proto__ === User.prototype);              // true
console.log(User.prototype.__proto__ === Object.prototype);     // true
console.log(Object.prototype.__proto__);                        // null (end of chain)
```

**How Method Lookup Works:**

1. JavaScript looks for `sayHello` on `userOne` object itself
2. Not found? Look in `User.prototype`
3. Not found? Look in `Object.prototype`
4. Not found? Return `undefined`

---

## 11. Extending Prototypes

**Dynamic Behavior Extension**

You can add behavior even after objects are created.

⚠️ **Warning:** This is powerful but risky:

- Can cause naming conflicts
- Can break third-party code
- Should be avoided in shared environments

```js
class User {
  constructor(id, username) {
    this.i = id;
    this.u = username;
  }
}

let userOne = new User(100, "Elzero");

// Add a new method to ALL User instances (even existing ones!)
User.prototype.sayWelcome = function () {
  return `Welcome ${this.u}`;
};

console.log(userOne.sayWelcome());  // "Welcome Elzero" - works!

// You can even extend built-in types (but DON'T do this in production!)
String.prototype.addDotBeforeAndAfter = function () {
  return `.${this}.`;
};

let myString = "Elzero";
console.log(myString.addDotBeforeAndAfter());  // ".Elzero."
```

**When is this useful?**

- Polyfills (adding modern features to older browsers)
- Internal utilities in controlled environments
- Educational purposes

**When to avoid:**

- Production code with external dependencies
- Modifying built-in types like String, Array, Object
- Shared libraries or frameworks

---

## 12. Property Descriptors

**Fine-Grained Property Control**

Property descriptors define how properties behave:

|Attribute|Meaning|Default (when using =)|
|---|---|---|
|`writable`|Can value be changed?|`true`|
|`enumerable`|Appears in loops (for...in)?|`true`|
|`configurable`|Can be deleted/redefined?|`true`|
|`value`|The actual value|Your value|

This gives fine-grained control over object shape.

```js
const myObject = { a: 1, b: 2 };

Object.defineProperty(myObject, "c", {
  writable: false,      // Cannot change value
  enumerable: true,     // Will show in for...in loops
  configurable: false,  // Cannot delete or reconfigure
  value: 3,
});

console.log(myObject.c);  // 3
myObject.c = 100;         // Silently fails (or throws in strict mode)
console.log(myObject.c);  // Still 3

delete myObject.c;        // Fails
console.log(myObject.c);  // Still 3
```

**Use Cases:**

- Creating constants that can't be changed
- Hiding internal properties from loops
- Making immutable configuration objects

---

## 13. Multiple Properties and Inspection

**Batch Property Definition**

This is useful when:

- Building libraries
- Creating immutable objects
- Enforcing strict APIs

You can freeze, lock, or carefully expose data.

```js
const myObject = { a: 1, b: 2 };

// Define multiple properties at once
Object.defineProperties(myObject, {
  c: { configurable: true, value: 3 },
  d: { configurable: true, value: 4 },
  e: { configurable: true, value: 5 },
});

// Inspect all property descriptors
console.log(Object.getOwnPropertyDescriptors(myObject));
/* Output:
{
  a: { value: 1, writable: true, enumerable: true, configurable: true },
  b: { value: 2, writable: true, enumerable: true, configurable: true },
  c: { value: 3, writable: false, enumerable: false, configurable: true },
  d: { value: 4, writable: false, enumerable: false, configurable: true },
  e: { value: 5, writable: false, enumerable: false, configurable: true }
}
*/
```

**Additional Object Control Methods:**

```js
// Prevent adding new properties
Object.preventExtensions(myObject);

// Prevent adding/deleting properties
Object.seal(myObject);

// Prevent any changes (read-only)
Object.freeze(myObject);

// Check object state
console.log(Object.isExtensible(myObject));  // false
console.log(Object.isSealed(myObject));      // true/false
console.log(Object.isFrozen(myObject));      // true/false
```

---
