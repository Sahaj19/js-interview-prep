# Let's first understand the problem
- `obj2` references the same object as `obj1`, not a new independent copy.
- Any modifications made to obj2 will directly affect obj1, and vice versa.
- Both obj1 and obj2 reference the same object in memory after the assignment `obj2 = obj1`.
- Modifying obj2 also modifies obj1, as they point to the same object.

```javascript
let obj1 = {
  username: "sahaj",
  age: 21,
};

//assigning obj1 properties and methods to obj2
let obj2 = obj1;

//updating obj2
obj2.username = "sammy";
obj2.age = 100;

console.log(obj1);                                     //{ username: 'sammy', age: 100 }
console.log(obj2);                                     //{ username: 'sammy', age: 100 }
console.log(obj1 === obj2);                            //true
console.log(Object.is(obj1, obj2));                    //true
```

- And same goes for `arrays` as well.
```javascript
let arr1 = [1, 2, 3, 4, 5];

let arr2 = arr1;

arr2[1] = "sahaj";
arr2[3] = true;

console.log(arr1);                                     //[ 1, 'sahaj', 3, true, 5 ]
console.log(arr2);                                     //[ 1, 'sahaj', 3, true, 5 ]
console.log(arr1 === arr2);                            //true
console.log(Object.is(arr1, arr2));                    //true
```

# Shallow Copying Objects

#### Using `Object.assign()`
```javascript
let obj1 = {
  username: "sahaj",
  age: 21,
};

let obj2 = Object.assign({}, obj1);

obj2.username = "sammy";
obj2.age = 100;

console.log(obj2);                                     //{ username: 'sammy', age: 100 }
console.log(obj1);                                     //{ username: 'sahaj', age: 21 }
console.log(obj1 === obj2);                            //false
console.log(Object.is(obj1, obj2));                    //false
```

#### Using `spread operator ...`
```javascript
let obj1 = {
  username: "sahaj",
  age: 21,
};

let obj2 = { ...obj1 };

obj2.username = "sammy";
obj2.age = 100;

console.log(obj2);                                     //{ username: 'sammy', age: 100 }
console.log(obj1);                                     //{ username: 'sahaj', age: 21 }
console.log(obj1 === obj2);                            //false
console.log(Object.is(obj1, obj2));                    //false
```

# Shallow Copying Arrays

#### Using `Object.assign()`
```javascript
let arr1 = [1, 2, 3, 4, 5];
let arr2 = Object.assign([], arr1);

arr2[0] = "sahaj";
arr2[4] = "arora";

console.log(arr1);                                     //[1,2,3,4,5]
console.log(arr2);                                     //[ 'sahaj', 2, 3, 4, 'arora' ]
console.log(arr1 === arr2);                            //false
console.log(Object.is(arr1, arr2));                    //false
```

#### Using `spread operator ...`
```javascript
let arr1 = [1, 2, 3, 4, 5];
let arr2 = [...arr1];

arr2[0] = "sahaj";
arr2[4] = "arora";

console.log(arr1);                                     //[1,2,3,4,5]
console.log(arr2);                                     //[ 'sahaj', 2, 3, 4, 'arora' ]
console.log(arr1 === arr2);                            //false
console.log(Object.is(arr1, arr2));                    //false
```

#### Using `concat()`
```javascript
let arr1 = [1, 2, 3, 4, 5];

let arr2 = [].concat(arr1);

arr2[0] = "sahaj";
arr2[4] = "arora";

console.log(arr1);                                     //[1,2,3,4,5]
console.log(arr2);                                     //[ 'sahaj', 2, 3, 4, 'arora' ]
console.log(arr1 === arr2);                            //false
console.log(Object.is(arr1, arr2));                    //false
```

#### Using `slice()`
```javascript
let arr1 = [1, 2, 3, 4, 5];

let arr2 = arr1.slice();

arr2[0] = "sahaj";
arr2[4] = "arora";

console.log(arr1);                                     //[1,2,3,4,5]
console.log(arr2);                                     //[ 'sahaj', 2, 3, 4, 'arora' ]
console.log(arr1 === arr2);                            //false
console.log(Object.is(arr1, arr2));                    //false
```