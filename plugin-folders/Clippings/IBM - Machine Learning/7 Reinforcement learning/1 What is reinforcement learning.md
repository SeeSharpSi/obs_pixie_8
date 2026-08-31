---
title: What is reinforcement learning?
source: https://www.ibm.com/think/topics/reinforcement-learning
author:
- '[[Jacob  Murel Ph.D.]]'
- '[[Eda Kavlakoglu]]'
published: 2024-11-22
created: 2026-08-31
description: "In reinforcement learning, an agent learns to make decisions by interacting with an environment. It is used in robotics and other decision-making settings."
---

## What is reinforcement learning?

Reinforcement learning (RL) is a type of [machine learning](https://www.ibm.com/think/topics/machine-learning) process in which autonomous agents learn to make decisions by interacting with their environment.

An autonomous agent is any system that can make decisions and act in response to its environment independent of direct instruction by a human user. Robots and self-driving cars are examples of autonomous agents.

In reinforcement learning, autonomous agents learn to perform a task by trial and error in the absence of any guidance from a human user. <sup>1</sup> It particularly addresses sequential decision-making problems in uncertain environments, and shows promise in [artificial intelligence](https://www.ibm.com/think/topics/artificial-intelligence) development.

### Supervised and unsupervised learning

Literature often contrasts reinforcement learning with supervised and unsupervised learning. [Supervised learning](https://www.ibm.com/think/topics/supervised-learning) uses manually labeled data to produce predictions or classifications. [Unsupervised learning](https://www.ibm.com/think/topics/unsupervised-learning) aims to uncover and learn hidden patterns from unlabeled data. In contrast to supervised learning, reinforcement learning does not use labeled examples of correct or incorrect behavior. But reinforcement learning also differs from unsupervised learning in that reinforcement learning learns by trial-and-error and reward function rather than by extracting information of hidden patterns.<sup>2</sup>

Supervised and unsupervised learning methods assume each record of input data is independent of other records in the dataset but that each record actualizes a common underlying data distribution model. These methods learn to predict with model performance measured according to prediction accuracy maximization.

By contrast, reinforcement learning learns to act. It assumes input data to be interdependent tuples—i.e. an ordered sequence of data—organized as state-action-reward. Many applications of reinforcement learning algorithms aim to mimic real-world biological learning methods through positive reinforcement.

Note that, although the two are not often compared in literature, reinforcement learning is distinct from [self-supervised learning](https://www.ibm.com/think/topics/self-supervised-learning) as well. The latter is a form of unsupervised learning that uses pseudo labels derived from unlabeled training data as a ground truth to measure model accuracy. Reinforcement learning, however, does not produce pseudo labels or measure against a ground truth—it is not a classification method but an action learner. The two have been combined however with promising results.<sup>3</sup>

## Reinforcement learning process

Reinforcement learning essentially consists of the relationship between an agent, environment, and goal. Literature widely formulates this relationship in terms of the Markov decision process (MDP).

### Markov decision process

The reinforcement learning agent learns about a problem by interacting with its environment. The environment provides information on its current state. The agent then uses that information to determine which actions(s) to take. If that action obtains a reward signal from the surrounding environment, the agent is encouraged to take that action again when in a similar future state. This process repeats for every new state thereafter. Over time, the agent learns from rewards and punishments to take actions within the environment that meet a specified goal.<sup>4</sup>

![Diagram for reinforcement learning topic page](https://assets.ibm.com/is/image/ibm/reinforcement-learning-figure-1?ts=1772488691817&dpr=off)

In Markov decision processes, *state space* refers to all of the information provided by an environment’s state. *Action space* denotes all possible actions the agent may take within a state.<sup>5</sup>

### Exploration-exploitation trade-off

Because an RL agent has no manually labeled input data guiding its behavior, it must explore its environment, attempting new actions to discover those that receive rewards. From these reward signals, the agent learns to prefer actions for which it was rewarded in order to maximize its gain. But the agent must continue exploring new states and actions as well. In doing so, it can then use that experience to improve its decision-making.

RL algorithms thus require an agent to both exploit knowledge of previously rewarded state-actions and explore other state-actions. The agent cannot exclusively pursue exploration or exploitation. It must continuously try new actions while also preferring single (or chains of) actions that produce the largest cumulative reward.<sup>6</sup>

### Components of reinforcement learning

Beyond the agent-environment-goal triumvirate, four principal sub-elements characterize reinforcement learning problems.

**- Policy.** This defines the RL agent’s behavior by mapping perceived environmental states to specific actions the agent must take when in those states. It can take the form of a rudimentary function or more involved computational process. For instance, a policy guiding an autonomous vehicle may map pedestrian detection to a stop action.

**- Reward signal.** This designates the RL problem’s goal. Each of the RL agent’s actions either receives a reward from the environment or not. The agent’s only objective is to maximize its cumulative rewards from the environment. For self-driving vehicles, the reward signal can be reduced travel time, decreased collisions, remaining on the road and in the proper lane, avoiding extreme de- or accelerations, and so forth. This example shows RL may incorporate multiple reward signals to guide an agent.

**- Value function.** Reward signal differs from value function in that the former denotes immediate benefit while the latter specifies long-term benefit. Value refers to a state’s desirability per all of the states (with their incumbent rewards) that are likely to follow. An autonomous vehicle may be able to reduce travel time by exiting its lane, driving on the sidewalk, and accelerating quickly, but these latter three actions may reduce its overall value function. Thus, the vehicle as an RL agent may exchange marginally longer travel time to increase its reward in the latter three areas.

**- Model.** This is an optional sub-element of reinforcement learning systems. Models allow agents to predict environment behavior for possible actions. Agents then use model predictions to determine possible courses of action based on potential outcomes. This can be the model guiding the autonomous vehicle and that helps it predict best routes, what to expect from surrounding vehicles given their position and speed, and so forth.<sup>7</sup> Some model-based approaches use [direct human feedback](https://www.ibm.com/think/topics/rlhf) in initial learning and then shift to autonomous leanring.

## Online versus offline learning

There are two general methods by which an agent collects data for learning policies:

- **Online.** Here, an agent collects data directly from interacting with its surrounding environment. This data is processed and collected iteratively as the agent continues interacting with that environment.

- **Offline.** When an agent does not have direct access to an environment, it can learn through logged data of that environment. This is offline learning. A large subset of research has turned to offline learning given practical difficulties in training models through direct interaction with environments.<sup>8</sup>

![Diagram for reinforcement learning topic page](https://assets.ibm.com/is/image/ibm/reinforcement-learning-figure-2?ts=1772488692839&dpr=off)

## Types of reinforcement learning

Reinforcement learning is a vibrant, ongoing area of research, and as such, developers have produced a myriad approaches to reinforcement learning. Nevertheless, three widely discussed and foundational reinforcement learning methods are dynamic programming, monte carlo, and temporal difference learning.

### Dynamic programming

Dynamic programming breaks down larger tasks into smaller tasks. Thus, it models problems as workflows of sequential decision made at discrete time steps. Each decision is made in terms of the resulting possible next state. An agent’s reward (*r*) for a given action is defined as a function of that action (*a*), the current environmental state (*s*), and the potential next state (*s’*):

![Dynamic programming formula](https://assets.ibm.com/is/image/ibm/reinforcement-learning-reward-function-equation?ts=1772488693491&dpr=off)

This reward function can be used as (part of) the policy governing an agent’s actions. Determining the optimal policy for agent behavior is a chief component of dynamic programming methods for reinforcement learning. Enter the Bellman equation.

The Bellman equation is:

![Bellman equation formula](https://assets.ibm.com/is/image/ibm/reinforcement-learning-bellman-equation?ts=1772488693794&dpr=off)

In short, this equation defines *v<sub>t</sub>(s)* as the total expected reward starting at time *t* until the end of a decision workflow. It assumes that the agent begins by occupying state *s* at time *t*. The equation ultimately divides the reward at time *t* into the immediate reward *r<sub>t</sub>(s,a)* (i.e. the reward formula) and the agent’s total expected reward. An agent thus maximizes its value function—being the total value of the Bellman equation—by consistently choosing that action which receives a reward signal in each state.<sup>9</sup>

### Monte Carlo method

Dynamic programming is model-based, meaning it constructs a model of its environment to perceive rewards, identify patterns, and navigate the environment. [Monte Carlo](https://www.ibm.com/think/topics/monte-carlo-simulation), however, assumes a black-box environment, making it model-free.

While dynamic programming predicts potential future states and reward signals in making decisions, Monte Carlo methods are exclusively experience-based, meaning they sample sequences of states, actions, and rewards solely through interaction with the environment. Monte Carlo methods thus learn through trial and error rather than probabilistic distributions.

Monte Carlo further differs from dynamic programming in value function determination. Dynamic programming seeks the largest cumulative reward by consistently selecting rewarded actions in successive states. Monte Carlo, by contrast, averages the returns for each state–action pair. This, in turn, means that the Monte Carlo method must wait until all actions in a given episode (or planning horizon) have been completed before calculating its value function, and then updating its policy.<sup>10</sup>

### Temporal difference learning

Literature widely describes temporal difference (TD) learning as a combination of dynamic programming and Monte Carlo. As in the former, TD updates its policy, and so estimates for future states, after each step without waiting for a final value. As in Monte Carlo, however, TD learns through raw interaction with its environment rather than using a model thereof.<sup>11</sup>

Per its name, the TD learning agent revises its policy according to the difference between predicted and actual received rewards in each state. That is, while dynamic programming and Monte Carlo only consider the reward received, TD further weighs the difference between its expectation and received reward. Using this difference, the agent updates its estimates for the next step without waiting until the event planning horizon, contra Monte Carlo.<sup>12</sup>

TD has many variations. Two prominent variations are State–action–reward–state–action (SARSA) and Q-learning. SARSA is an on-policy TD method, meaning it evaluates and attempts to improve its decision-governing policy. Q-learning is off-policy. Off-policy methods are those that use two policies: one for exploitation (target policy) and one for exploration to generate behavior (behavior policy).<sup>13</sup>

### Additional methods

There is a myriad of additional reinforcement learning methods. Dynamic programming is a value-based method, meaning it selects actions based on their estimated values according to a policy that aims to maximize its value function. By contrast, policy gradient methods learn a parameterized policy that can select actions without consulting a value function. These are called policy-based and are considered more effective in high-dimensional environments.<sup>14</sup>

Actor-critic methods use both value-based and policy-based. The so-called “actor” is a policy gradient determining which actions to take, while the “critic” is a value function to evaluate actions. Actor-critic methods are, essentially, a form of TD. More specifically, actor-critic evaluates a given action’s value based not only on its own reward but the possible value of the following state, which it adds to the action’s reward. Actor-critic’s advantage is that, due to its implementation of a value function and policy in decision-making, it effectively requires less environment interaction.<sup>15</sup>

## Examples of reinforcement learning

Given reinforcement learning is centrally concerned with decision-making in unpredictable environments, it has been a core area of interest in robotics. For accomplishing simple and [repetitive tasks](https://www.ibm.com/think/topics/rpa), decision-making may be straightforward. But more complicated tasks, such as attempts to simulate human behavior or automate driving, involve interaction with high-variable and mutable real-world environments. Research shows [deep reinforcement learning](https://www.ibm.com/think/topics/deep-learning) with deep [neural networks](https://www.ibm.com/think/topics/neural-networks) aids such tasks, especially with respect to generalization and mapping high-dimensionally sensory input to controlled systems outputs.<sup>16</sup> Studies suggest that deep reinforcement learning with robots relies heavily on collected datasets, and so recent work explores avenues for collecting real-world data<sup>17</sup> and repurposing prior data<sup>18</sup> to improve reinforcement learning systems.

Recent research suggests leveraging [natural language processing](https://www.ibm.com/think/topics/natural-language-processing) techniques and tools—e.g. [large language models (LLMs)](https://www.ibm.com/think/topics/large-language-models)—may improve generalization in reinforcement learning systems through textual representation of real-world environments.<sup>19</sup> Many studies show how interactive textual environments provide cost-effective alternatives to three-dimensional environments when instructing learning agents in successive decision-making tasks.<sup>20</sup> Deep reinforcement learning also undergirds textual decision-making in [chatbots](https://www.ibm.com/think/topics/chatbots). In fact, reinforcement learning outperforms other methods for improving chatbot dialogue response.<sup>21</sup>

## Footnotes

<sup>1</sup> Ian Goodfellow, Yoshua Bengio, and Aaron Courville. *Deep Learning*. MIT Press. 2016.

<sup>2</sup> Peter Stone. “Reinforcement Learning”. *Encyclopedia of Machine Learning and Data Mining*. Springer. 2017.

<sup>3</sup> Xiang Li, Jinghuan Shang, Srijan Das, Michael Ryoo. “Does Self-supervised Learning Really Improve Reinforcement Learning from Pixels?” *Advances in Neural Information Processing Systems*. Vol. 35. 2022. pp. 30865–30881. [https://proceedings.neurips.cc/paper_files/paper/2022/hash/c75abb33341363ee874a71f81dc45a3a-Abstract-Conference.html](https://proceedings.neurips.cc/paper_files/paper/2022/hash/c75abb33341363ee874a71f81dc45a3a-Abstract-Conference.html).

<sup>4</sup> Richard Sutton and Andrew Barto. *Introduction to Reinforcement Learning*. 2nd edition. MIT Press. 2018. Michael Hu. *The Art of Reinforcement Learning: Fundamentals, Mathematics, and Implementations with Python*. Apress. 2023.

<sup>5</sup> Brandon Brown and Alexander Zai. *Deep Reinforcement Learning in Action*. Manning Publications. 2020.

<sup>6</sup> Richard Sutton and Andrew Barto. *Introduction to Reinforcement Learning*. 2nd edition. MIT Press. 2018. Brandon Brown and Alexander Zai. *Deep Reinforcement Learning in Action*. Manning Publications. 2020.

<sup>7</sup> Richard Sutton and Andrew Barto. *Introduction to Reinforcement Learning*. 2nd edition. MIT Press. 2018. B. Ravi Kiran, Ibrahim Sobh, Victor Talpaert, Patrick Mannion, Ahmad A. Al Sallab, Senthil Yogamani, and Patrick Pérez. “Deep Reinforcement Learning for Autonomous Driving: A Survey”. *IEEE Transactions on Intelligent Transportation Systems*. Vol. 23, No. 6. 2022. pp. 4909–4926. [https://ieeexplore.ieee.org/document/9351818](https://ieeexplore.ieee.org/document/9351818).

<sup>8</sup> Sergey Levine, Aviral Kumar, George Tucker, and Justin Fu. “Offline Reinforcement Learning: Tutorial, Review, and Perspectives on Open Problems”. 2020. [https://arxiv.org/abs/2005.01643](https://arxiv.org/abs/2005.01643). Julian Schrittwieser, Thomas Hubert, Amol Mandhane, Mohammadamin Barekatain, Ioannis Antonoglou, and David Silver. “Online and Offline Reinforcement Learning by Planning with a Learned Model”. *Advances in Neural Information Processing Systems*. Vol. 34. 2021. pp. 27580–27591. [https://proceedings.neurips.cc/paper_files/paper/2021/hash/e8258e5140317ff36c7f8225a3bf9590-Abstract.html](https://proceedings.neurips.cc/paper_files/paper/2021/hash/e8258e5140317ff36c7f8225a3bf9590-Abstract.html).

<sup>9</sup> Martin Puterman and Jonathan Patrick. “Dynamic Programming”. *Encyclopedia of Machine Learning and Data Mining*. Springer. 2017.

<sup>10</sup> Richard Sutton and Andrew Barto. *Introduction to Reinforcement Learning*. 2nd edition. MIT Press. 2018. Phil Winder. *Reinforcement Learning: Industrial Applications of Intelligent Agents*. O’Reilly. 2020.

<sup>11</sup> Richard Sutton and Andrew Barto. *Introduction to Reinforcement Learning*. 2nd edition. MIT Press. 2018.

<sup>12</sup> Michael Hu. *The Art of Reinforcement Learning: Fundamentals, Mathematics, and Implementations with Python*. Apress. 2023.

<sup>13</sup> Richard Sutton and Andrew Barto. *Introduction to Reinforcement Learning*. 2nd edition. MIT Press. 2018.

<sup>14</sup> Richard Sutton and Andrew Barto. *Introduction to Reinforcement Learning*. 2nd edition. MIT Press. 2018. Michael Hu. *The Art of Reinforcement Learning: Fundamentals, Mathematics, and Implementations with Python*. Apress. 2023.

<sup>15</sup> Richard Sutton and Andrew Barto. *Introduction to Reinforcement Learning*. 2nd edition. MIT Press. 2018.

<sup>16</sup> Julian Ibarz, Jie Tan, Chelsea Finn, Mrinal Kalakrishnan, Peter Pastor, and Sergey Levine. “How to Train Your Robot with Deep Reinforcement Learning: Lessons We Have Learned”. *The International Journal of Robotics Research*. Vol. 40. 2021. pp. 969–721. [https://journals.sagepub.com/doi/full/10.1177/0278364920987859](https://journals.sagepub.com/doi/full/10.1177/0278364920987859).

<sup>17</sup> Saminda Wishwajith Abeyruwan, Laura Graesser, David B. D’Ambrosio, Avi Singh, Anish Shankar, Alex Bewley, Deepali Jain, Krzysztof Marcin Choromanski, and Pannag R. Sanketi. “i-Sim2Real: Reinforcement Learning of Robotic Policies in Tight Human-Robot Interaction Loops”. *Proceedings of the 6th Conference on Robot Learning*. PMLR. No. 205. 2023. pp. 212–224. [https://proceedings.mlr.press/v205/abeyruwan23a.html](https://proceedings.mlr.press/v205/abeyruwan23a.html).

<sup>18</sup> Homer Rich Walke, Jonathan Heewon Yang, Albert Yu, Aviral Kumar, Jędrzej Orbik, Avi Singh, and Sergey Levine. “Don’t Start From Scratch: Leveraging Prior Data to Automate Robotic Reinforcement Learning”. *Proceedings of the 6th Conference on Robot Learning*. PMLR. No. 205. 2023. pp. 1652–1662. [https://proceedings.mlr.press/v205/walke23a.html](https://proceedings.mlr.press/v205/walke23a.html).

<sup>19</sup> Nikolaj Goodger, Peter Vamplew, Cameron Foale, and Richard Dazeley. “Language Representations for Generalization in Reinforcement Learning”. *Proceedings of the 13th Asian Conference on Machine Learning*. PMLR. No. 157. 2021. pp. 390–405. [https://proceedings.mlr.press/v157/goodger21a.html](https://proceedings.mlr.press/v157/goodger21a.html). Yuqing Du, Olivia Watkins, Zihan Wang, Cédric Colas, Trevor Darrell, Pieter Abbeel, Abhishek Gupta, and Jacob Andreas. “Guiding Pretraining in Reinforcement Learning with Large Language Models”. *Proceedings of the 40th International Conference on Machine Learning*. PMLR. No. 202. 2023. pp. 8657–8677. [https://proceedings.mlr.press/v202/du23f.html](https://proceedings.mlr.press/v202/du23f.html). Kolby Nottingham, Prithviraj Ammanabrolu, Alane Suhr, Yejin Choi, Hannaneh Hajishirzi, Sameer Singh, and Roy Fox. “Do Embodied Agents Dream of Pixelated Sheep: Embodied Decision Making Using Language-Guided World Modelling”. *Proceedings of the 40th International Conference on Machine Learning*. PMLR. 2023. pp. 26311–26325. [https://proceedings.mlr.press/v202/nottingham23a.html](https://proceedings.mlr.press/v202/nottingham23a.html).

<sup>20</sup> Ruoyao Wang, Peter Jansen, Marc-Alexandre Côté, and Prithviraj Ammanabrolu. “ScienceWorld: Is Your Agent Smarter Than a 5th Grader?” *Proceedings of the 2022 Conference on Empirical Methods in Natural Language Processing*. 2022. pp. 11279–11298. [https://aclanthology.org/2022.emnlp-main.775/](https://aclanthology.org/2022.emnlp-main.775/). Peter Jansen. “A Systematic Survey of Text Worlds as Embodied Natural Language Environments”. *Proceedings of the 3rd Wordplay Workshop: When Language Meets Games*. 2022. pp. 1–15. [https://aclanthology.org/2022.wordplay-1.1](https://aclanthology.org/2022.wordplay-1.1).

<sup>21</sup> Paloma Sodhi, Felix Wu, Ethan R. Elenberg, Kilian Q. Weinberger, and Ryan McDonald. “On the Effectiveness of Offline RL for Dialogue Response Generation”. *Proceedings of the 40th International Conference on Machine Learning*. PMLR. No. 202. 2023. pp. 32088–32104. [https://proceedings.mlr.press/v202/sodhi23a.html](https://proceedings.mlr.press/v202/sodhi23a.html). Siddharth Verma, Justin Fu, Sherry Yang, and Sergey Levine. “CHAI: A Chatbot AI for Task-Oriented Dialogue with Offline Reinforcement Learning”. *Proceedings of the 2022 Annual Conference of the North American Chapter of the Association for Computational Linguistics: Human Language Technologies*. 2022. pp. 4471–4491. [https://aclanthology.org/2022.naacl-main.332/](https://aclanthology.org/2022.naacl-main.332/).
