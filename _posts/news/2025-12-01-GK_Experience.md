---
title: "✍️ Seeing Is Understanding: Gaze as a Cognitive Signal for Shared Autonomy"
description: Modeling intent, uncertainty, and timing through gaze to enable robust human robot collaboration
author: Gyanig Kumar
permalink: research/gaze_shared_autonomy.html
category: [research, robotics, human robot interaction, shared autonomy, research highlight]
excerpt_separator: <!-- More -->
---

When people collaborate with a robot, they rarely communicate intent through a single channel. Intent emerges through how a person looks, hesitates, verifies, commits, and corrects. Humans coordinate smoothly with new teammates because they can infer these cognitive signals quickly and adjust their behavior before misalignment becomes costly. Many autonomous systems still lack this capability. They respond primarily to overt action, such as joystick commands or end-effector motion, and they often discover misalignment only after the human intervenes.

This post argues for a simple principle. **If we want shared autonomy that feels collaborative, robots must infer cognitive state, not just control state.** Gaze is a uniquely valuable signal for this because it is continuous, low latency, and tied to decision dynamics. When fused with perception and robot state, gaze supports belief over intent and uncertainty that can drive timing-sensitive autonomy.

<!-- More -->

## Why Gaze Matters for Shared Autonomy ?

Most shared autonomy pipelines infer intent from observable behavior. That can work in structured settings, but it breaks down when goals are ambiguous, when users reconsider mid-action, or when task context evolves. Gaze provides information earlier than control alone because it often changes before a decision becomes an action.

In cognitive terms, gaze reflects search, comparison, verification, hesitation, and goal revision. In robotics terms, this suggests a partially observable interaction model in which gaze acts as an observation of latent human state, such as intent and uncertainty.

{% include image.html
   url="research/gaze-hri/eyegaze.jpg"
   max-width="60%"
   description="Human gaze trajectories overlaid on task-relevant objects during a collaborative manipulation task. Fixation patterns and gaze shifts often precede physical action, revealing intent formation and hesitation before control input."
%}

### From Intent Prediction to Belief Over Goals

A useful way to formalize collaboration is to maintain a belief over possible goals rather than committing to a single predicted intent. In practice, the robot can represent a set of candidate goals and update a belief distribution conditioned on multimodal observations. Gaze contributes evidence about which hypotheses are plausible and how stable the human plan is over time.

This shifts the problem from classification to inference under uncertainty. Instead of asking what the goal is, the robot asks how confident it should be, how quickly confidence is changing, and whether the human is reconsidering.

<!-- --- -->

### Dual-Task Interaction and Cognitive Load

In many realistic settings, humans distribute attention across multiple modalities. A person may visually inspect objects while simultaneously speaking, issuing partial commands, or verbally clarifying intent. These dual-task scenarios introduce additional cognitive load and often amplify hesitation or instability in intent.

For shared autonomy, this means that gaze should not be interpreted in isolation. Instead, gaze and verbal behavior together provide complementary signals about how intent is forming, how confident the user is, and whether clarification or delay is appropriate.

{% include image.html
   url="research/gaze-hri/verbal_system_dualtask.png"
   max-width="65%"
   description="Dual-task interaction scenario combining teleoperation and verbal input. Concurrent modalities provide complementary evidence about intent formation, uncertainty, and cognitive load, informing when autonomy should assist, wait, or request clarification."
%}

<!-- --- -->

### Timing-Sensitive Autonomy

In collaboration, many failures are not wrong actions. They are poorly timed actions. Assistance that triggers during hesitation can feel like interruption. Assistance that triggers too late becomes unhelpful. Timing is therefore a core part of shared autonomy.

Gaze is useful here because it can signal hesitation, goal instability, and divergence between what the human expects and what the robot is doing. These signals can drive an arbitration policy that decides whether to assist, wait, request clarification, or switch strategy.

<!-- --- -->

## Gaze-Conditioned Adaptive Autonomy

A practical architecture for gaze-conditioned shared autonomy typically contains four layers.

First, sensing and synchronization align gaze, perception, and robot state in time. Second, perception builds a task-relevant scene representation, such as objects, poses, and affordances. Third, inference estimates belief over goals and uncertainty, using gaze features such as fixations, transitions, and dispersion. Fourth, arbitration modulates autonomy as a function of uncertainty and context, producing behavior that can assist, pause, or clarify.

{% include image.html
   url="research/gaze-hri/gaze_system.png"
   max-width="75%"
   description="System diagram for gaze-conditioned adaptive autonomy. Gaze, perception, and robot state are fused into an interaction belief state that modulates autonomy allocation and recovery behaviors."
%}

<!-- --- -->

### Interaction-Aware Design: Environment, Task, and Policy Co-Design

Human cognition is shaped by environment structure. Layout, object spacing, and affordance overlap influence how ambiguous a task appears and how gaze behaves. This suggests that robust collaboration is not only about better models, but also about better task and environment design. An interaction-aware view asks how the workspace can be organized to reduce ambiguity, how the robot can present options to support human intent, and how recovery behaviors can be triggered when belief diverges.

<!-- --- -->

### Why This Matter ?

Shared autonomy for homes, rehabilitation, manufacturing, and public spaces requires more than accurate control. It requires the robot to understand when a person is committed, uncertain, or revising their plan. Gaze provides a principled bridge between perception and cognition that can support safer timing, smoother assistance, and earlier recovery when collaboration begins to break down.

<!-- --- -->

### Future Work

There are several directions that naturally follow from this view.

One direction is better calibration of uncertainty so that arbitration decisions are reliable across users, tasks, and sensing conditions. A second direction is learning interaction-repair policies that use gaze and belief dynamics to decide when to pause, when to clarify, and when to adapt autonomy allocation. A third direction is studying how environment and interface choices shape gaze behavior and intent ambiguity, enabling system-level co-design for robust collaboration.

<!-- *If anything on this page piques your interest, feel free to email Gyanig at gyanig.kumar@colorado.edu. If you are reaching out about a question, include [Q] in the subject line. If you want to discuss collaboration, include [C] in the subject line.* -->
