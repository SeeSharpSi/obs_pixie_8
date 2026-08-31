---
title: What is model training?
source: https://www.ibm.com/think/topics/model-training
author:
- '[[Dave Bergmann]]'
- '[[Cole Stryker]]'
published: 2025-02-13
created: 2026-08-31
description: "Model training is the process of “teaching” a machine learning model to optimize performance on a dataset of sample tasks resembling its real-world use cases."
---

## What is model training?

Model training is the process of “teaching” a [machine learning](https://www.ibm.com/think/topics/machine-learning) model to optimize performance on a training dataset of sample tasks relevant to the model’s eventual use cases. If training data closely resembles real-world problems that the model will be tasked with, learning its patterns and correlations will enable a trained model to make accurate predictions on *new* data.

The training process is the most critical step in the lifecycle of [AI models](https://www.ibm.com/think/topics/ai-model), from [forecasting](https://www.ibm.com/think/topics/forecasting) systems built on basic [linear regression](https://www.ibm.com/think/topics/linear-regression) algorithms to the complex [neural networks](https://www.ibm.com/think/topics/neural-networks) that power [generative AI](https://www.ibm.com/think/topics/generative-ai).

Model training is the machine learning (ML) step where the “learning” occurs. In machine learning, learning involves adjusting the parameters of an ML model. These parameters include the [weights and biases](https://www.ibm.com/think/topics/backpropagation#How+neural+networks+work) in the mathematical functions that make up their algorithms. The goal of this adjustment is to produce more accurate outputs. The specific values for these weights and biases, which are the end result of model training, are the tangible manifestation of a model’s “knowledge.”

Mathematically, the goal of this learning is to minimize a [loss function](https://www.ibm.com/think/topics/loss-function) that quantifies the error of model outputs on training asks. When the output of the loss function falls beneath some predetermined threshold—meaning the model’s error on training tasks is sufficiently small—the model is deemed “trained.” In reinforcement learning, the goal is reversed: instead of minimizing a loss function, the model’s parameters are optimized to maximize a reward function.

In practice, model training entails a cycle of collecting and curating data, running the model on that training data, measuring loss, optimizing parameters accordingly and testing model performance on validation datasets. This workflow proceeds iteratively until satisfactory results have been achieved. Adequate training might also require the adjustment of hyperparameters—structural choices that influence the learning process but are not themselves “learnable”—in a process called [hyperparameter tuning](https://www.ibm.com/think/topics/hyperparameter-tuning).

Sometimes, an already-trained model can be [fine-tuned](https://www.ibm.com/think/topics/fine-tuning) for more specific tasks or domains through further learning on new training data. Though both the original from-scratch training and the subsequent fine-tuning are “training,” the former is typically called “pretraining” in this context (for the sake of disambiguation). Fine-tuning is one of several types of [transfer learning](https://www.ibm.com/think/topics/transfer-learning), an umbrella term for machine learning techniques that adapt pretrained models for new uses.

## Models vs. algorithms

Though the words “model” and “algorithm” are often used interchangeably in the field of artificial intelligence, they are not the same thing. The distinction lies primarily in the relationship of each term to model training.

- **Algorithms** are procedures, usually described in mathematical language or pseudocode, used to output predictions or make decisions based on the input they are provided.
- **Models** are the outcome of the process of optimizing an algorithm’s parameters to improve its performance on a specific training dataset—and then on new data that resembles those training examples. In data science terms, this process is called “fitting” an algorithm to a dataset.

In other words, an AI model is used to make predictions or decisions, and an algorithm is the mathematical logic by which that model operates. Two models might use the same underlying algorithm but have different values for the weights and biases within that algorithm because they were trained on different data.

[Deep learning](https://www.ibm.com/think/topics/deep-learning) is a subset of machine learning whose models are neural networks with many layers—hence “deep”—rather than explicitly designed algorithms such as [logistic regression](https://www.ibm.com/think/topics/logistic-regression) or [Naïve Bayes](https://www.ibm.com/think/topics/naive-bayes). Two deep learning models might have the same structure, such as a standard [autoencoder](https://www.ibm.com/think/topics/autoencoder), but differ in the number of layers, number of neurons per layer or activation functions of each neuron.

## Types of model training

In most contexts, training is nearly synonymous with learning: a data scientist trains; a model learns. Learning entails adjusting the parameters of a machine learning algorithm until the resulting model’s outputs meet some metric of accuracy or usefulness. Training entails collecting training data and tuning hyperparameters—such as choosing a loss function, setting [the update rate of parameters](https://www.ibm.com/think/topics/learning-rate) or altering a neural network’s architecture—to facilitate that learning.

AI models are typically categorized as belonging to one of three distinct machine learning paradigms: [supervised learning](https://www.ibm.com/think/topics/supervised-learning), [unsupervised learning](https://www.ibm.com/think/topics/unsupervised-learning) or [reinforcement learning](https://www.ibm.com/think/topics/reinforcement-learning). Each type of machine learning has its own unique use cases, hyperparameters, algorithms and training processes.

- **Supervised learning** is used when a model is trained to predict the “correct” output for an input. It applies to tasks that require some degree of accuracy relative to some external [“ground truth,”](https://www.ibm.com/think/topics/ground-truth) such as classification or regression.

- **Unsupervised learning** is used when a model is trained to discern intrinsic patterns and correlations in data. Unlike supervised learning, unsupervised learning doesn’t assume the existence of any external ground truth against which its outputs should be compared.

- **Reinforcement learning** is used when a model is trained to evaluate its environment and take the action that will garner the greatest reward.

It’s worth noting that the definitions of and distinctions between each machine learning paradigm are not always formal or absolute. For instance, [self-supervised learning](https://www.ibm.com/think/topics/self-supervised-learning) (SSL) can feasibly be classified as both supervised or unsupervised learning, depending on which aspect of those terms’ definitions one focuses on. [Semisupervised learning](https://www.ibm.com/think/topics/semi-supervised-learning) combines unsupervised and supervised learning.

It’s also worth noting that multiple types of machine learning can sometimes be used to train a single AI system. For example, the versions of [large language models (LLMs](https://www.ibm.com/think/topics/large-language-models)) used for conversational applications such as [chatbots](https://www.ibm.com/think/topics/chatbots) typically undergo self-supervised pretraining, followed by supervised fine-tuning and, subsequently, [reinforcement learning from human feedback (RLHF](https://www.ibm.com/think/topics/rlhf)).

### Supervised learning

As the dominant form of training for the neural networks that comprise deep learning models, supervised learning underpins most state-of-the-art AI models today. Supervised learning is the primary training paradigm for tasks that require accuracy, such as [classification](https://www.ibm.com/think/topics/classification-machine-learning) or regression.

Training a model for accuracy requires comparing its output predictions for a specific input to the “correct” predictions for that input—usually called the ground truth. In conventional supervised learning, that ground truth is provided by labeled data pairs. For instance, training data for [object detection](https://www.ibm.com/think/topics/object-detection) models pairs raw images (the input) with annotated versions of the images indicating the location and classification of each object within them (the output).

Because this training method requires a human in the loop to provide that ground truth, it’s called “supervised” learning. But the definitive characteristic of supervised learning is not the involvement humans, but rather the use of some ground truth and minimization of a loss function that measures divergence from it. This distinction became important as innovative new learning techniques devised ways to implicitly infer “pseudolabels” from unlabeled data.

To accommodate a more versatile notion of supervised learning, modern ML terminology uses “supervision” or “supervisory signals” to refer to any source of ground truth. In [self-supervised learning](https://www.ibm.com/think/topics/self-supervised-learning), which is nominally “unsupervised” in that it uses unlabeled data, supervisory signals are derived from the structure of the unlabeled data itself. For example, LLMs are pretrained through SSL by predicting masked words in text samples, with the original text serving as ground truth.

### Unsupervised learning

Unlike in supervised learning, unsupervised learning doesn’t assume the preexistence of “correct” answers, and therefore doesn’t involve supervisory signals or conventional loss functions. Unsupervised learning algorithms seek to discover intrinsic patterns in unlabeled data, such as similarities, correlations or potential groupings, and are most useful where such patterns aren’t necessarily apparent to human observers.

Prominent categories of unsupervised learning algorithms include:

- **Clustering** algorithms partition unlabeled data points into “clusters,” or groupings, based on their proximity or similarity to one another. For instance, k-means clustering, a popular clustering algorithm, is used in market segmentation to group together customers with similar attributes into $k$ groups.
- **Association** algorithms discern correlations, such as between a particular action and certain conditions. For instance, e-commerce businesses such as Amazon use unsupervised [association](https://dataplatform.cloud.ibm.com/docs/content/wsd/nodes/associationrules.html?context=cpdaas) models to power recommendation engines.
- [**Dimensionality reduction**](https://www.ibm.com/think/topics/dimensionality-reduction) algorithms are designed to reduce the complexity of data by representing them with a smaller number of features—that is, representing them in fewer dimensions—while preserving their meaningful characteristics. They have several use cases, including data compression, data visualization and [feature engineering](https://www.ibm.com/think/topics/feature-engineering).

As their name suggests, unsupervised learning algorithms can be broadly understood as somewhat “optimizing themselves.” For example, [this animation](https://shabal.in/visuals/kmeans/6.html) from University of Utah professor Andrey Shabalin, Ph.D., demonstrates how a k-means clustering algorithm iteratively optimizes the centroid of each cluster.

As such, training AI models that use unsupervised learning algorithms is usually a matter of hyperparameter tuning. For example, in a clustering algorithm, the ideal number of clusters ($k$) is not always obvious and might require manual experimentation to yield optimal results.

### Reinforcement learning

Whereas supervised learning trains models by optimizing them to match ideal exemplars and unsupervised learning algorithms fit themselves to a dataset, reinforcement learning models are trained holistically through trial and error. Reinforcement problems don’t involve a singular “right” answer; instead, they involve “good” decisions and “bad” (or perhaps neutral) decisions.

Rather than the independent pairs of input-output data used in supervised learning, reinforcement learning (RL) operates on interdependent state-action-reward data tuples. A mathematical framework for reinforcement learning is built primarily on the these components:

- The **state space** contains all available information relevant to decisions that the model might make. It typically changes with each action that the model takes.
- The **action space** contains all the decisions that the model is permitted to make at a moment. In a board game, the action space comprises all legal moves available at that time. In text generation, the action space comprises the entire “vocabulary” of tokens available to an LLM.
- The **reward function** determines the positive (or negative) feedback to provide to the model as a result of each action into a reward signal: a scalar quantification of that feedback. For instance, when training a chess program with RL, a reward function might incentivize moves that increase the probability of winning and disincentivize moves that decrease the likelihood of victory. When training a self-driving car, a reward function might disincentivize maneuvers that break laws or decrease the probability of safety.
- A **policy** is the “thought process” that drives an RL agent’s behavior. Mathematically speaking, a policy ($π$) is a function that takes a state ($s$) as input and returns an action ($a$): $π(s)→a$.

The goal of an RL algorithm is to optimize a policy to yield maximum reward. In deep reinforcement learning, the policy is represented as a [neural network](https://www.ibm.com/think/topics/neural-networks) whose parameters are continuously updated to maximize the reward function (rather than minimize a loss function).

## How to train a machine learning model

The model development lifecycle comprises several processes, some of which are repeated cyclically in an iterative manner until satisfactory results have been achieved.

Though reinforcement learning, supervised learning and unsupervised learning each have elements of training that are unique to their paradigm, the general workflow required to train a model consists of these steps:

- **Model selection**
- **Data collection**
- **Data preparation**
- **Selecting hyperparameters**
- **Performance on training data**
- **Calculating loss (or reward)**
- **Optimizing parameters**
- **Model evaluation**

### Model selection

Selecting the right algorithm (or neural network architecture) isn’t solely a function of the problem that you need to solve and the types of data that the model will work with. The ideal model type also depends on whether you prioritize speed and efficiency over accuracy and performance (or the reverse), and on budget and the hardware or compute resources available to you. For example, training or fine-tuning an LLM often requires multiple graphics processing units (GPUs).

### Data collection

Obtaining high-quality training data for your use case is not trivial, especially for deep learning models that often require many thousands if not millions of examples for adequate training. Though a proprietary data pipeline presents unique opportunities for customization and competitive advantages, there are reputable open source datasets available for most domains and tasks. In some fields, particularly natural language processing (NLP), generating [synthetic data](https://research.ibm.com/blog/what-is-synthetic-data) is an increasingly viable option.

### Data preparation

To be used for training, raw data—especially when gathered firsthand or collated from multiple data sources—typically requires some preprocessing, which might include cleaning the data, normalizing values and standardizing formatting. Many services exist to automate some or all of this process, such as [Docling](https://github.com/DS4SD/docling), an open source tool that converts PDFs and other file formats into more machine-readable text while retaining important structural elements.

For supervised learning, data must be labeled and sometimes annotated with significant detail. For instance, images used to train image segmentation models must be labeled down to the pixel level. This labeling can entail significant time and labor, both of which should be accounted for in timelines and budget.

### Selecting hyperparameters

Even once you’ve chosen an algorithm or model architecture, you still have more choices to make. Conventional ML algorithms are rarely one-size-fits-all, and neural networks are even less standardized. Selecting the right hyperparameters, the modular elements of an algorithm that are external to parameter optimization, is essential to efficient and successful training.

When training is not proceeding satisfactorily—or when working with unsupervised learning algorithms or nonparametric supervised learning algorithms such as decision trees—model performance can be tweaked and enhanced through hyperparameter tuning. Some trial and error might be necessary to arrive at the optimal learning rate, batch size, loss function (and regularization terms) or optimization algorithm.

One such parameter is the initialization of the learnable parameters. They’re typically randomized, but even the randomization of parameters has multiple strategies. Optimal initial parameters can also be “learned” through a technique called [meta learning](https://www.ibm.com/think/topics/few-shot-learning#Optimization-based+meta+learning).

### Performance on training data

After the initial parameters and hyperparameters have been set, the model processes a batch of input data examples drawn from the training dataset. Because the initial parameters are random, the model generally doesn’t yield “good” outputs yet. The goal of the first training run is simply to establish a baseline to then optimize. The batch size—the number of examples that are processed in each “batch” before calculating loss and optimizing parameters—is itself an important hyperparameter.

There are many open source frameworks for configuring and running machine learning models for training, such as [PyTorch](https://www.ibm.com/think/topics/pytorch), Keras or [TensorFlow](https://developer.ibm.com/components/tensorflow/). Most operate on Python or JavaScript and, being community-driven projects, offer extensive libraries of tutorial content for beginners.

### Calculating loss (or reward)

As your model works through training examples, your chosen loss function tracks the discrepancy between the model’s outputs and the “correct” updates for each input. In deep learning, wherein models are neural networks comprising various equations nested within one another, [backpropagation](https://www.ibm.com/think/topics/backpropagation) is used to calculate how each node of the neural network contributes to the overall loss.

In supervised learning, the formal goal of training is usually to minimize that loss function. Some model architectures, such as [variational autoencoders (VAEs)](https://www.ibm.com/think/topics/variational-autoencoder#How+variational+autoencoders+work), instead reformulate the problem in terms of maximizing some proxy for the loss function. RL algorithms typically seek to maximize a reward function and sometimes simultaneously minimize a regularization term that penalizes unwanted behaviors.

### Optimizing parameters

The optimization of an ML algorithm is usually performed by a separate algorithm. In mathematics, an optimization algorithm is designed to minimize or maximize some other function—in this case, a loss function or reward function—by determining optimal values for variables in that function. In ML, those variables are the weights and biases in an algorithm or between different nodes of a neural network.

The ideal optimization algorithm depends on the type of model being trained. Many ML algorithms, and especially neural network-based models, use variations of gradient descent. Certain algorithms with quadratic functions, such as support vector machines (SVMs), might be better served by [quadratic programming](https://en.wikipedia.org/wiki/Quadratic_programming). Linear regression algorithms are typically optimized through [least squares](https://www.cns.nyu.edu/~eero/NOTES/leastSquares.pdf) algorithms. Reinforcement learning has its own optimization algorithms, such as proximal policy optimization (PPO), direct policy optimization (DPO) or advantage actor critic (A2C).

This sequence of training steps—tuning hyperparameters, running the model on a batch of training data, calculating loss and optimizing parameters—is repeated across multiple iterations until loss has been sufficiently minimized.

### Model evaluation

Excellent performance on training data is not, unto itself, conclusive evidence that the model has been successfully trained and prepared for real-world deployment. Care must be taken to avoid [overfitting](https://www.ibm.com/think/topics/overfitting), wherein a model has essentially memorized the training data but cannot generalize well to new data (thus defeating the purpose of training). Overfitting can be understood as the machine learning equivalent of [“teaching to the test.”](https://en.wikipedia.org/wiki/Teaching_to_the_test)

To avoid overfitting, standard practice is to set aside a portion of the training dataset in a process called cross-validation. This process allows for the model to be tested on new data it hasn’t seen, ensuring that it has been properly trained.
