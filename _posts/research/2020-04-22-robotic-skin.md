---
title: Flexible Whole-Body Artificial Skin for Collaborative Robotics
description: Flexible PCB, automatic kinematic calibration, and collision avoidance
author: Caleb Escobedo, Ander Aranburu
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
# Primary Objective
{:.no_toc}
Our longterm goal is to enable robots to sense their surroundings by adding distributed, heterogeneous sensors along the robot’s surface with a variety of sensing modalities. In order to efficiently utilize sensor information, we must develop a robotic controller that generates robust and safe robotic movement. We plan to achieve our goal in three ways:
1. Create a flexible printed circuit board (PCB) that can be attached to any robotic arm and relay information about nearby objects to a robotic controller in a plug-and-play fashion.
1. Develope a kinematic calibration algorithm to automatically, accurately locate each flexible PCB along a robot arm. This information is critical to ensure the robot knows where a sensor's information relates to on its surface.
1. Formulate a robust controller that utilizes sensor information to plan trajectories that avoid collision and enable robots to work in close proximity with human collaborators.


# Contents
{:.no_toc}

* This line will be replaced by the ToC, excluding the "Contents" header
{:toc}

{% include image.html url="research/roboskin/skin_unit.png" max-width="80%" description="Fig. 1. Flexible circuit created by etching the circuit diagram into a copper sheet and then encasing it in a flexible ecoflex polymer. The circuit contains an inertial measurement unit (IMU) used in our kinematic calibration algorithm to locate the circuit on the surface of a robot. We include a proximity sensor in each flexible circuit in order to observe and avoid objects near the robot surface after calibration." %}

# Contribution

1. **Skin Unit:** we present a new **flexible artificial skin** that can conform to multiple surfaces. The skin utilizes an Inertial Measurement Unit (IMU) and a proximity sensor to sense obstacles at a distance. Future prototypes will embed additional capabilities (e.g. pressure sensing, temperature sensing, tactile sensing...).

1. **Kinematic Calibration:** we present a framework for automatic kinematic calibration that leverages an IMU to automatically locate and orient skin units, of arbitrary number, along the surface of a robot.

1. **Controller:** we demonstrate a control scenario where a robot arm utilizes proximity sensors embedded within a skin unit to **avoid collision** when an object is nearby. We impose a repulsive force on the point the skin sensor is mounted on the robotic arm to ensure it will not collide with an object, but will still continue on a specified trajectory.

## Skin Units

Skin units are embedded with an IMU for kinematic calibration and a proximity sensor to sense nearby objects. We chose to embed our circuit in a flexible polymer called ecoflex in order to have each skin unit conform to the shape of the surface it is placed on. The figure below shows the flexible capabilities of the skin sensor.

{% include image.html url="research/roboskin/bent_skin_unit.jpg" max-width="75%" description="" %}


## Kinematic Calibration

To automatically locate skin units along the surface of a robot, we utilize an IMU that provides measurements of angular velocity and linear acceleration. Our optimization algorithm estimates the position and orientation of skin units using Denavit-Hartenberg as demonstrated in the figure below.

{% include image.html url="research/roboskin/calibration.png" max-width="75%" description="Illustrated setup of skin units (S) placed along the robots links (L) that are separated by joints (J). We estimate the  Denavit-Hartenberg parameters of each joint in order to calculate the pose of each skin unit along the surface of the robot. " %}



## Controller for safety oriented robot interaction

Calibrated skin units are used to locate obstacles in a robot’s environment, this information is used to modify the robot’s behaviour in real time. When a robot detects an obstacle, it should continue along a trajectory as long as the proximity to the obstacle does not compromise safety. The robot should avoid the object if close, or stop if there is no way to reach the goal location without a collision. For this purpose, we present two separate controllers that avoid obstacles, the first focus on **end-effector** and the second on **whole body** collision avoidance.

### End-effector collision avoidance

The end effector’s velocity is modified with a potential field method to avoid objects. This means that a variable magnitude vector will be subtracted from the end-effector velocity to obtain a new velocity that avoids collisions. The repulsive vector’s direction depends on the closest obstacle to the end effector and its magnitude is determined by the distance. If an obstacle does not hinder the robot’s task, the original task-level velocity will be preserved. However, if the obstacles are too close the end-effector will stop completely.

The robot's movement is altered by the following equations. The repulsive vector’s magnitude is obtained through the equation:

$$
v=\frac{V}{1+e^{\alpha(\|\boldsymbol{d}\|\frac{2}{D}-1)}}
$$

Where $$V$$ is the max repulsive velocity, $$\boldsymbol{d}$$ is the vector that goes from the end effector to the closest object and $$\|\boldsymbol{d}\|$$ is that distance's magnitude. The variables $$D$$ and $$\alpha$$ are adjustable constants that change how distance affects the repulsive vector.

