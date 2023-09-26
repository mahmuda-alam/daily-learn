# Contents
- [Number](#number)
  

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
