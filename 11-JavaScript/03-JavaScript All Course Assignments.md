---
Resources: "[JavaScript Bootcamp Extra Assignments - Elzero Web School](https://elzero.org/javascript-bootcamp-assignments-lesson-from-1-to-188/)"
---
# Extra Assignments

## Assignment no.1
```js
let fileName = "Elzero.php"
let data = fileName.split('.')
console.log(data[0])
console.log(data[1])
```

---

## Assignment no.2
```js
function addEl(str) {
    if(!str || str.startsWith('El'))
        return str
    else 
        return "El" + str
}
```

---

## Assignment no.3
```js
let myString = "Hello Elzero Web School @ We Love Programming@ @#!@#$%%^&*";
let firstPart = myString.slice(0, myString.indexOf('@'))
let rest = myString.slice(firstPart.length + 1)
let secondPart = rest.slice(0, rest.indexOf('@'))

console.log(firstPart + '@' + secondPart)
```

---

## Assignment no.4
```js
function checkRange(n1, n2, n3, n4, n5) {
    let min = n4, max = n5
    return (
        n1 >= min && n1 <= max &&
        n2 >= min && n2 <= max &&
        n3 >= min && n3 <= max
    ) ? "Yes All Numbers In Range" : "Not All Numbers Is In Range"
}
```
or
```js
function checkRange(n1, n2, n3, n4, n5) {
    return [n1, n2, n3].every(num => num >= n4 && num <= n5)
        ? "Yes All Numbers In Range"
        : "Not All Numbers Is In Range";
}
```
---

## Assignment no.5
```js
function replaceFirstWithLast(word) {
    return (
        word[word.length - 1]
        + word.slice(1, word.length - 1)
        + word[0]
    )
}
```

---

## Assignment no.6
```js
function checkBiggestNum(word) {
    return Math.max(...word.split("").map((e) => {return +e}))
}
```

---

## Assignment no.7
```js
console.log(nums.sort((a, b) => { return a < b }).slice(0, 2))
```

---

## Assignment no.8
```js
let nums = [10, 80, 85, 25, 30, 88, 15];
let goal = 100;

let closest = nums.reduce((prev, curr) => {
    return Math.abs(curr - goal) < Math.abs(prev - goal) ? curr : prev;
});

console.log(`Closest Number Is ${closest}`);
```

---

## Assignment no.9
```js
function swapEveryTwoChars(word) {
    let chars =  word.split("")
    for(let i = 0; i < chars.length; i += 2)
        chars[i] = (chars[i] === chars[i].toUpperCase()) ? chars[i].toLowerCase() : chars[i].toUpperCase()
    return chars.join("")
}
```

---

## Assignment no.10
```js
String.prototype.elzeroRepeat = function (times) {
    return this.repeat(times)
}
```

---

## Assignment no.11
```js
console.log(myMoney.toLocaleString())
```

---

## Assignment no.12
```js
result = names.filter((e) => {return e[0].toLowerCase() === e[e.length - 1].toLowerCase()})
```

---

## Assignment no.13
```js
console.log(`${theName[0] + theName[theName.length - 1]}\n${theName.slice(1, theName.length - 1)}\n${theName[theName.length / 2 - 1] + theName[theName.length / 2]}`)
```

---

## Assignment no.14
```js
function repeatWithRules(word) {
    let res = ""
    for (let i = 0; i < word.length; i++) {
        if (i === 0)
            res += word[i]
        else if (i === 1)
            res += word[i].repeat(2)
        else if (i === 2)
            res += word[i].repeat(3)
        else
            res += word[i].repeat(4)
    }
    return res
}
```

---

## Assignment no.15
```js
function concatenateWithoutLast(words) {
    return (words.map(element => {
        return element.slice(0, element.length - 1)
    }).join(" "))
}
```

---

## Assignment no.16
```js
function getCharacters(word, nums) {
    return (
        word.slice(0, nums) + word.slice(word.length - nums)
    )
}
```

---

## Assignment no.17
```js
function formatName(theName) {
    let letters = theName.split(" ").map(word => word[0].toLowerCase());
    letters[0] = letters[0].toUpperCase();
    return letters.join(".");
}
```

---

## Assignment no.18
```js
console.log(st[0].toUpperCase() + st.slice(1));

console.log(st.charAt(0).toUpperCase() + st.substring(1));

console.log(st.replace(st[0], st[0].toUpperCase()));

console.log(st.replace(/^./, st[0].toUpperCase()));

console.log(st.split("").map((c, i) => i === 0 ? c.toUpperCase() : c).join(""));

console.log(`${st.at(0).toUpperCase()}${st.slice(1)}`);

console.log(st.slice(0, 1).toUpperCase().concat(st.slice(1)));
```

---

## Assignment no.19
```js
let st = "Web SchoolElzero ";
console.log(
    st.slice(-7, -1)
    + st.slice(-1)
    + st.slice(-17, -13)
    + st.slice(-13, -7)
)
```

