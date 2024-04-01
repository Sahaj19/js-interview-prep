# Undefined
- JS allocates memory to variables and functions before executing any code.
- Even before a line of code is run, memory space is reserved for variables.
- The value of variable that hasn't been assigned is `undefined`.
- `undefined` acts as a placeholder or default value in memory until a variable is assigned.

```javascript
let a;
if(a === undefined) {
    console.log("a is undefined");
}else {
    console.log("a has some value in it!");
}
```
Output : `a is undefined`

- <strong>Undefined</strong> is not equivalent to empty or null, undefined means that memory has been allocated to a variable but no value has been assigned yet.
- `Undefined` is a special keyword in JS, that takes up its own space.

# Important Note
- `not defined` refers to a variable that has not been declared or allocated any memory.

```javascript
console.log(x);
```
Output : `Reference Error : x is not defined.`