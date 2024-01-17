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

## 1.1 Technical Fluency in Human-Agent Interaction

**Students:** [Stéphane Aroca-Ouellette](https://stephao.github.io/)

**_Publications:_**
- S. Aroca-Ouellette, M. Aroca-Ouellette, U. Biswas, K. Kann, and A. Roncone, _"Hierarchical Reinforcement Learning for Ad Hoc Teaming"_ in _Proceedings of the 2023 International Conference on Autonomous Agents and Multiagent Systems (AAMAS)_, 2023. [[PDF]]({{ site.url }}/papers/2023_Aroca-Ouellette_AAMAS_HAHA.pdf) [[BIB]]({{ site.url }}/papers/2023_Aroca-Ouellette_AAMAS_HAHA.bib)


Drastic variance in human knowledge, ability, and preference result in rich diversity of human behavior. For successful integration of autonomous agents
in human endeavours, these agents must be able to efficiently adapt to a wide range previously unseen collaborators.
For example, when working with a less experienced teammate, an agent should likely prioritize understandable behavior over complicated behaviors in order to build trust and
allow the teammate to adjust to the task. In contrast, when working with a more experience teammate, the agent can instead focus on more optimal behaviors. 
To accomplish this, an agent must be able to not have a range of behaviors, but also identify the necessary
traits of their partner.  In this stream of research, we explore how to imbue autonomous agents with these abilities.

<div class="row">
    {% include post-sorter.html subtype="haha" %}
</div>


## 1.2 Predictability for Human-Robot Teaming

**Students:** [Clare Lohrmann](https://cmlohrmann.github.io/)
In this research stream we lean into human cognitive tendencies to improve human-robot teaming and human perceptions of their robot teammates. Robots and humans reason in different, and often contradicting ways, making human-robot interactions challenging, unpredictable, and even dangerous. For humans to effectively work with robots, they must be able to predict the actions and behaviors of their robot teammates rather than merely react to them. While there are existing techniques enabling robots to adapt to human behavior, there is a demonstrated need for methods that explicitly improve humans' ability to understand and predict robot behavior.

In our work, we create robot behavior that is more in line with human expectations (predictable) by incorporating aspects of the human cognitive toolkit that humans often rely on, such as patterns, symmetry, etc. Thus, we make collaboration smoother and more intuitive for those who work with or around robots - without sacrificing team performance or speed.

{% include image.html url="research/algo-social-hri/maria_setup_img_blur.png" max-width="50%" description="The setup for a work currently under review, where participants played a coordination game with a Sawyer robot." %}
{% include image.html url="research/algo-social-hri/spot_in_enviro.png" max-width="50%" description="Here's a snapshot from our work in development - leveraging VR via Meta's Quest 3 to conduct robot predictability work." %}

## 1.3 Student-Robot Teaming and Robots in the Classroom

**Students:** [Kaleb Bishop](https://kalebishop.github.io/)

Recent work in cognitive learning theory and social psychology present new opportunities to improve and rethink the application of robots in the classroom.
Why are robots such powerful agents of tutoring, and how can we use their unique social roles to develop student skills in reading, STEM, and beyond, and address educational inequality across lines of race, gender, and ability?
Current projects, conducted in conjunction with the [NSF AI Institute for Student-AI Teaming (iSAT)](https://www.colorado.edu/research/ai-institute/) and the [Engineering Education and AI-Augmented Learning IRT](https://www.colorado.edu/irt/engineering-education-ai/), include study into HRI design considerations for students of color and developing a robot tutoring system to address grounded reading skills.

{% include image.html url="research/isat.jpg" description="iSAT's vision for student-AI teaming and classroom orchestration." %}

## 1.4 Task and Role Assignment for Human Robot Collaboration

To incorporate robots into human teams, robots need explainable task representations and better understanding of the social dynamics of the human team to be an effective member.
Our goal is to equip the robot with the ability to insert itself into an existing human team to promote collaboration and improve efficiency.
How can the robot decompose complex tasks and find the optimal role assignments for the team?
How does the robot balance the preferences of the human and the optimality of the task assignment?
How does the robot know what roles to take?

**Students:** Yi-Shiuan Tung

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
