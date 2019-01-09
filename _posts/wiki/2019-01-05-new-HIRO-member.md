---
title: Cheat sheet
description: Things to do when you join the HIRO group
permalink: new_member.html
---

# Contents
{:.no_toc}

* This line will be replaced by the ToC, excluding the "Contents" header
{:toc}

**Want do to robotics?**{:.color-banner}
The following is a list of things to do if you are new to the {{ site.title }}. Please consider this as a non-exhaustive cheat sheet that is modified over time. As such, feel free to edit it if there is anything you would like to add!

## 1. Preliminaries

 1. Create an account on our [Slack](https://arpg.slack.com), and share your username with your supervisor and/or point of contact. Ideally, install slack on your machine as well as on your phone in oder to be always up to date with what happens in the lab. Most of our internal communication happens there.
 2. Create an account on [GitHub](https://github.com) if you haven't already, and share your username with your supervisor and/or point of contact.
 3. Request to be added to our [GitHub organization](https://github.com/HIRO-group).
 4. Make your membership to the GitHub organization public.
 5. Write an email to [Chantel Lehl](mailto:chantel.lehl@colorado.edu) **with Prof. Alessandro Roncone in Cc**{:.color-banner} in order to get lab access with your Buff card number. Ask her to be added to ECES 116 and ECES 111. Please send her the following information: Name, Student ID, Buff Card Number, CU Login name, Email.
 6. Do a Pull Request [PR] on [this repository](https://github.com/HIRO-group/HIRO-group.github.io) to add your data to [this file](https://github.com/HIRO-group/HIRO-group.github.io/blob/master/_data/people.yml) and a picture of you to [this folder](https://github.com/HIRO-group/HIRO-group.github.io/tree/master/img/people). The picture needs to be square, and preferably not bigger than 400x400 px.

# 2. Software

For what concerns the software, your mileage may vary. This is what you need to do if you are developing software in the HIRO group.

## 2.1 Install Ubuntu [16.04]

Linux (and Ubuntu) is our operating system of choice. It is not important to be a Linux expert, but you need at least to have it installed in order to be able to develop on an environment as similar as possible to the one you will use when using the Sawyer Robot (or similar ROS-based robots).

You have the following options:

  1. **You already use Ubuntu** → great! You are a true nerd. Move on to the next section :sunglasses:
  2. **You use MacOS / Windows:**
      1. You can **install Ubuntu side by side** with your main OS partition [**recommended** option as it is the most flexible overall and it pays off over time]
      2. You can **use a virtual machine** with Ubuntu on it
      3. You can **use Docker** containers to virtualize an Ubuntu machine on your main operating system. Our Docker containers come with ROS and our code already preinstalled! Please be aware that this is definitely the option that requires you to be an advanced terminal user. Docker containers are still under development, however.
      4. If you use another Linux distribution or MacOS, there is also the option to install ROS on it directly, although it is (highly) unsupported and usually there are problems. But many students were able to do so!

**NOTE:** the Sawyer Robot ~~is stuck to~~ uses Ubuntu 16.04, so it is highly recommended to use that.

## 2.2 Install ROS [kinetic]

ROS is the so-called Robot Operating System. It is the core software we use to interface with the robot.

Also here, you have some specific requirements. Sawyer ~~is stuck to~~ uses [ROS kinetic](http://wiki.ros.org/kinetic). Here are some installation instructions:

  - [Installation according to Alessandro (HIGHLY RECOMMENDED)]({% post_url wiki/2018-10-18-ROS-kinetic-installation %})
  - [Installation according to ROS](http://wiki.ros.org/kinetic/Installation/Ubuntu)
  - [Installation from sources](http://wiki.ros.org/kinetic/Installation/Source)

## 2.3 Learn about ROS

To have some degree of understanding of ROS, please read the following documents:

  - [An introduction by Alessandro]({% post_url wiki/2018-04-18-ROS-concepts %})
  - [The official introduction](http://wiki.ros.org/ROS/Concepts),
  - [The documentation on nodes](http://wiki.ros.org/Nodes).

If you still need some practice, you might have a look at [ROS tutorials](http://wiki.ros.org/ROS/Tutorials).

## 2.4 Other tools

### 2.4.1 CMake

`CMake` is core to `ROS` development and any advanced, multi-platform, `C++` based development. It is relatively easy to learn, but very difficult to master. Here are some resources that might be useful:

 - [CGold: The Hitchhiker’s Guide to the CMake](http://cgold.readthedocs.io/en/latest/) is a very long, but complete and thorough set of tools
 - The [LLVM primer on CMake](https://llvm.org/docs/CMakePrimer.html) is useful for the language level (i.e. variables, control loops, commands), but it does not provide interesting information like explanation of `target_include_directories` `target_link_libraries`
 - [This one](https://github.com/onqtam/awesome-cmake#resources) is another long tutorial
 - [This one](https://gist.github.com/mbinna/c61dbb39bca0e4fb7d1f73b0d66a4fd1) is a useful collection of tips and tricks
 - [This](https://codingnest.com/basic-cmake/) instead is a series of tutorials oriented towards students that I saw recently and may be useful
 - [This](https://samthursfield.wordpress.com/2015/11/21/cmake-dependencies-between-targets-and-files-and-custom-commands/) is a nice article about what mess `CMake` is---and also a good way to start learning it

# 3 Guidelines / options / editor preferences

Here are some good things to set up before contributing to our code:

 * Use [Sublime text 3](https://www.sublimetext.com/3). Sublime is your friend!!!
 * Rebase by default when doing git pull → `git config --global branch.autosetuprebase always`
 * Use **ALWAYS** tab as spaces → on Sublime text, you should add this in your preferences `"translate_tabs_to_spaces": true`
 * Ensure newline at the end of files → on Sublime text, you should add this in your preferences `"ensure_newline_at_eof_on_save": true`
 * Trim trailing white space on save → on Sublime text, you should add this in your preferences `"trim_trailing_white_space_on_save": true`
 * **DO NOT** create backup files (those that end with `~`), or at least do not commit them
 * Set up `4` spaces as tab width.
 * Be considerate in using `git`. `git` is a great tool, but it needs to be used carefully in order to maximize its effectiveness. To this end, please:
    * commit frequently, push frequently
    * do not create huge commits with all the files you worked on during your day because it is harder for us to review them
    * use branching and pull requests to implement features/bug fixes
 * Keep your code **ALWAYS** in a compile-able state. We don't want our work on the Sawyer to be slowed down by some partial feature that is broken (which is fine) but then breaks all the compilations on the machine


Please be aware that, although the suggestions above are only guidelines, they will be **STRICTLY ENFORCED** throughout our code, as they set the minimum bar to have fruitful and effective collaborations.
