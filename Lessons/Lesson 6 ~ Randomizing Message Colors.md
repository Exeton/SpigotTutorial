# Randomizing Message Colors
## Intro
This lesson will show you how to add a random aspect to your code. This lesson will also cover Lists. This plugin will require the plugin from lessons 2, 4, and 5.

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

Now we're going to introduce a random number to decide what color our message is. We'll also change the number of times the message is sent, and store this in a variable. This will allow us to modify the amount of times the messages are sent with a config file in the future.

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

I dislike the fact that red was used twice, so we'll add a feature to prevent duplicate colors. We can do this by by keeping track of all the colors we've used, and prevent any color we've already used from being used again.
To do this, we'll use a List. Read **Section 1** (Overview of List collection) on [Codejava](https://www.codejava.net/java-core/collections/java-list-collection-tutorial-and-examples)

Every time onPlayerJoin is called, we'll create a list to keep track of what colors are used. Every time a color is used, we'll add it to the list. We'll also need to make sure colors we use aren't already in the list. We can acomplish this with a do while loop. Do while's aren't used nearly as much as while loops. They function pretty similarly. While a while loop starts by checking if a condition is true, then runs code as long as that condition stays true, a do while loop will start by running code, and stop running if the condition is false. This means that do while loops will always run at least once. For example.

```java
            while (false){
                System.out.println("Code ran");
                //Output: No output
            }

            do {
                System.out.println("Code ran");
                //Output: Code ran
            } while (false);
```

In this case the while loop outputted "Code ran" 0 times, and the do while outputted it 1 time.

We'll start by creating a list of used color codes, and then run a do while loop to ensure the color code isn't already in the list.

```java
    @EventHandler
    public void onPlayerJoin(PlayerJoinEvent event){

        List<Integer> usedColorCodes = new LinkedList<>();
        Player player = event.getPlayer();//Get the player variable stored inside our event

        int i = 0;
        while (i < amountOfMessages){

            int nextColorCode = 0;
            do {
                nextColorCode = random.nextInt(16);
            } while (usedColorCodes.contains(nextColorCode) == true);

            String colorCode = Integer.toHexString(nextColorCode);
            String message = ChatColor.translateAlternateColorCodes('&',"&" + colorCode + "Hello " + player.getName());
            player.sendMessage(message);
            i++;
        }
    }
```

We also need to add the color code to the list of used color codes.

```java
    @EventHandler
    public void onPlayerJoin(PlayerJoinEvent event){

        List<Integer> usedColorCodes = new LinkedList<>();
        Player player = event.getPlayer();//Get the player variable stored inside our event

        int i = 0;
        while (i < amountOfMessages){

            int nextColorCode = 0;
            do {
                nextColorCode = random.nextInt(16);
            } while (usedColorCodes.contains(nextColorCode) == true);

            String colorCode = Integer.toHexString(nextColorCode);
            String message = ChatColor.translateAlternateColorCodes('&',"&" + colorCode + "Hello " + player.getName());
            player.sendMessage(message);
            i++;
            usedColorCodes.add(nextColorCode);
        }
    }
```

This should prevent repeats. Our join messages should look like this.

Random No dups Picture.

## Challenges

1. As a challenge, figure out what would happen if we used a while loop instead of a do while. If you can't figure it out, try joining your server multiple times with both, and look at what colors are being used. Here is what the code would look like without a do while

```java
    @EventHandler
    public void onPlayerJoin(PlayerJoinEvent event){

        List<Integer> usedColorCodes = new LinkedList<>();
        Player player = event.getPlayer();//Get the player variable stored inside our event

        int i = 0;
        while (i < amountOfMessages){

            int nextColorCode = 0;
            while (usedColorCodes.contains(nextColorCode) == true) {
                nextColorCode = random.nextInt(16);
            }

            String colorCode = Integer.toHexString(nextColorCode);
            String message = ChatColor.translateAlternateColorCodes('&',"&" + colorCode + "Hello " + player.getName());
            player.sendMessage(message);
            i++;
            usedColorCodes.add(nextColorCode);
        }
    }
```

