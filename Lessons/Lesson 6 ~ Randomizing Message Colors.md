# Randomizing Message Colors
## Intro
This lesson will show you how to add a random aspect to your code. It will also show you how to create a config file and read information from it. This plugin will require the plugin from lessons 2, 4, and 5.

## Coding
Before we start coding, we're going to modify our plugin to say hello in all 16 colors. Your current code should look like this.
```java
    @EventHandler
    public void onPlayerJoin(PlayerJoinEvent event){
        Player player = event.getPlayer();//Get the player variable stored inside our event

        int i = 0;
        while (i < 10){
            String message = ChatColor.translateAlternateColorCodes('&',"&" + i + "Hello " + player.getName());
            player.sendMessage(message);
            i++;
        }
    }
```

We'll use the static method Integer.toHexString() to convert i into a hexadecimal string (i.e. 0, 1, 2, ..., a, b, c, etc.). We'll also increase the maximum i value to 15.

```java
    @EventHandler
    public void onPlayerJoin(PlayerJoinEvent event){
        Player player = event.getPlayer();//Get the player variable stored inside our event

        int i = 0;
        while (i < 16){
            String itterationAsHex = Integer.toHexString(i);

            String message = ChatColor.translateAlternateColorCodes('&',"&" + itterationAsHex + "Hello " + player.getName());
            player.sendMessage(message);
            i++;
        }
    }
```

Our plugin should now display all colors.

Picture

Now we're going to introduce a random number to decide what color our message is. We'll also change the number of times the message is sent, and store this in a variable. This will allow us to modify the amount of times the messages are sent with a config file.

```java
public class OnPlayerJoin implements Listener {

    public static int amountOfMessages = 5;

    //This variable is created at the class level instead of inside the method because we don't need to make a new random every time a player joins.
    Random random = new Random(); 
    
    @EventHandler
    public void onPlayerJoin(PlayerJoinEvent event){
        Player player = event.getPlayer();//Get the player variable stored inside our event

        int i = 0;
        while (i < amountOfMessages){
            
            String colorCode = Integer.toHexString(random.nextInt(16));
            String message = ChatColor.translateAlternateColorCodes('&',"&" + colorCode + "Hello " + player.getName());
            player.sendMessage(message);
            i++;
        }
    }
}
```

I also changed the string which stores our color code to colorCode. This reflects the change in our code from basing the colorCode from the itteration number of the while loop to a random value.
When we join the server, we should see something like this.

Random colors picture.

I dislike that black was one of the colors displayed. I also dislike the fact that red was used twice. We'll start by keeping track of all the colors we've used, and prevent any color we've already used from being used again.
To do this, we'll use a List. Read **Section 1** (Overview of List collection) on [Codejava](https://www.codejava.net/java-core/collections/java-list-collection-tutorial-and-examples)

Every time onPlayerJoin is called, we'll create a list to keep track of what colors are used. Every time a color is used, we'll add it to the list. We'll also need to make sure colors we use aren't already in the list.


