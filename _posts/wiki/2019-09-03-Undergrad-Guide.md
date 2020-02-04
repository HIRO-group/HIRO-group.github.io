---
title: Getting Started as a new member
description: Answering the questions you didn't know to ask
tags: [wiki,how to,tutorial,ros,installation,kinetic,ubuntu,16.04,robotics,Sawyer,simulator]
permalink: undergrad_guide.html
author: Garrett Pierson
---

# Contents
{:.no_toc}

* This line will be replaced by the ToC, excluding the "Contents" header
{:toc}

This guide is intended for new group members with limited exposure to
ROS and other tools used in the HIRO Group. This page in conjunction with the
[new member to-do list]({% post_url wiki/2020-02-03-new-HIRO-member %}) page will help you through setting up all of the software
so that you can get started working on your project with minimal frustration.

# When Should I Ask For Help?

Coding can be *very* frustrating, but learning when to ask for help can reduce
the time you spend looking for answers on Stack Overflow and keep making
progress on your project. Struggling with problems and learning to utilize
online resources is a valuable skill that takes time and frustration to develop,
but this does not mean you should not ask for help. Below are some simple
guidelines for when you should ask for help on a problem.

  1. **Google it!**
  Take the error messages or type what you are trying to do and search for answers
  using Google. This should always be your first step after trying for a solid
  15-20 minutes on your own. Carefully read through at least the first page for
  answers to your problems and refer to the tutorials. Try this for an hour, then
  if you can not figure it out, ask one of the other members.

  2. **Ask an Undergraduate Student!**
  You should introduce yourself to everyone in the lab and get to know them
  (everyone is also listed on the website under [people](https://hiro-group.ronc.one/people.html)) are struggling and make a
  hypothesis of why you are having a problem. If the undergraduates cannot
  quickly solve the issue or if you are specifically working with a graduate student,
  you should do some more searching online and review your code to see if something
  small was overlooked. If this does not work, go ask a graduate student.

  3. **Ask a Graduate Student!**
  Find a master's or PhD student and, like before, have an understanding
  of your problem, where you are struggling, and what you have tried. They should
  be able to help you with most issues you will encounter. If you are working on
  something specific and the graduate students in the lab are not sure how to
  help, you should ask Alessandro for advice on how to proceed.

# Development Goals

## 1. Learn how to use Linux

If you have never used Linux before, please try
[this](http://www.ee.surrey.ac.uk/Teaching/Unix/http://www.ee.surrey.ac.uk/Teaching/Unix/)
tutorial first to learn some basic command line tools.

## 2. Install the software (see preliminaries)

  * Consider dual booting with Ubuntu 16.04:
    * [MacOS](https://www.lifewire.com/dual-boot-linux-and-mac-os-4125733)
    * [Windows](https://www.tecmint.com/install-ubuntu-alongside-with-windows-dual-boot/)
    * [CS Department Virtual Machine](https://foundation.cs.colorado.edu/vm/)
  * Setup your workspaces:
    * Add paths to your `~/.bashrc` to source your workspaces. Access this via the
      command line by opening the file with an editor like gedit or Sublime Text.
      Then add the command `source $HOME/<yourwsname_ws>/devel/setup.bash` to the
      end of the `.bashrc` file.

## 3. Work through the ROS Tutorials Beginner Level (1-20)

  * Focus on package creation and how to execute your programs
  * Understand how to set up targets for the programs you want to run
  * This is done by going to your Cmake file in your workspace/package and going
   to the build section. From there you need to follow the instructions in the
   comments and:
    * Specify additional locations of header files.
      ~~~cmake
      Include_Directories (
          ${catkin_INCLUDE_DIRS}
          ~/src/ros_devel_ws/devel/include
          ~/src/ros_devel_ws/devel/include/intera_core_msgs
          ~/src/ros_devel_ws/src/your_package/include/your_package
      )
      ~~~
    * Declare a C++ Executable.
      ~~~cmake
      add_executable(target_name src/target_name.cpp)
      ~~~
    * Add Cmake Target Dependencies of the Executable.
      ~~~cmake
      add_dependencies(target_name ${${PROJECT_NAME}_EXPORTED_TARGETS} ${catkin_EXPORTED_TARGETS})
      ~~~
    * Specify Libraries to Link a Library or Executable Target Against.
      ~~~cmake
      target_link_libraries(target_name ${catkin_LIBRARIES})
      ~~~

    * Take a look at the Cmake tutorials linked in the [new member to-do list]({% post_url wiki/2020-02-03-new-HIRO-member %}) section.
    * Make sure to pay attention to publishers and subscribers as they are essential to ROS.

## 4. Get something moving! (See Section 5 for Example Code)

  * Run some of the example programs like the [wobble program](http://sdk.rethinkrobotics.com/intera/Head_Movement_Example) on the Intera SDK Gazebo site for Sawyer.
  * Write a program that can move the Sawyer arm around in Gazebo. As an extension, create a basic menu system so that the user can send poses to the Sawyer.
  * Write a program that records the joint angles when the cuff button on the Sawyer arm is pressed--please get training from a graduate student before using the robot.
  With the recorded poses, after the user is done moving the arm, have the Sawyer arm reenact these poses in the order they occurred. You will need to limit the maximum speed of the arm as this can be dangerous.
  * Send an image to the Sawyer display.

## 5. Example Code

  * Pan Sawyer's head.

      ~~~c
      #include "ros/ros.h"
      #include <iostream>
      #include <sstream>
      #include "HeadPanCommand.h"

      int main(int argc, char **argv)
      {
          ros::init(argc, argv, "pub");
          ros::NodeHandle n;

          ros::Publisher joint_pub = n.advertise<intera_core_msgs::HeadPanCommand>("/robot/head/command_head_pan", 100);

          ros::Rate loop_rate(1);
          float target = 1.0;

          while(ros::ok())
          {
              intera_core_msgs::HeadPanCommand msg;
              msg.target = 1.0 - target;
              target = msg.target;
              msg.speed_ratio = 0.5;
              msg.pan_mode = 0;
              joint_pub.publish(msg);
              ros::spinOnce();
              loop_rate.sleep();
          }
          return 0;
      }
      ~~~
  * Send a pose to Sawyer.
      ~~~c
      #include "ros/ros.h"
      #include <iostream>
      #include <sstream>
      #include "JointCommand.h"

      int main(int argc, char **argv) {
        ros::init(argc, argv, "pub");
        ros::NodeHandle n;

        ros::Publisher joint_pub = n.advertise<intera_core_msgs::JointCommand>("/robot/right_joint_position_controller/joints/right_j0_controller/command",100);
        ros::Rate loop_rate(1);

        float position = 2.0;
        intera_core_msgs::JointCommand msg;

        msg.mode = 1;
        msg.names[0] = "j0";
        msg.position[0] = position;

        joint_pub.publish(msg);
        ros::spinOnce();
        loop_rate.sleep();
        return 0;
       }
      ~~~
