---
title: What is regularization?
source: https://www.ibm.com/think/topics/regularization
author:
- '[[Jacob  Murel Ph.D.]]'
- '[[Eda Kavlakoglu]]'
published: 2024-12-03
created: 2026-08-31
description: "Regularization is a set of methods that correct for multicollinearity and overfitting in predictive machine learning models"
---

## What is regularization?

Regularization is a set of methods for reducing overfitting in machine learning models. Typically, regularization trades a marginal decrease in training accuracy for an increase in generalizability.

Regularization encompasses a range of techniques to correct for [overfitting](https://www.ibm.com/topics/overfitting) in [machine learning](https://www.ibm.com/think/topics/machine-learning) models. As such, regularization is a method for increasing a model’s generalizability—that is, its ability to produce accurate predictions on new [datasets](https://www.ibm.com/think/topics/dataset).<sup>1</sup> Regularization provides this increased generalizability at the sake of increased training error. In other words, regularization methods typically lead to less accurate predictions on [training data](https://www.ibm.com/think/topics/training-data) but more accurate predictions on test data.

Regularization differs from optimization. Essentially, the former increases model generalizability while the latter increases model training accuracy. Both are important concepts in machine learning and data science.

There are many forms of regularization. Anything in the way of a complete guide requires a much longer book-length treatment. Nevertheless, this article provides an overview of the theory necessary to understand regularization’s purpose in machine learning as well as a survey of several popular regularization techniques.

### Bias-variance tradeoff

This concession of increased training error for decreased testing error is known as bias-variance tradeoff. Bias-variance tradeoff is a well-known problem in machine learning. It’s necessary to first define “bias” and “variance.” To put it briefly:

- **Bias** measures the average difference between predicted values and true values. As bias increases, a model predicts less accurately on a training dataset. High bias refers to high error in training.
- **Variance** measures the difference between predictions across various realizations of a given model. As variance increases, a model predicts less accurately on unseen data. High variance refers to high error during testing and validation.

Bias and variance thus inversely represent model accuracy on training and test sets respectively.<sup>2</sup> Obviously, developers aim to reduce both model bias and variance. Simultaneous reduction in both is not always possible, resulting in the need for regularization. Regularization decreases model variance at the cost of increased bias.

### Regression model fits

By increasing bias and decreasing variance, regularization resolves model overfitting. Overfitting occurs when error on training data decreases while error on testing data ceases decreasing or begins increasing.<sup>3</sup> In other words, overfitting describes models with low bias and high variance. However, if regularization introduces too much bias, then a model will underfit.

Despite its name, [underfitting](https://www.ibm.com/think/topics/underfitting) does not denote overfitting’s opposite. Rather underfitting describes models characterized by high bias and high variance. An underfitted model produces unsatisfactorily erroneous predictions during training and testing. This often results from insufficient training data or [parameters](https://www.ibm.com/think/topics/model-parameters).

Regularization, however, can potentially lead to model underfitting as well. If too much bias is introduced through regularization, model variance can cease to decrease and even increase. Regularization may have this effect particularly on simple models, that is, models with few parameters. In determining the type and degree of regularization to implement, then, one must consider a model’s complexity, dataset, and so forth.<sup>4</sup>

## Types of regularization with linear models

[Linear regression](https://www.ibm.com/think/topics/linear-regression) and [logistic regression](https://www.ibm.com/think/topics/logistic-regression) are both predictive models underpinning machine learning. Linear regression (or ordinary least squares) aims to measure and predict the impact of one or more predictors on a given output by finding the best fitting line through provided data points (that is, training data). Logistic regression aims to determine the class probabilities of by way of a binary output given a range of predictors. In other words, linear regression makes continuous quantitative predictions while logistic regression produces discrete categorical predictions.<sup>5</sup>

Of course, as the number of predictors increase in either regression model, the input-output relationship is not always straightforward and requires manipulation of the regression formula. Enter regularization. There are three main forms of regularization for regression models. Note that this list is only a brief survey. Application of these regularization techniques in either linear or logistic regression varies minutely.

- **Lasso regression** (or L1 regularization) is a regularization technique that penalizes high-value, correlated coefficients. It introduces a regularization term (also called, penalty term) into the model’s sum of squared errors (SSE) loss function. This penalty term is the absolute value of the sum of coefficients. Controlled in turn by the hyperparameter lambda (λ), it reduces select feature weights to zero. Lasso regression thereby removes [multicollinear features](https://www.ibm.com/think/topics/multicollinearity) from the model altogether.
- **Ridge regression** (or [L2 regularization](https://www.ibm.com/think/topics/ridge-regression)) is regularization technique that similarly penalizes high-value coefficients by introducing a penalty term in the SSE loss function. It differs from lasso regression however. First, the penalty term in ridge regression is the squared sum of coefficients rather than the absolute value of coefficients. Second, ridge regression does not enact feature selection. While lasso regression’s penalty term can remove features from the model by shrinking coefficient values to zero, ridge regression only shrinks feature weights toward zero but never to zero.
- **Elastic net regularization** essentially combines both ridge and lasso regression but inserting both the L1 and L2 penalty terms into the SSE loss function. L2 and L1 derive their penalty term value, respectively, by squaring or taking the absolute value of the sum of the feature weights. Elastic net inserts both of these penalty values into the cost function (SSE) equation. In this way, elastic net addresses multicollinearity while also enabling feature selection.<sup>6</sup>

In statistics, these methods are also dubbed “coefficient shrinkage,” as they shrink predictor coefficient values in the predictive model. In all three techniques, the strength of the penalty term is controlled by lambda, which can be calculated using various [cross-validation](https://www.ibm.com/docs/en/spss-modeler/18.0.0?topic=settings-cross-validation) techniques.

## Types of regularization in machine learning

### Dataset

**Data augmentation** is a regularization technique that modifies model training data. It expands the size of the training set by creating artificial data samples derived from pre-existing training data. Adding more samples to the training set, particularly of instances rare in real world data, exposes a model to a greater quantity and diversity of data from which it learns. Machine learning research has recently explored data augmentation for classifiers, particularly as a means of resolving imbalanced datasets.<sup>7</sup> Data augmentation differs from synthetic data however. The latter involves creating new, artificial data while the former produces modified duplicates of preexisting data to diversify and enlarge the dataset.

![Visualization of modification techniques for diversifying imagesets](https://assets.ibm.com/is/image/ibm/regularization-data-augmentation?ts=1763386861251&dpr=off)

### Model training

**Early stopping** is perhaps the most readily implemented regularization technique. In short, it limits the number of iterations during model training. Here, a model continuously passes through the training data, stopping once there is no improvement (and perhaps even deterioration) in training and validation accuracy. The goal is to train a model until it has reached the lowest possible training error preceding a plateau or increase in validation error.<sup>8</sup>

Many machine learning Python packages provide a training command options for early stopping. In fact, in some, early stopping is a default training setting.

![Graph visualization of early stopping in relation to training and validation accuracy](https://assets.ibm.com/is/image/ibm/regularization-diagrams-figure-3-model?ts=1763386861476&dpr=off)

### Neural networks

[Neural networks](https://www.ibm.com/think/topics/neural-networks) are complex machine learning models that drive many [artificial intelligence](https://www.ibm.com/think/topics/artificial-intelligence) applications and services. Neural networks are composed of an input layer, one or more hidden layers, and an output layer, each layer in turn comprised of several nodes.

**Dropout** regularizes neural networks by randomly dropping out nodes, along with their input and output connections, from the network during training (Fig. 3). Dropout trains several variations of a fixed-sized architecture, with each variation having different randomized nodes left out of the architecture. A single neural net without dropout is used for testing, employing an approximate averaging method derived from the randomly modified training architectures. In this way, dropout approximates training large a quantity of neural networks with a multitude of diversified architectures.<sup>9</sup>

![Diagram comparison of neural network and dropout network](https://assets.ibm.com/is/image/ibm/regularization-diagrams-figure-2-model-bg?ts=1763386861712&dpr=off)

**Weight decay** is another form of regularization used for deep neural networks. It reduces the sum of squared network weights by way of a regularization parameter, much like L2 regularization in linear models.<sup>10</sup> But when employed in neural networks, this reduction has an effect similar to L1 regularization: select neuron weights decrease to zero.<sup>11</sup> This effectively removes nodes from the network, reducing network complexity through sparsity.<sup>12</sup>

Weight decay may appear superficially similar to dropout in deep neural networks, but the two techniques differ. One primary difference is that, in dropout, the penalty value grows exponentially in the network’s depth in cases, whereas weight decay’s penalty value grows linearly. Some believe this allows dropout to more meaningfully penalize network complexity than weight decay.<sup>13</sup>

Many online articles and tutorials incorrectly conflate L2 regularization and weight decay. In fact, scholarship is inconsistent—some distinguish between L2 and weight decay,<sup>14</sup> some equate them,<sup>15</sup> while others are inconsistent in describing the relationship between them.<sup>16</sup> Resolving such inconsistencies in terminology is a needed yet overlooked area for future scholarship.

## Footnotes

[[1]](https://www.researchgate.net/publication/301846616_Fundamental_differences_between_Dropout_and_Weight_Decay_in_Deep_Networks) [Deep Learning](https://www.deeplearningbook.org/), Goodfellow et al., The MIT Press, 2016

[[2]](https://www.clearscope.io/ibm1/reports/1deb555ed852b24b/editor#_ednref2) *An Introduction to Statistical Learning, G. James et al.,* Springer, 2013

[[3]](https://www.clearscope.io/ibm1/reports/1deb555ed852b24b/editor#_ednref3) [Deep Learning](https://www.deeplearningbook.org/), Goodfellow et al.

[[4]](https://www.clearscope.io/ibm1/reports/1deb555ed852b24b/editor#_ednref4) Vandenbussche, Vincent, [Regularization cookbook](https://github.com/PacktPublishing/The-Regularization-Cookbook), Packt Publishing, 2023

[[5]](https://www.clearscope.io/ibm1/reports/1deb555ed852b24b/editor#_ednref5) *An Introduction to Statistical Learning, G. James et al.*

[[6]](https://www.clearscope.io/ibm1/reports/1deb555ed852b24b/editor#_ednref6) *Applied Predictive Modeling*, Kuhn, Max and Johnson, Kjell, Springer, 2016. Also, *Regression: Models, Methods and Applications*, Fahrmeir, Ludwig, et al. 2nd edition, Springer, 2021

[[7]](https://www.clearscope.io/ibm1/reports/1deb555ed852b24b/editor#_ednref7) “[Simple Copy-Paste Is a Strong Data Augmentation Method for Instance Segmentation](https://openaccess.thecvf.com/content/CVPR2021/papers/Ghiasi_Simple_Copy-Paste_Is_a_Strong_Data_Augmentation_Method_for_Instance_CVPR_2021_paper.pdf),” Ghiasi et al., CVPR, 2021

[[8]](https://www.clearscope.io/ibm1/reports/1deb555ed852b24b/editor#_ednref8) *Neural Networks: Tricks of the Trade*, Montavon, et al. 2nd Ed. 2012

[[9]](https://www.clearscope.io/ibm1/reports/1deb555ed852b24b/editor#_ednref9) “[Dropout: A Simple Way to Prevent Neural Networks from Overfitting](https://jmlr.org/papers/v15/srivastava14a.html),” JMLR, Srivastava et al., 2014

[[10]](https://www.clearscope.io/ibm1/reports/1deb555ed852b24b/editor#_ednref10) *Applied Predictive Modeling*, Kuhn, Max and Johnson, Kjell, Springer, 2016.

[[11]](https://www.clearscope.io/ibm1/reports/1deb555ed852b24b/editor#_ednref11) “[Deep Learning Meets Sparse Regularization: A Signal Processing Perspective](https://arxiv.org/abs/2301.09554),” arXiv, Jan. 2023

[[12]](https://www.clearscope.io/ibm1/reports/1deb555ed852b24b/editor#_ednref12) “[Comparing Biases for Minimal Network Construction with Back-propagation](https://proceedings.neurips.cc/paper/1988/file/1c9ac0159c94d8d0cbedc973445af2da-Paper.pdf),” Proceedings, Hanson and Pratt, 1988

[[13]](https://www.clearscope.io/ibm1/reports/1deb555ed852b24b/editor#_ednref13) “[Surprising properties of dropout in deep networks](https://jmlr.org/papers/v18/16-549.html),” Helmbold, David and Long, Philip, JMLR, 2018

[[14]](https://www.clearscope.io/ibm1/reports/1deb555ed852b24b/editor#_ednref14) “[Three Mechanisms of Weight Decay Regularization](https://arxiv.org/abs/1810.12281),” Zhang, Guodong, Wang, Chaoqi, Xu, Bowen, Roger, Grosse, arXiv, 2018

[[15]](https://www.clearscope.io/ibm1/reports/1deb555ed852b24b/editor#_ednref15) “[Fundamental differences between Dropout and Weight Decay in Deep Networks](https://www.researchgate.net/publication/301846616_Fundamental_differences_between_Dropout_and_Weight_Decay_in_Deep_Networks),” Helmbold, David and Long, Philip, ResearchGate, 2016

[[16]](https://www.clearscope.io/ibm1/reports/1deb555ed852b24b/editor#_ednref16) [Deep Learning](https://www.deeplearningbook.org/), Goodfellow et al.
