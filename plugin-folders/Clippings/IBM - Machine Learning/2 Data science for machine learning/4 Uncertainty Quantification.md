---
title: What is uncertainty quantification in machine learning?
source: https://www.ibm.com/think/topics/uncertainty-quantification
author:
- '[[Joshua Noble]]'
published: 2025-06-10
created: 2026-05-21
description: "Model uncertainty helps us estimate not only how accurate a model is over time but also can help show the range of possible results. It also helps understand how to reduce the uncertainty both in measurement and in models."
---

## What is uncertainty quantification?

The statistician George Box wrote: “All models are wrong, but some are useful”.<sup>1</sup> Models, whether of qualitative, artificial intelligence, dynamic mathematical or statistical, always fall short of the complexities of reality.

There are multiple types of uncertainty that affect models of all kinds. Sources of uncertainty include random process or stochastic characteristics in a system (referred to as aleatoric uncertainty) incomplete knowledge (referred to as epistemic uncertainty), or computational limitations.

Model uncertainty helps us estimate not only how accurate a model is over time but also can help show the range of possible results. It also helps understand how to reduce the uncertainty both in measurement and in models.

Uncertainty and accuracy are different concepts that are closely related to one another. Prediction accuracy is how close a prediction is to a known value. Uncertainty is how much predictions and target values can vary.

A computer vision system that classifies only images of apples into red or green has much less inherent uncertainty than a system that classifies photos of every kind of fruit known in the world. Uncertainty quantification (UQ) is a way to measure exactly how much more uncertain those two problems are from one another.

When a model contains uncertainties, its outputs can vary with different probabilities. We treat these outputs as random variables and use probability distributions to measure uncertainty. The wider the distribution, the more uncertain the result. While variance works well for Gaussian distributions, many real-world systems create nonstandard distributions that require different measurement approaches.

