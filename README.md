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

* [Closure (article)](https://medium.com/@prashantramnyc/javascript-closures-simplified-d0d23fa06ba4), [Closure (article)](https://dmitripavlutin.com/simple-explanation-of-javascript-closures/), [WTF Is JavaScript Variable Hoisting](https://www.youtube.com/watch?v=j-9_15QBW2s)

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

* [Var, Let, and Const – What's the Difference?](https://www.freecodecamp.org/news/var-let-and-const-whats-the-difference/), [JavaScript Let, Const & Var: A Complete Guide](https://www.youtube.com/watch?v=dzEieWaOJE0)

### Var

Scope essentially means where these variables are available for use. *var* declarations are globally scoped or function/locally scoped.

The scope is global when a *var* variable is declared outside a function. This means that any variable that is declared with *var* outside a function block is available for use in the whole window.

*var* is function scoped when it is declared within a function. This means that it is available and can be accessed only within that function.

*var* variables are hoisted to the top of their scope and initialized with a value of *undefined*.

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

Just like *var*, a variable declared with *let* can be updated within its scope. Unlike *var*, a *let* variable cannot be re-declared within its scope. So while this will work:

``` javascript
let greeting = "say Hi";
greeting = "say Hello instead";
```

this will return an error:

``` javascript
let greeting = "say Hi";
let greeting = "say Hello instead"; // error: Identifier 'greeting' has already been declared
```

### Hoisting of *let*

Just like *var*, *let* declarations are hoisted to the top. Unlike *var* which is initialized as undefined, the *let* keyword is not initialized. So if you try to use a *let* variable before declaration, you'll get a *Reference Error*.

### Const

Variables declared with the *const* maintain constant values. *const* declarations share some similarities with *let* declarations.

Like *let* declarations, *const* declarations can only be accessed within the block they were declared.

*const* cannot be updated or re-declared. This means that the value of a variable declared with *const* remains the same within its scope. It cannot be updated or re-declared.

This behavior is somehow different when it comes to objects declared with *const*. While a *const* object cannot be updated, the properties of this objects can be updated.

### Hoisting of *const*

Just like *let*, *const* declarations are hoisted to the top but are not initialized.

* [Arrow functions, the basics](https://dmitripavlutin.com/differences-between-arrow-and-regular-functions/)

### This value

No matter how or where being executed, *this* value inside of an arrow function always equals *this* value from the outer function. In other words, the arrow function resolves *this* lexically.

``` javascript
const myObject = {
    myMethod(items) {
        console.log(this); // logs myObject
        const callback = () => {
            console.log(this); // logs myObject
        };
        items.forEach(callback);
    }
};

myObject.myMethod([1, 2, 3]);
```

*this* value inside the arrow function *callback()* equals to *this* of the outer function *myMethod()*.

### Constructors

A consequence of *this* resolved lexically is that an arrow function cannot be used as a constructor.

If you try to invoke an arrow function prefixed with *new* keyword, JavaScrip throws an error:

``` javascript
const Car = (color) => {
    this.color = color;
};

const redCar = new Car('red'); // TypeError: Car is not a constructor
```
### *arguments* object

Again (same as with *this* value), the *arguments* object is resolved lexically: the arrow function accesses *arguments* from the outer function.

``` javascript
function myRegularFunction() {
    const myArrowFunction = (...args) => {
        console.log(args);
    }

    myArrowFunction('c', 'd');
}

myRegularFunction('a', 'b'); // logs ['c', 'd']
```

*...args* rest parameter collects the execution arguments of the arrow function: *['c', 'd']*.

### Implicit *return*

If the arrow function contains one expression, and you omit the function’s curly braces, then the expression is implicitly returned. These are the inline arrows function.

``` javascript
const increment = (num) => num + 1;

increment(41); // => 42
```
### Methods

The method defined using an arrow binds *this* lexically to the class instance.

``` javascript
class Hero {
    constructor(heroName) {
        this.heroName = heroName;
    }

    logName = () => {
        console.log(this.heroName);
    }
}

const batman = new Hero('Batman');
```

Now you can use *batman.logName* as a callback without any manual binding of *this*.

* [Spread Operator (video)](https://www.youtube.com/watch?v=pYI-UuZVtHI&t=792s), [Spread Operator (article)](https://www.notion.so/The-Spread-Operator-b7608512fbd844ec9f27f31740fb7298)

( aka the ... operator)

### Spread & Functions

``` javascript
const temperatures = [76,72,68,79,54,65];
Math.min(...temperatures);
//the same as Math.min(76,72,68,79,54,65)
```

### Spread & Array Literals

``` javascript
const parents = ["Lorie", "Steve"];
const kids = ['Jake', "Annie", "Jess"];

const fullFamily = [...parents, ...kids];
//["Lorie", "Steve", "Jake", "Annie", "Jess"]
```

Spread is also commonly used to create a copy of an array.

``` javascript
const originals = ["Mona Lisa", "American Gothic", "The School of Athens"];
const copies = [...originals];

originals.push("Nighthawks");
console.log(copies);
// ["Mona Lisa", "American Gothic", "The School of Athens"]
```

### Spread & Object Literals

Just like with arrays, we can use spread to combine existing objects:


```jsx
const mainColors = {brightRed: "#e55039", waterfallBlue: "#38ada9"};
const accentColors = {lightGrey: "#778ca3", swanWhite: "#f7f1e3"};

const fullPalette = {...mainColors, ...accentColors};
//{brightRed: "#e55039", waterfallBlue: "#38ada9", lightGrey: "#778ca3", swanWhite: "#f7f1e3"}
```

* [Complete Guide to JS Sets (video)](https://www.youtube.com/watch?v=4pRkrVwpLQo&t=1s)

The first thing you need to know is that Sets are collections of UNIQUE values.

Sets often get lumped in with Arrays because they are both data collections, but there are some significant differences:
Arrays are indexed collections where elements are ordered and retrieved using an index; Sets are keyed collections, where elements are stored using...keys.  Sets do not support random access, re-ordering, and many other features that arrays do support. 

``` javascript
const hashTags = new Set(["#selfie", "#nofilter"])
// Set(2) {"#selfie", "#nofilter"}
```

Note: You cannot pass a non-iterable to `new Set()`.  Something like `new Set(1234)` does not work! Neither does `new Set(1,2,3,4)`. You have two choices: pass in an iterable object OR create an empty Set.

### Adding to Sets

 ```jsx
const annoyingHashTags = new Set();
annoyingHashTags.add("#YOLO");
annoyingHashTags.add("#Blessed");
// Set(2) {"#YOLO", "#Blessed"}
```

You can only pass a single value at a time to `add()`. If you pass an iterable to `add`, the entire object will be added as a single value:

```jsx
annoyingHashTags.add(['#GoodVibes', '#Foodie']);
// Set(3) {"#YOLO", "#Blessed", Array(2)}
```

### Size

```jsx
const annoyingHashTags = new Set();
annoyingHashTags.add("#YOLO");
annoyingHashTags.add("#Blessed")

annoyingHashTags.size //2
```

### Checking For Values

Sets do not support random access, but we are able to check if a Set contains a given value using `has()`.

### Removing Values

To remove a single value from a set, use `delete()`. We can also use `clear()` to empty a set of all values.

### Iterating Sets

Sets are iterable objects, so we can use them with things like `for...of` loops or the spread operator.  Values in a set are ordered by insertion order.

### Why Use Sets?

Sets are definitely not a general replacement for Arrays or other data structures.  They are useful in very specific situations where :

I.You need unique values
II.You don't care about random access
III.Order doesn't really matter (there is an order, but you cannot change it)

* [Temporal Dead Zone (article)](https://www.freecodecamp.org/news/what-is-the-temporal-dead-zone/)

The term to describe the state where variables are unreachable. They are in scope, but they aren't declared.

The `let` and `const` variables exist in the TDZ from the start of their enclosing scope until they are declared.

``` javascript
{
 	// This is the temporal dead zone for the age variable!
	// This is the temporal dead zone for the age variable!
	// This is the temporal dead zone for the age variable!
 	// This is the temporal dead zone for the age variable!
	let age = 25; // Whew, we got there! No more TDZ
	console.log(age);
}
```

You can see above that if I accessed the age variable earlier than its declaration, it would throw a `ReferenceError`. Because of the TDZ.

But `var` won't do that. `var` is just default initialized to `undefined` unlike the other declaration.
