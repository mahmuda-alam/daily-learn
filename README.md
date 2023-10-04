# Contents
- [How Javascript Executes Code](#how-javascript-executes-code)
- [Number](#number)


## How Javascript Executes Code
Javascript is a synchronous and single threated language. Means it executes line by line and executes a single command in a specific order. Everything in javascript is wrapped inside execution context. Execution context has two components. Javascript code is executed in two phases.They are memory allocation phase and code execution phase.
        
`Memory allocation phase`: In this phase, it starts skimming all the code. All the functions and variables are stored in a memory component in execution context. In the case of a function of javascript is copied all the function  and a variable is declared as `undifined` in a memory block. No matter where that function and variable are declared, they are moved top of the code as a memory component before execution the code. This is called `hoisting` to move the function and variable top of the code.

`Code execution phase`: In this phase, again it starts reading the code and executes line by line in a code component.

Let's see the whole process through an example.

```js
var number = 4;

function Square (n) {
	var res = n * n;
	return res;
}

var newNumber = Square(3);
```

So the memory allocaton phase for these code is allocated like this:

```js
number: undefined;

Square: function Square (n) {
	var res = n * n;
	return res;
}

newNumber: undefined;
```

Code allocation phase is allocated like this:
`n = 4;`
`res = 16;`

Then it assigns the code-
```js
number: 4;
Square: function Square (n) {
	var res = n * n;
	return res;
}
newNumber: 16;
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
