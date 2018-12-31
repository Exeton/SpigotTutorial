# Logging Events
## Intro
This lesson will introduce you to logging. Logging allows you to find errors in your code quickly, and is makes it significatly easier to fix bugs. We'll be using the plugin from lesson two in this lesson.

## What is Logging
Logging is when your code writes down information about itself. This can include values of variables, information of where the program is in the code, and other useful pieces of information.

## Example Setup
In this lesson, we'll look into logging to tell us why our event isn't working. The example used is simple so it's easy to understand.
We'll start off by modifying our event so it doesn't work

Go to your main class, and comment out the code used to register our event from lesson two. This can be done with two slashes //.

```java 
public class HelloWorld extends JavaPlugin {

    @Override
    public void onEnable() {

        //Create a plugin manager object. This can be used to register all your events.
        //PluginManager pluginManager = Bukkit.getPluginManager();
        //pluginManager.registerEvents(new OnPlayerJoin(), this);
    }
}

```
Modify your onPlayerJoin method in your OnPlayerJoin class to the following.

```
    @EventHandler
    public void onPlayerJoin(PlayerJoinEvent event){
        Player player = event.getPlayer();//Get the player variable stored inside our event
        
        if (player.getName().equalsIgnoreCase("Notch")){
            player.sendMessage("Hello Player");
        }
    }
```

This code includes an if statement. We'll spend more time on these later. Put simply, they check the criteria inside the parenthes (), and if it's true, they run the following block of code inside the curly brackets {}. This code will check if the player's name is Notch, and if and only if it's Notch will it display "Hello Player"
After this, build your plugin (Build dropdown >> Build Artifacts >> Build), reload your server, and ensure that your server doesn't send you "Hello Player".
## Fixing the plugin
By undoing the changes we just made, we can easily fix our plugin (so that it says Hello Player whenever a player joins). We're going to use logging to fix our plugin. To do this, we'll call Bukkit.getLogger().info("Our Message");

We'll start off by adding a log message inside our onPlayerJoin method to see if the event is called.

```java
    @EventHandler
    public void onPlayerJoin(PlayerJoinEvent event){

        Bukkit.getLogger().info("On Player Join called");
        
        Player player = event.getPlayer();//Get the player variable stored inside our event
        if (player.getName().equalsIgnoreCase("Notch")){
            player.sendMessage("Hello Player");
        }
    }
```
Build your artifacts and reload your server then connect to your server. Look inside your server console, it shouldn't say "On Player Join called".
This means we messed up registering our event (we forgot the @EventHandler annotation, didn't register the event, or didn't implement Listener). Go to your main class, and uncomment the code used to register your event. Build your artifacts and reload. When you connect to your server, it should say On Player Join called.


![alttext](https://github.com/Exeton/SpigotTutorial/blob/master/LessonPictures/Lesson3/OnPlayerJoin%20called.PNG)

Our event still doesn't do what we want, because when we join the server it doesn't say Hello Player. Now we'll put a log message inside our if statement in onPlayerJoin to see if the code inside the if statement is ever run.

```java
    @EventHandler
    public void onPlayerJoin(PlayerJoinEvent event){

        Bukkit.getLogger().info("On Player Join called");

        Player player = event.getPlayer();//Get the player variable stored inside our event
        if (player.getName().equalsIgnoreCase("Notch")){
            Bukkit.getLogger().info("Player name is Notch");
            player.sendMessage("Hello Player");
        }
    }
```

Build the plugin, reload your server, and check if the server console says "Player name is Notch" when you join. It shouldn't. This tells us that the code inside our if statement is never run. This is useful in more complicated secenarios when we're not sure wether the code in our if statements is being called.
Remove the if statement, but keep the logging and message being sent to the player.

```java
    @EventHandler
    public void onPlayerJoin(PlayerJoinEvent event){

        Bukkit.getLogger().info("On Player Join called");

        Player player = event.getPlayer();//Get the player variable stored inside our event
        Bukkit.getLogger().info("Player name is Notch");
        player.sendMessage("Hello Player");
    }
```

Now your plugin log two messages when the player joins, and send a message to players that join.


## Challenges
1. Create a new event (you can reffer to lesson 2). It should be an EntityDamagedByEntityEvent. Log "Entity Damaged" to the console every time the event is called.
