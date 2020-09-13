## Fun with the browser console!

Welcome! Today we are going to look in to how to fully utilise the power of the browser console. To get started, copy this code-snippet and run it in your console!

```js
console.log("%cR%ca%ci%cn%cb%co%cw", "color: red; font-size: 48pt", "color: orange; font-size: 48pt", "color: yellow; font-size: 48pt", "color: green; font-size: 48pt", "color: blue; font-size: 48pt", "color: darkblue; font-size: 48pt", "color: purple; font-size: 48pt")
```

Pretty cool, right? You can render CSS in the console!

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1599950177513/DW14Vbbxo.png)

Before we get in to that, let's go over some of the basics.

## console.log()

`console.log()` is the basic level for printing information to the console, and the one you have likely used the most. 

```js
console.log("This prints to the console.")
```

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1599954718041/9E38RRp8h.png)
## console.warn()

`console.warn()` is the next level above the standard .log() - like before, it prints the content to the console, but highlights it with a yellow background as a "warning". The warning level should be used for important debugging information that does not necessarily impact the app.

```js
console.warn("This is a warning.")
```

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1599954691092/jmN2jX8GO.png)

## console.error()

The next level above `warn` is the `console.error()`. Again, this prints the content to the console, but with a red background to indicate an "error". The error level should be used for information related to page-breaking failures. 

```js
console.error("This is an error.")
```

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1599954883678/jVnoF00Hh.png)

## console.dir()

The `console.dir()` behaves similarly to the `console.log()` in *most* cases, but is much more helpful for debugging *objects*. The log() will sometimes stringify the object, where the dir() will provide a navigable representation. 

```js
console.log([1, 2, 3])
console.dir([1, 2, 3])
```

> [NOTE] 
> Some browsers will identify objects in the `log` statement properly. 

## console.count()

This one is handy for counting iterations in a loop, or values in an array. Try running this code in your console:

```js
const array = [1, 2, 3, 2, 3, 1, 1, 5, 4, 5, 1]
for (let i = 0; i < array.length; i++) {
  console.count(array[i])
}
```

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1599955488885/doOI-xAY9.png)

You now have a running count of the number of times each element appears in the array! console.count tracks keeps a running total of the number of times it has been called with each specific parameter.

## console.assert()

Have you written tests in Chai or Jest before? You may be familiar with the `assert` method - here, it is very similar. 

```js
console.assert(true, "This is true")
console.assert(false, "This is false")
```

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1599955643137/IbYXT7w33.png)

You will see that the console is *silent* for *truthy* assert calls, and only throws an error for *falsy* assert calls. This can be helpful for quick testing of a code block. 

## CSS

Now we get to that feature we showed in the introduction! Within a console.log you can apply CSS! If you have a string to log, you can use the `%c` character to indicate a CSS section. Try this:

```js
console.log("I am default. %c I am blue!", "color: blue;")
```

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1599955791558/7VRJpQIHn.png)

The `%c` indicates where the CSS should begin to apply. If you like, you can include *multiple* CSS sections:

```js
console.log("%cI am red. %cI am yellow. %cI am green.", "color: red;", "color: yellow;", "color: green;")
```

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1599955878221/ph6Clwyt7.png)

Each occurrence of `%c` will begin applying the next CSS statement in the list. But you can also apply multiple rules at once!

```js
console.log("%cI am large and teal. %cI am small and purple.", "color: teal; font-size: 48pt;", "color: purple; font-size: 24pt;")
```

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1599955973790/PtMkJy_Rb.png)

## In Conclusion

Hopefully you are starting to see how powerful the browser console is. What are some of your favourite console methods, tips, and tricks?