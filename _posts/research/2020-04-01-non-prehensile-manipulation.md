---
title: Dexterous Robotic Manipulation and Skill Acquisition
description: Non-prehensile manipulation modeling and planning
author: Anuj Pasricha
permalink: research/non_prehensile_manipulation.html
image:
    feature: research/npm/npm_capability.png
excerpt_separator: <!-- More -->
---

Humans are highly dexterous in their interactions with real-world objects, engaging naturally in multiple forms of manipulation that involve grasping, pushing, poking, rolling, and tossing objects. Robots, on the other hand, tend to primarily rely on prehensile (grasping) manipulation, which is limiting the breadth of applicability of robot technologies in the real world. In order for robotic manipulation to approach human levels of dexterity, robots can benefit from engaging in non-prehensile manipulation (NPM).

<!-- More -->

NPM offers a complementary solution to prehensile manipulation by significantly expanding the size (intended as the set of reachable configurations) and dimensionality (intended as the number of degrees of freedom) of the operational space of even the simplest robot manipulator. NPM primitives such as pushing, flipping, and tossing can serve different purposes, from re-arranging objects in the workspace (e.g. poking an object out of clutter) to reducing uncertainty (i.e. engaging in forceful interactions with objects to improve perception through physical contact). In other words, **NPM can be used to manipulate objects when conventional grasping-based manipulation is infeasible or unnecessary, removing or diminishing a source of planning complexity**{:.color-banner}.

{% include image.html url="research/npm/npm_capability.png" max-width="100%" description="An object (green) is located between obstacles (red), i.e. in an ungraspable pose that is out of reach for the robot's end-effector. The robot pokes the object into a more easily graspable configuration, then performs a pick-and-place operation to get the object to its goal state. Work into skill modeling and multimodal planning can enable such behavior." %}

The vision at HIRO for achieving human-like dexterity in robotic manipulation is a three-stage process:

 * _Stage 1 --- Skill Modeling._
   Learning-based approaches are neither scalable nor generalizable and deep learning tools are much too opaque to operate in real-world scenarios on their own. Whereas physics-based approaches, while not requiring any training, make simplifying assumptions that do not represent real-world physics in full detail. Therefore, building **hybrid models for NPM primitives in which physics-based and learning-based approaches complement each other** is an interesting avenue of future work.

 * _Stage 2 --- Multimodal Planning._
   Given models that accurately and precisely represent object and skill dynamics in the real world, the next logical step is to build **a multimodal motion planning framework that incorporates both non-prehensile and prehensile manipulation primitives** to accomplish a variety of tasks.

 * _Stage 3 --- Higher-Order Skill Acquisition._
   Humans are capable of [learning rich representations](https://arxiv.org/pdf/1604.00289.pdf) of complex concepts from very few examples. This allows them to classify new examples, generate new instances of a particular class, parse concepts into parts and relations, and generate new concepts through composition. Equipped with a fundamental set of skills, a robot must learn how to acquire higher-order skills (eg: tool-use) that increase the probability of task success in the real-world. These skills typically require knowledge of object affordances, which can be learned from human demonstration or in simulation. **Having a repository of these affordance-to-motor program mappings can allow robots to combine them in interesting ways to achieve tasks they haven’t been explicitly trained for** (eg: turning a door knob and using a screwdriver are very similar actions conceptually). Learning a conceptual hierarchy will also allow **transferring skills from humans to robots or robots to robots where both parties don’t share the same embodiment**.

# Current Work

Our preliminary work focuses on modeling **poking manipulation as a fundamental NPM primitive** from which we can suitably derive models for a rich set of related motion primitives---namely, pushing, flipping/tilting, and rolling. Pushing can be thought of as constant-contact poking, while flipping, tilting, and rolling are particular form of poking for objects of specific geometries. Therefore, work on poking manipulation will yield key insights into other NPM primitives. To this end, **we are investigating analytical, learned, and hybrid models for poking**.

## Skill Modeling

For robots to operate efficiently in the real world, it is expected from them to be capable to operate in dense clutter, in presence of occlusions, or in hard to grasp configurations. Additionally, at times grasping might not be possible at all---for example, if the target object is too large or too heavy, or if it is in a pose that is not directly reachable by the end-effector. In such situations, it is beneficial to complement the robot's skillset with non-prehensive manipulation primitives.

Poking is a fundamental NPM primitive wherein: i) a robot end-effector applies an instantaneous force to an object of interest to set the object in translational and rotational motion (*impact* phase), and
ii) the object eventually slows down and comes to rest due to Coulomb friction (*free-sliding* phase).

