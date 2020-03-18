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
[new member to-do list]({% post_url wiki/2020-03-13-setup %}) page will help you through setting up all of the software
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

