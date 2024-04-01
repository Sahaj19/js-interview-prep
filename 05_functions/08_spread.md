# Spread operator
- It allows expanding an iterable (like an array, string or an object) into individual elements.

```javascript
let myStr = "sahaj";

let resultArr2 = [...myStr];
console.log(resultArr2);                        //[ 's', 'a', 'h', 'a', 'j' ]

let resultArr1 = { ...myStr };
console.log(resultArr1);                        //{ '0': 's', '1': 'a', '2': 'h', '3': 'a', '4': 'j' }
```

## Merging Arrays
```javascript
let myArr1 = [1, 2];
let myArr2 = [3, 4];
let myArr3 = [5, 6];
let resultArr = [...myArr1, ...myArr2, ...myArr3];
console.log(resultArr);                                        //[1,2,3,4,5,6]
```

## Merging Objects
```javascript
let myObj1 = { name: "sahaj" };
let myObj2 = { age: 21 };
let myObj3 = { gender: "male" };
let resultObj = { ...myObj1, ...myObj2, ...myObj3 };
console.log(resultObj);                                        //{ name: 'sahaj', age: 21, gender: 'male' }
```

## Passing Array Elements as Function Arguments
```javascript
function sum(a, b, c) {
  return a + b + c;
}

console.log(sum(1, 2, 3));                                     //6
console.log(sum(...[1, 2, 3]));                                //6
```

## Creating a Copy of an Object with Additional Items
```javascript
let info = {
  username: "sahaj",
  age: 21,
  gender: "male",
};

let resume = { ...info, profession: "developer" };

console.log(info);                                     
//{ username: 'sahaj', age: 21, gender: 'male' }

console.log(resume);               
//{ username: 'sahaj', age: 21, gender: 'male', profession: 'developer' }
```