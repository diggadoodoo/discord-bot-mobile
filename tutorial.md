# How to make a Discord Bot on mobile

It may seem hard but it isn't, follow the steps slowly and we'll get there 

> I used to use this method when I did not have a PC avaliable, it isn't the best, I'd suggest only you use it if you're *that desperate*, if you want to make a Discord bot the easy way **get a PC**!!

---
# WARNING: This works on android, I am not sure if the same will apply on IOS


## Requirements 
* Puffin browser
* A [Glitch](https://glitch.com) account
* Some sort of mobile code editor, they are easy to find

### Step 1, making a glitch account
Make a glitch account, it is very very very easy to do so. You can even use your github account to create one.

### Step 2, make your app on glitch
Make an app and select the `hello-express` one which is a node type. Delete all other files **except for the `package.json` and `server.js` ones**

### Step 3, adding discord.js
Go to `package.json` and search for `discord.js` in the library search bar  and add it to your project

### Step 4, making our config file
Before you add your bot's token, **make sure your project is private**. Make a `config.json` file containing the following code:

```json
{
"token": "put_your_bots_token_here",
"prefix": "!"
}
```

### Step 5, adding the bots code
Insert this code to get your bot running, for now this will only have a ping command, if you'd like a more exciting bot replace your server.js code with the code from [my open source bot](https://github.com/fifthsonofole/discord.js-moderation-bot)

```js
const Discord = require("discord.js");
const client = new Discord.Client();
const config = require("./config.json");


client.on("ready", () => {
    console.log("I am ready!");
});

client.on("message", message => {
    if (message.author.bot) return;  
    if (message.content.indexOf(config.prefix) !== 0) return;
    
    const args = message.content.slice(config.prefix.length).trim().split(/ +/g);
    const command = args.shift().toLowerCase();

    if (command === "ping") {
        message.channel.send("Pong")
    }
});

client.login(config.token);
```

### Step 6, running your bot
Now this is where Puffin gets involved, Puffin will help us a lot. Open your glitch console **on Puffin** and press the keyboard icon. Your keyboard should appear (We use Puffin so we have this ability, Chrome won't let us write in the console :P) and now write `node server`.

### Step 7, finished!
Well done, you have successfully made a Discord bot on your mobile device!


---

### I wrote this very late at night, if I am not clear enough, contact me via my [discord server](https://discord.gg/J3pSg6R) and I will explain better to you.
