# Number & Maths

```javascript
let num = 123.45652857;
console.log(num.toFixed(2));
```
Output : `123.46`

```javascript
let num = 1000000000000;
console.log(num.toLocaleString("en-In"));
```
Output : `10,00,00,00,00,000`

## Number to String Conversion
- By converting the number into a string, we can use string methods and properties on the number.

```javascript
let value = 100;
console.log(typeof value);                                  //number

let strValue = value.toString();
console.log(typeof strValue);                               //string
console.log(strValue.charAt(2));                            //0
console.log(strValue.length);                               //3
```

## Number Constants and Properties

```javascript
console.log(Number.MAX_VALUE);
console.log(Number.MIN_VALUE);
console.log(Number.MAX_SAFE_INTEGER);
console.log(Number.MIN_SAFE_INTEGER);
console.log(Number.POSITIVE_INFINITY);
console.log(Number.NEGATIVE_INFINITY);
```

## Useful Math Functions

```javascript
let num1 = 16;
let num2 = -49;
let num3 = 2;
let num4 = 4;
let num5 = 24.47;
console.log(Math.max(num1, num2, num3, num4, num5));         // Output: 24.47
console.log(Math.min(num1, num2, num3, num4, num5));         // Output: -49
console.log(Math.sqrt(num1));                                // Output: 4
console.log(Math.abs(num2));                                 // Output: 49
console.log(Math.pow(num3, num4));                           // Output: 16
console.log(Math.round(num5));                               // Output: 24
console.log(Math.ceil(num5));                                // Output: 25
console.log(Math.floor(num5));                               // Output: 24
```

## Generate any random number within a given range.

```javascript
function generateRandomInteger(min, max) {
    return Math.floor(Math.random() * (max - min + 1)) + min;
}

console.log(generateRandomInteger(90, 100));                  //both included
```