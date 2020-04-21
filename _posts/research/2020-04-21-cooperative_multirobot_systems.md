---
title: Autonomous Coordination of Cooperative Multi-Robot Systems
description: Reinforcement Learning for Distributed Control of Multiple Agents
author: Joewie J. Koh
permalink: research/cooperative_multirobot_systems.html
image:
    feature: research/multirobot/cooperative_manipulation.png
    size: 75%
excerpt_separator: <!-- More -->
---

Robotic systems with heterogeneous teams of cooperating robots have the potential to fundamentally change the paradigm of robotization. 
These multi-robot systems hold the promise of drastically expanding industrial robotic applications: by coordinating multiple agents to cooperatively accomplish common goals, a system can be imbued with capabilities that are more than the sum of its parts.
For example, while a team of robots might typically work independently, the occasional object that is too unwieldy or heavy for a single robot to manage could be cooperatively transported by a pair of robots.
The emphasis on modularity allows for improved efficiency, robustness, and flexibility, reducing the capital requirement for state-of-the-art robotic systems and enabling more accessible automation across all segments of industry.

<!-- More -->

{% include image.html url="research/multirobot/cooperative_manipulation.png" max-width="75%" description="An object too heavy or unwieldy for a single robotic arm could be manageable for two cooperating robots. Robots cooperating as needed could increase the efficiency of robotic systems, as the robots can work on independent tasks at other times." %}

# Challenges

Despite the additional capabilities that multi-robot systems could offer, research in multi-robot control is still in its infancy.
The high number of degrees of freedom and the coupling of multiple kinematic and dynamic constraints pose challenges for both traditional model-based control and model-free learning, the two classes of methods typically used for robot control.

Additionally, model-based methods require knowledge of system kinematics and dynamics, and are therefore difficult to employ in unstructured environments regardless of the number of robots.
Model-free deep reinforcement learning (RL), conversely, does not have this limitation and has thus seen significant recent interest from the robotics community.
However, much of this work have been in the single-robot setting—successfully applying RL in multi-robot systems requires addressing the issues mentioned in the previous paragraph. One approach involves deviating from the centralized learning paradigm and training multiple agents in parallel. Unfortunately, naive distributed RL ignores agent interactions and can lead to instability in the policy learning process.

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
