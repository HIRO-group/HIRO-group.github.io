---
title: Robotic Skin
description: Research Page
tags: [robotics,baxter,simulator,research]
permalink: robotic_skin.html
---

{% include image.html url="research/skin_unit.png" max-width="100%" description="Flexible skin unit created by etching the circuit diagram into a copper sheet and then encasing it in the flexible polymer ecoflex." %}


Robots have been transitioning into human-populated environments, and replacing their physical cages used to keep humans safe with complex perception and software. However, current solutions are computationally expensive, prone to occlusion, and require setup overhead. Robots require compact, self-contained sensing of nearby space to provide inherently save interactions. In this work we present the first prototype of a flexible, conformant whole-body artificial skin for collaborative robotics. In order to locate all skin units on the surface of a robot a kinematically calibration algorithm is required to reduce setup time. 

# Contributions

1. <strong>Kinematic Calibration:</strong> We present a framework for automatic kinematic calibration that leverages the IMU to automatically locate skin units, of arbitrary number, along the surface of a robot.

1. <strong>Skin Unit:</strong> We present a new <strong>flexible artificial skin</strong> that can conform to multiple surfaces. The skin utilizes an Inertial Measurement Unit (IMU) and a proximity sensor to sense obstacles at a distance. Future prototypes will embed additional capabilities (e.g. pressure sensing, temperature sensing, tactile sensing...)

1. <strong>Control Example:</strong> We demonstrate an example control scenario where a robot arm utilizes the skin to <strong>avoid collision</strong>  with a human, therefore increasing operational safety with and around people.


# Kinematic Calibration

{% include image.html url="research/calibration.png" max-width="100%" description="Illustrated setup of skin units (S) placed along the robots links (L) that are separated by joints (J). We estimate the  Denavit-Hartenberg parameters of each joint in order to calculate the pose of each skin unit along the surface of the robot. " %}

{% include image.html url="research/franka_arm.png" max-width="50%" description="Flexible skin unit created in lab" %}

# Skin Unit

{% include image.html url="research/skin_unit.jpg" max-width="50%" description="Flexible skin unit created by etching the circuit diagram into a copper sheet and then encasing it in the flexible polymer ecoflex." %}

{% include image.html url="research/bent_skin_unit.jpg" max-width="50%" description="Demonstration of the skin’s flexible capabilities." %}

# Control Example

{% include image.html url="research/control.png" max-width="100%" description="Flexible skin unit created by etching the circuit diagram into a copper sheet and then encasing it in the flexible polymer ecoflex." %}
