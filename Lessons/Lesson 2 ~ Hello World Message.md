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

![alttext](https://github.com/Exeton/SpigotTutorial/blob/master/LessonPictures/Lesson2/ImplementsListener.PNG)

Now we'll create another method (another set of instructions) to be run when a player joins. All event methods you create will take in one event paramater which'll information about the event. In our case, our method will take in a PlayerJoinEvent object which will store varriables like a player varriable. This method must be labeled with @EventHandler. This tells Spigot that this method is what should be called when a PlayerJoinEvent is fired.

```java
public class OnPlayerJoin implements Listener {

    @EventHandler
    public void onPlayerJoin(PlayerJoinEvent paramater){

    }
    
}

```

As you can see, out method takes in a paramater called "paramater". This paramater is an object with the type "PlayerJoinEvent". This object will be different every time a player joins the server, or in other words, we'll recieve a new paramater varriable with a new player name, a new join message, etc. On the other hand, the class will remain constant when players join. We'll always recieve a join message variable, a player name variable, etc., just with different values.

Before we add the code to send the player a message, we'll rename our PlayerJoinEvent object from paramater to event so that our code is easier to understand.

```java
public class OnPlayerJoin implements Listener {

    @EventHandler
    public void onPlayerJoin(PlayerJoinEvent event){

    }

}
```


To send the Player a message, we'll get a player varriable and then call the sendMessage method. Be to import any new classes (Press alt + enter when hovering over a class that needs to be imported)

```java
    @EventHandler
    public void onPlayerJoin(PlayerJoinEvent event){

        Player player = event.getPlayer();//Get a player object from our event object
        player.sendMessage("Hello Player");

    }
```

Note: We have to use a player object to call player.sendMessage(). For example the following code won't work because we're not refference a specific player.

```java
    //This code won't work

    @EventHandler
    public void onPlayerJoin(PlayerJoinEvent event){
        Player.sendMessage("");
    }
 ```

After adding the player.sendMessage("Hi") code, we need to register our event. We'll register the event inside our Main file in onEnable(). To do this, we'll tell Bukkit's pluginManager to register our event. We'll need to pass in an onPlayerJoin object, and a main class object. Because we're running this code inside of our main class, we can pass our Main class as a paramater into the method using the "this" keyword.

```java
public class HelloWorld extends JavaPlugin {

    @Override
    public void onEnable() {

        //Create a plugin manager object. This can be used to register all your events.
        PluginManager pluginManager = Bukkit.getPluginManager();
        pluginManager.registerEvents(new OnPlayerJoin(), this);
    }
}
```

Remember: Your class might not be named HelloWorld. If you change the name of the class inside the code, but don't change the file name, Intellij will throw an error. If this is happening, don't copy and paste all the code into your Main class, just the code inside of onEnable().

## Results
We're done coding. Be sure to build your artifact (Click the build dropdown then Build Artifacts > Build. Your plugin should send you a message when you join the server that says HelloPlayer. If it doesn't, check the debugging section below and try to figure out what you did wrong.

![alttext](https://github.com/Exeton/SpigotTutorial/blob/master/LessonPictures/Lesson2/Results.PNG)

## Debuging

If your event isn't working, it could be for any number of reasons. 
If you forget to implement Listener, Spigot will throw an error when your plugin loads. </br>
If you forget to register the event, the event won't work, but it won't throw an error. </br>
If you forget to add the annotation, it also won't work or give an error. </br>
If the code inside of your event throws an error, an error will display every time the event is run. </br>

## Challenges
[Read - Classes vs Objects](https://www.javatpoint.com/difference-between-object-and-class)
