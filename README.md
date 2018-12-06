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

This is useful for writing methods that refer to object's properties.

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
const box66 = {
    position: 1,
    clickMe: () => {
        document.querySelector('.green').addEventListener('click', () => {
            alert(This is box number ' + this.position);
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
