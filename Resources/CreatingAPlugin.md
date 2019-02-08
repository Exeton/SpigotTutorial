# CreatingAPlugin

## Intro
Getting started with spigot is very easy. Simply open Intellij, and follow these 5 steps.

1. ![Create a project](https://github.com/Exeton/SpigotTutorial/blob/master/Resources/CreatingAPlugin.md#creating-a-project)
2. [Tell Intellij where your spigot.jar is](https://github.com/Exeton/SpigotTutorial/blob/master/Resources/CreatingAPlugin.md#tell-intellij-where-your-spigotjar-is)
3. [Tell Intellij where to put your finished plugin](https://github.com/Exeton/SpigotTutorial/blob/master/Resources/CreatingAPlugin.md#tell-intellij-where-to-put-your-finished-plugin)
4. [Create your Main class](https://github.com/Exeton/SpigotTutorial/blob/master/Resources/CreatingAPlugin.md#create-your-main-class) (classes are places where you can put code)
5. [Create your plugin.yml](https://github.com/Exeton/SpigotTutorial/blob/master/Resources/CreatingAPlugin.md#create-your-pluginyml) (a file containing information like the name and version of your plugin)


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

Click on the Artifacts tab. Click the +, then JAR, then empty. 

You'll have a lot of options to configure your JAR (or the file that's outputted).

1. Name: You're able to change the name of your jar file in the name area.
2. Output Directory: You can change where your jar gets placed every time you build your plugin. I like to make the output directory my plugins folder, so I don't have to constantly keep moving my jar every time I want to test something in the plugin.
3. Output Layer: You might also notice an area where it has your jar and a bunch of avaiable elements. Each element on the left side (underneath your jar) will be put inside the jar when you build your plugin. Generally the only element you'll need inside your jar will be "ProjectName compile output". You'll need to drag and drop this element onto your jar, otherwise your code won't be put into the jar.

If you don't drag and drop the compile output onto the jar file (see step 3), your Jar file won't be created. Once you've finished creating configuring your jar settings, click done.

<details><summary>Creating an Artifact</summary>

![alt text](https://github.com/Exeton/SpigotTutorial/blob/master/LessonPictures/Lesson1/Adding%20Artifact.PNG)
![alt text](https://github.com/Exeton/SpigotTutorial/blob/master/LessonPictures/Lesson1/Artifact%20Creation.PNG)

</details>


## Create your Main class


## Create your plugin.yml



