# Hello World Console

## public void onEnable()

So what does this mean? There's a lot of new info to take in, but we'll go over the onEnable() method you just added in.
The onEnable() method has a lot of parts. It starts off with an @Override annotation. We're not going to worry about this. Following that is the keyword public, the keyword void, the method name - onEnable, some parentheses, and then a pair of curly brackets. Here's what all that means.

**public** - This describes the accessiability of the method. Public methods can be accessed from inside other classes while private methods cannot. <br/>
**void** - This desribes the return type of the method. Some methods, like an addition method give back numbers. Methods which return void don't return anything. <br/>
**onEnable** - This is the name of the method. It's used in other parts of the code to invoke the method. <br/>
**()** - Inside here are where method inputs (paramaters) go. And addition method would take in two numbers as paramaters. <br/>
**{}** - Inside here is where all the instructions of the method go. Any code inside here will be executed when the method is executed. <br/>

Not all of that will make sense right now, but over time all these characteristics will start to make sense.

We've now got most of the code we need in order to run our plugin. The one final thing to do is call Bukkit.getLogger().info(); inside our onEnable method. info (sic) is a method inside of the Logger class. This method takes in a text varriable and displays it to the console.

To do this, we can either pass in an existing varriable, or we can create a new text varriable and pass it in. You can see both methods below.

![alt text](https://github.com/Exeton/SpigotTutorial/blob/master/LessonPictures/Lesson1Part2/HelloWorld%20Finished.PNG)

## Results
Once you've built your artifacts, you server should display "Hello World" when your plugin is loaded. If Spigot throws an error this could mean a varity of things. For example an InvalidPluginDescription error means that you messed up in your plugin.yml file. Look for the error message and google the error.

![alt text](https://github.com/Exeton/SpigotTutorial/blob/master/LessonPictures/Lesson1Part2/Result.PNG)

## Challenges
Remember: Don't stress if you can't get these. Be sure to come back to this project if you can't figure them out. You might need to play around to get these working.

1. (Modify the plugin) Change the message displayed on the Console.
2. (Modify the plugin) Send the Hello World message 5 times.
3. (Answer the question) What is the keybind to open the Project Structure GUI?
