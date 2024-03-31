# Basic array destructuring
```javascript
let myArr = ["sahaj", "arora", 21, "male"];

let [firstName, lastName, age, gender] = myArr;

console.log(firstName);            //sahaj
console.log(lastName);             //arora
console.log(age);                  //21
console.log(gender);               //male
```

# Skipping values while destructuring
```javascript
let myArr = ["sahaj", "arora", 21, "male"];

let [firstName, lastName, , gender] = myArr;

console.log(firstName);            //sahaj
console.log(lastName);             //arora
console.log(gender);               //male
```

```javascript
let myArr = ["sahaj", "arora", 21, "male", "developer"];

let [, , age, , profession] = myArr;

console.log(age);                  //21
console.log(profession);           //developer
```

# Default Values
```javascript
let myArr = [];

let [a, b, c] = myArr;

console.log(a);                    //undefined
console.log(b);                    //undefined
console.log(c);                    //undefined
```

```javascript
let myArr = [];

let [a = 2, b = 2, c = "sahaj"] = myArr;

console.log(a);                     //2
console.log(b);                     //2
console.log(c);                     //sahaj
```

```javascript
let [a = 2, b = 3, c = 4] = [10, , 20];

console.log(a);                     //10
console.log(b);                     //3
console.log(c);                     //20
```

```javascript
let [a = 2, b, c = 4] = [10, , 20];

console.log(a);                     //10
console.log(b);                     //undefined
console.log(c);                     //20
```

# Nested Destructuring
```javascript
let myArr = [1, 2, [3, 4, [5, 6]]];

let [a, b, [c, d, [e, f]]] = myArr;

console.log(a);                    //1
console.log(b);                    //2
console.log(c);                    //3
console.log(d);                    //4
console.log(e);                    //5
console.log(f);                    //6
```

```javascript
let myArr = [1, 2, ["sahaj", 21]];

let [, , [, age]] = myArr;

console.log(age);                  //21
```

# rest operator
```javascript
let myArr = ["sahaj", "arora", 21, "male", "developer"];

let [firstName, lastName, ...remaining] = myArr;

console.log(firstName);                      //sahaj
console.log(lastName);                       //arora
console.log(remaining);                      //[ 21, 'male', 'developer' ]

let [age, gender, profession] = remaining;

console.log(age);                            //21
console.log(gender);                         //male
console.log(profession);                     //developer
```

# Object Destructuring Inside Array Destructuring
```javascript
let myArr = [
  {
    username: "sahaj",
    age: 21,
  },
  {
    username: "saloni",
    age: 20,
  },
];
```

```javascript
//Partial destructuring

let [{ username, age }] = myArr;

console.log(username);                  //sahaj
console.log(age);                       //21
```

```javascript
//complete destructuring

let [{ username: userName1, age: age1 }, { username: userName2, age: age2 }] = myArr;

console.log(userName1, age1);           //sahaj 21
console.log(userName2, age2);           //saloni 20
```