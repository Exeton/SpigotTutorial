# CreatingAPlugin

## Intro
Getting started with spigot is very easy. Simply open Intellij, and follow these 5 steps.

1. Create a project.
2. Tell Intellij where your spigot.jar is.
3. Tell Intellij where to put your finished plugin.
4. Create your Main class (classes are places where you can put code)
5. Create your plugin.yml (a file containing information like the name and version of your plugin)


## Creating a project
When you're working on a project, Intellij will automatically reopen that project every time you reopen Intellij. This means when you're creating a new project, your Intellij will look like on of the following.
<br>

#### Case A
If you're in the welcome to Intellij window, simply click "Create New Project"
![alt text](https://github.com/Exeton/SpigotTutorial/blob/master/LessonPictures/Lesson1/Create%20Project.PNG)


#### Case B
If you have a selected project, go to the top left corner and click File. A dropdown will open. Hover over New, and click Project.
![alt text](https://github.com/Exeton/SpigotTutorial/blob/master/LessonPictures/Lesson1/Create%20Project%202.PNG)


#### Adding project info
A new window will now open. On the first page select the Java Project type. Click Next to go to the next page. You won't need to do anything on this page. Click Next again to go to the final page. Name your project HelloWorld (if you're creating the plugin in lesson 1), then click Finish.

<details><summary>GIF</summary>

![alt text](https://github.com/Exeton/SpigotTutorial/blob/master/LessonPictures/Lesson1/Project%20Creation.gif)

</details>


## Tell Intellij where your spigot.jar is
This step is very easy. Press Ctrl + Alt + Shift + S simultaneously to open the Project Structure Window. Click the Libaries tab in this window, and then click the + to add a new libary. 

<br>
Note: Adding Libaries allows you to use other peoples code. For example, using World Edit as a libary allows you to reuse WorldEdit's code for copy and pasting regions in your own code. In our case, we'll be adding Spigot.jar as a libary, this will allow us to use Spigot's code for features like sending player's messages.

<details><summary>Adding Libary Pictures</summary>

![alt text](https://github.com/Exeton/SpigotTutorial/blob/master/LessonPictures/Lesson1/Project%20Structure%20Window.PNG)
![alt text](https://github.com/Exeton/SpigotTutorial/blob/master/LessonPictures/Lesson1/Java%20Libary.PNG)
![alt text](https://github.com/Exeton/SpigotTutorial/blob/master/LessonPictures/Lesson1/Spigot%20lib.PNG)

</details>


## Tell Intellij where to put your finished plugin
