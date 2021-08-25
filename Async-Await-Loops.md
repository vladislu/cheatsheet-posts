---
title: Async-Await-Loops
categories: 
  - JavaScript
date: 2021-06-01 19:20:42
tag: [tag1]
version: cheatSheets
github: Async-Await-Loops
---

## get started

## Async function get array and run in side function and wait for result

### For Loop

```js
const forLoop = async (array, func) => {
  console.log('Start');
  let results;
  for (let index = 0; index < array.length; index++) {
    const item = array[index];
    const result = await func(item);
    results.push(result);
  }
  console.log('End');
  return results;
}

// Example
forLoop([1,2,3], item => console.log(item)); 
// Start
// 1
// 2
// 3
// End
```

### ForEach Loop

```js
const forEachLoop = (array, func) => {
  console.log('Start');
  let results;
  array.forEach(async item => {
    const result = await func(item);
    results.push(result);
  })
  console.log('End');
  return results;
}

// Example
forLoop([1,2,3], item => console.log(item)); 
// Start
// 1
// 2
// 3
// End
```