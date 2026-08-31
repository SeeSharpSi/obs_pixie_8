---
title: What is lasso regression?
source: https://www.ibm.com/think/topics/lasso-regression#1190488335
author:
- '[[IBM]]'
published: null
created: 2026-05-21
description: Lasso regression is a regularization technique that applies a penalty
  to prevent overfitting and enhance the accuracy of statistical models.
---
Lasso regression is a regularization technique that applies a penalty to prevent [overfitting](https://www.ibm.com/think/topics/overfitting) and enhance the accuracy of statistical models.

Lasso regression—also known as L1 regularization—is a form of regularization for [linear regression](https://www.ibm.com/topics/linear-regression) models. [Regularization](https://www.ibm.com/think/topics/regularization) is a statistical method to reduce errors caused by overfitting on training data. This approach can be reflected with this formula:

w-hat = argmin <sub>w</sub> MSE(W ) + ||w|| <sub>1</sub>

The concepts behind the Lasso technique can be traced to a 1986 [geophysics research paper](https://epubs.siam.org/doi/10.1137/0907087) (link resides outside ibm.com) by Santosa and Symes [^1], which used the L1 penalty for coefficients. However, in 1996, statistician, Robert Tibshirani, [independently developed and popularized the term](https://webdoc.agsci.colostate.edu/koontz/arec-econ535/papers/Tibshirani%20\(JRSS-B%201996\).pdf) [^2] (link resides outside ibm.com), “lasso”, based on [Breiman’s nonnegative garrote work](https://www.tandfonline.com/doi/abs/10.1080/00401706.1995.10484371) [^3] (link resides outside ibm.com).

Lasso stands for Least Absolute Shrinkage and Selection Operator. It is frequently used in machine learning to handle high dimensional data as it facilitates automatic feature selection with its application. It does this by adding a penalty term to the residual sum of squares (RSS), which is then multiplied by the regularization parameter (lambda or λ). This regularization parameter controls the amount of regularization applied. Larger values of lambda increase the penalty, shrinking more of the coefficients towards zero; this subsequently reduces the importance of (or altogether eliminates) some of the features from the model, resulting in automatic feature selection. Conversely, smaller values of lambda reduce the effect of the penalty, retaining more features within the model.

This penalty promotes sparsity within the model, which can help avoid issues of [multicollinearity](https://www.ibm.com/think/topics/multicollinearity) and [overfitting](https://www.ibm.com/think/topics/overfitting) issues within datasets. Multicollinearity occurs when two or more independent variables are highly correlated with one another, which can be problematic for causal modeling. Overfit models will generalize poorly to new data, diminishing their value altogether. By reducing regression coefficients to zero, lasso regression can effectively eliminate independent variables from the model, sidestepping these potential issues within modeling process. Model sparsity can also improve the interpretability of the model compared to other regularization techniques such as [ridge regression](https://www.ibm.com/think/topics/ridge-regression) (also known as L2 regularization).

As a note, this article focuses on regularization of linear regression models, but it’s worth noting that lasso regression may also be applied in [logistic regression](https://www.ibm.com/think/topics/logistic-regression).

### Bias-variance tradeoff

Bias-variance tradeoff is a well-known property of predictive models. In this context, bias measures the average difference between predicted values and true values; variance measures the difference between predictions across various realizations of a given model. As bias increases, a model predicts less accurately on a training dataset. As variance increases, a model predicts less accurately on other datasets. Bias and variance thus measure model accuracy on training and test sets respectively. Simultaneously reducing both bias and variance is not always feasible–hence the need for regularization techniques, such as lasso regression.

In lasso regression, the hyperparameter lambda (λ), also known as the L1 penalty, balances the tradeoff between bias and variance in the resulting coefficients. As λ increases, the bias increases, and the variance decreases, leading to a simpler model with fewer parameters. Conversely, as λ decreases, the variance increases, leading to a more complex model with more parameters. If λ is zero, then one is left with an OLS function–that is, a standard linear regression model without any regularization.

![Graph modeling relation between MSE, vias, variance, and lambda penalty term](https://assets.ibm.com/is/image/ibm/skill-up-ridge-regression-figure-2:16x9?fmt=png-alpha&dpr=on%2C2.2222222222222223&wid=1584&hei=891)

## How does lasso regression work?

This section summarizes how to apply lasso regression and highlights common use cases within data science.

### Conduct an exploratory data analysis

Before applying a linear regression algorithm to your dataset, explore the data to understand potential underlying issues that may exist. It’s important to understand if:

- there any missing data
- there is a high number of features
- the distribution of the continuous variables centered at the mean with equivalent standard deviations
- any of the predictors correlate to one another

These are important to understand as datasets with high dimensionality and correlated variables can be prone to overfitting. Data that is not centered at the mean with a standard deviation of 1 will also need rescaling to limit the impact of large scales on the model. If features are not rescaled, this can adversely affect the cost function, which in turn impacts the beta coefficients. Put simply, unscaled features can result in the application of unintentional penalties in lasso regression due to differences in units.

### Split the data and rescale continuous predictors

Once we’ve conducted an exploratory data analysis, we’ll split the data into a training set and test set. After splitting the data, rescaling is applied to the data as needed. Z-score scaling is a common feature scaling approach, which rescales features to share a standard deviation of 1 and a mean of 0.

### Fit the lasso model and choose a value for λ

Fit the lasso regression model on the training data and choose a value for λ with the objective of minimizing the mean squared error (MSE). The mean square error (MSE) can help determine a suitable λ value. MSE is a means of measuring the difference, on average, between predicted and true values of the dependent variable. Lasso regression minimizes the mean squared error (MSE) while balancing the opposing factors of bias and variance to build the most accurate predictive model. It achieves this by adding a penalty term to the residual sum of squares (RSS) equal to the sum of the absolute values of the coefficients multiplied by a parameter λ.

![Graph showing the optimal MSE ](https://assets.ibm.com/is/image/ibm/4-1_model-complexity-bias-variance:16x9?fmt=png-alpha&dpr=on%2C2.2222222222222223&wid=1584&hei=891)

### Optimize for λ with cross-validation

The optimal value of λ can be determined with [cross-validation](https://www.ibm.com/docs/en/spss-modeler/18.0.0?topic=settings-cross-validation) techniques, such as k-fold cross-validation; this approach finds the λ value that minimizes the mean squared error or other performance metrics.

As noted previously, a higher λ value applies more regularization. As λ increases, model bias increases while variance decreases. This is because as λ becomes larger, more coefficients 𝛽 shrink to zero.

### Evaluate the performance of your model

Generally, we might print out a few values to understand model performance, specifically R <sup>2</sup> and MSE. R <sup>2</sup> tells us the proportion of variance in our dependent variable (or response variable) which is explained by independent variables. By comparing MSE values for different values of λ, you will see if the model has been effectively optimized for the global minimum.

## When to use lasso regression

Lasso regression is ideal for predictive problems; its ability to perform automatic variable selection can simplify models and enhance prediction accuracy. That said, ridge regression may outperform lasso regression due to the amount of bias that lasso regression introduces by reducing coefficients towards zero. It also has its limitations with correlated features in the data as it arbitrarily chooses a feature to include in the model.

### Common applications

Lasso regression may be ideal in these scenarios.

Handling high-dimensional datasets

A dataset is considered high-dimensional when the number of predictor variables is much larger than the number of observations. Lasso regression can help to reduce dimensionality within a dataset by shrinking the weight parameters to zero, eliminating less important features from the model.

[

Learn more about dimensionality reduction

](https://www.ibm.com/think/topics/dimensionality-reduction)

Automating feature selection

The bias introduced by the L1 penalty will artificially shrink the coefficients towards zero. Some variables will shrink exactly to zero, leaving the model with a subset of the most important variables to make predictions.

### Limitations of lasso regression

Lasso regression can handle some multicollinearity without negatively impacting interpretability of the model, but it cannot overcome severe multicollinearity [^4]. If covariates are highly correlated, lasso regression will arbitrarily drop one of the features from the model. Elastic net regularization is a good alternative in this situation.

## Implementing lasso regression in Python or R

Both Python and R are widely used in data science. Python is flexible and can handle a broad spectrum of tasks. On the other hand, R is specifically designed for statistical computing and data visualization, including rich graphic options for plots and charts.

Lasso regression can be implemented in Python using libraries like [sklearn](https://scikit-learn.org/stable/index.html) (link resides outside ibm.com) which provides the Lasso class for this purpose. R is a great choice as the glmnet package can be utilized for efficient cross-validation for λ Selection and provides the flexibility to set α to different values. R also shines with its visualization capabilities, which play a crucial role in understanding and interpreting the Lasso regression model.

Link copied

[IBM X-Force Threat Intelligence Index 2026](https://www.ibm.com/reports/threat-intelligence)

[

Gain insights to prepare and respond to cyberattacks with greater speed and effectiveness with the IBM X-Force® Threat Intelligence Index.

](https://www.ibm.com/reports/threat-intelligence)

[^1]: [Linear Inversion of Band-Limited Reflection Seismograms](https://epubs.siam.org/doi/10.1137/0907087) (external link to ibm.com), Society for Industrial and Applied Mathematics, 1986

[^2]: [Regression Shrinkage and Selection via the Lasso](https://webdoc.agsci.colostate.edu/koontz/arec-econ535/papers/Tibshirani%20\(JRSS-B%201996\).pdf) (external link to ibm.com), Journal of the Royal Statistical Society, 1996

[^3]: [Better Subset Regression Using the Nonnegative Garrote](https://www.tandfonline.com/doi/abs/10.1080/00401706.1995.10484371) (external link to ibm.com), Technometrics, 2012

[^4]: [Regularized Multiple Regression Methods to Deal with Severe Multicollinearity](https://www.researchgate.net/publication/332934338_Regularized_Multiple_Regression_Methods_to_Deal_with_Severe_Multicollinearity) (external link to ibm.com), International Journal of Statistics and Applications, 2018