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
- `Inheritance` means one class `(Child)` (i.e subclass) can automatically get all the properties and methods of another class `(Parent)` (i.e parentclass).
- It helps us reuse code instead of writing it again and again.

```javascript
class Parent {
    name = "Varsha";
    hobby = "Coding";
    money = 100;
    isHumble = true;

    greet(somename) {
        console.log(`Hello ${somename}`);
    }

    spendMoney() {
        return this.money;
    }
}

class Child extends Parent {};                                    // inheritance

const myChild = new Child();

console.log(myChild.name);                                        // Varsha
console.log(myChild.hobby);                                       // Coding
console.log(myChild.isHumble);                                    // true

console.log(myChild.spendMoney());                                // 100
myChild.greet("Sahaj");                                           // Hello Sahaj
```

```javascript
class Parent {
    constructor() {
        console.log("Parent Constructor");
    }
}

class Child extends Parent{};

const sahaj = new Child();                                        // Parent Constructor
const varsha = new Parent();                                      // Parent Constructor

/*
Explanation:
- Parent class has a constructor that logs "Parent Constructor".
- Child class extends `Parent`, so it inherits the constructor unless it defines its own.
- When new Child() is called, it internally calls the `Parent` constructor due to inheritance.
- So both new Child() and new Parent() trigger the same constructor, hence "Parent Constructor" is logged twice.
*/
```

## super keyword
- `super` is a keyword used only and only in child class to access the `constructor or methods of the parent class`.
- It must be called with `super()` inside the child constructor `before` calling any method, console.log, or using this keyword.
- `super` keyword cannot be used in base classes (i.e Parent class) or outside class contexts.

```javascript
class Parent {
    constructor() {
        console.log("Parent Constructor");
    }
}

class Child extends Parent {
    constructor() {
        super();                                    // ✅ Must be called first in the child constructor
        console.log("Child Constructor");  
    }
}

const Varsha = new Parent();                       // Parent Constructor
const sahaj = new Child();                         // Parent Constructor    Child Constructor

/*
Explanation:
- super() is used to call the Parent class's constructor and initialize the inherited properties.
- If we don't use super() inside the child's constructor, we will face issues.

class Child extends Parent {
    constructor() {
        console.log("Child Constructor");  
    }
}

❌ Reference Error: Must call super constructor in derived class before accessing 'this' or returning from derived constructor

Summary:
✅ Always remember: In child class constructors, super() comes before anything else — even console.log() or this.
*/
```

```javascript
class Parent {
    food = "Rajma Chawal";                             // class field
    hobby = "Walking";                                 // class field

    constructor(name,age) {
        this.myName = name;                            //✅ Dynamic via constructor
        this.myAge = age;                              //✅ Dynamic via constructor
    }

    parentDetails() {
        console.log(this.food);
        console.log(this.hobby);
    }
}

//++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

class Child extends Parent {
    constructor(profession) {
        super("Nobita", 23);                            //✅ using super() to call Parent constructor first
        this.myProfession = profession;                 //✅ adding Child-specific dynamic property
    } 

    //✅ super keyword can also be used to call parent methods from child class
    childDetails() {
        super.parentDetails();                          //✅ Calls Parent's method using super.method()
    }
}

//++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

const sahaj = new Child("Frontend Engineer");
console.log(sahaj);
/*
Here:
- food and hobby are static values defined as class fields.
- myName, myAge, and myProfession are dynamic and set through the constructor. 

{
    "food": "Rajma Chawal",
    "hobby": "Walking",
    "myName": "Nobita",
    "myAge": 23,
    "myProfession": "Frontend Engineer"
}
*/

console.log(sahaj.myName);                                      // Nobita
console.log(sahaj.myAge);                                       // 23
console.log(sahaj.myProfession);                                // Frontend Engineer

sahaj.childDetails();
/*
Rajma Chawal
Walking
*/

//✅ Class fields can still be updated later
sahaj.food = "Burger";
sahaj.hobby = "Coding";
sahaj.childDetails();
/*
Burger
Coding
*/


/*
Explanation:
The super keyword in JavaScript has two main use cases:

1️⃣ It is Used inside the child constructor to call the parent class constructor (Must be the first statement). 
2️⃣ It Used to call a method from the parent class inside a child class method.
*/
```

## Encapsulation
- `Grouping` related variables and methods together into a single unit (like an object or class)
- Encapsulation in OOP means bundling both **data (properties)** and **behavior (methods)** inside a class.

```javascript
// ❌ Non-encapsulated variables
const myName = "Sahaj";
const myProfession = "Front End Engineer";
const myAge = 23;

// ✅ Encapsulated into an object
const myDetails = {
    myName: "Sahaj",
    myProfession: "Front End Engineer",
    myAge: 23
};
```

```javascript
class User {
    myName = "Sahaj";
    myAge = 23;

    getMyAge() {
        return this.myAge;
    }

    getMyName() {
        return this.myName;
    }
}
```

## Access Modifiers
- By default, all class properties and methods in JavaScript are **public**. `That means:` they can be accessed from outside the class using an object.
- If you want to make something **private** (only accessible inside the class), you use a `#` before the variable or method name.

```javascript
class Superhero {
    #power = "running";                                           // 🔐 Private field

    #greeting() {                                                 // 🔐 Private method
        return "Hello";
    }

    getPower() {                                                 // ✅ Public method — can access private stuff internally
        return this.#power;
    }

    revealGreeting() {                                           // ✅ Public method — can access private stuff internally
        return this.#greeting();
    }
}

const hero = new Superhero();

// ✅ Public access (works)
console.log(hero.getPower());                                    // running
console.log(hero.revealGreeting());                              // Hello

// ❌ Direct access to private properties/methods (fails)
console.log(hero.power);                                         // undefined
console.log(hero.#power);                                        // ❌ Private field '#power' must be declared in an enclosing class
console.log(hero.#greeting());                                   // ❌ Private field '#greeting' must be declared in an enclosing class
```