---
title: What is meta learning?
source: https://www.ibm.com/think/topics/meta-learning
author:
- '[[Rina Diane Caballar]]'
- '[[Cole Stryker]]'
published: 2024-07-08
created: 2026-08-31
description: "Meta learning, also called “learning to learn,” is a subcategory of machine learning that trains artificial intelligence (AI) models to understand and adapt to new tasks on their own."
---

## What is meta learning?

Meta learning, also called “learning to learn,” is a subcategory of [machine learning](https://www.ibm.com/topics/machine-learning) that trains [artificial intelligence (AI) models](https://www.ibm.com/topics/ai-model) to understand and adapt to new tasks on their own. Meta learning’s primary aim is to provide machines with the skill to learn how to learn.

Unlike conventional [supervised learning](https://www.ibm.com/topics/supervised-learning), where models are trained to solve a specific task using a defined [training dataset](https://www.ibm.com/think/topics/training-data), the meta learning process entails a variety of tasks, each with its own associated dataset. From these multiple learning events, models gain the ability to generalize across tasks, which allow them to adapt swiftly to novel scenarios even with little data.

Meta learning algorithms are trained on the predictions and metadata of other [machine learning algorithms](https://www.ibm.com/topics/machine-learning-algorithms). Meta learning algorithms then generate predictions of their own and information that can be used to enhance the performance and results of other machine learning algorithms.

## How meta learning works

Meta learning involves two key stages: meta training and meta testing. For both stages, a base learner model adjusts and updates its parameters as it learns. The dataset used is divided into a support set for meta training and a test set for meta testing.

### Meta training

In the meta training phase, the base learner model is supplied with a wide array of tasks. The model’s goal is to uncover common patterns among these tasks and acquire broad knowledge that can be applied in solving new tasks.

### Meta testing

During the meta testing phase, the base learner model’s performance is assessed by giving it tasks it hasn’t encountered when it was trained. The model’s effectiveness is measured by how well and how fast it adapts to these new tasks using its learned knowledge and generalized understanding.

![Diagram depicting base learner and meta learner making predictions](https://assets.ibm.com/is/image/ibm/ensemble-learning-stacking?ts=1763387059276&dpr=off)

## Common meta learning approaches

There are three typical approaches to meta learning. Here’s how each approach works and their different types:

### Metric-based meta learning

Metric-based meta learning is centered around learning a function that computes a distance metric, which is a measure of the similarity between two data points. This approach is akin to the [k-nearest neighbors (KNN) algorithm](https://www.ibm.com/topics/knn), which uses proximity to make classifications or predictions.

#### Convolutional Siamese neural network

A convolutional Siamese [neural network](https://www.ibm.com/topics/neural-networks) consists of identical twin [convolutional neural networks](https://www.ibm.com/topics/convolutional-neural-networks) that share parameters and weights. Parameter updates are mirrored across the two networks. Both networks are joined by a loss function that calculates a distance metric (usually pairwise similarity).<sup>1</sup>

The training dataset is composed of pairs of matching and nonmatching samples. Convolutional Siamese neural networks then learn to compute pairwise similarity, maximizing the Euclidean distance between nonmatching or dissimilar pairs and minimizing the distance between matching or similar pairs.<sup>1</sup>

#### Matching networks

Matching networks learn to predict classification by measuring a distance metric known as [cosine similarity](https://community.ibm.com/community/user/ai-datascience/blogs/moloy-de1/2020/06/18/points-to-ponder) between two samples.<sup>2</sup>

#### Relation network

A relation network learns a deep nonlinear distance metric for comparing items. The network classifies items by calculating relation scores, which represent the similarity between items.<sup>3</sup>

#### Prototypical networks

Prototypical networks compute the mean of all samples of a class to create a prototype for that class. The network then learns a metric space, where classification tasks are done by calculating the squared Euclidean distance between a particular data point and the prototype representation of a class.<sup>4</sup>

### Model-based meta learning

Model-based meta learning involves learning a model’s parameters, which can facilitate rapid learning from sparse data.

#### Memory-augmented neural networks

A memory-augmented neural network (MANN) is equipped with an external memory module to allow for stable storage and speedy encoding and retrieval of information.<sup>5</sup>

In meta learning, MANNs can be trained to learn a general technique for the kinds of representations to store in external memory and a method for using those representations to make predictions. MANNs have been shown to perform well in regression and classification tasks.<sup>5</sup>

#### Meta Networks

MetaNet (short for Meta Networks) is a meta learning model that can be applied in imitation learning and [reinforcement learning](https://www.ibm.com/topics/reinforcement-learning). Like MANNs, Meta Networks also have external memory.<sup>6</sup>

MetaNet is composed of a base learner and a meta learner working in separate space levels. The meta learner acquires general knowledge across different tasks within a meta space. The base learner takes an input task and sends meta information about the current task space to the meta learner. Based on this information, the meta learner conducts fast parameterization to update the weights within both spaces.<sup>6</sup>

### Optimization-based meta learning

[Deep learning](https://www.ibm.com/topics/deep-learning) typically requires multiple iterative updates of model parameters through backpropagation and the [gradient descent](https://www.ibm.com/topics/gradient-descent) optimization algorithm. In optimization-based meta learning, sometimes called gradient-based meta learning, the algorithm learns which initial model parameters or hyperparameters of deep neural networks can be efficiently fine-tuned for relevant tasks. This usually means meta-optimization—that is, optimizing the optimization algorithm itself.

#### LSTM meta-learner

This optimization-based meta learning method uses a popular [recurrent neural network](https://www.ibm.com/topics/recurrent-neural-networks) architecture called [long-short term memory (LSTM) networks](https://developer.ibm.com/tutorials/iot-deep-learning-anomaly-detection-1/) to train a meta-learner to acquire both long-term knowledge shared among tasks and short-term knowledge from each task. The meta-learner then optimizes another learner neural network classifier. It learns an initialization of the learner’s parameters for fast training convergence and how to update those parameters efficiently given a small training set, helping the learner adapt to new tasks quickly.<sup>7</sup>

#### Model-agnostic meta learning (MAML)

As its name implies, this optimization-based meta learning algorithm is model-agnostic. This makes it compatible with any model trained using gradient descent and suitable for solving various learning problems, such as classification, regression and reinforcement learning.<sup>8</sup>

The core idea behind MAML is to train the model’s initial parameters in a way that a few gradient updates will result in rapid learning on a new task. The goal is to determine model parameters that are sensitive to changes in a task such that minor changes to those parameters lead to major improvements in the task’s loss function. Meta-optimization across tasks is done using stochastic gradient descent (SGD).<sup>8</sup>

Unlike gradient descent, which computes derivatives to optimize a model’s parameters for a certain task, MAML computes second derivatives to optimize a model’s initial parameters for task-specific optimization. A modified version of model-agnostic meta learning, known as first-order MAML or FOMAML, omits second derivatives for a less computationally expensive process.<sup>8</sup>

#### Reptile

Reptile is a first-order gradient-based meta learning algorithm similar to FOMAML. It repeatedly samples a task, trains on that task through many gradient descent steps and moves the model weight toward the new parameters.<sup>9</sup>

## Meta learning use cases in machine learning

To further demonstrate meta learning’s versatility, here are a few ways meta learning can be used within the machine learning realm itself:

[Automated machine learning (AutoML)](https://www.ibm.com/topics/automl) allows for the automation of tasks in the machine learning pipeline. Meta learning techniques are well suited for AutoML, especially when it comes to hyperparameter optimization and model selection.

Fine-tuning hyperparameters for machine learning models is typically done manually. Meta learning algorithms can help automate this procedure by learning how to optimize hyperparameters or identifying the ideal hyperparameters for a certain task.

Meta learning algorithms can also learn how to choose the most appropriate model—and even that model’s parameters and architecture—to solve a specific task. This helps automate the model selection process.

[Few-shot learning](https://www.ibm.com/topics/few-shot-learning) is a machine learning framework that trains an AI model on a small number of examples. Most few-shot learning methods are built around meta learning, where models adapt to new tasks given scarce training data.

A [recommendation engine](https://www.ibm.com/think/topics/recommendation-engine) relies on machine learning algorithms to find patterns in user behavior data and recommend relevant items based on those patterns. Meta learning systems can learn recommendation models to generate more accurate and more relevant suggestions that better personalize user experiences.

Meta learning can help facilitate transfer learning, which adapts a pretrained model to learn new tasks or previously unseen classes of data.

## Applications of meta learning

Meta learning can be applied to different areas of the technology industry, some of which include:

Meta learning can be employed for [computer vision](https://www.ibm.com/topics/computer-vision) tasks, which include facial recognition, image classification, [image segmentation](https://www.ibm.com/topics/image-segmentation), object detection and object tracking.

Meta learning can be used for [natural language processing](https://www.ibm.com/topics/natural-language-processing) tasks, such as language modeling, [sentiment classification](https://www.ibm.com/topics/sentiment-analysis), speech recognition and text classification.<sup>10</sup>

Meta learning can help robots rapidly learn new tasks and adapt to dynamic environments. It can be applied in a number of tasks such as grasping, navigation, manipulation and movement.<sup>11</sup>

## Benefits of meta learning

Meta learning holds much potential. Here are a few of its advantages:

### Adaptability

Meta learning can be used to build more generalized AI models that can learn to do many related tasks. Due to this flexibility, meta learning systems can quickly adapt to new tasks and different domains.

### Efficient use of data

Meta learning supports learning from just a few samples, which might eliminate the need for huge dataset volumes. This can be particularly helpful for domains where gathering and preparing data might be labor intensive and time consuming.

### Decreased training time and training cost

Because of its data efficiency and swift learning, meta learning can result in a faster training process and reduced training costs.

## Challenges of meta learning

Despite the promise of meta learning, it also presents challenges. Here are some of them:

### Lack of data

Sometimes, the amount of data to train AI models is insufficient, especially for niche domains. Or, if data is available, the quality might not be adequate to efficiently train meta learning algorithms.

### Overfitting

Not having enough variability among tasks in the support set for meta training can lead to [overfitting](https://www.ibm.com/topics/overfitting). This means that a meta learning algorithm might only be applicable to specific tasks without being able to effectively generalize across a broad spectrum of tasks.

### Underfitting

Conversely, having too much variability among tasks in the support set for meta training can result in [underfitting](https://www.ibm.com/think/topics/underfitting). This means that a meta learning algorithm might not be able to use its knowledge in solving another task and might have difficulty adapting to new scenarios. Therefore, a balance in task variability is key.

## Footnotes

<sup>1 </sup>“[SigNet: Convolutional Siamese Network for Writer Independent Offline Signature Verification](https://arxiv.org/abs/1707.02131)”. arXiv. September 30, 2017.

<sup>2 </sup>“[Matching Networks for One Shot Learning](https://arxiv.org/abs/1606.04080)”. arXiv. December 29, 2017.

<sup>3 </sup>“[Learning to Compare: Relation Network for Few-Shot Learning](https://arxiv.org/abs/1711.06025)”. arXiv. March 27, 2018.

<sup>4 </sup>“[Prototypical Networks for Few-shot Learning](https://arxiv.org/abs/1703.05175)”. arXiv. June 19, 2017.

<sup>5 </sup>“[Meta-Learning with Memory-Augmented Neural Networks](https://proceedings.mlr.press/v48/santoro16.pdf)”. Proceedings of the 33rd International Conference on Machine Learning. June 19, 2016.

<sup>6 </sup>“[Meta Networks](https://arxiv.org/abs/1703.00837)”. arXiv. June 8, 2017.

<sup>7 </sup>“[Optimization as a Model for Few-Shot Learning](https://openreview.net/forum?id=rJY0-Kcll)”. OpenReview. July 22, 2022.

<sup>8 </sup>“[Model-Agnostic Meta-Learning for Fast Adaptation of Deep Networks](https://arxiv.org/abs/1703.03400)”. arXiv. July 18, 2017.

<sup>9 </sup>“[On First-Order Meta-Learning Algorithms](https://arxiv.org/abs/1803.02999)”. arXiv. October 22, 2018.

<sup>10 </sup>“[Meta Learning for Natural Language Processing: A Survey](https://arxiv.org/abs/2205.01500)”. arXiv. July 2, 2022.

<sup>11 </sup>“[Rapidly Adaptable Legged Robots via Evolutionary Meta-Learning](https://arxiv.org/abs/2003.01239)”. arXiv. July 30, 2020.
