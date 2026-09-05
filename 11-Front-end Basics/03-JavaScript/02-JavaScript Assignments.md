---
Resources: "[JavaScript Bootcamp Assignments - Elzero Web School](https://elzero.org/category/assignments/javascript-bootcamp-assignments/)"
Assignements:
- "[Introduction](https://elzero.org/javascript-bootcamp-assignments-lesson-from-001-to-009/)"
- "[Data Types And Variables](https://elzero.org/javascript-bootcamp-assignments-lesson-from-010-to-017/)"
- "[Operators](https://elzero.org/javascript-bootcamp-assignments-lesson-from-018-to-022/)"
- "[Numbers](https://elzero.org/javascript-bootcamp-assignments-lesson-from-023-to-026/)"
- "[Strings And Methods](https://elzero.org/javascript-bootcamp-assignments-lesson-from-027-to-030/)"
- "[Comparison & Logical Operators](https://elzero.org/javascript-bootcamp-assignments-lesson-from-031-to-032/)"
- "[If Condition](https://elzero.org/javascript-bootcamp-assignments-lesson-from-033-to-037/)"
- "[Switch Statement](https://elzero.org/javascript-bootcamp-assignments-lesson-from-038-to-039/)"
- "[Arrays And Methods](https://elzero.org/javascript-bootcamp-assignments-lesson-from-040-to-047/)"
- "[Loop - For](https://elzero.org/javascript-bootcamp-assignments-lesson-from-048-to-053/)"
- "[Loop - While](https://elzero.org/javascript-bootcamp-assignments-lesson-from-054-to-056/)"
- "[Function And Parameters](https://elzero.org/javascript-bootcamp-assignments-lesson-from-057-to-063/)"
- "[Function And Scopes](https://elzero.org/javascript-bootcamp-assignments-lesson-from-064-to-070/)"
- "[Higher Order Functions](https://elzero.org/javascript-bootcamp-assignments-lesson-from-071-to-078/)"
- "[Objects And Methods](https://elzero.org/javascript-bootcamp-assignments-lesson-from-079-to-085/)"
- "[Document Object Model](https://elzero.org/javascript-bootcamp-assignments-lesson-from-086-to-093)"
- "[Browser Object Model](https://elzero.org/javascript-bootcamp-assignments-lesson-from-102-to-110/)"
- "[Destructuring](https://elzero.org/javascript-bootcamp-assignments-lesson-from-115-to-122/)"
- "[Map And Set](https://elzero.org/javascript-bootcamp-assignments-lesson-from-123-to-133/)"
- "[Regular Expression](https://elzero.org/javascript-bootcamp-assignments-lesson-from-134-to-146/)"
- "[Object Oriented Programming](https://elzero.org/javascript-bootcamp-assignments-lesson-from-147-to-158/)"
- "[Date, Generators, Modules](https://elzero.org/javascript-bootcamp-assignments-lesson-from-159-to-168/)"
- "[AJAX and JSON](https://elzero.org/javascript-bootcamp-assignments-lesson-from-169-to-178/)"
- "[Promises](https://elzero.org/javascript-bootcamp-assignments-lesson-from-179-to-188/)"
---
# Introduction
## Assignment 1
```javascript
// code one won't work because it will search for the element before its creation
```
## Assignment 2
```js
document.body.innerHTML += `<h1 style="color: blue;font-size: 80px;font-weight: bold;text-align: center;font-family: Arial">Elzero</h1>`;
```
## Assignment 3
```js
console.log("%cElzero %cWeb %cSchool","color:red; font-size:40px;","color:green; font-size:40px; font-wight;bold;","color:white; font-size:40px; background-color:blue;")
```
## Assignment 4
```js
console.group("Group 1");
console.log("Message One");
console.log("Message Two");
console.group("Child Group");
console.log("Message One");
console.log("Message Two");
console.group("Grand Child Group");
console.log("Message One");
console.log("Message Two");
console.groupEnd();
console.groupEnd();
console.groupEnd();
console.group("Group 2");
console.log("Message One");
console.log("Message Two");
console.groupEnd();
```
## Assignment 5
```js
console.table(["Elzero", "Ahmed", "Sameh", "Gamal", "Aya"])
```
## Assignment 6
```js
// 1
/*
console.log("Iam In Console");
document.write("Iam In Page");
*/

// 2-redefine the functions
console.log = function() {}; 
document.write = function() {};
```
# Data Types And Variables
## Assignment 1
```js
var numberOne = 10, numberTwo = 20;

console.log(`${numberOne}${numberTwo}`);
console.log(typeof (`${numberOne}${numberTwo}`))
console.log(`${numberTwo}\n${numberOne}`)
```
## Assignment 2
```js
<div id="elzero">object</div>
```
## Assignment 3
```js
console.log("\`I\'m In\n\\\\\nLove \\\\ \"\"\" \'\'\'\n\+\+ With \+\+\n \\\"\"\"\\\"\"\"\n\"\"JavaScript\"\"\`\`")
```
## Assignment 4
```js
let a = 21;
let b = 20;

console.log("_" + a + "_" + b + a + "_" + b + a + "_" + a + b + "_" + b + "_");
```
# Operators
## Assignment 1
```js
console.log(10 * 20 + 15 % 3 + 190 + 10 - 400);
```
## Assignment 2
```js
let num = 3;

// Solution One
console.log(num + num); // 6

// Solution Two
console.log(num + (num * true)); // 6

// Solution Three
console.log(++num + true + true); // 6

// Solution Four
console.log(--num * (true + true)); // 6

// Solution Five
console.log(num ** (true + true) - num); // 6

// Solution Six
console.log(num * (num - true)); // 6
```
## Assignment 3
```js
let num = "10";

// Solution One
console.log(+num + +num); // 20

// Solution Two
console.log(+num * (true + true)); // 20
```
## Assignment 4
```js
let points = 10;

// Write Your Code Here
console.log(points + (true + true + true)); // 13

// Write Your Code Here
console.log(points - (true + true)); // 8;
```
# Numbers
## Assignment  1
```js

```
## Assignment  2
```js
console.log(Number.MIN_SAFE_INTEGER + (-2 * Number.MIN_SAFE_INTEGER)); // 9007199254740991
```
## Assignment  3
```js
console.log(Number.MAX_SAFE_INTEGER.toString().length); // 16
```
## Assignment  4
```js
console.log(parseInt(myVar)); // 100
console.log(parseFloat(myVar).toFixed(2)); // 100.57
```
## Assignment  5
```js  
console.log(Number.isInteger(num) + Number.isInteger(num)); // 2
```
## Assignment  6
```js
console.log(Math.trunc(flt)); // 10
console.log(Math.floor(flt)); // 10
console.log(parseInt(flt)); // 10
console.log(flt | 0); // 10
// `| 0`Bitwise OR يحذف الكسر
console.log(~~flt); // 10
// `~~`Double Bitwise NOT يحذف الكسر
```
## Assignment  7
```js
console.log(Math.floor(Math.random() * 5));
```
# Strings And Methods
## Assignment  1
```js

```
## Assignment  2
```js
console.log(word.includes(letterZ)); // True
console.log(word.startsWith(letterE.toUpperCase())); // True
console.log(word.endsWith(letterO.toLowerCase())); // True
```
# Comparison & Logical Operators
## Assignment 1
```js
console.log(100 == "100"); // true
console.log(100 != 1000); // true
console.log(110 > 100 > 10 < 20); // true
console.log(-10 == "-10"); // true
console.log(-50 != +"-40"); // true
console.log(10 != -"-40"); // true
console.log("10" == 10); // true
console.log(! 20 == false); // true
```
## Assignment 2
```js

```
## Assignment 3
```js
let a = 20;
let b = 30;
let c = 10;

console.log(a < b && a > c || a == b); // true
console.log(a < b && a > c); // true
console.log((a < b) && !(a >= b) && (a > c) && (a != c)); // true
```
# If Condition
## Assignment 1
```js
if (num < 10) {
	console.log("00" + num);
} else if (num > 10 && num < 100) {
	console.log("0" + num);
} else {
	console.log(num);
}
```
## Assignment 2
```js
let num1 = 9;
let str = "9";
let str2 = "20";

if (num1 == str) {
	console.log(`${num1} Is The Same Value As ${str}`);
}
if (num1 == str && num1 !== str) {
	console.log(`${num1} Is The Same Value As ${str} But Not The Same Type`);
}
if (num1 !== str2 && typeof num1 !== typeof str2) {
	console.log(`${num1} Is Not The Same Value Or The Same Type As ${str2}`);
}
if (typeof str === typeof str2 && str != str2) {
	console.log(`${str} Is The Same Type As ${str2} But Not The Same Value`);
}
```
## Assignment 3
```js
let num1 = 10;
let num2 = 30;
let num3 = "30";

if (num3 > num1 && typeof num3 !== typeof num2) {
	console.log(`${num3} Is Larger Than ${num1} And Type ${typeof num3} Not The Same Type As ${typeof num2}`);

	if (num3 == num2) {
		console.log(`${num3} Is Larger Than ${num1} And Value Is The Same As ${num2} And Type ${typeof num3} Not The Same Type As ${typeof num2}`);
	}

	if (num3 !== num1 && typeof num3 !== typeof num2) {
		console.log(`${num3} Value And Type Is Not The Same As ${num1} And Type Is Not The Same As ${num2}`);
	}
}
```
## Assignment 4
```js
let num1 = 5;
let num2 = 3;
let num3 = "5";
let num4 = 20;
```
# Switch Statement
## Assignment 1
```js
let day = " friday ";

day = day.trim();
day = day[0].toUpperCase() + day.slice(1).toLowerCase();

switch (day) {
case "Friday":
case "Saturday":
case "Sunday":
	console.log("No Appointments Available");
break;
case "Monday":
case "Thursday":
	console.log("From 10:00 AM To 5:00 PM");
break;
case "Tuesday":
	console.log("From 10:00 AM To 6:00 PM");
break;
case "Wednesday":
	console.log("From 10:00 AM To 7:00 PM");
break;
default:
	console.log("Its Not A Valid Day");
}
```
# Arrays And Methods
## Assignment 1
```JS
let myFriends = ["Ahmed", "Elham", "Osama", "Gamal"];
let num = 3;

// Method 1
console.log(myFriends.slice(0, num)); // ["Ahmed", "Elham", "Osama"];

// Method 2
console.log(myFriends.splice(0, num)); // ["Ahmed", "Elham", "Osama"];
```
## Assignment 2
```JS
friends.shift();
friends.pop();
```
## Assignment 3
```JS
finalArr = arrOne.concat(arrTwo).sort().reverse();
```
## Assignment 4
```JS
console.log(words[website.length][0].slice(website.length).toUpperCase());
```
## Assignment 5
```JS
console.log(haystack.indexOf(needle) ? "Found" : "");

console.log((haystack.some(item => item === needle) ? "Found" : ""));

console.log(haystack.includes(needle) ? "Found" : "");
```
## Assignment 6
```JS
allArrs = arr1.concat(arr2).sort().splice(arr2.length, arr1.length).join("").toLowerCase();
```
# Loop - For
## Assignment 1
```JS
for (let i = start; i <= end; i += 10) {
    if (i === exclude) {
        continue;
    }
    console.log(i);
}
```
## Assignment 2
```JS
for (let i = start; i >= end; i--) {
    console.log(i);
    if (i === stop) {
        break;
    }
}
```

