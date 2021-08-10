# CoreJS
* [Understanding the Keyword THIS in JavaScript (video)](https://www.youtube.com/watch?v=syhNj7X0Vvk)
* [Gentle Explanation of "this" in JavaScript (long read article)](https://dmitripavlutin.com/gentle-explanation-of-this-in-javascript/)

*This* is the context of a function invocation.

*This* is the global object in a function invocation.

*This* is *undefined* in a function invocation in strict mode.

* [What is the difference between scope and context (video)](https://www.youtube.com/watch?v=hDT3IbvH-9I)

*Scope* refers to visibility of variables (in scope or not).

*Context* in JavaScript is related to objects.

* [JavaScript data types and data structures (article)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Data_structures)

JavaScript is a *loosely typed* and *dynamic* language.

The latest ECMAScript standard defines **nine types**: undefined, boolean, number, string, bigInt, symbol, object, function, null.

TypeOf for Data Types and instanceof for Structural Types: 
- {} - Object
- Function - function
- Array - Object
- null - Object
- new String/Boolean/Number - Object
- undefined - undefined
- true - boolean
- "Text" - string
- alert - function
- [] - object
- new Date - object

* [Hight order function REDUCE (video)](https://www.youtube.com/watch?v=6_XzV25rkcE)
``` javascript
// Arrow function
reduce((accumulator, currentValue, index, array) => { ... }, initialValue)

// Callback function
reduce(callbackFn, initialValue)

// Inline callback function
reduce(function callbackFn(accumulator, currentValue, index, array) { ... }, initialValue)
```

* [Expressions vs. Statements in JS (video)](https://www.youtube.com/watch?v=WVyCrI1cHi8)

* [Function declaration vs. function expression (article)](https://medium.com/@mandeep1012/function-declarations-vs-function-expressions-b43646042052)

Function declarations load before any code is executed while Function expressions load only when the interpreter reaches that line of code.

Similar to the var statement, function declarations are hoisted to the top of other code. Function expressions aren’t hoisted, which allows them to retain a copy of the local variables from the scope where they were defined.




