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

## Method Overriding (✅ Available in JavaScript)
- **Method overriding** occurs when a child class provides its own version of a method that already exists in its parent class — using the `same method name` and compatible parameters.

```javascript
class Parent {
    earnMoney() {
        console.log("Work Hard");
    }
}

class Child extends Parent {
    earnMoney() {
        console.log("Work Smart");
    }
}

const p1 = new Parent();
p1.earnMoney();                                                 // Work Hard

const c1 = new Child();
c1.earnMoney();                                                 // Work Smart


/*
Explanation:
- Child class overrides the Parent's earnMoney() method.
- Now, Parent and child have independent behavior.
*/
```

```javascript
class Parent {
    earnMoney() {
        console.log("Work Hard");
    }
}

class Child extends Parent {
    earnMoney() {
        super.earnMoney();                                     
        console.log("Work Smart");                            
    } 
}

const p1 = new Parent();
p1.earnMoney();                                                 // Work Hard

const c1 = new Child();
c1.earnMoney();                                                // Work Hard   Work Smart


/*
Explanation:
- super.earnMoney() invokes the parent version.
- Child extends behavior instead of replacing it completely.
*/
```

## Method Overloading (❌ Not supported in JavaScript)
- `Function overloading` means you can define multiple functions with the same name but with different numbers or types of parameters, **and the correct one will be called based on how you invoke it.**
- ❌ **JavaScript** does NOT support `method/function overloading`
- But in JavaScript, if you define multiple methods with the same name, **the last one simply overwrites the previous ones.**

```javascript
class Math {
    add(a, b) {
        return a + b;
    }

    add(a, b, c) {
        return a + b + c;
    }
}

const m1 = new Math();

console.log(m1.add(2, 3));                                    // NaN → calls the second 'add', but c is undefined
console.log(m1.add(2, 3, 5));                                 // 10 → works as expected

/*
Explanation:
- The first add(a, b) gets overwritten by the second add(a, b, c)
- So only the latest method (i.e second add()) exists
- When you pass only 2 arguments, c is undefined → 2 + 3 + undefined = NaN
*/

/*
❌ Why doesn’t JavaScript support this?
- Because JavaScript is an interpreted language — it doesn't do any compile-time type or parameter checking.
- Because Since JavaScript doesn’t check method signatures, any previously defined method with the same name is simply overwritten by the last one.
- Because All function calls are resolved at runtime, not compile-time.
*/
```

## static keyword
- `static` means the **property or method belongs to the class, not the object.**
- You don’t need to create an object (i.e class instance) to use it.
- Just call it using the **class name.**

```javascript
class Config {
    static API_KEY = "1234abcd";
    static AWS_Key = "985858494";
}

console.log(Config.API_KEY);                                   // 1234abcd
console.log(Config.AWS_Key);                                   // 985858494

const c1 = new Config();
console.log(c1.API_KEY);                                       // undefined
console.log(c1.AWS_Key);                                       // undefined

/*
Explanation:
- static properties are attached to the class itself (Config), not its instances.
- c1 is an object of Config, so it doesn't have direct access to static members.
*/
```

```javascript
class Validator {
    static isEmail(email) {
        return email.includes("@");
    }
}

Validator.isEmail("sahaj@yopmail.com");                        // ✅ true

/*
Explanation:
- static keyword is Used to group helper methods that Don’t need an object instance and are directly accessible via class name
- You don't need to create an object of Validator to use isEmail().
*/
```

```javascript
class User {
    static userCount = 0;

    constructor(name) {
        this.userName = name;
        User.userCount++;
    }
}

const user1 = new User("Sahaj");
const user2 = new User("Mitali");
const user3 = new User("John");

console.log(User.userCount);                                   // 3

/*
Why this is good:
- userCount belongs to the class, not individual users
- Useful in real-world cases like tracking how many objects were created
*/
```

