---
title: Cooperative Object Manipulation
description: Reinforcement learning for multi-robot cooperation
author: Joewie J. Koh
permalink: cooperative_object_manipulation.html
tags: [research]

subcategory: research
---

{% include image.html url="research/cooperative_manipulation.png" max-width="75%" description="Two robots cooperatively manipulating the same object." %}

While deep reinforcement learning (RL) has been successful in various robot control problems, most applications have been in single-agent settings. Despite the promise of multi-robot systems, challenges such as a large number of degrees of freedom (DoFs) and heterogeneous physical constraints complicate the dominant paradigm of centralized learning due to issues of scalability. The alternative of parallel implementations of single-agent RL on different agents in the environment scale better, but ignoring agent-agent interactions can lead to learning instability. In our work, we propose and validate two distributed multi-agent RL approaches in the setting of cooperative object manipulation.

# Method
We consider a setting where the agents share the common observed state but try to individually learn a deterministic policy. In distributed approximate RL (DA-RL), each agent applies Q-learning with individual reward functions being coupled and aligned to the goal of the cooperative task. In game-theoretic RL (GT-RL), the agents update their Q-values based on the Nash equilibrium of the bimatrix game of estimated Q-values. 

## Distributed Approximate RL

DA-RL starts with a specification of individual agent behavior, with the sum of individual agent rewards being a well-defined systemwide reward for the whole multi-agent system. This approach can be seen as a distributed approximation of centralized RL, hence termed distributed approximate RL (DA-RL).

## Game-Theoretic RL

GT-RL uses the Nash equilibrium as the solution concept for the desired outcome from the multi-agent interaction. At the Nash equilibrium, no agent has incentive to change its policy given that the other agent takes the equilibrium policy. Convergence to the Nash equilibrium guarantees the stability of the policies learned by each agent, effectively accounting for the non-stationary nature of multi-agent systems.
