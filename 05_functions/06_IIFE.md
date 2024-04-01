# Immediately Invoked Function Expressions (IIFE)
- If we put all our JavaScript files together into one `index.html` file, we might have problems with variables mixing up or causing issues with each other. This is where IIFE comes in handy to keep things organized and separate.
- Always remember to add a `semicolon at the end of an IIFE`. It helps to avoid unexpected errors in your code.
- IIFE functions run automatically as soon as the file is executed.

## Named IIFE

```javascript
(function greet() {
  console.log("Hello from IIFE");
})();
```
Output : `Hello from IIFE`

## IIFE using arrow function

```javascript
(() => {
  console.log("Arrow function IIFE");
})();
```
Output : `Arrow function IIFE`

## IIFE with arguments

```javascript
(function greetOne(username) {
  console.log(`Hello ${username}`);
})("sahaj");
```
Output : `Hello sahaj`

```javascript
(function greetOne(username) {
  console.log(`Hello ${username}`);
})();
```
Output : `Hello undefined`

```javascript
(function greetTwo(username = "anonymous") {
  console.log(`Hello ${username}`);
})();
```
Output : `Hello anonymous`

## IIFE expression

```javascript
let result = (function() {
  console.log("Hello there");
})();

result;
```
Output : `Hello there`

```javascript
let result = (function () {
  return "sahaj";
})();

console.log(result);
```
Output : `sahaj`

```javascript
let result = (function () {
  return function () {
    return "sahaj arora";
  };
})();

console.log(result());
```
Output : `sahaj arora`