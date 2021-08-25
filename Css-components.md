---
title: Css components 
categories: 
  - Css
date: 2021-08-24 21:20:42
tag: [tag1]
version: cheatSheets
github: Css-components
---

## get started

## Css components

### checkbox

```js
input[type="checkbox"]:checked + label::after {
  content: "";
  position: absolute;
  width: 1.3ex;
  height: 0.4ex;
  background: rgba(0, 0, 0, 0);
  top: 0.9ex;
  left: 0.4ex;
  border: 3px solid white;
  border-top: none;
  border-right: none;
  -webkit-transform: rotate(-45deg);
  -moz-transform: rotate(-45deg);
  -o-transform: rotate(-45deg);
  -ms-transform: rotate(-45deg);
  transform: rotate(-45deg);
}

input[type="checkbox"]:checked + label::before {
  content: "";
  background: #030000;
}

input[type="checkbox"]:disabled + label::before {
  content: "";
  border: 1px solid rgba(0, 0, 0, 0.5);
  background: rgba(0, 0, 0, 0.5);
}

input[type="checkbox"] {
  line-height: 2.1ex;
}

input[type="checkbox"] {
  position: absolute;
  left: -999em;
}

input[type="checkbox"] + label {
  position: relative;
  overflow: hidden;
  cursor: pointer;
}

input[type="checkbox"] + label::before {
  content: "";
  display: inline-block;
  vertical-align: -41%;
  height: 16px;
  width: 16px;
  background-color: white;
  box-sizing: border-box;
  border: 1px solid #8c8c8c;
  border-radius: 2px;
  margin: 8px 0.5em 3px 0px;
}
```

### radio button

```js
input[type="radio"] + label {
  position: relative;
  overflow: hidden;
  cursor: pointer;
}

input[type="radio"] {
  display: none;
}

input[type="radio"] + label::before {
  content: " ";
  display: inline-block;
  position: relative;
  top: 5px;
  margin: 0 5px 2px 0;
  width: 14px;
  height: 14px;
  border-radius: 16px;
  border: 1px solid #080000;
  background-color: transparent;
}

input[type="radio"]:checked + label::after {
  border-radius: 16px;
  width: 8px;
  height: 8px;
  position: absolute;
  top: 4px;
  left: 4px;
  content: " ";
  display: block;
  background: #030000;
}

```