```javascript
class Bank {
    static bankName = "BOI";                                 
    #balance = 100;                                           

    checkbalance() {
        return this.#balance;                                
    }

    static getBankName() {
        return Bank.bankName;                                
    }
}

const b1 = new Bank();

console.log(b1.checkbalance());                              // ✅ 100 
console.log(Bank.bankName);                                  // ✅ BOI 
console.log(Bank.getBankName());                             // ✅ BOI 
 
/*
Explanation:
- I hope now the dots are connecting :)
*/
```

## Abstraction
- **Abstraction** means `hiding the internal implementation details` and showing only the essential parts to the user.
- It focuses on `what` an object does rather than `how` it does it.

```javascript
class Car {
    checkEngine() {
        return  "Checked & working Fine";
    }

    checkFuel() {
        return "Checked & Tank is Full";
    }

    checkTyrePressure() {
        return "Checked & Enough Pressure";
    }

    checkAirConditioning() {
        return "Checked & working Fine";
    }

    checkMusicSystem() {
        return 'Checked & working Fine';
    }

    StartTheCar() {
        this.checkEngine();
        this.checkFuel();
        this.checkTyrePressure();
        this.checkAirConditioning();
        this.checkMusicSystem();
        return "Starting the car..."
    }
}

const myCar = new Car();
console.log(myCar.StartTheCar());                            // Starting the car...

/*
Explanation:
- StartTheCar() is an abstracted method that hides all the complex internal checks.
- The user doesn't need to call each individual check — they just use one method.
- This is abstraction: showing only the necessary detail (StartTheCar) and hiding how it's done internally.
- In a way, we are encapsulating other functions inside the abstracted function.
*/
```

```javascript
class Smartphone {
    #loadBIOS() {
        console.log("BIOS loaded");
    }

    #loadKernel() {
        console.log("Kernel booted");
    }

    #loadOS() {
        console.log("Operating System started");
    }

    powerOn() {
        this.#loadBIOS();
        this.#loadKernel();
        this.#loadOS();
        return "Phone is now ON";
    }
}

const phone = new Smartphone();
console.log(phone.powerOn());     
/*
BIOS loaded
Kernel booted
Operating System started
Phone is now ON
*/

phone.#loadOS();                                            // ❌ Error: Private field '#loadOS' must be declared in an enclosing class


/*
Why This Works:
- As a user, you don't need (or want) to run BIOS or kernel yourself.
- You just hit powerOn(), and the complex steps are abstracted inside.
- This is true abstraction — hiding the parts you shouldn’t (or can’t) control.
*/
```

## Polymorphism
- **Polymorphism** means `many forms` — the same method name behaves differently based on the object that calls it.

```javascript
/*
Ad-hoc Polymorphism (❌ Not True OOP Polymorphism)
*/

const Honda = {
    start() {
        console.log("Honda is Starting");
    }
}

const Ford = {
    start() {
        console.log("Ford is Starting");
    }
}

const Toyota = {
    start() {
        console.log("Toyota is Starting");
    }
}

// Polymorphic Function
function startTheCar(car) {
    car.start();
}

startTheCar(Honda);                                          // Honda is Starting
startTheCar(Ford);                                           // Ford is Starting
startTheCar(Toyota);                                         // Toyota is Starting
```

```javascript
/*
❌ Neither Method Overriding nor Polymorphism
*/

class Dog {
  makeSound() {
    return "Woof!";
  }
}

class Robot {
  makeSound() {
    return "Beep boop!";
  }
}


const dog = new Dog();
const robot = new Robot();

console.log(dog.makeSound());                                // Woof!
console.log(robot.makeSound());                              // Beep boop!
```

```javascript
/*
True OOP Polymorphism (✅Inheritance + ✅Overriding)
*/

class Animal {
    makeSound() {
        console.log("Animal Making Sound");
    }
}

class Dog extends Animal {
    makeSound() {
        console.log("Woof");
    }
}

class Cat extends Animal {
    makeSound() {
        console.log("Meow");
    }
}

const myAnimal = new Animal();
const myDog = new Dog();
const myCat = new Cat();

myAnimal.makeSound();                                     // Animal Making Sound
myDog.makeSound();                                        // Woof
myCat.makeSound();                                        // Meow
```