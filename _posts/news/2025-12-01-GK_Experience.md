---
title: ✍️ Seeing is Understanding: Gaze as a Cognitive Signal for Shared Autonomy
description: Why I believe the future of collaborative robotics begins with understanding the human mind
extlink: https://gyanigk.github.io
tags: [research, robotics, shared-autonomy, HRI]
author: Gyanig Kumar
---

# Seeing is Understanding: Gaze as a Cognitive Signal for Shared Autonomy

Over the past year at the Collaborative AI and RObotics (CAIRO) Lab and the Human Interaction and RObotics (HIRO) Group at the University of Colorado Boulder, I have been fortunate to work at the intersection of robotics, cognition, and human-centered autonomy. The deeper I go into this space, the clearer one idea becomes:

> Robots fail at collaboration not because they lack perception or motion-planning, but because they do not understand *how humans think*.

The frontier of shared autonomy is moving beyond recognizing objects or generating trajectories. Real collaboration requires robots that anticipate human intent, detect uncertainty, and adapt when things go wrong. And among all human signals, **gaze is one of the most powerful and under-utilized cognitive cues.**

---

## Why Gaze Matters

When a person interacts with the world, their eyes reveal far more than their actions. Gaze encodes search, attention, verification, hesitation, confidence, uncertainty, and decision-making. It precedes motion and exposes intention sometimes *before the user even realizes their own plan*.

Eye movements are not random; they are predictive of:

- where the human wants the robot to go,
- whom they are signaling to,
- how they are reasoning about a task,
- and whether the task is succeeding or failing.

Yet most collaborative robots today still rely on speech, buttons, interfaces, or joystick teleoperation to infer user state. This creates a layer of friction — a mismatch between how humans communicate and how robots interpret commands.  

To build robots that work with us instead of waiting for us, we need autonomy that interprets human cognition directly.

---

## Building Multimodal Shared Autonomy

At HIRO, I have been working on an end-to-end platform that integrates gaze, multimodal perception, and shared control with the Sawyer robot. This involved:

- joystick and Relaxed-IK teleoperation,
- RealSense RGB-D vision for scene understanding,
- GraspNet and segmentation for grasp proposals,
- prompting and inference through Vision-Language Models, and
- real-time integration with Tobii Glasses 3 for streaming gaze.

Together with collaborators in the lab, we built the first combined pipeline that synchronizes:

**Gaze + Sawyer + VLMs + shared autonomy.**

It allows the robot to “see through the user’s eyes” and infer their goal from visual fixation and attention shift rather than explicit commands.

The more we experimented, the more a pattern emerged:

> **Most shared autonomy failures are predictable — and gaze reveals them first.**

Incorrect intent inference, delayed autonomy, misaligned grasps, and unexpected user intervention often show up in gaze before in control signals or motion.

This led us to a new idea:
gaze is not only a signal for intent recognition, but also for *failure-aware autonomy*.

---

## When Autonomy Should Transfer—And When It Should Not

Human-robot collaboration breaks not when a robot does the wrong thing, but when the robot does the right thing at the wrong moment.

Gaze offers the earliest signal that:
- the user is uncertain,
- the task is diverging,
- or autonomy activation is misplaced.

We are now studying how gaze can:
- detect and recover from failures,
- dynamically adjust level of autonomy,
- guide shared-control decisions,
- and detect user confusion or distraction.

Instead of waiting for explicit commands or overrides, the robot learns to interpret the user’s cognitive state.

This is not about building a better user interface — it is about building robots that reason about what humans are thinking.

---

## From Workspace Optimization to Cognitive Modelling

This direction complements two major projects in the lab:

- **SAWO (Shared Autonomy Workspace Optimization)** — using workspace geometry to reduce ambiguity and improve intent recognition.
- **CRED (Counterfactual Reasoning and Environment Design)** — leveraging simulations to evaluate preference-learning and uncertainty.

The physical space, the task, and the interaction dynamics all shape cognition. Our research shows that autonomy works best when *the robot and the environment adapt to the human’s mental model*, not the other way around.

---

## Why This Matters

If robots are going to assist at home, support rehabilitation, help in manufacturing, or collaborate in shared spaces, they will need to do more than track trajectories. They will need to:

- read human intent,
- understand uncertainty,
- predict failures,
- and adapt to diverse users.

This is why I believe gaze is a foundational signal for cognitive-aware robotics. It helps bridge the gap between perception and understanding — between seeing and interpreting.

> The future of shared autonomy is not simply more autonomy.  
> It is autonomy that knows when to act, when to wait, and when to help.

---

## What’s Next

I am currently working on experiments that log gaze heatmaps, robot state, multimodal perception, joystick commands, and VLM predictions during failure situations. The goal is simple but ambitious:

**robots that recover when collaboration breaks down.**

The more we explore this space, the closer we get to robots that collaborate like teammates, not tools.

If you are excited about working at the intersection of cognition, autonomy, and robotics, HIRO is a remarkable place to grow as a researcher. I am incredibly grateful to have had the opportunity to contribute to this direction — and I look forward to what comes next.



