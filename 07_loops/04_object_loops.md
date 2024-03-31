# for in loop
```javascript
let obj = {
  name: "sahaj",
  age: 21,
  gender: "male",
};

for (let key in obj) {
  console.log(key, obj[key]);
}

/*
name     sahaj
age      21     
gender   male
*/
```

# Object.keys() method
```javascript
let obj = { a: 1, b: 2, c: 3 };

Object.keys(obj).forEach((key) => {
  console.log(key);
});

/*
a
b
c
*/
```

# Object.values() method
```javascript
let obj = { a: 1, b: 2, c: 3 };

Object.values(obj).forEach((value) => {
  console.log(value);
});

/*
1
2
3
*/
```

# Object.entries() method
```javascript
let obj = { a: 1, b: 2, c: 3 };

Object.entries(obj).forEach((pair) => {
  let [key, value] = pair;
  console.log(key, value);
});

/*
a 1
b 2
c 3
*/
```