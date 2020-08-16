## Recursion

What is recursion? Recursion is the term used to describe a function that calls itself repeatedly until a specific condition is met. Recursion functions similarly to iteration (loops), but offers more powerful manipulation options - things like branching, or stack manipulation. In most programming languages, recursion tends to be significantly slower than iteration, and is reserved for use cases where iteration would require a much larger (or messier) amount of code. 

For the purpose of this article, however, we will look at a rather basic example of recursion.

## Our example

```js
function countdown(n) {
  if (n < 1) {
    return [];
  } else {
    const arr = countdown(n - 1);
    arr.unshift(n);
    return arr;
  }
}
```

This function takes an initial parameter `n`, which should be a number, and returns an array of numbers from `n` to 1, counting down. 

Breaking down the code, if the value of `n` is less than 1, the function returns an empty array. This is often called the *base case*, and ensures that the recursion ends at some point - otherwise, you end up with an infinite series of function calls!

Otherwise, the function declares a variable `arr` with the value of `countdown(n-1)` - this is the recursion. The function then uses `.unshift(n)` to append the value of `n` to the *beginning* of the array. Finally the function returns the `arr` array.

## How does it work?

To understand the process of recursion, we need to touch on the meaning of the "call stack". The call stack is a last-in-first-out queue of function calls - like stacking cards on top of each other. Each function call gets placed on the stack after the previous function calls.

Let's call the function and take it step by step. 
```js
countdown(5)
```
Here we have called the function with a value of 5 for `n`. This is the beginning of our call stack. As we described above, the function checks that 5 is not < 1 - since it is not, the function proceeds with another call. The function calls itself with a value of `n-1`, so now it has called `countdown(4)`. This has our stack looking like:
```js
countdown(5)
  countdown(4)
```

The function will continue until it reaches a value of `n` that is less than 1 - then the recursion ends. At this point, here is what the stack looks like:
```js
countdown(5)
  countdown(4)
    countdown(3)
      countdown(2)
        countdown(1)
          countdown(0)
```

## Resolving the Stack

Once the recursive function calls have stopped, the stack can resolve. Remember that the stack is last-in-first-out; we started our function calls at the top, so we start resolving the function calls at the bottom.

Our first function call is `countdown(0)`, which returns an empty array. Great - that was the easy part! But what about `countdown(1)`?

`countdown(1)` takes the returned value of `countdown(0)`, assigns it to the `arr` variable, and appends `n` at the beginning. `n` has the value of `1`, at this point. The function then returns that array. 

`countdown(2)` takes the returned value of `countdown(1)`, and continues the process. The stack resolves when `countdown(5)` is done running, and we get a final return value. 

## Visualise the Stack

Sometimes it helps to see it broken down visually. Here is what the complete process looks like:

```js
countdown(5) // calls countdown(4)
  countdown(4) // calls countdown(3)
    countdown(3) //calls countdown(2)
      countdown(2) //calls countdown(1)
        countdown(1) //calls countdown(0)
          countdown(0) //base case reached, no more function calls
          [ ] // returned from countdown(0)
        [1] // returned from countdown(1)
      [2, 1] // returned from countdown(2)
    [3, 2, 1] // returned from countdown(3)
  [4, 3, 2, 1] // returned from countdown(4)
[5, 4, 3, 2, 1] // returned from countdown(5)
```

The final return value of `countdown(5)` is the array `[5, 4, 3, 2, 1]`. 

Hopefully this helps you visualise the recursion process!