# Javascript Basics

## What is Javascript?

### Javascript's History
Javascript was originally created as an addition to Netscape Navigator (a predecessor to Firefox & the most popular browser at the time) 

Javascript is not related to the Java programming language.  
Javascript was merely named similarly because Java was an extremely popular language at the time. The name was an attempt to piggyback on that popularity.

Javascript became the dominant language for web client-side programming because of early adoption by international standards body ECMA & because of built-in Javascript support by multiple browsers.

Javascript and ECMAscript are essentially synonymous. 

The latest major revision of Javascript is ES6 in 2015. This introduced major changes such as ```const```, ```let```, and arrow functions. 


## ```console.log```



- use ```console.log();``` to print
- use ```console.log();``` to debug
```js
"hello"                         // Prints nothing.
                                // The REPL takes in "hello" but has not recieved
                                // instructions to spit anything back out

console.log("hello world");     // hello world
console.log("how are you?");    // how are you?
```
```console.log();``` should be used for debugging purposes only.   
Debugging means to locate and solve errors in your code. ```console.log``` is mostly used as a way to debug.

<br>

## Operators & Operations
### Operators
```js
()      // parenthesis - encloses an operation and makes it highest priority. 
        
        // If there are multiple operations enclosed in parenthesis, use Order of Operations to determine priority

%       // modulo - divides a number by a number and returns the remainder
*       // multiplication
/       // division
+       // addition
-       // subtraction
```

<br>  

## Order of Operations
**In order of importance, order of operations is:**
```js
()   % / *   + -

()      // top priority

%       // equal priority to / or *
/       // equal priority to % or *
*       // equal priority to % or /

+       // equal priority to -
-       // equal priority to +

// in the event that there is more than one equal priority equation to solve, go left to right
```

Just like Elementray and Middle School math, the Order of Operations works like this:
```js
console.log(6 + 4 / (8 % 6) - 6)   // 2

(6 + 4 / (8 % 6) - 6)              // ((8 % 6)) === 2    |  Parenthesis is top priority
(6 + 4 / (2) - 6)                  // (4 / (2)) === (2)  |  Division is top priority
(6 + (2) - 6)                      // (6 + (2)) === 8    |  Addition and subtraction have equal priority, go left to right
(8 - 6)                            // ((8) - 6) = 2      |  Subtraction is the only operation remaining
(2)                                // (2)                |  Expression returns 2
```
<br>

## Boolean Operations
```js
!       // (not) referred to as "bang"
&&      // (and)
||      // (or)
```
**The ```!``` bang operator inverts the status of what it is in front of. Opposite day!**  
**Two bangs ```!!``` is essentially 'not not" and returns the status to normal:** 
```js
console.log(!true);     // false
console.log(!false);    // true
console.log(!!false);   // false
```

**The ```&&``` AND operator only returns true if both sides are true**
```js
console.log(false && false);    // false
console.log(false && true);     // false
console.log(true && false);     // false
console.log(true && true);      // true
```

**the ```||``` OR operator only returns false if both sides are false**
```js
console.log(false || false);    // false
console.log(false || true);     // true
console.log(true || false);     // true
console.log(true || true);      // true
```

<br>

## De Morgan's Law
**De Morgan's Law distributes bang ```!``` across an expression in parenthesis and flips the boolean operator**
```js
 !(A || B) is equivalent to !A && !B
 !(A && B) is equivalent to !A || !B
```

<br> 

## Comparison Operators
```js
>       // (greater than)
<       // (less than)
>=      // (greater than or equal to)
<=      // (less than or equal to)
==      // (**DO NOT USE** -- loose equals -- is tricky and finnicky)
===     // (deep equals / strict equals)
!==     // (not equal to)
```
```js
console.log(10 > 5);            // true
console.log(10 < 5);            // false
console.log(1 < 7);             // true
console.log(7 <= 7);            // true
console.log(5 === 6);           // false
console.log(5 !== 6);           // true
console.log("a" !== "A");       // true
console.log(false === false);   // true
```
**Be careful with ```==``` vs ```===``` when writing code. Loose equals ```==``` is a trap!  
Always use deep equals / strict equals ```===```**
```js
console.log(5 === "5");         // false
console.log(5 == "5");          // true
console.log(0 === false);       // false
console.log(0 == false);        // true
```

<br>

## NaN
#### NaN refers to Not a Number, a result you get when you are doing bad math
```js
let num;
console.log(num + 3);               // NaN

console.log(undefined + 3);         // NaN
console.log("fish" * 2);            // NaN

// ? NaN is a number type
console.log(typeof Number(NaN));   // number
```
<br>

## Variables

