---
title: What is logistic regression?
source: https://www.ibm.com/think/topics/logistic-regression
author:
- '[[Fangfang Lee]]'
published: 2024-12-02
created: 2026-08-31
description: "Logistic regression estimates the probability of an event occurring, such as voted or didn’t vote, based on a given data set of independent variables."
---

## What is logistic regression?

Logistic regression is a [supervised](https://www.ibm.com/think/topics/supervised-learning) [machine learning](https://www.ibm.com/think/topics/machine-learning) algorithm in [data science](https://www.ibm.com/think/topics/data-science). It is a type of [classification](https://www.ibm.com/think/topics/classification-machine-learning) algorithm that predicts a discrete or categorical outcome. For example, we can use a classification model to determine whether a loan is approved or not based on predictors such as savings amount, income and credit score.

In this article, we dive into the mathematics behind logistic regression—one of the most used classification algorithms in machine learning and artificial intelligence (AI). We will also delve into the details of regression analysis, use cases and different types of logistic regressions. In the era of [generative AI](https://www.ibm.com/think/topics/generative-ai), the foundations that underpin logistic regression still play a critical role in orchestrating complex [neural network](https://www.ibm.com/think/topics/neural-networks) models. Logistic regression is also still highly relevant in performing statistical testing in the context of behavioral and social science research, and the data science field at large. We can implement logistic regression easily by using the [scikit-learn](https://www.ibm.com/think/topics/scikit-learn) module in Python.

In this explainer, we introduce you to the difference between linear regression and logistic regression, the mathematical underpinnings, different types of logistic regressions and its associated use cases.

## Logistic regression vs. linear regression

Logistic regression, like [linear regression](https://www.ibm.com/think/topics/linear-regression), is a type of linear model that examines the relationship between predictor variables (independent variables) and an output variable (the response, target or dependent variable). The key difference is that linear regression is used when the output is a continuous value—for example, predicting someone's credit score. Logistic regression is used when the outcome is categorical, such as whether a loan is approved or not.

In logistic regression, the model predicts the probability that a specific outcome occurs. For instance, given someone’s financial profile, we might predict the probability that their loan is approved. The output of the model is a value between 0 and 1. Based on a threshold—often 0.5—we classify the outcome as either "approved" or "not approved." Instead of drawing a straight line through the data as we would in linear regression, logistic regression fits an S-shaped curve to map input values to a probability.

Both linear and logistic regression use statistical tests to evaluate which predictor variables meaningfully impact the output. Techniques such as the t-test and analysis of variance (ANOVA) (or likelihood ratio tests for logistic regression) generate p-values for each coefficient, helping us assess whether the relationship is statistically significant. A low p-value (typically below 0.05) suggests that the variable contributes meaningfully to the model. We also evaluate the goodness of fit—how well the model explains the observed outcomes—using different metrics depending on the regression type.

As we build models, it’s important to guard against [overfitting](https://www.ibm.com/think/topics/overfitting), where the model captures noise in the training data and performs poorly on new data. This risk increases when we have many predictor variables but a small sample size. To address this issue, we can apply [regularization](https://www.ibm.com/think/topics/regularization), a technique that reduces the influence of less important variables by shrinking their coefficients. Careful attention must also be paid to outliers, as they can distort the model and lead to misleading p-values or coefficients. In practice, we improve models through multiple iterations of [feature selection](https://www.ibm.com/think/topics/feature-selection), testing and refinement.

To contrast the two models more concretely, consider a linear regression scenario where we want to predict someone's credit score, based on features like their current savings. We can model this as:

$$ Y_{creditscore} = \beta_0 + \beta_1 X_{savings}

 $$

![Small scatter plot with blue data points and an upward diagonal trend line on labeled axes.](https://assets.ibm.com/is/image/ibm/linear-regression_-savings-vs-credit-score?ts=1778780625821&dpr=off)

## Logistic regression under the hood

Like linear regression, logistic regression is a type of linear model that falls under the generalized linear models (GLM) family. As in the previous example, if we want to represent the probability of approve or not approve, we apply the linear function.

$$ Y_{approval} = \beta_0 + \beta_1 X_{savings} $$

Because the linear function assumes a linear relationship, as the values of X changes, Y can take on a value from (-inf, inf). Probabilities, as we know, are confined to [0,1]. Using this principle of linear model, we cannot directly model the probabilities for a binary outcome. Instead, we need a logistic model to make sense of the probabilities. Therefore, we want to apply a transformation to the input so the outcome can be confined. This transformation is known as the logistic regression equation. This equation might look complex, but we will break it down step by step how it is derived in the following section.

$$ Y = P(x) = \frac{e^{\beta_0 + \beta_1 x}}{1 + e^{\beta_0 + \beta_1 x}}

 $$

![Small line chart showing an S-shaped curve with blue data points on labeled axes.](https://assets.ibm.com/is/image/ibm/loan-approval-by-savings-amount?ts=1778780626908&dpr=off)

The sigmoid transformation allows us to make a binary prediction for the preceding use case. After applying the transformation, the value of X can take on (-inf, inf) and y will be confined to [0,1]

To understand the logistic regression function (or the sigmoid function), we need a solid foundation on the following concepts:

- Odds, log-odds and odds ratio
- Coefficients of the logistic regression
- Maximum likelihood estimates (MLE)

## Odds, log odds and odds ratio

### Odds

The log of the ratio of the probabilities is known as the logit function, and it forms the basis of logistic regression.

Because we cannot model probabilities directly by using a linear function—because probabilities are constrained between 0 and 1—we instead work with odds. While both probability and odds represent the likelihood of an outcome, they differ in definition:

Probability measures the chance of an event occurring out of all possible outcomes.

![A minimalist graphic featuring blue and red circles on a white square.](https://assets.ibm.com/is/image/ibm/oddsv2?ts=1778780628072&dpr=off)

Odds compare the chance of an event occurring to the chance of it not occurring.

![A minimalist graphic featuring blue and red circles on a white square.](https://assets.ibm.com/is/image/ibm/oddsv1?ts=1778780628646&dpr=off)

### Log Odds

Let p(x) represent the probability of an outcome. Then, the odds of x are defined as:

$$ {odds}(x) = \frac{p(x)}{1 - p(x)} $$

Let’s take a concrete example:

Suppose a basket contains 3 apples and 5 oranges.

- The probability of picking an orange is 5/(3+5) = 0.625

- The odds of picking an orange are 5/3 ≈ 1.667

This means that picking an orange is ≈1.667 times more likely than picking an apple. Conversely, the odds of picking an apple are 3 / 5 = 0.6, which is less than 1, indicating the outcome (picking an apple) is less likely than not. Following the equation of odds, we can also think of odds as the probability of an outcome occurring over 1 - probability of outcome occurring. Therefore, odds of picking an orange are = P(oranges)/(1-P(oranges))=0.625/(1-0.625)≈1.667

Odds can range from 0 to infinity. An odds value greater than 1 indicates a favorable outcome, less than 1 indicates an unfavorable outcome and equal to 1 means the event is just as likely to occur as not.

However, the odds are not symmetric around 1. For example, odds of 2 and 0.5 represent “twice as likely” and “half as likely,” but they’re on very different numerical scales. To address this imbalance, we take the logarithm of the odds, which transforms the unbounded [0, ∞) scale of odds to the real number line (−∞, ∞). This is known as the **log-odds**, or logit, and is the foundation of the logistic regression model.

We define the log-odds as:

$$ \log\left(\frac{p(x)}{1 - p(x)}\right)

 $$

This transformation allows us to express the log-odds as a linear function of the input:

$$ \log\left(\frac{p(x)}{1 - p(x)}\right) = \beta_0 + \beta_1 \cdot x_1

 $$

We can then exponentiate both sides to get back to odds:

$$ \frac{p(x)}{1 - p(x)} = e^{\beta_0 + \beta_1 \cdot x_1}

 $$

Solving for $p(x)$ we get the sigmoid function, which helps ensure the predicted value stays between 0 and 1:

$$ p(x) = \frac{e^{\beta_0 + \beta_1 \cdot x_1}}{1 + e^{\beta_0 + \beta_1 \cdot x_1}}

 $$

This transformation allows logistic regression to output valid probabilities, even though we’re modeling them using a linear function underneath.

### Odds Ratio

Finally, let’s introduce the odds ratio, a concept that helps interpret the effect of model coefficients. The odds ratio tells us how the odds change when the input variable x1 increases by one unit.

Let’s say the odds of the event are:

$$ {odds}(x_1) = e^{\beta_0 + \beta_1 \cdot x_1} $$

If we increase x1 by one unit, the new odds become:

$$ {odds}(x_1 + 1) = e^{\beta_0 + \beta_1 (x_1 + 1)} = e^{\beta_0 + \beta_1 x_1} \cdot e^{\beta_1}
 $$

This means that for every one-unit increase in x1, the odds are multiplied by eb1 . This multiplier is the odds ratio.

- If b1>1, then the odds increase (event becomes more likely)

- If b1<1, then the odds decrease (events becomes less likely)

- If b1=1, the odds ratio is 0, meaning the input has no effect on the odds

The odds ratio gives logistic regression its interpretability—it tells you how the odds of an event change based on inputs, which is useful in many applied settings like healthcare, marketing and finance. However, we cannot interpret the coefficients the same way we interpret that of linear regression. In the next section, let’s take a close look at how the coefficients are determined and interpreted.

## Coefficients of logistic regression

### Continuous predictors

Recall from before: in linear regression, the coefficients are straightforward to interpret. Take an example of a linear regression with continuous variables: for a one-unit increase in the input feature x results in a b1-unit increase in the predicted outcome y. This direct relationship works because linear regression assumes a constant rate of change between input features and the target. Its output is unbounded and grows linearly.

However, logistic regression does not model y directly—it models the probability of y through the log-odds (the log of the odds). Because of this, we cannot say that a one-unit increase in x results in a constant unit change in y. Instead, we interpret the coefficient in terms of its effect on the log-odds, and by extension, on the odds and the probability of the outcome.

More specifically, in logistic regression:

- A positive coefficient means the log-odds of the outcome increase as the input increases. This corresponds to an increase in probability.
- A negative coefficient means the log-odds decrease as the input increases. This corresponds to a decrease in probability.
- A coefficient of zero means that the variable has no effect on the outcome.

Importantly, the magnitude of the coefficient reflects how strong this influence is, and the odds ratio (which is the exponential of the coefficient) tells us how much the odds change for a one-unit increase in the variable.

### Categorical predictors

Just like other [machine learning algorithms](https://www.ibm.com/think/topics/machine-learning-algorithms), we can incorporate categorical variables to make predictions for logistic regression. When working with categorical or discrete variables, we often use [feature engineering](https://www.ibm.com/think/topics/feature-engineering) techniques such as one-hot encoding or dummy variables to convert them into a binary format that the model can use.

For example, using the same concept from earlier, let’s say we want to predict whether someone is approved for a loan ($y = 1$ for approved, $y = 0$ for not approved) based on whether they still have an existing debt:

- Let $x=0$ mean that they have no existing debt

- Let $x = 1$ mean that they have existing debt

Our log-odds of $y = approval$ would be $y = b_0 + b_1 * x_1$

The coefficient $b_1$, then represents the change in log-odds of being approved when the person has an existing debt, compared to someone who does not.

To make this more interpretable, we can exponentiate b1 to get the odds ratio:

- If $b_1$ is positive, $e$ to the power of $b_1$ is greater than 1, meaning having existing debt increases the odds of being approved.
- If $b_1$ is negative, $e$ to the power of $b_1$ is less than 1, meaning having existing debt decreases the odds of approval.
- If $b_1$ is 0, $e$ to the power of $b_1 $ is 1, meaning debt status has no effect.

So, although we lose the straightforward interpretation of coefficients from linear regression, logistic regression still offers rich, interpretable insights—especially when we frame them in terms of odds and probability shifts. The magnitude of increase or decrease in probability as a function of $x$ does not correspond to one unit of increase in $x$, but depends on where $x$ is at a certain point.

## Maximum likelihood estimate

The coefficients in logistic regression, $\beta{0}$ and $\beta_{1}$ , are estimated by using **maximum likelihood estimation (MLE)**. The core idea behind MLE is to find the parameters that make the observed data most "likely" under the logistic regression model.

In logistic regression, we model the probability that the target variable $y_1$ is 1 (for example, "approved") given an input $x_1$ by using the logistic (sigmoid) function:

$$ Y = P(x) = \frac{e^{\beta_0 + \beta_1 x}}{1 + e^{\beta_0 + \beta_1 x}}

 $$

MLE tries different combinations of $b_0
$ and $b_1$, and for each combination, asks: How likely is it that we would see the actual outcomes in our data, given these parameters?

This is captured by using the likelihood function, which multiplies the predicted probabilities for each data point:

$$ L(\beta_0, \beta_1) = \prod_{i=1}^{n} p{(x_i)}^{y_i} \cdot (1 - p{(x_i)})^{1 - y_i} $$

- If $y_1 = 1$ =1 (“approved”), we want the model’s predicted probability $P(x_{1})$ to be as close as 1. The term $p(xi)^yi$ addresses this. If the actual observed data of y1 is actually “approved” or 1, the term will be 1.

- If $y_1 = 0$ =0, we want the predicted probability to be close to 0. The term $(1 - p(x_i))^{1 - y_i}$ handles this case. If the actual observed data of $y1$ is “not approved”, or 0, the value will be $p(x_i)$ will be close to 0, therefore $1 - p(x_i)$ will be close to 1.

So for each data point, we multiply either $p(x1)$ or $1−p(x_i)$ , depending on whether the actual label is 1 or 0. The product over all examples gives us a single number: the likelihood of seeing the entire dataset under the current model. As we can see, if the predicted outcomes (using parameters $b_0$ and $b_1$) conform to the observed data, the value of likelihood will be maximized. The reason behind multiplying all the probabilities together is that we assume the outcomes are independent of each other. In other words, one person’s chance of approval should not influence another person’s chance of approval.

Because this product can get extremely small, we usually work with the log-likelihood, which turns the product into a sum and is easier to compute and optimize.

To find the values of $b_0$ and $b_1$ that maximize the log-likelihood, we use gradient descent—an iterative optimization algorithm. At each step, we compute how the log-likelihood changes with respect to each parameter (for example, its gradient), and then update the parameters slightly in the direction that increases the likelihood. Over time, this process converges toward the values of $b_0$ and $b_1$ that best fit the data.

## Types of logistic regression

There are three types of logistic regression models, which are defined based on categorical response.

- **Binary logistic regression:** In this approach, the response or dependent variable is dichotomous in nature—that is, it has only two possible outcomes (for example, 0 or 1). Some popular examples of its use include predicting if an email is spam or not spam or if a tumor is malignant or not malignant. Within logistic regression, this is the most commonly used approach, and more generally, it is one of the most common classifiers for binary classification.
- **Multinomial logistic regression:** In this type of logistic regression model, the dependent variable has three or more possible outcomes; however, these values have no specified order. For example, movie studios want to predict what genre of film a moviegoer is likely to see to market films more effectively. A multinomial logistic regression model can help the studio to determine the strength of influence a person's age, gender and dating status might have on the type of film that they prefer. The studio can then orient an advertising campaign of a specific movie toward a group of people likely to go see it.
- **Ordinal logistic regression:** This type of logistic regression model is leveraged when the response variable has three or more possible outcomes, but in this case, these values do have a defined order. Examples of ordinal responses include grading scales from A to F or rating scales from 1 to 5.

## Use cases of logistic regression

Logistic regression is commonly used for prediction and classification problems. Some of these use cases include:

- **Fraud detection:** Logistic regression models can help teams identify data anomalies, which are predictive of fraud. Certain behaviors or characteristics might have a higher association with fraudulent activities, which is particularly helpful to banking and other financial institutions in protecting their clients. SaaS-based companies have also started to adopt these practices to eliminate fake user accounts from their datasets when conducting data analysis around business performance.
- **Disease prediction:** In medicine, this analytics approach can be used to predict the likelihood of disease or illness for a given population. Healthcare organizations can set up preventive care for individuals that show a higher propensity for specific illnesses.
- **Churn prediction**: Specific behaviors can be indicative of churn in different functions of an organization. For example, human resources and management teams may want to know if there are high performers within the company who are at risk of leaving the organization. This type of insight can prompt conversations to understand problem areas within the company, such as culture or compensation. Alternatively, the sales organization might want to learn which of their clients are at risk of taking their business elsewhere. This can prompt teams to set up a retention strategy to avoid lost revenue.
