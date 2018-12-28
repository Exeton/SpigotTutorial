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

To organise classes in java, you can use packages. These are similar to folders. It's common pratice to name packages as your domain name reversed. I own the domain fireflower.online, so my package would be fireflower.online
