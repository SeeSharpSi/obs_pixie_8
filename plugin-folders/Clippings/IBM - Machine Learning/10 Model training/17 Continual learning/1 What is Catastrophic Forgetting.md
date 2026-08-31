---
title: What is catastrophic forgetting?
source: https://www.ibm.com/think/topics/catastrophic-forgetting
author:
- '[[Ivan Belcic]]'
- '[[Cole Stryker]]'
published: 2025-03-28
created: 2026-08-31
description: "Catastrophic forgetting occurs when neural networks forget previously learned tasks after being trained on new data or undergoing fine-tuning for specific tasks."
---

## What is catastrophic forgetting?

Catastrophic forgetting occurs when [neural networks](https://www.ibm.com/think/topics/neural-networks) forget previously learned tasks after being trained on new data or undergoing [fine-tuning](https://www.ibm.com/think/topics/fine-tuning) for specific tasks. Also known as “catastrophic interference,” this phenomenon causes trained networks to lose information related to old tasks when being trained on new data in a sequential learning process.

Many [artificial intelligence implementations](https://www.ibm.com/think/insights/artificial-intelligence-implementation) require [machine learning](https://www.ibm.com/think/topics/machine-learning) models to adapt to new use cases over time. Catastrophic forgetting happens when the training process for the new tasks interferes with the model’s understanding of old tasks. As new knowledge replaces prior learning, the model loses the ability to handle its original tasks.

## Why does catastrophic forgetting happen?

First observed by Michael McCloskey and Neal J. Cohen in 1989<sup>[1](#footnotes1)</sup>, catastrophic forgetting happens as a result of the way [machine learning algorithms](https://www.ibm.com/think/topics/machine-learning-algorithms) adapt to new [datasets](https://www.ibm.com/think/topics/dataset). The training process for [deep learning](https://www.ibm.com/think/topics/deep-learning) models, such as [large language models](https://www.ibm.com/think/topics/large-language-models) (LLMs), involves exposing the model to data and allowing it to update its weights accordingly. A 2023 computer science paper<sup>[2](#footnotes2)</sup> found that it affects large models more severely than smaller ones.

Network weights, also known as a model’s parameters, are its internal ruleset that it uses to capture patterns and relationships in training datasets. During training, a machine learning algorithm updates its weights iteratively according to a [loss function](https://www.ibm.com/think/topics/loss-function): a mathematical equation that measures the error in the model’s predictions.

The goal of training is to minimize the loss function through methods such as [gradient descent](https://www.ibm.com/think/topics/gradient-descent). The learning rate sets the pace at which a model updates its weights during training.

The configuration of a model’s weights is its knowledge representation: a mathematical reflection of how the model understands its training data. If a model adjusts its weights substantially enough so that the new values are no longer relevant to previous tasks, it loses the ability to perform those tasks. In the process of learning new tasks, the model has “catastrophically” or completely forgotten how to approach old ones.

### Why do neural networks forget?

Neural networks are composed of interconnected nodes which mimic the neurons in the human brain. When learning, the brain creates synapses, or connections between the neurons in the neocortex, the region of the brain responsible for higher-level cognition. Meanwhile, the hippocampus is responsible for converting short-term memories into long-term ones and preserving knowledge.

While the field of neuroscience still has much to discover about the brain, we do know that the brain excels at internal optimization. Neuroplasticity, or brain plasticity, refers to the brain’s ability to restructure itself for continual learning. Synaptic connections used more often become stronger, while those used less frequently wither and eventually disappear.

Plasticity is what allows people to regain lost abilities, such as speech or motion, after suffering a traumatic brain injury. Without neural plasticity, humans would not be able to learn as they grow. The brains of babies and young children have greater plasticity, which is why they are able to learn languages so easily as compared to typical adults.

Artificial neural networks work similarly in that they adjust their weights in response to new data, much as the brain forges new synaptic connections. The hidden layers between the input and output of a neural network can shift over time. When neural networks overprioritize new data over previous knowledge, they can over-adjust their weights: rather than expand its knowledge, the model effectively replaces its previously knowledge with the new data.

## The effects of catastrophic forgetting

Catastrophic forgetting can have substantial effects on the performance of machine learning models, such as those used for generative AI apps. As models are applied to new use cases, they can experience [model drift](https://www.ibm.com/think/topics/model-drift) as their weights shift and eventually undergo catastrophic forgetting.

Catastrophic forgetting can adversely affect:

- **Model training and resource use:** Models that forget foundational knowledge must be retrained. The LLMs that power leading generative AI services cost millions of dollars to train, including compute resources as well as electricity and water to power the hyperscale data centers housing them.
- **Model deployment and AI app maintenance:** As a model’s performance degrades, the apps calling it will also suffer performance issues. In edge deployments where models must adapt to local circumstances, the risk of catastrophic forgetting can increase.
- **Autonomous learning:** Experiential learning systems can suffer catastrophic forgetting over time. The loss of foundational knowledge might make these systems less adaptable, reliable and consistent. With robotics and self-driving automobiles, these effects might be especially dangerous.

## Overcoming catastrophic forgetting

Researchers and other experts have proposed a range of techniques for countering catastrophic forgetting. A landmark paper published in 2017 by James Kirkpatrick, Andrei A. Rusi and others explored a method based on slowing the learning rate for weights relevant to older tasks. In 2025, another group of computer scientists explored the use of [backpropagation](https://www.ibm.com/think/topics/backpropagation) to overcome catastrophic forgetting (**FOOTNOTE**: [https://arxiv.org/abs/2501.01045#](https://arxiv.org/abs/2501.01045#)).

Other techniques for overcoming catastrophic forgetting include:

- Regularization
- Architectural solutions
- Ensemble methods
- Rehearsal techniques
- Memory-augmented neural networks (MANNs)

### Regularization

[Regularization](https://www.ibm.com/think/topics/regularization) is a set of techniques that make models more generalizable at the risk of increasing biases—they adapt more easily to new data. **Elastic weight consolidation (EWC)** is one such technique that adds a penalty to the loss function for adjustments to model weights that are important for old tasks.

**Synaptic intelligence** works similarly, disincentivizing the model from changing major parameters. Both techniques make the model less likely to lose previous knowledge.

### Architectural solutions

Model architecture describes the structure of a neural network, including the number of layers it has and the way the nodes are connected. Each layer is dedicated to a different function in the [AI workflow](https://www.ibm.com/think/topics/ai-workflow), such as [prediction](https://www.ibm.com/think/topics/predictive-ai) or [feature extraction](https://www.ibm.com/think/topics/feature-extraction).

**Progressive neural networks (PNNs)** add networks for new tasks while retaining the connections in networks used for earlier roles. The model combines the outputs of all networks, drawing on its older knowledge even when working on new tasks.

Other networks use **dynamic weight average (DWA)** during multi-task learning to dynamically adjust model weights during training. DWA allows models to flexibly adapt to different tasks.

### Ensemble methods

Ensemble methods combine the outputs of multiple models for more reliable results. **Lifelong learning forests** are [random forest](https://www.ibm.com/think/topics/random-forest) models that add new forests or decision trees for new tasks—similar to how PNNs add new networks as their workload expands.

Meanwhile, compartmentalized **modular architectures** can prevent new data from contaminating the rest of the network. Task-specific modules activate as required, preserving acquired knowledge when not in use.

### Rehearsal techniques

Rehearsal techniques expose the model to old data during training for new tasks, helping ensure that the model doesn’t catastrophically forget what it has previously learned. **Experience replay** is a [reinforcement learning](https://www.ibm.com/think/topics/reinforcement-learning) technique in which a model stores past experiences in a separate dataset, then randomly samples from this memory during training.

### Memory-augmented neural networks (MANNs)

Memory-augmented neural networks are a promising architecture combining neural networks with external memory storage. When processing input sequences such as user prompts, MANNs can read from and write to the memory. Many use attention mechanisms to isolate the most relevant memory components for each task.

**Gradient episodic memory (GEM)** is a MANN example that allows AI models to store and recall past experiences to inform new tasks and preserve previously acquired knowledge.

## Footnotes

1. ["Catastrophic Interference in Connectionist Networks: The Sequential Learning Problem,"](https://www.sciencedirect.com/science/article/abs/pii/S0079742108605368?via%3Dihub) McCloskey and Cohen, Psychology of Learning and Motivation, 1989

2. ["An Empirical Study of Catastrophic Forgetting in Large Language Models During Continual Fine-tuning"](https://arxiv.org/abs/2308.08747), Luo et al, 5 Jan 2025