## Assignment 3
```JS
for (let i = start; i <= end; i++) {
    console.log(i);
    for (let j = start - start; ;) {
        j += breaker;
        console.log(`-- ${j}`);
        if (j === (breaker * breaker)) {
            break;
        }
    }
}
```
## Assignment 4
```JS
for (;;) {
  // Write Your Code Here
  console.log(index);
  index -= jump;
  if (index < 4) {
    break;
  }
}
```
## Assignment 5
```JS
for (let i = letter.length - letter.length, count = letter.length; i < friends.length; i++) {
    if (!friends[i].startsWith(letter.toUpperCase())) {
        console.log(`${count++} => ${friends[i]}`);
    }
}
```
## Assignment 6 
```JS
for (let i = start; i < swappedName.length; i++) {
  if (swappedName[i] === swappedName[i].toUpperCase()) {
    swappedName =
      swappedName.slice(0, i) +
      swappedName[i].toLowerCase() +
      swappedName.slice(i + 1);
  } else {
    swappedName =
      swappedName.slice(0, i) +
      swappedName[i].toUpperCase() +
      swappedName.slice(i + 1);
  }
}
console.log(swappedName);
```
## Assignment 7
```JS
for (let i = start; i < mix.length; i++) {
  if (typeof mix[i] === "number" && i !== 0)
    console.log(mix[i]);
}
```
# Loop - While
## Assignment 1
```JS
while (index < friends.length) {
  if (typeof friends[index] !== "number" && !friends[index].startsWith("A")) {
    
    counter++;
    console.log(`${counter} => ${friends[index]}`);
  }
  index++;
}
```
# Function And Parameters
## Assignment 1
```JS
function sayHello(theName, theGender) {
    const prefix = theGender
        ? (theGender[0].toLowerCase() === 'm' ? "Mr " : theGender[0].toLowerCase() === 'f' ? "Miss " : "")
        : "";

        console.log(`Hello ${prefix}${theName}`);
}
```
## Assignment 2
```JS
function calculate(firstNum, secondNum, operation = 'add') {
    if (firstNum === undefined) {
        console.log("First Number Not found");
        return;
    }
    if (secondNum === undefined) {
        console.log("Second Number Not found");
        return;
    }

    var result;
    var opChar = operation[0].toLowerCase();

    if (opChar === 'a') {
        result = firstNum + secondNum;
    } else if (opChar === 's') {
        result = firstNum - secondNum;
    } else if (opChar === 'm') {
        result = firstNum * secondNum;
    } else {
        return ("Not available operation");
    }

    return result;
}
```
## Assignment 3
```JS
function ageInTime(theAge) {
    if (theAge < 10 || theAge > 100) {
        console.log("Age out of range")
        return
    }
    const currentDate = new Date();
    const startDate = new Date;
    startDate.setFullYear(currentDate.getFullYear() - theAge)

    // different in milly seconds
    var diffInMs = currentDate - startDate,
        totalSec = Math.floor(diffInMs / 1000),
        totalMin = Math.floor(totalSec / 60),
        totalHours = Math.floor(totalMin / 60),
        totalDays = Math.floor(totalHours / 24),
        totalWeeks = Math.floor(totalDays / 7),
        totalMonths = theAge * 12;
}
```
## Assignment 4
```JS
function checkStatus(a, b, c) {
    let name, age, status, args = [a, b, c];

    for (let i = 0; i < args.length; i++) {
        if (typeof args[i] === "string") {
            name = args[i];
        } else if (typeof args[i] === "number") {
            age = args[i];
        } else if (typeof args[i] === "boolean") {
            status = args[i];
        }
    }
    
    let statusMessage = status ? "You Are Available For Hire" : "You Are Not Available For Hire";
    console.log(`Hello ${name}, Your Age Is ${age}, ${statusMessage}`);
}
```
## Assignment 5
```JS
function createSelectBox(startYear, endYear) {
    document.write(`<select>`);
    for (let i = startYear; i <= endYear; i++) {
        document.write(`  <option value="${i}">${i}</option>`);
    }
    document.write(`</select>`);
}
```
## Assignment 6
```JS
function multiply(...args) {
    let result = 1;
    for (let i = 0; i < args.length; i++) {
        let ele = args[i]
        if (typeof ele === "number") {
            ele = parseInt(ele)
            result *= ele;
        }
    }
    console.log(result);
}
```
# Function And Scopes
## Assignment 
```JS
function getDetails(zName, zAge, zCountry) {
    function namePattern(zName) {
        let idx = zName.indexOf(" ")
        let fName = zName.slice(0, idx)
        let sName = zName.slice(idx + 1, idx + 2).toUpperCase()
        // console.log(`${fName} ${sName}`)
        return `Hello ${fName} ${sName}.`
    }

    function ageWithMessage(zAge) {
        let ageString = ""
        for (let ch of zAge) {
            if (ch >= '0' && ch <= '9')
                ageString += ch
        }
        let age = Number(ageString)
        // console.log(age)
        return `Your Age Is ${age}`
    }
    function countryTwoLetters(zCountry) {
        zCountry = zCountry.toUpperCase()
        // console.log(zCountry.slice(0, 2))
        return `You Live in ${zCountry.slice(0, 2)}`
    }
    function fullDetails() {
        return `${namePattern(zName)}, ${ageWithMessage(zAge)}, ${countryTwoLetters(zCountry)}`
    }
    return fullDetails(); // Do Not Edit This
}
```
## Assignment 
```JS
const itsMe = () => `Iam A Normal Function`;

const urlCreate = (protocol, web, tld) => `${protocol}://www.${web}.${tld}`;
```
## Assignment 
```JS
const checker = zName => status => salary => status === "Available" ? `${zName}, My Salary Is ${salary}` : `Iam Not Avaialble`;
```
## Assignment 
```JS
function specialMix(...data) {
    let numOfStrings = 0, ans = 0;
    dataLoop:
    for (let ele of data) {
        if (typeof ele === "string") {
            let hasNum = false, numStr = "";
            for (let c of ele) {
                if (c >= '0' && c <= "9") {
                    hasNum = true
                    numStr += c
                }
            }
            if (hasNum) {
                ans += parseInt(numStr)
                continue dataLoop
            }
            numOfStrings += 1
        }
        else {
            ans += ele
        }
    }
    if (numOfStrings === data.length) {
        return `All Is Strings`
    }
    return ans
}
```
# Higher Order Functions
## Assignment 1
```JS
let fMix = mix.map((ele) => (isNaN(parseInt(ele)) ? ele : "")).reduce((ele, acc) => (ele + acc))
```
## Assignment 2
```JS
let seen = []
let ans = myString
    .split("")
    .filter((ele) => {
        if(seen.includes(ele)) 
            return false
        seen.push(ele)
        return true
    })
    .join("")
