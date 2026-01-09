---
title: "✍️ Seeing Is Understanding: Gaze as a Cognitive Signal for Shared Autonomy"
description: Modeling intent, uncertainty, and timing through gaze to enable robust human robot collaboration
author: Gyanig Kumar
category: [research, robotics, human robot interaction, shared autonomy, research highlight, social intelligence]
excerpt_separator: <!-- More -->
---

When people collaborate with a robot, they rarely communicate intent through a single channel. Intent emerges through how a person looks, hesitates, verifies, commits, and corrects. Humans coordinate smoothly with new teammates because they can infer these cognitive signals quickly and adjust their behavior before misalignment becomes costly. Many autonomous systems still lack this capability. They respond primarily to overt actions, such as joystick commands or end-effector motion, and often discover misalignment only after the human intervenes. Current research pushes efforts to build better teleoperation, improve action decoding, and fine-tune models for varied real-world applications.

This post argues for a simple principle. **If we want shared autonomy that feels collaborative, robots must infer cognitive state, not just control state.** Past research in human–computer interaction and robotics has shown that human eye gaze is a uniquely valuable signal because it is continuous, low latency, and tightly coupled to decision dynamics. When fused with perception and robot state, gaze supports a belief over intent and uncertainty that can drive timing-sensitive autonomy. While the benefits of eye gaze seem immense, a definitive structure or framework for utilizing it still lacks. In research studies, gaze is a difficult modality to compare against standardized benchmarks, and multimodal fusion is still predominantly grounded in verbal communication frameworks derived from large language models. My work aims to build richer sensor fusion systems—robots that perceive through human eye gaze, sense through skin-like touch and reflexes, and converse in ways that resemble human interaction.

<!-- More -->

## Why does different input modalities matters for Shared Autonomy ?

Most shared autonomy pipelines infer intent from observable behavior. This can work in structured settings, but it breaks down when goals are ambiguous, when users reconsider mid-action, or when task context evolves. Gaze provides information earlier than control signals alone because it often shifts before a decision manifests as physical action.

In cognitive terms, gaze reflects search, comparison, verification, hesitation, and goal revision. In robotics terms, this suggests a partially observable interaction model in which gaze acts as an observation of latent human state, such as intent and uncertainty.

{% include image.html
   url="./research/gaze-hri/eyegaze.jpg"
   max-width="60%"
   description="Human gaze trajectories overlaid on task-relevant objects during a collaborative manipulation task. Fixation patterns and gaze shifts often precede physical action, revealing intent formation and hesitation before control input."
%}

### From Intent Prediction to Belief Over Goals

A useful way to formalize collaboration is to maintain a belief over possible goals rather than committing to a single predicted intent. This behavior is neither purely stochastic nor deterministic; rather, it is highly conditional. In practice, the robot can represent a set of candidate goals and update a belief distribution conditioned on multimodal observations. This perspective is reflected in several research efforts, one such is Cartella, Giuseppe, et al., “Modeling Human Gaze Behavior with Diffusion Models for Unified Scanpath Prediction.” Gaze contributes evidence about which hypotheses are plausible and how stable the human plan is over time.

This reframes the problem from classification to inference under uncertainty. Instead of asking what the goal is, the robot asks how confident it should be, how quickly that confidence is changing, and whether the human is reconsidering or anticipating.

<!-- --- -->

### Dual-Task Interaction and Cognitive Load

In many realistic settings, humans distribute attention across multiple modalities. A person may visually inspect objects while simultaneously speaking, issuing partial commands, verbally clarifying intent, or physically interacting with objects. These dual-task scenarios introduce additional cognitive load and often amplify hesitation, which can obscure true intent.

For shared autonomy, this means gaze should not be interpreted in isolation. Instead, gaze and verbal behavior together provide complementary signals about how intent is forming, how confident the user is, and whether clarification or delay is appropriate. This naturally connects to the problem of mechanical interpretability in large language models, which will be a key element in designing frameworks for cognitive understanding in robotics.

