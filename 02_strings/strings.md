# Template Literal

```javascript
let name = "sahaj";
let age = 21;
let result = `Hello ${name}, are you ${age} years old ?`;
console.log(result);
```
Output : `Hello sahaj, are you 21 years old ?`

# Length

```javascript
let name = "sahaj arora";
console.log(name.length);
```
Output : `11`

# ACCESSING CHARACETRS

```javascript
let str = "sahaj arora";
console.log(str[4]);            //j
console.log(str.charAt(4));     //j
```

# Basic String Conversion

```javascript
let str = "My naMe is SAhaj ArorA";

console.log(str.toLowerCase());    //my name is sahaj arora
console.log(str.toUpperCase());    //MY NAME IS SAHAJ ARORA
```

# STRINGS ARE IMMUTABLE

```javascript
let str = "sahaj arora";
str[4] = "P";
console.log(str);
```
Output : `sahaj arora`

# replace()
- replaces only the first instance of that particular character or word.

```javascript
let str = "my name is sahaj arora";
let newStr = str.replace("name", "full name");
console.log(newStr);
```
Output : `my full name is sahaj arora`

# replaceAll()
- replaces all instances of that particular character or word.

```javascript
let str = "smart smartphone small sky";
let newStr = str.replaceAll("s", "S");
console.log(newStr);
```
Output : `Smart Smartphone Small Sky`

# concat()

```javascript
let str1 = "sahaj";
let str2 = "arora";
let age = 21;

let resultStr = str1.concat(" ", str2, " and my age is ", age);
console.log(resultStr);
```
Output : `sahaj arora and my age is 21`

# trim()
- removes the leading as well as the trailing white spaces.

```javascript
let str = "            sahaj arora                 ";
let trimmedStr = str.trim();
console.log(trimmedStr);
```
Output : `sahaj arora`

# SEARCHING CHARACTERS

```javascript
let str = "sahaj arora";

console.log(str.indexOf("sahaj"));     //0
console.log(str.indexOf("j"));         //4
console.log(str.indexOf("a"));         //1
console.log(str.lastIndexOf("a"));     //10
```

# startsWith() & endWith()

```javascript
let str = "name is sahaj arora is my name";
console.log(str.startsWith("name"));    //true
console.log(str.endsWith("name"));      //true
console.log(str.startsWith("n"));       //true
console.log(str.endsWith("e"));         //true
console.log(str.startsWith("N"));       //false
```

# includes()

```javascript
let str = "user validation failed : password is required";

console.log(str.includes("user validation failed"));  //true
console.log(str.includes("sahaj"));                   //false
```

# slice()

```javascript
let str = "Hello, world!";
let slicedStr = str.slice(7, 12);
console.log(slicedStr); 
```
Output : `world`

# split()

```javascript
let str1 = "my name is sahaj arora";
let str2 = "my-name-is-sahaj-arora";
let str3 = "myname_is_sahajarora";
let str4 = "sahaj";

console.log(str1.split(" "));    //[ 'my', 'name', 'is', 'sahaj', 'arora' ]
console.log(str2.split("-"));    //[ 'my', 'name', 'is', 'sahaj', 'arora' ]
console.log(str3.split("_"));    //[ 'myname', 'is', 'sahajarora' ] 
console.log(str4.split(""));     //[ 's', 'a', 'h', 'a', 'j' ]
```

# join()

```javascript
let arr = ["sahaj", "arora"];

console.log(arr.join(" and "));       //sahaj and arora
console.log(arr.join("-"));           //sahaj-arora
console.log(arr.join(""));            //sahajarora
console.log(arr.join(" "));           //sahaj arora
```

# Comparing two strings

```javascript
let str1 = "apple";
let str2 = "mango";
let str3 = "apple";

console.log(str1.localeCompare(str2)); //-1
console.log(str1.localeCompare(str3)); //0
```

# ASCII CODE CHARACTERS

```javascript
let str = "abcde";

console.log(str.charCodeAt(0), String.fromCharCode(97));   //97 a
console.log(str.charCodeAt(1), String.fromCharCode(98));   //98 b
console.log(str.charCodeAt(2), String.fromCharCode(99));   //99 c
console.log(str.charCodeAt(3), String.fromCharCode(100));  //100 d
console.log(str.charCodeAt(4), String.fromCharCode(101));  //101 e
```

# String-Object Conversion

```javascript
let obj = {
  name: "sahaj",
  age: 21,
};

//wrong way
console.log(String(obj));

//converting obj into string
let strObj = JSON.stringify(obj);
console.log(strObj);                       //{"name":"sahaj","age":21}

//converting string back to obj
let originalObj = JSON.parse(strObj);
console.log(originalObj);                  //{ name: 'sahaj', age: 21 }
```