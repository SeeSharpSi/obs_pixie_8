---
title: What are model parameters?
source: https://www.ibm.com/think/topics/model-parameters
author:
- '[[Ivan Belcic]]'
- '[[Cole Stryker]]'
published: 2025-04-28
created: 2026-08-31
description: "Model parameters are the internal configuration variables of a machine learning model which control how it processes data and makes predictions."
---

## What are model parameters?

Model parameters are the learned values within a [machine learning](https://www.ibm.com/think/topics/machine-learning) model that determine how it maps input data to outputs, such as generated text or a predicted classification. The purpose of a machine learning algorithm is to adjust parameters until an [artificial intelligence (AI) model](https://www.ibm.com/think/topics/ai-model)’s outputs closely align with the expected results.

The values of these parameters determine a model’s predictions and ultimately the model’s performance on a given task. The number of parameters in a model directly influences the model’s ability to capture patterns across data points. Large models, such as those used in generative AI, can have billions of parameters, enabling them to generate highly sophisticated outputs. More parameters allows models to more accurately capture more nuanced patterns of data, but too many parameters risks [overfitting](https://www.ibm.com/think/topics/overfitting).

Different machine learning algorithms have different types of parameters. For example, regression models have coefficients, neural networks have weights and biases, and some algorithms, like support vector machines or state space models, have unique types of parameters.

Model parameters, variables learned during training, should not be confused with [hyperparameters](https://www.ibm.com/think/topics/hyperparameter-tuning), which are set in advance. Both types of parameters influence a model’s performance and behavior, but in significantly different ways.

## Model parameters simplified

Model parameters are present in simple models—even in the very simplest mathematical model possible, which describes a quantity changing at a constant rate.

### Linear regression

To find out how square footage might impact the price of a house, one could use a simple [linear regression](https://www.ibm.com/think/topics/linear-regression) model that uses the equation $y = mx + b$, where *m* (the slope) and *b* (the intercept) are parameters. By adjusting them, the resulting line shifts and tilts until it best fits the data.

### Classification

A slightly more complex example might be using a logistic regression model to determine whether or not a house will sell based on how many days the home is on the market.

Logistic regression uses the formula: $p = \frac{1}{1 + e^{-(w x + b)}}$ , where *p* = the “probability of selling” and *x* = “days on market.” Again, *w* and *b* are parameters the model “learns.” The equation has gotten a bit more complex, but there are still only 2 parameters at play.

## Types of model parameters

In machine learning, model parameters mainly come in 2 types: weights and biases. In the example of a simple linear regression model, $y
=
m
x
+
b$ , the weight corresponds to the slope *m*, controlling how strongly the input influences the output. The larger the weight, the more impact of the input. The bias corresponds to the intercept *b*. This lets the model shift the whole line up or down.

### Weights

*Weights* are the fundamental control knobs or settings for a model and determine how a model evaluates new data and makes predictions.

In linear regression models, weights determine the relative influence of each features used to represent each input data point. In neural networks, weights determine the relative influence of each neuron’s output on that of each of the neurons in the following layer.

In the example of a model trying to predict whether a house will sell based on factors like “days on market,” each of these factors has a weight reflecting how strongly that factor affects the likelihood of selling.

### Biases

*Biases* enable models to adjust outputs independently of model weights and inputs, acting as thresholds or offsets. Biases help models generalize and capture larger patterns and trends across a dataset.

Sticking with the home sale model, maybe historically, 60% of all houses in the area eventually sell, regardless of how many days on the market, across the board, even if a particular house has been listed for many days or has few showings. The bias allows the model to start with this realistic baseline probability and then adjust up or down based on the other inputs.

This usage of “bias” is a separate concept from [algorithmic bias](https://www.ibm.com/think/topics/algorithmic-bias), which is when a model yields discriminatory outcomes. Bias is also the term for the type of error that results from the model making incorrect assumption about the data, leading to a divergence between predicted and actual values. Both are unrelated to parameter bias.

### Other parameters

There are other types of parameters in the world of machine learning. The above simple models use weights and biases, as do far more complex neural networks, along with *gain* and *shift* parameters for normalization.

[Convolutional neural networks](https://www.ibm.com/think/topics/convolutional-neural-networks), for example have filters (also known as kernels), which detect spatial patterns. [Recurrent neural networks](https://www.ibm.com/think/topics/recurrent-neural-networks) with long short-term memory use gating parameters that control the flow of information through the network. Probabilistic models such as [Naive Bayes](https://www.ibm.com/think/topics/naive-bayes) use parameters to define conditional probabilities or the properties of probability distributions. [Support vector machines](https://www.ibm.com/think/topics/support-vector-machine) define parameters that position and orient “hyperplanes” to separate classes in feature space. [State space models](https://www.ibm.com/think/topics/state-space-model) have observation and noise parameters.

This is a limited list of examples, and different models’ parameters work in distinct ways. But across all of them, parameters determine how models map input data to outputs.

## Model parameters vs hyperparameters

Parameters are essentially the answers to the question the model is asking (e.g. “What is the best possible slope of the equation that will tell us with the greatest accuracy what the price of the home will be, based on square footage?”)

Hyperparameters, on the other hand, can be perceived as the rules of the game that tell the model how to find that answer. The data scientists training the model use their understanding of the problem to impose boundaries that determine how the model will search for answers.

Model parameters are internal to a model and are updated by it across iterations of the learning process in response to training data. The model updates parameter values during training. Parameters control how a model reacts to unseen data.

Model hyperparameters are external to a model and set in advance of training through [hyperparameter tuning](https://www.ibm.com/think/topics/hyperparameter-tuning). Some hyperparameters determine the model’s behavior during training, such as the [learning rate](https://www.ibm.com/think/topics/learning-rate) during gradient descent or the number of epochs of the training process.

Other hyperparameters are responsible for the model’s shape and structure, such as the number of [decision trees](https://www.ibm.com/think/topics/decision-trees) in a [random forest](https://www.ibm.com/think/topics/random-forest), clusters in [k-means clustering](https://www.ibm.com/think/topics/k-means-clustering) or hidden layers in a [neural network](https://www.ibm.com/think/topics/neural-networks).

## Model parameters in neural networks

Machine learning models can be far more complex than the previous examples. In a [neural network](https://www.ibm.com/think/topics/neural-networks) such as a [large language model](https://www.ibm.com/think/topics/large-language-models) (LLM), a model makes decisions in a manner similar to the way biological neurons work together in the human brain. Every neural network consists of layers of artificial *neurons*, where each neuron represents a mathematical function that processes numbers. In [deep learning](https://www.ibm.com/think/topics/deep-learning), neural networks consist of many of these layers.

![Illustration of a deep neural network with labeled input, multiple hidden, and output layers. The graphic shows columns of circular nodes connected by intersecting lines to represent neurons and weighted connections. Blue and teal colors distinguish different layers and emphasize the flow of data through the network. Text labels include 'Deep neural network', 'Input layer', 'Multiple hidden layer', and 'Output layer'.](https://assets.ibm.com/is/image/ibm/ICLH_Diagram_Batch_01_03-DeepNeuralNetwork?ts=1787568252585&dpr=off)

### From layer to layer

Each neuron controls how strongly one part of the network influences the other. Weights determine the strength of the connections between neurons: the degree to which one neuron’s output affects the next neuron’s input.

During training, the network receives inputs. To continue the example of home prices, this might be square footage, year of construction, neighborhood demographic data, and dozens of other inputs.

These input features are passed into the first layer of neurons. Each input is multiplied by a weight, the network’s best guess about how important that neuron is, and a bias is added to improve flexibility, giving neurons some independence from the influence of the weighted sum of the inputs from neurons in the previous layer. An activation function decides how strongly that neuron “fires” and passes information to the next layer as input to the activation functions of each individual neuron in the next layer. Each of these neuron-to-neuron connections have their own weight.

The weights form a matrix, biases form a vector and the layer computes linear combinations of inputs + bias, then passes the result through an activation function, such as a sigmoid, tanh, ReLU or softmax function. The job of this function is to introduce nonlinearity, which allows the network to learn and model complex patterns instead of just linear relationships.

The data moves through the subsequent “hidden” layers. The first hidden layer might combine the home’s square footage and its number of bedrooms to arrive at “overall living space.” Another layer might combine the home’s geographical location + the rating of its school district to determine the “desirability of the neighborhood.” The model doesn’t have a human’s understanding of what “neighborhood desirability” is, it merely recognizes patterns in the numbers of its training data and makes correlations.

From layer to layer, the network begins to “understand” which patterns are most relevant. These stacked layers turn simple operations into a powerful network capable of learning complex, hierarchical patterns.

### Loss and backpropagation

In the next stage, the network computes the loss (the difference between the network’s output and ground truth—the structure of data present in training dataset). This provides a single number representing how far off the model is.

Then, during [backpropagation](https://www.ibm.com/think/topics/backpropagation), the network calculates the gradient of the loss with respect to the weights and biases, which tells the network which parameters are influencing the loss, and how to adjust them to minimize it. This happens in reverse order, layer by layer, with a [gradient descent](https://www.ibm.com/think/topics/gradient-descent) [algorithm](https://www.ibm.com/think/topics/machine-learning-algorithms). Optimization algorithms such as gradient descent are designed to minimize a loss function, telling the model how to efficiently change its parameters to reduce loss.

The above processes repeat until the model is capable of delivering outputs (in this case, predicted home price) at a desired level of performance.

The example of predicting home prices expresses how neural networks take many features at once, combine them in nonlinear ways, and output a useful prediction. However, this could have been accomplished by a simpler linear regression model. Neural networks really shine when data is unstructured or when patterns are too complex or high-dimensional for traditional models. For example, a neural network could be used to process satellite photos and neighborhood map data to predict sale price. Or, a neural network could be trained to recognize key terms in listing descriptions such as “quiet street” or “new roof.”

### Fine-tuning

When initial training is complete, [AI models](https://www.ibm.com/think/topics/ai-model) can be further adapted to specific tasks or subject areas. Fine-tuning is the process of adapting a pre-trained model for specific use cases. To do this, the model’s parameters are updated through additional training on new data.

## Other types of learning

The above example of the neural network used to predict home prices describes [supervised learning](https://www.ibm.com/think/topics/supervised-learning), where models learn using labeled data. In this context, the model is given both inputs and the correct outputs. The model compares its predictions with the ground truth (in this case, labeled data). Fine-tuning often happens in a supervised context.

[Unsupervised learning](https://www.ibm.com/think/topics/unsupervised-learning) allows models to learn parameters by finding patterns or structures in unlabeled data, without being told the “right answer.” Instead of comparing predictions to ground truth labels (as in supervised learning), these models optimize objectives that measure how well the model explains the data itself. For example, in [clustering](https://www.ibm.com/think/topics/clustering), parameters (like cluster centroids in k-means) are updated iteratively so that similar points are grouped closer together. In [dimensionality reduction](https://www.ibm.com/think/topics/dimensionality-reduction), parameters are learned by finding directions that capture the most variance in the data.

In [reinforcement learning](https://www.ibm.com/think/topics/reinforcement-learning), A model (or an agent powered by a model) interacts with an environment, receiving rewards for correct actions. The parameters usually define a policy or value function estimating expected reward. Parameters are updated by comparing predicted rewards to actual rewards received.

## Validating model parameter performance

Improving performance on training data is the objective of training, but that’s only a means to an end. The primary goal is *generalization*, which is achieved by training the model in a way that it will generalize well to real-world tasks that it didn’t see in its training data.

Care must be taken to avoid pitfalls such as overfitting, when parameters capture noise or random fluctuations in the [training data](https://www.ibm.com/think/topics/training-data), leading to poor generalization on new data. Parameters must be flexible enough to learn meaningful patterns but not so flexible that they memorize irrelevant details.

Several [data science](https://www.ibm.com/think/topics/data-science) techniques are used to evaluate model performance. Cross-validation is a model evaluation technique where the dataset is split into several parts (folds). The model is trained on some folds and tested on the remaining fold, and this process is repeated until every fold has been used as the test set. This reduces the risk of overfitting, since the model is tested on multiple partitions of the data. Cross-validation doesn’t directly change the parameters, but it tests how well the learned parameters generalize to unseen data. If performance is consistent across folds, the parameters are likely well-optimized. If not, then the model parameters might be overly fit to the subset of the training data that it has seen already. Further training on more diverse data may improve generalization.

Another technique is bootstrapping, a statistical method involving the creation of new datasets by randomly sampling with replacement from the original dataset. Bootstrapping produces many sets of parameters, since each bootstrap sample is slightly different. By looking at the variation across these bootstrapped models, one can measure how reliable the parameters are when trained on slightly different data.

Practitioners also rely on metrics that quantify [model performance](https://www.ibm.com/think/insights/model-performance), such as accuracy, precision, recall or mean squared error. These provide objective feedback on whether the current parameters are moving the model in the right direction.