```
## Assignment 3
```JS
let array = myArray
    .reduce((ele, acc) => (ele + acc))
    .split("")
    .filter((ele) => (ele !== ","))
    .join("")
```
## Assignment 4
```JS
let ans = numsAndStrings
    .filter((ele) => (!isNaN(parseInt(ele))))
    .map((ele) => (-ele))
```
## Assignment 5
```JS
let ans = nums.reduce(function (acc, ele) {
    if (ele % 2)
        return ele + acc
    else
        return ele * acc
}, 1)
```
# Objects And Methods
## Assignment 1
```JS
let member = {
    name: "Elzero",
    age: 38,
    country: "Epypt",
    fullDetails: function() {
        return `My Name Is ${this.name}, My Age Is ${this.age}, I Live in ${this.country}`
    }
}
```
## Assignment 2
```JS
let objMethodOne = {
	property: "Method One"
}
let objMethodTwo = new Object({ property: "Method Two" })
let objMethodThree = Object.create({ property: "Method Three" })
let objMethodFour = Object.assign({}, { property: "Method Four" })
```
## Assignment 3
```JS
let finalObject = Object.assign({}, {a}, threeNums, twoNums)
```
## Assignment 4
```JS
let objectLength = Object.keys(myFavGames).length;
for (let i = 0; i < objectLength; i++) {
    let currGame = Object.keys(myFavGames)[i];
    console.log(`The Game Name Is ${currGame}`);
    console.log(`The Publisher Is ${myFavGames[currGame].publisher}`);
    console.log(`The Price Is ${myFavGames[currGame].price}`);

    if (myFavGames[currGame].bestThree) {
        console.log("- Game Has Releases");
        console.log(`First => ${myFavGames[currGame].bestThree.one}`);
        console.log(`Second => ${myFavGames[currGame].bestThree.two}`);
        console.log(`Third => ${myFavGames[currGame].bestThree.three}`);
    }
    console.log("#".repeat(20));
}

