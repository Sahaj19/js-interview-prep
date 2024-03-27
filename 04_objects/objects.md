# Basics

```javascript
let userInfo = {
  myName: "sahaj",
  age: 21,
};
```

### Accessing Values

```javascript
console.log(userInfo.myName);          //sahaj
console.log(userInfo["myName"]);       //sahaj
console.log(userInfo.age);             //21
console.log(userInfo["age"]);          //21
```

### Accessing keys,values,entries

```javascript
//Return an array of keys
console.log(Object.keys(userInfo));         // [ 'myName', 'age' ]

//Return an array of values
console.log(Object.values(userInfo));       // [ 'sahaj', 21 ]

//Return an array of entries
console.log(Object.entries(userInfo));      // [ [ 'myName', 'sahaj' ], [ 'age', 21 ] ]
```

### Checking if a key exists in the object

```javascript
console.log(userInfo.hasOwnProperty("myName"));       //true
console.log(userInfo.hasOwnProperty("age"));          //true
console.log(userInfo.hasOwnProperty("gender"));       //false
```

```javascript
console.log("myName" in userInfo);                    //true
console.log("age" in userInfo);                       //true
console.log("gender" in userInfo);                    //false
```

### CRUD

```javascript
//updating property
userInfo.myName = "sahaj arora";

//deleting property
delete userInfo.age;

//adding property
userInfo.gender = "male";
```
Output : `{ myName: 'sahaj arora', gender: 'male' }`

# Object.freeze()
- makes an object completely immutable (both properties and values).

```javascript
let userInfo = {
  myName: "sahaj",
  age: 21,
  gender: "male",
};

Object.freeze(userInfo);
console.log(Object.isFrozen(userInfo));  //true

userInfo.myName = "sahaj arora";
delete userInfo.gender;
userInfo.age = 25;


console.log(userInfo);
```
Output : `{ myName: 'sahaj', age: 21, gender: 'male' }`

# Object.seal()
- Allows changes to the values of existing properties but prevents adding or removing properties.

```javascript
let userInfo = {
  myName: "sahaj",
  age: 21,
  gender: "male",
};

Object.seal(userInfo);
console.log(Object.isSealed(userInfo));   //true

//Possible operations
userInfo.myName = "saloni arora";
userInfo.age = 25;
userInfo.gender = "female";

//Impossible operations
delete userInfo.age;
userInfo.hobby = "coding";

console.log(userInfo);
```
Output : `{ myName: 'saloni arora', age: 25, gender: 'female' }`

# Merging Objects

```javascript
let obj1 = { name: "sahaj" };
let obj2 = { age: 21 };
let obj3 = { gender: "male" };

let result1 = Object.assign({}, obj1, obj2, obj3);
console.log(result1);

let result2 = { ...obj1, ...obj2, ...obj3 };
console.log(result2);
```
Output : `{ name: 'sahaj', age: 21, gender: 'male' }`

# Call by reference
- obj1 and obj2 both reference the same object. Modifying obj2 also modifies obj1 because they share the same reference to the object.

```javascript
let obj1 = {
  myName: "sahaj",
  age: 21,
};

let obj2 = obj1;

obj2.myName = "saloni arora";
obj2.age = 20;

console.log(obj2);
console.log(obj1);
```
Output : `{ myName: 'saloni arora', age: 20 }`

# Shallow Copy

```javascript
let obj1 = {
  myName: "sahaj",
  age: 21,
  gender: "male",
};

let obj2 = obj1;

console.log(obj1 === obj2);           //true
console.log(Object.is(obj1, obj2));   //true

obj2.myName = "sammy";
obj2.age = 25;
obj2.gender = "female";

console.log(obj1);             //{ myName: 'sammy', age: 25, gender: 'female' }
console.log(obj2);             //{ myName: 'sammy', age: 25, gender: 'female' }
```

# Deep Copy

```javascript
let obj1 = {
  myName: "sahaj",
  age: 21,
  gender: "male",
};

let obj2 = Object.assign({}, obj1);

console.log(obj1 === obj2);         //false
console.log(Object.is(obj1, obj2)); //false

obj2.myName = "varsha";
obj2.age = 40;
obj2.gender = "female";

console.log(obj2);         //{ myName: 'varsha', age: 40, gender: 'female' }
console.log(obj1);         //{ myName: 'sahaj', age: 21, gender: 'male' }  
```

# Dynamic Property

```javascript
let key = "name";

let obj = {
  [key]: "sahaj arora",
};

console.log(obj.name);
console.log(obj[key]);
console.log(Object.values(obj)[0]);
```
Output : `sahaj arora`

# Computed Property

```javascript
let key = "full";

let obj = {
  [key + "name"]: "sahaj arora",
};

console.log(obj["fullname"]);
```
Output : `sahaj arora`

