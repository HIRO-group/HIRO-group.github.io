---
title: Franka Installation Tutorial
description: Setting up the PC to control the Panda
tags: [wiki,how to,tutorial,Franka,ros,kernel]
permalink: franka_installation_tutorial.html
author: Garrett Pierson
---

# Contents
{:.no_toc}

* This line will be replaced by the ToC, excluding the "Contents" header
{:toc}

This guide is intended to show how to setup the Franka control interface on a PC
controlling the Panda robotic arm and summarizes the instructions on the [Franka Emika website](https://frankaemika.github.io/docs/installation_linux.html#building-from-source).
The following steps will show how to install the necessary dependencies and set up
the real time Linux kernel necessary for controlling the Panda robot.

# Installing Dependencies & Building the Packages

Begin by installing the dependencies:
 ~~~bash
`sudo apt install ros-kinetic-libfranka ros-kinetic-franka-ros`
 ~~~
 * Building the libfranka Package:
 ~~~bash
 sudo apt install build-essential cmake git libpoco-dev libeigen3-dev
 git clone --recursive https://github.com/frankaemika/libfranka
 cd libfranka
 mkdir build
 cd build
 cmake -DCMAKE_BUILD_TYPE=Release ..
 cmake --build .
 sudo make install
 ~~~
 * Building the franka-ros Package:
 ~~~bash
 cd /path/to/desired/folder
 mkdir -p catkin_ws/src
 cd catkin_ws
 source /opt/ros/kinetic/setup.sh
 catkin_init_workspace src
 git clone --recursive https://github.com/frankaemika/franka_ros src/franka_ros
 rosdep install --from-paths src --ignore-src --rosdistro kinetic -y --skip-keys libfranka
 catkin_make -DCMAKE_BUILD_TYPE=Release -DFranka_DIR:PATH=/path/to/libfranka/build
 source devel/setup.sh
 ~~~

# Kernel Installation and Set Up
The Panda requires a real time kernel running at 1 kHz to operate properly.
 * Getting a Generic Kernel:
  * Check the Kernel version: `uname -r`
  * Get the Kernel Patch for the kernel version found previously at this [website](https://www.kernel.org/pub/linux/kernel/projects/rt/).
   * Dependencies:
~~~bash
sudo apt install build-essential bc curl ca-certificates fakeroot gnupg2 libssl-dev lsb-release libelf-dev bison flex
~~~
   * Download Patch:
~~~bash
curl -SLO https://www.kernel.org/pub/linux/kernel/v4.x/linux-<your version>.tar.xz
curl -SLO https://www.kernel.org/pub/linux/kernel/v4.x/linux-<your version>.tar.sign
curl -SLO https://www.kernel.org/pub/linux/kernel/projects/rt/<your version number ex: 4.12 >/older/patch-<your version>-rt10.patch.xz
curl -SLO https://www.kernel.org/pub/linux/kernel/projects/rt/<your version number ex: 4.12 >/older/patch-<your version>-rt10.patch.sign
~~~
   * Unpack Patch:
~~~bash
xz -d linux-<your version>.tar.xz
xz -d patch-<your version>-rt10.patch.xz
~~~

# Compiling the Kernel
 * Extract the Source Code:
 ~~~bash
 tar xf linux-<your version>.tar
 cd linux-<your version>
 patch -p1 < ../patch-<your version>-rt10.patch
 ~~~
 * Configure Kernel:
 ~~~bash
 make oldconfig
 When menu pops up choose option 5: Fully Preemptible Kernel
 # For the rest of the options, use default values
 # if fakeroot doesn't work, use sudo make deb-pkg
 fakeroot make deb-pkg
 sudo dpkg -i ../linux-headers-<your version>-rt10_*.deb ../linux-image-<your version>-rt10_*.deb
 ~~~
# Verifying the Kernel
 * Restart the computer, go to the Grub boot menu, select your kernel. After entering `uname -a` you should see the output which contains `PREEMPT_RT`.
 realtime should exist at `/sys/kernel/realtime` and contain the number `1`.
# Adding Permissions
 * After kernel is running you need to create then add the user controlling the robot to the group named `realtime`:
 ~~~bash
 sudo addgroup realtime
 sudo usermod -a -G realtime <username here>
 ~~~
 * Add the following to the realtime group in `/etc/security/limits.conf` then logout and log back in:
 ~~~bash
 @realtime soft rtprio 99
 @realtime soft priority 99
 @realtime soft memlock 102400
 @realtime hard rtprio 99
 @realtime hard priority 99
 @realtime hard memlock 102400
 ~~~
# Finding DHCP For Panda
 * Go to [HIRO Github](https://github.com/HIRO-group/HIRO-group.github.io) for the
 router user-name and password. Go to the router [website](http://tplinkwifi.net/) and login to find the DHCP.
# Using the Panda
 * Enter the DHCP and log in to the Franka interface using the user-name and password from the HIRO Github.
 * Do not forget to unlock the joints from the control interface before using the Panda.
 * When shutting the Panda down be sure to wait for the robot to completely shut down before exiting the interface window.
