# outclick 👉
![code style : standard](https://img.shields.io/badge/code%20style-standard-brightgreen.svg)
![build : passing](https://img.shields.io/badge/build-passing-brightgreen.svg)

A library used to detect DOM clicks outside specific elements, useful for closing menus

![Example use .gif](https://raw.githubusercontent.com/joe-tom/outclick/master/test/outclick.gif)

## Warning
If you don't specifiy otherwise, this library will alter the addEventListener property. This should be okay for most cases but may lead to complications with other libraries. 

## Installation
You can download the latest [release](https://raw.githubusercontent.com/joe-tom/outclick/master/release/outclick.min.js) or install it as an npm package
```javascript
npm install --save outclick
```

## Basic Usage
Using outclick you can register event listeners on DOM elements to detect whether another element that was that element or another element inside it was clicked.
The most common use of this is in menus.
```javascript
var menu = document.getElementById('menu')

menu.onoutclick = function () {
	hide(menu)
}
```
this can also be done using the addEventListener method
```javascript
var menu = document.getElementById('menu')

menu.addEventListener('outclick', function (e) {
	hide(menu)
})
```
the exceptions parameter, is an array of elements that are an exception to the outclick event.
```javascript
var menu = document.getElementById('menu')
var exceptions = [
 document.getElementById('menuBtn'),
 document.getElementById('dontCloseTheMenu')
]

menu.addEventListener('outclick', function (e) {
	hide(menu)
}, exceptions)
```
Alternatively, you can also use the html attribute outclick to trigger an event.
This does not handle dynamic HTML, and we have no plans to add that, yet
```html
<div outclick="someFunc()"></div>
```