In the following interactive graph the x-axis represents the distance from object to end-effector $$\|\boldsymbol{d}\|$$ and the y-axis represents the force exerted on the end-effector. It is necessary to adjust the variables $$D$$ and $$\alpha$$ to achieve a smooth reaction from the end-effector collision avoidance algorithm.

<iframe src="https://www.desmos.com/calculator/dcf80ot3pm" width="1000px" height="500px" style="border: 1px solid #ccc" frameborder="0"></iframe>

<br />

The final repulsive vector $$\boldsymbol{V}(\boldsymbol{P}, \mathbf{O})$$, that as we have seen depends on the end effectors and the closest object's locations $$\boldsymbol{P}$$ and $$\boldsymbol{O}$$, points towards the object that is closest to the robots end-effector and is calculated by the equation:

$$
\boldsymbol{V}(\boldsymbol{P}, \mathbf{O})=v \frac{\boldsymbol{d}}{\|\boldsymbol{d}\|}
$$

The following video demonstrates end-effector collision avoidance where the end-effector is commanded to first move towards the robot body, avoiding the yellow obstacle point. The robot then moves towards the yellow obstacle, causing the robot to slow down to a complete stop at close proximity to avoid collision.


{% include image.html url="research/roboskin/flacco_end_effector.gif" max-width="75%" %}

### Whole body collision avoidance

To ensure safe human-robot collaboration, the robot must avoid collisions along its entire body. Instead of modifying the end-effector velocity directly, as in the previous method, repulsive vectors will be used to apply kinematic constraints to joint velocities along the body of the robot.

The constraints are computed as in the following equations:

$$
f\left(\|\boldsymbol{d}\|)\right)=\frac{1}{1+e^{\alpha \left(\|\boldsymbol{d}\|(2 / D)-1\right) }}
$$

Where $$\|\boldsymbol{d}\|$$ represents the distance form an arbitrary control point along the robot's body to an obstacle as in seen in the figures below. The rest of the equation is identical to the repulsive vector equation presented in the previous section, but $$f$$ is now bounded between $$0$$ and $$1$$. This value $$f$$ is is used to limit the joint velocities in the next equations. Depending on the closest object's location either the maximum or minimum joint velocity $$\dot{q}_{i}$$ will be updated.

$$
\dot{q}_{\max , i}=V_{\max , i}\left(\left(1-f\left(\|\boldsymbol{d}\|)\right)\right)\right.
$$

<br />

$$
\dot{q}_{\min , i}=-V_{\max , i}\left(\left(1-f\left(\|\boldsymbol{d}\|)\right)\right)\right.
$$

<br />

{% include image.html url="research/roboskin/flacco_body_before.gif" max-width="75%" description= "No collision avoidance: the robot's body collides with the yellow obstacle point" %}

{% include image.html url="research/roboskin/flacco_body_after.gif" max-width="75%" description= "Collision avoidance: The robot reacts to an obstacle near a body control point and alters its joint velocities without hindering the end-effectors task"%}


# Future Work

## Dense Coverage of a Robot Arm with Skin Units

In order to consistently avoid obstacles around the robot, dense skin unit coverage is required. To achieve this goal we must efficiently distribute wiring and computational resources about the surface of the robot. This has been accomplished by Mittendorfer et al. by using rigid printed circuit boards equipped with onboard microcontrollers and redundant connections in their paper “Realizing whole-body tactile interactions with a self-organizing, multi-modal artificial skin on a humanoid robot”. Additional challenges arise due to the flexible and stretchable nature of our robotic skin that must conform to the surface it is placed on.

Our next milestone is to densely cover a portion of a robotic arm with sensor units and with those units, consistently avoid collision from any direction. This step will require advancements in hardware to ensure measurement fidelity, reduce the amount of wiring, and allow a multitude of sensors to be placed on a robot easily. With a high density of measurements, we must have a robust control scheme that uses sensor measurements to avoid obstacles and alter the robots behavior.


## Robotic control using simulated Skin Units

Expand our current controller to avoid dynamic and static obstacles using only proximity sensor information in simulation. In order to iterate through possible control mechanisms without physical skin units we must cover a robot with skin units in simulation. Simulated robotic skin will allow us to rapidly iterate through control prototypes and easily share our work with collaborators that don’t have access to proper hardware. 

Simulated skin units will be represented by a uniform distribution of single point laser scans emanating from the surface of the robot. Ideally, skin unit coverage will be automated to easily change coverage density.

*Please email [Kandai](mailto:kandai.watanabe@colorado.edu) or [Caleb](mailto:caleb.escobedo@colorado.edu) if you would like to learn more about the current project, or would like to collaborate with us!*
