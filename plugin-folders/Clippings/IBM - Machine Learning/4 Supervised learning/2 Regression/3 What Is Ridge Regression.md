---
title: What is ridge regression?
source: https://www.ibm.com/think/topics/ridge-regression
author:
- '[[Jacob  Murel Ph.D.]]'
- '[[Eda Kavlakoglu]]'
published: 2024-12-06
created: 2026-08-31
description: "Ridge regression is a statistical regularization technique. It corrects for overfitting on training data in machine learning models."
---

## What is ridge regression?

Ridge regression is a statistical regularization technique. It corrects for [overfitting](https://www.ibm.com/think/topics/overfitting) on training data in [machine learning](https://www.ibm.com/think/topics/machine-learning) models.

Ridge regression—also known as L2 regularization—is one of several types of regularization for [linear regression](https://www.ibm.com/topics/linear-regression) models. [Regularization](https://www.ibm.com/topics/regularization) is a statistical method to reduce errors caused by overfitting on training data. Ridge regression specifically corrects for [multicollinearity](https://www.ibm.com/topics/multicollinearity) in regression analysis. This is useful when developing machine learning models that have a large number of parameters, particularly if those parameters also have high weights. While this article focuses on regularization of linear regression models, note that ridge regression may also be applied in [logistic regression](https://www.ibm.com/topics/logistic-regression#:~:text=Resources-,What%20is%20logistic%20regression%3F,given%20dataset%20of%20independent%20variables.).

### The problem: multicollinearity

A standard, multiple-variable linear regression equation is:

![Standard multivariate linear regression formula](https://assets.ibm.com/is/image/ibm/skill-up-ridge-regression-equation-1?ts=1763386758792&dpr=off)

Here, *Y* is the predicted value (dependent variable), *X* is any predictor (independent variable), *B* is the regression coefficient attached to that independent variable, and *X<sub>0</sub>* is the value of the dependent variable when the independent variable equals zero (also called the y-intercept). Note how the coefficients mark the relationship between the dependent variable and a given independent variable.

Multicollinearity denotes when two or more predictors have a near-linear relationship. Montgomery et al. offer one apt example: Imagine we analyze a supply chain delivery dataset in which long-distance deliveries regularly contain a high number of items while short-distance deliveries always contain smaller inventories. In this case, delivery distance and item quantity are linearly correlated, as shown in Figure 1. This creates problems when using these as independent variables in a single predictive model.

![Scatter plot showing linear correlation between independent variables, order distance and size](https://assets.ibm.com/is/image/ibm/skill-up-ridge-regression-figure-1?ts=1763386758956&dpr=off)

This is only one example of multicollinearity, and its fix is relatively simple: collect more diversified data (for example data for short distance deliveries with large inventories). Collecting more data is not always be a viable fix, however, such as when multicollinearity is intrinsic to the data studied. Other options for fixing multicollinearity include increasing sample size, reducing the number of independent variables, or simply deploying a different model. Such fixes do not always succeed in eliminating multicollinearity, however, and ridge regression serves as another method for regularizing a model to address multicollinearity.<sup>1</sup>

## How ridge regression works: the regularization algorithm

When initially developing predictive models, we often need to compute coefficients, as coefficients are not explicitly stated in the training data. To estimate coefficients, we can use a standard ordinary least squares (OLS) matrix coefficient estimator:

![Ordinary least squares matrix coefficient estimator](https://assets.ibm.com/is/image/ibm/skill-up-ridge-regression-equation-2?ts=1763386759312&dpr=off)

Knowing this formula’s operations requires familiarity with matrix notation. Suffice it to say, this formula aims to find the best-fitting line for a given dataset by calculating coefficients for each independent variable that collectively result in the smallest residual sum of squares (also called the sum of squared errors).<sup>2</sup>

Residual sum of squares (RSS) measures how well a linear regression model matches training data. It is represented by the formulation:

![Residula sum of squares formula](https://assets.ibm.com/is/image/ibm/skill-up-ridge-regression-equation-3?ts=1763386759473&dpr=off)

This formula measures model prediction accuracy for ground-truth values in the training data. If RSS = 0, the model perfectly predicts dependent variables. A score of zero is not always desirable, however, as it can indicate [overfitting](https://www.ibm.com/topics/overfitting) on the training data, particularly if the training dataset is small. Multicollinearity may be one cause of this.

High coefficient estimates can often be symptomatic of overfitting.<sup>3</sup> If two or more variables share a high, linear correlation, OLS may return erroneously high-value coefficients. When one or more coefficients are too high, the model’s output becomes sensitive to minor alterations in the input data. In other words, the model has overfitted on a specific training set and fails to accurately generalize on new test sets. Such a model is considered unstable.<sup>4</sup>

Ridge regression modifies OLS by calculating coefficients that account for potentially correlated predictors. Specifically, ridge regression corrects for high-value coefficients by introducing a regularization term (often called the penalty term) into the RSS function. This penalty term is the sum of the squares of the model’s coefficients.<sup>5 </sup>It is represented in the formulation:

![L2 penalty term formulation](https://assets.ibm.com/is/image/ibm/skill-up-ridge-regression-equation-4?ts=1763386759715&dpr=off)

The L2 penalty term is inserted as the end of the RSS function, resulting in a new formulation, the ridge regression estimator. Therein, its effect on the model is controlled by the hyperparameter lambda (λ):

![Ridge regression formula, or RSS formula with L2 penalty term](https://assets.ibm.com/is/image/ibm/skill-up-ridge-regression-equation-5?ts=1763386759881&dpr=off)

Remember that coefficients mark a given predictor’s (that is, independent variable’s) effect on the predicted value (that is, dependent variable). Once added into RSS formula, the L2 penalty term counteracts especially high coefficients by reducing all coefficient values. In statistics, this is called coefficient shrinkage. The above ridge estimator thus calculates new regression coefficients that reduce a given model’s RSS. This minimizes every predictor’s effect and reduces overfitting on training data.<sup>6</sup>

Note that ridge regression does not shrink every coefficient by the same value. Rather, coefficients are shrunk in proportion to their initial size. As λ increases, high-value coefficients shrink at a greater rate than low-value coefficients.<sup>7</sup> High-value coefficients are thus penalized greater than low-value coefficients.

## Ridge regression versus lasso regression

Note that the L2 penalty shrinks coefficients towards zero but never to absolute zero; although model feature weights may become negligibly small, they never equal zero in ridge regression. Reducing a coefficient to zero effectively removes the paired predictor from the model. This is called feature selection, which is another means of correcting multicollinearity.<sup>8 </sup>Because ridge regression does not reduce regression coefficients to zero, it does not perform feature selection.<sup>9</sup> This is often cited as a disadvantage of ridge regression. Moreover, another oft-cited disadvantage is ridge regression’s inability to separate predictor effects in the face of severe multicollinearity.<sup>10</sup>

Lasso regression—also called L1 regularization—is one of several other regularization methods in linear regression. L1 regularization works by reducing coefficients to zero, essentially eliminating those independent variables from the model. Both lasso regression and ridge regression thus reduce model complexity, albeit by different means. Lasso regression reduces the number of independent variables affecting the output. Ridge regression reduces the weight each independent variable has on the output.

### Other regression regularization techniques

Elastic net is an additional form of regularization. Whereas ridge regression obtains its regularization parameter from the sum of squared errors and lasso obtains its own from the sum of the absolute value of errors, Elastic net incorporates both regularization parameters into the RSS cost function.<sup>11</sup>

Principal componenet regression (PCR) can also act as a regularizing procedure. While PCR can resolve multicollinearity, it does not do so by enforcing a penalty on the RSS function as in ridge and lasso regression. Rather PCR produces linear combinations of correlated predictors from which to create a new least squares model.<sup>12</sup>

## Ridge regression in machine learning

### Model complexity

In machine learning, ridge regression helps reduce overfitting that results from model complexity. Model complexity can be due to:

- **A model possessing too many features.** Features are the model’s predictors and may also be called “parameters” in machine learning. Online tutorials often recommend keeping the number of features below the number of instances in training data sets. Such is not always be feasible however.
- **Features possessing too much weight.** Feature weight refers to a given predictor’s effect on the model output. A high feature weight is equivalent to a high-value coefficient.

Simpler models do not intrinsically perform better then complex models. Nevertheless, a high degree of model complexity can inhibit a model’s ability to generalize on new data outside of the training set.

Because ridge regression does not perform feature selection, it cannot reduce model complexity by eliminating features. But if one or more features too heavily affect a model’s output, ridge regression can shrink high feature weights (that is, coefficients) across the model per the L2 penalty term. This reduces the complexity of the model and helps make model predictions less erratically dependent on any one or more feature.

### Bias-variance tradeoff

In machine learning terms, ridge regression amounts to adding bias into a model for the sake of decreasing that model’s variance. Bias-variance tradeoff is a well-known problem in machine learning. But to understand bias-variance tradeoff, it’s necessary to first know what “bias” and “variance” respectively mean in machine learning research.

To put it briefly: bias measures the average difference between predicted values and true values; variance measures the difference between predictions across various realizations of a given model. As bias increases, a model predicts less accurately on a training dataset. As variance increases, a model predicts less accurately on other datasets. Bias and variance thus measure model accuracy on training and test sets respectively. Obviously, developers hope to reduce model bias and variance. Simultaneous reduction in both is not always feasible, however, and thus the need for regularization techniques such as ridge regression.

As mentioned, ridge regression regularization introduces additional bias for the sake of decreased variance. In other words, models regularized through ridge regression produce less accurate predictions on training data (higher bias) but more accurate predictions on test data (lower variance). This is bias-variance tradeoff. Through ridge regression, users determine an acceptable loss in training accuracy (higher bias) in order to increase a given model’s generalization (lower variance).<sup>13 </sup>In this way, increasing bias can help improve overall model performance.

The strength of the L2 penalty, and so the model’s bias-variance tradeoff, is determined by the value λ in the ridge estimator loss function equation. If λ is zero, then one is left with an ordinary least squares function. This creates a standard linear regression model without any regularization. By contrast, a higher λ value means more regularization. As λ increases, model bias increases while variance decreases. Thus, when λ equals zero, the model overfits the training data, but when λ is too high, the model underfits on all data.<sup>14</sup>

Mean square error (MSE) can help determine a suitable λ value. MSE is closely related to RSS and is a means of measuring the difference, on average, between predicted and true values. The lower a model’s MSE, the more accurate its predictions. But MSE increases as λ increases. Nevertheless, it is argued that there always exists a value of λ greater than zero such that MSE obtained through ridge regression is smaller than that obtained through OLS.<sup>15</sup> One method for deducing a suitable λ value is to find the highest value for λ that does not increase MSE, as illustrated in Figure 2. Additional [cross-validation](https://www.ibm.com/docs/en/spss-modeler/18.0.0?topic=settings-cross-validation) techniques can help users select optimal λ values for tuning their model.<sup>16</sup>

![Graph modeling relation between MSE, bias, variance, and lambda penalty term](https://assets.ibm.com/is/image/ibm/skill-up-ridge-regression-figure-2?ts=1763386760974&dpr=off)

## Example use cases

Ridge regression models are best used when dealing with datasets that possess two or more correlated features. Additionally, many fields use ridge regression to deal with models with a larger number of predictors and small training datasets.<sup>17</sup>[](#_edn1) Such situations can be quite common in when dealing with a variety of data.

Computational biology and genetic studies often deals with models in which the number of predictors vastly outnumber dataset sample sizes, particularly when investigating genetic expression. Ridge regression provides one means to address such model complexity by reducing the total weight of these multitudinous features, compressing the model’s predictive range.

A myriad predictors determine a house’s final sale price and many are correlated, such as number of bedrooms and bathrooms. Highly correlated features lead to high regression coefficients and overfitting on training data. Ridge regression corrects for this form of model complexity by reducing total feature weights on the model’s final predicted value.

These are only two examples in the wider discipline of data science. But as these two examples illustrate, you can most effectively employ ridge regression in situations where you either have more model features than data samples or when your model has two or more highly correlated features.

## Recent research

Recent research explores a modified variant of ridge regression for the purpose of conducting feature selection.<sup>18 </sup>This modified form of ridge regression utilizes different regularization parameters on each coefficient. In this way, one may individually penalize feature weights, and so potentially implement feature selection through ridge regression.<sup>19</sup>

## Footnotes

<sup>1</sup> Douglas C. Montgomery, Elizabeth A. Peck, and G. Geoffrey Vining. *Introduction to Linear Regression Analysis*. John Wiley & Sons. 2012.

<sup>2</sup> Max Kuhn and Kjell Johnson. *Applied Predictive Modeling*. Springer. 2016. Ludwig Fahrmeir, Thomas Kneib, Stefan Lang, and Brian D. Marx. *Regression: Models, Methods and Applications*. 2nd edition. Springer. 2021.

<sup>3</sup> Wessel N. van Wieringen. *Lecture Notes on Ridge Regression*. 2023. [https://arxiv.org/pdf/1509.09169.pdf](https://arxiv.org/pdf/1509.09169.pdf)

<sup>4</sup> A. K. Md. Ehsanes Saleh, Mohammad Arashi, and B. M. Golam Kibria. *The Theory of Ridge Regression Estimation with Applications*. Wiley. 2019.

<sup>5</sup> Ludwig Fahrmeir, Thomas Kneib, Stefan Lang, and Brian D. Marx. *Regression: Models, Methods and Applications*. 2nd edition. Springer. 2021.

<sup>6</sup> Max Kuhn and Kjell Johnson. *Applied Predictive Modeling*. Springer. 2016.

<sup>7</sup> A. K. Md. Ehsanes Saleh, Mohammad Arashi, Resve A. Saleh, and Mina Norouzirad. *Rank-Based Methods for Shrinkage and Selection: With Application to Machine Learning*. Wiley. 2022.

<sup>8</sup> Douglas C. Montgomery, Elizabeth A. Peck, and G. Geoffrey Vining. *Introduction to Linear Regression Analysis*. John Wiley & Sons. 2012.

<sup>9</sup> Max Kuhn and Kjell Johnson. *Applied Predictive Modeling*. Springer. 2016.

<sup>10</sup> Ludwig Fahrmeir, Thomas Kneib, Stefan Lang, and Brian D. Marx. *Regression: Models, Methods and Applications*. 2nd edition. Springer. 2021.

<sup>11</sup> Hui Zou and Trevor Hastie. “Regularization and Variable Selection via the Elastic Net.” *Journal of the Royal Statistical Society*. Vol. 67, No. 2. 2005. pp. 301–320. [https://academic.oup.com/jrsssb/article/67/2/301/7109482](https://academic.oup.com/jrsssb/article/67/2/301/7109482)

<sup>12</sup> Ludwig Fahrmeir, Thomas Kneib, Stefan Lang, and Brian D. Marx. *Regression: Models, Methods and Applications*. 2nd edition. Springer. 2021.

<sup>13</sup> Max Kuhn and Kjell Johnson. *Applied Predictive Modeling*. Springer. 2016.

<sup>14</sup> Gianluigi Pillonetto, Tianshi Chen, Alessandro Chiuso, Giuseppe De Nicolao, and Lennart Ljung. *Regularized System Identification: Learning Dynamic Models from Data*. Springer. 2022.

<sup>15</sup> Arthur E. Hoerl and Robert W. Kennard. “Ridge Regression: Biased Estimation for Nonorthogonal Problems.” *Technometrics*. Vol. 12, No. 1. Feb. 1970. pp. 55–67. [https://www.tandfonline.com/doi/abs/10.1080/00401706.2020.1791254](https://www.tandfonline.com/doi/abs/10.1080/00401706.2020.1791254)

<sup>16</sup> Wessel N. van Wieringen. *Lecture Notes on Ridge Regression*. 2023. [https://arxiv.org/pdf/1509.09169.pdf](https://arxiv.org/pdf/1509.09169.pdf)

<sup>17</sup> Ludwig Fahrmeir, Thomas Kneib, Stefan Lang, and Brian D. Marx. *Regression: Models, Methods and Applications*. 2nd edition. Springer. 2021.

<sup>18</sup> Yichao Wu. “Can’t Ridge Regression Perform Variable Selection?” *Technometrics*. Vol. 63, No. 2. 2021. pp. 263–271. [https://www.tandfonline.com/doi/abs/10.1080/00401706.2020.1791254](https://www.tandfonline.com/doi/abs/10.1080/00401706.2020.1791254)

<sup>19</sup> Danielle C. Tucker, Yichao Wu, and Hans-Georg Müller. “Variable Selection for Global Fréchet Regression.” *Journal of the American Statistical Association*. 2021. [https://www.tandfonline.com/doi/abs/10.1080/01621459.2021.1969240](https://www.tandfonline.com/doi/abs/10.1080/01621459.2021.1969240)
