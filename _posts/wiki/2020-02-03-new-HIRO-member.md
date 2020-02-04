---
title: New member to-do list
description: Things to do when you join the HIRO group
permalink: new_member.html
category: [research, wiki]
subcategory: news
---

# Contents
{:.no_toc}

* This line will be replaced by the ToC, excluding the "Contents" header
{:toc}

**Want do to robotics?**{:.color-banner}
The following is a list of things to do if you are new to the {{ site.title }}. Please consider this as a non-exhaustive cheat sheet that is modified over time. As such, feel free to edit it if there is anything you would like to add.

For _{{ site.meetings.semester }}_, we will be holding group meetings in **{{ site.meetings.location }}**{:.color-banner}. Feel free to stop by if you want to have a chat!!

# 1 Preliminaries

Prospective new members should do the following:
 1. find a supervisor,
 2. find a project, and
 3. communicate with [Prof. Alessandro Roncone]((mailto:alessandro.roncone@colorado.edu)) regarding your project.

Once you are done with these preliminary steps, follow the instructions in the next section to finalize your membership. **You are expected to complete these tasks within 2 days of joining the group.**{:.color-banner}

# 2 New members

## 2.1 Slack

 1. Create an account on our [Slack](https://arpg.slack.com/signup).
 2. Share your username with your supervisor and/or point of contact.
 3. Ideally, [install Slack on your machine](https://slack.com/download) as well as on your phone in order to be always up to date with what happens in the group.
 4. Join the **#hiro-group** and **#hiro-github** channels on Slack. Most of our internal communication happens there.

## 2.2 GitHub & Google Calendar

 1. If you don't already have a [GitHub](https://github.com) account, create one.
 2. Share your username with your supervisor and/or point of contact.
 3. Send an email to **[Joewie Koh](mailto:joewie.koh@colorado.edu) with [Prof. Alessandro Roncone](mailto:alessandro.roncone@colorado.edu) in Cc**{:.color-banner}. Include your:
    - GitHub username, and
    - preferred email address for Google Calendar.
 4. Joewie will add you to our [GitHub organization](https://github.com/HIRO-group) and Google Calendar.
 5. Make your membership to the GitHub organization public.

## 2.3 Lab agreements

 1. Read carefully the lab agreements. There are currently three documents available:
    - [Lab etiquette](/docs/HIRO-Group-Lab-Etiquette.pdf), shared among all students and people working in the lab, with the rules of working in the lab;
    - [Graduate student agreement](/docs/HIRO-Group-Grad-Agreement.pdf), slightly biased toward PhD students but to be used for all graduate students;
    - [Undergraduate student agreement](/docs/HIRO-Group-UGrad-Agreement.pdf), for undergraduates.

 2. Print them and be prepared to sign them at your next one-on-one meeting with Prof. Roncone. (This does not need to be done within 2 days.)

## 2.4 Lab access

 1. Write an email to **[Chantel Lehl](mailto:chantel.lehl@colorado.edu) with [Prof. Alessandro Roncone](mailto:alessandro.roncone@colorado.edu) and [Joewie Koh](mailto:joewie.koh@colorado.edu) in Cc**{:.color-banner}.
 2. Ask to be granted access to ECST 322, ECES 116 and ECES 111. Please include the following information: 
    - name,
    - student ID,
    - Buff OneCard number,
    - CU login name,
    - email.

## 2.5 Group website

 1. Do a Pull Request [PR] on [this repository](https://github.com/HIRO-group/HIRO-group.github.io) to add your data to [this file](https://github.com/HIRO-group/HIRO-group.github.io/blob/master/_data/people.yml) and a picture of you to [this folder](https://github.com/HIRO-group/HIRO-group.github.io/tree/master/img/people). **The picture needs to be square, and not bigger than 400x400 px.**{:.color-banner}
 2. If you're not familiar with the PR workflow, you can refer to [this guide](https://github.com/HIRO-group/HIRO-group.github.io/blob/master/CONTRIBUTING.md).

## 2.6 Mailing list

 1. [Subscribe to our mailing list!](https://lists.colorado.edu/sympa/subscribe/hiro-group)
 2. Click on the verification link sent to your email to complete your subscription.

# 3 Optional steps

 1. Ask for an invitation to our [Trello](https://trello.com) team and [Mendeley](https://www.mendeley.com) group from **@joewie** on Slack or in the **#hiro-group** channel. Provide your preferred email. We share and keep track of relevant papers on Mendeley, while Trello is where we coordinate work on projects.
 2. To access research papers off-campus, set up the [CU Boulder VPN client](https://oit.colorado.edu/services/network-internet-services/vpn) on your machine. Alternatively, drag the following link to your bookmarks toolbar: [CU Proxy](javascript:void(location.href='https://colorado.idm.oclc.org/login?url='+location.href)). Whenever you come across a paywall, simply click on the bookmark to access the resource through the University Libraries proxy.
 3. If you plan to perform research with human subjects, please [be aware of the policies for doing so](https://www.colorado.edu/researchinnovation/irb) and [do the CITI training for Social Behavioral Research Investigators and Key Personnel](https://www.colorado.edu/researchinnovation/irb/getting-started/citi-training). [If your project requires IRB review](https://www.colorado.edu/researchinnovation/irb/getting-started/does-my-research-require-irb-review), please be prepared to do so on a timely manner as submitting an IRB Protocol [and having it reviewed] takes time.
 4. If you need storage for data, request an account with CU Boulder Research Computing on [this page](https://rcamp.rc.colorado.edu/accounts/account-request/create/verify/ucb). After receiving your RC account, await further instructions from RC to set up Duo two-factor authentication.
 5. If you are an undergraduate student joining for the summer, please [subscribe to this list](https://lists.colorado.edu/sympa/subscribe/cs-summer-undergrads).

# 4 Software

For what concerns the software, your mileage may vary. This is what you need to do if you are developing software in the HIRO group.

## 4.1 Install Ubuntu [16.04]

Linux (and Ubuntu) is our operating system of choice. It is not important to be a Linux expert, but you need at least to have it installed in order to be able to develop on an environment as similar as possible to the one you will use when using the Sawyer Robot (or similar ROS-based robots).

You have the following options:

  1. **You already use Ubuntu** → great! You are a true nerd. Move on to the next section :sunglasses:
  2. **You use MacOS / Windows:**
      1. You can **install Ubuntu side by side** with your main OS partition [**recommended** option as it is the most flexible overall and it pays off over time]
      2. You can **use a virtual machine** with Ubuntu on it
      3. You can **use Docker** containers to virtualize an Ubuntu machine on your main operating system. Our Docker containers come with ROS and our code already preinstalled! Please be aware that this is definitely the option that requires you to be an advanced terminal user. Docker containers are still under development, however.
      4. If you use another Linux distribution or MacOS, there is also the option to install ROS on it directly, although it is (highly) unsupported and usually there are problems. But many students were able to do so!

**NOTE:** the Sawyer Robot ~~is stuck to~~ uses Ubuntu 16.04, so it is highly recommended to use that.

## 4.2 Install ROS [kinetic]

ROS is the so-called Robot Operating System. It is the core software we use to interface with the robot.

Also here, you have some specific requirements. Sawyer ~~is stuck to~~ uses [ROS kinetic](http://wiki.ros.org/kinetic). Here are some installation instructions:

  - [Installation according to Alessandro (highly recommended)]({% post_url wiki/2018-10-18-ROS-kinetic-installation %})
  - [Installation according to ROS](http://wiki.ros.org/kinetic/Installation/Ubuntu)
  - [Installation from sources](http://wiki.ros.org/kinetic/Installation/Source)

## 4.3 Learn about ROS

To have some degree of understanding of ROS, please read the following documents:

  - [An introduction by Alessandro]({% post_url wiki/2018-04-18-ROS-concepts %})
  - [The official introduction](http://wiki.ros.org/ROS/Concepts)
  - [The documentation on nodes](http://wiki.ros.org/Nodes)

If you still need some practice, you might have a look at [ROS tutorials](http://wiki.ros.org/ROS/Tutorials).

## 4.4 Other tools

### 4.4.1 CMake

`CMake` is core to `ROS` development and any advanced, multi-platform, `C++` based development. It is relatively easy to learn, but very difficult to master. Here are some resources that might be useful:

 - [CGold: The Hitchhiker’s Guide to the CMake](http://cgold.readthedocs.io/en/latest/) is a very long, but complete and thorough set of tools
 - The [LLVM primer on CMake](https://llvm.org/docs/CMakePrimer.html) is useful for the language level (i.e. variables, control loops, commands), but it does not provide interesting information like explanation of `target_include_directories` `target_link_libraries`
 - [This one](https://github.com/onqtam/awesome-cmake#resources) is another long tutorial
 - [This one](https://gist.github.com/mbinna/c61dbb39bca0e4fb7d1f73b0d66a4fd1) is a useful collection of tips and tricks
 - [This](https://codingnest.com/basic-cmake/) instead is a series of tutorials oriented towards students that I saw recently and may be useful
 - [This](https://samthursfield.wordpress.com/2015/11/21/cmake-dependencies-between-targets-and-files-and-custom-commands/) is a nice article about what mess `CMake` is---and also a good way to start learning it

# 5 Guidelines / options / editor preferences

Here are some good things to set up before contributing to our code:

 * If you are on the hunt for a versatile code/text editor, consider using [Sublime text 3](https://www.sublimetext.com/3). Sublime is your friend!!!
 * Rebase by default when doing git pull → `git config --global branch.autosetuprebase always`
 * Use **ALWAYS** tab as spaces → on Sublime text, you should add this in your preferences `"translate_tabs_to_spaces": true`
 * Ensure newline at the end of files → on Sublime text, you should add this in your preferences `"ensure_newline_at_eof_on_save": true`
 * Trim trailing white space on save → on Sublime text, you should add this in your preferences `"trim_trailing_white_space_on_save": true`
 * **DO NOT** commit backup files (those that end with `~`)
 * Set up `4` spaces as tab width.
 * Be considerate in using `git`. `git` is a great tool, but it needs to be used carefully in order to maximize its effectiveness. To this end, please:
    * commit frequently, push frequently
    * do not create huge commits with all the files you worked on during your day because it is harder for us to review them
    * use branching and pull requests to implement features/bug fixes
 * Keep your code **ALWAYS** in a compile-able state. We don't want our work on the Sawyer to be slowed down by some partial feature that is broken (which is fine) but then breaks all the compilations on the machine


Please be aware that, although the suggestions above are only guidelines, they will are **strictly enforced** in our code, as they set the minimum bar to have fruitful and effective collaborations.
