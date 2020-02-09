---
title: Visual Studio Code URDF Previewer
description: Preview urdf files in VS Code!
permalink: vscode_urdf_previewer.html
tags: [wiki,how to,tutorial,ros,vscode,urdf]

subcategory: news
---

# Contents
{:.no_toc}

* This line will be replaced by the ToC, excluding the "Contents" header
{:toc}

**Try Out Visual Studio Code's URDF Previewer!**{:.color-banner}
Sometimes, running a software like Gazebo becomes tedious if you're trying to see that your `urdf` model looks correct. You can avoid this by using the URDF previewer that is conveniently part of the ROS extension in Visual Studio Code.

# 1 Preliminary Steps

First, make sure that you have Visual Studio Code installed. It can be installed (for Windows, Linux, and Mac) [here](https://code.visualstudio.com/download).

Once VS Code is installed, you will want to open a catkin workspace from there. For example, let's say that you have your workspace folder named `catkin_ws`. Since `catkin_ws` is a catkin workspace, you can do `code catkin_ws`, which will open a running instance of VS Code containing all of the contents of that directory. Below is an example:

~~~bash
mkdir -p catkin_ws/src
cd catkin_ws/src
# get some ROS packages, write some code
cd ..
# build the packages within the workspace
catkin_make
# OR
catkin build
# Opens VS Code instance containing catkin_ws contents
code .

~~~

# 2 Installing the Extension

Once VS Code is up and running, type `Ctrl+Shift+X` to go to the Marketplace, where we can get some awesome extensions. Here's what the Marketplace looks like (it's the section on he left):

{% include image.html url="misc/vscode_extensions.jpg" max-width="100%" description="VS Code's Marketplace" %}

The extension you'll need is the **ROS** extension (it's the first result that shows up when you type in ROS, as shown below). Install this package, and make sure that it is is enabled, shown below:

{% include image.html url="misc/vscode_ros_extension.jpg" max-width="100%" description="The awesome ROS Extension" %}

# 3 Usage

In order to use the ROS extension, first, go to a `.urdf` file (or .urdf.xacro file, either works), click on it, and then press `Ctrl+Shift+P` to be able to search for the extension usage.

{% include image.html url="misc/vscode_search.jpg" max-width="100%" description="Searching for Extensions" %}

As you type in ROS, the option `ROS: Preview URDF` will show up. Make sure to click on that option.

{% include image.html url="misc/vscode_search_ros.jpg" max-width="100%" description="Preview URDF option" %}

Once that option is clicked, you should be able to see what the model will look like. An example is shown below.

{% include image.html url="misc/vscode_urdf_panda.jpg" max-width="100%" description="Franka Panda's urdf file" %}

Side note: Make sure that you have not opened VS Code within the directory of a ROS package; make sure that you have happened VS Code from the **root** of a catkin workspace.

Enjoy!
