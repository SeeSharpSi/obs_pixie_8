---
title: What is backpropagation?
source: https://www.ibm.com/think/topics/backpropagation
author:
- '[[Dave Bergmann]]'
- '[[Cole Stryker]]'
published: 2024-07-02
created: 2026-08-31
description: "Backpropagation is a machine learning algorithm for training neural networks by using the chain rule to compute how network weights contribute to a loss function."
---

## What is backpropagation?

Backpropagation is a [machine learning](https://www.ibm.com/think/topics/machine-learning) technique essential to the optimization of [artificial neural networks](https://www.ibm.com/think/topics/neural-networks). It facilitates the use of [gradient descent](https://www.ibm.com/think/topics/gradient-descent) algorithms to update network weights, which is how the [deep learning](https://www.ibm.com/think/topics/deep-learning) models driving modern [artificial intelligence (AI)](https://www.ibm.com/think/topics/artificial-intelligence) “learn.”

Short for "backward propagation of error", backpropagation is an elegant method to calculate how changes to any of the weights or biases of a neural network will affect the accuracy of model predictions. It’s essential to the use of supervised learning, [semi-supervised learning](https://www.ibm.com/think/topics/semi-supervised-learning) or [self-supervised learning](https://www.ibm.com/think/topics/self-supervised-learning) to train neural networks.

Though equivalents and predecessors to backpropagation were independently proposed in varying contexts dating back to the 1960s, David E. Rumelhart, Geoffrey Hinton and Ronald J. Williams first published the formal learning algorithm. Their 1986 paper, “Learning representations by back-propagating errors,” provided the derivation of the backpropagation algorithm as used and understood in a modern machine learning context.

The logic of backpropagation is that the layers of neurons in artificial neural networks are essentially a series of nested mathematical functions. During training, those interconnected equations are nested into yet another function: a "loss function" that measures the difference (or “loss”) between the desired output (or “ground truth”) for a given input and the neural network’s actual output.

We can therefore use the "chain rule", a [calculus principle dating back to the 17<sup>th</sup> century](https://www.jstor.org/stable/27900650), to compute the rate at which each neuron contributes to overall loss. In doing so, we can calculate the impact of changes to any variable—that is, to any weight or bias—within the equations those neurons represent.

Mathematically speaking, backpropagation works backward from the output to efficiently calculate the "gradient" of the loss function: a vector of derivatives for every equation in the network. This gradient tells optimization algorithms such as "gradient descent" which equations to adjust, and which direction to adjust them in, to reduce loss.

These three interwoven processes—a loss function that tracks model error across different inputs, the backward propagation of that error to see how different parts of the network contribute to the error and the gradient descent algorithms that adjust model weights accordingly—are how deep learning models “learn.” As such, backpropagation is fundamental to training neural network models, from the most basic [multilayer perceptrons](https://www.ibm.com/docs/en/spss-statistics/saas?topic=networks-multilayer-perceptron) to the complex deep neural network architectures used for [generative AI](https://www.ibm.com/topics/generative-ai).

## How neural networks work

Because the process of backpropagation is so fundamental to how neural networks are trained, a helpful explanation of the process requires a working understanding of how neural networks make predictions.

Most importantly, it’s useful to understand the purpose and context of "weights" and "biases": the adjustable model parameters that are optimized through backpropagation and gradient descent.

### Neural network structure

Neural networks aim to roughly mimic the structure of the human brain. They’re composed of many interconnected nodes (or neurons), arranged in layers. Neural networks make predictions once the original input data has made a "forward pass" through the entire network.

Neurons in the "input layer" receive input data, usually as a [vector embedding](https://www.ibm.com/think/topics/vector-embedding), with each input neuron receiving an individual feature of the input vector. For example, a model that works with 10x10 pixel grayscale images will typically have 100 neurons in its input layer, with each input neuron corresponding to an individual pixel. Neural networks thus typically require inputs of fixed size, though techniques like pooling or normalization can provide some flexibility.

In a standard feedforward neural network, each neuron in the input layer is connected to each of the neurons in the following layer, which are themselves connected to the neurons in the next layer, and so on until the *output layer* where final predictions are made. The intermediate layers between the input layer and output layer called the network’s *hidden layers*, are where most “learning” occurs.

While some specialized neural network architectures, such as [mixture of expert](https://www.ibm.com/think/topics/mixture-of-experts) models or [convolutional neural networks](https://www.ibm.com/think/topics/convolutional-neural-networks), entail variations, additions or exceptions to this straightforward arrangement, all neural networks employ this core structure.

![Diagram of a neural network with three hidden layers: input layer, multiple hidden layers, output layer](https://assets.ibm.com/is/image/ibm/ICLH_Diagram_Batch_01_03-DeepNeuralNetwork?ts=1787568252585&dpr=off)   Visual depiction of a basic feedforward neural network with 3 hidden layers. During inference, information about input data flows from left to right; during backpropagation, information about error flows from right to left.

### Weights and biases

Though each neuron receives input from each node of the previous layer, not all of those inputs are given the same importance. Each connection between two neurons is given a unique "weight": a multiplier that increases or decreases one neuron’s contribution to a neuron in the following layer.

Each individual neuron may also be given a "bias": a constant value added to the sum of the weighted inputs from the neurons in the previous layer.[](#_msocom_1)

The ultimate goal of backpropagation and gradient descent is to calculate the weights and biases that will yield the best model predictions. Neurons corresponding to data features that significantly correlate with accurate predictions are given greater weights; other connections may be given weights approaching zero.

Modern deep neural networks, often with dozens of hidden layers each containing many neurons, might comprise thousands, millions or—in the case of most large language models (LLMs)—billions of such adjustable parameters.

### Activation functions

Each neuron is configured to perform a mathematical operation, called an “activation function”, on the sum of varyingly weighted inputs it receives from nodes in the previous layer. Activation functions introduce “nonlinearity”*,* enabling the model to capture complex patterns in input data and yield gradients that can be optimized. Using only linear activation functions essentially collapses the neural network into a [linear regression](https://www.ibm.com/think/topics/linear-regression) model.

[Common activation functions](https://www.ibm.com/docs/spss-statistics/29.0.0?topic=perceptron-architecture-multilayer&mhsrc=ibmsearch_a&mhq=Architecture%20%26lpar%3BMultilayer%20Perceptron%26rpar%3B%20) in neural networks include:

- The **sigmoid** function, which maps any input to a value between 0 and 1.
- The **hyperbolic tangent** (or **tanh**) function, which maps inputs to a value between -1 and 1.
- The **rectified linear unit** (or **ReLU**), which maps any negative input to 0 and leaves any positive input unchanged.
- The **softmax** function, which converts a vector of inputs to a vector whose elements range from 0 and 1 and collectively sum to 1.

Consider a hypothetical hidden unit *z,* with a *tanh* activation function and bias term *t,* in the second layer of a neural network with 3 input nodes, *a*, *b* and *c,* in its input layer. Each of the connections between the input nodes and node *z* has a unique weight, *w.* We can describe the output value that node *z* will pass to the neurons in the next layer with the simplified equation *z* = *tanh*(*w<sub>az</sub>*a + w<sub>bz</sub>*b* + *w<sub>cz</sub>*c* *+ t*)*.*

The neuron *z* is connected to neurons in the next layer. That equation for *z* is therefore part of the activation functions in the next layer and, by extension, also part of every activation function for any neurons in any subsequent layer.

![Formulas and visualizations for common activation functions in neural networks. LEFT: sigmoid; CENTER: tanh; RIGHT: ReLU](https://assets.ibm.com/is/image/ibm/common-activation-functions-combined?ts=1763386818015&dpr=off)   Formulas and visualizations for common activation functions in neural networks. LEFT: sigmoid; CENTER: tanh; RIGHT: ReLU

## Why use backpropagation?

As will be explained in the following sections, backpropagation is a remarkably fast, efficient algorithm to untangle the massive web of interconnected variables and equations in a neural network.

To illustrate backpropagation’s efficiency, Michael Nielsen compares it to a simple and intuitive alternative approach to computing the gradient of a neural network’s loss function in his online textbook, "Neural Networks and Deep Learning"*.*

As Nielsen explains, one can easily estimate the impact of changes to any specific weight *w*<sub>j</sub> in the network by simply completing a forward pass for two slightly different values of *w*<sub>j</sub>, while keeping all other parameters unchanged, and comparing the resulting loss for each pass. By formalizing that process into a straightforward equation and implementing a few lines of code in Python, you can automate that process for each weight in the network.

But now imagine that there are 1 million weights in your model, which would be quite modest for a modern deep learning model. To compute the entire gradient, you’d need to complete 1,000,001 forward passes through the network: 1 to establish a baseline, and then another pass to evaluate changes to each of the million weights.[](#_ftn1)

Backpropagation can achieve the same goal in *2* passes: 1 forward pass and 1 backward pass.

## Key mathematical concepts for backpropagation

To simplify an explanation of how backpropagation works, it will be helpful to first briefly review some core mathematical concepts and terminology.

- A **derivative** is the rate of change in an equation at a specific instant. In a linear equation, the rate of change is a constant slope. In a *nonlinear* equation, like those used for activation functions, this slope varies. **Differentiation** is the process of finding the derivative of a specific function. By differentiating a nonlinear function, we can then find the slope—its instantaneous rate of change—at any specific point in the curve.

- In functions with multiple variables, a **partial derivative** is the derivative of one variable concerning the others. If we change one variable, but keep the others the same, how does the output of the overall function change? The activation functions of individual nodes in a neural network have many variables, including the many inputs from neurons in previous layers and the weights applied to those inputs. When dealing with a specific node *n*, finding the partial derivatives of the activation functions of neurons from the previous layer allows us to isolate the impact of each on the overall output of *n*’s own activation function.

- A **gradient** is a vector containing all the partial derivatives of a function with multiple variables. It essentially represents all the factors affecting the rate at which the output of a complex equation will change following a change in the input.

- The **chain rule** is a formula for calculating the derivatives of functions that involve not just multiple variables, but multiple functions. For example, consider a composite function *ƒ*(*x*) *= A*(*B(x*)). The derivative of the composite function, *f*, is equal to the derivative of the outer function (*A*) multiplied by the derivative of the inner function (*B*).

The chain rule is essential to calculating the derivatives of activation functions in neural networks, which are composed of the outputs of activation functions of other neurons in previous layers.

Though the logic behind backpropagation is relatively straightforward, the mathematics and notation can become very complex, especially for those unfamiliar with variable calculus.

## How does backpropagation work?

Working backward from the model’s output, backpropagation applies the "chain rule" to calculate the influence of changes to each individual neural network parameter on the overall error of the model’s predictions.

Abstractly speaking, the purpose of backpropagation is to train a neural network to make better predictions through supervised learning. More fundamentally, the goal of backpropagation is to determine how model weights and biases should be adjusted to minimize error as measured by a "loss function"*.*

On a technical, mathematical level, the goal of backpropagation is to calculate the gradient of the loss function with respect to each of the individual parameters of the neural network. In simpler terms, backpropagation uses the chain rule to calculate the rate at which loss changes in response to any change to a specific weight (or bias) in the network.

Generally speaking, training neural networks with backpropagation entails the following steps:

- **A *forward pass****,* **making predictions on training data.**
- **A *loss function* measures the error of the model’s predictions during that forward pass.**
- ***Backpropagation* of error, or a *backward pass,* to calculate the partial derivatives of the loss function.**
- ***Gradient descent,* to update model weights.**

### Forward pass

Neural networks output predictions through *forward propagation.* Forward propagation is essentially a long series of nested equations, with the outputs of the activation functions from one layer of neurons serving as inputs to the activation functions of neurons in the next layer.

Model training typically begins with a random initialization of weights and biases. Model *hyperparameters*, such as the number of hidden layers, the number of nodes in each layer and activation functions for specific neurons, are configured manually and not subject to training.

In each *forward pass*, an input is sampled from the training data set. The nodes of the input layer receive the input vector, and each passes their value—multiplied by some random initial weight—to the nodes of the first hidden layer. The hidden units take the weighted sum of these output values as input to an activation function, whose output value (conditioned by a random initial weight) serves as input to the neurons in the next layer. This continues until the output layer, where a final prediction occurs.

Consider this simplified example of a neural network that classifies inputs into one of 5 categories:

- The *input layer* receives a numerical representation of an example sampled from the training data.
- The input nodes pass their values to hidden units in the next layer. The hidden units use a *ReLU* activation function.
- Data flows through the *hidden layers,* each progressively extracting key features until it reaches the *output layer.*
- The output layer contains 5 neurons, each corresponding to a potential classification category.
- The output neurons use a *softmax* activation function. The output value of each output neuron’s softmax function corresponds to the probability, out of 1, that the input should be classified as the category that the neuron represents.
- The network predicts that the original input belongs to the category of whichever output neuron has the highest softmax value.

In a well-trained network, this model will consistently output a high probability value for the correct classification and output low probability values for the other, incorrect classifications. However, this neural network isn’t yet trained. At this point, its weights and biases have random initial values, so its predictions are generally inaccurate.

### Loss function

After each forward pass, a "loss function*"* measures the difference (or “loss”) between the model’s predicted output for a given input and the correct predictions (or “ground truth”) for that input. In other words, it measures how different the model’s actual output is from the desired output.

In supervised learning, which uses labeled data, ground truth is provided by manual annotations. In self-supervised learning, which masks or transforms parts of unlabeled data samples and task models by reconstructing it, the original sample serves as ground truth.

The goal of this loss function is to quantify inaccuracy in a way that appropriately reflects both the nature and magnitude of the error of the model’s output for each input. Different mathematical formulas for loss are best suited to specific tasks: for example, variants of *mean squared error* work well for regression problems, whereas variants of *cross-entropy loss* work well for classification.

Because the loss function takes the output of a neural network as an input, and that neural network output is a composite function comprising many nested activation functions of individual neurons, differentiating the loss function entails differentiating the entire network. To do so, backpropagation uses the chain rule.

**"Loss function," "cost function" or "error function?"**  
 It’s worth quickly noting that in some contexts, the terms *cost function* or *error function* are used in place of *loss function*, with “cost” or “error” replacing “loss*.”*

Though some machine learning literature assigns unique nuance to each term, they’re generally interchangeable.<sup>1</sup> An *objective function* is a broader term for any such evaluation function that we want to either minimize or maximize. *Loss function, cost function* or *error* *function* refer specifically to terms we want to minimize.

### Backwards pass

Starting from the final layer, a "backward pass" differentiates the loss function to compute how each individual parameter of the network contributes to the overall error for a single input.

Returning to our earlier example of the classifier model, we would start with the 5 neurons in the final layer, which we’ll call layer *L.* The softmax value of each output neuron represents the likelihood, out of 1, that an input belongs to their category. In a perfectly trained model, the neuron representing the correct classification would have an output value close to 1 and the other neurons would have an output value close to 0.

For now, we’ll focus on the output unit representing the correct prediction, which we’ll call *L<sub>c</sub>. L*<sub>c</sub>’s activation function is a composite function, containing the many nested activation functions of the entire neural network from the input layer to the output layer. Minimizing the loss function would entail making adjustments throughout the network that bring the output of *L*<sub>c</sub>’s activation function closer to 1.

To do so, we’ll need to know how any change in previous layers will change *L*<sub>c</sub>’s own output. In other words, we’ll need to find the *partial derivatives* of *L*<sub>c</sub>’s activation function.

The output of *L*<sub>c</sub>’s activation function depends on the contributions that it receives from neurons in the penultimate layer, which we’ll call layer *L-1.* One way to change *L*<sub>c</sub>’s output is to change the weights between the neurons in *L-1* and *L*<sub>c</sub>. By calculating the partial derivative of each *L-1* weight with respect to the other weights, we can see how increasing or decreasing any of them will bring the output of *L*<sub>c</sub> closer to (or further away from) 1.

But that’s not the only way to change *L*<sub>c</sub>’s output. The contributions *L*<sub>c</sub> receives from *L-1* neurons are determined not just by the *weights* applied to *L-1*’s output values, but by the actual (pre-weight) output values themselves. The *L-1* neurons’ output values, in turn, are influenced by weights applied to inputs they receive from *L-2.* So we can differentiate the activation functions in *L-1* to find the partial derivatives of the weights applied to *L-2*’s contributions. These partial derivatives show us how any change to an *L-2* weight will affect the outputs in *L-1,* which would subsequently affect the output value of *L*<sub>c</sub> and thereby affect the loss function.

By that same logic, we could also influence the output values that *L-1* neurons receive from *L-2* neurons by adjusting the contributions that *L-2* neurons receive from neurons in *L-3*. So we find the partial derivatives in *L-3*, and so on*,* recursively repeating this process until we’ve reached the input layer. When we’re done, we have the ***gradient*** of the loss function: a vector of its partial derivative for each weight and bias parameter in the network.

We’ve now completed a forward pass and backward pass for a single training example. However, our goal is to train the model to generalize well to new inputs. To do so requires training on a large number of samples that reflect the diversity and range of inputs the model will be tasked with making predictions on post-training.

### Gradient descent

Now that we have the gradients of the loss function with respect to each weight and bias parameter in the network, we can minimize the loss function—and thus optimize the model—by using [gradient descent](https://www.ibm.com/think/topics/gradient-descent) to update the model parameters.

Moving down—*descending—*the gradient of the loss function will decrease the loss. Since the gradient we calculated during backpropagation contains the partial derivatives for every model parameter, we know which direction to “step” each of our parameters to reduce loss.

Each step reflects the model “learning” from its training data. Our goal is to iteratively update weights until we have reached the minimum gradient. The object of gradient descent algorithms is to find the specific parameter adjustments that will move us down the gradient most efficiently.

#### Learning rate

The size of each step is a tunable hyperparameter, called the *learning rate.* Choosing the right learning rate is important for efficient and effective training.

Recall that the activation functions in a neural network are *nonlinear*. Some gradients may be approximately U-shaped: stepping in one direction moves *down* the gradient, but continuing to step in that direction will eventually move *up* the gradient.

A low learning rate ensures we always step in the right direction, but calculating so many changes is time-consuming and computationally expensive. A high learning rate is computationally efficient, but risks overshooting the minimum.

#### Batch size

Another consideration in gradient descent is how often to update weights. One option is to compute the gradients for every example in the training data set, then take an average of those gradients and use it to update parameters. The process is repeated iteratively in a series of training epochs until the error rate stabilizes. This method is *batch gradient descent*.

When the training data set is very large—as it typically is in deep learning—batch gradient descent entails prohibitively long processing times. Calculating gradients for millions of examples for each iteration of weight updates becomes inefficient. In *stochastic gradient descent* (SGD), each epoch uses a single training example for each step. While loss might fluctuate on an epoch-to-epoch basis, it quickly converges to the minimum throughout many updates.

![Gradient descent diagram, "value of weight" in x-axis and "loss" in y-axis, and a "starting point" in the upper left side of the diagram, there is the text in the lowest part "point of convergence i.e. where the cost function is at its minimum"](https://assets.ibm.com/is/image/ibm/ICLH_Diagram_Batch_01_04-GradientDescent?ts=1763386819907&dpr=off)   A visual demonstration of gradient descent

*Mini-batch gradient descent* represents a middle-ground approach. Training examples are randomly sampled in batches of fixed size, and their gradients are then calculated and averaged together. This mitigates the memory storage requirements of batch gradient descent while also reducing the relative instability of SGD.

## Footnotes

¹ “[Deep Learning](https://www.deeplearningbook.org/contents/numerical.html)”. Goodfellow et al. MIT Press. 2016.
