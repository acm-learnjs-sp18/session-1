# Session 1

## Types

### Data Types

- number

  - only one 64-bit floating-point number type. no int, float, double, long long, etc.
  - operations ` + - * / % `
    - `/` is long division, not integer division
  - precedence with parentheses

  ```javascript
  3+5; // 8
  3-5; // -2
  3*5; // 15
  3/5; // 0.6 NOT 0
  Math.floor(7/3); // 2 (integer division)
  ```

- string

  - `+` is both addition and concatenation. if any operand is a string, `+` becomes concatenation, NOT addition

  ```javascript
  // concatenation
  "Welcome to " + "Learn.js"; // "Welcome to Learn.js"
  ```

- boolean

- object

  - functions, arrays, anything not any other type

  - equivalent to dictionaries/maps because they're all *unordered collections of key-value pairs*

    ```javascript
    var myObj = {
        key: "value",
        secondKey: "2ndValue"
    };
    var event = {
        name: "Learn.js",
        location: "Covel 227",
        funLevel: 4/0
    }
    ```

  - there are object wrappers for every other type!

    ```javascript
    var a = "learn.js";
    typeof(a); //"string"
    var b = new String(a);
    typeof(b); //"object"
    a.length; // 8
    b.length; //8
    a == b; // true
    a === b; // false
    ```

  - through a process called **auto-boxing** the interpreter will convert `a` to an object every time a property is required (like `a.length`)

- undefined

  - refers to unassigned variables or, more generally, the absence of a value

- null

  - not an object! it is the *deliberate* *absence* of an object (i.e. `null` is assigned as a "value" (the intentional value of "no value") whereas `undefined` is a default state of meaninglessness/the absence of ever having had a meaning)
  - `typeof(null) == object` is a flaw in the design of JavaScript
  - `null instanceof Object === false` 

- symbol

  - covered in ES6+ workshop! (May 2)

### Arrays

Can be of dissimilar data types

```javascript
var arr = ["Learn.js", 425, true];
arr; // ["Learn.js", 425, true]
arr.unshift("im first!");
arr; // ["im first!", "Learn.js", 425, true]
arr.shift();
arr; // ["Learn.js", 425, true]
arr.push("im last!");
arr; // ["Learn.js", 425, true, "im last!"]
arr.pop();
arr; // ["Learn.js", 425, true]
```



### Type Coercion: Friend or Foe?

- in statically-typed languages (C, C++, Java), you must make coercion explicit and you call it “casting”
- in dynamically-typed languages (i.e. JavaScript), you can cast but you can also do implicit coercion
  - implicit = the interpreter tries to “help” you and make your code work (not "garbage in, garbage out," more like "garbage in, semi-functional less-than-ideal code out")

```javascript
var x = 42;

var y = x + "";     // implicit coercion!
y;                  // "42"

var z = String(x);  // explicit coercion!
z;                  // "42"
```

```javascript
// no coercion
if (x === 3 || x === "3") {
    // do something
}

// explicit coercion
if (Number(x) == 3) {
    // do something
}

// implicit coercion
if (x == 3) {
    // do something
}
```

```javascript
42/"a"; // NaN
"0"/3; // 0
3/"0"; // Infinity
```



## Operators

### Logical Operators

- `&&` does not just evaluate bools but actually returns the second object unless the first is `false`

  - think of it like this:

    ```
    function AND(x, y) {
        if (x == false) {
            return x;
        } else {
            return y;
        }
    }
    ```

- `||` returns the second object unless the first is `true`

  - think of it like this:

    ```
    function OR(x, y) {
        if (x == true) {
            return x;
        } else {
            return y;
        }
    }
    ```

- `!` converts to boolean and returns opposite

### Comparison Operators

- `==`
- `===`
- `!==`
- `<` `<=` `>` `>=`

```javascript
"5" == 5; // true
null == undefined; // true

"5" === 5; // false
null === undefined; // false
```

### Bitwise Operators

Bitwise operators convert all operands to signed 32-bit integers (CS 33?)

- `&` AND
- `|` OR
- `^` XOR
- `~` NOT/negation
- `<<` left shift
- `>>` arithmetic right shift (sign bit/MSB extended)
- `>>>` logical right shift (0s shifted in MSB)

```javascript
5 / 2 | 0; // hacky way to do integer division, not recommended
```

## Control Flow

### If-Else

If you're familiar with other programming languages, then `if-else` statements are pretty much identical:

```javascript
var x = 9;
if (x < 8) {
    console.log("i am smol x!");
} else {
    console.log("i am big x!"); // this will be executed since x is NOT < 8
}
```



### While Loops

```
var x = 0;
while (x < 5) {
    x++;
    console.log("x is " + x);
}
```

The above code will print:

```
x is 1
x is 2
x is 3
x is 4
x is 5
```

And then terminate as x will no longer be less than 5.

### For Loops

