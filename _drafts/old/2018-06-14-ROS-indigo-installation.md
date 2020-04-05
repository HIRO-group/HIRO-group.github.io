---
title: How to install ROS indigo
description: and live happily ever after
tags: [wiki,how to,tutorial,ros,installation,indigo,ubuntu,14.04,robotics,baxter,simulator]
permalink: ros_indigo_installation.html
---

# Contents
{:.no_toc}

* This line will be replaced by the ToC, excluding the "Contents" header
{:toc}

This guide is intended to be a pain-free, future-proof way of installing `ros indigo` on a Ubuntu 14.04 machine. It is a collection of information from a variety of different sources, and the gist of it is that it will install `ROS` from sources in user space in order to avoid messing around with debian packages that are usually out-of-date and/or conflicting with more advanced features.

This page is about `ros` installation. For a summary about the main `ros` concepts and some useful command-line tools, go [here]({% post_url wiki/2018-04-18-ROS-concepts %}).

# Installing ROS indigo from sources

Why `ros indigo`? Because it is the same version that has been installed on the [Baxter robot](http://sdk.rethinkrobotics.com/wiki/Main_Page) we are using at the [Social Robotics Lab](http://scazlab.yale.edu/).

Why installing from sources? It is the way to go if you want to have access to the source files and get a better idea of the middleware. Below, there is a set of instructions, heavily inspired by [the official ros wiki](http://wiki.ros.org/indigo/Installation/Source).

**NOTE**: [This page](http://sdk.rethinkrobotics.com/wiki/Workstation_Setup#Step_3:_Create_Baxter_Development_Workspace) provides a complete step-by-step guide on how to setup a workstation for the Baxter robot.

## Prerequisites

### Setup `sources.list`

Installing `ros indigo` is not particularly difficult. First thing is to setup the machine to accept software from `packages.ros.org`. According to [this page](http://wiki.ros.org/indigo/Installation/Ubuntu#indigo.2BAC8-Installation.2BAC8-Sources.Setup_your_sources.list) (Section 1.2 and 1.3):

~~~bash
sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'
sudo apt-key adv --keyserver hkp://pool.sks-keyservers.net --recv-key 0xB01FA116
sudo apt-get update
~~~

### Installing bootstrap dependencies

These tools are used to facilitate the download and management of `ros` packages and their dependencies, among other things.

~~~bash
sudo apt-get install python-rosdep python-rosinstall-generator python-wstool python-rosinstall build-essential
~~~

### Initializing `rosdep`

~~~bash
sudo rosdep init
rosdep update
~~~

## Building the `catkin` packages

`ros` moved away from `rosbuild` and started to used `catkin`. From [here](http://wiki.ros.org/catkin/conceptual_overview):

  > _"`catkin` combines `CMake` macros and `Python` scripts to provide some functionality on top of `CMake`'s normal workflow. `catkin` was designed to be more conventional than `rosbuild`, allowing for better distribution of packages, better cross-compiling support, and better portability. `catkin`'s workflow is very similar to `CMake`'s but adds support for automatic 'find package' infrastructure and building multiple, dependent projects at the same time.
  The name `catkin` comes from the tail-shaped flower cluster found on willow trees -- a reference to Willow Garage where `catkin` was created."_

In summary: _welcome to the modern age!_

### Creating a catkin workspace

Let's create a catkin workspace called `ros_catkin_ws` in your `src` directory (assuming you have a directory called `src` for all your code):

~~~bash
cd ~/src
mkdir ros_catkin_ws
cd ros_catkin_ws/
~~~

Now, there are a number of options to choose from. The recommended one is the _Desktop-Full_ installation: this will install `ROS`, `rqt`, `rviz`, robot-generic libraries, 2D/3D simulators, navigation and 2D/3D perception packages.

~~~bash
rosinstall_generator desktop_full --rosdistro indigo --deps --wet-only --tar > indigo-desktop-full-wet.rosinstall
wstool init -j8 src indigo-desktop-full-wet.ros
~~~

### Resolving dependencies

Before you can build your catkin workspace, you need to make sure that you have all the required dependencies. They use the `rosdep` tool for this:

~~~bash
rosdep install --from-paths src --ignore-src --rosdistro indigo -y
~~~

This will look at all of the packages in the `src` directory and find all of the dependencies they have. Then it will recursively install the dependencies.

### Building the catkin workspace

Once it has completed downloading the packages and resolving the dependencies you are ready to build the catkin packages. We will use the `catkin_make_isolated` command because there are both catkin and plain cmake packages in the base install, when developing on your catkin only workspaces you should use `catkin/commands/catkin_make`.

Invoke `catkin_make_isolated`:

~~~bash
./src/catkin/bin/catkin_make_isolated --install -DCMAKE_BUILD_TYPE=Release
~~~

**WARNING:** this takes a loong time. Go grab a coffee or enjoy your life.

### `.bashrc`

Add this to your `~/.bashrc` file:

~~~bash
# Ros stuff
export ROS_ROOT="$HOME/src/ros_catkin_ws/install_isolated"
export PATH=$ROS_ROOT/bin:$PATH
source $ROS_ROOT/setup.bash
~~~

Now everything should be set up correctly. It's time to [follow some tutorials](http://wiki.ros.org/ROS/Tutorials).

# Installing `catkin_tools`

From here onward, we will use here `catkin_tools` instead of `catkin_make`, so let's install it before doing anything else. Similarly to `ros` before, we will download it from sources and install it in user space  (from [here](http://catkin-tools.readthedocs.io/en/latest/installing.html)):

~~~bash
cd ~/src
git clone https://github.com/catkin/catkin_tools.git
cd catkin_tools
pip install -r requirements.txt --upgrade --user
python setup.py install --user --record install_manifest.txt
~~~

Why we haven't been using `catkin_tools` to compile `ros` too? Because I have never tested it myself so I can't recommend it (feel free to try it out yourself).

# Installing Baxter SDK from sources

If you need to use the [Baxter Research Robot](http://sdk.rethinkrobotics.com/wiki/Baxter_Setup), it is best if you download and install its SDK. It is even better if you download and install the Gazebo simulator to simulate it!

## Create a new workspace for the Baxter SDK

In order to decouple the stable `ros` installation from the baxter SDK, it is better to maintain two separate workspaces (please notice that we are using `catkin_tools` instead of `catkin_make`).

~~~bash
cd ~/src
mkdir -p ros_baxter_ws
mkdir -p ros_baxter_ws/src
cd ros_baxter_ws/
catkin init -w .
catkin build
~~~

## Install SDK Dependencies

~~~bash
sudo apt-get update
sudo apt-get install git-core python-argparse python-wstool python-vcstools python-rosdep ros-indigo-control-msgs ros-indigo-joystick-drivers
~~~

## Install and compile SDK

~~~bash
cd ~/src/ros_baxter_ws/src
wstool init .
wstool merge https://raw.githubusercontent.com/RethinkRobotics/baxter/master/baxter_sdk.rosinstall
wstool update
cd ~/src/ros_baxter_ws
catkin build
~~~

## Source the Baxter SDK workspace

Again, go back to the `~/.bashrc`, and add the following (it should go **after** the previous `source $ROS_ROOT/setup.bash`):

~~~bash
source $HOME/src/ros_baxter_ws/devel/setup.bash
~~~

## Installing the Baxter simulator

We will add the Baxter simulator to the same `ros_baxter_ws` we have created before:

~~~bash
cd ~/src/ros_baxter_ws/src
wstool merge https://raw.githubusercontent.com/RethinkRobotics/baxter_simulator/master/baxter_simulator.rosinstall
wstool update
cd ~/src/ros_baxter_ws
catkin build
cp src/baxter/baxter.sh .
~~~

Please refer to [this link](http://sdk.rethinkrobotics.com/wiki/Simulator_Installation) for instructions on how to run it and use it.

# Creating a development ROS workspace

Similarly to before, in order to decouple the stable `ros` installation from the development packages you are working on, it is better to create a third workspace. Below, you can find instructions on how to do it (from [here](http://wiki.ros.org/ROS/Tutorials/InstallingandConfiguringROSEnvironment)).

~~~bash
cd ~/src
mkdir -p ros_devel_ws
mkdir -p ros_devel_ws/src
cd ros_devel_ws/
catkin init -w .
~~~

Even though the workspace is empty (there are no packages in the `src` folder) you can still `build` the workspace:

~~~bash
cd ~/src/ros_devel_ws/
catkin build
~~~

The `catkin build` command is a convenience tool for working with catkin workspaces. If you look in your current directory you should now have a `build` and `devel` folder. Inside the `devel` folder you can see that there are now several `setup.*sh` files. Sourcing any of these files will overlay this workspace on top of your environment:

~~~bash
source devel/setup.bash
~~~

To make this permanent, you have to again go back to the `~/.bashrc`, and add the following (it should go **after** the previous `source $HOME/src/ros_baxter_ws/devel/setup.bash`):

~~~bash
source $HOME/src/ros_devel_ws/devel/setup.bash
~~~

To make sure your workspace is properly overlayed by the setup script, make sure `ROS_PACKAGE_PATH` environment variable includes the directory you are in.

~~~bash
[scazlab@baxter]$ echo $ROS_PACKAGE_PATH
/home/scazlab/code/ros_devel_ws/src:/home/scazlab/code/ros_catkin_ws/install_isolated/share:/home/scazlab/code/ros_catkin_ws/install_isolated/stacks
~~~
