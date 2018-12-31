---
title: Student Projects
description: List of student projects for Spring 2019
permalink: student_projects.html
---

# Contents
{:.no_toc}

* This line will be replaced by the ToC, excluding the "Contents" header
{:toc}


# Algorithmic Human-Robot Interaction [a-HRI] :robot:

Human-Robot Collaboration [HRC] is tasked with designing algorithms and systems for humans and robots to work together. At its highest level of abstraction, we want to maximize the human-robot team efficiency, in order for our robots to be better collaborators and workers. Crucial to this is the development of interfaces that are as natural and transparent to the user as possible, in order to reduce the barrier to entry for humans to take advantage of the human-robot team. This requires scientists to draw upon research from other disciplines (Human-Computer Interaction, Neurosciences, Psychology, Cognitive Sciences, Natural Language Processing, Machine Learning, Computer Vision) in order to develop systems that are able to detect what the human partner is doing, predict what she will do next, and efficiently exchange information with her.

Below, there is a non-comprehensive list of projects in this area. If you are interested in any of them, please [send me an email](mailto:{{ site.email }})!! Feel free to integrate and/or expand on this with your own ideas and interests.

 * Language enabled agents
 * Human detection and sensing
 * Augmented/virtual reality
 * Reinforcement learning for HRC
 * Cognitive systems to transfer knowledge to and from the human (humans teaching robots, robots teaching humans)
 * High-level transfer learning and self adaptation to unforeseen circumstances

# Physical Human-Robot Interaction [p-HRI] :robot:

One of the current limitations of even the most advanced robots is the fact that their capabilities are limited to very simple actions (e.g., pick-and-place).  A new generation of robot controllers and motion planners is needed for robots to be more capable and useful in most of the domains they are currently employed (factories, search and rescue) and the domains they will be employed in the near future (hospitals, households, roads).
In particular, robots should be able to perform better when they are co-located with humans, and should not shy away from engaging in close, _elbow-to-elbow_ collaboration with them.

> *To date, robot controllers largely concentrate on the end-point as the only part that enters in physical contact with the environment. The rest of the body is typically represented as a kinematic chain, the volume and surface of the body itself rarely taken into account. Sensing is dominated by “distal” sensors, like cameras, whereas the body surface is “numb”. As a consequence, reaching in cluttered, unstructured environments poses severe problems, as the robot is largely unaware of the full occupancy of its body, limiting the safety of the robot and the surrounding environment. **This is one of the bottlenecks that prevent robots from working alongside human partners.*** [Roncone et al. 2015]

We think we should do better. We think that, if we equip robots with enough information about their surroundings, we can improve their interaction capabilities with the outside world _and_ humans. In particular, artificial tactile systems will be a key enabler to these types of technologies.

Below, there is a non-comprehensive list of projects in this area. If you are interested in any of them, please [send me an email](mailto:{{ site.email }})!! Feel free to integrate and/or expand on this with your own ideas and interests.

 * Development of Artificial Tactile Sensors
 * Distributed robot controllers
 * Reaching in clutter
 * Self-supervised learning of the body model (i.e. the robot kinematics)
 * Exploring tool use and object affordances
 * Immersive, hands-free tele-operation


