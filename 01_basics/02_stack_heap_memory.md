# Stack Memory
- Primitive datatypes are stored in stack memory.
- They are passed by value, meaning only a copy is passed, not the original reference.

```javascript
let str1 = "frontend";
let str2 = str1;

str2 = "backend";

console.log(str2);                         // Output: backend
console.log(str1);                         // Output: frontend
```

# Heap Memory
- Non-primitive datatypes are stored in heap memory.
- They are passed by reference, meaning the original reference is directly accessed.

```javascript
let userInfo = {
  name: "sahaj",
  age: 30,
};

let updatedUserInfo = userInfo;

updatedUserInfo.age = 21;

console.log(userInfo);                    // Output: { name: 'sahaj', age: 21 }
console.log(updatedUserInfo);             // Output: { name: 'sahaj', age: 21 }
```