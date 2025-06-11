---
title: Algorithmic HRI and Human-AI Teaming
description: Creating robot behaviors that promote safer, more reliable, and more effective interactions with humans
subtype: algorithmic hri and human-ai teaming
permalink: subteam/algorithmic-hri.html
image:
    feature: research/isat.jpg
    size: 80%
excerpt_separator: <!-- More -->
---

Substantial effort has been invested in expanding the role of robots into a multitude of new domains, from schools, to grocery stores, to warehouses.
But as robots are increasingly expected to work in close quarters or even interact with humans, the challenges in human-robot interaction have become more pronounced.
Behaviors that allow robots to engage with humans safely, efficiently, and smoothly are difficult to create, which is exacerbated by human perceptions of and responses to robots, which is itself still an open problem.

The goal of this subteam is to create robot behaviors that make robots more effective teammates and collaborators with humans. We use an interdisciplinary approach, leveraging machine learning, cognitive science, and social psychology to make robots more predictable, legible, and safe around humans. This subteam works with a variety of collaborators to conduct foundational research and run human-subjects studies to validate these approaches.

<!-- More -->

# Contents
{:.no_toc}

* This line will be replaced by the ToC, excluding the "Contents" header
{:toc}

# 1. Projects

## 1.1 Hierarchical Human-Agent Interaction

