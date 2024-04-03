# Basics of let, const & var
- `var` allows both redeclaration and reinitialization.

```javascript
var a = 5;
a = "sahaj";                            // Reinitialization allowed
var a = 20;                             // Redeclaration allowed

console.log(a);                         // 20
```

- `let` allows reinitialization but not redeclaration.

```javascript
let b = "sahaj";
b = 20;                                 // Reinitialization allowed
let b = 35;                             // Error: Identifier 'b' has already been declared
```

- `const` does not allow either redeclaration or reinitialization.

```javascript

const c = 30;
c = "sahaj";                            // Error: Assignment to constant variable
const c = 20;                           // Error: Identifier 'c' has already been declared
```

# Global Object Property
- `var` declarations create properties on the global object (`window` in browsers).
- The global object can be accessed using the `window` keyword or `this` keyword at the global level.

```javascript
var a = 5;

console.log(a);                        // 5
console.log(this.a);                   // 5
console.log(window.a);                 // 5
```

- `let` & `const` declarations do not create properties on the global object.

```javascript
let a = 5;

console.log(a);                        // 5
console.log(window.a);                 // undefined
console.log(this.a);                   // undefined
```

```javascript
const a = 5;

console.log(a);                        // 5
console.log(window.a);                 // undefined
console.log(this.a);                   // undefined
```

# Scope
- `Scope` refers to the context in which variables are declared & accessed.
- <strong>Global scope</strong> is any code we write inside JS file, which is not inside any function.
- A group of multiple JS statements enclosed within curly braces `{}` is called a `block`.
- All the variables & functions that we can access inside a <strong>block</strong> is called
a `block scope`.

### Let's first understand the problem
```javascript
if (true) {
    let a = 5;
    const b = 10;
    var c = 15;
}

console.log(a);               // ReferenceError: a is not defined    (This is good!!)
console.log(b);               // ReferenceError: b is not defined    (This is good!!)
console.log(c);               // 15                                  (This is very very bad!!) 
```

- To prevent scope leaks and improve code clarity, it's generally recommended to use `let` or `const` instead of `var`, as they provide better control over variable scope and help in writing safer and more maintainable code.

# Shadowing
- Shadowing occurs when a variable declared in an `inner scope` has the same name as a variable in an `outer scope`.
- Shadowing is more prevalent and significant when dealing with variables declared using `var` due to its `function-scoped` nature.
- Since <strong>let and const</strong> are `block-scoped`, they naturally limit the scope of variables to the block they are defined in, reducing the likelihood of shadowing-related issues.

```javascript
var a = 5;

{
  var a = 10;
  console.log(a);                //10
}

console.log(a);                  //10
```
Output : `Variables declared with var are function-scoped (i.e not block scoped), so the inner block reassigns the value of the outer a`.

```javascript
let a = 5;

{
    var a = 10;
}
```
Output : `Technically var a = 10; is declared in the global space (i.e not block scoped), and we know that variables declared with let cannot be redeclared.`

```javascript
let a = 5;

function demo() {
  var a = 10;
  console.log(a);
}

demo();                           //10

console.log(a);                   //5
```
Output : `Since var is function scoped, now it will remain inside its boundary and will not pollute the global scope.`

```javascript
let a = 5;

{
  let a = 10;

  {
    let a = 15;

    {
      let a = 20;
      console.log(a);            //20
      console.log(b);            //ReferenceError: b is not defined
    }
  }
}
```

### Output
- Variables and functions are accessed by traversing the scope chain according to the `lexical hierarchy (i.e from the innermost block or function to the outer enclosing scopes)`.
- When a variable is not found in the current scope, the JS engine checks the parent scope for that variable in the chain.
- If it reaches the end of the chain without finding the variable, it means the variable is not defined in the current scope.