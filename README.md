# Programming-With-JavaScript

## Expressions and operators

### Operators

JavaScript has the following types of operators:

[Assignment Operators](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Expressions_and_Operators#assignment_operators) This operator assigns a value to its left operand based on the value of its right operand. 

[Comparison Operators](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Expressions_and_Operators#comparison_operators) This operator compares its operands and returns a logical value based on whether the comparison is true.

[Arithmetic Operators](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Expressions_and_Operators#arithmetic_operators) This operator takes numerical values (either literals or variables) as their operands and returns a single numerical value. 

[Bitwise Operators](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Expressions_and_Operators#bitwise_operators) This operator treats its operands as a set of 32 bits (zeros & ones), rather than as a decimal, hexadecimal, or octal numbers.

[Logical Operators](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Expressions_and_Operators#logical_operators) This operator is typically used with Boolean (logical) values; when they are, they return a Boolean value.

[String Operators](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Expressions_and_Operators#string_operators) In addition to the comparison operators, which can be used on string values, the concatenation operator (+) concatenates two string values together, returning another string that is the union of the two operand strings.

[Conditional (ternary) operator](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Expressions_and_Operators#conditional_ternary_operator) This is the only JavaScript operator that takes three operands. The operator can have one of two values based on a condition. 

[Comma Operator](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Expressions_and_Operators#comma_operator) This operator (,) evaluates both of its operands and returns the value of the last operand. 

[Unary Operators](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Expressions_and_Operators#unary_operators) This operator is an operation with only one operand.

[Relational Operators](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Expressions_and_Operators#relational_operators) This operator compares its operands and returns a Boolean value based on whether the comparison is true. 

### Expressions

An expression is any valid unit of code that resolves to a value. There are two types of expressions: with side effects (for example: those that assign value to a variable) and those that in some sense evaluate and therefore resolve to a value. JavaScript has the following expression categories:

-Arithmetic: evaluates to a number, for example, 9.51413 (Generally uses arithmetic operators)

-String: evaluates to a character string, for example, "John" or "483" (Generally uses string operators)

-Logical: evaluates to true or false. (Often involves logical operators)

-Primary Expressions: Basic keywords and general expressions in JavaScript.

-Left-hand-side expressions: Left values are the destination of an assignment.

## Functions

Functions are one of the fundamental building blocks in JavaScript. A function in JavaScript is similar to a procedure, which is a set of statements that performs a task or calculates a value; however, for a procedure to qualify as a function, it should take some input and return an output. 

### Defining Functions

A function definition (a.k.a function declaration or function statement) consists of the function keyword followed by:

-The name of the function.

-A list of parameters to the function, enclosed in parantheses and separated by commas.

-The JavaScript statements that define the function, enclosed in curly brackets { }. For example, the following code defines a simple function named square:

function square(number) {
  
  return number * number;

}

### Function Expressions

Functions can also be created by a function expression. Such a function can be anonymous; it doesn't have to have a name. For example, the function square can could have been defined as:

const square = function(number) { return number * number }

var x = square(4) // x gets the value 16

However, a name can be provided with a function expression.

const factorial = function fac(n) { return n < 2 ? 1 : n * fac(n - 1) }

console.log(factorial(3))

### Calling functions

Defining a function does not execute it. Defining it names the function and specifies what to do when the function is called. Calling the function actually performs the specified actions with the indicated parameters. For example, if you define the function square, you could call it as follows: 

square(5);

The preceding statement calls the function with an argument of 5. The function executes its statements and returns the value 25. Functions must be in scope when they are called, but the function declaration can be hoisted (appear below the call in the code), for example;

console.log(square(5));

/* ... */

function square(n) { return n * n }

### Function Scope

Variables defined inside a function can't be accessed from anywhere outside the function, because the variable is defined only in the scope of the function; however, a function can access all variables and functions defined inside the scope in which it's defined. For example:

// The following variables are defined in the global scope

var num1 = 20,
    
    num2 = 3,
    
    name = 'Chamakh';

// This function is defined in the global scope

function multiply() {
  
  return num1 * num2;

}

multiply(); // Returns 60

// A nested function example
f
unction getScore() {
  
  var num1 = 2,
      
      num2 = 3;

  function add() {
    
    return name + ' scored ' + (num1 + num2);
  
  }

  return add();

}

getScore(); // Returns "Chamakh scored 5

### Nested Functions and Closures

You may nest a function within another function. The nested (inner) function is private to its containing (outer) function. It also forms a **closure,** which is an expression (most commonly, a function) that can have free variables together with an environment that binds those variables (that closes the expression). Since a nested function is a closure, this means that a nested function can "inherit" the arguments and variables of its containing function. In other words, the inner function contains the scope of the outer function. 

function addSquares(a, b) {
  
  function square(x) {
    
    return x * x;
  
  }
  
  return square(a) + square(b);

}

a = addSquares(2, 3); // returns 13

b = addSquares(3, 4); // returns 25

c = addSquares(4, 5); // returns 41

Since the inner function forms a closure, you can call the outer function and specify arguments for both the outer and inner function.

function outside(x) {
  
  function inside(y) {
    
    return x + y;
 
 }
  
  return inside;

}

fn_inside = outside(3); // Think of it like: give me a function that adds 3 to whatever you g

give
                        // it
result = fn_inside(5); // returns 8

result1 = outside(3)(5); // returns 8

### Closures

One of the most powerful features of JavaScript is Closures. JavaScript allows for the nesting of functions and grants the inner function full access to all the variables and functions defined inside the outer function (and all other variables and functions that the outer function has access to). However, the outer function does not have access to the variables and functions defined inside the inner function. This provides a sort of encapsulation for the variables of the inner function. 

var pet = function(name) {   // The outer function defines a variable called "name"
  
  var getName = function() {
    
    return name;             // The inner function has access to the "name" variable of the 
    
    outer
                             //function
  
  }
  
  return getName;            // Return the inner function, thereby exposing it to outer 
  
  scopes

}

myPet = pet('Vivie');


myPet();                     // Returns "Vivie"

### Using the Arguments Objects

The arguments of a function are maintained in an array like object. Within a function, you can address the arguments passed to it as follows:

arguments[i]

Consider a function that contains several strings. The only formal argument for the function is a string that specifies the characters that separate the items to concatenate. The function is defined as follows:

function myConcat(separator) {
   
   var result = ''; // initialize list
   
   var i;
   
   // iterate through arguments
   
   for (i = 1; i < arguments.length; i++) {
      
      result += arguments[i] + separator;
   
   }
   
   return result;

}

### Arrow Functions

An Arrow Function Expression is a compact alternative to a traditional function expression, but it's limited and can't be used in all situations. In comparison to Function Expressions, Arrow Functions have a shorter syntax. Arrow Functions are always anonymous. Below is an example of an Arrow Function.

var a = [
  
  'Hydrogen',
  
  'Helium',
  
  'Lithium',
  
  'Beryllium'

];

var a2 = a.map(function(s) { return s.length; });

console.log(a2); // logs [8, 6, 7, 9]

var a3 = a.map(s => s.length);

console.log(a3); // logs [8, 6, 7, 9]


## Control Flow

The Control Flow is the order in which the computer executes statements in a script. Unless your computer runs across conditionals and loops, which are very frequent structures that change the control flow, code will be run in order from the first line to the last line. In the example below, a script is used to validate user data from a web page. Validated data is being submitted from the script, however, if the user leaves a required field empty, the script prompts them to fill it in . To do this, the script uses a conditional structure or if....else, so that different code executes depending on whether the form is complete or not.

if (field==empty) {
    
    promptUser();

} else {
    
    submitForm();

}

The above example might also be inside a function that runs when the user clicks the submit button for the form. The function could also include a loop, which iterates through all of the fields in the form, checking each one. So, as seen in the example, it's important to keep in mind that in Control Flow whenever you read a script, you must not only read from start to finish, but also look at program structure and how it affects order of execution.

## JavaScript Functions 

JavaScript Function is a block of code that is designed to perform a particular task. It is executed when something invokes (calls) it. When JavaScript Function is invoked, the code inside the function will execute. This will happen  

- When an event occurs (when a user clicks a button)

- When it is invoked (called) from JavaScript code

- Automatically (self invoked)

### JavaScript Function Syntax

A JavaScript Function is defined with the function keyword, followed by a name, followed by a parantheses ( ). The function names can contain letters, digits, underscores, and dollar signs (same rule as variables). The parantheses may include parameter names separated by commas (parameter1, parameter2). The code to be executed, by the function, is placed inside curly brackets { }. 

function name(parameter1, parameter2, parameter3) {
  
  // code to be executed

}

In the example above, the function parameters are listed inside the parentheses in the function definition. Function arguments are the values received by the function when it is invoked. Inside the function, the arguments (the parameters) behave as local variables. 

### Function Return

A function will stop executing, when JavaScript reaches a return statement. JavaScript will return to execute the code after the invoking statement, if the function was invoked from a statement. Functions will usaully compute a return value, which is returned back to the caller. 

Calculate the product of two numbers, and return the result:

let x = myFunction(4, 3);   // Function is called, return value will end up in x

function myFunction(a, b) {
  return a * b;             // Function returns the product of a and b
}

### Why Functions?

You are able to reuse code. You just have to define the code once, and then you are able to use it many time over, with different arguments, to produce different results. For example,

function toCelsius(fahrenheit) {
  
  return (5/9) * (fahrenheit-32);

}

document.getElementById("demo").innerHTML = toCelsius(77);

In the example above, toCelsius refers to the function object, and toCelsius() refers to the function result. So, the () operator invokes the function. If you access a function without (), it will return the function object instead of the function result. 

### Local Variables

Variables that are declared within a JavaScript function, become local to the function. Local variables can only be accessed from within the function. 

// code here can NOT use carName

function myFunction() {
  
  let carName = "Volvo";
  
  // code here CAN use carName

}

// code here can NOT use carName