Uncertainty quantification methods help tell you how confident you should be in any particular prediction. That can be a prediction made by a statistical technique like a test of distributions or it can be a prediction or inference made by a [machine learning](https://www.ibm.com/think/topics/machine-learning) algorithm. UQ also helps us understand the range of possible outcomes for models.

For example, if a weather model predicts a 70% chance of rain, UQ helps determine whether that 70% is based on solid training data or if there's so much uncertainty that the actual chance might be anywhere from 50% to 90%.

UQ methods are important because it shows how errors and unknowns affect final results. This prevents models from becoming overconfident and helps focus on how to improve the accuracy of a machine learning model.

Calculating UQ helps to identify which uncertainties matter most and aids in the optimization of model training. UQ also helps decision-makers understand the reliability of predictions. UQ helps you to turn a statement like "this model might be wrong" into specific, measurable information about how wrong it might be and in what ways it might be wrong. This is invaluable when working in fields like medicine, fault-intolerant engineering or other scenarios where reliability is paramount.

## Methods for UQ

Uncertainty comes in two primary types: data-driven uncertainty and model-driven uncertainty. In either case, it can be helpful to know how reliable a prediction is both before it's made and after it's made.

You can think of this as a model predicting how many times a door hinge can open and close before it fails to approximately plus or minus 1000 operation. It can also show how likely it is that this time closing the door hinge breaks it.

## Sampling-based methods

Sampling-based approaches are some of the most commonly used techniques for uncertainty quantification because they can handle any kind of model complexity and provides an intuitive comprehensive uncertainty characterization. By generating many possible scenarios, sampling can build up a statistical picture of what outcomes are likely and how uncertain our predictions are when applied to real-world data. Instead of computing uncertainty analytically, these methods use statistical analysis of many sample outputs to characterize uncertainty distributions.

Monte Carlo simulation is one of the most common approaches. This runs thousands of model simulations with randomly varied inputs to see the range of possible outputs. These are especially common with parametric models where the confidence intervals and model outputs for different models are compared to see the range of all possible values.

A variation of Monte Carlo simulation called Latin hypercube sampling is a more efficient version that requires fewer runs while still covering the input space well.

Monte Carlo dropout is another technique that keeps the dropout active during prediction, running multiple forward passes to get a distribution of outputs.<sup>2</sup> Dropout is primarily used as a regularization technique, a method employed to fine-tune machine learning models. It aims to optimize the adjusted loss function while avoiding the issues of overfitting or underfitting.

Monte Carlo Dropout applies dropout at test time and runs multiple forward passes with different dropout masks. This has the model produce a distribution of predictions rather than a single point estimate. The distribution provides insights into the model uncertainty about predictions. It's a computationally efficient technique to get neural networks to output distributions without requiring the networks to be trained multiple times.

When running the actual model many times is too expensive, statisticians create simplified "surrogate" models by using techniques like Gaussian process regression (GPR).<sup>5</sup> GPR is a Bayesian approach for modeling certainty in predictions that makes it a valuable tool for optimization, [time series](https://www.ibm.com/think/insights/time-series-forecasting) forecasting and other applications. GPR is based on the concept of a 'Gaussian process', which is a collection of random variables that have a joint Gaussian distribution.

You can think of a Gaussian process as a distribution of functions. GPR places a prior distribution over functions and then uses observed data to create a posterior distribution. Using GPR to calculate uncertainty doesn’t require extra training or model runs because the output inherently expresses how certain or uncertain the model is about the estimate through the distribution. Libraries like [Scikit-learn](https://scikit-learn.org/stable/modules/gaussian_process.html) provide implementations of GPR for uncertainty analysis.

The choice of sampling method depends on what features matter most for your model and scenario. Most real-world applications combine multiple approaches.

## Bayesian methods

Bayesian statistics is an approach to statistical inference that using Bayes' theorem to combine prior beliefs with observed data and update the probability of a hypothesis. Bayesian statistics explicitly deals with uncertainty by assigning a probability distribution rather than a single fixed value. Instead of giving a single 'best' estimate for a [model parameter](https://www.ibm.com/think/topics/model-parameters), Bayesian methods provide a distribution of the likelihood of possible estimates.

Bayesian inference updates predictions as new data becomes available, which naturally incorporates uncertainty throughout the process of estimating covariates. Markov chain Monte Carlo (MCMC) methods help implement Bayesian approaches when mathematical solutions are complex. The MCMC approach samples from complex, high-dimensional probability distributions that cannot be sampled directly, particularly posterior distributions in Bayesian inference.

Bayesian neural networks (BNNs) are a departure from traditional neural networks that treat network weights as probability distributions rather than fixed-point estimates. This probabilistic approach enables principled and rigorous uncertainty quantification. Instead of single point estimates for weights, these maintain probability distributions over all network parameters. Predictions typically include

- mean and variance estimates for the predictive distribution
- samples from the predictive distribution
- credible intervals derived from the distribution

Several popular open source libraries exist for implementing BNNs like [PyMC](https://www.pymc.io/welcome.html) and [Tensorflow-Probability](https://www.tensorflow.org/probability).

## Ensemble methods

The core idea behind ensemble-based uncertainty quantification is that if multiple independently trained models disagree on a prediction, this disagreement indicates uncertainty about the correct answer.<sup>4</sup> Conversely, when all models in the ensemble agree, this suggests higher confidence in the prediction. This intuition translates into concrete uncertainty measures through the variance or spread of ensemble predictions.

If f₁, f₂, ..., fₙ represent the estimators of N ensemble members for input x, the uncertainty can be quantified as

$$ Var[f(x)] = \frac{1}{N}\sum_{i=1}^{N}(f_i(x) - \bar{f}(x))^2 $$

where f̄(x) is the ensemble mean. Training multiple diverse models (different architectures, training data subsets or initialization) and combining their predictions. The main drawback of this approach is the computational cost: it requires training and running multiple models.

## Conformal prediction

Conformal prediction is a technique for uncertainty quantification. It provides a distribution-free, model-agnostic framework for creating prediction intervals (for regression scenarios) or prediction sets (for classification applications).<sup>3</sup> This provides valid coverage guarantees with minimal assumptions about the model or data. This makes conformal prediction particularly helpful when working with black-box pretrained models.

Conformal prediction has several features that make it widely applicable. For instance, it requires only that data points are exchangeable, rather than requiring that they be independent and identically distributed. Conformal prediction can also be applied to any predictive model and allows you to set the allowable predictive uncertainty of a model.

For instance, in a regression task, you might want to achieve 95% coverage, which would mean that the model should output a range where the true falls into the output interval 95% of the time. This approach is model independent and works well with classification, linear regression, neural networks and a wide variety of time series models.

To use conformal prediction, you split your data into three sets: a training set, a baseline testing set and a calibration set. The calibration set is used to compute the nonconformity scores, often denoted as *s<sub>i</sub>*. This score measures how unusual a prediction is. Given a new input, form a prediction interval based on these scores to guarantee coverage.

In a classification task, conformal prediction the nonconformity score is a measure of how much a new instance deviates from the existing instances in the training set. This determines whether a new instance belongs to a particular class or not. For multiclass classification, this is typically 1—predicted class probability for the particular label.

$$ s_i = 1 - f(x_i)[y_i] $$

So, if the predicted probability of a new instance belonging to a certain class is high, the nonconformity score is low, and vice versa. A common approach is to compute the *s<sub>i</sub>* scores for each instance in the calibration set and sort the scores from low (certain) to high (uncertain).

To get to 95% conformal coverage, compute the threshold q where 95% of the s<sub>i</sub> scores are lower. For new test examples, you include a label in the prediction set if its s<sub>i</sub> is less than the threshold q.

If you required a guarantee that your model had 95% conformal coverage, you would obtain average *s<sub>i</sub>* scores for all classes. Then, you would find a threshold of *s<sub>i</sub>* scores that contain 95% of the data. You can then be assured that your classifier correctly identifies 95% of new instances across all classes.

This is slightly different than the accuracy of the classifier because conformal prediction might identify multiple classes. In a multiclass classifier, conformal prediction also shows the coverage for all classes. You can assign a coverage rate for individual classes rather than for the entire training set.

## Applications of uncertainty quantification

Uncertainty quantification is important across many fields in machine learning, artificial intelligence development and computer science. Here are just a few of the most common applications.

## Uncertainty in time series forecasting

Managing and quantifying uncertainty in time series forecasting is crucial for decision-making processes across finance, economics, weather forecasting and supply chain management. Probabilistic models are favored for their capacity to output distributions instead of single points estimates. These models can be contrasted with deterministic models, which output only a single value rather than a distribution of possible values. Numerous probabilistic models exist for time series forecasting, for instance, ARIMA models or Bayesian neural networks.

Fitting an [ARIMA](https://www.ibm.com/think/topics/arima-model) model begins with capturing the autoregressive (AR) and moving average (MA) components and ensuring stationarity through differencing. After generating point forecasts the model assesses the residuals, which represent the differences between the observed and predicted values. ARIMA uses the standard deviation of the normally distributed residuals to construct prediction intervals around the point forecasts.

Essentially, the wider the prediction interval, the greater the uncertainty associated with the forecast. This technical methodology not only refines the accuracy of point forecasts but also provides a statistically sound measure of the range within which future observations are likely to fall.

## Deep learning and uncertainty

[Deep learning](https://www.ibm.com/think/topics/deep-learning) presents multiple challenges for uncertainty quantification because deep learning models often have such high dimensionality and nonlinear relationships across the layers of the network. There are also often significant computational constraints both in training and deploying these models, which makes quantifying the amount of uncertainty present in any inference difficult.

Several commonly used techniques have been developed specifically for deep [neural networks](https://www.ibm.com/think/topics/neural-networks). For instance, sampling-based methods like deep ensembles where multiple independently trained networks have different initializations or data subsets. The variance across ensemble predictions can indicate uncertainty in the prediction of the architecture itself. This is a simple but computationally expensive technique as it requires training multiple full models.

Another commonly used technique is Monte Carlo dropout, which keeps dropout layers active during inference.<sup>6</sup> This approach performs multiple forward passes to approximate Bayesian inference. Each dropout mask creates a different subnetwork, and the prediction variance estimates uncertainty. This is easy to implement with existing models because no changes are required in the model architecture. Instead of turning off dropout during inference, you would keep it enabled and run multiple forward passes. A similar approach is batch normalization uncertainty which randomly sample from the learned batch statistics at inference time to create prediction distributions.

## Active learning

Active learning is a scalable machine learning paradigm where the algorithm can selectively choose which data points to learn from, rather than being trained on a fixed dataset. A learning algorithm can achieve better performance with fewer labeled examples if it's allowed to choose the data it learns from. Traditional supervised learning assumes that a large labeled dataset is available from the start of the model development process. In many real-world scenarios, unlabeled data is abundant while labeled data is expensive, time-consuming, or requires expert knowledge to obtain. After training a model using the smaller labeled set, you would use the model to evaluate a large pool of unlabeled examples. Active learning select the most "informative" unlabeled examples according to some acquisition strategy.

Active learning strategies can use estimates of uncertainty quantification to identify which unlabeled examples would be most valuable to label next. The basic premise is that the model should request labels for data points where it is most uncertain, as these examples are likely to provide the greatest information gain.

## Metrics for UQ

Metrics for uncertainty quantification are often used to compare different models that use the same architecture rather than for comparing different architectures or as an absolute value. Some types of measures, like expected calibration error, do allow you to measure the calibration of a specific model.

If you're not measuring the calibration of the model to the test data though, you might use multiple complementary metrics rather than relying on a single measure, as different metrics capture different aspects of uncertainty.

Generally, metrics for uncertainty fall into two broad categories, [proper scoring rules](#psr) and c[alibration metrics](#cm).

## Proper scoring rules

Proper scoring rules work best with probabilistic models with natural uncertainty estimates because they estimate the deviation from the true probability distribution. A high value indicates that the predicted probability is far away from the true probability. This provides a metric to evaluate a probabilistic forecast or prediction, which is often a range of possible outputs rather than a single value.

Typical loss functions like mean squared error assign a goodness-of-fit score to a predicted value and an observed value. However, scoring rules assign a score to a predicted probability distribution and an observed value.

Negative log likelihood (NLL) is a commonly used method for optimizing neural networks for classification tasks. However, this loss function can also be used as an uncertainty metric. As NLL directly measures how well a model's predicted probability distributions align with observed outcomes, it inherently captures both the accuracy and confidence quality of probabilistic predictions.

In the case of a classification model that predicts [0.9, 0.1] for a binary problem where the true class distribution is 60–40, that model has a higher NLL on average. This is because NLL heavily penalizes the overconfident second model when its confident predictions are wrong.

Brier score is another proper scoring rule typically used for classification tasks. It is sometimes preferred over NLL because it is strictly bounded within a range of 0–1 and so is more numerically stable. It's a comprehensive uncertainty metric because it evaluates both how well predicted probabilities match observed frequencies and how confident the predictions are.

Continuous Ranked Probability Score (CRPS) is a metric widely used in fields like meteorology, hydrology and climate science. CRPS measures the discrepancy between the predicted cumulative distribution function (CDF) of a forecast and a step function representing the true outcome. CRPS quantifies the spread of the forecast distribution around the observed value.

## Calibration metrics

Calibration metrics work best with pretrained models like foundation models or large language models (LLMs) or with classification tasks that use a softmax output. They help measure the difference between “true confidence” and “predicted confidence”. Where a proper scoring rule compares distributions, calibration compares the certainty itself. If the calibration metric is calculated to be 0.6 then it should mean that the neural network is 60% certain in a particular prediction.<sup>7</sup>

A model is considered calibrated when its predicted confidence scores accurately reflect the true likelihood of correctness. More formally, calibration means that among all predictions where the model expresses confidence p, approximately p fraction should be correct. Calibration metrics are computed on the whole dataset in order to group different probabilities. In contrast, proper scoring rules compare individual probabilities.<sup>8</sup>

Expected Calibration Error (ECE) is one of the most widely used metrics. It partitions predictions into bins based on confidence levels and measures the average difference between confidence and accuracy within each bin. A typical approach uses 10–15 equally spaced bins, which are used to calculate the mean of predicted probabilities in that bin and the fraction of predictions that were actually correct in that bin.

A perfectly calibrated model should be correct 90% of the time when it's 90% confident. ECE measures this by returning a value from 0 (perfect calibration) to 1 (worst possible calibration). The metric treats overconfidence and underconfidence equally due to the absolute value of the metric. It's most helpful for comparing models to one another as opposed to applying a metric to a specific model in isolation.

Maximum Calibration Error (MCE) measures the worst-case calibration error by taking the maximum difference between confidence and accuracy across all bins, rather than the average. This provides insight into the most poorly calibrated regions.

Adaptive Calibration Error (ACE) addresses limitations of fixed binning by using adaptive binning strategies that ensure each bin contains roughly the same number of samples, providing more robust estimates especially with limited data.

## Footnotes

1. Box, G. E. P. (1976). Science and statistics. Journal of the American Statistical Association, 71(356), 791–799. [https://doi.org/10.1080/01621459.1976.10480949](https://www.tandfonline.com/doi/abs/10.1080/01621459.1976.10480949)

2. Gal, Y., Ghahramani, Z., & University of Cambridge. (2016). Dropout as a Bayesian approximation: representing model uncertainty in deep learning. In Proceedings of the 33rd International Conference on Machine Learning.

3. Angelopoulos, A. N., & Bates, S. (2021, July 15). A gentle introduction to conformal prediction and Distribution-Free uncertainty quantification. arXiv.org. [https://arxiv.org/abs/2107.07511](https://arxiv.org/abs/2107.07511)

4. Lakshminarayanan, B., Pritzel, A., & Blundell, C. (2016, December 5). Simple and Scalable Predictive Uncertainty Estimation using Deep Ensembles. arXiv.org. [https://arxiv.org/abs/1612.01474](https://arxiv.org/abs/1612.01474)

5. Williams, C. K. I., Neural Computing Research Group, Rasmussen, C. E., Department of Computer Science, & University of Toronto. (1996). Gaussian processes for regression. [https://proceedings.neurips.cc/paper_files/paper/1995/file/7cce53cf90577442771720a370c3c723-Paper.pdf](https://proceedings.neurips.cc/paper_files/paper/1995/file/7cce53cf90577442771720a370c3c723-Paper.pdf)

6. Wang, C. (2023, August 2). Calibration in Deep Learning: A Survey of the State-of-the-Art. arXiv.org. [https://arxiv.org/abs/2308.01222](https://arxiv.org/abs/2308.01222)

7. Guo, C., Pleiss, G., Sun, Y., & Weinberger, K. Q. (2017). On calibration of modern neural networks. International Conference on Machine Learning, 1321–1330. [https://proceedings.mlr.press/v70/guo17a/guo17a.pdf](https://proceedings.mlr.press/v70/guo17a/guo17a.pdf)

8. Nixon, J., Dusenberry, M. W., Zhang, L., Jerfel, G., & Tran, D. (2019). Measuring calibration in deep learning. Computer Vision and Pattern Recognition, 38–41. [https://openaccess.thecvf.com/content_CVPRW_2019/papers/Uncertainty and Robustness in Deep Visual Learning/Nixon_Measuring_Calibration_in_Deep_Learning_CVPRW_2019_paper.pdf](https://openaccess.thecvf.com/content_CVPRW_2019/papers/Uncertainty%20and%20Robustness%20in%20Deep%20Visual%20Learning/Nixon_Measuring_Calibration_in_Deep_Learning_CVPRW_2019_paper.pdf)
