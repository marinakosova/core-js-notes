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

* [Typing (Type coercion): Static vs Dynamic, Weak vs. Strong (video)](https://www.youtube.com/watch?v=C5fr0LZLMAs)

* [The JS Call Stack Explained In 9 Minutes (video](https://www.youtube.com/watch?v=W8AeMrVtFLY)

What is the Call Stack? A "todo list" of function invocations (Last In, First out).

Whenever you invoke a function, the details of the invocation are saved to the top of the stack (pushed to the top).

Whenever a function returns, the info about the invocation is taken off the top of the stack (popped off of the top).

* [Learn JS Event Loop (video)](https://www.youtube.com/watch?v=8aGhZQkoFbQ)
**00:53** how does javascript actually work ? **02:46** V8, setTimeout **04:03** the call tack **07:18** blocking, what happens when things are slow **10:35** aynchronous callbacks, setTimout **11:1**3 aynchronous callbacks, the call stack **11:56** concurrency **12:50** stack, webapis, eventloop, task queue, console

* [Scope in JavaScript, Execution Context (article)](https://scotch.io/tutorials/understanding-scope-in-javascript), [The Ultimate Guide to Execution Contexts, Hoisting, Scopes, and Closures (video)](https://www.youtube.com/watch?v=Nt-qa_LlUH0&t=1290s)

Variables defined inside a function are in local scope while variables defined outside of a function are in the global scope. Each function when invoked creates a new scope.

Block statements like *if* and *switch* conditions or *for* and *while* loops, unlike functions, don't create a new scope. Variables defined inside of a block statement will remain in the scope they were already in.

JavaScript is a single-threaded language so it can only execute a single task at a time. The rest of the tasks are queued in the Execution Context. As I told you earlier that when the JavaScript interpreter starts to execute your code, the context (scope) is by default set to be global. This global context is appended to your execution context which is actually the first context that starts the execution context.

After that, each function call (invocation) would append its context to the execution context. The same thing happens when an another function is called inside that function or somewhere else.

There can only be one global context but any number of function contexts.

The execution context has two phases of creation and code execution.

* [Closure (article)](https://medium.com/@prashantramnyc/javascript-closures-simplified-d0d23fa06ba4), [Closure (article)](https://dmitripavlutin.com/simple-explanation-of-javascript-closures/)

What is a closure? A closure is a feature in JavaScript where an inner function has access to the outer (enclosing) function’s variables — a scope chain.
The closure has three scope chains:

it has access to its own scope — variables defined between its curly brackets;

it has access to the outer function’s variables;

it has access to the global variables.

**A rule of thumb to identify a closure: if inside a function you see an alien variable (not defined inside that function), most likely that function is a closure because the alien variable is captured.**

``` javascript
let a = 4;

function myFunction() {
    return a * a;
}

// another example
function OuterFunction() {

    var outerVariable = 1;

    function InnerFunction() {
        alert(outerVariable);
    }

    InnerFunction();
}

// another example
function outerFunc() {
    let outerVar = 'I am outside!';
  
    function innerFunc() {
      console.log(outerVar); // => logs "I am outside!"
    }
  
    return innerFunc;
  }
  
  const myInnerFunc = outerFunc();
  myInnerFunc();
```

* [Var, Let, and Const – What's the Difference?](https://www.freecodecamp.org/news/var-let-and-const-whats-the-difference/)

### Var

Scope essentially means where these variables are available for use. *var* declarations are globally scoped or function/locally scoped.

The scope is global when a *var* variable is declared outside a function. This means that any variable that is declared with *var* outside a function block is available for use in the whole window.

*var* is function scoped when it is declared within a function. This means that it is available and can be accessed only within that function.

*var* variables are hoisted to the top of their scope and initialized with a value of undefined.

``` javascript
var greeter = "hey hi";
var times = 4;

if (times > 3) {
    var greeter = "say Hello instead";
}

console.log(greeter) // "say Hello instead"
```

### Problem with *var*

There's a weakness that comes with *var*. I'll use the example below to explain:

``` javascript
var greeter = "hey hi";
var times = 4;

if (times > 3) {
    var greeter = "say Hello instead";
}

console.log(greeter) // "say Hello instead"
```

So, since *times > 3* returns true, *greeter* is redefined  to *"say Hello instead"*. While this is not a problem if you knowingly want *greeter* to be redefined, it becomes a problem when you do not realize that a variable *greeter* has already been defined before.

### Let

*let* is now preferred for variable declaration. It's no surprise as it comes as an improvement to *var* declarations.

A variable declared in a block with *let* is only available for use within that block.

Just like *var*, a variable declared with let can be updated within its scope. Unlike *var*, a *let* variable cannot be re-declared within its scope. So while this will work:

``` javascript
let greeting = "say Hi";
greeting = "say Hello instead";
```

this will return an error:

``` javascript
let greeting = "say Hi";
let greeting = "say Hello instead"; // error: Identifier 'greeting' has already been declared
```
    
