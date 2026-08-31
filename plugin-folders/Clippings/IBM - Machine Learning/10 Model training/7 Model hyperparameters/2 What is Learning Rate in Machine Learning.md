---
title: What is learning rate in machine learning?
source: https://www.ibm.com/think/topics/learning-rate
author:
- '[[Ivan Belcic]]'
- '[[Cole Stryker]]'
published: 2024-11-28
created: 2026-08-31
description: "Learning rate is a hyperparameter that governs how much a machine learning model adjusts its parameters at each step of its optimization algorithm. The learning rate can determine whether a model delivers optimal performance or fails to learn during the training process."
---

## What is learning rate in machine learning?

Learning rate is a hyperparameter that governs how much a [machine learning](https://www.ibm.com/topics/machine-learning) model adjusts its parameters at each step of its optimization algorithm. The learning rate can determine whether a model delivers optimal performance or fails to learn during the training process.

The goal of the optimization algorithm is to minimize the loss function that measures the gap between a model’s predictions and real-world data. Each time the model runs its optimization algorithm, it updates its [model parameters](https://www.ibm.com/think/topics/model-parameters) based on the result. Learning rate, or *step size,* is represented by the Greek letter *η*, and determines the size of the changes the model is permitted to make.

Learning rate helps ensure that a model learns enough from training to make meaningful adjustments to its parameters while also not overcorrecting. Imagine descending a hill. To reach the bottom safely, one must travel fast enough to make meaningful progress, but not too fast that one loses control and stumbles. The best learning rate sets a safe speed of descent.

Each training step represents the model overriding its previous understanding of its dataset. A [neural network](https://www.ibm.com/topics/neural-networks) “learns” more about its training data with each pass of its optimization algorithm.

## Why is learning rate important?

Learning rate is important because it guides [AI models](https://www.ibm.com/topics/ai-model) in learning effectively from its training data.

A low learning rate doesn’t let the model “learn” enough at each step. The model updates its parameters too slowly and take too long to reach convergence. But that doesn’t mean that a high learning rate is the answer.

With a high learning rate, the algorithm can fall victim to overshooting: where it goes too far in correcting its mistakes. In this case, the algorithm needs a smaller learning rate, but not too small that learning is inefficient.

As an example, imagine an alien who has come to learn about life on Earth. The alien sees cats, dogs, horses, pigs and cows and concludes that all animals have four legs. Then, the alien sees a chicken. Is this creature also an animal? Depending on the alien’s learning rate, they will reach one of three conclusions:

- At an **optimal learning rate**, the alien will conclude that chickens are also animals. And if that is the case, this must mean that leg quantity is not a key determinant of whether something is an animal or not.

- If the alien has a **low learning rate**, it can’t gain enough insight from this single chicken. The alien will conclude that chickens are not animals because they do not have four legs. The alien’s small learning rate does not allow it to update its thinking until it sees more chickens.

- At a **high learning rate**, the alien will overcorrect. Now, it will conclude that because the chicken is an animal, and because the chicken has two legs, that *all* animals must have two legs. A high learning rate means that the model learns “too much” at once.

Different learning rates result in different learning outcomes. The best learning rate is one that allows the algorithm to adjust the model’s parameters in a timely manner without overshooting the point of convergence.

## What are parameters in machine learning?

Parameters are configuration variables that govern how a deep learning model works. Parameters are analogous to a model’s settings in that they determine its behavior and can be adjusted to improve the model’s performance.

### Model-learned parameters

Model-learned parameters, or model weights, are internal to the model and learned during training. At each training step, the model changes its internal parameters to improve its performance. The size of the changes the model makes is set by the learning rate. The configuration of a model’s parameters directly affects its performance.

When [fine-tuning](https://www.ibm.com/topics/fine-tuning) a model, smaller adjustments are needed because the model has already been trained. Fine-tuning typically requires a lower learning rate than when initially training a model.

### Hyperparameters

Hyperparameters are external rules that shape the model’s structure and training process. They are configured by the people responsible for training the model. Learning rate is one such hyperparameter and typically has a value of between 0.0 and 1.0.

Two other fundamental hyperparameters are:

- **Epoch:** the number of times the entire training dataset passes through the model during training. An epoch is complete when the model processes each sample in its training data one time. The epoch hyperparameter sets the number of epochs in the training process.

- **Batch size:** Training epochs can be broken into smaller chunks called batches. The model updates its weights after each training batch.

Epoch sets the duration of the training process, while batch size determines how often the model updates its weights. Learning rate tells the model how much to learn after each batch.

## What is an optimization algorithm?

An optimization algorithm, or learning algorithm, is a programming process that teaches a [deep learning](https://www.ibm.com/topics/deep-learning) model how to learn from its training data and update its model weights. Learning algorithms are made up of a [loss function](https://www.ibm.com/think/topics/loss-function)—also known as a cost function or error function—and a method for optimizing the model weights.

Each iteration of the learning algorithm further refines the model. When a model can no longer be improved with further training, it is said to have reached *convergence*.

### Gradient descent

[Gradient descent](https://www.ibm.com/topics/gradient-descent) is an optimization algorithm for training machine learning models. Gradient descent algorithms use a loss function to chart the difference between a [machine learning algorithm](https://www.ibm.com/topics/machine-learning-algorithms)’s predictions and actual values. The gradient is the slope of the function, representing its potential values.

The goal of the optimization algorithm is to descend the gradient to its local minimum, where the function produces the lowest output. But local minima are not necessarily the function’s singular global minimum, or its overall minimum value. Data scientists use supplementary methods, such as other algorithms and [regularization](https://www.ibm.com/topics/regularization), to keep a model from getting stuck at a suboptimal local minimum as the loss function output decreases.

The process of updating a model’s weights through the minimizing of its loss function is known as [backpropagation](https://www.ibm.com/think/topics/backpropagation). Gradient descent is a common method of carrying out the backpropagation technique.

Each time the algorithm updates the model’s parameters to reduce the loss function and descend the gradient, the model gets a bit closer to convergence. The learning rate controls this descent by limiting the pace at which the algorithm updates model weights.

There are three types of gradient descent:

- **Batch gradient descent** iterates after calculating loss for all the samples in the dataset. It is highly stable, but not the best at achieving optimal convergence.

- **Stochastic gradient descent (SGD)** randomly selects one data point per iteration, greatly increasing speed and nuance. But its high update frequency can reduce stability. SGD has many variants, including Adam, AdaGrad and RMSProp.

- **Mini-batch gradient descent** is a compromise method that chooses a small group of data points per iteration instead. It provides a good update frequency and speed without sacrificing stability.

## How to determine the optimal learning rate

Determining a good learning rate is largely a trial-and-error process. There is no foolproof [data science](https://www.ibm.com/topics/data-science) technique that would guarantee an optimal initial learning rate without assessing progress during training.

Common methods for determining learning rate include:

- Grid search

- Learning rate schedules

- Adaptive learning rate

- Hyperparameter optimization

Learning rate optimization rests heavily on the core principles of decay and momentum. Many deep learning libraries calculate decay and momentum on behalf of users. One such library is the open source Keras API, written in Python with support for TensorFlow, JAX and [PyTorch](https://www.ibm.com/topics/pytorch).

- **Decay** slows the learning rate as training progresses. Effective use of decay allows the model to learn quickly at first, then more incrementally to avoid overshooting convergence.

- **Momentum** is the inertia of the optimization algorithm. It increases learning rate when the gradient follows the same direction—meaning that the algorithm has yet to reach convergence—while bypassing local minima to continue downward progress. Increasing the momentum can lead to faster convergence. Low momentum can stall training at minor local minima, while high momentum can accidentally skip over significant local minima.

### Grid search

Grid search is a brute force method for determining learning rate. Data scientists assemble a grid containing all potential learning rates. Then, each learning rate is tested and validated. Validation tests the trained model on a new set of data and further updates its hyperparameters.

While grid search facilitates an exhaustive learning rate evaluation process, it is time-consuming and compute-intense.

### Learning rate schedules

Learning rate schedules update the learning rate during the training process according to one of several predetermined plans. Common learning rate schedules include:

- Fixed learning rate

- Time-based decay

- Step decay

- Exponential decay

- Polynomial decay

#### Fixed learning rate

A fixed learning rate, or constant learning rate, does not change during training. With a fixed learning rate, momentum and decay remain static during training. A fixed learning rate gives a benchmark or reference point from which to test other learning rate strategies.

#### Time-based decay

A time-based learning schedule triggers learning rate decay after a predetermined number of training epochs or at specified epochs. The amount by which the learning rate decays is based on the learning rate of the previous cycle. A typical time-based learning schedule bases the decay on a factor inversely proportional to the number of epochs.

#### Step decay

Step decay reduces learning rate by a predetermined factor, such as halving, after a set number of epochs.

#### Exponential decay

Exponential decay learning rates decrease exponentially after a set number of epochs. Otherwise, exponential decay learning schedules are similar to step decay schedules.

#### Polynomial decay

In a polynomial learning schedule, decay is determined by a polynomial function of the current epoch. Multiplying the epoch by a higher exponent increases the rate of decay, while a lower power keeps a steadier decay rate.

#### Cyclical learning rate schedule

A cyclical learning schedule defines a minimum and maximum learning rate, then bounces the learning rate between the two. A triangular schedule linearly increases from the minimum to the maximum and back by a set constant. Other schedules use cosine, sinusoidal or parabolic functions.

### Adaptive learning rate

Adaptive learning algorithms dynamically adjust in response to current conditions or previous iterations. In contrast, scheduled learning rates all depend on predefined hyperparameters.

Many adaptive learning methods are SGD variants. Notable adaptive learning algorithms include:

- **AdaGrad:** The AdaGrad (adaptive gradient) family of algorithms, introduced in 2011, updates the learning rate separately for each parameter. It usually sets an inversely proportional relationship between learning rate and feature frequency. This approach maintains focus on more relevant features in the dataset.

- **RMSProp:** RMSProp (root mean square propagation) adjusts the learning weight for each parameter according to a moving average of the squares of each gradient. It improves on AdaGrad by ignoring gradients in the distant past, increasing stability and leading to faster convergence.

- **Adam:** Introduced in 2014, Adam (adaptive moment estimation) combines momentum with RMSProp to adjust each parameter’s learning rate based on its previous gradients. Later versions of Adam added a warm start, which gradually increases learning rate when beginning training.

### Hyperparameter optimization

Hyperparameter optimization, or [hyperparameter tuning](https://www.ibm.com/think/topics/hyperparameter-tuning), is the practice of identifying the optimal configuration for all hyperparameters, including learning rate. Hyperparameter tuning algorithms automate the process of configuring optimal hyperparameters, each algorithm favoring certain hyperparameters over others.

Searching for the overall optimal hyperparameter configuration allows consideration for how each hyperparameter affects the others. However, this approach can become computationally expensive, especially with large amounts of hyperparameters.
