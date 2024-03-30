# Accessing elements
```javascript
let arr = ["apple", "mango", "banana", { name: "sahaj", age: 21 }];

console.log(arr[0]);               //apple
console.log(arr[1]);               //mango
console.log(arr[2]);               //banana
console.log(arr[3]);               //{ name : "sahaj" , age : 21 }
console.log(arr[3].name);          //sahaj
console.log(arr[3].age);           //21
```

# indexOf()
- It searches the array from the beginning to the end.
- Returns the index or -1 if the element is not present.

```javascript
let arr = ["sahaj", 30, "arora", 100, "saloni", "arora"];

console.log(arr.indexOf("arora"));               //2
console.log(arr.indexOf("javascript"));          //-1
```

# lastIndexOf()
- It searches the array from the end to the beginning.
- Returns the index or -1 if the element is not present.

```javascript
let arr = ["sahaj", 30, "arora", 100, "saloni", "arora"];

console.log(arr.lastIndexOf("arora"));           //5
console.log(arr.lastIndexOf("javascript"));      //-1
```

# length
```javascript
let arr = [1, "sahaj", true, null, undefined];
console.log(arr.length);
```
Output : `5`

# join()
```javascript
let arr = ["sahaj", "arora"];

console.log(arr.join(" and "));       //sahaj and arora
console.log(arr.join("-"));           //sahaj-arora
console.log(arr.join(""));            //sahajarora
console.log(arr.join(" "));           //sahaj arora
```

# push(), pop(), shift(), unshift()
- These methods modifies the original array.

```javascript
let original_arr = ["sahaj", "arora", "developer"];
```

```javascript
let push_result = original_arr.push("engineer");

console.log("Original Array : ", original_arr);
//Original Array :  [ 'sahaj', 'arora', 'developer', 'engineer' ]

console.log("push() method return the length : ", push_result);
//push() methods return the length :  4
```

```javascript
let pop_result = original_arr.pop();

console.log("Returns the popped out element : ", pop_result);
//Returns the popped out element :  developer

console.log("Original Array : ", original_arr);
//Original Array :  [ 'sahaj', 'arora' ]
```
 
```javascript
let unshift_result = original_arr.unshift("engineer");

console.log("unshift() method return the length : ", unshift_result);
//unshift() methods return the length :  4

console.log("Original Array : ", original_arr);
//Original Array :  [ 'engineer', 'sahaj', 'arora', 'developer' ]
```

```javascript
let shift_result = original_arr.shift();

console.log("Returns the popped out element : ", shift_result);
//Returns the popped out element :  sahaj

console.log("Original Array : ", original_arr);
//Original Array :  [ 'arora', 'developer' ]
```

# toString()
- Doesn't modify the original array, it just returns a string representation of it.

```javascript
let myArr = ["sahaj", 2000, "saloni"];

let myStr = myArr.toString();
console.log("Required strings : ", myStr);         //Required strings :  sahaj,2000,saloni
console.log("Original array : ", myArr);           //Original array :  [ 'sahaj', 2000, 'saloni' ]
```
 
# flat()
- Pass Infinity as the depth argument.

```javascript
let original_arr = [1, 2, [3, 4, 5], 6, 7, [8, 9, [10, 11]]];

console.log("Original Array : ", original_arr);
//[ 1, 2, [ 3, 4, 5 ], 6, 7, [ 8, 9, [ 10, 11 ] ] ]

let flatten_arr = original_arr.flat(Infinity);
console.log(flatten_arr);
//[1,2,3,4,5,6,7,8,9,10,11]
```

# includes()
```javascript
let arr = ["sahaj", 23, true, "password"];

console.log(arr.includes("sahaj"));        //true
console.log(arr.includes("Sahaj"));        //false
console.log(arr.includes(23));             //true
console.log(arr.includes("password"));     //true
console.log(arr.includes(true));           //true
```

# concat()
```javascript
let arr1 = [1, 2];
let arr2 = ["sahaj", true];
let arr3 = [null, undefined];

let result = arr1.concat(arr2, arr3);
console.log(result);
```
Output : `[ 1, 2, 'sahaj', true, null, undefined ]`

# fill()
- It modifies the original array.

```javascript
let arr = ["sahaj", "apple", "orange", "mango"];

console.log(arr.fill(5));
//[ 5, 5, 5, 5 ]

console.log(arr.fill("sahaj"));
//[ 'sahaj', 'sahaj', 'sahaj', 'sahaj' ]

console.log(arr.fill("orange", 2));
//will start filling from 2nd index
//[ 'sahaj', 'apple', 'orange', 'orange' ]

console.log(arr.fill("kiwi", 1, 3));
//[ 'sahaj', 'kiwi', 'kiwi', 'mango' ]
```

