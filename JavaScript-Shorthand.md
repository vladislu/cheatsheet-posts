---
title: JavaScript-Shorthand
categories: 
  - JavaScript
date: 2021-03-26 11:20:42
tag: [tag1]
version: cheatSheets
github: JavaScript-Shorthand
---


## get started

### Declaring variables
```js

// Longhand
let x;   
let y = 20;   
```

```js
// Shorthand
let x, y = 20;   
```

### Assigning values to multiple variables

```js
// Longhand
let a, b, c; 
a = 5; 
b = 8; 
c = 12;
```

```js
// Shorthand
let [a, b, c] = [5, 8, 12];
```

### The Ternary operator

```js
// Longhand
let result; 
let marks = GetNumber(); 
if(marks >= 56){
 result = 'Pass'; 
}else{ 
 result = 'Fail'; 
} 
```

```js
// Shorthand
let result = GetNumber() >= 56 ? 'Pass' : 'Fail'; 
```

### AND(&&) Short circuit evaluation

```js
// Longhand
if (isLoggedin) {
 goToHomepage(); 
} 
```

```js
// Shorthand
isLoggedin && goToHomepage();
```

### Swap two variables

```js
let x = 'Hello', y = 55; 
```

```js
// Longhand
const temp = x; 
x = y; 
y = temp; 
```

```js
// Shorthand
[x, y] = [y, x];
```

### Assigning default value

```js
// Longhand
let imagePath; 
let path = getImagePath(); 
if(path !== null && path !== undefined) { 
  imagePath = path; 
} else { 
  imagePath = 'default.jpg'; 
} 
```

```js
// Shorthand
let imagePath = getImagePath() || 'default.jpg';
```

### Arrow Function

```js
// Longhand
function add(num1, num2) { 
   return num1 + num2; 
} 
```

```js
// Shorthand
const add = (num1, num2) => num1 + num2;
```

Reference: [JavaScript Arrow function](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Arrow_functions)

### Object Property Assignment

```js
let firstname = 'John';
let lastname = 'Doe';
```

```js
// Longhand
let obj = {firstname: firstname,
           lastname: lastname};
```

```js
// Shorthand
let obj = {firstname, lastname};
```

### Multi-line String

```js
// Longhand
console.log('JavaScript, often abbreviated\n' +
'as JS, is a programming language that \n' + 
'conforms to the ECMAScript specification. \n' + 
'JavaScript is high-level, often \n' + 
'just-in-time compiled, and multi-paradigm.' ); 
```

```js
// Shorthand
console.log(`JavaScript, often abbreviated 
as JS, is a programming language that 
conforms to the ECMAScript specification. 
JavaScript is high-level, often 
just-in-time compiled, and multi-paradigm.`);
```

### String into a Number

```js
// Longhand
let total = parseInt('453');
let average = parseFloat('42.6');
```

```js
// Shorthand
let total = +'453'; 
let average = +'42.6';
```

### Double NOT bitwise operator (~~)

```js
// Longhand
const floor = Math.floor(6.8); // 6 
```

```js
// Shorthand
const floor = ~~6.8; // 6
```
Reference: [Math.floor()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math/floor)

### Repeat a string for multiple times

```js
// Longhand
let str = ''; 
for(let i = 0; i < 5; i ++) { 
  str += 'Hello '; 
} 
console.log(str); // Hello Hello Hello Hello Hello 
```

```js
// Shorthand
'Hello '.repeat(5);
```

### Find max and min number in array

```js
const arr = [2, 8, 15, 4]; 
```

```js
// Longhand
let min = 100, max = 0
for(let i = 0; i < arr.length ; i ++) { 
  if(i >= max){
    max = i;
  }
  if(i <= min){
    min = i;
  }
}
```

```js
// Shorthand
Math.max(...arr); // 15 
Math.min(...arr); // 2
```

### For loop

```js
let arr = [10, 20, 30, 40]; 
```

```js
// Longhand
for (let i = 0; i < arr.length; i++) { 
  console.log(arr[i]); 
} 
```

```js
// Shorthand
for (const val of arr) { 
  console.log(val); 
}
```

```js
// Shorthand
for (const index in arr) { 
  console.log(`index: ${index},
               value: ${arr[index]}`); 
}
```

### Template Literals

```js
// Longhand
console.log('Call from ' + number + ' at ' + time);
```

```js
// Shorthand
console.log(`Call from ${number} at ${time}`);
```

### Get character from string

```js
let str = 'Hello world'; 
```

```js
// Longhand
str.charAt(2); // e
```

```js
// Shorthand
str[2]; // e
```

### Exponent Power

```js
// Longhand
const power = Math.pow(4, 3); // 64 
```

```js
// Shorthand
const power = 4**3; // 64
```

### Merging of arrays

```js
let arr = [20, 30]; 
```

```js
// Longhand
let arr2 = arr.concat([60, 80]); 
// [20, 30, 60, 80] 
```

```js
// Shorthand
let arr2 = [...arr, 60, 80]; 
// [20, 30, 60, 80]
```

### Loop in object

```js
let obj = {x: 20, y: 50};
```

```js
// Longhand
const objectArray = Object.keys(obj);
for (let i = 0; i < objectArray.length; i++) { 
  console.log(obj[objectArray[i]]); 
} 
```

```js
// Shorthand
for (const key in obj) { 
  console.log(obj[key]); 
}
```

### Multiple condition checking

```js
// Longhand
if (value === 1 ||
    value === 'one' ||
    value === 2 || 
    value === 'two') { 
     // Execute some code 
} 
```

```js
// Shorthand
if ([1, 'one', 2, 'two'].indexOf(value) >= 0) { 
    // Execute some code 
}
```

```js
// Shorthand
if ([1, 'one', 2, 'two'].includes(value)) { 
    // Execute some code 
}
```
### Deep cloning of multi-level object

```js
let obj = {x: 20, y: {z: 30}}; 
```

```js
// Longhand
const makeDeepClone = (obj) => { 
  let newObject = {}; 
  Object.keys(obj).map(key => { 
    if(typeof obj[key] === 'object'){ 
      newObject[key] = makeDeepClone(obj[key]); 
    } else { 
      newObject[key] = obj[key]; 
    } 
  }); 
 return newObject; 
} 
const cloneObj = makeDeepClone(obj); 
```

```js
// Shorthand
const cloneObj = JSON.parse(JSON.stringify(obj));
```

```js
//Shorthand for single level object
let obj = {x: 20, y: 'hello'};
const cloneObj = {...obj};
```