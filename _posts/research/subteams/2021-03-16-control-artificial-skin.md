---
title: Control and Artificial Skin
description: Novel sensing hardware and motion control frameworks for safe human–robot interaction
subtype: control and artificial skin
permalink: subteam/control-artificial-skin.html
image:
    feature: research/roboskin/sensor_units.jpg
    size: 60%
excerpt_separator: <!-- More -->
years:
 - 2021
 - 2020
 - 2019
 - 2018
 - 2017
 - 2016
 - 2015
 - 2014
---

In this subteam, we focus on ensuring that humans and robots can interact safely in collaborative and cramped situations by simultaneously developing novel sensing hardware and motion control frameworks.
This work is interdisciplinary in nature; it requires expertise in computer science, electrical engineering, control systems, material science, and a multitude of other fields.
The HIRO Group’s research projects span across multiple research labs that are in constant communication.
These complementary technologies are used to elicit natural, fluid interactions that focus on human safety in the presence of robotic manipulators.
The hardware component of this project has led to the development of modular sensor units that can be placed anywhere on the surface of a robot manipulator to gather information about the robot’s immediate surroundings.
Using the information provided by our sensor units, we have developed a control framework that allows robot manipulators to anticipate, detect, and react to external contact that could otherwise be harmful.
Going forward, we plan to imbue robots with the ability to detect objects near and directly touching their surface with capacitive touch and tactile sensors.
These additional data streams and others to be included in future sensor units will allow for experimentation in nonverbal communication, object hand-off, and movement in clutter.

<!-- More -->

# Contents
{:.no_toc}

* This line will be replaced by the ToC, excluding the "Contents" header
{:toc}

# 1. Projects

## 1.1 Plug-and-Play Sensor Units for Environmental Robotic Perception

**Students:** Mary West, Matt Strong, [Caleb Escobedo]({% post_url people/2019-10-10-caleb %})

**_Publications:_**
 - K. Watanabe, M. Strong, M. West, C. Escobedo, A. Aramburu, K. Chaitanya and A. Roncone, _"Self-contained kinematic calibration of a novel whole-body artificial skin for human-robot collaboration,"_ in _2021 IEEE/RSJ International Conference on Intelligent Robots and Systems (IROS)_, 2021. [[PDF]]({{ site.url }}/papers/2021_Watanabe_IROS_skin_calibration.pdf) [[BIB]]({{ site.url }}/papers/2021_Watanabe_IROS_skin_calibration.bib)

The HIRO Group has begun the development of small, self-contained sensor units that can be placed on the surface of a robot manipulator to gather information about the robot’s environment.
One of the initial projects in the HIRO Group focused on improving accuracy and reducing the time required to automatically locate sensors on the robot's surface.
In this work, a system was developed that calibrated each sensor unit with accuracies multiple times greater than that of previously developed state-of-the-art methods.
With precise knowledge of the sensor unit’s position and orientation, we can locate objects or disturbances in the environment so that the robot can act intelligently, based on that data.
The sensor units are currently embedded with IMU and proximity sensors for calibration and collision anticipation algorithms.
The next generation of sensors will include capacitive and force sensing to allow high-resolution tactile feedback from touch events. In particular, we can use this data for tactile-visual sensor fusion and tactile feature extraction when interacting with physical objects.

<div class="row">
    {% include post-sorter.html subtype="roboskin" %}
</div>

## 1.2 Control Framework for Force Reduction and Human Anticipation

**Students:** [Caleb Escobedo]({% post_url people/2019-10-10-caleb %}), Matt Strong, Mary West, Nataliya Nechyporenko

**_Publications:_**
 - C. Escobedo, M. Strong, M. West, A. Aramburu, and A. Roncone, _"Contact anticipation for physical human–robot interaction with robotic manipulators using onboard proximity sensors,"_ in _2021 IEEE/RSJ International Conference on Intelligent Robots and Systems (IROS)_, 2021. [[PDF]]({{ site.url }}/papers/2021_Escobedo_IROS_contact_anticipation.pdf) [[BIB]]({{ site.url }}/papers/2021_Escobedo_IROS_contact_anticipation.bib)

In order to facilitate ubiquitous human-robot interaction, human safety must be ensured while still allowing for meaningful contact between humans and robots.
Humans can make contact with each other to share information about the environment or request attention for a particular interaction.
For example, two people working in a crowded kitchen can tap each other on the shoulder to gain their attention or signal that something is happening where one cannot see.
The HIRO Group has created a control framework that focuses on the need for humans to physically interact with their environment.
The controller uses data from onboard and proprioceptive sensors to allow robots to both avoid collisions and allow for soft purposeful contact to be made by collaborators.
After a gentle collision occurs, a reactive behavior causes the robot to move away from the contact location, allowing space for a collaborator to move through the area where contact was made.
After the human has left the scene, the robot is able to continue with its previous requested or new trajectory without entering an error state.
The control framework is constantly being improved to include information from multiple sensor sources in order to act on a detailed representation of the robot’s environment.
Future work in this area will focus on gentle continuous contact interactions, low-level control measures that guarantee human safety, and integration with complex human-robot collaboration.

{% include image.html url="research/roboskin/sensor_units.jpg" max-width="40%" description="Anticipating contact with whole-body sensing." %}

# 2. Publications

<section id="post-cv" style="padding-top: 0;">
    <div class="container">
        <div id="article">

            {% include pubs-subteam.html subteam=page.subtype publications=site.data.publications %}

        </div>
    </div>
</section>
