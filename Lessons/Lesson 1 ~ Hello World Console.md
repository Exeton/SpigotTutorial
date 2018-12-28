# Hello World Console
## Intro
This tutorial will show you how to create a Intellij project and setup a spigot plugin. This lessons expects you to have installed Intellij and have a working Spigot server.

## Creating a project
After opening intellij, you'll want to create a new project. You can do that from both inside intellij, and from the welcome to intellij screen.

Pic1
Pic2

A GUI (like shown below) will open. You'll want to select java project, click next, click next, and name your project before clicking finish.

Project Type Pic
Name Project Pic

After creating your project, Intellij's main window will open.
Main window pic

## The Four Parts of a Spigot plugin
In order to create a spigot plugin, you need to do four things.

1. Add Spigot as a libary
2. Create an artifact (the jar your plugin will create)
3. Create a plugin.yml
4. Create your main class


## Adding Spigot

The first two are very simple. Inside Intellij, press Ctrl + Alt + Shift + S. Click on the libaries tab, then the +.

## Creating an Artifact

Click on the Artifacts tab. Add a new empty jar. (From dependiceys works too, but you'll have to remove the spigot.jar from output layout). Change the jar name, output path (I recommend to your spigot/plugins folder), and drage the 'Hello World' compile output into your jar.

If your jar does not get created, you messed up a step here. (Check your output path, and that you have 'Hello World' compile output on the left side of your output layer).

Once you're done, click OK.
Ok Picture

## Creating plugin.yml

## Creating your Main class
