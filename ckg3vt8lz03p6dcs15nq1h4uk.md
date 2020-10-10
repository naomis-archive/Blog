## Algorithms: How Important Are They Really?

Hackerrank, Leetcode, CodeWars, and even freeCodeCamp all offer a vast number of algorithm challenges to practise your coding skills. Quite often I hear new developers say "I'm terrible at math" and "Algorthims are hard, maybe programming isn't for me". 

**You do not need to be an algorithm master to be a 'real' programmer**

Today we will talk about why algorithms are such a "hot topic", and how to improve your skills at them. 

## Why are Algorithms Important?

A *lot* of companies use algorithm challenges/assessments in their interviews. When writing production code, the use-case for them is often very small (unless you're in a field like data analysis), so why do they come up in almost every technical interview?

*They are easily quantifiable.* An interviewer can assess a candidate's coding ability much more efficiently with an algorithm challenge than with something like building a website, as it requires less investment to set up the environment and less time to complete the challenge. Additionally, while there is not necessarily a "correct" answer to solve an algorithm (if the code works, it works!) seeing a candidate's thought process and approach can provide insight into their abilities and overall problem solving skill.

## How do I Improve?

Practise Practise Practise! The best way to strengthen your skills is to *use* them. The websites mentioned above are great resources for practising. 

Many algorithms might *seem* math heavy, and having mathematical knowledge can help. But I would argue that mathematical knowledge (and math was my strong suit in school) is less important than problem solving skills (which maths classes help with). So let's look at a good universal approach for solving an algorithm.

Here are the steps I take:
1. Identify the input.
1. Identify the output.
1. In plain words, determine the steps to turn the input to output.
1. Turn those steps into code. 
1. Debug and Refactor (optional).

Let's apply these steps to a basic algorithm:

```md
Write a function isPalindrome that takes a string and returns `true` if the string is a palindrome (the same spelled backwards and forwards) or `false` if it is not.
```

### Identify the Input

Our very first step is to identify the input. Thankfully, this example is written clearly, and says the function "takes a string". So we know our function is called `isPalindrome` and takes a string. We can write our boilerplate with this - today we will use TypeScript to help with the type-checking. 

```typescript
function isPalindrome(str: string) {

}
```

### Identify the Output

Again, the example has been helpful in describing the goal. According to the text, our function should return `true` or `false`, which means it returns a boolean value. We can add that typing to our function declaration.

```typescript
function isPalindrome(str: string): boolean {

}
```

Great! Now we are ready to break down the challenge into steps.

### Determine the Steps

I like to use comments within the code to plan out the steps, so I have them within the editor when I start writing the code. So how do we check if a word, like "racecar", is a palindrome? Well, a good approach is to write a new word using the letters in the old word - but starting from the end. This gives us a reversed version of the word, then we can compare. Let's add those steps to our code.

```typescript
function isPalindrome(str: string): boolean {
    //Create a new string
    //Build the string using the letters from the old string backwards
    //compare the two
}
```

### Write the code

Awesome! We now have some basic steps. Now we can turn them in to code! So we look at each line individually. First, how do we create a new string? Well, we can declare a new variable and initialise it as `""`, an empty string. How about building the new string from the old one? A standard `for` loop could be a good first approach here, as it allows us to start at the end and move to the beginning. Inside that loop we should add each letter to the new string. Finally, we need to compare the two and return true or false based on that comparison. Because the comparison itself returns a boolean, we can return that value directly.

Here is what we have now:
```typescript
function isPalindrome(str: string): boolean {
    //Create a new string
    let newStr = "";
    //Build the string using the letters from the old string backwards
    for (let i = str.length; i >= 0; i++) {
        newStr += str[i];
    }
    //compare the two
    return str === newStr;
}

console.log(isPalindrome("racecar"));
```

Great! Let's run it! The [TypeScript Playground](https://www.typescriptlang.org/play) is a great resource for testing quick TS snippets without having to spin up a local environment, so let's head over there and run it. 

Oh no! The function returned `false`, but "racecar" IS a palindrome. Let's add a `console.log(newStr)` before our return statement and see what happened:

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1602346103266/L0CXmJG42.png)

### Debug and Refactor

Okay, so we have a bug in our code that we need to fix. The value of `newStr` starts with `undefined`. How can we fix this? Take another look at our loop bounds. We start at `str.length`, but strings are 0-indexed, so we actually need to start at one less than this value.

```typescript
function isPalindrome(str: string): boolean {
    //Create a new string
    let newStr = "";
    //Build the string using the letters from the old string backwards
    for (let i = str.length - 1; i >= 0; i++) {
        newStr += str[i];
    }
    //compare the two
    return str === newStr;
}

console.log(isPalindrome("racecar"));
```

And now we have success! But... we are not done yet. What if we try `console.log(isPalindrome("race car"))`? The space between the words throws off the comparison and returns `false`, even though it is still a palindrome. So we need to fix this as well. 

In general, it is good practise to *avoid* mutating the original function input. Let's create a variable called `oldStr` and use that to store the original string with whitespaces removed. We will also need to update all of our `str` references to use `oldStr` instead:

```typescript
function isPalindrome(str: string): boolean {
    //remove white spaces
    let oldStr = str.replace(/\s/g, "")
    //Create a new string
    let newStr = "";
    //Build the string using the letters from the old string backwards
    for (let i = oldStr.length - 1; i >= 0; i--) {
        newStr += oldStr[i];
    }
    //compare the two
    console.log(newStr)
    return oldStr === newStr;
}

console.log(isPalindrome("race car"))
```

And now we have success! You have successfully solved the algorithm, and hopefully gained some insight into a good general approach for algorithm challenges. Remember to keep practising, and good luck in your journey!

