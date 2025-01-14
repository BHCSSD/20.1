# Intro to Functions
  
## Before we start
There are a few keywords you need to know by the end of this unit:
- **Function**
- **Parameter**
- **Argument**
- **Return Value**
- **Scope**
  - **Local Variable**
  - **Global Variable**

## videos for review 
- [Basics](https://thecodingtrain.com/tracks/code-programming-with-p5-js/code/5-functions/1-basics)
- [Function Parameters and Arguments](https://thecodingtrain.com/tracks/code-programming-with-p5-js/code/5-functions/2-arguments)
- [Functions & Return](https://thecodingtrain.com/tracks/code-programming-with-p5-js/code/5-functions/3-return)


## 
Functions are the building blocks of programming. All your code should be in well-defined, well-named, well-written, and well-tested functions. This is the hallmark of a strong intermediate programmer.

We have periodically used functions in our previous units. 
- print()
- draw()
- rect()
- random()
  
They do stuff for us so we don't need to keep coding the same things over and over. Imagine having to code the logic for random() every time you needed it last year.

As you start learning to work with functions, a general rule of thumb is to have a function only do 1 thing. 
- figure out the area of a square
- draw a face
- deal with key press

  

# 1.1 Writing Your Own Functions

First, run this code:

```javascript
function cubed(n) {
  return n ** 3;
}

console.log(cubed(2)); // prints 8
console.log(cubed(3)); // prints 27
```

This code defines a new function named `cubed`. The function takes one parameter, `n`, and returns `n^3`. The code then calls the function twice.

## Important points:

- The first line of a function definition is the function header. It has 4 parts, in order:
  1. The `function` keyword
  2. The function name. This is `cubed` in the example.
  3. The function parameters, in parentheses. This is `(n)` in the example.
  4. A pair of curly braces `{}` to enclose the function body.

- The rest of the function definition is the function body. Note:
  - The body is always enclosed in curly braces `{}` inside the function definition.
  - The body should contain a `return` statement, which immediately ends the function and returns the result of the call to that function.
  - If the function completes without a `return` statement, then JavaScript automatically returns the value `undefined`.
  
- Once a function is defined, you can call it just like any other function.
- When you call the function, you must provide arguments, one for each parameter, in order.

**Question: True or False: every function call returns some value?**


## Another Example

```javascript
function sumOfSquares(x, y) {
  return x ** 2 + y ** 2;
}

console.log(sumOfSquares(3, 4)); // prints 25, which is 3**2 + 4**2
```

This defines a function named `sumOfSquares`. It takes two parameters, `x` and `y`. When we call this function, we must provide two arguments, the values for `x` and `y` in that order.

## Functions that Take No Parameters

Here is another example:

```javascript
function bigNumber() {
  return 78238477823487248727834;
}

console.log(bigNumber()); // prints 78238477823487248727834
```

Here we define a function that takes no parameters. Note that you still have to include the parentheses, both in the function definition and in the function call.

## Functions that Return Multiple Values

Finally, here is one more example:

```javascript
function sumAndProduct(x, y) {
  return { sum: x + y, product: x * y };
}

let result = sumAndProduct(2, 3);
console.log(result.sum, result.product); // prints 5 6
```

# 1.2 Variable Scope
Variables exist in a specific scope based on where they are defined. This means they **cannot** be used outside that scope, in other parts of the code. For now, we will consider two scopes: local and global.

## Local Variables

Variables defined **inside** a function definition. Including its parameters and anywhere in its function body, are called local variables and have local scope. That is, they can only be used in that function. 

Here is an example that tries, and fails, to use local variables outside of a function:

```javascript
function f(x) {
  return x + 5;
}

console.log(f(4)); // prints 9
console.log(x);    // ReferenceError: x is not defined
```

### a few more notes about local variables

- Local variables have a lifetime and exist only during a function call. Each new call to a function gets entirely new local variables.
- Even if another function has variables with the same names, those are different variables with different scopes.

## Global Variables

Variables defined **outside** of a function definition (that is, at the top level) are called global variables and have global scope. That is, they can be used everywhere.

Using global variables can lead to a variety of obscure bugs. For that reason, we generally do not use global variables in your code. However, it can be handy to use global variables in short examples, which is why we do that in the notes. 

**Still: in general, do not use global variables.**



# 1.3 Print Versus Return

A common mistake is to confuse `print` with `return`. For example:

```javascript
function cubed(x) {
  console.log(x ** 3); // Here is the error!
  //print(x ** 3); // in case you use print
}

cubed(2); // prints 8, so it seems to work...
```

This code seems to work, but it doesn't! The function does not explicitly return a value. Thus, as we have learned, JavaScript automatically returns `undefined`. Let's see that:

```javascript
function cubed(x) {
  console.log(x ** 3); // Here is the error!
}

console.log(cubed(2)); // still prints 8, but then also prints undefined
```

As the comment notes, this code still prints 8 but it also prints `undefined`. That suggests something went wrong. 

Let's go one step further and really prove it:

```javascript
function cubed(x) {
  console.log(x ** 3); // Here is the error!
}

let x = cubed(2);
console.log(x + 1); // crashes: we cannot add undefined and a number
```

Ok, so this proves that the function returned `undefined`. 

The key point is: calling `console.log`\`print` has no effect on a return value.

The fix is simple: do not use `console.log` or `print` to return a value. Instead, always use `return`, like so:

```javascript
function cubed(x) {
  return x ** 3; // Fixed
}

let x = cubed(2);
console.log(x + 1); // prints 9 (whew!)
```


# 1.4 Helper Functions

A great way to simplify coding is to use so-called helper functions. These are functions, like any other, but their purpose is to perform part of a computation for another function. For example:

```javascript
function double(n) {
  return n * 2;
}

function largerDouble(x, y) {
  return Math.max(double(x), double(y));
}

console.log(largerDouble(3, 5)); // prints 10
console.log(largerDouble(7, 2)); // prints 14
```

Here, `double()` is a helper function for `largerDouble()`. We could have written `largerDouble()` without `double()`, but there are several key advantages to using helper functions:

1. **Helper functions let us solve smaller problems at a time.** This makes it much easier to reason over each logical chunk when solving larger problems.
2. **Helper functions can be thoroughly tested with their own test functions.** This isolates errors, which makes it much easier to test and debug our code.
3. **Helper functions are reusable.** We can use the same helper function for another function we may write in the future. This saves time and again reduces bugs.

In general, you should embrace using helper functions liberally. In fact, we will often require specific helper functions in the exercises to help you get used to this very effective approach.

**Checkpoint**

True or False: You can write multiple helper functions for one function.

