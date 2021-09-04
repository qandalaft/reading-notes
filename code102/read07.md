# **Introduction**

## today we will going to talk about Functions

- Functions are one of the fundamental building blocks in JavaScript. A function in JavaScript is similar to a procedure—a set of statements that performs a task or calculates a value, but for a procedure to qualify as a function, it should take some input and return an output where there is some obvious relationship between the input and the output. To use a function, you must define it somewhere in the scope from which you wish to call it.

### 
**Defining functions**

- Function declarations
A function definition (also called a function declaration, or function statement) consists of the function keyword, followed by:
- The name of the function.
A list of parameters to the function, enclosed in parentheses and separated by commas.
- The JavaScript statements that define the function, enclosed in curly brackets, {...}.
- **For example, the following code defines a simple function named square:**
function square(number)
{

  return number * number;
}
 
 - The function square takes one parameter, called number. The function consists of one statement that says to return the parameter of the function (that is, number) multiplied by itself. The statement return specifies the value returned by the function:
  
  - return number * number;
- Primitive parameters (such as a number) are passed to functions by value; the value is passed to the function, but if the function changes the value of the parameter, this change is not reflected globally or in the calling function.

If you pass an object (i.e. a non-primitive value, such as Array or a user-defined object) as a parameter and the function changes the object's properties, that change is visible outside the function, as shown in the following example:
 
 - function myFunc(theObject) {
  theObject.make = 'Toyota';
}

var mycar = {make: 'Honda', model: 'Accord', year: 1998};
var x, y;

x = mycar.make; // x gets the value "Honda"

myFunc(mycar);
y = mycar.make; // y gets the value "Toyota"
                // (the make property was changed by the function)

- Function expressions
While the function declaration above is syntactically a statement, functions can also be created by a function expression.

Such a function can be anonymous; it does not have to have a name. For example, the function square could have been defined as:

- const square = function(number) { return number * number }
var x = square(4) // x gets the value 16
- However, a name can be provided with a function expression. Providing a name allows the function to refer to itself, and also makes it easier to identify the function in a debugger's stack traces:
- const factorial = function fac(n) { return n < 2 ? 1 : n * fac(n - 1) }

console.log(factorial(3))

- Function expressions are convenient when passing a function as an argument to another function. The following example shows a map function that should receive a function as first argument and an array as second argument.
- function map(f, a) {
  let result = []; // Create a new Array
  let i; // Declare variable
  for (i = 0; i != a.length; i++)
    result[i] = f(a[i]);
  return result;
}

- In the following code, the function receives a function defined by a function expression and executes it for every element of the array received as a second argument.
- function map(f, a) {
  let result = []; // Create a new Array
  let i; // Declare variable
  for (i = 0; i != a.length; i++)
    result[i] = f(a[i]);
  return result;
}
const f = function(x) {
   return x * x * x;
}
let numbers = [0, 1, 2, 5, 10];
let cube = map(f,numbers);
console.log(cube);
- Function returns: [0, 1, 8, 125, 1000].

In JavaScript, a function can be defined based on a condition. For example, the following function definition defines myFunc only if num equals 0:
var myFunc;
if (num === 0) {
  myFunc = function(theObject) {
    theObject.make = 'Toyota';
  }
}
- In addition to defining functions as described here, you can also use the Function constructor to create functions from a string at runtime, much like eval().

A method is a function that is a property of an object. Read more about objects and methods in Working with objects.
- **Calling functions**
- Defining a function does not execute it. Defining it names the function and specifies what to do when the function is called.

Calling the function actually performs the specified actions with the indicated parameters. For example, if you define the function square, you could call it as follows:
- square(5);

- The preceding statement calls the function with an argument of 5. The function executes its statements and returns the value 25.

Functions must be in scope when they are called, but the function declaration can be hoisted (appear below the call in the code), as in this example:

console.log(square(5));
- console.log(square(5));
/* ... */
function square(n) { return n * n }

