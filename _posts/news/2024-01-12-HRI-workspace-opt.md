---
title: 📑 Paper on workspace optimization to improve human motion prediction accepted to HRI 2024!
description: Configure workspace to improve human legibility
tags: [news]
author: Yi-Shiuan Tung
---

The canonical approach for human robot interaction is to first predict the human motion and then generate a robot plan. This requires a robust and accurate predictions of human behavior. If the human models are inaccurate, the robot may produce unsafe interactions. Our work takes a different approach and addresses a fundamental challenge faced by all human motion prediction models; **we reduce the uncertainty inherent in modeling the intentions of human collaborators by pushing them towards legible behavior via environment design**. Our work improves human motion model predictions by increasing environmental structure to reduce uncertainties, facilitating more fluent human-robot interactions.

We present an algorithmic approach to configure the workspace. We incorporate a legibility metric that considers all the possible goals the human might be reaching for at a given stage of task execution and the probability of correctly predicting the human's chosen goal. Finding the optimal environment by simply iterating through all possible workspace configurations quickly becomes intractable as the number of objects or possible states increases. To address this, we use a quality diversity algorithm called MAP-Elites to search for environments that best elicit legible human behavior. Instead of finding a single optimal solution, MAP-Elites produces a map of performant solutions along dimensions of a feature space chosen by the designer. MAP-Elites enables efficient and extensive exploration of complex search spaces, leading to higher quality solutions as compared to other search algorithms.

Take a look at the [project website](https://yi-shiuan-tung.github.io/blog/2024/workspace-optimization/) for more information!

<div align="center">
<img width="500" src="{{ site.baseurl }}/img/research/algo-social-hri/human_legibility.png"/>
</div>
<p align="justified" style="font-style: italic">
Suppose that you are picking up the blue square cube (left). The natural path (solid) makes it hard for the robot to predict whether you are picking up the blue square cube or the red triangle cube while the legible path (dotted) requires you to take a circuitous route. To improve a robot's prediction of a human teammate's goals during a collaborative task (right), the robot can configure the workspace by rearranging objects and projecting "virtual obstacles" in augmented reality (cyan and red barriers), in order to induce naturally legible paths from the human.
</p>
