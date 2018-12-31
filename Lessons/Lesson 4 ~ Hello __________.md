# Hello _______________
## Intro
In this lesson, we'll make a plugin which will greet players joining your server. For example if Notch joins your server, the server will send a "Hello Notch" message. This lesson will use the plugin from lesson two.

## Getting Started
The first thing we'll remove the logging messages added to onPlayerJoin in lesson three. This'll make our code easier to read.

```java
public class OnPlayerJoin implements Listener {

    @EventHandler
    public void onPlayerJoin(PlayerJoinEvent event){
        Player player = event.getPlayer();//Get the player variable stored inside our event
        player.sendMessage("Hello Player");
    }
}
```

Now that we've removed the extra logging messages, we're going to change our method so that "Hello Player" is stored inside a varriable. We can do this by creating a String variable. Strings are used to store text.

```java
    @EventHandler
    public void onPlayerJoin(PlayerJoinEvent event){
        Player player = event.getPlayer();//Get the player variable stored inside our event
        String message = "Hello Player";
        player.sendMessage(message);
    }
```

Before sending our message, we're going to modify it. When modifying Strings, you can use the + operator. For example, the following code would output "Hi Bob" to the console.

```java
String a = "Hi ";
String b = "Bob";
String c = a + b;
System.out.println(c);
//Output: Hi Bob
```

In our case we're going to use player.getName() as one of our strings. Using the information above, modify your plugin to send "Hello YourMinecraftName" every time you join the server. Be sure to test your plugin to make sure it works.

## Using Chat Colors
One very useful aspect of making your plugin look professional is chat colors. Chat colors are very easy to use, and you can use the method ChatColor.translateAlternateColorCodes() to add chat colors to your text. This method is a static method. Static methods don't require you to have an object. Sending a message to a player is an example of a non static method, because you need to know what player to send the message to. Bukkit.getLogger() is an example of a static method because you don't need an instance of the Bukkit class. This is because Bukkit only uses one Logger object to log information to the console.

ChatColor.translateAlternateColorCodes() is also a static method, because the only relevant data to adding chat colors to text is the text itself, and what symbol is used to denote colorcodes. We'll use & to denote colorcodes.

This method will also return a String (text) which means we can set our message varriable equal to the result of ChatColor.translateAlternateColorCodes().

```java
    @EventHandler
    public void onPlayerJoin(PlayerJoinEvent event){
        Player player = event.getPlayer();//Get the player variable stored inside our event
        String message = "&6Hello Player";
        String coloredMessage = ChatColor.translateAlternateColorCodes('&', message);
        player.sendMessage(coloredMessage);
    }
```
As you might've noticed ChatColor.translateAlternateColorCodes takes in two paramaters (or inputs). It requires one character which is essentially one letter / number / symbol (i.e. curly brackets are symbols). It also requires the text to be modified, which is our message variable. The method takes in both these inputs, and returns back a String (text) varriable which we can store and send to the player. Another way to write this would be.

```java
    @EventHandler
    public void onPlayerJoin(PlayerJoinEvent event){
        Player player = event.getPlayer();//Get the player variable stored inside our event
        String message = ChatColor.translateAlternateColorCodes('&',"&6Hello Player");
        player.sendMessage(message);
    }
```

Be sure to modify this so it says Hello YourUsername instead of Hello Player.

## Result
After finishing your plugin, you should get a message like this when you join your server.
![alttext](https://github.com/Exeton/SpigotTutorial/blob/master/LessonPictures/Lesson4-6/Lesson%204%20Result.PNG)

## Challenges
Remake the first plugin from scratch (it should say Hello World when you start up your server). Give it a shot before refferencing the first plugin. It's a lot to remember, so you'll probably need to. Don't forget the 4 parts of setting up a plugin. Be sure to name your package appropriately.