# reverse()
- It modifies the original array.

```javascript
let original_arr = [1, 2, 3, 4, 5];
original_arr.reverse();

console.log("Original Array : ", original_arr);
```
Output : `Original Array :  [ 5, 4, 3, 2, 1 ]`

# spread operator
```javascript
let value1 = ["sahaj", 21];
let value2 = [true, false];

let result = [...value1, ...value2];
console.log(result);
```
Output : `[ 'sahaj', 21, true, false ]`

# slice()
- Returns the sliced part from the array.

```javascript
let originalArr = [2, 4, 6, 8, 9, 10];

let slicedArr1 = originalArr.slice(1, 5);
let slicedArr2 = originalArr.slice(-1);
let slicedArr3 = originalArr.slice(-3);
let slicedArr4 = originalArr.slice();

console.log("Sliced Array 1 : ", slicedArr1);
//Sliced Array 1 :  [ 4, 6, 8, 9 ]

console.log("Sliced Array 2 : ", slicedArr2);
//Sliced Array 2 :  [ 10 ]

console.log("Sliced Array 3 : ", slicedArr3);
//Sliced Array 3 :  [ 8, 9, 10 ]

console.log("Sliced Array 4 : ", slicedArr4);
//Sliced Array 4 :  [ 2, 4, 6, 8, 9, 10 ]

console.log("Original Array : ", originalArr);
//Original Array :  [ 2, 4, 6, 8, 9, 10 ]
```

# splice()
- It modifies the original array.

```javascript
let arr = [1, 2, "sahaj", 4, 5];
```

```javascript
let removedArr = arr.splice(1);
console.log("Removed array : ", removedArr);          //Removed array :  [ 2, 'sahaj', 4, 5 ]
console.log("Original array : ", arr);                //Original array :  [ 1 ]
```

```javascript
let removedArr = arr.splice(2);
console.log("Removed array : ", removedArr);          //Removed array :  [ 'sahaj', 4, 5 ]
console.log("Original array : ", arr);                //Original array :  [ 1, 2 ]
```

```javascript
let removedArr = arr.splice(-1);
console.log("Removed array : ", removedArr);          //Removed array :  [ 5 ]
console.log("Original array : ", arr);                //Original array :  [ 1, 2, 'sahaj', 4 ]
```

```javascript
let removedArr = arr.splice(-2);
console.log("Removed array : ", removedArr);          //Removed array :  [ 4, 5 ]
console.log("Original array : ", arr);                //Original array :  [ 1, 2, 'sahaj' ]
```

```javascript
let removedArr = arr.splice(0, 2);
console.log("Removed array : ", removedArr);          //Removed array :  [ 1, 2 ]
console.log("Original array : ", arr);                //Original array :  [ 'sahaj', 4, 5 ]
```

```javascript
let removedArr = arr.splice(1, 3, "saloni", "varsha");
console.log("Removed array : ", removedArr);         //Removed array :  [ 2, 'sahaj', 4 ]
console.log("Original array : ", arr);               //Original array :  [ 1, 'saloni', 'varsha', 5 ]
```

```javascript
let removedArr = arr.splice(2, 2, "nodejs");
console.log("Removed array : ", removedArr);         //Removed array :  [ 'sahaj', 4 ]
console.log("Original array : ", arr);               //Original array :  [ 1, 2, 'nodejs', 5 ]
```

# Array.isArray()

```javascript
let myName = "sahaj";
console.log(Array.isArray(myName));
```
Output : `false`

```javascript
let arr = [1, 2, 3];
console.log(Array.isArray(arr));
```
Output : `true`

# Array.from()

```javascript
let myName = "sahaj";
console.log(Array.from(myName));
```
Output : `[ 's', 'a', 'h', 'a', 'j' ]`

```javascript
let obj = {
  myName: "sahaj",
  age: 21,
  gender: "male",
};

//here it will return an empty array.
console.log(Array.from(obj));
//[]

let obj_array1 = Array.from(Object.keys(obj));
console.log(obj_array1);
//[ 'myName', 'age', 'gender' ]

let obj_array2 = Array.from(Object.values(obj));
console.log(obj_array2);
//[ 'sahaj', 21, 'male' ] 
```

# Array.of()

```javascript
let value1 = 100;
let value2 = true;
let value3 = "sahaj";

let result = Array.of(value1, value2, value3);
console.log(result);
```
Output : `[ 100, true, 'sahaj' ]`