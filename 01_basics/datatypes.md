# Primitive datatypes
- number
- boolean
- string
- null
- undefined
- symbol
- bigint

# Non-Primitive datatypes
- Array
- Object
- Function

# Undefined
- JS allocates memory to variables and functions before executing any code.
- Even before a line of code is run, memory space is reserved for variables.
- The value of variable that hasn't been assigned yet is `undefined`.
- Undefined acts as a placeholder or default value in memory until a variable is assigned.

```javascript
    let a;
    if(a === undefined) {
        console.log("a is undefined");
    }else {
        console.log("a has some value in it!");
    }
```

```javascript
    //false
    console.log(Boolean(undefined)); 
```

# Null
- null is a standalone value, representing an empty value or the absence of a meaningful value.
```javascript
    //false
    console.log(Boolean(null)); 
```

- Comparisons convert null to a number, treating as a zero.
```javascript
    //false
    console.log(null == 0); 
    console.log(null > 0); 
    console.log(null < 0);

    //true
    console.log(null >= 0);
    console.log(null <= 0);
```

# Important Notes
- `NaN` (Not a Number) is not a distinct data type in JS. Instead, it is a special value of the number data type. When a mathematical operation cannot produce a meaningful result, NaN is returned. 

```javascript
    //falsy values
    console.log(Boolean(null));
    console.log(Boolean(undefined));
    console.log(Boolean(""));
    console.log(Boolean(0));
    console.log(Boolean(-0));
    console.log(Boolean(0n));
    console.log(Boolean(NaN));
```



