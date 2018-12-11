# JS-refcards

#### `let` and `const` VS `var`
New `let` and `const` defined in ES6 are block scoped while `var` is function scoped.
```javascript
{
  var a = 'a';
  let b = 'b'; // is not defined outside
  const c = 'c'; // is not defined outside
}
console.log(a);
```

#### IIFE (Immediately Invoked Function Expression)
A way to immediately invoke a function expression, utilizing the function's execution context to create "privacy".
```javascript
(function() { 
  var a = 'a'; 
})();

console.log(a); // 'a' is undefined here
```
#### Function declaration VS function expression
//TODO

#### Arrow functions VS functions
Methods are functions attached to an object. They can refer to the object via `this`.
Instead regular functions have `this` pointing to the global object (e.g. "Window" object).

Arrow functions do not have their own `this`. 
Instead they share a surrounding's `this`.

This is useful when it is necessary to preserve the value of `this`.

:exclamation: Arrow functions can not be constructors, i.e. `new (() => {})` is not acceptable.

```javascript
// ES5
var box5 = {
    position: 1,
    clickMe: function() {
       var self = this; 
       document.querySelector('.green').addEventListener('click', function() {
            // can not refer to box5.position as `this.position` here:
            alert('This is box number ' + self.position);
        });
    }
}

// ES6
const box6 = {
    position: 1,
    clickMe: () => {
        document.querySelector('.green').addEventListener('click', () => {
            alert('This is box number ' + this.position);
        });
    }
}
```

#### String tempaltes in ES6
```javascript
var a = 5;
var b = 10;
console.log(`Fifteen is ${a + b} and not ${2 * a + b}.`);
```

#### The `arguments` object
`Arguments` is an Array-like object accessible inside functions that contains the values of the arguments passed to that function.
Rest parameters in ES6 should be preferred.
```javascript
function func1(a, b, c) {
  console.log(arguments[0]);
}
```

#### Rest parameters in ES6
The rest parameter syntax allows us to represent an indefinite number of arguments as an array.
```javascript
function sum(...theArgs) {
  return theArgs.reduce((previous, current) => {
    return previous + current;
  });
}
```
Unlike spread operator rest parameters are used in function's declaration.

#### Spread syntax
In ES6 spread operator expands an iterable into it's components
```javascript
function sum(x, y, z) {
  return x + y + z;
}

const numbers = [1, 2, 3];

console.log(sum(...numbers));
```

Useful to copy or concatenate arrays:
```javascript
//Copy an array
var arr = [1, 2, 3];
var arr2 = [...arr]; // like arr.slice()

// Concatenate
var arr1 = [0, 1, 2];
var arr2 = [3, 4, 5];
arr1 = [...arr1, ...arr2];
```

#### Default function parameters
Default function parameters allow named parameters to be initialized with default values if no value or undefined is passed.
```javascript
function multiply(a, b = 1) {
  return a * b;
}
```
Can be useful for constructors:
```javascript
function Person(firstName, lastName = 'Smith') {...}