### What is a Variable?
**A variable is a definition set to a value**  
A variable can be thought of as a box with an item inside. The item is the value. 
```js
let eggs = 15;
let bacon = 10;
```
<img src="../images/variable_box.jpg"><br>
More literally, **a variable is a *pointer* to the value it represents.** More on that below at the [bottom of this section.](#variables-in-memory) 

Variables are Declared and then Initialized.    
Variables can contain strings, numbers, or booleans. 
Variables that have not been assigned a value return ```undefined```

#### Declaration:
```js
let bootcamp;
// ? let variable bootcamp exist
console.log(bootcamp);      // undefined
```

#### Assignment
```js
// ? The assignment operator = allows a declared variable to be assigned a value

bootcamp = "c0dingz";
// ? let variable bootcamp contain the string value "c0dingz"
console.log(bootcamp);      // 'c0dingz'
// variable bootcamp now holds the value of 'c0dingz'
```
You don't need to do both of these things separately:


#### Initialization
```js
let bootcamp = "c0dingz";
console.log(bootcamp);      // 'c0dingz'

let birthYear = 2012;
console.log(birthYear);     // 2012
```

When initializing variables, you can also use your variable intializer for multiple variables on one line: 

```js
let size = "XXS", biggerSize = "M", biggestSize = "XXXL";
```

<br>

### Messing About with Variables
#### Manipulating the value of a variable
```js
let num = 42;
// ? num has the value of 42
console.log(num + 8);   // 50
// ! This only adds 8 to the value of num (42) - It doesn't change the varible
console.log(num);       // 42
// ! The value of num (42) is still 42 because that's what it was initialized as
```

#### How to reassign values to variables
```js
num = num + 10;
// ? num = num (42) + 10
// ? num = new num (52)
console.log(num);       // 52

// Examples
let number = 0;
number += 10;           // equivalent to number = number + 10
number -= 2;            // equivalent to number = number - 2
number /= 4;            // equivalent to number = number / 4
number *= 7;            // equivalent to number = number * 7
console.log(number);    // 14
```
#### Data Types in Variables
Variables can hold several data types:

```js
let falsey = false;                             // boolean
let message = "🎶 message in a bottle 🎶";     // string    
let num = 5;                                    // number
let negNum = -5;                                // negative number
let newObj = {};                                // objects
let nullVariable = null;                        // null value
let noValue;                                    // undefined
```
<br>

### camelCase
Variable names for javascript are written usually in camelCase.   
Words are run together, the first letter of the first word is *lowercase*, and the first letter of any following words is *uppercase*.  

```js
 var dontUseVar = "Seriously, var is globally or fuction scoped, don't use var."

 let betterVariable = "Thank God, let is a normal block-scoped variable"

 const constantVariable = "Good luck changing the value of this constant"
```

<br>

### ```let``` vs. ```const``` vs. ```var```
```let``` and ```const``` have different use cases, while ```var``` is sometimes beloved and sometimes a pariah. 
 
#### ```var```
Using ```var``` will result in a variable that is function-scoped or globally-scoped and has behavior inconsistent with what you would get using ```let```. Many developers will tell you **Don't Do it.**

```js
 var varIsScary = "should I really be using var?"
 ```

If you use ```var```, be aware of the scope issues. More on this in [Scope and Hoisting.](../03_JS/11_Scope_Hoisting.md)
<br>

**You also need to be aware of several other behaviors of ```var```:**
Variables defined with ```var``` can be accidentally redeclared:
```js
var x = "purple";

var x = 9;                      // no error will be thrown, this is valid! Say bye to "purple", x is now 9! 
```



<br>

#### Let
Using ```let``` will result in a block-scoped variable with block-scoped behavior.
```js
let bootPairs = 1;              // Gabby has 1 pair of boots
bootpairs = 2;                  // Gabby buys a pair of boots and updates her variable
console.log(bootPairs);         // Gabby's variable is 2  
```
Here, Gabby's variable updated because ```let``` is reassignable. 
<br>

#### Const
Using ```const``` will result in a variable that is non-reassignable. ```const```, like ```let```, is block-scoped.   
```js
const sandalPairs = 4;          // Gabby has 4 pairs of sandals
sandalPairs = 3;                // Gabby donates 1 pair of sandals and updates her variable
console.log(sandalPairs);       // Gabby's variable is still 4
```
Here, Gabby's variable did not update because ```const``` is non-reassignable and therefore is not able to be changed. 

<br>

### Plus Equals ```+=``` and Minus Equals ```-=```
```js
let checkingAccount = 3500;
let paycheck = 5000;
```
Let's say here that you want to add the value of ```paycheck``` to the value of ```checkingAccount```   

A valid way to do this is:
```js
checkingAccount = checkingAccount + paycheck;   // 8500
```
Here, ```checkingAccount``` is being *reassigned* the value of ```checkingAccount + paycheck```.  

Another valid way is to use the *shorthand* of ```+=```:
```js
checkingAccount += paycheck;                    // 8500                           
```
Here, ```checkingAccount``` is *also* being *reassigned* the value of ```checkingAccount + paycheck``` all in one single step using ```+=```.

<br>

### Minus Minus ```--``` and Plus Plus ``++``
```js
let sum = 1;
sum += 1;                       // 2 
sum -= 1;                       // 0  
```
When you are adding or subtracting by just 1, you can choose to use ```++``` to *increment* or ```--``` to *decrement* by 1 instead.

There are **two** ways to do this, with important differences:
```js
sum ++                          // Return the value, THEN increment value
++ sum                          // Increment the value, THEN return the value
```
```js
console.log(sum);               // 1
console.log(++ sum);            // 2 
```
The value of ```sum``` will be ```2``` in console if you call ```counter```, but ```sum++``` spits out ```1``` in a ```console.log();``` because it ***RETURNS THE VALUE*** first ***BEFORE*** incrementing
```js
console.log(sum);               // 1
console.log(sum ++);            // 1 
```
The value of ```sum``` will be ```2``` when using ```console.log();``` because it ***INCREMENTS THE VALUE*** first and ***THEN*** returns the value   

The same is true for ```--```
```js
console.log(sum);               // 1
console.log(sum --);            // 1  
console.log(-- sum);            // 0
```


<br>

### Variables in Memory
A variable is a *pointer* to the place in RAM on a computer where the value of the variable's data is stored. 

Think of this like a shortcut on the desktop of your PC: the shortcut is not the actual executable. The shortcut is a *pointer* to the executable that is somewhere in a file structure on your hard drive.   

Every shortcut you make is an independent, different pointer.  

<br>