```
# Document Object Model
## Assignment no.1
```JS
let one = document.getElementById('elzero')
let two = document.getElementsByClassName('element')[0]
let three = document.getElementsByName('js')[0]
let four = document.getElementsByTagName("div")[0]

let five = document.querySelector(".element")
let six = document.querySelector("#elzero")
let seven = document.querySelector("[name='js']");
let eight = document.querySelector("div");

let nine = document.querySelectorAll(".element")[0]
let ten = document.querySelectorAll("#elzero")[0]
let eleven = document.querySelectorAll("div")[0]
let twelve = document.querySelectorAll("[name='js']")[0]

let thirteen = document.body.firstElementChild
let fourteen = document.body.children[0]
let fifteen = document.body.firstChild.nextSibling
```
## Assignment no.2
```JS
let images = document.getElementsByTagName("img")

for(let i = 0; i < images.length; i++) {
    let ele = images[i]
    ele.src = "https://elzero.org/wp-content/themes/elzero/imgs/logo.png"
    ele.alt = "Elzero Logo"
    ele.decoding = "async";
    console.log(ele)
}
```
## Assignment no.3
```JS
let res = document.querySelector(".result")
let input = document.querySelector("input")
let rate = 15.6

input.addEventListener("input", () => {
    let dollar = input.value || 0
    let pound = (dollar * rate).toFixed(2)
    res.innerHTML = `${dollar} USD Dollar = ${pound} Egyptian Pound`;
})
```
## Assignment no.4
```JS
let one = document.querySelectorAll("div")[0]
let two = document.querySelectorAll("div")[1]