**Students:** [Stéphane Aroca-Ouellette](https://stephao.github.io/)

**_Publications:_**
- S. Aroca-Ouellette, M. Aroca-Ouellette, U. Biswas, K. Kann, and A. Roncone, _"Hierarchical Reinforcement Learning for Ad Hoc Teaming"_ in _Proceedings of the 2023 International Conference on Autonomous Agents and Multiagent Systems (AAMAS)_, 2023. [[PDF]]({{ site.url }}/papers/2023_Aroca-Ouellette_AAMAS_HAHA.pdf) [[BIB]]({{ site.url }}/papers/2023_Aroca-Ouellette_AAMAS_HAHA.bib)

In collaborative tasks, humans excel at adapting to their partners and converging toward an aligned strategy to maximize team success.
This is an inherently human skill that current state-of-the-art machine learning models largely lack.
We contend that this gap stems from the traditional focus on learning human-agent interaction from low-level primitive actions, whereas human collaboration centers around high-level strategies.
To address this, we introduce HAHA: Hierarchical Ad Hoc Agents, a novel framework using hierarchical reinforcement learning to train an agent capable of navigating the intricacies of ad hoc teaming at a level of abstraction more akin to human collaboration.
HAHA consists of a Worker and a Manager, which respectively focus on optimizing efficient sub-task completion and high-level team strategies.
We evaluate HAHA in the Overcooked environment, demonstrating that it outperforms existing baselines in both quantitative and qualitative metrics, offering improved teamwork, better resilience to environmental shifts, and heightened agent intelligibility. 
Furthermore, we show that the generalization ability of HAHA extends to changes in the environment and that our structure allows for the induction of new strategies not encountered during training.
We posit that the advancements proposed in this paper form a crucial building block toward the realization of safer and more efficient human–AI teams.

{% include image.html url="research/haha/haha_architecture.png" max-width="40%" description="Architecture of the Hierarchical Ad Hoc Agents (HAHA). Similar to a human, the manager first selects which high-level task to accomplish next. The low-level worker then takes over to carry out the task." %}

## 1.2 Predictability in HRI

**Students:** [Clare Lohrmann](https://cmlohrmann.github.io/)
**_Publications_**
- C. Lohrmann, E. Berg, B. Hayes, and A. Roncone, _"Improving Robot Predictability via Trajectory Optimization Using a Virtual Reality Testbed,"_ in _7th International Workshop on Virtual, Augmented, and Mixed-Reality for Human-Robot Interactions (VAM-HRI)_, 2024. [[PDF]]({{ site.url }}/papers/2024_Lohrmann_VAMHRI_predictability.pdf) [[BIB]]({{ site.url }}/papers/2024_Lohrmann_VAMHRI_predictability.bib)
- C. Lohrmann, M. Stull, A. Roncone, and B. Hayes _"Generating Pattern-Based Conventions for Predictable Planning in Human-Robot Collaboration,"_ in _ACM Transactions on Human-Robot Interaction_, 2024. [[PDF]]({{ site.url }}/papers/2024_Lohrmann_THRI_patterns.pdf) [[BIB]]({{ site.url }}/papers/2024_Lohrmann_THRI_patterns.bib)

For humans to effectively work with robots, they must be able to predict the actions and behaviors of their robot teammates rather than merely react to them. While there are existing techniques enabling robots to adapt to human behavior, there is a demonstrated need for methods that explicitly improve humans' ability to understand and predict robot behavior. 

Our methods leverage the innate human propensity for pattern recognition and abstraction in order to improve team dynamics in human-robot teams and to make robots more predictable to the humans that work with them. Patterns are a cognitive tool that humans use and rely on often, and the human brain is in many ways primed for pattern recognition and usage. In this research stream we lean into human cognitive tendencies to improve human-robot teaming and human perceptions of their robot teammates.

{% include image.html url="research/algo-social-hri/maria_setup_img_blur.png" max-width="50%" description="The setup for experiments conducted for our THRI journal article, where participants played a coordination game with a Sawyer robot." %}

In our most recent work, we introduce PACT, a method for setting conventions for a human-robot team using patterns that humans can recognize. Our method emphasizes using human-visible features of the game setting, such as color, shape, and location to form these patterns. PACT selects a pattern-based convention that is both a deterministic and unique as possible. In this way, if the human knows the pattern, they will know what comes next (determinism), and the robot's behavior cannot be explained by another pattern (unique). Our experiment shows that by emphasizing predictability via pattern-based conventions, we can not only improve human-robot performance on a coordination task, but PACT also increases positive perceptions of the robot and its contributions to the team. 

## 1.3 Interactive Task and Role Assignment for Human Robot Collaboration

**Postdoc:** [Jake Brawer](https://jakebrawer.com/)
**Students:** [Kaleb Bishop](https://kalebishop.github.io/)

**_Publications_***
- J. Brawer, K. Bishop, B. Hayes, and A. Roncone, _"Towards A Natural Language Interface for Flexible Multi-Agent Task Assignment,"_ in _2023 AAAI Fall Symposium on Artificial Intelligence for Human-Robot Interaction (AI-HRI)_, 2023. [[PDF]]({{ site.url }}/papers/2023_Brawer_AI-HRI_task_assignment.pdf) [[BIB]]({{ site.url }}/papers/2023_Brawer_AI-HRI_task_assignment.bib)

Task assignment and scheduling (TAS) algorithms are powerful tools for coordinating large teams of robots, AIs, or humans with optimality and safety guarantees.
However, standard optiization-based techniques for TAS require deep technical knowledge to design, and are far too rigid to handle the complexities of many real-world, high-stakes tasks.
Large language models (LLMs) like ChatGPT, in contrast, are extraordinarily flexible and capbale of wide-ranging feats of generalized reasoning, though lack these desired gaurantees.
Our ongoing work seeks to narrow the gap between human ingenuity and algorithmic efficiency by enabling users to shape, update, and modify TAS systems entirely via LLM-mediated, interactive dialogue.
We are confident that this approach will not only enhance the efficiency and flexibility of task management, but also democratizes the use of advanced TAS algorithms.

## 1.4 Student-Robot Teaming and Robots in the Classroom

**Students:** [Kaleb Bishop](https://kalebishop.github.io/)

Recent work in cognitive learning theory and social psychology present new opportunities to improve and rethink the application of robots in the classroom.
Why are robots such powerful agents of tutoring, and how can we use their unique social roles to develop student skills in reading, STEM, and beyond, and address educational inequality across lines of race, gender, and ability?
Current projects, conducted in conjunction with the [NSF AI Institute for Student-AI Teaming (iSAT)](https://www.colorado.edu/research/ai-institute/) and the [Engineering Education and AI-Augmented Learning IRT](https://www.colorado.edu/irt/engineering-education-ai/), include study into HRI design considerations for students of color and developing a robot tutoring system to address grounded reading skills.

{% include image.html url="research/isat.jpg" description="iSAT's vision for student-AI teaming and classroom orchestration." %}

## 1.5 Robotic Intent Signaling System

**Students:** Mitchell Scott, Shreyas Kadekodi, [Caleb Escobedo]({% post_url people/2019-10-10-caleb %}), Clare Lohrmann

The creation of information channels between robots and humans is complicated and fraught with potential pitfalls; the goal being a simplistic system that effectively carries information from one party to another consistently and clearly.
While much work has gone into creating robot signals and modes of communication, most research seeks to answer the question “Does this system communicate what it was intended to?”, be it the robot's path, intent, or status.
Research is conducted in a controlled environment, so the applicability of these systems to environments constrained by space or time is unknown.
We are currently examining the effectiveness of a projection-based trajectory system in a cluttered and fast paced environment.
Through this work we hope to determine when this method of communication is most effective, and if/when the environment becomes too crowded or too fast moving for the communication to be effective.

# 2. Publications

<section id="post-cv" style="padding-top: 0;">
    <div class="container">
        <div id="article">

            {% include pubs.html subteam=page.subtype publications=site.data.publications %}

        </div>
    </div>
</section>
