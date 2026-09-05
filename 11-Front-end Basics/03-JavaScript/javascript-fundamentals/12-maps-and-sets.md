## 15. Set Data Type

Object that lets you store **unique values** of any type (primitives or object references)

**Key Characteristics**
- No duplicate values
- No index-based access (`set[0]` → undefined)
- Iterable

**Creation**
```javascript
new Set()                    // empty set
new Set([1, 2, 3])           // from array
new Set("hello")             // from string → Set(4) {'h','e','l','o'}
```

**Core Methods & Properties**
```javascript
let mySet = new Set();

mySet.add(1).add(1).add(2).add("A");   // chaining
mySet.has("A")                         // true
mySet.delete(2)                        // true (removed)
mySet.size                             // number of elements
mySet.clear()                          // removes all elements
```

**Example**
```javascript
let myData = [1, 1, 1, 2, 3, "A"];
let unique = new Set(myData);

console.log(unique);          // Set(4) {1, 2, 3, "A"}
console.log(unique.size);     // 4
console.log(unique.has(2));   // true
```

### 15.1 Set vs WeakSet

| Feature                  | Set                              | WeakSet                          |
|--------------------------|----------------------------------|----------------------------------|
| Allowed values           | Any type                         | **Objects only**                 |
| Size property            | Yes (`size`)                     | **No**                           |
| Methods                  | `has`, `add`, `delete`, `clear`  | `has`, `add`, `delete`           |
| Iteration (`forEach`, keys, values, entries) | Yes                   | **No**                           |
| Garbage collection       | Strong references                | **Weak references** (objects can be GC'd) |
| Use case                 | General unique values            | Store objects temporarily, allow GC |

**WeakSet example** (useful for tracking objects without preventing GC)
```javascript
let obj = { name: "test" };
const ws = new WeakSet();
ws.add(obj);
obj = null; // can be garbage collected now
```

## 16. Map Data Type

Key-value pairs where **keys can be anything** (not just strings/symbols like in objects)

**Creation**
```javascript
new Map()
new Map([[1, "one"], ["name", "Ali"]])
```

**Core Methods & Properties**
```javascript
let map = new Map();

map.set("name", "Sara")           // add/update
map.set(10, "number")
   .set(true, "boolean")
   .set({x:1}, "object");

map.get(10)                       // "number"
map.has("name")                   // true
map.delete("name")
map.size                          // count
map.clear()                       // remove all
```

**Map vs Object Comparison**

| Feature                        | Object                              | Map                                   |
|--------------------------------|-------------------------------------|---------------------------------------|
| Key types                      | String or Symbol                    | **Any** (object, function, number...) |
| Default keys                   | Has prototype methods               | **Clean** (no default keys)           |
| Key order                      | Not guaranteed (modern: insertion)  | **Insertion order** guaranteed        |
| Size                           | Manual (`Object.keys().length`)     | Built-in `size` property              |
| Iteration                      | Needs `Object.keys/values/entries`  | **Directly iterable**                 |
| Performance (add/remove)       | Slower when many operations         | **Better** performance                |

### 16.1 Map vs WeakMap

| Feature                  | Map                              | WeakMap                          |
|--------------------------|----------------------------------|----------------------------------|
| Key types                | Any                              | **Objects only**                 |
| Garbage collection       | Strong refs                      | **Weak refs** (keys can be GC'd) |
| Size / clear / keys etc. | Yes                              | **No**                           |
| Use case                 | General key-value store          | Private data, DOM nodes tracking |

**Example – WeakMap allows GC**
```javascript
let user = { name: "Ali" };
const wm = new WeakMap();
wm.set(user, "secret data");

user = null; // key can now be garbage collected
```

## 17. Advanced Array Methods

### 17.1 Array.from()

Creates a new array from an **array-like** or **iterable** object

```javascript
// String → array
Array.from("hello")                // ["h","e","l","l","o"]

// With mapping
Array.from("123", n => +n + +n)    // [2, 4, 6]

// Remove duplicates from array
Array.from(new Set([1,1,2,3]))     // [1,2,3]

// From arguments object
function f() {
  return Array.from(arguments);
}
f(10,20,30)                        // [10,20,30]
```

### 17.2 Array.copyWithin(target, start?, end?)

Copies part of array **to another position** (in-place, mutates array)

```javascript
let arr = [10, 20, 30, 40, 50, "A", "B"];

// Copy from index -2 to -1 (last two → "A","B")
arr.copyWithin(1, -2, -1);
console.log(arr);  // [10, "A", 30, 40, 50, "A", "B"]
```

### 17.3 Array.some() — At least one element satisfies condition

```javascript
const nums = [1,2,3,4,5,10,20];

// Check if any > 10
nums.some(n => n > 10)             // true

// With thisArg
nums.some(function(n) { return n > this.max; }, {max: 15})  // true
```

### 17.4 Array.every() — All elements satisfy condition

```javascript
const values = [20, 30, 40, 50];
values.every(n => n > 15)          // true
```

## 18. Spread Operator (`...`)

Expands iterables into individual elements

**Common Uses**
```javascript
// String
console.log([..."hello"]);              // ["h","e","l","l","o"]

// Merge arrays
[1,2,3, ...[4,5,6]]                    // [1,2,3,4,5,6]

// Copy array (shallow)
const copy = [...original];

// Function arguments
Math.max(...[10, 50, 100])             // 100

// Merge objects (shallow)
{ ...obj1, ...obj2, extra: true }
```

**Quick Summary Table**

| Feature             | Set              | Map              | Spread (`...`)       |
|---------------------|------------------|------------------|----------------------|
| Purpose             | Unique values    | Key-value pairs  | Expand / copy / merge|
| Key types           | —                | Any              | —                    |
| Order               | Insertion        | Insertion        | —                    |
| GC friendly         | No (except WS)   | No (except WM)   | —                    |
