# for loop
```javascript
let myStr = "sahaj";
for (let i = 0; i < myStr.length; i++) {
  console.log(myStr[i]);
}
```

```javascript
let myStr = "sahaj";
let resultStr = [];
for (let i = 0; i < myStr.length; i++) {
  resultStr.push(myStr[i]);
}
console.log(resultStr);                  //[ 's', 'a', 'h', 'a', 'j' ]
console.log(resultStr.join(""));         //sahaj
```

# for of loop
```javascript
let myStr = "HELLO";

for (let char of myStr) {
  console.log(char);
}
```

```javascript
let myStr = "sahaj";
let resultStr = [];

for (let char of myStr) {
  resultStr.push(char);
}

console.log(resultStr);                   //[ 's', 'a', 'h', 'a', 'j' ]
console.log(resultStr.join(""));          //sahaj
```

# forEach() loop
```javascript
let myStr = "sahaj";
myStr.split("").forEach((char) => {
  console.log(char);
});
```

```javascript
let myStr = "sahaj";
Array.from(myStr).forEach((char) => {
  console.log(char);
});
```

# map()
```javascript
let myStr = "sahaj";

let myStrArray = Array.from(myStr).map((char) => {
  return char;
});

console.log(myStrArray);                    //[ 's', 'a', 'h', 'a', 'j' ]
console.log(myStrArray.join(""));           //sahaj
```

# spread operator
```javascript
let myStr = "sahaj";

[...myStr].forEach((char) => {
  console.log(char);
});
```

```javascript
let myStr = "sahaj";

let result = [...myStr].map((char) => {
  return char;
});

console.log(result);                        //[ 's', 'a', 'h', 'a', 'j' ]
console.log(result.join(""));               //sahaj
```

# for in loop
```javascript
let myStr = "sahaj";

for (let char in myStr) {
  console.log(char, myStr[char]);
}

/*
0 s
1 a
2 h
3 a
4 j
*/
```

```javascript
let myStr = "sahaj";
let result = [];

for (let char in myStr) {
  result.push(myStr[char]);
}

console.log(result);                          //[ 's', 'a', 'h', 'a', 'j' ]
console.log(result.join(""));                 //sahaj
```

# reduce()
```javascript
let myStr = "sahaj";

let result = Array.from(myStr).reduce((acc, curr) => {
  acc.push(curr);
  return acc;
}, []);

console.log(result);                          //[ 's', 'a', 'h', 'a', 'j' ]
console.log(result.join(""));                 //sahaj
```

```javascript
let myStr = "sahaj";

let result = Array.from(myStr).reduce((acc, curr) => {
  acc = acc + curr;
  return acc;
}, "");

console.log(result);                          //sahaj
console.log(result.split(""));                //[ 's', 'a', 'h', 'a', 'j' ]
```