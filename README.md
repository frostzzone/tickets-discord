<div align="center">
  <br />
  <p>
    <a href="https://www.npmjs.com/package/tickets-discord"><img src="https://img.shields.io/npm/v/tickets-discord.svg?maxAge=3600" alt="npm version" /></a>
  </p>
</div>

# Example 🔍
```js
let {
        Discord,
        Client,
        MessageEmbed,
        MessageButton,
        MessageActionRow,
        Intents,
        Permissions,
        MessageSelectMenu
    } = require("discord.js")
    
    const client = new Discord.Client({
        intents: [Object.values(Discord.Intents.FLAGS).reduce((acc, p) => acc | p, 0)]
    });
    
    client.login("TOKEN")
    
    const ticket = require('tickets-discord');
    
    ticket.start(client, "MONGODB url", true/false) //defined client, mongodb url 
    //the true parameter is logs parameter (logs = true/false)

    client.on('messageCreate', async (message) => {
    if (message.content.startsWith('n!ticket')) {
        ticket.setup(message, message.mentions.channels.first().id);
        //you can use parent id here also (optional)
        ticket.setup(message, message.mentions.channels.first().id, "Parent ID");
    }
    if (message.content.startsWith('n!close')) {
        ticket.close(message.channel);
    }
    if (message.content.startsWith('n!archive')) {
        ticket.archive(message.channel);
    }
    if (message.content.startsWith('n!unarchive')) {
        ticket.unarchive(message.channel);
    }

});
```

# Setup 🎟

## Example in detail ✔
### Declaration 📢
```js
const ticket = require('tickets-discord');

//Login with MongoDB/Local DB
ticket.start(client, "URL", true/false) //client
//the true/false parater triggers logs!
```
You can use `local` instead of a mongodb url to make a local DB.

Example 
```js
const ticket = require('tickets-discord');

//Login with MongoDB/Local DB
ticket.start(client, "local", true/false) //client
//the true/false parater triggers logs!

//This will make a local quickdb database!
```
### Make ticket 🎫

```js
ticket.setup(message/interaction, channelID)//message, ticket setup channel id
```
### Archiving a ticket 🎫
The button archives the ticket also you can use 

```js
ticket.archive(messsage.channel) //message channel parameter
```

### Unarchiving a ticket 🎫

```js
ticket.archive(messsage.channel) //message channel parameter
```
### Closing a ticket 🎫
Genarally the close button is already given in this ticket welcome and also you can delete a ticket by using.

```js
ticket.close(message.channel) //the message channel parameter
```

# Whats new in v4 🎉
1. Events 
2. Bug Fixes