---
title: Learning, Modeling, and Robotics
author:
permalink: subteam/learning-modeling-robotics.html
category: [subteams]
excerpt_separator: <!-- More -->
---

Our goal is to catalyze tangible and substantial improvements in robot capabilities, especially in human–robot scenarios, with research at the confluence of learning, modeling, and robotics.
We accomplish this from two reciprocal perspectives. 

In the first, we leverage contemporary advances in learning and modeling to develop more sophisticated, accessible, and generalizable robot technologies.
Our research attention here is primarily directed toward robots that exist in human environments; the capacity of robots to interact or even cooperate with humans are considerations that are often neglected in the learning and modeling communities.

Complementarily, we draw upon our expertise in robotics and human–robot interaction to inform foundational research in artificial intelligence—particularly in natural language processing and reinforcement learning.
Our experience with real-world robotic systems allows us to underpin our research with strong empirical motivations, an approach that is conspicuously scant in much of the existing literature.

<!-- More -->

### Non-Prehensile Manipulation

Non-prehensile manipulation (i.e., manipulation that does not involve grasping) can significantly expand the operational space of a robot.
We posit that robots need to leverage non-prehensile manipulation as part of their skill set if they are to achieve human-level dexterity.
Our past work introduced a novel planner that uses poking as a skill _and_ failure recovery tactic synergistically with grasping.
Moving forward, we are building hybrid models for manipulation in which physics-based and learning-based approaches complement each other, toward generating a repository of skills that robots can then use to engage in more complex, affordance-informed task planning and manipulation.

**Students:** [Anuj Pasricha]({{ site.url }}/anuj), Yi-Shiuan Tung

**_Publications_**
 - A. Pasricha, Y. Tung, B. Hayes, and A. Roncone, "PokeRRT: Poking as a skill and failure recovery tactic for planar non-prehensile manipulation," 2021. In review.


### Natural Language Grounding Skill Transfer

Natural language is the easiest and most generalizable way for humans to specify a task, provide new information, and convey intentions.
Achieving this communication with robots requires grounding language to the world that they exist in.
More concretely, this requires enabling robots to map words and phrases to objects, actions, and concepts.
To this end, we are investigating how to condition robotic motion on natural language with the aim of developing a more flexible and generalizable task specification framework.
Further, we are interested in how real-world experience changes a model’s interpretation of language.

**Students:** Stéphane Aroca-Ouellette


### Multi-Agent Reinforcement Learning

Reinforcement learning (RL), which allows an agent to learn from interactions with its environment, presents an increasingly promising alternative to traditional model-based control.
However, much of the work applying RL to robotics has been in the single-agent paradigm—despite the pervasiveness of multi-agent robotic systems in the real world.
We are most interested in developing algorithms for controlling heterogeneous teams that cooperate to accomplish common goals, with the aim of enabling multi-robot systems to be imbued with capabilities that are more than the sum of their parts.
Moreover, we envision multi-agent systems serving as the setting for the next wave of progress in RL research, and are further driven by the belief that multi-agent RL can provide a theoretical basis for understanding the application of RL in human–robot contexts.

**Students:** Guohui Ding, [Joewie J. Koh]({{ site.url }}/joewie)

**_Publications_**
 - J. J. Koh*, G. Ding*, C. Heckman, L. Chen, A. Roncone, "Cooperative control of mobile robots with Stackelberg learning," in _2020 IEEE/RSJ International Conference on Intelligent Robots and Systems (IROS)_, 2020. [[PDF]]({{ site.url }}/papers/2020_Koh_IROS_SLiCC.pdf) [[BIB]]({{ site.url }}/papers/2020_Koh_IROS_SLiCC.bib)
 - G. Ding*, J. J. Koh*, K. Merckaert, B. Vanderborght, M. M. Nicotra, C. Heckman, A. Roncone, L. Chen, "Distributed reinforcement learning for cooperative multi-robot object manipulation," in _19th International Conference on Autonomous Agents and Multiagent Systems (AAMAS)_, 2020. [[PDF]]({{ site.url }}/papers/2020_Ding_AAMAS_cooperative_object_manipulation.pdf) [[BIB]]({{ site.url }}/papers/2020_Ding_AAMAS_cooperative_object_manipulation.bib)


### Learning Discourse Policies for Dialog Management

The [NSF National AI Institute for Student-AI Teaming (iSAT)](https://www.colorado.edu/research/ai-institute/) is a multi-site interdisciplinary institute with the vision of developing artificial intelligence as a social, collaborative partner that helps both students and teachers make learning more effective, engaging, and equitable.
As a part of this institute, we conduct foundational research on dialog management for AI-based conversation participation and facilitation.
Specifically, we are studying how reinforcement learning might be applied to autonomously generate and fine-tune discourse policies.

**Students:** [Joewie J. Koh]({{ site.url }}/joewie), [Kaleb Bishop](https://kalebishop.github.io/)
