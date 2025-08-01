# Let's first understand the problem

```javascript
const myName = "sahaj";
const myAge = 23;
const myProfession = "frontend engineer";

function greet(myName) {
    console.log(`Hello ${myName}`);
}
function getMyAge(myAge) {
    console.log(`My Age is ${myAge}`);
} 

function getMyProfession(myProfession) {
    console.log(`I am a ${myProfession}`);
} 

greet(myName);                             // Hello sahaj
getMyAge(myAge);                           // My Age is 23
getMyProfession(myProfession);             // I am a frontend engineer

/*
In procedural or function-based code, variables and functions are separate
As the App grows :- 
- Data is passed around manually
- Logic becomes harder to trace
- Dependencies tangle

In Short :-
- We need OOPS to structure, simplify, and scale software by organizing logic around real-world objects instead of loose functions and data.
*/
```

## Introduction to OOPS
- `Object-Oriented Programming (OOP)` is a way of writing code where we organize everything around objects.
- Each object has its own data (like name, age, speed) and its own actions (like walk, drive, speak).
- This makes our code easier to `manage` and `reuse`.

```javascript
class User {
    name = "sahaj";
    age = 23;
    speed = "100 Km/h";

    walk() {
        console.log("I am walking");
    }

    drive() {
        console.log("I am driving");
    }

    speak() {
        console.log("I am speaking");
    }
    
}

const myUser = new User();

console.log(myUser.name);                     // sahaj
console.log(myUser.age);                      // 23
console.log(myUser.speed);                    // 100 Km/h

myUser.walk();                                // I am walking
myUser.drive();                               // I am driving
myUser.speak();                               // I am speaking
```
- Inside `classes`, we don't need `let` and `const` variable to declare a variable.
- Inside `classes`, we don't need `function` keyword to define a function.
- By convention, class names start with a capital letter (e.g., `User`).
- We create an object (instance) using the `new` keyword: `const myUser = new User();`

## Constructor
- A `constructor` is a special method inside a `class` that runs everytime when an `object is created (i.e instantiated using the new keyword).`
- It is used to set `initial values or perform any setup logic.`
- Only `one constructor per class` is allowed in JS.

```javascript
class Parent {
    constructor() {
        console.log("Inside Constructor.");
    }
}

const myParent = new Parent();                                     // Inside Constructor.
```

```javascript
class Parent {
    constructor(name, profession, age) {
        console.log("Inside constructor.");

        // 'this' points to the new object being created (i.e myParent)
        this.parentName = name;
        this.parentProfession = profession;
        this.parentAge = age;
    }
}

const myParent = new Parent("Varsha", "Govt Employee", 50);        // Inside constructor

console.log(myParent); 
/*
{
    "parentName": "Varsha",
    "parentProfession": "Govt Employee",
    "parentAge": 50
}
*/

console.log(myParent.parentName)                                  // Varsha
console.log(myParent.parentProfession)                            // Govt Employee
console.log(myParent.parentAge)                                   // 50
```

## Inheritance
- `Inheritance` means one class `(Child)` can automatically get all the properties and methods of another class `(Parent)`.
- It helps us reuse code instead of writing it again and again.

```javascript
class Parent {
    name = "Varsha";
    hobby = "Coding";
    isHumble = true;

    greet() {
        console.log("Hello");
    }
}

class Child extends Parent {};                                    // inheritance

const myChild = new Child();

console.log(myChild.name);                                        // Varsha
console.log(myChild.hobby);                                       // Coding
console.log(myChild.isHumble);                                    // true

myChild.greet();                                                  // Hello
```