let oneContent = one.textContent
let twoContent = two.textContent
let oneTitle = one.title
let twoTitle = two.title

one.textContent = twoContent
two.textContent = oneContent + " 2"
one.title = twoTitle
two.title = oneTitle
```
## Assignment no.5
```JS
let images = document.getElementsByTagName("img");

for (let i = 0; i < images.length; i++) {
    let ele = images[i];

    if (ele.hasAttribute("alt")) {
        ele.setAttribute("alt", "Old");
    } else {
        ele.setAttribute("alt", "Elzero New");
    }
}
```
## Assignment no.6
```JS
document.body.style.cssText = `
    font-family: Arial, Helvetica, sans-serif;
    background: #f5f5f5;
    display: flex;
    justify-content: center;
    padding: 40px;
`;

const form = document.querySelector("form");
form.style.cssText = `
    width: 450px;
    background: #fff;
    padding: 25px;
    border-radius: 10px;
    box-shadow: 0 10px 25px rgba(0,0,0,.1);
`;

document.querySelectorAll(".input").forEach(input => {
    input.style.cssText = `
        width: 100%;
        hight: 45px;
        padding: 15px 12px;
        margin-bottom: 15px;
        border: 1px solid #ccc;
        border-radius: 6px;
        font-size: 16px;
        outline: none;
        box-sizing: border-box;
    `;
});