---

## Assignment no.20
```js
let st = "Elzero";
console.log(st[st.length - 1]);

console.log(st.charAt(st.length - 1))

console.log(st.substring(st.length - 1));

console.log(st.split("").map((c, i) => i === st.length - 1 ? c : "").join(""));

console.log("".concat(st.slice(st.length - 1)));
// كنكل
// كنكل
```

---

## Assignment no.21
```js
function getLastDigit(num) {
    return parseInt(`${num}`.split("")[`${num}`.length - 1])
}
```
or
```js
function getLastDigit(num) {
  return num % 10;
}
```
---

## Assignment no.22
```js
console.log(`${str1.slice(1)} ${str2.slice(1)}`);
```

---

## Assignment no.23
```js
function reversing(str) {
    return str.replace(/[A-Za-z]+/g, word =>
        word.split("").reverse().join("")
    );
}
```

---

## Assignment no.24
```js
function dashBetweenOdd(num) {
    let str = num.toString();
    let result = "";
    for (let i = 0; i < str.length; i++) {
        result += str[i];
        if (
            i < str.length - 1 &&
            str[i] % 2 !== 0 &&
            str[i + 1] % 2 !== 0
        ) {
            result += "-";
        }
    }
    return result;
}
```

---

## Assignment no.25
```js
myArr.length = 0;
console.log(myArr);

myArr.splice(0);
console.log(myArr);

while (myArr.length) {
    myArr.pop();
}
console.log(myArr);

while (myArr.length) {
    myArr.shift();
}
console.log(myArr)
```

---

## Assignment no.26
```js
let arr1 = [...new Set(myArr)];
console.log(arr1);

let arr2 = myArr.filter((item, index) => myArr.indexOf(item) === index);
console.log(arr2);

let arr3 = myArr.reduce((acc, curr) => {
    if (!acc.includes(curr)) {
        acc.push(curr);
    }
    return acc;
}, []);
console.log(arr3);

let arr4 = [];
for (let item of myArr) {
    if (!arr4.includes(item)) {
        arr4.push(item);
    }
}
console.log(arr4);
```

---

## Assignment no.27
```js
let result = myArr.map((char) => {return String.fromCharCode(char)}).join("")
```

---

## Assignment no.28
```js
function customMerge(...objects) {
    return objects
        .join()
        .split(",")
        .map(Number)
        .sort((a, b) => a - b);
}
```

---

## Assignment no.29
```js
function customCalc(...numbers) {
    let arr = numbers.map(_ => +_).filter(num => !Number.isNaN(num))
    return arr[0] * arr[arr.length - 1] * arr.reduce((curr, acc) => curr + acc)
}
```

---

## Assignment no.30
```js
for (let i = 1; i < 100; i += 5) {
    `${i}`.slice(-1) === "1"  ? console.log(i) : ""
}
```

---

## Assignment no.31
```js
let clonedArray = [...myArray];
clonedArray = myArray.slice();
console.log(clonedArray)

clonedArray = Array.from(myArray);
console.log(clonedArray)

clonedArray = [].concat(myArray);
console.log(clonedArray)

clonedArray = myArray.map(item => item);
console.log(clonedArray)

clonedArray = myArray.filter(() => true);
console.log(clonedArray)

clonedArray = Object.assign([], myArray);
console.log(clonedArray)

clonedArray = myArray.reduce((acc, curr) => {
    acc.push(curr);
    return acc;
}, []);
console.log(clonedArray)

clonedArray = [];
for (let item of myArray) {
    clonedArray.push(item);
}
console.log(clonedArray)
```

---

## Assignment no.32
```js
console.log(Number(strNumber));

console.log(+strNumber);

console.log(parseInt(strNumber));

console.log(parseFloat(strNumber));

console.log(Math.floor(strNumber));

console.log(Math.ceil(strNumber));

console.log(Math.round(strNumber));
```

---

## Assignment no.33
```js
console.log(
    "%cElzero Web School",
    `
        background: #0d6efd;
        color: white;
        font-size: 28px;
        font-family: monospace;
        font-weight: bold;
        padding: 100px 50px;
    `
);
```

---

## Assignment no.34
```js
let uniqueElements = [...new Set(arr)];
console.log(uniqueElements);

uniqueElements = arr.filter((item, index) => arr.indexOf(item) === index);
console.log(uniqueElements);

uniqueElements = arr.reduce((acc, curr) => {
    return acc.includes(curr) ? acc : [...acc, curr];
}, []);
console.log(uniqueElements);

uniqueElements = [];
for (const item of arr) {
    if (!uniqueElements.includes(item)) {
        uniqueElements.push(item);
    }
}
console.log(uniqueElements);
```

---

## Assignment no.35
```js
let chars = "ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789";

function generateSerial() {
    return Array.from({ length: 20 }, () =>
        chars[Math.floor(Math.random() * chars.length)]
    ).join("");
}
```

