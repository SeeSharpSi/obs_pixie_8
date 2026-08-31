---
title: What is underfitting?
source: https://www.ibm.com/think/topics/underfitting
author: null
published: 2024-11-21
created: 2026-08-31
description: "Underfitting is a scenario in data science where a data model is unable to capture the relationship between the input and output variables accurately"
---

## What is underfitting?

Underfitting is a scenario in data science where a data model is unable to capture the relationship between the input and output variables accurately, generating a high error rate on both the training set and unseen data.

Underfitting occurs when a model is too simple, which can be a result of a model needing more training time, more input features, or less [regularization](https://www.ibm.com/think/topics/regularization).

Like [overfitting](https://www.ibm.com/think/topics/overfitting), when a model is underfitted, it cannot establish the dominant trend within the data, resulting in training errors and poor performance of the model. If a model cannot generalize well to new data, then it cannot be leveraged for [classification](https://www.ibm.com/think/topics/classification-machine-learning) or [prediction](https://www.ibm.com/think/topics/predictive-analytics) tasks. Generalization of a model to new data is ultimately what allows us to use [machine learning algorithms](https://www.ibm.com/think/topics/machine-learning-algorithms) every day to make predictions and classify data.

High bias and low variance are good indicators of underfitting. Since this behavior can be seen while using the training dataset, underfitted models are usually easier to identify than overfitted ones.

## Underfitting versus overfitting

Put simply, [overfitting](https://www.ibm.com/think/topics/overfitting) is the opposite of underfitting, occurring when the model has been overtrained or when it contains too much complexity, resulting in high error rates on test data. Overfitting a model is more common than underfitting one, and underfitting typically occurs in an effort to avoid overfitting through a process called “early stopping.”

If undertraining or lack of complexity results in underfitting, then a logical prevention strategy would be to increase the duration of training or add more relevant inputs. However, if you train the model too much or add too many features to it, you may overfit your model, resulting in low bias but high variance (i.e. the bias-variance tradeoff). In this scenario, the statistical model fits too closely against its training data, rendering it unable to generalize well to new data points. It’s important to note that some types of models can be more prone to overfitting than others, such as [decision trees](https://www.ibm.com/think/topics/decision-trees) or [KNN](https://www.ibm.com/think/topics/knn).

Identifying overfitting can be more difficult than underfitting because unlike underfitting, the training data performs at high accuracy in an overfitted model. To assess the accuracy of an algorithm, a technique called k-fold cross-validation is typically used.

In k-folds cross-validation, data is split into k equally sized subsets, which are also called “folds.” One of the k-folds will act as the test set, also known as the holdout set or validation set, and the remaining folds will train the model. This process repeats until each of the fold has acted as a holdout fold. After each evaluation, a score is retained and when all iterations have completed, the scores are averaged to assess the performance of the overall model.

The ideal scenario when fitting a model is to find the balance between overfitting and underfitting. Identifying that “sweet spot” between the two allows machine learning models to make predictions with accuracy.

## How to avoid underfitting

Since we can detect underfitting based off of the training set, we can better assist at establishing the dominant relationship between the input and output variables at the onset. By maintaining adequate model complexity, we can avoid underfitting and make more accurate predictions. Below are a few techniques that can be used to reduce underfitting:

### Decrease regularization

Regularization is typically used to reduce the variance with a model by applying a penalty to the input parameters with the larger coefficients. There are a number of different methods, such as L1 regularization, [Lasso regularization](https://www.ibm.com/think/topics/lasso-regression), dropout, etc., which help to reduce the noise and outliers within a model. However, if the data features become too uniform, the model is unable to identify the dominant trend, leading to underfitting. By decreasing the amount of regularization, more complexity and variation is introduced into the model, allowing for successful training of the model.

### Increase the duration of training

As mentioned earlier, stopping training too soon can also result in underfit model. Therefore, by extending the duration of training, it can be avoided. However, it is important to cognizant of overtraining, and subsequently, overfitting. Finding the balance between the two scenarios will be key.

### Feature selection

With any model, specific features are used to determine a given outcome. If there are not enough predictive features present, then more features or features with greater importance, should be introduced. For example, in a [neural network](https://www.ibm.com/think/topics/neural-networks), you might add more hidden neurons or in a [random forest](https://www.ibm.com/think/topics/random-forest), you may add more trees. This process will inject more complexity into the model, yielding better training results.