const submit = document.querySelector('input[type="submit"]');
submit.style.cssText = `
    width: 100%;
    padding: 12px;
    margin-bottom: 20px;
    border: none;
    border-radius: 6px;
    background: #2196f3;
    color: #fff;
    font-size: 16px;
    cursor: pointer;
`;

const results = document.querySelector(".results");
results.style.cssText = `
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(100px, 1fr));
    gap: 15px;
`;

let inputs = document.querySelectorAll(".input")

submit.addEventListener("click", (e) => {
    e.preventDefault()
    results.innerHTML = ""
    let num = +inputs[0].value, text = inputs[1].value, type = inputs[2].value
    for (let i = 0; i < num; i++) {
        let ele = document.createElement(type.toLowerCase());
        ele.title = "Element"
        ele.id = `id-${i + 1}`
        ele.class = "box"
        ele.textContent = text
        results.appendChild(ele)
    }
})
```
## Assignment no.7 
```html
<script>
        document.addEventListener("DOMContentLoaded", () => {
            const link = [...document.querySelectorAll("a")].find(
                (ele) =>
                    ele.classList.contains("open") &&
                    ele.textContent.trim() === "Elzero"
            );
            console.log(link)
            if (link)
                link.click()
        })
</script>
```
## Assignment no.8
```JS
const current = document.querySelector("[title='Current']");
const addInput = document.querySelector(".classes-to-add");
const removeInput = document.querySelector(".classes-to-remove");
const result = document.querySelector(".classes-list div")

function showClasses() {
    result.innerHTML = ""

    if (current.classList.length === 0) {
        result.textContent  = "No Classes to Show"
        return
    }

    [...current.classList].forEach(cls => {
        const span = document.createElement("span")
        span.textContent = cls
        result.appendChild(span)
    })
}

function handleClasses(input, action) {
    let value = input.value.trim().toLowerCase();

    if (value !== "") {
        let classes = value.split(/\s+/);

        current.classList[action](...classes);
    }

    input.value = "";
    showClasses();
}

addInput.addEventListener("blur", () => handleClasses(addInput, "add"));
removeInput.addEventListener("blur", () => handleClasses(removeInput, "remove"));

showClasses()
```
## Assignment no.9
```JS
const p = document.querySelector("p")
const d = document.querySelector("div")
p.remove()

const start = document.createElement("div")
start.title = "Start Element"
start.textContent = "Start"

const end = document.createElement("div")
end.title = "End Element"
end.textContent = "End"

d.before(start)
d.after(end)
```
## Assignment no.10 
```JS
let d = document.querySelector("div")
let text = d.textContent.split("\n")
let needed_word = ""

text.forEach(ele => {
    if(ele.trim() === "Elzero") {
        needed_word = ele.trim()
    }
})
```
## Assignment no.11 
```JS
document.body.querySelectorAll("*").forEach((element) => {
    element.addEventListener("click", () => {
        console.log(`This Is ${element.tagName}`);
    });
});
```
# Browser Object Model
## Assignment no.1
```JS
let [num1, num2] = prompt("Print number from - to", "Example: 5-20")
    .split("-")
    .map(Number);

let start = Math.min(num1, num2);
let end = Math.max(num1, num2);

for (let i = start; i <= end; i++) {
    console.log(i);
}
```
## Assignment no.2
```JS
function createPopUp() {
    let overlay = document.createElement("div");
    let popup = document.createElement("div");
    let title = document.createElement("h2");
    let text = document.createElement("p");
    let close = document.createElement("span");

    title.textContent = "Welcome";
    text.textContent = "Welcome To Elzero Web School";
    close.textContent = "X";

    popup.append(title, text, close);
    overlay.appendChild(popup);
    document.body.appendChild(overlay);

    document.body.style.cssText = `
        width: 100vw;
        height: 100vh;
        display: flex;
        align-items: center;
        justify-content: center;
    `;
    Object.assign(overlay.style, {
        position: "fixed",
        backgroundColor: "rgba(0,0,0,0.2)",
        display: "flex",
        justifyContent: "center",
        alignItems: "center"
    });
    Object.assign(popup.style, {
        position: "relative",
        width: "400px",
        transform: "translate(-50 %, -50 %)",
        padding: "30px",
        backgroundColor: "#fff",
        border: "1px solid #ccc",
        textAlign: "center"
    });
    Object.assign(close.style, {
        position: "absolute",
        top: "-15px",
        right: "-15px",
        width: "30px",
        height: "30px",
        borderRadius: "50%",
        backgroundColor: "red",
        color: "#fff",
        display: "flex",
        justifyContent: "center",
        alignItems: "center",
        cursor: "pointer",
        fontWeight: "bold"
    });

    close.onclick = () => overlay.remove();
}