- The scope of a function is the function in which it is declared (or the entire program, if it is declared at the top level).
- The arguments of a function are not limited to strings and numbers. You can pass whole objects to a function. The showProps() function (defined in Working with objects) is an example of a function that takes an object as an argument.

A function can call itself. For example, here is a function that computes factorials recursively:
- function factorial(n) {
  if ((n === 0) || (n === 1))
    return 1;
  else
    return (n * factorial(n - 1));
}

- You could then compute the factorials of 1 through 5 as follows:
- var a, b, c, d, e;
- a = factorial(1); // a gets the value 1
- b = factorial(2); // b gets the value 2
- c = factorial(3); // c gets the value 6
- d = factorial(4); // d gets the value 24
- e = factorial(5); // e gets the value 120
- There are other ways to call functions. There are often cases where a function needs to be called dynamically, or the number of arguments to a function vary, or in which the context of the function call needs to be set to a specific object determined at runtime.

It turns out that functions are themselves objects—and in turn, these objects have methods. (See the Function object.) One of these, the apply() method, can be used to achieve this goal.
## **Function scope**
- Variables defined inside a function cannot be accessed from anywhere outside the function, because the variable is defined only in the scope of the function. However, a function can access all variables and functions defined inside the scope in which it is defined.

In other words, a function defined in the global scope can access all variables defined in the global scope. A function defined inside another function can also access all variables defined in its parent function, and any other variables to which the parent function has access.

- // The following variables are defined in the global scope
var num1 = 20,
    num2 = 3,
    name = 'Chamakh';

// This function is defined in the global scope
function multiply() {
  return num1 * num2;
}

-multiply(); // Returns 60

// A nested function example
function getScore() {
  var num1 = 2,
      num2 = 3;

  function add() {
    return name + ' scored ' + (num1 + num2);
  }

  return add();
}

getScore(); // Returns "Chamakh scored 5"

- **Scope and the function stack**
- Recursion
1. The function's name
2. arguments.callee
3. An in-scope variable that refers to the function

- 
For example, consider the following function definition:
- var foo = function bar() {
   // statements go here
}
## Within the function body, the following are all equivalent:
1. bar()
2. arguments.callee()
3. foo()
- A function that calls itself is called a recursive function. In some ways, recursion is analogous to a loop. Both execute the same code multiple times, and both require a condition (to avoid an infinite loop, or rather, infinite recursion in this case).
- For example, the following loop...
var x = 0;
while (x < 10) { // "x < 10" is the loop condition
   // do stuff
   x++;
}
- 
Copy to Clipboard
...can be converted into a recursive function declaration, followed by a call to that function:
- function loop(x) {
  if (x >= 10) // "x >= 10" is the exit condition (equivalent to "!(x < 10)")
    return;
  // do stuff
  loop(x + 1); // the recursive call
}
loop(0);
- However, some algorithms cannot be simple iterative loops. For example, getting all the nodes of a tree structure (such as the DOM) is easier via recursion:

- function walkTree(node) {
  if (node == null) //
    return;
  // do something with node
  for (var i = 0; i < node.childNodes.length; i++) {
    walkTree(node.childNodes[i]);
  }
}
- function walkTree(node) {
  if (node == null) //
    return;
  // do something with node
  for (var i = 0; i < node.childNodes.length; i++) {
    walkTree(node.childNodes[i]);
  }
}
- function foo(i) {
  if (i < 0)
    return;
  console.log('begin: ' + i);
  foo(i - 1);
  console.log('end: ' + i);
}
foo(3);

// Output:

// begin: 3
// begin: 2
// begin: 1
// begin: 0
// end: 0
// end: 1
// end: 2
// end: 3

## **Nested functions and closures**
- You may nest a function within another function. The nested (inner) function is private to its containing (outer) function.

It also forms a closure. A closure is an expression (most commonly, a function) that can have free variables together with an environment that binds those variables (that "closes" the expression).

