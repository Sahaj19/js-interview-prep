# Let's first understand the problem

- You're building a function to print user details. You might start by writing code like this, where each user object has its own way to print details:

```javascript
let userDetails1 = {
  myName: "sahaj",
  myAge: 22,
  printDetails: function() {
    console.log(`My name is ${this.myName} and I am ${this.myAge} years old!`);
  }
};

let userDetails2 = {
  myName: "tim david",
  myAge: 25,
  printDetails: function() {
    console.log(`My name is ${this.myName} and I am ${this.myAge} years old!`);
  }
};

let userDetails3 = {
  myName: "sheldon cooper",
  myAge: 16,
  printDetails: function() {
    console.log(`My name is ${this.myName} and I am ${this.myAge} years old!`);
  }
};

userDetails1.printDetails();  // My name is sahaj and I am 22 years old!
userDetails2.printDetails();  // My name is tim david and I am 25 years old!
userDetails3.printDetails();  // My name is sheldon cooper and I am 16 years old!
```

- Notice how `printDetails` function is **duplicated** across objects. This violates the DRY (Don't Repeat Yourself) principle.

### Solution 1: Using Classes (Modern Approach)

```javascript
class User{
  constructor(myName, myAge) {
    this.myName = myName;
    this.myAge = myAge;
  }

  printDetails() {
    console.log(`My name is ${this.myName} and I am ${this.myAge} years old!`)
  }
}

const userDetails1 = new User("sahaj", 22);
const userDetails2 = new User("tim david", 25);
const userDetails3 = new User("sheldon cooper", 16);

userDetails1.printDetails();  // My name is sahaj and I am 22 years old!
userDetails2.printDetails();  // My name is tim david and I am 25 years old!
userDetails3.printDetails();  // My name is sheldon cooper and I am 16 years old!
```

### Solution 2: Using call

```javascript
let userDetails1 = {
  myName: "sahaj",
  myAge: 22,
};

let userDetails2 = {
  myName: "tim david",
  myAge: 25,
};

let userDetails3 = {
  myName: "sheldon cooper",
  myAge: 16,
};

function printDetails() {
    console.log(`My name is ${this.myName} and I am ${this.myAge} years old!`);
  }

printDetails.call(userDetails1);  // My name is sahaj and I am 22 years old!
printDetails.call(userDetails2);  // My name is tim david and I am 25 years old!
printDetails.call(userDetails3);  // My name is sheldon cooper and I am 16 years old!
```

### Then, why do we even need call() method?
- **call(), apply(), & bind()** comes handly when we need to separate the object to that function and when data is of different size and form , but we need the data in similar format. We can make the function generic using these methods.

```javascript
const user = {
  myName: "sahaj",
  myAge: 22
};

const apiUser = {
  fullName: "Leonard Hofstadter",
  age: 33,
  status: "Active"
};

const dbUser = {
  first_name: "Penny",
  user_age: 28,
  role: "Sales Representative"
};

function printDetails() {
  console.log(`My name is ${this.myName} and I am ${this.myAge} years old!`)
}

printDetails.call(user);                                                // My name is sahaj and I am 22 years old!
printDetails.call({myName: apiUser.fullName, myAge: apiUser.age});      // My name is Leonard Hofstadter and I am 33 years old!
printDetails.call({myName: dbUser.first_name, myAge: dbUser.user_age}); // My name is Penny and I am 28 years old!
```


## call()
- The `call()` method executes a function immediately, allowing you to specify what `this` should refer to inside that function. **It accepts arguments individually, one after another**.
- `Example` func.call(obj, arg1, arg2, arg3)

```javascript
let userDetails1 = {
  myName: "sahaj",
  myAge: 22,
};

let userDetails2 = {
  myName: "tim david",
  myAge: 25,
};

let userDetails3 = {
  myName: "sheldon cooper",
  myAge: 16,
};

function printDetails(profession, company) {
    console.log(`${this.myName} - ${this.myAge} - ${profession} - ${company}`);
  }

printDetails.call(userDetails1, "Software Engineer", "Strawket");    // sahaj - 22 - Software Engineer - Strawket
```

## apply()
- The `apply()` method also executes a function immediately like `call()`, but instead of taking arguments separately, **it accepts arguments as an array (or array-like object)**. This is useful when the number of arguments is dynamic.
- `Example` func.apply(obj, [arg1, arg2, arg3])

```javascript
let userDetails1 = {
  myName: "sahaj",
  myAge: 22,
};

let userDetails2 = {
  myName: "tim david",
  myAge: 25,
};

let userDetails3 = {
  myName: "sheldon cooper",
  myAge: 16,
};

function printDetails(profession, company) {
    console.log(`${this.myName} - ${this.myAge} - ${profession} - ${company}`);
  }

printDetails.apply(userDetails2, ["Cricketer", "RCB"]);             // tim david - 25 - Cricketer - RCB
```

## bind()
- The `bind()` method creates a new function where this is permanently bound to a specific object. Unlike call() and apply(), it doesn't execute the function immediately—instead, **it returns a new function that can be called later.**
- `Example` const newFunc = func.bind(obj, arg1, arg2, arg3)

```javascript
let userDetails1 = {
  myName: "sahaj",
  myAge: 22,
};

let userDetails2 = {
  myName: "tim david",
  myAge: 25,
};

let userDetails3 = {
  myName: "sheldon cooper",
  myAge: 16,
};

function printDetails(profession, company) {
    console.log(`${this.myName} - ${this.myAge} - ${profession} - ${company}`);
  }

const result = printDetails.bind(userDetails3, "Actor", "Young Sheldon"); 
result();                                                            // sheldon cooper - 16 - Actor - Young Sheldon
```

### Summary
- `call()`  → Immediate execution, separate arguments.

- `apply()` → Immediate execution, arguments in an array.

- `bind()`  → No Immediate execution, separate arguments, Returns a new function for later use.