setTimeout(createPopUp, 5000);
```
## Assignment no.3
```JS
let div = document.createElement("div")
div.innerText = "10"
document.body.append(div)

let func = setInterval(() => {
    let counter = +div.innerText
    div.innerText = `${counter - 1}`
    counter -= 1
    if (counter === 0) {
        clearInterval(func)
    }
}, 1000);

```
## Assignment no.4
```JS
let div = document.createElement("div")
div.innerText = "10"
document.body.append(div)

let func = setInterval(() => {
    let counter = +div.innerText
    div.innerText = `${counter - 1}`
    counter -= 1
    if (counter === 0) {
        clearInterval(func)
        window.location.href = "https://elzero.org"
    }
}, 1000);
```
## Assignment no.5
```JS
let div = document.createElement("div")
div.innerText = "10"
document.body.append(div)

let func = setInterval(() => {
    let counter = +div.innerText
    div.innerText = `${counter - 1}`
    counter -= 1
    if (counter === 5) {
        window.open("https://elzero.org", "_blank", "width=400,height=300,left=200,top=100");
    }
    if (counter === 0) {
        clearInterval(func)
    }
}, 100);

```
## Assignment no.6 
```html
<!DOCTYPE html>
<html lang="en">

<head>
	<meta charset="UTF-8" />
	<meta http-equiv="X-UA-Compatible" content="IE=edge" />
	<meta name="viewport" content="width=device-width, initial-scale=1.0" />
	<title>Learn JavaScript</title>
</head>

<body>
	<select id="fonts">
		<option value="Open Sans">Open</option>
		<option value="Cairo">Cairo</option>
		<option value="Roboto">Roboto</option>
	</select>

	<select id="colors">
		<option value="black">Black</option>
		<option value="red">Red</option>
		<option value="green">Green</option>
		<option value="blue">Blue</option>
		<option value="orange">Orange</option>
		<option value="purple">Purple</option>
	</select>

	<select id="sizes"></select>

	<div style="width: 100vw; height: 100vh; display: flex; align-items:center; justify-content:center; font-family: Open Sans sans-serif; color: black; font-size: 16px;">test</div>
	<script src="./script/main.js"></script>
</body>

</html>
```

```JS
let div = document.querySelector("div")

let fontSelect = document.getElementById("fonts")
let colorSelect = document.getElementById("colors")
let sizeSelect = document.getElementById("sizes")

for (let i = 16; i <= 30; i++) {
    let option = document.createElement("option")
    option.value = `${i}px`
    option.textContent = i
    sizeSelect.appendChild(option)
}

fontSelect.value = localStorage.getItem("font") || "Open Sans"
colorSelect.value = localStorage.getItem("color") || "black"
sizeSelect.value = localStorage.getItem("size") || "16px"

div.style.fontFamily = fontSelect.value
div.style.color = colorSelect.value
div.style.fontSize = sizeSelect.value

fontSelect.addEventListener("change", () => {
    div.style.fontFamily = fontSelect.value
    localStorage.setItem("font", fontSelect.value)
})
colorSelect.addEventListener("change", () => {
    div.style.color = colorSelect.value
    localStorage.setItem("color", colorSelect.value)

})
sizeSelect.addEventListener("change", () => {
    div.style.fontSize = sizeSelect.value
    localStorage.setItem("size", sizeSelect.value)
})
```
## Assignment no.7 
```html
<!DOCTYPE html>
<html lang="en">

<head>
<meta charset="UTF-8" />
<meta http-equiv="X-UA-Compatible" content="IE=edge" />
<meta name="viewport" content="width=device-width, initial-scale=1.0" />
<title>Learn JavaScript</title>
</head>

<body>
	<form>
		<input type="text" id="name" placeholder="Name">
		<input type="email" id="email" placeholder="Email">
		<input type="number" id="age" placeholder="Age">
		<select id="country">
			<option value="Egypt">Egypt</option>
			<option value="Saudi Arabia">Saudi Arabia</option>
			<option value="UAE">UAE</option>
			<option value="Jordan">Jordan</option>
			<option value="Morocco">Morocco</option>
		</select>
	</form>
	<script src="./script/main.js"></script>
