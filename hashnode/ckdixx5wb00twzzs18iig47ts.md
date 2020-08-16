## Iteration

The other day we talked about recursion - but today we are going to explore iteration. More specifically, we are going to touch on one very bad practise for iterating through an array. For those who have not heard this term, iteration is the process of going through an array of elements and checking each element, or going through a string and checking each letter. 

## Basic Iteration

To begin, let's look at a basic iteration example - the `for` loop.

```js
const array = [1, 2, 3, 4, 5]
for (let i = 0; i < array.length; i++) {
  console.log(array[i])
}
```

We have a few things going on here - first, we have declared an array `array` (creative name, right? 😉) which contains the numbers 1, 2, 3, 4, and 5. Then we have started a `for` loop to iterate through that array. A `for` loop has three components: First, we delcare the iteration variable `i` and initialise it with a value of 0. Second, we set the condition for running the loop - the loop will run while this condition is true. In our loop, the condition is `i < array.length`, meaning the loop will run until `i` reaches 5. Third, we set the variable `i` to increment by one at the end of each iteration. In our code block, we tell the loop to log the value of `array[i]` (the element in `array` at index `i`) to the console. If we run this loop, our console will show `1 2 3 4 5`. Woohoo!

## Changing the Array

One thing I see a lot of newer developers try to do is change the array while they iterate. This *can* be effective, under very specific circumstances, but in general if you change the length of your array you will not get the value you expect from the loop. Let's modify our previous example to take a look.

```js
const array =[1, 2, 3, 4, 5]
for (let i = 0; i < array.length; i++) {
  console.log(array[i])
  array.splice(i, 1)
}
console.log(array)
```

We have changed the code to log the value of `array[i]` to the console then *remove* that element from the array. When the loop completes, the code will log the value of `array` to the console. After executing this loop, what do you think the console would show? If you guessed the console would show `1, 2, 3, 4, 5` and an empty array, you fell for the trap (sorry!). Here is what the console will actually show:
 
```js
1
3
5
[ 2, 4 ]
```

But why? Our loop should go through the entire array right? Let's break it down step-by-step.

### First Iteration
On our first iteration, the value of `i` is 0. We log the value of `array[0]` to the console, and remove `array[0]` from the array.
```js
array before: [1, 2, 3, 4, 5]
console: 1
array: [2, 3, 4, 5]
```

### Second Iteration
On our second iteration, the value of `i` is now 1. We log the value of `array[1]` to the console, and remove `array[1]` from the array.
```js
array before: [2, 3, 4, 5]
console: 1 3
array: [2, 4, 5]
```

But wait! It skipped over the `2`! Because we removed an element from the array, the indices of the remaining elements have changed. Our loop still incremented the value of `i`, and has skipped over an element! The element `2`, which was originally at index 1, shifted to index 0 when we removed the first element. But our loop does not know this, and continues as written.

### Third Iteration
On our third iteration, the value of `i` is now 2. We log the value of `array[2]` to the console, and remove `array[2]` from the array.
```js
array before: [2, 4, 5]
console: 1 3 5
array: [2, 4]
```

It happened again! Our loop has skipped over 4, because the index of the elements has changed while the iteration variable still incremented. After this iteration, `i` gets incremented to 3, and the array has a length of 2 - our loop condition is no longer true and this code stops executing (resulting in the console printout above).

Iterations and loops have many uses - in general, however, it is poor practise to change the length of an array while you are iterating through it. What iteration tips do you have for newer programmers? 