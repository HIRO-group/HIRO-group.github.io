---
title: Autonomous Coordination of Cooperative Multi-Robot Systems
description: Multi-Agent Reinforcement Learning for Robot Control
author: Joewie J. Koh and Guohui Ding
permalink: research/cooperative_multirobot_systems.html
image:
    feature: research/multirobot/cooperative_manipulation.png
    size: 75%
excerpt_separator: <!-- More -->
---

Robotic systems with heterogeneous teams of cooperating robots have the potential to be successful even in uncertain environments.
With a reasonable distribution of roles among agents, a multi-robot system can be imbued with capabilities that are more than the sum of its parts by coordinating multiple agents to cooperatively accomplish common goals; using search and rescue as an example, cooperation between unmanned aerial and ground vehicles could increase the odds of success with larger search areas and better mobility.
However, autonomous coordination of robots cannot rely on predefined rules or simple control schemes.
Robots are both creators and users of data, and appropriate decision-making models that map observed data to actions can endow a multi-robot system with intelligent behaviors that improve cooperation.

<!-- More -->

{% include image.html url="research/multirobot/cooperative_manipulation.png" max-width="75%" description="An object too heavy or unwieldy for a single robotic arm could be manageable for two cooperating robots. Robots cooperating as needed could increase the efficiency of robotic systems, as the robots can work on independent tasks at other times." %}

# Challenges

One of the main challenges in intelligent robotics is interaction with the environment to achieve a goal, which motivates the question of "how a robot should learn to manipulate the world around it" [1].
As a decision-making model, reinforcement learning (RL) has been widely studied in the multi-agent context because of its performance in a broad range of applications.
Compared to classical optimal control methods for robot manipulation, RL requires less system knowledge for modeling and circumvents analytical intractability using approximations and a data-driven approach [2].
However, research in multi-agent RL for multi-robot control is still in its infancy because of the following challenges:
 1. **Stability of the learning process.**
 This issue arises because an agent's observed transition function is unstable when its counterparts' policies are not stationary.
 Instead of parallelizing the single-agent RL model, we should consider how to coordinate the robot-robot interaction as it determines the success or failure of policy learning.
 2. **Alignment of individual objectives to the system-wide objective.**
 Autonomy in multi-robot systems has to entail not just the agents' amenability to coordinate actions with one another, but also the capability to make decisions based on the agents' personal requirements.
 The proposed methods should accommodate these private concerns without losing sight of the system-wide objective.
 3. **Finding a reasonable learning objective and training framework.**
 The global state-value function can be optimized with centralized learning, but that results in poor scalability.
 Parallelized independent RL is sufficiently scalable, but has no performance guarantees; ignoring the equilibrium among agents might result in higher state-value functions in aggregate, but at the expense of certain agents' performance.
 Considering these tradeoffs, how should we design a multi-agent RL framework?

[1] Oliver Kroemer, Scott Niekum, and George Konidaris, "A review of robot learning for manipulation: Challenges, representations, and algorithms," Jul. 2019, arXiv:1907.03146.  
[2] Jens Kober, J. Andrew Bagnell, and Jan Peters, "Reinforcement learning in robotics: A survey," _The International Journal of Robotics Research_, vol. 32, no. 11, pp. 1238--1274, Sep. 2013, doi:10.1177/0278364913495721.

# Methods

In this work, we propose several competing approaches for the problem of distributed multi-agent RL-based systems.
Our proposed methods rely on novel agent-agent negotiation mechanisms enabled by information sharing between agents, and are motivated by a desire to mitigate adverse impacts of agent interactions on the policy learning process.

## Value-Decomposition Reinforcement Learning

We start with a well-defined global system objective that can be expressed as a system-wide reward function.
It is useful to think of this as the reward function appropriate for centralized RL to succeed at the task (ignoring issues of scalability).
Moreover, this reward function should capture both the final objective (e.g., target position to which an object should be transported) and task considerations (e.g., not dropping the object during transportation).
In the context of cooperative tasks, the task considerations often encode the agent-agent interactions in the system (e.g., the two robots need to always be a fixed distance apart).

With this system objective, we can assign responsibilities to the different agents via their individual reward functions.
This is done by decomposing the system-wide reward function into its constituent terms, and distributing these terms to the individual reward functions.
This method of forumlating individual reward functions assures that each agent's reward function is well-aligned with the system objective, and establishes a good distributed approximator of centralized RL.

Furthermore, we also show in our work that following this scheme for distributed RL results in the distributed optimal policies being the optimal solution due to the global Q-value being the linear combination of individual Q-values.
In other words, because we obtain improved global Q-values from better estimates of individual Q-values, we can estimate the global policy through distributed policies.
Accordingly, we term this method _value-decomposition RL_ (VD-RL).

## Game-Theoretic Reinforcement Learning

It is also possible to model the cooperation problem from a game-theoretic perspective: using the Nash equilibrium as the solution concept for the desired outcome from the multi-agent interaction. 
The key insight here is that no agent has incentive to change its policy at the Nash equilibrium if the other agent follows the equilibrium policy.

Specifically, we approach the task with a general-sum Markov game formalism, and decompose the game into a sequence of stages.
Notably, the Nash equilibrium of the bimatrix game at each stage is also part of the Nash equilibrium of the Markov game.
Through taking equilibrium-guided actions at each stage, the agents update their policies with a deep RL framework.
We claim that _game-theoretic RL_ (GT-RL) accounts for the non-stationary nature of multi-agent systems because convergence to the Nash equilibrium guarantees stability of the learned policies.

## Stackelberg Learning in Cooperative Control

With the above methods, we considered a setting where the agents share the common observed state. 
This is not always feasible or realistic: agents might have asymmetric capabilities and be differentially limited by various constraints, whether perceptual, communicative, locomotive, or computational.
Besides introducing different observation scopes between agents, this asymmetry might also manifest as agent-wise private preferences.

{% include image.html url="research/multirobot/cooperative_transport.jpg" max-width="50%" description="Two mobile robots cooperatively transporting an object. The robots could have different perceptual capabilities, resulting in observation asymmetry. We can also imagine other forms of heterogeneity; for example, two different models of robots could have different turning radii, resulting in locomotive asymmetry." %}

To address these issues, we introduce a framework that accounts for the relationship between perception asymmetry and agent utility.
Critically, at least one agent in the system needs to be aware of agent interactions.
Since deriving the interaction dynamics requires an agent to observe the complete state, we require the agent with complete state perception to be responsible for obeying constraints of the common goal, i.e. its utility is dependent on both agents' decisions.
A vital advantage of this framework is that there is less emphasis on the capabilities of individual agents; in robotic applications, this might mean that we need only equip a single agent with the full suite of sensors typically required for the task.

We model the asymmetric cooperation problem as a partially observable stochastic game (POSG) that can be decomposed into a sequence of Stackelberg bimatrix games.
Similarly to GT-RL, the agents take actions at each step based on the Stackelberg equilibrium, and the sequence of Stackelberg equilibria approximates the equilibrium of the POSG.
With the game-theoretic negotiation mechanism, our method implicitly accounts for the agents' private preferences in the decision-making process.
Furthermore, should the private preferences change, the implicit treatment allows for much quicker adaptation compared to the centralized learning paradigm, by virtue of the drastically reduced dimensionality of the Q-value space.

# Future Work

There are a number of promising directions for future work:
 - human-aware adaptation in multi-agent systems,
 - cooperative control in continuous action spaces,
 - packet loss or latency during agent-agent communication.
