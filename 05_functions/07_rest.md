# Rest operator basics
- The rest operator `(...)` is commonly used in JS with function parameters and destructuring assignments.
- It allows you to represent an indefinite number of arguments as an `array`.

```javascript
function result(...values) {
  return values;
}

console.log(result("sahaj", "b", true, 20));                  //[ 'sahaj', 'b', true, 20 ]
console.log(result({ myName: "sahaj" }, { age: 21 }));        //[ { myName: 'sahaj' }, { age: 21 } ]
```

```javascript
let myArr = [1, 2, "sahaj", 4, true];

let [element1, element2, myName, ...remaining] = myArr;

console.log(element1);                                        //1
console.log(element2);                                        //2
console.log(myName);                                          //sahaj
console.log(remaining);                                       //[4,true]
```

# Concatenating Strings
```javascript
function concatStr(...strings) {
  return strings.join("-");
}

console.log(concatStr("sahaj", "arora", "developer"));        //sahaj-arora-developer
```

# Concatenating Arrays
```javascript
function concatArr(...arrays) {
  return arrays.flat(Infinity);
}

console.log(concatArr([1, 2], [3, 4], [5, 6]));               //[1,2,3,4,5,6]
```

```javascript
function concatArr(...arrays) {
  return arrays.reduce((acc, curr) => {
    return acc.concat(curr);
  }, []);
}

console.log(concatArr([1, 2], [3, 4], [5, 6]));               //[1,2,3,4,5,6]
```

# Mini shopping cart
```javascript
function sum(...values) {
  return values.reduce((acc, curr) => {
    return acc + curr;
  }, 0);
}

console.log(sum());                                            //0
console.log(sum(100, 200));                                    //300
console.log(sum(100, 200, 300));                               //600
console.log(sum(100, 200, 300, 400));                          //1000
console.log(sum(100, 200, 300, 400, 500));                     //1500
```

# Multiplying All Arguments
```javascript
function multiply(...values) {
  return values.reduce((acc, curr) => {
    return acc * curr;
  }, 1);
}

console.log(multiply());                                       //1
console.log(multiply(2, 5));                                   //10
console.log(multiply(2, 5, 10));                               //100
```

# Adding elements of multiple arrays
```javascript
function addElements(...arrays) {
  let flattenArray = arrays.flat(Infinity);
  return flattenArray.reduce((acc, curr) => {
    return acc + curr;
  }, 0);
}

console.log(addElements([1, 2, 3], [4, 5], [6, 7, 8]));        //36
console.log(addElements());                                    //0
console.log(addElements(["sahaj"], ["arora"]));                //0sahajarora
```

# Finding max & min of given arguments
- Combined implementation of both the operators.

```javascript
function maxNum(...nums) {
  return Math.max(...nums);
}

console.log(maxNum(1, 2, 3));                                  //3
console.log(maxNum(-1, -100, 30, 20));                         //30
console.log(maxNum(34, 43, -20, 100, 300));                    //300
```

```javascript
function minNum(...nums) {
  return Math.min(...nums);
}

console.log(minNum(1, 2, 3));                                  //1
console.log(minNum(-1, -100, 30, 20));                         //-100
console.log(minNum(34, 43, -20, 100, 300));                    //-20
```

# Finding Max & Min of Multiple Arrays arguments
- Combined implementation of both the operators.

```javascript
function maxValue(...arrays) {
  return Math.max(...arrays.flat(Infinity));
}

console.log(maxValue([1, 2, 30], [40, -5, 6], [7, 8, 97]));    //97
```

```javascript
function minValue(...arrays) {
  return Math.min(...arrays.flat(Infinity));
}

console.log(minValue([1, 2, 30], [40, -5, 6], [7, 8, 97]));     //-5
```

```javascript
function maxValue(...arrays) {
  let concatArr = arrays.reduce((acc, curr) => {
    return acc.concat(curr);
  }, []);

  return Math.max(...concatArr);
}
console.log(maxValue([1, 2, 30], [40, -5, 6], [7, 8, 97]));     //97
```

```javascript
function minValue(...arrays) {
  let concatArr = arrays.reduce((acc, curr) => {
    return acc.concat(curr);
  }, []);

  return Math.min(...concatArr);
}

console.log(minValue([1, 2, 30], [40, -5, 6], [7, 8, 97]));     //-5
```