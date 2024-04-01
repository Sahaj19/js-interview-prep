# Function declaration vs Function expression
```javascript
//Function declaration

function myName() {
  console.log("sahaj");
}
myName();
```

```javascript
//Function expression

let myName = function () {
  console.log("sahaj");
};

myName();
```

# Parameters & Arguments
- Variables that we define in the function's declaration (i.e num1 , num2) are called `Parameters`.
- `Arguments` are the Actual values that are passed to the function when its called (i.e 7 , 18).

```javascript
function addition(num1, num2) {
  console.log(num1 + num2);
}

addition(7, 18);
```

# Handling Missing Arguments
```javascript
function greet(username) {
  if (username === undefined) {
    return "Please enter a username";
  }
  return `Hello ${username}`;
}

console.log(greet("sahaj"));  //Hello sahaj
console.log(greet(""));       //Hello 
console.log(greet());         //Please enter a username
```

# Default parameters
```javascript
function greet(username = "anonymous") {
  return `Hello ${username}`;
}

console.log(greet("sahaj"));   //Hello sahaj
console.log(greet(""));        //Hello
console.log(greet());          //Hello anonymous
```

# Passing Objects as arguments
```javascript
let user = {
  myName: "sahaj",
  age: 21,
};

function userInfo(userObj) {
  return `${userObj.myName} is ${userObj.age} years old!`;
}

console.log(userInfo(user));                              //sahaj is 21 years old!
console.log(userInfo({ myName: "saloni", age: 20 }));     //saloni is 20 years old!
```

# Passing Arrays as Arguments
```javascript
let arr = [20, "sahaj", true, 100];

function secondValue(anyArray) {
  return anyArray[1];
}

console.log(secondValue(arr));                   //sahaj
console.log(secondValue([1, 2, 3, 4, 5]));       //2
```

# First Class Functions
- Functions in JS are first class citizens meaning they can be treated just like any other value, such as strings , numbers or objects.

```javascript
let func1 = function () {
  return "I am function one";
};

let func2 = function () {
  return "I am function two";
};

let func3 = function () {
  return "I am function three";
};

let arr_functions = [func1, func2, func3];

console.log(arr_functions[0]());           //I am function one
console.log(arr_functions[1]());           //I am function two
console.log(arr_functions[2]());           //I am function three
```

# Return Types : Explicit vs Implicit
```javascript
//Explicit return

let func = (num1, num2) => {
  return num1 + num2;
};

console.log(func(4, 5));
```

```javascript
//Implicit return

let func = (num1, num2) => (num1 + num2);
console.log(func(4, 5));
```

# Arguments Object
- `arguments` is a special array-like object available in every regular function, containing all the arguments passed to the function.

```javascript
function func() {
  return arguments;
}

let obj_result = func(19, "sahaj", true);
```

```javascript
console.log(obj_result);                        //{ '0': 19, '1': 'sahaj', '2': true }
console.log(Array.isArray(obj_result));         //false
```

```javascript
let array_result = Array.from(obj_result);
console.log(array_result);                      //[ 19, 'sahaj', true ]
console.log(Array.isArray(array_result));       //true
```

# Mini Hoisting
```javascript
console.log(one());                     //I am function one

function one() {
  return "I am function one";
}
```
Result : `Function declarations can be accessed before their definition.`

```javascript
console.log(two());                     //error

let two = function () {
  return "I am function two";
};
```
Result : `Function expressions cannot be accessed before their definition`