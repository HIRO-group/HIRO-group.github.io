---
title: Robotic Skin
description: Research Page
tags: [robotics,baxter,simulator,research]
permalink: robotic_skin.html
---

{% include image.html url="research/skin_unit.png" max-width="100%" description="Flexible skin unit created by etching the circuit diagram into a copper sheet and then encasing it in the flexible polymer ecoflex." %}


Robots have been transitioning into human-populated environments, and replacing their physical cages used to keep humans safe with complex perception and software. However, current solutions are computationally expensive, prone to occlusion, and require setup overhead. Robots require compact, self-contained sensing of nearby space to provide inherently save interactions. In this work we present the first prototype of a flexible, conformant whole-body artificial skin for collaborative robotics. In order to locate all skin units on the surface of a robot a novel kinematically calibration algorithm is required to reduce setup time. 

# Contributions

1. <strong>Kinematic Calibration:</strong> We present a framework for automatic kinematic calibration that leverages an Inertial Measurement Unit (IMU) to automatically locate skin units, of arbitrary number, along the surface of a robot.

1. <strong>Skin Unit:</strong> We present a new <strong>flexible artificial skin</strong> that can conform to multiple surfaces. The skin utilizes an IMU and a proximity sensor to sense obstacles at a distance. Future prototypes will embed additional capabilities (e.g. pressure sensing, temperature sensing, tactile sensing...)

1. <strong>Control Example:</strong> We demonstrate an example control scenario where a robot arm utilizes artificial skin to <strong>avoid collision</strong>  with a human, Sincreasing operational safety with and around people.


# Kinematic Calibration
To automatically locate skin units along the surface of a robot we utilize an IMU that provides measurements of angular velocity and linear acceleration. Our optimization algorithm estimates the location and orientation of skin units using Denavit-Hartenberg as demonstrated in the figure below. 
 
{% include image.html url="research/calibration.png" max-width="75%" description="Illustrated setup of skin units (S) placed along the robots links (L) that are separated by joints (J). We estimate the  Denavit-Hartenberg parameters of each joint in order to calculate the pose of each skin unit along the surface of the robot. " %}

# Skin Unit
Skin units are embedded with an IMU for kinematic calibration and a proximity sensor to sense nearby objects. We chose to embed our circuit in a flexible polymer called ecoflex in order to have each skin unit conform to the shape of the surface it is placed on. The figure below shows the flexible capabilities of the skin sensor and an image of one unit mounted on a robotic arm. 

{% include image.html url="research/skin_unit.jpg" max-width="50%" description="Flexible skin unit mounted on a robotic arm." %}

{% include image.html url="research/bent_skin_unit.jpg" max-width="50%" description="Demonstration of the skin’s flexible capabilities." %}

# Control Example

Calibrated skin units can be used to locate obstacles with respect to the robot’s links and avoid undesired collisions by exerting a repulsive force on the robotic arm. To avoid object we require the following information:

* Calibrated pose of the Skin Unit (x, y, z, φ, θ, ψ)
* Distance d normal to the skin sensor

With this information we apply a repulsive force perpendicular to the skin unit as seen in the figure below.

{% include image.html url="research/control.png" max-width="75%" description=" A mounted skin unit exerting a repulsive force β on a robots trajectory 
<strong>T</strong> when an object is near the skin unit. The distance d is measured in millimeters. As an object approaches the robot the force exerted by β increases exponentially." %}
