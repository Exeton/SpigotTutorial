# Creating A Plugin

## Intro
Getting started with spigot is very easy. Simply open Intellij, and follow these 6 steps.

1. [Create a project](https://github.com/Exeton/SpigotTutorial/blob/master/Resources/CreatingAPlugin.md#creating-a-project)
2. [Tell Intellij where your spigot.jar is](https://github.com/Exeton/SpigotTutorial/blob/master/Resources/CreatingAPlugin.md#tell-intellij-where-your-spigotjar-is)
3. [Tell Intellij where to put your finished plugin](https://github.com/Exeton/SpigotTutorial/blob/master/Resources/CreatingAPlugin.md#tell-intellij-where-to-put-your-finished-plugin)
4. [Create a Package](https://github.com/Exeton/SpigotTutorial/blob/master/Resources/CreatingAPlugin.md#create-a-package)
5. [Create your Main class](https://github.com/Exeton/SpigotTutorial/blob/master/Resources/CreatingAPlugin.md#create-your-main-class) (classes are places where you can put code)
6. [Create your plugin.yml](https://github.com/Exeton/SpigotTutorial/blob/master/Resources/CreatingAPlugin.md#create-your-pluginyml) (a file containing information like the name and version of your plugin)

<br>

## Creating a project
When you're working on a project, Intellij will automatically reopen that project every time you reopen Intellij. This means when you're creating a new project, your Intellij will look like on of the following.


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

<br>

## Tell Intellij where your spigot.jar is
This step is very easy. Press Ctrl + Alt + Shift + S simultaneously to open the Project Structure Window. Click the Libraries tab in this window, and then click the + to add a new library. 

<br>
Note: Adding Libraries allows you to use other people's code. For example, using World Edit as a library allows you to reuse WorldEdit's code for copy and pasting regions in your own code. In our case, we'll be adding Spigot.jar as a library, this will allow us to use Spigot's code for features like sending player's messages.

<br>

<details><summary>Adding Libraries Pictures</summary>

![alt text](https://github.com/Exeton/SpigotTutorial/blob/master/LessonPictures/Lesson1/Project%20Structure%20Window.PNG)
![alt text](https://github.com/Exeton/SpigotTutorial/blob/master/LessonPictures/Lesson1/Java%20Libary.PNG)
![alt text](https://github.com/Exeton/SpigotTutorial/blob/master/LessonPictures/Lesson1/Spigot%20lib.PNG)

</details>

<br>

## Tell Intellij where to put your finished plugin

Click on the Artifacts tab. Click the +, then JAR, then empty. 

You'll have a lot of options to configure your JAR (or the file that's outputted).

1. Name: You're able to change the name of your jar file in the name area.
2. Output Directory: You can change where your jar gets placed every time you build your plugin. I like to make the output directory my plugins folder, so I don't have to constantly keep moving my jar every time I want to test something in the plugin.
3. Output Layer: You might also notice an area where it has your jar and a bunch of available elements. Each element on the left side (underneath your jar) will be put inside the jar when you build your plugin. Generally the only element you'll need inside your jar will be "ProjectName compile output". You'll need to drag and drop this element onto your jar, otherwise your code won't be put into the jar.

If you don't drag and drop the compile output onto the jar file (see step 3), your Jar file won't be created. Once you've finished creating configuring your jar settings, click done.

<details><summary>Creating an Artifact</summary>

![alt text](https://github.com/Exeton/SpigotTutorial/blob/master/LessonPictures/Lesson1/Adding%20Artifact.PNG)
![alt text](https://github.com/Exeton/SpigotTutorial/blob/master/LessonPictures/Lesson1/Artifact%20Creation.PNG)

</details>

<br>

## Create a Package

Packages are like folders on your computer. They allow you to keep similar classes together which is very important for larger projects. Packages are also used to distinguish classes with the same name. For example, if you want to reference a class from Spigot, which has the same name as a class from another project, you can let Intellij (and Java) know which one you want to use, by telling it the correct package name. For this reason, all code you write should be inside of packages.

When naming packages, packages should be 
1. All lower case
2. Underscores should be used to separate words
3. If you own a domain (I own fireflower.online), you should name your package your domain reversed. My packages all start with online.fireflower

<br>

You can find more information [here](https://docs.oracle.com/javase/tutorial/java/package/namingpkgs.html).

#### Creating packages in Intellij
Creating packages in Intellij is simple. Right click your src folder, then hover over new, and click Package.

<details><summary>Creating a package</summary>
  
![alt text](https://github.com/Exeton/SpigotTutorial/blob/master/LessonPictures/Lesson1Part2/Create%20Package.PNG)
![alt text](https://github.com/Exeton/SpigotTutorial/blob/master/LessonPictures/Lesson1Part2/Name%20package.PNG)

</details>

<br>

## Create your Main class

[What are classes?](https://docs.oracle.com/javase/tutorial/java/concepts/class.html)

Classes should be named with each word of the name being capitalized. For example "My sample class name" would be "MySampleClassName". You can create a class by right clicking your package and then New > Java Class. 

<details><summary>Creating your Main class</summary>
  
![alt text](https://github.com/Exeton/SpigotTutorial/blob/master/LessonPictures/Lesson1Part2/Create%20Package.PNG)
![alt text](https://github.com/Exeton/SpigotTutorial/blob/master/LessonPictures/Lesson1Part2/Name%20package.PNG)

</details>

We're going to add some code to make the plugin work. We'll go over what the code does in a future lesson. Type "extends JavaPlugin" after your class name. Your class should look like this.

```java
package online.fireflower.hello_world;

public class HelloWorld extends JavaPlugin {

}
```
Hover over JavaPlugin, and press Alt + Enter to import JavaPlugin.

```java
package online.fireflower.hello_world;

import org.bukkit.plugin.java.JavaPlugin;

public class HelloWorld extends JavaPlugin {

}
```

Now add the following code to your HelloWorld class. This code is the starting point for making all plugins, and is needed for every plugin you make. The code will be gone over in Lesson 1.

```Java
package online.fireflower.hello_world;

import org.bukkit.plugin.java.JavaPlugin;

public class HelloWorld extends JavaPlugin {
    
    public void onEnable() {

    }
}
```
<br>

## Create your plugin.yml

To create your plugin.yml file, click the src folder, right click it, then go new >> File. Name it plugin.yml.

<details><summary>Pictures</summary>
  
![alt text](https://github.com/Exeton/SpigotTutorial/blob/master/LessonPictures/Lesson1Part2/Create%20File.PNG)
![alt text](https://github.com/Exeton/SpigotTutorial/blob/master/LessonPictures/Lesson1Part2/NameFile.PNG)
![alt text](https://github.com/Exeton/SpigotTutorial/blob/master/LessonPictures/Lesson1Part2/Plugin.yml%20empty.PNG)

</details>

You'll need to fill in the plugin.yml with 5 things. *Note using spaces in some fields will cause an error*
* name
* authour
* description
* location of your main class
* version.

The location of your main class should be the package your main class is in (i.e. online.fireflower.hello_world) + the name of the main class. Capitalization is important.

![alt text](https://github.com/Exeton/SpigotTutorial/blob/master/LessonPictures/Lesson1Part2/Finished%20Config.PNG)

<br>

## You're done!

You've finished your first plugin. In future lessons, you'll do things like sending the player messages, and making soup heal people. To ensure you've done everything correctly you'll need to create a jar file, and ensure your plugin loads when you start your server.

#### Create the plugin jar file
To make the file your server will use, click on the build tab, then build artifacts > build. A jar file should be created wherever you specified in the Project Structure window. If you forgot where you told Intellij to build the jar, reopen the Project Structure window (ctrl + alt + shift + s), and click the Artifacts tab. If your artifact isn't getting created, you probably messed up [creating the artifact](https://github.com/Exeton/SpigotTutorial/blob/master/Resources/CreatingAPlugin.md#tell-intellij-where-to-put-your-finished-plugin).

<details><summary>Pictures</summary>
  
![alt text](https://github.com/Exeton/SpigotTutorial/blob/master/LessonPictures/Lesson1Part2/Build%20Artifacts.PNG)
![alt text](https://github.com/Exeton/SpigotTutorial/blob/master/LessonPictures/Lesson1Part2/Build%20Artifacts%202.PNG)

</details>

To ensure your plugin is working, restart your spigot server and run /plugins. If your plugin shows up, everything is working. 

If your plugin isn't showing up on the list, make sure your plugin.yml is in the src folder, and not inside one of your packages. You'll have to move the plugin.yml if it's in the wrong spot.

If your plugin is showing up red, make sure there are no spaces in fields inside your plugin.yml. Check your server console for errors.
