# Hello World Message
## Intro
This tutorial will show you how to create an event which sends a join message to players. You will create a new project before we get started.

## Setup
Create a new project, and create all the files and code needed for plugins. You can review [Creating A Plugin](https://github.com/Exeton/SpigotTutorial/blob/master/Resources/CreatingAPlugin.md) for any steps you've forgotten. Be sure to reload your server, and make sure your plugin is enabled when you run /plugins.

#### Possible Errors
If your plugin isn't enabled, it might be for any number of reasons.

1. Is a jar being created in the output directory you specified. If it isn't, you might not have moved compile output onto your jar file in the artifacts tab of the project structure window (the window opened with ctrl + alt + shift + s).
2. Your plugin.yml might have an error, or it might not be in the src folder (and instead might be in a package).
3. Your Main class doesn't extend JavaPlugin
4. If it isn't any of those reasons, check your server console for an error. If an error appears, be sure to google it.

## Coding
In the last lesson, we added code to onEnable(). In this lesson, we're going to add code inside events. Note: Events allow you to execute portions of code whenever something happens. For example
- When a player joins the server
- When a player dies
- When an entity damages another entity
- When a player moves
- When a player clicks something in their inventory

In our case we're going to use the PlayerJoinEvent, which will provide us information about a player when they join our server. We can use this information to send players messages whenever they join. To get started, create a new Java class called OnPlayerJoin. It's important not to name this calss OnPlayerJoinEvent because that's the name of the class inside the SpigotAPI which will cause naming conflicts. To elobrate, we'd be creating a class with the same name as a class we're going to be using in our code, which we'll avoid for simplicity's sake.

There are 3 things we need to do to get this event working.
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
