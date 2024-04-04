# Hoisting
- During the memory creation phase of the `Execution Context`, variables are initialized with undefined while function declarations are stored in the memory as they are.

## How Hoisting works with var?
- Variables declared with `var` are hoisted `WITH` a default initialization of `undefined`. So accessing them before the line they were declared returns undefined.
- Only the `variable declaration` is `hoisted` - the initialization isn't.

```javascript
console.log(a);                                            //undefined

var a;

console.log(a);                                            //undefined
```

```javascript
console.log(a);                                            //undefined

var a = 6;

console.log(a);                                            //6
```

## How Hoisting works with let & const?
- Variables declared with `let` or `const` are hoisted `WITHOUT` a default initialization. So accessing them before the line they were declared throws <strong>ReferenceError: Cannot access 'variable' before initialization.</strong>

```javascript
console.log(a);                           //ReferenceError: Cannot access 'a' before initialization

let a;

console.log(a);                           //undefined
```

## let, const & Temporal Dead Zone (TDZ)
- `let` and `const` are indeed `hoisted`, but they enter a special phase called the <strong>Temporal Dead Zone (TDZ)</strong> until they are initialized. 
- Once a `let` or `const` variable is declared, it enters the `TDZ`. 
- If you attempt to access the variable `before its declaration`, you'll get a <strong>reference error because it's not yet initialized.</strong>
- <strong>The period during execution where let/const variables are hoisted but not accessible: it's called the Temporal Dead Zone.</strong>
- Once the variable is initialized, the TDZ ends.

```javascript
console.log(a)                            //ReferenceError: Cannot access 'a' before initialization

let a = 10

console.log(a)                            //10
```

- Variable `a` is in a TDZ where JavaScript knows of its <strong>existence (because its declaration is hoisted) but it's not accessible (as it doesn't have an initialization).</strong>

## How Hoisting works with function declarations & function expressions
- Function declarations are `fully hoisted.`

```javascript
demo();                                  //I am Hoisted

function demo() {
  console.log("I am Hoisted");
}
```

- Function expressions only hoist the variable declaration `( i.e only when declared with var )`, not the function initialization, so attempting to call them before their declaration will result in an error.

```javascript
demo();                                  //ReferenceError: Cannot access 'demo' before initialization

let demo = function () {
  console.log("Let's see");
};
```

```javascript
demo();                                  //ReferenceError: Cannot access 'demo' before initialization

const demo = function () {
  console.log("Let's see");
};
```

```javascript
demo();                                  //TypeError: demo is not a function

var demo = function () {
  console.log("Let's see");
};

/*
Reason for different error message...

When demo() is called before the assignment, 
demo is still undefined, hence the TypeError.
*/
```

# Some tricky examples

### Example-1
```javascript
{
    var a = 5;
}

console.log(a);                                      //5
```
Output : `There's no "access before declaration" here; it's simply because var declarations are not scoped to blocks.`

### Example-2
```javascript
const a = 1;
console.log(a);                           //1

var b;
console.log(b);                          //undefined
b = 2;

console.log(c);                          //undefined
var c = 3;

console.log(d);                          //ReferenceError: Cannot access 'd' before initialization
let d = 2;
```

### Example-3
```javascript
const func1 = () => {
  console.log(1);
};
func1();                                 //1


func2();                                 // 2
function func2() {
  console.log(2);
}

func3();                                 // TypeError: func3 is not a function
var func3 = function func4() {
  console.log(3);
};
```

### Example-4
```javascript
let foo = 10;

function func1() {
  console.log(foo);                      // undefined
  var foo = 1;
}
func1();


function func2() {
  console.log(foo);                    //ReferenceError: Cannot access 'foo' before initialization
  let foo = 1;
}
func2();
```

### Example-5 (IIFE)
```javascript
(function () {
  console.log(x);                     //undefined
  if (true) {
    console.log(x);                   //undefined
    var x = 20;
  }
  console.log(x);                     //20 (since var is function scoped, not block scoped)
})();
```

### Example-6
```javascript
let x = 5;
function three() {
  let x = 10;
  function two() {
    let x = 15;
    function one() {
      let x = 20;
      console.log(x);                 //20
    }
    one();
  }
  two();
}

three();
console.log(x);                        //5
```

#### Output
- When a variable is accessed, JS searches for its value `first` in the local variable environment and then in the outer variable environments until it reaches the <strong>Global Variable Environment.</strong>
- This `hierarchical` structure of variable environments allows for `lexical scoping`. Where variables are resolved based on their `proximity` to the `Current Execution Context`