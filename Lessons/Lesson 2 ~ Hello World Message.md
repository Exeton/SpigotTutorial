# Hello World Message
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
The first thing you're going to do is create a new Java class called OnPlayerJoin. It's important not to name this calss OnPlayerJoinEvent because that's the name of the class inside the SpigotAPI that we'll be using. In other words, we'd be creating a class with the same name as a class we're going to be using in our code, which can be confusing.

Pictures of creating class inside the package.

Besides making the event class, there's 3 things you need to do to get your event working.
1. Implement Listener
2. Add an @EventHandler annotation above the method that'll be ran by the event.
3. Register the event

Implementing Listener is easy. Simply add "implements Listener" after your class name. This allows Spigot to know your class has an event inside of it. Your class should look like.

Sample code

Now we'll create another method (another set of instructions) to be run when a player joins. All event methods you create will take in one event paramater which'll information about the event. In our case, our method will take in a PlayerJoinEvent object which will store varriables like a player varriable.


Talk about objects vs classes.

## Debuging

If your event isn't working, it could be for any number of reasons. 
If you forget to implement Listener, Spigot will throw an error when your plugin loads. </br>
If you forget to register the event, the event won't work, but it won't throw an error. </br>
If you forget to add the annotation, it also won't work or give an error. </br>
If the code inside of your event throws an error, an error will display every time the event is run. </br>
