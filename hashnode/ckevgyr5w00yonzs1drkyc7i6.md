## JavaScript Loops - while (!metaphor) return new Metaphor()

While hanging around in the freeCodeCamp Discord, a member shared how their instructor explained the difference between a `for` loop and a `while` loop. The explanation used the process of applying for jobs as a metaphor. I thought it was an excellent description, and decided to expand upon it for other JavaScript iteration methods. I would like to share these with you, in the hopes that it helps you understand how these different methods work. 

## `for` 

The `for` loop is seeing a job you want, deciding you should send out `i` number of applications, and ending the process when you've reached that value of `i`. 

```javascript
for (let i = 1; i <= 20; i++) {
  application.send()
}
```

This loop would send an application 20 times.

## `while`

The `while` loop is for bombarding job postings with applications until you find a job. 

```javascript
while (!job) {
  application.send()
}
```

Unlike a `for` loop, which takes specific loop conditions, a `while` loop accepts a boolean condition. While that condition is true, the loop will continue to run. Once the condition is false, the loop terminates. Note: the `!` operator converts a value into the opposite boolean. In this case, you can read it as "while not job".

## `do...while`

A `do...while` loop is like hammering applications out until you get a job, and then sending *one more* just to be safe. 

```javascript
do {
  application.send()
} while (!job)
```

The key difference between a `while` loop and a `do...while` loop is that the `while` loop checks the condition *before* running the code - the `do...while` loop checks the condition *after* running the code, so the code will always run at least once.

## `.forEach`

The `forEach` method is like taking the same application and sending it to each job opening once.

```javascript
jobs.forEach((job) => application.send)
```

A `.forEach` loop performs the same block of code on every element in the array or collection. 

## `.filter`

The `filter` method is like searching for job postings and *only* finding ones that require Angular experience. 

```javascript
jobs.filter((job) => job.requires("Angular"))
```

A filter iteration will return a new array that only includes elements that evaluate to "true" in the callback function. 

## `.map`

The `map` method is like searching through job postings and collecting the phone numbers to make follow-up phone calls. 

```javascript
jobs.map((job) => job.phoneNumber)
```

The `map` method will take an array, iterate through each element of the array, and add the result of passing that element into the callback function to a new array. 

## `.reduce`

The `reduce` method is like collecting the feedback you get from each application and using them to create a perfect application. 

```javascript
applications.reduce((perfectApp, app) => perfectApp + app.goodFeedback)
```

The `reduce` method is very powerful, but is generally used to turn an array into a single value (such as the sum of all elements in the array). 

## In conclusion

I hope that these metaphors help you understand how these iterations work. If you have any questions or feedback, drop a comment below!

*Special thanks to the freeCodeCamp members Harp (for sharing the initial metaphors), Bjorno43 (for providing the `reduce` metaphor), and bradtaniguchi (for help with clarifying the metaphors).