# Hello World Player
## Intro
This tutorial will show you how to create an event and send messages to players. In this lesson, you will create a new project before we get started.

## Setup
For this plugin, you'll need to create a new project named Hello Player using the four steps of plugin creation.
1. Add Spigot as a libary
2. Create an artifact (the jar your plugin will create)
3. Create a plugin.yml
4. Create your main class
You will probably need to look back at the first tutorial to remember how to do these steps. Although you can just add code to the last plugin instead of creating a new project, it's good pratice to make a new one.

## Before Coding
Before we start coding, build your plugin. Then run your server and type /plugins. Ensure that your plugin is Green and on the list of enabled plugins.
If your plugin isn't green, check the console for errors. Some possible errors include:
1. Your Main class doesn't extend JavaPlugin
2. There's an error in your plugin description

## Coding
Now that we know your plugin works, we can add an events. Events allow you to execute portions of code whenever something happens. For example
- When a player joins the server
- When a player dies
- When an entity damages another entity
- When a player moves
- When a player clicks something in their inventory

In our case we're going to use the PlayerJoinEvent, which will provide us information about a player when they join our server.

