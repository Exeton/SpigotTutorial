# Hello World Console
## Intro
This tutorial will show you how to create a Intellij project and setup a spigot plugin. This lessons expects you to have installed Intellij and have a working Spigot server.

## Creating a project
After opening intellij, you'll want to create a new project. You can do that from both inside intellij, and from the welcome to intellij screen.

![alt text](https://github.com/Exeton/SpigotTutorial/blob/master/LessonPictures/Lesson1/Create%20Project.PNG)
![alt text](https://github.com/Exeton/SpigotTutorial/blob/master/LessonPictures/Lesson1/Create%20Project%202.PNG)

A GUI (like shown below) will open. You'll want to select java project, click next, click next, and name your project before clicking finish.

![alt text](https://github.com/Exeton/SpigotTutorial/blob/master/LessonPictures/Lesson1/Project%20Type.PNG)
![alt text](https://github.com/Exeton/SpigotTutorial/blob/master/LessonPictures/Lesson1/Name%20Project.PNG)

After creating your project, Intellij's main window will open.
![alt text](https://github.com/Exeton/SpigotTutorial/blob/master/LessonPictures/Lesson1/Main%20Window.PNG)

## The Four Parts of a Spigot plugin
In order to create a spigot plugin, you need to do four things.

1. Add Spigot as a libary
2. Create an artifact (the jar your plugin will create)
3. Create a plugin.yml
4. Create your main class


## Adding Spigot

The first two are very simple. Inside Intellij, press Ctrl + Alt + Shift + S. Click on the libaries tab, then the +.

![alt text](https://github.com/Exeton/SpigotTutorial/blob/master/LessonPictures/Lesson1/Project%20Structure%20Window.PNG)
![alt text](https://github.com/Exeton/SpigotTutorial/blob/master/LessonPictures/Lesson1/Java%20Libary.PNG)
![alt text](https://github.com/Exeton/SpigotTutorial/blob/master/LessonPictures/Lesson1/Spigot%20lib.PNG)

## Creating an Artifact

Click on the Artifacts tab. Add a new empty jar. (From dependiceys works too, but you'll have to remove the spigot.jar from output layout). Change the jar name, output path (I recommend to your spigot/plugins folder), and drage the 'Hello World' compile output into your jar.

![alt text](https://github.com/Exeton/SpigotTutorial/blob/master/LessonPictures/Lesson1/Adding%20Artifact.PNG)
(https://github.com/Exeton/SpigotTutorial/blob/master/LessonPictures/Lesson1/Artifact%20Creation.PNG)


If your jar does not get created, you messed up a step here. (Check your output path, and that you have 'Hello World' compile output on the left side of your output layer).

Once you're done, click OK.
![alt text](https://github.com/Exeton/SpigotTutorial/blob/master/LessonPictures/Lesson1/OK%20picture.PNG)

## Creating plugin.yml

To create your plugin.yml file, goto your src folder, right click it, then go new >> File. Name it plugin.yml.

Create file picture
Not filled picture


You might not be able to view this file inside intellij. If you can't, you can open it notepad, or notepad++. Hashtags in this file are comments and won't be parsed by spigot.

Filled picture


We'll come back to this file to add the location of our main class.

## Creating your Main class

To organise classes in java, you can use packages. These are basically folders. It's common pratice to name packages as your domain name reversed. I own the domain fireflower.online, so my package would be fireflower.online. After this, and the project name (HelloWorld). All words in package names should be lower case, and words should be seperated with an underscore. I would call this project online.fireflower.hello_world

After creating your package, create a class called HelloWorld. Class names should start with a capital letter, and every new word in the class name should start with a capital letter. For example the "My sample class name" would be "MySampleClassName".


Now you're going to make your class extend java plugin. We'll cover what this means later. If you're getting an error in Intellij, you can press Alt + Enter and then click import class to import the JavaPlugin class.
After importing the class, add the following code to your Main class (your HelloWorld class).


Picture

So what does this mean? There's a lot of new info to take in, but we'll go over the onEnable() method you just added in.
The onEnable() method has a lot of parts. It starts off with an @Override annotation. We're not going to worry about this. Following that is the keyword public, the keyword void, the method name - onEnable, some parentheses, and then a pair of curly brackets. Here's what all that means.

public - This describes the accessiability of the method. Public methods can be accessed from inside other classes while private methods cannot.
void - This desribes the return type of the method. Some methods, like an addition method give back numbers. Methods which return void don't return anything.
onEnable - This is the name of the method. It's used in other parts of the code to invoke the method.
() - Inside here are where method inputs (paramaters) go. And addition method would take in two numbers as paramaters.
{} - Inside here is where all the instructions of the method go. Any code inside here will be executed when the method is executed.

Not all of that will make sense right now, but over time all these characteristics will start to make sense.

We've now got most of the code we need in order to run our plugin. The one final thing to do is call Bukkit.getLogger().info(); inside our onEnable method. info (sic) is a method inside of the Logger class. This method takes in a text varriable and displays it to the console.

To do this, we can either pass in an existing varriable, or we can create a new text varriable and pass it in. You can see both methods below.

## Adding our main class to our config

Before we can create our jar file, we have to add our main class location to our plugin.yml. This should be all the folders that go upto your main class, and your Main class. For me it's online.fireflower.hello_world.HelloWorld which is package1.package2.MainClassName

Finished config picture

## Building artifacts
Building artifacts is pretty simple. Click on the build tab, then build articafts >> build.

Pictures

## Challenges
Remember: Don't stress if you can't get these. Be sure to come back to this project if you can't figure them out. You might need to play around to get these working.

1. (Modify the plugin) Change the message displayed on the Console.
2. (Modify the plugin) Send the Hello World message 5 times.
3. (Answer the question) What is the keybind to open the Project Structure GUI?