{% include image.html
   url="research/gaze-hri/verbal_system_dualtask.png"
   max-width="65%"
   description="Dual-task interaction scenario combining teleoperation and verbal input. Concurrent modalities provide complementary evidence about intent formation, uncertainty, and cognitive load, informing when autonomy should assist, wait, or request clarification."
%}

<!-- --- -->

### Timing-Sensitive Autonomy

In collaboration, many failures are not the result of incorrect actions, but of poorly timed ones—often due to inference limitations in robotic systems. Assistance that triggers during hesitation can feel intrusive, while assistance that arrives too late becomes unhelpful. Timing is therefore a core component of shared autonomy.

Any modality is useful here if it can signal hesitation, goal instability, or divergence between human expectation and robot behavior. These signals can drive an arbitration policy that decides whether to assist, wait, request clarification, or switch strategies.

<!-- --- -->

## Gaze-Conditioned Adaptive Autonomy

A practical architecture for gaze-conditioned shared autonomy typically consists of four layers.

First, sensing and synchronization align gaze, perception, and robot state in time. Second, perception constructs a task-relevant scene representation, such as objects, poses, and affordances. Third, inference estimates belief over goals and uncertainty using gaze features such as fixations, transitions, and dispersion. Fourth, arbitration modulates autonomy as a function of uncertainty and context, producing behaviors that assist, pause, or request clarification.

{% include image.html
   url="research/gaze-hri/gaze_system.png"
   max-width="75%"
   description="System diagram for gaze-conditioned adaptive autonomy. Gaze, perception, and robot state are fused into an interaction belief state that modulates autonomy allocation and recovery behaviors."
%}

While the research continues to improve upon individual functional capabilities of robots, task scenarios remain an important direction for executing and validating these ideas. If we consider tasks from environments such as robosuite, extending them toward cognitively rich shared autonomy scenarios would require long-horizon planning algorithms capable of leveraging human feedback. Many physical tasks studied today are one-off executions, often focused on actions that are simple for humans yet difficult for robots, such as cloth folding. A cognitive task environment, by contrast, would entail mutual dependency between human and robot—something closer to science-fiction scenarios like Interstellar, where a robot performs docking maneuvers in coordination with a human pilot. However, the robotics community is still far from such scenarios, and current efforts largely focus on industry-level tasks or home assistance.

<!-- --- -->

### Interaction-Aware Design: Environment, Task, and Policy Co-Design

Human cognition is shaped by environmental structure. Layout, object spacing, and affordance overlap influence how ambiguous a task appears and how humans behave. This suggests that robust collaboration is not only about better models, but also about better task and environment design. An interaction-aware perspective asks how workspaces can be organized to reduce ambiguity, how robots can present options to support human intent, and how recovery behaviors can be triggered when belief diverges.

<!-- --- -->
<!-- 
### Why This Matter ?

Shared autonomy for homes, rehabilitation, manufacturing, and public spaces requires more than accurate control. It requires the robot to understand when a person is committed, uncertain, or revising their plan. Gaze provides a principled bridge between perception and cognition that can support safer timing, smoother assistance, and earlier recovery when collaboration begins to break down. -->

<!-- --- -->

### Future Work

There are several directions that naturally follow from this view.

One direction is better calibration of uncertainty so that arbitration decisions remain reliable across users, tasks, and sensing conditions. A second direction involves learning interaction-repair policies that use gaze and belief dynamics to decide when to pause, clarify, or adapt autonomy allocation. A third direction is studying how environment and interface design shape gaze behavior and intent ambiguity, enabling system-level co-design for robust collaboration. A fourth direction explores the mechanical interpretability of LLMs, VLMs, and VLAs for designing cognitively grounded robotic agents. Shared autonomy for homes, rehabilitation, manufacturing, and public spaces ultimately requires more than accurate control, it requires robots that understand when a person is committed, uncertain, or revising their plan.

<!-- *If anything on this page piques your interest, feel free to email Gyanig at gyanig.kumar@colorado.edu. If you are reaching out about a question, include [Q] in the subject line. If you want to discuss collaboration, include [C] in the subject line.* -->
