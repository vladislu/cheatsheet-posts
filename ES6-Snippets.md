---
title: ES6-Snippets
categories: 
  - JavaScript
date: 2021-03-26 11:20:42
tag: [tag1]
version: cheatSheets
github: ES6-Snippets
---

## get started

### Copy a string to the clipboard

```js
const copyToClipboard = str => {
  const el = document.createElement('textarea');
  el.value = str;
  el.setAttribute('readonly', '');
  el.style.position = 'absolute';
  el.style.left = '-9999px';
  document.body.appendChild(el);
  const selected =
    document.getSelection().rangeCount > 0 ? 
    document.getSelection().getRangeAt(0) : false;
  el.select();
  document.execCommand('copy');
  document.body.removeChild(el);
  if (selected) {
    document.getSelection().removeAllRanges();
    document.getSelection().addRange(selected);
  }
};

// Example
copyToClipboard('Lorem ipsum'); 
// 'Lorem ipsum' copied to clipboard.
```

### Encode a set of form elements as an object

```js
const formToObject = form =>
  Array.from(new FormData(form)).reduce(
    (acc, [key, value]) => ({
      ...acc, [key]: value
    }),{}
  );

// Example
formToObject(document.querySelector('#form')); 
// { email: 'test@email.com', name: 'Test Name' }
```



### Smooth-scroll to the top of the page

```js
const scrollToTop = () => {
  const c = document.documentElement.scrollTop || 
            document.body.scrollTop;
  if (c > 0) {
    window.requestAnimationFrame(scrollToTop);
    window.scrollTo(0, c - c / 8);
  }
};

// Example
scrollToTop();
```

### Scroll position of the current page

```js
const getScrollPosition = (el = window) => ({
  x: el.pageXOffset !== undefined ? 
     el.pageXOffset : el.scrollLeft,
  y: el.pageYOffset !== undefined ?
     el.pageYOffset : el.scrollTop
});

// Example
getScrollPosition(); // {x: 0, y: 200}
```

### Mobile device or a desktop/laptop

```js
const detectDeviceType = () =>
  /Android|webOS|iPhone|iPad|
  iPod|BlackBerry|IEMobile|Opera Mini/i.
  test(navigator.userAgent)
    ? 'Mobile'
    : 'Desktop';

// Example
detectDeviceType(); // "Mobile" or "Desktop"
```

### Hide all elements specified

```js
const hide = (...el) => 
   [...el].forEach(e => 
   (e.style.display = 'none'));

// Example
// Hides all <img> elements on the page
hide(document.querySelectorAll('img'));
```

### Invoke the provided function after wait

```js
const delay = (fn, wait, ...args) => 
    setTimeout(fn, wait, ...args);

// Example
delay(
  (text) => {
    console.log(text);
  },1000,'later'); 
// Logs 'later' after one second.
```

### Get the difference (in days) 

```js
const getDaysDiffBetweenDates = 
  (dateInitial, dateFinal) =>
  (dateFinal - dateInitial) / 
  (1000 * 3600 * 24);

// Example
getDaysDiffBetweenDates(
  new Date('2017-12-13'),
  new Date('2017-12-22')); // 9
```

## Http requests

### GET request to the passed URL

```js
const httpGet = (url, callback, err) => {
  const request = new XMLHttpRequest();
  request.open('GET', url, true);
  request.onload = () => 
    callback(request.responseText);
  request.onerror = () => 
    err(request);
  request.send();
};

httpGet(
  'https://jsonplaceholder.typicode.com/posts/1',
  console.log
); 


```

### POST request to the passed URL

```js
const httpPost = (url, data, callback, err) => {
  const request = new XMLHttpRequest();
  request.open('POST', url, true);
  request.setRequestHeader('Content-type',
   'application/json; charset=utf-8');
  request.onload = () => 
    callback(request.responseText);
  request.onerror = () => 
    err(request);
  request.send(data);
};

const newPost = {
  userId: 1,
  id: 1337,
  title: 'Foo',
  body: 'bar bar bar'
};
const data = JSON.stringify(newPost);
httpPost(
  'https://jsonplaceholder.typicode.com/posts',
  data,
  console.log
); 

`Logs: {"userId": 1, "id": 1337, 
"title": "Foo", "body": "bar bar bar"}`
```