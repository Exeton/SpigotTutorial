# While loops and Multicolored messages
## Intro
This tutorial will show you how to use loops to send multiple colored messages. This lesson will build off lessons two and four
## Getting Started
Go to your onPlayerJoin event. It should look similar to the following.
```java
    @EventHandler
    public void onPlayerJoin(PlayerJoinEvent event){
        Player player = event.getPlayer();//Get the player variable stored inside our event
        String message = ChatColor.translateAlternateColorCodes('&',"&6Hello " + player.getName());
        player.sendMessage(message);
    }
```

We're going to modify this code to display Hello PoorManSwag, in multiple colors.

![alttext](https://github.com/Exeton/SpigotTutorial/blob/master/LessonPictures/Lesson4-6/Lesson%205%20Result.PNG)

We'll start off by creating something called a while loop. While loops look like this.
```java
while (someCondition){
  //Run the code inside here
}
```

A while loop will start off by checking if some condition is true. If it is, it'll execute the code inside the while loop. After that, it'll check if the condition is true again, if it is, it'll run the code again. It'll keep doing this until the condition is false.
That means your condition is always true, you program will stop responding and either crash or throw an error.

```java
//This will create an error or crash your program
while (true){

}
```

It's possible for while(true) loops not to crash / freeze your program if it's multithreaded, but we won't go over that.

Now what we're going to do is use a while loop to run a block of code multiple times. We'll go over more ways of running blocks of code in the future. If you know how to use a for loop, use that instead.

```java
int i = 0;//Create a number variable and set it to 0
while (i < 10){//Run this code as long as i < 10.
    i = i + 1;
}
```

As you can see, everytime our loop runs, i increases by 1. Eventually i will become equal to 10, and the loop will stop running. If you'd like to challenge yourself, try to use this in your code to send the player 10 messages when they join the server.
The resultant code inside onPlayerJoin should look like.

<details><summary>Finished Code</summary>
<p>

```java
    public void onPlayerJoin(PlayerJoinEvent event){
        Player player = event.getPlayer();//Get the player variable stored inside our event
        String message = ChatColor.translateAlternateColorCodes('&',"&6Hello " + player.getName());
        int i = 0;
        while (i < 10){
            player.sendMessage(message);
            i++;
        }
    }
```

</p>
</details>



Now we can spam players when they join our server, but it looks pretty boring.
![alttext](https://github.com/Exeton/SpigotTutorial/blob/master/LessonPictures/Lesson4-6/Lesson%205%20OneColor.PNG)

We're going to modify our plugin to say greet our players in multiple colors.
To do this, we'll change the color code from &6, to a different number everytime we run through our loop. Just like we can add text to other text, we can add numbers to text. For example

```java
        String a = "hi";//Text
        int b = 2;//Number
        String c = a + b;
        System.out.println(c);
        //output "hi2"
```

Go ahead and change our current code to display text with color codes 0 - 9 (i.e. &0 to &9). You might need to move where the message variable is in the code.


<details><summary>Finished Code</summary>
<p>

```java
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
</p>
</details>


## Result
![alttext](https://github.com/Exeton/SpigotTutorial/blob/master/LessonPictures/Lesson4-6/Lesson%205%20Result.PNG)

## Challenges
1. Modify the plugin from lesson 1 to use a while loop to display "Hello World" to the console 5 times.