Since a nested function is a closure, this means that a nested function can "inherit" the arguments and variables of its containing function. In other words, the inner function contains the scope of the outer function.

To summarize:

The inner function can be accessed only from statements in the outer function.
The inner function forms a closure: the inner function can use the arguments and variables of the outer function, while the outer function cannot use the arguments and variables of the inner function.
The following example shows nested functions:

- function addSquares(a, b) {
  function square(x) {
    return x * x;
  }
  return square(a) + square(b);
}
a = addSquares(2, 3); // returns 13
b = addSquares(3, 4); // returns 25
c = addSquares(4, 5); // returns 41

- Since the inner function forms a closure, you can call the outer function and specify arguments for both the outer and inner function:


- function outside(x) {
  function inside(y) {
    return x + y;
  }
  return inside;
}
fn_inside = outside(3); // Think of it like: give me a function that adds 3 to whatever you give
                        // it
result = fn_inside(5); // returns 8

result1 = outside(3)(5); // returns 8

- **Preservation of variables**

- Notice how x is preserved when inside is returned. A closure must preserve the arguments and variables in all scopes it references. Since each call provides potentially different arguments, a new closure is created for each call to outside. The memory can be freed only when the returned inside is no longer accessible.

This is not different from storing references in other objects, but is often less obvious because one does not set the references directly and cannot inspect them.


- **Multiply-nested functions**
- Functions can be multiply-nested. For example:

A function (A) contains a function (B), which itself contains a function (C).
Both functions B and C form closures here. So, B can access A, and C can access B.
In addition, since C can access B which can access A, C can also access A.
Thus, the closures can contain multiple scopes; they recursively contain the scope of the functions containing it. This is called scope chaining. (The reason it is called "chaining" is explained later.)

Consider the following example:
- function A(x) {
  function B(y) {
    function C(z) {
      console.log(x + y + z);
    }
    C(3);
  }
  B(2);
}
A(1); // logs 6 (1 + 2 + 3)

- In this example, C accesses B's y and A's x.

This can be done because:

B forms a closure including A (i.e. B can access A's arguments and variables).
C forms a closure including B.
Because B's closure includes A, C's closure includes A, C can access both B and A's arguments and variables. In other words, C chains the scopes of B and A, in that order.
The reverse, however, is not true. A cannot access C, because A cannot access any argument or variable of B, which C is a variable of. Thus, C remains private to only B.

- **Name conflicts**
- When two arguments or variables in the scopes of a closure have the same name, there is a name conflict. More nested scopes take precedence. So, the inner-most scope takes the highest precedence, while the outer-most scope takes the lowest. This is the scope chain. The first on the chain is the inner-most scope, and the last is the outer-most scope. Consider the following:

- function outside() {
  var x = 5;
  function inside(x) {
    return x * 2;
  }
  return inside;
}

outside()(10); // returns 20 instead of 10

- The name conflict happens at the statement return x * 2 and is between inside's parameter x and outside's variable x. The scope chain here is {inside, outside, global object}. Therefore, inside's x takes precedences over outside's x, and 20 (inside's x) is returned instead of 10 (outside's x).

- **Closures**

- Closures are one of the most powerful features of JavaScript. JavaScript allows for the nesting of functions and grants the inner function full access to all the variables and functions defined inside the outer function (and all other variables and functions that the outer function has access to).

However, the outer function does not have access to the variables and functions defined inside the inner function. This provides a sort of encapsulation for the variables of the inner function.

Also, since the inner function has access to the scope of the outer function, the variables and functions defined in the outer function will live longer than the duration of the outer function execution, if the inner function manages to survive beyond the life of the outer function. A closure is created when the inner function is somehow made available to any scope outside the outer function.

- var pet = function(name) {   // The outer function defines a variable called "name"
  var getName = function() {
    return name;             // The inner function has access to the "name" variable of the outer
                             //function
  }
  return getName;            // Return the inner function, thereby exposing it to outer scopes
}
myPet = pet('Vivie');

myPet();                     // Returns "Vivie"








