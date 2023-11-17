# Contents
- [How Javascript Executes Code](#how-javascript-executes-code)
- [Number](#number)
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




