# Configs and Selecting Colors
## Intro
This lesson will cover creating configs. We'll modify the plugin we've been working on to only display the colors stated in the config file.

## Coding

We'll pick up where we left off last time. Your OnPlayerJoin calss should look like this.

```java
public class OnPlayerJoin implements Listener {

    public static int amountOfMessages = 5;

    //This variable is created at the class level instead of inside the method because we don't need to make a new random every time a player joins.
    Random random = new Random();

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
}
```

We'll come back to this later. For now we're going to focus on our Main class (our HelloWorld class).

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

We'll start by adding a new method. Remember methods are sets of insturctions that are run every time our method is called. This method won't return anything, so it'll be of type void.

```java
public class HelloWorld extends JavaPlugin {

    @Override
    public void onEnable() {

        //Create a plugin manager object. This can be used to register all your events.
        PluginManager pluginManager = Bukkit.getPluginManager();
        pluginManager.registerEvents(new OnPlayerJoin(), this);
    }
    
    
    public void loadConfig(){
        
    }
    
}
```

Now we'll call our loadConfig method from inside onEnable. This means that every time our plugin is loaded, the code inside loadConfig() will run. Because this method is inside our class. Unlike sending a player a message, which was player.sendMessage(), we can call loadConfig() without a helloWorld object because the method is being called by another method inside the class.

```java
public class HelloWorld extends JavaPlugin {

    @Override
    public void onEnable() {

        //Create a plugin manager object. This can be used to register all your events.
        PluginManager pluginManager = Bukkit.getPluginManager();
        pluginManager.registerEvents(new OnPlayerJoin(), this);
        loadConfig();
    }


    public void loadConfig(){

    }

}
```

Now that we've created our method, we'll add the code to load the config. Read [working with configs](https://www.spigotmc.org/wiki/config-files/). **You don't have to read using custom config files.** Now we'll start by calling saveDefaultConfig(). Remember from [the spigot article](https://www.spigotmc.org/wiki/config-files/), this "will not overwirte an existing config file".

```java 
public class HelloWorld extends JavaPlugin {

    @Override
    public void onEnable() {

        //Create a plugin manager object. This can be used to register all your events.
        PluginManager pluginManager = Bukkit.getPluginManager();
        pluginManager.registerEvents(new OnPlayerJoin(), this);
        loadConfig();
    }


    public void loadConfig(){
        saveDefaultConfig();
    }

}
```

Now we need to add a new config file. This file needs to go in the root of the src folder. If it goes inside your package, it won't work. Right click the src folder >> new >> file.

Creating Config Picture.

Config location Picture

We'll add an option to configure the ammount of messages sent, an option to configure the message, and an option to configure what colors those messages can be.

```yaml
NumberOfMessages: 5

# %Player% will be replaced by the player joining the server's name
Message: "Hello %Player%"

# 0 to 15 is allowed. 10 = a, 11 = b, 15 = f
AllowedColorValues:
  - 0
  - 1
  - 2
  - 3
  - 4
  - 5
  - 6
  - 7
  - 8
  - 9
  - 10
  - 11
  - 12
  - 13
  - 14
  - 15
```

Build and reload your plugin. A folder called HelloWorld should be created inside your plugins folder. It should have a config file inside of it.

Config folder picture

Now that our config is saved, we're going to access the values in it to configure how many messages are sent, what color messages can be sent, and what the message should look like.
