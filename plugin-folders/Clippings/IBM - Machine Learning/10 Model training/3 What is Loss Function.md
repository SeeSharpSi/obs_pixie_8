---
title: What is a loss function?
source: https://www.ibm.com/think/topics/loss-function
author:
- '[[Dave Bergmann]]'
- '[[Cole Stryker]]'
published: 2024-07-12
created: 2026-08-31
description: "In machine learning, loss functions measure model performance by calculating the deviation of a model’s predictions from the “ground truth” predictions."
---

## What is a loss function?

In [machine learning (ML)](https://www.ibm.com/think/topics/machine-learning), a loss function is used to measure model performance by calculating the deviation of a model’s predictions from the correct, “ground truth” predictions. Optimizing a model entails adjusting model parameters to minimize the output of some loss function.

A loss function is a type of *objective function*, which in the context of [data science](https://www.ibm.com/think/topics/data-science) refers to any function whose minimization or maximization represents the objective of model training. The term “loss function,” which is usually synonymous with *cost function* or *error function*, refers specifically to situations where minimization is the training objective for a machine learning model.

In simple terms, a loss function tracks the degree of error in an [artificial intelligence (AI) model's](https://www.ibm.com/think/topics/ai-model) outputs. It does so by quantifying the difference (“loss”) between a predicted value—that is, the model’s output—for a given input and the actual value or *ground truth*. If a model’s predictions are accurate, the loss is small. If its predictions are inaccurate, the loss is large.

The fundamental goal of machine learning is to train models to output good predictions. Loss functions enable us to define and pursue that goal mathematically. During training, models “learn” to output better predictions by adjusting parameters in a way that reduces loss. A machine learning model has been sufficiently trained when loss has been minimized below some predetermined threshold.

## How do loss functions work?

In a typical training setup, a model makes predictions on a batch of sample data points drawn from the training data set and a loss function measures the average error for each example. This information is then used to optimize model parameters.

Loss functions are specific to [supervised learning](https://www.ibm.com/think/topics/supervised-learning), whose training tasks assume the existence of a correct answer: the *ground truth*. Conventional unsupervised learning algorithms, such as [clustering](https://www.ibm.com/think/topics/clustering) or [association](https://dataplatform.cloud.ibm.com/docs/content/wsd/nodes/associationrules.html?context=cpdaas), do not involve “right” or “wrong” answers, as they solely seek to discover intrinsic patterns in unlabeled data.

Supervised learning requires labeled data sets, in which manual annotations provide ground truth for each training sample. For example, [image segmentation](https://www.ibm.com/think/topics/image-segmentation) models require training samples with each pixel annotated according to its correct class. In [self-supervised learning](https://www.ibm.com/think/topics/self-supervised-learning), which masks or transforms parts of unlabeled data samples and tasks models with reconstructing them, the original sample itself serves as ground truth.

## Loss functions and model optimization

Loss functions are not simply evaluation metrics. Their explicit purpose is not only to measure model success, but also serve as input to an algorithm that optimizes the model’s parameters to minimize loss.

Optimization algorithms such as [gradient descent](https://www.ibm.com/think/topics/gradient-descent) typically use the *gradient* of the loss function. The gradient is the *derivative* of a function with multiple variables. Essentially, a derivative describes the rate and amount that the output of a function is changing at any point. Therefore, it’s important for loss functions to be *differentiable*: in other words, to have a derivative at all points.

Machine learning models learn to make accurate predictions through adjustments to certain model parameters. For example, a simple [linear regression](https://www.ibm.com/think/topics/linear-regression) algorithm models data with the function *y* = *wx*+*b*, where *y* is the model output, *x* is the input, *w* is a weight and *b* is bias. The model learns by updating the weight and bias terms until the loss function has been sufficiently minimized.

Using the gradient of the loss function, optimization algorithms determine which direction to “step” model parameters in order to move down the gradient and thereby reduce loss.

## Loss functions in deep learning

Deep learning models employ large artificial [neural networks](https://www.ibm.com/think/topics/neural-networks), comprising layers of interconnected neurons that each have their own nonlinear activation function, rather than relying on a singular function. To differentiate the entire network requires calculating the partial derivatives of hundreds, thousands or even millions of separate variables and activation functions with respect to the others.

To do so, neural networks use [backpropagation](https://www.ibm.com/think/topics/backpropagation) to find the gradient of the loss function after a *forward pass* that ends with a prediction on a data point from the training data set. Short for *backward propagation of error*, backpropagation begins with the output of the loss function. In a backwards pass through the network from output layer to input layer, backpropagation uses the chain rule to calculate how each individual weight and bias in the network contributed to overall loss.

The resulting gradient of partial derivatives for the entire network can then be used by gradient descent algorithms to iteratively update the network weights until loss has been sufficiently minimized.

## Regularization

Though models are trained and validated by making predictions on a training data set, performing well on training examples is not the ultimate objective. The true goal of machine learning is to train models that generalize well to new examples.

Relying solely on the minimization of a singular loss function is called “empirical risk minimization.” While it has an obvious, simple appeal, it runs the risk of a model [overfitting](https://www.ibm.com/think/topics/overfitting) the training data and thus generalizing poorly. To reduce this risk, among other purposes, many algorithms and architectures introduce *regularization terms* that modify the primary loss function.

For example, mean absolute error (MAE)—which in this context is called L1 regularization—can be used to enforce sparsity by penalizing the number of activated neurons in a neural network or the magnitude of their activation.

## Types of loss functions

There exists a wide variety of different loss functions, each suited to different objectives, data types and priorities. At the highest level, the most commonly used loss functions are divided into regression loss functions and classification loss functions.

- **Regression loss functions** measure errors in predictions involving *continuous* values. Though they most intuitively apply to models that directly estimate quantifiable concepts such as price, age, size or time, regression loss has a wide range of applications. For example, a regression loss function can be used to optimize an image model whose task entails estimating the color value of individual pixels.
- **Classification loss functions** measure errors in predictions involving *discrete* values, such as the category a data point belongs to or if an email is spam or not. Types of classification loss can be further subdivided into those suitable for *binary classification* and those suitable for *multi-class classification*.

## Choosing the right loss function

The selection of any one loss function from within those two broad categories should depend on the nature of one’s use case. Some machine learning algorithms require a specific loss function befitting their mathematical structure, but for most model architectures there are, at least theoretically, multiple options.

Different loss functions prioritize different types of error. For example, some might harshly penalize outliers whereas others control for minor variance. Some provide greater accuracy but at the expense of greater complex computation and, therefore, more time and computational resources to calculate.

Ultimately, the choice of a loss function should reflect the specific learning task, the nature of the data the model analyzes, the types of inaccuracies that will be most costly and the computational resources at hand.

## Regression loss functions

Regression problems, such as linear regression or polynomial regression, output continuous values by determining the relationship between one or more independent variables (*x*) and a dependent variable (*y*): *given x, predict the value of y*. Regression loss must, therefore, be sensitive to not just whether an output is incorrect, but the degree to which it diverges from the ground truth.

### Mean squared error (MSE)

The mean squared error loss function, also called L2 loss or quadratic loss, is generally the default for most regression algorithms. As its name suggests, MSE is calculated as the average of the squared differences between the predicted value and the true value across all training examples. The formula for calculating the MSE across n data points is written as 1n∑i=1n(yi-yi^)2, in which y<sub> </sub>is the true value and ŷ is the predicted value.

Squaring the error means that the resulting value is always positive: as such, MSE evaluates only the magnitude of error and not its direction. Squaring the error also gives large mistakes a disproportionately heavy impact on overall loss, which strongly punishes outliers and incentivizes the model to reduce them. MSE is thus suitable when the target outputs are assumed to have a normal (Gaussian) distribution.

MSE is always differentiable, making it practical for optimizing regression models through gradient descent.

### Mean squared logarithmic error (MSLE)

For regression problems where the target outputs have a very wide range of potential values, such as those involving exponential growth, heavy penalization of large errors might be counterproductive. Mean squared logarithmic error (MSLE) offsets this problem by averaging the squares of the natural logarithm of the differences between the predicted and average values. However, it's worth noting that MSLE assigns a greater penalty to predictions that are too low than to predictions that are too high.

The formula for MSLE is written as 1n∑i=1n(loge(1+yi)-loge(1+yi^))2

### Root mean squared error (RMSE)

Root mean squared error is the square root of the MSE, which makes it closely related to the formula for standard deviations. Specifically, RMSE is calculated as

$\sqrt{\frac{\sum_{i=1}^{n} (y_i - \hat{y}_i)^2}{n}}$ .

RMSE thus largely mirrors the qualities of MSE in terms of sensitivity to outliers but is easier to interpret because it expresses loss in the same units as the output value itself. This benefit is somewhat tempered by the fact that calculating RSME requires another step compared to calculating MSE, which increases computation costs.

### Mean absolute error (MAE)

*Mean absolute error* or *L1 loss*, measures the average *absolute difference* between the predicted value and actual value. Like MSE, MAE is always positive and doesn’t distinguish between estimates that are too high or too low. It’s calculated as the sum of the absolute value of all errors divided by the sample size: $\frac{1}{n}\sum_{i=1}^{n}|y_i - \hat{y}_i|$

Because it doesn’t square each loss value, MAE is more robust to outliers than MSE. MAE is thus ideal when the data might contain some extreme values that shouldn’t overly impact the model. L1 loss also penalizes small errors more than L2 loss.

The MAE loss function is not differentiable in cases where the predicted output matches the actual output. Therefore, MAE requires more workaround steps during optimization.

### Huber loss

Huber loss, also called *smooth L1 loss*, aims to balance the strengths of both MAE and MSE. It incorporates an adjustable hyperparameter, *δ*, that acts as a transition point: for loss values below or equal to *δ*, Huber loss is quadratic (such as MSE); for loss values greater than *δ*, Huber loss is linear (such as MAE).

$$ L_{\delta}=
    \left\{\begin{matrix}
        \frac{1}{2}(y - \hat{y})^{2} & if \left | (y - \hat{y})  \right | < \delta\\
        \delta (\left | (y - \hat{y})  \right | - \frac1 2 \delta) & otherwise
    \end{matrix}\right. $$

Huber loss thus offers a fully differentiable function with MAE’s robustness to outliers and MSE’s ease of optimization through gradient descent. The transition from quadratic to linear behavior at *δ* also results in an optimization less prone to problems such as vanishing or exploding gradients when compared to MSE loss.

These benefits are tempered by the need to carefully define *δ*, adding complexity to model development. Huber loss is most appropriate when neither MSE nor MAE can yield satisfactory results, such as when a model should be robust to outliers but still harshly penalize extreme values that are beyond some specific threshold.

## Classification loss functions

Classification problems, and the loss functions used to optimize models that solve them, are divided into *binary* classification—for example, “spam” or “not spam,” “approve” or “reject”—or *multi-class* classification.

Multi-class classification problems can be approached in two ways. One approach is to compute the relative probability of a data point belonging to each potential category, then select the category assigned the highest probability. This approach is typically employed by neural networks, using a *softmax* activation function for neurons in the output layer. The alternative approach is to divide the problem into a series of binary classification problems.

### Cross-entropy loss functions

In most cases, classification loss is calculated in terms of entropy. Entropy, in plain language, is a measure of uncertainty within a system. For an intuitive example, compare flipping coins to rolling dice: the former has lower entropy, as there are fewer potential outcomes in a coin flip (2) than in a dice toss (6).

In supervised learning, model predictions are compared to the ground truth classifications provided by data labels. Those ground truth labels are certain and thus have low or no entropy. As such, we can measure loss in terms of the difference in certainty we’d have using the ground truth labels to the certainty of the labels predicted by the model.

The formula for cross-entropy loss (CEL) is derived from that of Kullback-Leibler divergence (KL divergence), which measures the difference between two probability distributions. Ultimately, minimizing loss entails minimizing the difference between the ground truth distribution of probabilities assigned to each potential label and the relative probabilities for each label predicted by the model.

#### Binary cross-entropy (log loss)

Binary cross-entropy loss, also called log loss, is used for binary classification. Binary classification algorithms typically output a likelihood value between 0 and 1. For example, in an email spam detection model, email inputs that result in outputs closer to 1 might be labeled “spam.” Inputs yielding outputs closer to 0 would be classified as “not spam.” An output of 0.5 would indicate maximum uncertainty or entropy.

Though the algorithm will output values between 0 and 1, the ground truth values for the correct predictions are exactly “0” or “1.” Minimizing binary cross-entropy loss thus entails not only penalizing incorrect predictions but also penalizing predictions with low certainty. This incentivizes the model to learn parameters that yield predictions that are not only correct but also confident. Furthermore, focusing on the logarithms of predicted likelihood values results in the algorithm more heavily penalizing predictions that are confidently wrong.

To maintain the common convention of lower loss values meaning less error, the result is multiplied by -1. Log loss for a single example i is thus calculated as –(yi·log(p(yi))+(1-yi)·log(1-p(yi))), where y<sub>i</sub> is the true likelihood—either 0 or 1—and p(y<sub>i</sub>) is the predicted likelihood. Average loss across an entire set of n training examples is thus calculated as –1n∑i=1nyi·log(p(yi))+(1-yi)·log(1-p(yi)).

#### Categorical cross-entropy loss

Categorical cross-entropy loss (CCEL) applies this same principle to multi-class classification. A multi-class classification model will usually output a value for each potential class, representing the probability of an input belonging to each respective category. In other words, they output predictions as a *probability distribution*.

In deep learning, neural network classifiers typically use a *softmax* activation function for neurons in the output layer. Each output neuron’s value is mapped to a number between 0 and 1, with the values collectively summing up to 1.

For example, in a data point containing only one potential category, the ground truth values for each prediction thus comprise “1” for the true class and “0” for each incorrect class. Minimizing CCEL entails increasing the output value for the correct class *and* decreasing output values for incorrect classes, thereby bringing the probability distribution closer to that of the ground truth. For each example, log loss must be calculated for each potential classification predicted by the model.

### Hinge loss

Hinge loss is an alternative loss function for binary classification problems, and is particularly well suited to optimizing [support vector machine (SVM)](https://www.ibm.com/think/topics/support-vector-machine) models. Specifically, it’s an effective loss function for optimizing a decision boundary separating two classes: points can thereafter be classified according to which side of the decision boundary they fall on.

In algorithms using hinge loss, the ground truth value for each binary label is mapped to {-1, 1} rather than {0,1}. The hinge loss function *ℓ* is defined as **ℓ(𝑦)=max(0,1−𝑡⋅𝑦)**, wherein *t* is the true label and *y* is the output of the classifier. The outcome of this equation is always non-negative: if 1−𝑡⋅𝑦 is negative—which is only possible when *t* and *y* are the same sign because the model predicted the correct class—loss is instead defined as 0.

This provides various possibilities and incentives:

- When model predictions are correct and confident—that is, when *y* is the correct sign and |*y*| ≥ 1—the value of 1–*t*⋅𝑦 will be negative and therefore *ℓ* = 0.
- When model predictions are correct, but not confident—that is, when *y* is the correct sign but |*y*| < 1—the value of *ℓ* will be positive, between 0 and 1. This disincentivizes unconfident predictions.
- When model predictions are incorrect—that is, when *y* is the incorrect sign—the value of *ℓ* will be greater than 1 and increase linearly with the value of |*y*|. This strongly disincentivizes incorrect predictions.

## Specialized loss functions

Some model architectures, particularly those used in deep learning, ostensibly employ unique, specialized loss functions. Though such objective functions are unique in terms of their context and logic, they’re often—but not always—simply the specialized application of a common loss function to a specific training objective.

For example:

- [Autoencoders](https://www.ibm.com/think/topics/autoencoder) are unsupervised models that learn to efficiently encode a compressed representation of input data by squeezing said data through a “bottleneck,” then using that compressed representation to reconstruct the original input. Autoencoders learn by minimizing *reconstruction loss*: the difference between the original and reconstructed input, typically calculated through mean squared error (MSE). [Variational autoencoders](https://www.ibm.com/think/topics/variational-autoencoder) incorporate KL divergence as a regularization term.
- [Object detection](https://www.ibm.com/topics/object-detection) models minimize two kinds of loss: *bounding box regression* and cross-entropy loss. The former employs MSE, MAE or a specialized loss such as intersection over union (IoU) to compare the coordinates of the predicted bounding box to those of the ground truth. The latter measures the classification of the object itself.
- *Contrastive learning*, a form of self-supervised learning, trains a model to output similar [vector embeddings](https://www.ibm.com/think/topics/vector-embedding) for similar data points. It aims to reduce contrastive loss or specialized variants such as [triplet loss](https://research.ibm.com/publications/learning-thematic-similarity-metric-using-triplet-networks).
