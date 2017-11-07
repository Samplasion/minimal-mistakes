---
title: "My Discord Bot"
date: 2017-11-07 19:39:40 +0100
tags: Discord
categories: Discord
layout: single
comments: true
excerpt: "In this post, I'll show you my first Discord bot, entirely written in JavaScript."
---
{% highlight js linenos %}
const Discord = require("discord.js");
const client = new Discord.Client();
const config = require("./config.json");
const Cleverbot = require("cleverbot-node");
const clbot = new Cleverbot;
clbot.configure({botapi: config.clbotToken});
const fs = require("fs");
const talkedRecently = new Set();
var coin = Math.random(0, 1) + 1 - 1
// We also load the rest of the things we need in this file:
const { promisify } = require("util");
const readdir = promisify(require("fs").readdir);
function clean(text) {
  if (typeof(text) === "string")
    return text.replace(/`/g, "`" + String.fromCharCode(8203)).replace(/@/g, "@" + String.fromCharCode(8203));
  else
      return text;
}

client.on("message", message => {
  if (message.channel.type === "dm") {
    clbot.write(message.content, (response) => {
      message.channel.startTyping();
      setTimeout(() => {
        message.channel.send(response.output).catch(console.error);
        message.channel.stopTyping();
      }, Math.random() * (1 - 3) + 1 * 1000);
    });
  }
});

// This loop reads the /events/ folder and attaches each event file to the appropriate event.
fs.readdir("./events/", (err, files) => {
  if (err) return console.error(err);
  files.forEach(file => {
    let eventFunction = require(`./events/${file}`);
    let eventName = file.split(".")[0];
    // super-secret recipe to call events with all their proper arguments *after* the `client` var.
    client.on(eventName, (...args) => eventFunction.run(client, ...args));
  });
});

client.on("message", message => {
  if (message.author.bot) return;
  if(message.content.indexOf(config.prefix) !== 0) return;

  // This is the best way to define args. Trust me.
  const args = message.content.slice(config.prefix.length).trim().split(/ +/g);
  const command = args.shift().toLowerCase();

  // The list of if/else is replaced with those simple 2 lines:
  try {
    let commandFile = require(`./commands/${command}.js`);
    commandFile.run(client, message, args);
  } catch (err) {
    console.error(err);
  }
});

client.on("ready", () => {
  console.log("I am ready!");
  client.user.setPresence({game: {name: `Help for ${client.channels.size} channels on ${client.guilds.size} servers, for ${client.users.size} users!`, type: 0}});
});

//commands start
client.on("message", (message) => {
  const args = message.content.split(" ").slice(1);
  // Exit and stop if the prefix is not there or if user is a bot
  if (!message.content.startsWith(config.prefix) || message.author.bot) return;
  if (talkedRecently.has(message.author.id))
  return;

// Adds the user to the set so that they can't talk for 2.5 seconds
talkedRecently.add(message.author.id);
setTimeout(() => {
  // Removes the user from the set after 2.5 seconds
  talkedRecently.delete(message.author.id);
}, 2500);

  if (message.content.startsWith(config.prefix + "foo")) {
    message.channel.send("bar!");
  } else

  if (message.content.startsWith(config.prefix + "stoo")) {
    message.channel.send("pid!");
  } else

  if (message.content.startsWith(config.prefix + "help")) {
    message.channel.send({embed: {
      color: 111111,
      author: {
      name: client.user.username,
      icon_url: client.user.avatarURL
    },
    title: "List of Useless Bot's Commands",
    url: "",
    description: "Note: your prefix is " + config.prefix + ".",
    fields: [{
        name: "**VV COMMANDS VV**"
      },
      {
        name: config.prefix + "help",
        value: "This dialogue."
      },
      {
        name: config.prefix + "foo and " + config.prefix + "stoo",
        value: "Responds with _**bar!**_ and _**pid!**_ respectively."
      },
      {
        name: config.prefix + "asl",
        value: "Responds with: _I see you're a value 1 year old value 2 from value 3. Wanna date?_. **Usage: " + config.prefix + "asl age sex location**. _Example: " + config.prefix + "asl 27 male Rome_."
      },
      {
        name: config.prefix + "prefix",
        value: "Sets the prefix. **Usage: " + config.prefix + "prefix {prefix}**"
      },
      {
        name: "```(╯°□°）╯︵ ┻━┻```",
        value: "`┬─┬﻿ ノ( ゜-゜ノ)`. **Usage: (╯°□°）╯︵ ┻━┻**"
      },
      {
        name: config.prefix + "say",
        value: "Repeat something. **Usage: " + config.prefix + "say {something}**"
      }
    ],
    footer: {
      icon_url: "https://cdn.discordapp.com/embed/avatars/4.png",
      text: "© Samplasion | List of Useless Bot's Commands"
    }
    }
    }).catch(console.error);
  }

  if (message.content.startsWith(config.prefix + "prefix")) {
   // Gets the prefix from the command (eg. "!prefix +" it will take the "+" from it)
   let newPrefix = message.content.split(" ").slice(1, 2)[0];
   // change the configuration in memory
   config.prefix = newPrefix;

   // Now we have to save the file.
   fs.writeFile("./config.json", JSON.stringify(config), (err) => console.error);
   message.channel.send("Prefix set to " + newPrefix + ".");
 } else

 if (message.content.startsWith(config.prefix + "eval")) {
  if(message.author.id !== config.ownerID) return;
  try {
    const code = args.join(" ");
    let evaled = eval(code);

    if (typeof evaled !== "string")
      evaled = require("util").inspect(evaled);

    message.channel.send(clean(evaled), {code:"xl"});
  } catch (err) {
    message.channel.send(`\`ERROR\` \`\`\`xl\n${clean(err)}\n\`\`\``);
  }
} else

 if (message.content.startsWith(config.prefix + "asl")) {
 const args = message.content.split(/\s+/g).slice(1);
 let age = args[0]; // yes, start at 0, not 1.
 let sex = args[1];
 let location = args[2];
 message.reply(`I see you're a ${age} year old ${sex} from ${location}. Wanna date?`);
 } else

 if(message.content.startsWith(config.prefix + "kick")) {
   let member = message.mentions.members.first();
   let reason = message.content.split(/\s+/g).slice(2).join(" ");
   member.kick(reason);
 } else

 if(message.content.startsWith(config.prefix + "ban")) {
   let member = message.mentions.members.first();
   let reason = message.content.split(/\s+/g).slice(2).join(" ");
   member.ban(reason);
 } else

 if (message.content.startsWith(config.prefix + "test")) {
 message.channel.send({embed: {
    color: 3447003,
    author: {
      name: client.user.username,
      icon_url: client.user.avatarURL
    },
    title: "This is an embed",
    url: "http://google.com",
    description: "This is a test embed to showcase what they look like and what they can do.",
    fields: [{
        name: "Fields",
        value: "They can have different fields with small headlines."
      },
      {
        name: "Masked links",
        value: "You can put [masked links](http://google.com) inside of rich embeds."
      },
      {
        name: "Markdown",
        value: "You can put all the *usual* **__Markdown__** inside of them."
      }
    ],
    timestamp: new Date(),
    footer: {
      icon_url: client.user.avatarURL,
      text: "© Example"
    }
  }
})} else

  if (message.content.startsWith(config.prefix + "about")) {
  message.channel.send({embed: {
     color: 3447003,
     author: {
     name: "About Page",
     icon_url: client.user.avatarURL
   },
   title: "About Useless Bot",
   description: "Created with Discord.js.",
   fields: [{
       name: "Created by Samplasion",
       value: "[My Website](samplasion.github.io)."
     }
   ],
   footer: {
     icon_url: client.user.avatarURL,
     text: "© Samplasion"
   }
 }
  })} else

  if (message.content.startsWith("(╯°□°）╯︵ ┻━┻")) {
    message.channel.send("┬─┬﻿ ノ( ゜-゜ノ)")
  }
});

//commands end

client.login(config.token);
{% endhighlight %}
That's my Discord bot's `mybot.js` file. You can invite your bot to your server [by clicking here](https://discordapp.com/oauth2/authorize?&client_id=352864830794891267&scope=bot). {% capture notice %}BTW, on Discord I'm [samplasion★®#7901](https://discordapp.com/channels/@me){% endcapture %}
<div class="notice notice--success">{{ notice | markdownify }}</div>
