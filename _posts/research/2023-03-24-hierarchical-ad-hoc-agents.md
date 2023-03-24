---
title: "HAHA: Hierarchical Ad Hoc Agents"
description: Using hierarchical structures to improve human-agent interaction
author: Stéphane Aroca-Ouellette
permalink: research/haha.html
category: [research, learning and modeling, haha, research highlight]
image:
    feature: research/haha/haha_architecture.png
    size: 50%
excerpt_separator: <!-- More -->
---

When performing collaborative tasks with new unknown teammates, humans are particularly adept at adapting to their collaborator 
and converging toward an aligned strategy. However, state of the art autonomous agents still do not have this capability. 
We propose that a critical reason for this disconnect is that there is an inherent hierarchical structure to human behavior 
that current agents lack. In this research, we explore the use of hierarchical reinforcement learning to train an agent that can 
navigate the complexities of ad hoc teaming at the same level of abstraction as humans. Our results demonstrate that when paired with humans, 
our Hierarchical Ad Hoc Agent (HAHA) outperforms all baselines on both the team's objective performance and the human’s perception of the agent.  
<!-- More -->

# Published Work:
## HAHA: Hierarchical Ad Hoc Agents
The proliferation of autonomous agents in our everyday lives require us to consider how we want these agents to interact with us. 
Increasingly, the AI community has recognized the importance of creating agents that can collaborate effectively with humans. 
Drastic variance in human knowledge, ability, and preference require adaptive agents that can quickly conform to new and unseen teammates---an ability frequently named ad hoc teaming or zero-shot coordination.
Current state of the art methods for developing autonomous agents in multiplayer scenarios, such as self-play, were originally developed for competitive tasks.
However, when applied to cooperative tasks, these methods tend to create agents that behave in rigid patterns and lack the ability to efficiently adapt to new teammates.

Previous work has made valuable strides toward zero-shot coordination by having the training agent play with a teammate who resembles human behavior, 
or play with a diverse set of different teammates that vary in their skill level. However, the majority of this work has focused on low-level agents that output low level actions (e.g *move left, right, up, down*). 
Notably, there is an inherent hierarchical structure to human behavior that these techniques fail to capture. 
Humans utilize task hierarchies to both analyze and manage projects and synchronize with other humans. 
**In this work, We hypothesize that providing an autonomous agent with a similar hierarchical structure**---with high level tasks (e.g. get an onion, serve the soup, ...) that organize low-level actions---**will facilitate human-agent teams to better understand each other and adapt to aligned strategies**. 
To this end, we explore the use hierarchical reinforcement learning (HRL) to train an agent that can navigate the complexities of ad hoc teaming at the same level of abstraction as humans.

{% include image.html url="research/haha/haha_example.png" max-width="50%" description="Two strategies in Overcooked." %}
To better understand the intricacies of zero-shot coordination, we analyze a scenario in the collaborative game "Overcooked", 
in which players cook and serve onion soups. The above figure depicts two possible strategies: in the individual strategy, 
the blue chef and green chef each pick up onions and place them in their respective pots. 
The coordinated strategy has the blue chef passing onions to the green chef using the counter. 
While the latter strategy is faster, it will fail if coordination is not achieved.
However, the former strategy can succeed even if only a single agent is productive. 
Ideally, when playing with a new teammate, an agent should be able to quickly identify which strategy to pursue based on their teammates play.
We note that this an illustrative example: Overcooked requires many strategic decisions that depend on each layout and that continue to evolve throughout play.
We also highlight that the strategies can only be reasonably described and understood at a task level---the low level description (e.g. *left, left, up, up, right, right, up, interact,...*) is not at a level of abstraction that a human could understand. 
Therefore, a key hypothesis that this work investigates is to understand if providing a hierarchical structure to an autonomous agent will enable it to align with their human teammates at the behavioral and cognitive level.

Importantly, a hierarchical approach provides the additional advantage of being able to tune an agent's behavior after training is complete. 
In previous approaches, if a strategy does not emerge in training, it will never be used by the agent. 
However, having a high level agent in the system enables one to impart a bias on certain sub-tasks to produce strategies unseen during training. 
For example, if all teammates in the training population only use the individual strategies, 
then no RL agent would learn to use the coordinated strategy as it would never produce a better reward. 
However, with a hierarchical agent one can manually bias the "place onion on the counter" sub-task after training to promote the use of the 
coordinated strategy. 

To our knowledge, we are the first paper to propose, motivate, and demonstrate the benefit of using HRL for agents that interact with humans. Specifically, we propose the following novel contributions:
1. We develop Hierarchical Ad Hoc Agents (HAHA) capable of zero-shot coordination with humans.
2. We demonstrate that HAHA outperforms all baselines when paired with unseen autonomous agents.
3. We demonstrate that HAHA outperforms and is preferred over baselines when paired with humans.
4. We investigate leveraging the hierarchical structure to promote specific cooperative strategies post training.
Our proposed hierarchical approach produces agents that can cooperate effectively with the rich diversity of human behavior, which can produce safe and efficient human-AI teams.

Code and full paper will be released soon.

# Future Work
We are continuing to look into how to explicitly parametrize new teammates, as well as how to tune agents based on human feedback.

*Please email Stéphane at stephane.aroca-ouellette@colorado.edu if anything on this page piques your interest (include [Q] in the subject line) or if you’re keen on collaborating (include [C] in the subject line).*
