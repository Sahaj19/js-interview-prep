# for loop
```javascript
let myArray = ["sahaj", 20, true];

for (let i = 0; i < myArray.length; i++) {
  console.log(myArray[i]);
}
```

# while loop
```javascript
let myArray = ["sahaj", 20, true];

let i = 0;
while (i < myArray.length) {
  console.log(myArray[i]);
  i++;
}
```

# for...of loop
```javascript
let myArray = ["sahaj", 20, true];

for (let element of myArray) {
  console.log(element);
}
```

# for...in loop
```javascript
let myArray = ["sahaj", 20, 40, "saloni"];

for (let index in myArray) {
  console.log(index, myArray[index]);
}

/*
0 sahaj
1 20
2 40
3 saloni
*/
```

# forEach() loop
```javascript
let myArr = ["sahaj", "arora", 21];

// Approach 1: Using a separate function
function values(element) {
  console.log(element);
}

myArr.forEach(values);

// Approach 2: Using an anonymous arrow function
myArr.forEach((item) => {
  console.log(item);
});

// Approach 2: Using an anonymous regular function
myArr.forEach(function (item) {
  console.log(item);
});
```

### Parameters
- <strong>element</strong>: The current element being processed in the array.
- <strong>index (Optional)</strong>: The index of the current element being processed in the array.
- <strong>arrList (Optional)</strong>: The array forEach() was called upon.

```javascript
let myArr = ["sahaj", "arora", 21];

myArr.forEach((element, index, arrList) => {
  console.log(element, index, arrList);
});

/*
sahaj   0   [ 'sahaj', 'arora', 21 ]
arora   1   [ 'sahaj', 'arora', 21 ]
21      2   [ 'sahaj', 'arora', 21 ]
*/
```

### return value
- The `forEach()` loop does not return anything. It simply iterates over the array and executes the provided function for each element.

```javascript
let myArr = ["sahaj", "arora", 21];

let result = myArr.forEach((item) => {
  return item;                            // This return statement has no effect
});

console.log(result);                      // Output will be undefined
```

# some()
- Returns `true` if at least one element in the array satisfies the condition specified in the callback function.

```javascript
let myArr = [10, 20, 30, 87, 55, -34];

let result = myArr.some((value) => {
  return value >= 80;
});

console.log(result);                  // Output: true (since 87 is greater than or equal to 80)
```

# every()
- Returns `true` only if all elements in the array satisfy the condition specified in the callback function.

```javascript
let myArr = [10, 20, 30, 40, 50];

let result = myArr.every((value) => {
  return value % 10 === 0;
});

console.log(result);                  // Output : true (since every element is completely divisible by 10)
```

# find()
- The `find()` method in JavaScript is used to return the first element in the array that satisfies the provided testing function. If no such element is found, `undefined` is returned. 

```javascript
let myArr = [13, 8, 40, 4, 5];

let result1 = myArr.find((value) => {
  return value >= 100;
});

console.log(result1); 
// Output: undefined (since no element in the array is greater than or equal to 100)
```

```javascript
let myArr = [13, 20, "sahaj", 100, "developer"];

let result1 = myArr.find((value) => {
  return typeof value === "string";
});

console.log(result1);   //sahaj
```

### What if we need all the elements satisfying our given condition??
- We will use `filter()` method.

```javascript
let myArr = [13, 20, "sahaj", 100, "developer"];

let result = myArr.filter((value) => {
  return typeof value === "string";
});

console.log(result);          //[ 'sahaj', 'developer' ]
```

# findIndex()
- The `findIndex()` method in JavaScript is used to find the index of the first element in the array that satisfies the provided testing function. It returns `-1` if no such element is found.

```javascript
let myArr = ["sahaj", "saloni", "arnav", "shivam"];

let result = myArr.findIndex((value) => {
  return value === "sahaj arora";
});

console.log(result);                          //-1
```

```javascript
let myArr = ["sahaj", "saloni", "arnav", "shivam"];

let result = myArr.findIndex((value) => {
  return value === "arnav";
});

console.log(result);                          //2
```

# map()
- It creates a new array with the results of calling a provided function on every element in the calling array.

```javascript
let myArr = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];

let result = myArr.map((value) => {
  return value * 10;
});

console.log(result);              //[10, 20, 30, 40, 50, 60, 70, 80, 90, 100]
```

# filter()
- The `filter()` method in JavaScript is used to create a new array with all elements that pass the test implemented by the provided function.

```javascript
let numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];

let evenNumbers = numbers.filter((num) => {
  return num % 2 === 0;
});

console.log(evenNumbers);          // Output: [2, 4, 6, 8, 10]
```

# reduce()
- The `reduce()` method reduces an array to a single value.

### when initial value is passed
- The accumulator `acc` starts with the initial value (10), and the current value `curr` starts from the first element of the array (1).

```javascript
let myArr = [1, 2, 3, 4, 5];

let result = myArr.reduce((acc, curr) => {
  console.log(`Acc : ${acc} and Curr : ${curr}`);
  return acc + curr;
}, 10);

console.log(result);
```

Output 
```javascript
Acc : 10 and Curr : 1
Acc : 11 and Curr : 2
Acc : 13 and Curr : 3
Acc : 16 and Curr : 4
Acc : 20 and Curr : 5
25
```

### when initial value is not passed
- The accumulator `acc` from the first element of the array (1), and the current value `curr` starts from the second element of the array (2).

```javascript
let myArr = [1, 2, 3, 4, 5];

let result = myArr.reduce((acc, curr) => {
  console.log(`Acc : ${acc} and Curr : ${curr}`);
  return acc + curr;
});

console.log(result);
```

Output 
```javascript
Acc : 1 and Curr : 2
Acc : 3 and Curr : 3 
Acc : 6 and Curr : 4 
Acc : 10 and Curr : 5
15
```