[//]: <> ## pHRI.1 → _Self modeling_

[//]: <> > *...by 2-3 months, infants engage in exploration of their own body as it moves and acts in the environment. They babble and touch their own body, attracted and actively involved in investigating the rich intermodal redundancies, temporal contingencies, and spatial congruence of self-perception.* [Rochat, 1998]

[//]: <> By starting with as little information as possible, it is possible to compute a reliable enough kinematic model from self-observation and exploration of the consequences of the robot's actions.

[//]: <> > *This process calibrates the robot's kinematic model to its vision model, producing a unified model that allows kinematic and visual information to be meaningfully combined. The presented model is demonstrated to predict end-effector position in the visual field. The robot further refines this combined kinematic-visual model by minimizing the distance between the predicted and observed positions of its end-effector in its visual field. The fact that the robot learns these properties based on first-hand observations of its body, through its sensors, allows the model to adapt to changes in the robot’s configuration on-line. This endows the robot with the ability to adapt its self-model for tool use.* [Hart and Scassellati, 2011]

[//]: <> ### TASK C2. Exploring Tool Use and object affordances If I am able to incorporate a new tool into my internal model, how can I exploit it in order to do new tasks? In summary: what the robot is capable or not capable of doing after training with a tool, w.r.t. the previous experience. See Hart and Scassellati [2011], Tikhanoff et al [2013].

[//]: <> ### TASK C3. Kinematic self calibration

[//]: <> By starting from a known kinematic model, it is possible to compensate for systematic errors by means of visuo-kinematic calibration. It improves reaching and visual servoing - see Fanello et al. [2014].
[//]: <> Systematic errors include (i) mismatch between the robot model based on the mechanical design specifications (CAD model) and the actual physical robot; (ii) inaccuracies in joint sensor calibration and measurements; (iii) unobserved variables as for example backlash or mechanical elasticity; (iv) inaccuracies in taxel pose calibration; (v) errors in visual perception due to inaccurate camera calibration. The combination of these sources of error can amount to a total of several centimeters.

[//]: <> There is evidence that, in adult humans, sensory systems are not fixed structures with immutable functions. It is of course widely appreciated that sensory systems can be significantly modified by the input they receive during development. For example, to achieve optimal motor behavior for reaching and grasping, visual and somatic senses must be continually adjusted as different body parts grow at different pace. One might expect such adjustments to proceed very slowly and to be largely restricted to immature organisms, but there is evidence of strong sensory plasticity that can be evoked within minutes in adults. [Volcic et al. 2013]

[//]: <> ## References

[//]: <>  * A. De Luca and F. Flacco [2012]. **Integrated control for pHRI: Collision avoidance, detection, reaction and collaboration**, in *Biomedical Robotics and Biomechatronics (BioRob), 2012 4th IEEE RAS EMBS International Conference on*. June 2012, pp. 288–295. [[PDF]](http://www.dis.uniroma1.it/~labrob/pub/papers/BioRob12.pdf)
[//]: <>  * F. Flacco et al. [2012]. **A depth space approach to human-robot collision avoidance**, in *Robotics and Automation (ICRA), 2012 IEEE International Conference on*. May 2012, pp. 338–345. [[PDF]](http://www-cs.stanford.edu/groups/manips/publications/pdfs/Flacco_2012_ICRA.pdf)
[//]: <>  * P. Rochat [1998]. **Self-perception and action in infancy**. *Experimental Brain Research*. 1998
[//]: <>  * M. Hoffmann et al. [2010]. **Body Schema in Robotics: A Review**. In: *IEEE Transactions on Autonomous Mental Development*. Vol. 2, No. 4, Dec 2010. [[PDF]](http://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.357.6076&rep=rep1&type=pdf)
[//]: <>  * J. W. Hart and B. Scassellati [2011]. **A Robotic Model of the Ecological Self**. In: *Proceedings of the 11th IEEE/RAS International Conference on Humanoid Robots (Humanoids 2011)*. Bled, Slovenia, October 2011. [[PDF]](http://scazlab.yale.edu/sites/default/files/files/hart-humanoids-11.pdf)
[//]: <>  * M. Hersch et al [2008]. **Online Learning of the body schema**. In *International Journal of Humanoid Robotics*. Vol. 5, No. 2, 2008. [[PDF]](http://infoscience.epfl.ch/record/117918/files/IJHR_0502_P161.pdf)
[//]: <>  * Tikhanoff et al. [2013]. **Exploring affordances and tool use on the iCub**. In *Proceedings of the 13th IEEE/RAS International Conference on Humanoid Robots (Humanoids 2013)*. [[PDF]](http://www.poeticon.eu/publications/1335_Tikhanoff_etal2013.pdf)
[//]: <>  * S. R. Fanello et al. [2014]. **3D Stereo Estimation and Fully Automated Learning of Eye-Hand Coordination in Humanoid Robots**. In *Proceedings of the 14th IEEE/RAS International Conference on Humanoid Robots (Humanoids 2014)*. [[PDF]](http://alecive.github.io/papers/2014_Fanello_humanoids_eye_hand_coordination.pdf)
[//]: <>  * R. Volcic et al. [2013]. **Visuomotor Adaptation Changes Stereoscopic Depth Perception and Tactile Discrimination**. In *The Journal of Neuroscience*, Oct 23, 2013.

[//]: <> ## Project D: Better control → _Reaching in clutter_

[//]: <>  * Development of a perception algorithm (kinect-based) able to detect obstacles close to the robot's arms
[//]: <>    * Calibration of camera w.r.t. the robot
[//]: <>    * Detection of the robot arms inside the camera frame
[//]: <>    * Detection of robot - obstacle distances throughout the robot's body

[//]: <>  * Development of a suitable avoidance strategy for the robot
[//]: <>    * Computation of avoidance vectors based on robot-obstacle distances (the one from [Flacco 2012] should suffice)
[//]: <>  * Deployment of the control algorithm on the Sawyer/ROS platform

[//]: <> ## Project E: Hands-free teleoperation

[//]: <> There are many previous works to take inspiration from (and many different techniques have been used). The basic principle is to be able to track the 6 degrees of freedom of the user's hand, and transfer them to the robot's end-effector (with a 6-DOF tracker the problem is fully determined).
[//]: <> The goal would be to develop a robot-agnostic platform (i.e. able to work on both the Sawyer and the KUKA).

[//]: <> ### Attack Plan

[//]: <>  1. Implement a ROS compatible, 6-DOF hand pose tracker.
[//]: <>  2. Implement (or use an existing) an Inverse Kinematic controller for both the robots.
[//]: <>  3. Interface the 6-DOF hand pose tracker with the IK controller.
[//]: <>  4. ...
[//]: <>  5. Profit!

[//]: <> *Disclaimer: if you didn't get the joke, it means you never saw [this video](https://www.youtube.com/watch?v=EmoCuA4-y9E)!*

[//]: <> ### Stretch goals

[//]: <>  Implement a face tracking system able to detect the user's face orientation (3DoF). It can be purely vision based (e.g. the [CLM tracker](https://github.com/TadasBaltrusaitis/CLM-framework)), or use some more complex systems (e.g. see this [Google Glass head teleoperation on the iCub robot](https://www.youtube.com/watch?v=Hw_Yw8LtZTE)).

[//]: <>  Implement a head teleoperation system on the Sawyer robot (2DoF, pan and tilt)

