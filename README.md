## Table of CONTENTS
1. SCOPE
2. HOISTING
3. RECURSION
4. CLOSURE

## What is **Scope** in **JavaScript** ?
Scope determines the accessibility (visibility) of variables.
JavaScript has 3 types of scope:
* Block scope
* Function scope
* Global scope

## Block Scope
Before ES6 (2015), JavaScript had only **Global Scope** and **Function Scope**.
ES6 introduced two important new JavaScript keywords: _**let**_ and _**const**_.
These two keywords provide **Block Scope** in JavaScript.

*Example*
{
  let x = 2;
}
// x can NOT be used here
Variables declared with the _**var**_ keyword can NOT have block scope.
Variables declared inside a { } block can be accessed from outside the block.

*Example*
{
  var x = 2;
}
// x CAN be used here

## Function Scope
JavaScript has function scope: Each function creates a new scope.
Variables defined inside a function are not accessible (visible) from outside the function.
Variables declared with _**var**_, _**let**_ and _**const**_ are quite similar when declared inside a function.
#### They all have **Function Scope**:
**function** myFunction() {
  **var** carName = "Volvo"; // Function Scope
}   
**function** myFunction() {
  **let** carName = "Volvo"; // Function Scope
}   
**function** myFunction() {
  **const** carName = "Volvo"; // Function Scope
}   

## Global Scope
Variables declared **Globally** (outside any function) have **Global Scope**.
**Global** variables can be accessed from anywhere in a JavaScript program.
Variables declared with _**var**_, _**let**_ and _**const**_ are quite similar when declared outside a block.
#### They all have **Global Scope**:
**var** x = 2;  // Global scope
**let** x = 2;  // Global scope
**const** x = 2;  // Global scope


## What is **Hoisting** in **JavaScript** ?
Take a look at the code below and guess what happens when it runs:
console.log(foo);
**var** foo = 'foo';

It might surprise you that this code outputs **undefined** and doesn't fail or throw an error – even though **foo** gets assigned after we **console.log** it!

This is because the JavaScript interpreter splits the declaration and assignment of functions and variables: it "hoists" your declarations to the top of their containing scope before execution.

This process is called hoisting, and it allows us to use **foo** before its declaration in our example above.

Let's take a deeper look at functions and variable hoisting to understand what this means and how it works.

### Variable hoisting in JavaScript
As a reminder, we declare a variable with the **var**, **let**, and **const** statements. For example:
**var** foo;
**let** bar;

We **assign** a variable a value using the assignment operator:

// Declaration
**var** foo;
**let** bar;
// Assignment
foo = 'foo';
bar = 'bar';

In many cases, we can combine declaration and assignment into one step:

**var** foo = 'foo';
**let** bar = 'bar';
**const** baz = 'baz';

Variable hoisting acts differently depending on how the variable is declared. Let's begin by understanding the behavior for  **var** variables.

## Hoisting – Variable **(Var)**

There’s a temptation to think that all of the code you see in a  JavaScriptprogram is interpreted line-by-line, top-down in order, as the programexecute. While that is essentially true, there’s one part of that as‐assumption that can lead to incorrect thinking about your program.
**a** =2;
**var a**;
**console.log(a)**;

## Hoisting – FUNCTION DECLARATION

So, one way of thinking, sort of metaphorically, about this process, is that variable and functiondeclarations are “moved” from where they appear in the flow of the code to the top of the code. This gives rise to the name hoisting.

**foo**();
**function foo**(){
    **console.log(a)**;  // *undefined*
    **var a** = 2;
}

So, one way of thinking, sort of metaphorically, about this process, is that variable and functiondeclarations are “moved” from where they appear in the flow of the code to the top of the code. This gives rise to the name hoisting.

## TEMPORAL DEAD ZONE, **let** and **const**

The reason that we get a reference error when we try to access a **let** or **const** variable before its declaration is because of the temporal dead zone (TDZ).

The TDZ starts at the beginning of the variable's enclosing scope and ends when it is declared. Accessing the variable in this TDZ throws a **ReferenceError**.

Here's an example with an explicit block that shows the start and end of **foo**'s TDZ:

{

 	// Start of foo's TDZ
 	
  	let bar = 'bar';
  	
	console.log(bar); // "bar"
	
	console.log(foo); // ReferenceError because we're in the TDZ

	let foo = 'foo';  // End of foo's TDZ
}

## What is **Recursion** in **JavaScript** ?

**Recursion** is **when a function calls itself until someone stops it**. If no one stops it then it'll recurse (call itself) forever. Recursive functions let you perform a unit of work multiple times.
Modern programming languages like JavaScript already have the for and while statements asalternatives to recursive functions. But some languages like Closure do not have any loopingstatements, so you need to use recursion to repeatedly execute a piece of code.

**function** recurse(){
    // *function code*    
    recurse();
}
recurse();

A recursive function must have a condition to stop calling itself. Otherwise, the function is called indefinitely.

Once the condition is met, the function stops calling itself. This is called the base condition.

To prevent infinite recursion, you can use if...else statement (or similar approach) where one branch makes the recursive call, and the other doesn't

**function recurse**(){
    **if**(condition){
        recurse();
    }
    else{
        // stop calling recurse()
    }
}
recurse();


## What is **Closure** in **JavaScript** ?

A **closure** is the combination of a function bundled together (enclosed) with references to its surrounding state (the **lexical environment**). In other words, a closure gives you access to an outer function's scope from an inner function.

**function makeAdder(x)**{
    // *parameter 'x' is an inner variable*
    //*inner function 'add()' uses 'x', so it has a "closure" over it*
    **function add(y)**{
        **return y + x** ;
    };
    **return add**;
}









