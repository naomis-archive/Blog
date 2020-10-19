## Discord Bot: A Quick TypeScript Tutorial

Today I slapped together a small Discord bot to auto-reply when a friend's name was mentioned in a message. While building it, I realised "Hey, this might make a decent tutorial", so here we are. 

Building a Discord bot can be done in a multitude of ways, and there is an abundance of libraries in various languages to facilitate handling the Discord API. For this tutorial we will be using the `discord.js` library and TypeScript. If you have not done so already, you will need to [install node]().

## Setting up the Project

First, create a folder to hold your project. Open your terminal and point the CLI to that folder. 

Next we initialise a node project:
```bash
npm init
```

The CLI will walk you through the process of creating a `package.json` file - for this tutorial, many of the values are negligible. You *will* want to ensure the `entry point` is `index.js`. 

Now we install the necessary `npm` packages. Start with the production packages:
```bash
npm install discord.js typescript dotenv
```

- `discord.js` will handle our connection to the Discord service
- `typescript` needs to be installed to use the language
- `dotenv` is needed to handle the environment variables

Once we have the packages installed, we need to prepare our project for TypeScript.
```bash
tsc --init
```

This command will generate a `tsconfig.json` file which contains the settings for compiling the TypeScript into JavaScript. For this project, you will not need to adjust anything in the file. 

> [!NOTE]
> If you get a `tsc is not a command` type of error, you may need to install TypeScript globally with `npm install -g typescript`.

Great! Now that we have this set, let's make a couple of files. Go ahead and add a file called `.env` and a file called `index.ts` to the root directory of the project.

Our file structure should now look like this:
```
|-/node_modules/
|-.env
|-index.ts
|-package.json
|-package-lock.json
|-tsconfig.json
```

To make things easier, we will now add a couple of `npm` scripts to our `package.json`. Replace the current `scripts` inside that file with:
```json
  "scripts": {
    "build": "tsc",
    "start": "node index.js"
  },
```

The `build` script will compile our TypeScript into JavaScript (using the configuration in `tsconfig.json`) and the `start` script will run our bot once we've written the code!

Before we move on to the code, another quick note: If you plan on committing this project to GitHub you will want to add a `.gitignore` file with the following contents:
```
/node_modules/
.env
*.js
```

The `.env` file will contain our secrets and should NEVER be committed to a repository. The node_modules folder should also never be committed, as this bloats the size of the repository. We are also not committing the compiled JavaScript files. 

## Writing Code!

Alright, let's get to the code! Now all of our work will be done in the `index.ts` file, so go ahead and open that. 

Our first step will be to import the packages we need - the default TypeScript configuration uses `import/export` syntax, rather than the `require/exports` syntax. 

```ts
import { Client, Message } from "discord.js";
import dotenv from "dotenv";
```

Here we have imported the `Client` and `Message` exports from `discord.js`, and the entire `dotenv` module. 

Now we can create our bot! Let's go ahead and declare a couple of variables:
```ts
dotenv.config();
const client = new Client();
const token = process.env.TOKEN;
```

We start by calling the `dotenv.config()` function, which reads our `.env` file and generates environment variables for the secrets within. Then we declare `client` as a `new Client()`. With the `discord.js` library, the `Client` constructor generates a new Discord client that our bot will log in to. Finally we declare `token` with this `process.env.TOKEN` value. This value comes from the `.env` file, which we have not written yet. But that's okay! We can add this when we are ready to run the code. 

Time to write the code for the bot to connect to the Discord server!
```ts
client.login(token)
```

 With this line we are telling the client to log in as the bot user associated with the `token`. We do not have this token yet, but this tutorial will show you how to get one.

We do have a slight problem - this code will not tell us if the bot has successfully connected, and if it fails to connect the process will crash. So we need to add some additional handling here.
```ts
client
  .login(token)
  .then(() => console.log("It's alive!"))
  .catch((err) => console.error(err));
```

Perfect! Now the code will attempt to log in as our bot. If it succeeds, `.then` it will log "It's alive!" to our console so we see the success. If it fails, it will `.catch` the error and print it to our console. 

Our bot might be able to log in, but we also want it to listen for messages. To accomplish this, we will use the `client.on()` method to listen for the `message` event. 
```ts
client.on("message", (message) => {})
```

Now the bot is listening, but it is not going to respond! We need to add some handling in our call back function. The call back function takes an argument `message`, which will be the message that triggered this event. 

So, let's write the code to have the bot listen for messages that say "nhcarrigan". (You can choose whichever name you'd like)
```ts
client.on("message", (message) => {
  if (message.content.includes("nhcarrigan")
}
```

This new logic we've added will listen for any `message` whose `.content` (the text content of the message) `.includes` the string "nhcarrigan". But when the bot catches these messages, it needs to do something with them! Let's polish off this code.
```ts
client.on("message", (message) => {
  if (message.content.includes("nhcarrigan") {
    message.channel.send("Hello nhcarrigan!")
  }
}
```

Great! Now when the bot receives that message, it will locate the `channel` the message came from and `.send` back the string "Hello nhcarrigan!".

We are now ready to test our bot! If you do not have a bot application already, you will need to visit the [Discord Developer Portal](https://discord.com/developers/applications) and create an application. Then, in that application you will create a bot. That bot will have a `token` you need to copy, as we will add this to the `.env` file as:
```
TOKEN="yourtokenhere"
```
> [!WARNING]
> Your token is a password for your bot. NEVER commit it to a repository or post it in a public place.

Make sure to invite your bot into your server!

Time to compile our TypeScript into JavaScript:
```bash
npm run build
```

This command will call the `tsc` command and output a `.js` file for each compiled `.ts` file - you should now see an `index.js` file! This is the file that our next script will look for:
```bash
npm run start
```

If everything is successful, you should see "It's Alive!" printed in your console. Try sending a message in your server that includes the name you chose!

*If you would like to see the code for the bot I mentioned, [the bot is available on GitHub](https://github.com/nhcarrigan/we-love-matt)*