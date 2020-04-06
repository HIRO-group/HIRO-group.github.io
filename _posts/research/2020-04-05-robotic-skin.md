---
title: Self-Contained Kinematic Calibration of Flexible Whole-Body Artificial Skin for Collaborative Robotics
description: Skin unit design, automatic kinematic calibration, and collision avoidance
author: Caleb Escobedo
permalink: research/robotic_skin.html
image:
    feature: research/roboskin/skin_unit.png
    size: 80%
excerpt_separator: <!-- More -->
---

Robots have been transitioning into human-populated environments and replacing physical separation from humans with complex perception and control software. However, current solutions are computationally expensive, prone to occlusion, and require a significant setup overhead. Robots are in need of compact, self-contained sensing of nearby space to provide inherently safe interactions.
In this work, we present the first prototype of a flexible circuit for collaborative robotics embedded with an inertial measurement unit for kinematic calibration and a proximity sensor for obstacle detection and avoidance.
When a circuit is first placed on the surface of a robot, the exact location on the surface is unknown to the robot. To address this, we present a novel kinematic calibration algorithm to reduce manual setup time.

<!-- More -->

# Contents
{:.no_toc}

* This line will be replaced by the ToC, excluding the "Contents" header
{:toc}


{% include image.html url="research/roboskin/skin_unit.png" max-width="80%" description="Fig. 1. Flexible circuit created by etching the circuit diagram into a copper sheet and then encasing it in a flexible ecoflex polymer. The circuit contains an inertial measurement unit (IMU) used in our kinematic calibration algorithm to locate the circuit on the surface of a robot. We include a proximity sensor in each flexible circuit in order to observe and avoid objects near the robot surface after calibration." %}


# Contribution

1. **Skin Unit:** we present a new **flexible artificial skin** that can conform to multiple surfaces. The skin utilizes an Inertial Measurement Unit (IMU) and a proximity sensor to sense obstacles at a distance. Future prototypes will embed additional capabilities (e.g. pressure sensing, temperature sensing, tactile sensing...).

1. **Kinematic Calibration:** we present a framework for automatic kinematic calibration that leverages an IMU to automatically locate and orient skin units, of arbitrary number, along the surface of a robot.

1. **Control Example:** we demonstrate an example control scenario where a robot arm utilizes proximity sensors embedded within a skin unit to **avoid collision** when an object is nearby. We impose a repulsive force on the point the skin sensor is mounted on the robotic arm to ensure it will not collide with an object, but will still continue on a specified trajectory.


## Skin Units

Skin units are embedded with an IMU for kinematic calibration and a proximity sensor to sense nearby objects. We chose to embed our circuit in a flexible polymer called ecoflex in order to have each skin unit conform to the shape of the surface it is placed on. The figure below shows the flexible capabilities of the skin sensor and an image of one unit mounted on a robotic arm.


<div class="row">
  <div class="col-md-6 col-print-6">
    {% include image.html url="research/roboskin/skin_unit.jpg" max-width="75%" description="Flexible skin unit mounted on a robotic arm." %}
  </div>
  <div class="col-md-6 col-print-6">
    {% include image.html url="research/roboskin/bent_skin_unit.jpg" max-width="75%" description="Demonstration of the skin’s flexible capabilities." %}
  </div>
</div>


## Kinematic Calibration

To automatically locate skin units along the surface of a robot, we utilize an IMU that provides measurements of angular velocity and linear acceleration. Our optimization algorithm estimates the position and orientation of skin units using Denavit-Hartenberg as demonstrated in the figure below.

{% include image.html url="research/roboskin/calibration.png" max-width="75%" description="Illustrated setup of skin units (S) placed along the robots links (L) that are separated by joints (J). We estimate the  Denavit-Hartenberg parameters of each joint in order to calculate the pose of each skin unit along the surface of the robot. " %}



## Control Example

Calibrated skin units can be used to locate obstacles with respect to the robot’s links and avoid undesired collisions by exerting a repulsive force on the robotic arm. To avoid objects, we require the following information:

* Calibrated pose of the Skin Unit (x, y, z, φ, θ, ψ)
* Distance d normal to the skin sensor

With this information, we apply a repulsive force perpendicular to the skin unit as seen in the figure below.

{% include image.html url="research/roboskin/control.png" max-width="75%" description=" A mounted skin unit exerting a repulsive force β on a robot's trajectory
T when an object is near the skin unit. The distance d is measured in millimeters. As an object approaches, β increases exponentially." %}

The amount of force exerted on the robot is determined by the exponential function: 

{% include image.html url="research/roboskin/control_equation.png" max-width="40%" description=""%}


This vector is multiplied by the max end-effector velocity and then added to the end-effect velocity by calculating the Jacobian of the robotic arm. In addition to altering end-effector velocity, control points along the robot can be specified and then used as a reference point to calculate a partial Jacobian that allows us to avoid collisions with objects that would impact the robot body.





# Future Work


## Dense Coverage of a Robot Arm with Skin Units

In order to consistently avoid obstacles around the robot, dense skin unit coverage is required. To achieve this goal we must efficiently distribute wiring and computational resources about the surface of the robot. This has been accomplished by Mittendorfer et al. by using rigid printed circuit boards equipped with onboard microcontrollers and redundant connections in their paper “Realizing whole-body tactile interactions with a self-organizing, multi-modal artificial skin on a humanoid robot”. Additional challenges arise due to the flexible and stretchable nature of our robotic skin that must conform to the surface it is placed on. 

Our next milestone is to densely cover a portion of a robotic arm with sensor units and with those units, consistently avoid collision from any direction. This step will require advancements in hardware to ensure measurement fidelity, reduce the amount of wiring, and allow a multitude of sensors to be placed on a robot easily. With a high density of measurements, we must have a robust control scheme that uses sensor measurements to avoid obstacles and alter the robots behavior.


## Dynamic Obstacle Avoidance

We plan to use proximity sensors embedded within each skin unit to avoid obstacles in two separate control schemes.

* End-effector movement
* Control point movement

As demonstrated in the paper “A Depth Space Approach to Human-Robot Collision Avoidance” by Flacco et al. a robot arm can avoid collision by exerting a repulsive vector to its end effector or control points along the robot arm. Both schemes can be used to increase safety when robots and humans work in close proximity.

For this milestone, we designate control points along the robot body as seen in the simulation below: 

{% include image.html url="research/roboskin/control_points.png" max-width="75%" description=""%}


The control points are then used as a reference to calculate a partial Jacobian that is used to alter joint velocities to avoid collision. Future work on this project will entail creating a robust control mechanism that quickly avoids obstacles and accounts for the robot detecting itself in certain configurations. 