These two phases of poking can be modeled individually and solved in reverse to build an analytical physics model for poking manipulation. Given an object's current and desired poses, we can determine the object's initial translational and angular velocities at impact, which then (through a heuristic-based approach) determines the end-effector velocity necessary to achieve the desired object velocities.

Our current work models poking manipulation as a skill and as a failure recovery mechanism. Specifically, we focus on developing a simple yet effective analytical model for poking that captures essential characteristics of the dynamics of an object **through elementary physics principles**. The **proposed model is independent of object geometry and mass distribution**, and it is **readily available for use with unfamiliar objects** in that it does not require training data.

## Multimodal Motion Planning

{% include image.html url="research/npm/pokerrt_block_diagram.png" max-width="100%" description="<em>PokeRRT</em> planner pipeline---skill thresholding is performed on augmented object configuration space to extract regions of grasping (blue) and poking (green). These skill regions are then used by PokeRRT to plan an object path from a start state to a goal state through augmented object configuration space. In this example, robot pokes object out from between the obstacles and into a more graspable configuration. Then the robot performs a pick-and-place operation to the object's goal configuration." %}

Leveraging traditional sampling-based motion planning can allow us to build a synergistic multimodal planning framework that further enhances robot dexterity. This vision **enables the decoupling of skill modeling and motion planning**, allowing for platform-independent and application-driven robot dexterity without learning from scratch with the introduction of each new skill as current reinforcement learning approaches in this area require. Our most recent contribution in this domain is **the development of the *PokeRRT* algorithm to plan in scenarios that combine poking and grasping manipulation.**

*PokeRRT* leverages goal and obstacle information in the object configuration space to introduce a bias into motion planning and to keep the sampling space low-dimensional to ensure fast planning. It also makes use of the insight that grasping is difficult in narrow spaces and poking would therefore be useful here.

# Future Work

{% include image.html url="research/npm/flip.jpg" max-width="100%" description="This combination of primitives is useful in cases where taking advantage of object geometry can yield low-effort manipulation strategies. For instance, if a cylindrical can is too heavy for a vertical lift, it can be flipped on its side and rolled over to goal state. Specifically, a cylindrical object will start off resting on its base. The robot will flip the object onto its side and then apply a normal force to the object to initiate a rolling motion. Finally, the robot will catch the object at its goal pose." %}

Several streams of work stem from our preliminary work into poke modeling and planning:
* A dynamic approach to skill thresholding in the current *PokeRRT* framework that leverages skill error models.
* Comparison of analytical poking model to its learning-based and hybrid counterparts.
* A multimodal motion planning framework that incorporates 3 or more skills.
* Using the same modeling framework as poking for other NPM skills such as tossing, rolling, and pushing that demonstrates poking as a fundamental NPM primitive.
* Transferring skill models across different robot end-effectors to test model robustness.
* Collecting and analyzing data on model accuracy and precision.
* Building a few-shot tuning framework that allows for model transfer from simulation to real-world.

*Please email [Anuj](mailto:anuj.pasricha@colorado.edu) if anything on this page piques your interest or if you're keen on collaborating. There is a lot of infrastructure engineering work that goes into these projects so help from all levels of technical capability is welcome.*
