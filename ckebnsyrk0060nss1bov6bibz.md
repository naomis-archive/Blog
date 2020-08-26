## JAMStack

As you continue your development journey, you may run across "stack" terms such as MERN, MEAN, and JAMStack. But what do these mean? And how do they affect you?

MERN and MEAN are considered "technology stacks". The MERN stack applies to an app built using MongoDB, Express, React, and Node.js - the MEAN stack would be MongoDB, Express, Angular, and Node.js. But what about the JAMStack? What is that?

## Definition

The JAMStack is not a "technology stack" in the same sense as MERN or MEAN, as it does not require or apply to the use of specific technologies for an application. Instead, JAM stands for "Javascript, APIs, and Markup". The term appears to have been coined by [Netlify](https://netlify.com), and applies to any web application that *does not rely on a server*. The application does not need to use JavaScript, or APIs, or Markup, specifically. Instead, it applies a combination of some or all of these approaches to build a functional app.

## Examples

Did you build a portfolio page using HTML and CSS? That's a JAMStack application. What about a page using React, but served as static build files? That is also JAMStack. How about an app that fetches data from an API and renders it to the page? Yep - it's JAMStack. There are no restrictions or requirements for the use of languages, libraries, or frameworks. The only expectation is that the page be fully functional without server-side code.

## Benefits

A JAMStack application can be faster and have shorter load times, because there is no waiting for a response from the server. APIs can slow it down, depending on the speed of the response, but overall a JAMStack application tends to be quicker to load and render. A JAMStack application also alleviates the concerns of handling server-side security and database protections. The applications also scale very well, due to the nature of how CDNs and static apps work. But perhaps the most significant benefit is the myriad of hosting options.

A JAMStack application, because it does not require a live server, can be hosted on many platforms. Netlify touts itself as a JAMStack provider (which makes sense, since it's their word), but there are other options as well. My personal preference is GitHub Pages, due to the perks it offers (an unlimited number of free pages, automatic domain routing for all pages, a homepage). The most important part is that these services are often *free*, as the cost to host a static page is significantly less than the cost to host a server-based application. 

## Final Thoughts

The JAMStack term works a little differently than technology stacks like MERN. While this is a brief touch on what a JAMStack is, there is a lot more information out there. I recommend checking out the [official documentation](https://jamstack.org/) if you would like to learn more!