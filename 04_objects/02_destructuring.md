# Basic object destructuring
```javascript
let userInfo = {
  username: "sahaj",
  age: 21,
  gender: "male",
  profession: "developer",
};

let { username, age, gender, profession } = userInfo;

console.log(username);                     //sahaj
console.log(age);                          //21
console.log(gender);                       //male
console.log(profession);                   //developer
```

# Default parameters in object destructuring
```javascript
let info = {
  username: "sahaj",
  userage: 21,
};

let { username: myName = "anonymous", userage: myAge = 100 } = info;

console.log(myName);                        //sahaj
console.log(myAge);                         //21

console.log(info.username);                 //sahaj
console.log(info.userage);                  //21

console.log(username);                      //ReferenceError: username is not defined
console.log(userage);                       //ReferenceError: userage is not defined

console.log(info.myName);                   //undefined
console.log(info.myAge);                    //undefined
```

# Nested Object Destructuring
```javascript
let info = {
  username: "sahaj",
  age: 21,
  location: {
    city: "narela",
    state: "delhi",
    country: "india",
  },
};

let { username, age, location: { city, state, country } } = info;

console.log(username);                       //sahaj
console.log(age);                            //21
console.log(city);                           //narela
console.log(state);                          //delhi
console.log(country);                        //india
```

# rest operator
```javascript
let userInfo = {
  username: "sahaj",
  age: 21,
  gender: "male",
  profession: "developer",
  location: "delhi",
};

let { username, age, ...remaining } = userInfo;

console.log(username);                       //sahaj
console.log(age);                            //21
console.log(remaining);                      //{ gender: 'male', profession: 'developer', location: 'delhi' }

let { gender, profession, location } = remaining;

console.log(gender);                         //male
console.log(profession);                     //developer
console.log(location);                       //delhi
```

# Destructuring Parameters in Functions
```javascript
function userInfo({ username, age }) {
  return `${username} : ${age}`;
}

console.log(userInfo({ username: "sahaj", age: 21 }));            //sahaj : 21
```

# Destructuring with Function's Returning Object
```javascript
function userInfo() {
  return { username: "sahaj", age: 21 };
}

let { username, age } = userInfo();

console.log(username);                       //sahaj
console.log(age);                            //21
```

# Destructuring with Dynamic Property Names
```javascript
let key1 = "fullname";
let key2 = "age";
let key3 = "gender";

let userInfo = {
  fullname: "sahaj arora",
  age: 21,
  gender: "male",
};

let { [key1]: myName, [key2]: myAge, [key3]: myGender } = userInfo;

console.log(myName);                         //sahaj arora
console.log(userInfo[key1]);                 //sahaj arora

console.log(myAge);                          //21
console.log(userInfo[key2]);                 //21

console.log(myGender);                       //male
console.log(userInfo[key3]);                 //male
```