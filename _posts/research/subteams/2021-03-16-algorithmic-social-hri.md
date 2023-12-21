---
title: Algorithmic and Social HRI
description: Creating robot behaviors that promote safer, more reliable, and more effective interactions with humans
subtype: algorithmic and social hri
permalink: subteam/algorithmic-social-hri.html
image:
    feature: research/isat.jpg
    size: 80%
excerpt_separator: <!-- More -->
---

Substantial effort has been invested in expanding the role of robots into a multitude of new domains, from schools, to grocery stores, to warehouses.
But as robots are increasingly expected to work in close quarters or even interact with humans, the challenges in human-robot interaction have become more pronounced.
Behaviors that allow robots to engage with humans safely, efficiently, and smoothly are difficult to create, which is exacerbated by human perceptions of and responses to robots, which is itself still an open problem.

The goal of this subteam is to create robot behaviors that promote safer, more reliable, and more effective interactions with humans.
We use an interdisciplinary approach, leveraging work from cognitive learning theory, cumulative prospect theory, social psychology, and experimental economics to conduct foundational research in human-robot interaction and collaboration.

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

## 1.2 Interactive Task and Role Assignment for Human Robot Collaboration

**Postdoc:** [Jake Brawer](https://jakebrawer.com/)
**Students:** [Kaleb Bishop](https://kalebishop.github.io/)

Task assignment and scheduling (TAS) algorithms are powerful tools for coordinating large teams of robots, AIs, or humans with optimality and safety guarantees.
However, standard optiization-based techniques for TAS require deep technical knowledge to design, and are far too rigid to handle the complexities of many real-world, high-stakes tasks.
Large language models (LLMs) like ChatGPT, in contrast, are extraordinarily flexible and capbale of wide-ranging feats of generalized reasoning, though lack these desired gaurantees.
Our ongoing work seeks to narrow the gap between human ingenuity and algorithmic efficiency by enabling users to shape, update, and modify TAS systems entirely via LLm-mediated, interactive dialogue.
We hope this work  This approach not only enhances the efficiency and flexibility of task management, but also democratizes the use of advanced TAS algorithms.

## 1.3 Reference Dependent Risk Attitudes in HRI

**Students:** Clare Lohrmann

Prior research has shown that humans struggle to accurately judge the ability of robots.
This gap in expectations creates misplaced trust, which can result in disappointment and erosion of trust.
We hypothesize that this decrease in trust is caused by the human tendency towards loss aversion.
Loss aversion, a part of Prospect Theory, states that people prioritize avoiding losses (or the feeling of loss) over accumulating gains when making decisions.
Further work in experimental economics has indicated that “a prior expectation to take on risk decreases aversion to both the anticipated and additional risk”, meaning that when individuals are made aware that they are taking on risk, they experience less loss, and are less risk averse in the future. [Kȍszegi and Rabin, 2007].
In this project, we are testing the applicability of these experimental economics concepts in the context of human-robot interaction, in an effort to limit the expectations gap and promote more positive outcomes.
With knowledge of how applicable these concepts are to HRI, along with information about the effects of risk awareness on human behavior with robots, we hope to be able to create new models of robot behavior that guide humans to more accurate perceptions of robot ability, without eroding trust.

{% include image.html url="research/algo-social-hri/prospect-theory.png" max-width="50%" description="Humans have a tendency to underestimate the value of outcomes." %}

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

            {% include pubs-subteam.html subteam=page.subtype publications=site.data.publications %}

        </div>
    </div>
</section>
