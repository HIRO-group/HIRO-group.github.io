---
title: Research (Anuj)
description: Dexterous Manipulation
author: Anuj Pasricha
---

{% include image.html url="misc/npm_capability.png" max-width="100%" description="An object (green) is located between obstacles (red), i.e. in an ungraspable pose that is out of reach for the robot's end-effector. The robot pokes the object into a more easily graspable configuration, then performs a pick-and-place operation to get the object to its goal state. Work into skill modeling and multimodal planning can enable such behavior." %}

Humans are highly dexterous in their interactions with real-world objects, engaging naturally in multiple forms of manipulation that involve grasping, pushing, poking, rolling, and tossing objects. Robots, on the other hand, tend to primarily rely on prehensile (grasping) manipulation, which is limiting the breadth of applicability of robot technologies in the real world. In order for robotic manipulation to approach human levels of dexterity, robots can benefit from engaging in non-prehensile manipulation (NPM).

NPM offers a complementary solution to prehensile manipulation by significantly expanding the size (intended as the set of reachable configurations) and dimensionality (intended as the number of degrees of freedom) of the operational space of even the simplest robot manipulator. NPM primitives such as pushing, flipping, and tossing can serve different purposes, from re-arranging objects in the workspace (e.g. poking an object out of clutter) to reducing uncertainty (i.e. engaging in forceful interactions with objects to improve perception through physical contact). In other words, NPM can be used to manipulate objects when conventional grasping-based manipulation is infeasible or unnecessary, removing or diminishing a source of planning complexity. Our preliminary work focuses on modeling poking manipulation as a fundamental NPM primitive from which we can suitably derive models for a rich set of related motion primitives---namely, pushing, flipping/tilting, and rolling. Pushing can be thought of as constant-contact poking, while flipping, tilting, and rolling are particular form of poking for objects of specific geometries. Therefore, work on poking manipulation will yield key insights into other NPM primitives. To this end, we are investigating analytical, learned, and hybrid models for poking.

In addition to NPM skill modeling, leveraging traditional sampling-based motion planning can allow us to build a synergistic multimodal planning framework that further enhances robot dexterity. Realistic robot applications might expect the robot to operate in dense clutter, in presence of occlusions, or in ungraspable configurations---for example, if the target object is too large or too heavy, or if it is in a pose that is not directly reachable by the end-effector. In such situations, it is beneficial to complement the robot's skillset with NPM primitives.

This vision enables the decoupling of skill modeling and motion planning, allowing for platform-independent and application-driven robot dexterity...without learning from scratch as current reinforcement learning approaches in this area require.