</body>

</html>
```

```JS
let inputs = document.querySelectorAll("input");
let select = document.querySelector("select");

inputs.forEach((input) => {
    input.value = sessionStorage.getItem(input.id) || "";

    input.addEventListener("input", () => {
        sessionStorage.setItem(input.id, input.value);
    });
});

select.value = sessionStorage.getItem("country") || select.options[0].value;

select.addEventListener("change", () => {
    sessionStorage.setItem("country", select.value);
});
```
# Destructuring
## Assignment 
```JS

```
# Map And Set
## Assignment 
```JS

```
# Regular Expression
## Assignment 
```JS

```
# Object Oriented Programming
## Assignment 
```JS

```
# Date, Generators, Modules
## Assignment 
```JS

```
# AJAX and JSON
## Assignment no.1
```JS
[
    {
        "id": 1,
        "author_name": "unknown",
        "section": "unknown",
        "title": "unknown",
        "content": "unknown"
    },
    {
        "id": 1,
        "author_name": "unknown",
        "section": "unknown",
        "title": "unknown",
        "content": "unknown"
    },
    {
        "id": 1,
        "author_name": "unknown",
        "section": "unknown",
        "title": "unknown",
        "content": "unknown"
    },
    {
        "id": 1,
        "author_name": "unknown",
        "section": "unknown",
        "title": "unknown",
        "content": "unknown"
    },
    {
        "id": 1,
        "author_name": "unknown",
        "section": "unknown",
        "title": "unknown",
        "content": "unknown"
    }
]
```

## Assignment no.2
```JS
let req = new XMLHttpRequest()
req.open("GET", "articles.json")
req.send()

req.onreadystatechange = function () {
    if (this.readyState === 4 && this.status === 200) {
        console.log(JSON.parse(this.responseText))
    }
}

req.onload = function() {
    console.log("data loaded")
}
```

## Assignment no.3 
```JS
let req = new XMLHttpRequest();

req.open("GET", "articles.json");
req.send();

req.onload = function () {
    let JSObject = JSON.parse(this.responseText);

    JSObject.forEach((article) => {
        article.section = "All";
    });

    console.log(JSObject);
};
```

## Assignment no.4 
```JS
let req = new XMLHttpRequest();

req.open("GET", "articles.json");
req.send();

req.onload = function () {
    let JSObject = JSON.parse(this.responseText);
    let div = document.createElement("div")
    div.id = 'data'

    JSObject.forEach((article) => {
        article.section = "All";
        let child = document.createElement("div")
        let h2 = document.createElement("h2")
        h2.textContent = article.title
        let p1 = document.createElement("p")
        p1.textContent = `articel number ${article.id} body`
        let p2 = document.createElement("p")
        p2.textContent = `author: ${article.author_name}`
        let p3 = document.createElement("p")
        p3.textContent = `category ${article.section}`
        child.append(h2, p1, p2, p3)
        div.append(child)
    })
    document.body.appendChild(div)
};
```
# Promises
## Assignment no.1
```JS
const getData = (apiLink) => {
    return new Promise((res, rej) => {
        let req = new XMLHttpRequest()
        req.onload = function () {
            if (this.readyState === 4 && this.status === 200) {
                res(JSON.parse(this.responseText))
            }
            else {
                rej(Error("No Data Found"))
            }
        }
        req.open("GEt", apiLink)
        req.send()
    })
}

getData("articles.json")
    .then((data) => {
        data.length = 5
        return data
    })
    .then((data) => {
        data.forEach(article => {
            let div = document.createElement("div")
            div.innerHTML = `
                <h3>${article.title}</h3>
                <p>${article.description}</p>
            `
            document.body.appendChild(div)
        });
    })
    .catch((err) => {
        console.log(err)
    })
```
## Assignment no.2
```JS
const getData = (apiLink) => {
    return fetch(apiLink)
        .then((response) => {
            if (!response.ok) {
                throw new Error("No Data Found");
            }

            return response.json();
        });
};

getData("articles.json")
    .then((data) => {
        data.length = 5;
        return data;
    })
    .then((data) => {
        data.forEach((article) => {
            let div = document.createElement("div");

            div.innerHTML = `
                <h3>${article.title}</h3>
                <p>${article.description}</p>
            `;

            document.body.appendChild(div);
        });
    })
    .catch((err) => {
        console.log(err);
    });
```

# *Done*