# Implicit Scope
- Single statement, no curly braces, it's commonly referred to as implicit scoping.

```javascript
let value;

value = 100;
if (typeof value === "number") console.log("It is of number type");

value = "sahaj";
if (typeof value === "string") console.log("It is of string type");

value = true;
if (typeof value === "boolean") console.log("It is of boolean type");
```

# Switch Case
- Without the `break` keyword, the control flow would continue to the next case, potentially leading to unintended behavior.

```javascript
let value;
value = "sahaj";                  //N0 Valid Day Available!
value = 4;                        //Thursday!
value = 1;                        //Monday!
value = 0;                        //No Valid Day Available!

switch (value) {
  case 1: {
    console.log("Monday!");
    break;
  }
  case 2: {
    console.log("Tuesday!");
    break;
  }
  case 3: {
    console.log("Wednesday!");
    break;
  }
  case 4: {
    console.log("Thursday!");
    break;
  }
  case 5: {
    console.log("Friday!");
    break;
  }
  case 6: {
    console.log("Saturday!");
    break;
  }
  case 7: {
    console.log("Sunday!");
    break;
  }
  default: {
    console.log("No Valid Day Available!");
    break;
  }
}
```

# Truthy and Falsy Values
```javascript
let value;
```

```javascript
//+++++++++ Falsy values +++++++++++

value = false;
value = "";
value = 0;
value = -0;
value = 0n;
value = null;
value = undefined;
value = NaN;
```
Output : `false`

```javascript
//+++++++++ Truthy values +++++++++++

value = true;
value = " ";
value = "0";
value = "false";
value = "sahaj";
value = "null";
value = {};
value = [];
value = function () {};
```
Output : `true`

# True Values
```javascript
console.log(false == 0);
console.log(false == " ");
console.log(false == "");
console.log(0 == "");
console.log(0 == " ");
console.log(true == 1);
```
Output : `true`

# Checking for Empty Array
```javascript
let arr = [];

if (arr.length === 0) {
  console.log("array is empty");
} else {
  console.log("array has some value in it");
}
```

# Checking for Empty Object
```javascript
let obj = {};

if (Object.keys(obj).length === 0) {
  console.log("obj is empty");
} else {
  console.log("obj has some value in it");
}
```

# Nullish Coalescing Operator (??)
- It is used to provide a default value for variables that may be `null` or `undefined`.

```javascript
let value;

value = null ?? 10;                     //10
value = 10 ?? null;                     //10
value = null ?? undefined;              //undefined
value = null ?? undefined ?? 20;        //20
value = 20 ?? "sahaj";                  //20
value = "sahaj" ?? 20;                  //sahaj

console.log(value);
```

# Ternary Operator
```javascript
let age = 21;
let value = age >= 18 ? "You can drive" : "You cannot drive";
console.log(value);
```
Output : `You can drive`

```javascript
let num = 10;
let result = num % 2 === 0 ? "Even" : "Odd";
console.log(result);
```
Output : `Even`

# Optional Chaining (?.)
```javascript
let userInfo = {
  username: "sahaj",
  address: {
    country: "India",
    state: "Delhi",
    city: "Narela",
  },
};
```

### Without Optional Chaining
```javascript
let country = userInfo.address ? userInfo.address.country : "undefined";
let state = userInfo.address ? userInfo.address.state : "undefined";
let city = userInfo.address ? userInfo.address.city : "undefined";
let liveLocation = userInfo.address ? userInfo.address.liveLocation : "undefined";
```

### With Optional Chaining
```javascript
let country = userInfo.address?.country;
let state = userInfo.address?.state;
let city = userInfo.address?.city;
let liveLocation = userInfo.address?.liveLocation;
```

### Output
```javascript
console.log(country);                  // Output: "India"
console.log(state);                    // Output: "Delhi"
console.log(city);                     // Output: "Narela"
console.log(liveLocation);             // Output: undefined
```
