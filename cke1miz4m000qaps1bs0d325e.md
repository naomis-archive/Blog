## Async/await

JavaScript functions are synchronous by default. This means a function, when called, will execute its lines of code one after the other without pause. However, there are times where you may *need* the code to wait for an event to occur, such as a `fetch` request from an API. How do you get the code to wait for that to happen? Today we are going to look at a basic, surface-level explanation of `async` and `await`.

## Promises

Before we dive in to this, we need to look in to what a JavaScript `Promise` is. A JavaScript Promise is just that  - a *promise*. Certain operations, such as `fetch`, return a Promise instead of a value. That Promise effectively serves as a placeholder - the code is saying "I know there will be a value here, but I haven't figured out what that value is yet. I *promise* I'll get you that value though". 

A Promise is considered `pending`, until it either becomes `resolved` or `rejected`. A `resolved` promise will return a value, where a `rejected` promise usually leads to an error. Trying to manipulate a promise that is still pending will cause errors, so we need to tell the code to wait until that promise resolves (or rejects).

## Async

`Async` is a keyword used in a function declaration. 

```js
async function example() {}
//or
const example = async () => {}
```

Using the `async` keyword tells the function "Hey, you're not going to run all of your code at once. Instead, you'll be pausing at spots I tell you to". The important thing to know when making a function `async` are:
* The function will now return a Promise instead of a value
* The function execution might pause, but the *rest of the code* execution will NOT.

## Await

Using the `await` keyword *requires* that a function is `async`. The `await` keyword is used specifically for callbacks or lines that result in a Promise, and tells the function to wait for that Promise to resolve before executing the next line of code. Again, `await` will pause the execution of that `async` function, but will **not** pause the execution of the rest of the code. 

## Example

```js
function bad() {
  const data = fetch(url)
  console.log(data)
}
```

If you call this function, you would see `Promise{<pending>}` in the console, because the `console.log(data)` line runs before the `fetch` promise is resolved.

```js
async function good() {
  const data = await fetch(url)
  console.log(data)
}
```

This function, however, will log the actual response, as `await` tells the code to pause until the `fetch` promise is resolved, *then* logs the value of `data` to the console. 

## Conclusion

Hopefully this helps you understand `async/await` a little bit more. Please feel free to provide feedback or ideas on how this description could be improved!