---

## Assignment no.36
```js
let smallLetters = [...Array(26).keys()]
  .map(i => String.fromCharCode(i + 97))
  .join("");

console.log(smallLetters);
```

```js
let smallLetters = Array.from(
  { length: 26 },
  (_, i) => String.fromCharCode(i + 97)
).join("");

console.log(smallLetters);
```

```js
let smallLetters = "";

for (let i = 97; i <= 122; i++) {
  smallLetters += String.fromCharCode(i);
}

console.log(smallLetters);
```

```js
let smallLetters = Array.from({ length: 26 })
  .reduce((acc, _, i) => acc + String.fromCharCode(i + 97), "");

console.log(smallLetters);
```
---

## Assignment no.37
```js
console.log(
    (numOne > numTwo)
        ? "1st > 2nd"
        : ((numOne < numTwo)
            ? "1st < 2nd"
            : "1st = 2nd"
        )
)
```

---

## Assignment no.38
```js
let ans = str
    .toLowerCase()
    .split(" ")
    .map(word => word[0].toUpperCase() + word.slice(1))
    .join(" ")
console.log(ans)
```

---

## Assignment no.39
```js
Object.freeze(myData)
```

---

## Assignment no.40
```js
Object.preventExtensions(myData)
```

---

## Assignment no.41
```js
let cloned = new Object(myData)
let cloned = Object.assign(myData)
let cloned = Object.create(myData)
let cloned = myData
```

---

## Assignment no.42
```js
let printed = false

document.addEventListener("keydown", (e) => {
    if(e.ctrlKey && e.altKey && e.shiftKey && !printed)
    {
        console.log("You Presses Ctrl + Alt + Shift")
        printed = true
    }
})
```

---

## Assignment no.43
```js
fetch("https://api.github.com/users/ElzeroWebSchool/repos")
    .then(res => res.json())
    .then(data => {
        let table = document.querySelector("tbody");

        data.slice(0, 15).forEach(repo => {
            let row = document.createElement("tr");

            let name = document.createElement("td");
            name.textContent = repo.name;

            let stars = document.createElement("td");
            stars.textContent = repo.stargazers_count;

            let link = document.createElement("td");
            let a = document.createElement("a");
            a.href = repo.html_url;
            a.target = "_blank";
            a.textContent = "Visit";
            link.appendChild(a);

            row.append(name, stars, link);
            table.appendChild(row);
        });
    });
```

---

## Assignment no.44
```js
let last = 30, odd = true, res = 0
for (let i = last; i >= 0; i -= 1) {
    if(i % 2 && odd) {
        console.log(i)
        odd = false
        res += i
    }
    else if (i % 2 && !odd)
        odd = true
}
console.log(res)
```

---

## Assignment no.45
```js
let myRange = Array.from({length: rangeEnd}, (_, i) => i + 1)
console.log(myRange)

myRange = [...Array(rangeEnd).keys()].map(num => num + 1)
console.log(myRange)

myRange = new Array(rangeEnd)
    .fill(0)
    .map((_, i) => {return i + 1})
console.log(myRange)
```

---

## Assignment no.46
```js
let maxNumber = nums[0];

for (let i = 1; i < nums.length; i++) {
    if (nums[i] > maxNumber) {
        maxNumber = nums[i];
    }
}

console.log(maxNumber);
console.log(Math.max(...nums))
console.log(nums.reduce((max, curr) => {
    return curr > max ? curr : max
}))
console.log(nums.sort((a, b) => b - a)[0])
```

---

## Assignment no.47
```js
let textarea = document.querySelector("textarea");
let button = document.querySelector("button");

button.addEventListener("click", () => {
    let blob = new Blob([textarea.value], { type: "text/plain" });

    let link = document.createElement("a");
    link.href = URL.createObjectURL(blob);
    link.download = "text.txt";

    link.click();

    URL.revokeObjectURL(link.href);
});
```

---

## Assignment no.48
```js
function createStars(num) {
    let result = "";

    for (let i = 1; i <= num; i++) {
        result += "*".repeat(i * 2 - 1);
        if (i !== num) result += "\n";
    }
    return result;
}
```

---

## Assignment no.49
```js
function createStars(num) {
    let result = "";
    
    for (let i = 1; i < num; i++) {
        result += "*".repeat(i * 2 - 1);
        if (i !== num) result += "\n";
    }
    
    for (let i = num; i >= 1; i--) {
        result += "*".repeat(i * 2 - 1) + "\n";
    }
    return result;
}
```

---

## Assignment no.50
```js
function createStars(num) {
    let result = "";

    for (let i = num; i >= 1; i--) {
        result += " ".repeat(num - i) + "*".repeat(i * 2 - 1) + "\n";
    }
    for (let i = 1; i <= num; i++) {
        result += " ".repeat(num - i) + "*".repeat(i * 2 - 1);
        if (i !== num) result += "\n";
    }
    return result;
}
```