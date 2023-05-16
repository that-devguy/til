# Closures

Allows a function to remember and access variables from its outer scope even after the outer function has finished executing. 

**Closures** enable functions to have private variables and maintain state across multiple function calls. Commonly used for encapsulation, data privacy, and creating functions with persistent state.

Example to illustrate a closure:

```javascript
function outerFunction() {
    var outerVariable = 'Hello';

    function innerFunction() {
        console.log(outerVariable);
    }

    return innerFunction;
}

var closure = outerFunction(); // assigns the returned inner function to a variable
closure(); // Hello
```

In this example, `outerFunction()` declares a variable and then defines an inner function called `innerFunction()`. `innerFunction()` has access to the `outerVariable` even after the `outerFunction()` has finished executing. We create a closure by calling the `outerFunction()` and assigning the returned `innerFunction()` to `closure`. When we call `closure()` it still has access to the `outerVariable` even after the closure has finished executing and logs `'Hello'`.