# Contents
- [How Javascript Executes Code](#how-javascript-executes-code)
- [Number](#number)
- [Type of Function](#type-of-function)
  	- [Arrow Function](#arrow-function)
  	- [Pure Function](#pure-function)
  	- [First Class Function](#first-class-function)
  	- [Anonymous Function](#anonymous-function)
  	- [Callback Function](#callback-function)
- [Git Commands](#git-commands)
    - [Set Git User Name and Email](#set-git-user-name-and-email)
    - [Create Branch](#create-branch)
    - [Stage Files in Git](#stage-files-in-git)
    - [Set Commit Message](#set-commit-message)
    - [Upload Changes to Remote Branch](#upload-changes-to-remote-branch)
    - [Check Current Status](#check-current-status)
    - [Check All Commits](#check-all-commits)
    - [Fetch Remote Branches to Local Repository](#fetch-remote-branches-to-local-repository)
    - [Switch Branch](#switch-branch)
- [Terminal Commands](#terminal-commands)
  	- [Create Directory](#create-directory)
  	- [Navigate Directory](#navigate-directory)
  	- [Create File](#create-file)
  	- [Show File List](#show-file-list)
  	- [Open VS code](#open-vs-code)


## How Javascript Executes Code
**Javascript is a synchronous and single threaded language.** That means it executes code line by line. It executes a single command in a specific order. Everything in javascript is wrapped inside execution context. Execution context has two components.

1. **Memory Component:** It is also known as **Variable Environment.** It consist of Key value pair and functions are stored. The **variable environment** is where all the Variables and Functions are stored.
2. **The Code Component:** It consists of lines of code. It executes one line of code at a time. It is also called a **thread of execution** means each line of code is executed one by one.

Javascript code is executed in two phases.They are **memory allocation phase** and **code execution phase.**
        
**Memory allocation phase:** In this phase, it starts skimming all the code. All the functions and variables are stored in a memory component in execution context. In case of a function of javascript is copied all the function code into a memory block but in case of a variable, it assigns `undefined` as a default value. No matter where that functions or variables are declared, they are moved top of the code as a memory component before execution of the code. This is called **hoisting**. So hoisting means, move the function and variable declaration at top of the code.

**Code execution phase:** In this phase, again it starts reading the code and executes line by line in a code component.

Let's see the whole process through an example.

```js
var number = 4;

function sum (a, b) {
	var res = a + b;
	return res;
}

var newNumber = sum(3, 5);
```

So in the memory allocaton phase, these code are allocated like this:

```js
// Global memory component
number: undefined;

sum: function sum (a, b) {
	var res = a + b;
	return res;
}

newNumber: undefined;
```

Then it will start the next phase code execution like this:

```js
// Global memory component
number: 4;
sum: function sum (a, b) {
	var res = a + b;
	return res;
}
newNumber: sum(3, 5);
```
Now `sum` function is invoked. So it will create another same loop from above, memory allocation phase and code execution phase.

In memory allocation phase it looks like this:

```js
// 'sum' function's memory component
a: undefined
b: undefined
res: undefined
```

Then in code executation phase it will work like this:

```js
a: 3;
b: 5;
res: 8;
```

At last the function return `8` to the `newNumber`. So the final result of the global memory component will be:

```js
// Global memory component
number: 4;
sum: function sum (a, b) {
	var res = a + b;
	return res;
}
newNumber: 8;
```


## Number
Number is a very complicated thing in Programming.There are different types of number,for example-
- **Integers:** This is a number without fraction,for example-600,45,78,-3
- **Floating point number:** This is a decimal point and decimal places,for example - `12.5, 67.9889`
- **Doubles:** They are accurate to a greater number of decimal places.

We even have different types of numbers. Decimal is based `10(0-9)`.But we have different things like...
- **Binary:** This is two number for understanding of computar`(0s and 1s)`.
- **Octal:** This is based on 8, uses `0-7`.
- **Hexadecimal** This is based on 16,uses `0-9` and `a-f`.
  
There are some methods in javaScript. One of them is `toFixed(<expected_decimal_number>)`. To get fix number of decimal, we can use `toFixed`. For example
```js
const number = 2.765437;
number.toFixed(2); // Output will be 2.77
```

Converting number of data types. For example
```js
let myNumber = "45";
myNumber += 3; // The result is 453,not 48 because myNumber is a string.

typeof myNumber; // Output will be string
```

Now if you want to get your expected result, you need to convert the number `string` into `number`. Then you can add any number with that. For example
```js
let myNumber = "45";
myNumber = Number(myNumber) + 3; // Output will be 48, because 'myNumber' has converted into Number before add operation.
```

# Type of Function
#### Arrow Function
In Javascript, there are two types of function. we have `normal function` and `arrow function`. `Arrow function` `()=>{}` is concise way of writing javascript functions in shorter way. They make our code more structured and readable. `Arrow function` are anonymous function. Functions without a name and are not bound by an identifier. `Arrow function` do not return any value and can be declared without function keyword.

Example:
```js
const multiply = (num1, num2) => {
const result = num1 * num2;
return result
}
```

If the `return` statement is the only statement in the function, you can even have a shorter function expression. For example:
```js
const multiply = (num1, num2) => {
return num1 * num2;
}
```

This function only contains the return statement. With arrow functions, we can have something shorter like this:
```js
const multiply = (num1,num2) => num1 * num2
```
**Todo: Need to add more details** 


#### Pure function
A `pure function` is a function that always return the same result if the same arguments are passed. It does not depend on any data change during a program's execution. Rather it only depends on its input arguments.
Also a pure function does not produce any observable side effcts such as network requests or data mutation etc.

**1.Same Input => Same Output**
This example returns a value based on the given parameters, regardless of where/when you call it.
If you pass 2 and 4, you’ll always get 6. Nothing else affects the output.
```js
const add = (x, y)=> x + y;
add(2, 4); //Output will be 6.
add(2, 4); //Output will be 6.
```
```js
let x = 2;
const add = (y)=> {
x+=y;
}
add(4); Output will be 6, the first time
add(4); Output wil be 10
//So this is not a pure function.
```

#### First Class Function

In javascript, Functions are first class objects, which means they can be:

- stored in a variable, objects or array
- passed as an arguments to a function
- returned from a function
  
**Storing a function**
  Functions can be stored in 3 ways:
  - store in a variable `let fn = function doSomethig() {}`
  - store in an object ` let obj = { doSomething : function(){} }`
  - store in an array `arr.puch(function doSomething() {})`
    
**Function as an arguments**

We are passing our sayHello() function as an argument to the greet() function, this explains how we are treating the function as a value.
```js
function sayHello() {
return hello;
}
function greet (helloFn, name) {
console.log(helloFn() + name);
}
greet(sayHello, john); //Output will be: hello, John
```

**Returning a function**

In this example, we are returning a function from another function - We can return a function because functions in JavaScript are treated as values.

```js
function outerFunction() {
return function innerFunction() {
return 'Hello World'
}
}
let myFunction = outerFunction()
console.log(myFunction); //Output will be: Hello world
```

#### Anonymous Function
`Anonymous` is a function that does not have any name associated with it. Normally we use the function keyword before the function name to define a function in JavaScript, however in anonymous function in JavaScript we use only the function keyword without the function name. 

An `Anonymous function` is not accessible after its initial creation , we can only access this function after storing this function in a variable as a value. An `Anonymous function` can also have multiple arguments, but only one expression.

Example:
```js
let greet = function() {
console.log("Welcome to World!")
}
greet(); //Output will be: Welcome to World!
```

We pass arguments to the anonymous function.

```js
let greet = function(platform) {
console.log("welcome to", platform )
}
greet(World!); //Output will be: Welcome to World!
```

#### Callback Function
A `callback` is a function that is passed as an arguments to an another function, and is called after the main function has finished its execution. The main function is called with a callback function as its arguments, and when the main function is finshed, it calls the callback function to provide a result. Callbacks allow you to handle the results of an asyncronous operation in a non-blocking manner, which means that the program can continue to run while the operation is being executed.

Example:
```js
mainFunction(callback) {
console.log("Performing Operation");
setTimeOut(function() {
callback("Operation Complete")
}, 1000);
}

callBackFunction(result) {
console.log('result: ' + result);
}

mainFunction(callbackFunction);

```



# Terminal Commands

#### Create Directory
To create a directory:

`mkdir <dir_name>`

#### Navigate Directory
To navigate into directory:

`cd <dir_name>`

To move out from a directory:

`cd ..`

#### Create File
To create a file:

`touch <file_name>`

#### Show File List
To show list of files and directories:

`ls`

To show all files and directories including hidden:

`ls -a`

#### Open VS Code
To open current folder into the VS code:

`code .`


# Git Commands

#### Set Git User Name and Email
To set git user name and email in current repository

`git config user.name <user_name>`

`git config user.email <user_email>`

To set git user name and email globally

`git config --global user.name <user_name>`

`git config --global user.email <user_email>`


#### Create Branch
To create a new branch from current branch

`git checkout -b <branch_name>`

To create a new branch from other branch

`git checkout -b <branch_name> <source_branch_name>`

#### Stage Files in Git

`git add <file_path>`

To add all files at a single command

`git add .`

#### Set Commit Message

`git commit -m <message>`

#### Upload Changes to Remote Branch

`git push origin <branch_name>`

`git push origin HEAD`(HEAD means current branch)

#### Check Current Status
To see current status of the folder

`git status`

#### Check All Commits
To check all commits 

`git log`

#### Fetch Remote Branches to Local Repository
`git fetch`

#### Switch Branch
`git checkout<branch_name>`







