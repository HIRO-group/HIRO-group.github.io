---
title: ROS Concepts
description: Summary about some ROS concepts and tools
tags: [wiki,how to,tutorial,ros,concepts,tools,command-line,indigo,ubuntu,14.04,robotics,baxter,simulator]
permalink: ros_concepts.html
---

# Contents
{:.no_toc}

* This line will be replaced by the ToC, excluding the "Contents" header
{:toc}

This page is a summary about the main ROS concepts and some useful command-line tools. It is a summary of what is available [here](http://wiki.ros.org/ROS/Concepts). For a tutorial on how to install ROS `indigo` and the Baxter SDK from sources, go [here]({% post_url wiki/2018-06-14-ROS-indigo-installation %}); if you want to install ROS `kinetic` and the Sawyer SDK instead, please go [here]({% post_url wiki/2018-10-18-ROS-kinetic-installation %}).

# Master

The ROS Master provides naming and registration services to the rest of the nodes in the ROS system. It tracks publishers and subscribers to topics as well as services. The role of the Master is to enable individual ROS nodes to locate one another. Once these nodes have located each other they communicate with each other peer-to-peer.
The Master also provides the Parameter Server.

The Master is most commonly run using the `roscore` command, which loads the ROS Master along with other essential components.

# Nodes

A node is a process that performs computation. Nodes are combined together into a graph and communicate with one another using _streaming topics_, _RPC services_, and the _Parameter Server_. These nodes are meant to operate at a fine-grained scale; a robot control system will usually be comprised of many nodes.

All running nodes have a graph resource name that uniquely identifies them to the rest of the system - e.g. `/hrc_controller`. Nodes also have a node type, that simplifies the process of referring to a node executable on the fileystem. These node types are package resource names with the name of the node's package and the name of the node executable file. In order to resolve a node type, ROS searches for all executables in the package with the specified name and chooses the first that it finds. As such, you need to be careful and not produce different executables with the same name in the same package.

A ROS node is written with the use of a ROS client library, such as `roscpp` or `rospy`.

# Topics

Topics are named buses over which nodes exchange messages. Topics have anonymous publish/subscribe semantics, which decouples the production of information from its consumption. In general, _nodes are not aware of who they are communicating with_. Instead, nodes that are interested in data subscribe to the relevant topic; nodes that generate data publish to the relevant topic. There can be multiple publishers and subscribers to a topic.

Topics are intended for unidirectional, streaming communication. Nodes that need to perform remote procedure calls, i.e. receive a response to a request, should use services instead. There is also the Parameter Server for maintaining small amounts of state.

Each topic is strongly typed by the ROS message type used to publish to it and nodes can only receive messages with a matching type. The Master does not enforce type consistency among the publishers, but subscribers will not establish message transport unless the types match. Furthermore, all ROS clients check to make sure that an MD5 computed from the `msg` files match. This check ensures that the ROS Nodes were compiled from consistent code bases.

# Services

The publish/subscribe model is a very flexible communication paradigm, but its many-to-many one-way transport is not appropriate for RPC request/reply interactions, which are often required in a distributed system. Request/reply is done via a service, which is defined by a pair of messages: one for the request and one for the reply. A providing ROS node offers a service under a string name, and a client calls the service by sending the request message and awaiting the reply. Client libraries usually present this interaction to the programmer as if it were a remote procedure call.

Services are defined using `srv` files, which are compiled into source code by a ROS client library.

A client can make a persistent connection to a service, which enables higher performance at the cost of less robustness to service provider changes.

# Messages

Nodes communicate with each other by publishing messages to topics. A message is a simple data structure, comprising typed fields. Standard primitive types (integer, floating point, boolean, etc.) are supported, as are arrays of primitive types. Messages can include arbitrarily nested structures and arrays (much like C structs).
Nodes can also exchange a request and response message as part of a ROS service call. These request and response messages are defined in `srv` files.

Message types use standard ROS naming conventions: `package_name/msg_file_name`. For example, `std_msgs/msg/String.msg` has the message type `std_msgs/String`.

In addition to the message type, messages are versioned by an MD5 sum of the `.msg` file. Nodes can only communicate messages for which both the message type and MD5 sum match.

## Field types

### Built-in types

|---------------------+-----------------------------------+-------------------+-----------------|
| **Primitive Type**  | **Serialization**                 | **C++**           | **Python**      |
|:--------------------|:---------------------------------:|:-----------------:|:----------------|
|     bool            | unsigned 8-bit int                | uint8_t           | bool            |
|     int8,16,32,64   | signed 8,16,32,64-bit int         | int8,16,32,64_t   | int             |
|    uint8,16,32,64   | unsigned 8,16,32,64-bit int       | uint8,16,32,64_t  | int             |
|     float32         | 32-bit IEEE float                 | float             | float           |
|     float64         | 64-bit IEEE float                 | double            | float           |
|     string          | ascii string                      | std::string       | string          |
|     time            | secs/nsecs unsigned 32-bit ints   | ros::Time         | rospy.Time      |
|     duration        | secs/nsecs  signed 32-bit ints    | ros::Duration     | rospy.Duration  |
{: class="table"}

### Array Handling

|-------------------+-------------------------+---------------------------------------------------+-------------|
| **Array Type**    | **Serialization**       | **C++**                                           | **Python**  |
|:------------------|:-----------------------:|:-------------------------------------------------:|:-----------:|
| fixed-length      | no extra serialization  | 0.11+: `boost::array`, otherwise: `std::vector`   | tuple       |
| variable-length   | uint32 length prefix    | `std::vector`                                     | tuple       |
| uint8[]           | see above               | `std::vector<uint8_t>`                            | string      |
| bool[]            | see above               | see above                                         | list(bool)  |
|-------------------+-------------------------+---------------------------------------------------+-------------|
{: class="table"}

# Bags

A bag is a file format in ROS for storing ROS messages. Bags -- so named because of their .bag extension -- have an important role in ROS, and a variety of tools have been written to allow you to store, process, analyze, and visualize them. **The bag file format is very efficient for both recording and playback**, as messages are stored in the same representation used in the network transport layer of ROS. As such, **bags are the primary mechanism in ROS for data logging**, which means that they have a variety of offline uses.

Bags are typically created by a tool like `rosbag`, which subscribe to one or more ROS topics, and store the serialized message data in a file as it is received. These bag files can also be played back in ROS to the same topics they were recorded from, or even remapped to new topics.

Using bag files within a ROS Computation Graph is generally no different from having ROS nodes send the same data, though you can run into issues with timestamped data stored inside of message data. For this reason, the `rosbag` tool includes an option to publish a simulated clock that corresponds to the time the data was recorded in the file.

# Parameter server

A parameter server is a shared, multi-variate dictionary that is accessible via network APIs. Nodes use this server to store and retrieve parameters at runtime. It is meant to be globally viewable so that tools can easily inspect the configuration state of the system and modify if necessary.

The Parameter Server is implemented using XMLRPC and runs inside of the ROS Master, which means that its API is accessible via normal XMLRPC libraries.

## Parameters

Parameters are named using the normal ROS naming convention. This means that ROS parameters have a hierarchy that matches the namespaces used for topics and nodes, meant to protect parameter names from colliding. The hierarchical scheme also allows parameters to be accessed individually or as a tree. For example, for the following parameters:

~~~bash
/camera/left/name: leftcamera
/camera/left/exposure: 1
/camera/right/name: rightcamera
/camera/right/exposure: 1.1
~~~

The parameter `/camera/left/name` has the value `leftcamera`. You can also get the value for `/camera/left`, which is the dictionary:

~~~bash
name: leftcamera
exposure: 1
~~~

And you can also get the value for `/camera`, which has a dictionary of dictionaries representation of the parameter tree:

~~~bash
left: { name: leftcamera, exposure: 1 }
right: { name: rightcamera, exposure: 1.1 }
~~~

The Parameter Server uses XMLRPC data types for parameter values, which include:

 * 32-bit integers
 * booleans
 * strings
 * doubles
 * iso8601 dates
 * lists
 * base64-encoded binary data

You can also store dictionaries (i.e. structs) on the Parameter Server, though they have special meaning. The Parameter Server represents ROS namespaces as dictionaries. For example, imagine you set the following parameters:

~~~bash
/gains/P = 10.0
/gains/I = 1.0
~~~

You can either read them back separately, i.e. retrieving `/gains/P` would return `10.0`, or you can retrieving `/gains`, which would return a dictionary:

~~~bash
{ 'P': 10.0, 'I': 1.0 }
~~~

Just like the ROS naming hierarchy, you can nest dictionaries within dictionaries to represent child namespaces.

## Private Parameters

The ROS naming convention refers to ~name as a private name. These private names primarily are for parameters specific to a single Node. The `~` prefix prepends the Node's name to use it as a semi-private namespace -- they are still accessible from other parts of the system, but they are generally protected from accidental name collisions.

You can use remapping arguments to specify node parameters on the command line by changing the tilde `~` to an underscore `_`, e.g.:

~~~bash
rosrun rospy_tutorials talker _param:=1.0
~~~

# ROS tools and misc things

**LINK:** [http://wiki.ros.org/ROS/Tutorials/NavigatingTheFilesystem](http://wiki.ros.org/ROS/Tutorials/NavigatingTheFilesystem)

 * `rospack = ros+pack(age)` : provides information related to ROS packages
 * `roscd = ros+cd` : changes directory to a ROS package or stack
 * `rosls = ros+ls` : lists files in a ROS package
 * `roscp = ros+cp` : copies files from/to a ROS package
 * `msg` and `srv` : message and service files
 * `rosmsg = ros+msg` : provides information related to ROS message definitions
 * `rossrv = ros+srv` : provides information related to ROS service definitions
 * `catkin_make` : makes (compiles) a ROS package

# Using `rospack`

`rospack` allows you to get information about packages. In this tutorial, we are only going to cover the find option, which returns the path to package.

~~~bash
[alecive@malakim]$ rospack find roscpp
/home/alecive/code/ros_catkin_ws/install_isolated/share/roscpp
~~~

# Using `roscd`

`roscd` is part of the `rosbash` suite. It allows you to change directory to a package or a stack. Like other ROS tools, it will **only** find ROS packages that are within the directories listed in your `ROS_PACKAGE_PATH`.

~~~bash
(~) ()
[alecive@malakim]$ roscd roscpp

(~/code/ros_catkin_ws/install_isolated/share/roscpp) ()
[alecive@malakim]$
~~~

## What to do if your package is not listed in `roscd`

You need to update the database:

~~~bash
rospack profile
~~~

# Using `rosmsg`

Example Usage:

~~~bash
rosmsg show beginner_tutorials/Num
~~~

You will see:

~~~bash
int64 num
~~~

In the previous example, the message type consists of two parts:

 * beginner_tutorials -- the package where the message is defined
 * Num -- The name of the `msg` Num.

If you can't remember which Package a `msg` is in, you can leave out the package name. Try:

~~~bash
rosmsg show Num
~~~

You will see:

~~~bash
[beginner_tutorials/Num]:
int64 num
~~~

# Using `rossrv`

Example Usage:

~~~bash
rossrv show beginner_tutorials/AddTwoInts
~~~

You will see:

~~~bash
int64 a
int64 b
---
int64 sum
~~~

Similar to `rosmsg`, you can find service files like this without specifying package name:

~~~bash
rossrv show AddTwoInts
[beginner_tutorials/AddTwoInts]:
int64 a
int64 b
---
int64 sum

[rospy_tutorials/AddTwoInts]:
int64 a
int64 b
---
int64 sum
~~~

# `msg` and `srv`

`msg` files are stored in the `msg` directory of a package, and `srv` files are stored in the `srv` directory.

`msgs` are just simple text files with a field type and field name per line. The field types you can use are:

 * int8, int16, int32, int64 (plus uint*)
 * float32, float64
 * string
 * time, duration
 * other `msg` files
 * variable-length array[] and fixed-length array[C]

There is also a special type in ROS: the **header**, which contains a timestamp and coordinate frame information that are commonly used in ROS.
Here is an example of a `msg` that uses a Header, a string primitive, and two other msgs :

~~~
Header header
string child_frame_id
geometry_msgs/PoseWithCovariance pose
geometry_msgs/TwistWithCovariance twist
~~~

`srv` files are just like `msg` files, except they contain two parts: a request and a response. The two parts are separated by a `---` line. Here is an example of a `srv` file where A and B are the request, and Sum is the response:

~~~
int64 A
int64 B
---
int64 Sum
~~~

The full specification for the message format is available at the [Message Description Language](http://wiki.ros.org/ROS/Message_Description_Language) page.
If you are building C++ nodes which use your new messages, you will also need to declare a dependency between your node and your message, as described in the [catkin msg/srv build documentation](http://docs.ros.org/hydro/api/catkin/html/howto/format2/building_msgs.html).

## Using `msg` in your package

We need to make sure that the `msg` files are turned into source code for C++, Python, and other languages. To this end, follow these steps:

 1. Open `package.xml`, and make sure these two lines are in it and uncommented:

    ~~~xml
    <build_depend>message_generation</build_depend>
    <run_depend>message_runtime</run_depend>
    ~~~

 2. Add the `message_generation` dependency to the `find_package` call which already exists in your `CMakeLists.txt` so that you can generate messages:

    ~~~cmake
    find_package(catkin REQUIRED COMPONENTS
      roscpp
      rospy
      std_msgs
      message_generation
    )
    ~~~

 3. Make sure you export the message runtime dependency:

    ~~~cmake
    catkin_package(
      ...
      CATKIN_DEPENDS message_runtime ...
      ...)
    ~~~

 4. Uncomment the following block of code in your `CMakeLists.txt`, and replace the stand in `Message*.msg` files with your `.msg` file:

    ~~~cmake
    add_message_files(
      FILES
      Message1.msg
      Message2.msg
    )
    ~~~

 5. We must ensure the `generate_messages()` function is called. Uncomment these lines:

    ~~~cmake
    generate_messages(
      DEPENDENCIES
      std_msgs
    )
    ~~~

## Using `srv` in your package

We need to make sure that the `srv` files are turned into source code for C++, Python, and other languages. Do step #1, #2, #3, #5 from previous section, and then uncomment the following lines, and replace the placeholder `Service*.srv` files for your service files:

~~~cmake
add_service_files(
  FILES
  Service1.srv
  Service2.srv
)
~~~

Now you're ready to generate source files from your service definition.
