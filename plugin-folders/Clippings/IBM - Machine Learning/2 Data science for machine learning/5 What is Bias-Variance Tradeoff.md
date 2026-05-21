---
title: "What is Bias-Variance Tradeoff?"
source: "https://www.ibm.com/think/topics/bias-variance-tradeoff#498277086"
author:
  - "[[Fangfang Lee]]"
published:
created: 2026-05-21
description: "Bias-variance tradeoff is a fundamental principle that governs the performance of machine learning models. Understanding the core concept of bias-variance tradeoff will help practitioners build robust AI systems that are strike a balance between high training accuracy and high testing accuracy. The article aims to show details and example of bias-variance tradeoff."
tags:
  - "clippings"
---
## Author

Developer Advocate

IBM

## Introduction to bias-variance tradeoff

When we decide on building an ML model for a specific business problem, we want to choose a model architecture that minimizes errors and capture underlying signals. Bias and variance represent two sources of prediction error. Bias measures how far off predictions are from the true values due to overly simplistic assumptions; variance, however, captures how much predictions fluctuate based on different training data.

Understanding and managing this tradeoff is crucial for building models that generalize well to unseen data. Models with high bias are prone to [underfitting](https://www.ibm.com/think/topics/underfitting), missing important patterns, while models with high variance are prone to [overfitting](https://www.ibm.com/think/topics/overfitting), capturing noise as if it were signal. Striking the right balance is at the heart of effective machine learning design and helps explain why models that perform well on training data might still fail in the real world.

In this explainer, we dive into technical details of bias-variance tradeoff and prediction error, painting a picture of how to build the right model for a dataset.

## Tradeoff illustrated

In predictive models such as linear regression or K-nearest neighbor (KNN), bias and variance are interdependent:

- **Bias** measures how far off, on average, a model’s predictions are from the ground truth values. High-bias models tend to make strong assumptions about the form of the data and cause underfitting. An overly simplistic model tends to have high bias and low variance—a model like this tends to have high training errors and high prediction errors.
- **Variance** measures how much a model’s predictions change with different training datasets. High-variance models are sensitive to noise in the training data and cause overfitting. A model with complex architecture and more parameters tends to have high variance and low bias.

![Bias variance diagram](https://assets.ibm.com/is/image/ibm/bias-variance-diagram:1x1?fmt=png-alpha&dpr=on%2C2.2222222222222223&wid=1584&hei=1584)

In this explainer, we use [linear regression](https://www.ibm.com/think/topics/linear-regression) as an example to illustrate how the model complexity affects the bias and variance in predicted results. Recall that in linear regression, the evaluation metric is defined by mean square error (MSE): the average squared error from ground truth and predicted value. A large MSE indicates a poorly fit model on the training data, whereas a low MSE indicates a well-fitted model on the training data.

MSE is defined as:

$MSE=(ypred-yactual)2$

Or expressed as a residual sum of squares:

$RSS=∑i=1n(yi-yi^)2$

Let’s say we’re given a set of input values X and corresponding output values Y. The true relationship between X and Y is nonlinear—think of a smooth, curved U-shape like a sine wave. But we don’t know that underlying function. Instead, we observe noisy data points that approximate it.

![Graphic of noisy data](https://assets.ibm.com/is/image/ibm/noisy-data:3x2?fmt=png-alpha&dpr=on%2C2.2222222222222223&wid=1584&hei=1056)

We now want to build a model to predict Y by using X.

To illustrate how model complexity affects performance, we can try fitting three models of increasing complexity: a linear model, a moderately complex polynomial model and a very complex polynomial model.

This noise component introduces randomness, mimicking real-world data. A polynomial is a mathematical expression involving a sum of powers of X multiplied by coefficients.

**For example, a degree 1 polynomial is:**

$y^=β0+β1x$

The model is represented as a straight line:

![Polynomial degree 1](https://assets.ibm.com/is/image/ibm/polynomial_degree_1:1x1?fmt=png-alpha&dpr=on%2C2.2222222222222223&wid=1584&hei=1584)

This model is **very simple** and makes a strong assumption that the relationship between X and Y is linear. But the data clearly has a curved pattern. As a result:

- Bias is high: The model cannot capture the nonlinear pattern in the data.
- Variance is low: It is stable and doesn’t change much with different datasets.
- MSE (mean squared error): 0.2929. This is relatively high.

This is an example of underfitting—the model is too simple to learn the true structure.

**A degree 4 polynomial is**:

$y^=β0+β1x+β2x2+β3x3+β4x4$

![Polynomial degree 4](https://assets.ibm.com/is/image/ibm/polynomial_degree_4:1x1?fmt=png-alpha&dpr=on%2C2.2222222222222223&wid=1584&hei=1584)

Now we use a polynomial that includes powers of x up to $x4$:

$y^=β0+β1x+β2x2+β3x3+β4x4$

This model is complex enough to capture the curve of the data without being too sensitive to noise.

- Bias is moderate: The model can represent the true function fairly well.
- Variance is moderate: It doesn’t overreact to small fluctuations in the data.
- MSE: About 0.0714, lower than degree 1.

This is the best-performing model in our example—it generalizes well.

**A degree 25 polynomial is:**

$y^=∑i=025βixi$

![Polynomial degree 25](https://assets.ibm.com/is/image/ibm/polynomial_degree_25?fmt=png-alpha&dpr=on%2C2.2222222222222223&wid=1584&hei=1584)

With 26 parameters, the model has high flexibility and fits the training data very closely—even the random noise. The curve looks very squiggly and overfits the data.

- Bias is low: It’s flexible enough to follow the signal.
- Variance is high: It reacts strongly to noise and would change significantly with a new sample of data.
- MSE: About 0.059—lower than degree 4 because it overmemorized the pattern of the training data and over.

This is an example of overfitting—the model learns the noise along with the signal and doesn’t generalize well to the unseen data.

The higher the degree, the more "wiggly" the curve becomes, and the more it can adapt to the training data—including both signal and noise.

In the example above, we can see that model complexity and the number of parameters directly affect bias-variance tradeoff. As the model becomes more complex and has more parameters, the variability in predicted values in the testing set increases, leading to high variance. However, as the model simplifies and the numbers of parameters decrease, the $bias2$ in prediction increases.

Therefore, when we construct a machine learning model, we aim to simultaneously bias and variance to achieve optimum model performance. This optimization not only generates good results from the training, but also generalize well to unseen testing data. In the next section, we dive into the mathematical details of how bias and variance calculation is derived and why machine learning model contains uncertainties that are made up of bias, variance and irreducible error.

![Bias variance tradeoff](https://assets.ibm.com/is/image/ibm/bias_variance_tradeoff_padding:4x3?fmt=png-alpha&dpr=on%2C2.2222222222222223&wid=1584&hei=1188)

## Bias and variance in practice

Understanding how bias and variance manifest in real-world machine learning models is essential for diagnosing and improving performance. In the following section, we dive into details on how high bias and high variance model lead to potentially poor performances in an AI system.

### High-bias models

High-bias models are typically too simplistic to capture the true patterns in the data. They underfit the training set, leading to poor training and test accuracy. A classic example is linear regression applied to the nonlinear data shown before. If the true relationship between features and target is quadratic or sinusoidal and we fit a straight line, the model lacks the capacity to capture the underlying structure.

Symptoms: High error on both training and test sets. The bias becomes large and leading to poor performance on both training set and testing set.

### High-variance models

High-variance models are overly flexible and fit the training data too closely, including the noise. They overfit the training set and fail to generalize to unseen data, leading to overfitting and leading to predictions with abnormally high variability.

Common examples include:

- [Decision trees](https://www.ibm.com/think/topics/decision-trees) with no pruning.
- Polynomial regression with high degrees.
- KNN with very low k.

Symptoms: Low training error but high test error. The predictions vary significantly across different [datasets](https://www.ibm.com/think/topics/dataset). The variance term dominates the error, indicating the model is unstable regarding training data changes.

### Diagnosing bias and variance

Some practical tools to diagnose these errors include:

**Learning curves (shown before in section I):**

- Plot training and validation error versus training set size.
- If both errors are high and converge, it indicates a high bias.

**If training error is low and validation error is high, with a gap that doesn't close, it suggests high variance. Cross-validation can be applied to diagnose the performance of the model and averaging out errors from the selected training set.**

- Helps estimate generalization error.
- Useful for comparing models or hyperparameters in a variance-aware way.

## The latest tech news, backed by expert insights

Stay up to date on the most important—and intriguing—industry trends on AI, automation, data and beyond with the Think newsletter. See the [IBM Privacy Statement](https://www.ibm.com/us-en/privacy).

## Real-world consideration

In practice, controlling the bias-variance tradeoff is less about picking the "perfect" model and more about managing complexity through various strategies. We can apply several techniques to control the variability in prediction errors by applying some of the following strategies:

### Regularization

[Regularization](https://www.ibm.com/think/topics/regularization) refers to a set of techniques used to constrain or penalize a model's complexity to improve generalization—that is, performance on unseen data. In mathematical terms, regularization modifies the original loss function by adding a penalty term that discourages complexity (usually in the form of large weights or overly flexible models).

The goal is to prevent overfitting, especially when dealing with high-dimensional or limited data. When training a machine learning model, we typically minimize a loss function like Mean Squared Error (MSE)

RSS=∑i=1n(yi-yi^)2

With regularization, we add a penalty to this objective.

### L2 regularization (ridge regression)

LossRidge=∑i=1n(yi-yi^)2+λ\*Penalty

Here,

λ is a [hyperparameter](https://www.ibm.com/think/topics/hyperparameter-tuning) that controls the tradeoff between fitting the training data and keeping the model simple.

It adds a penalty proportional to the square of the magnitude of coefficients. This discourages overly large weights, reducing variance. The penalty term ensures the features that have low predictive power to have low values, effectively reducing the coefficients of the parameters.

### L1 regularization (lasso)

Encourages sparsity:

Losslasso=∑i=1n(yi-ŷi)2+λ∑j=1p|βj|

It can eliminate irrelevant features entirely, simplifying the model and thus reducing the variance. The penalty term USD{\\sum\_{j=1}^{p} |\\beta\_j}USD ensures the insignificant features to be reduced to zero, effectively completely eliminating the features.

### Ensemble methods

[Ensemble](https://www.ibm.com/think/topics/ensemble-learning) methods combine multiple models to reduce error by averaging out individual prediction deviation. It involves combining, or stacking multiple high-variance models together to get the best prediction accuracy. Some examples include:

\- [Bagging](https://www.ibm.com/think/topics/bagging) (for example, [Random forests](https://www.ibm.com/think/topics/random-forest)) reduces variance by averaging multiple high-variance estimators trained on different data subsets.

\- [Boosting](https://www.ibm.com/think/topics/boosting) (for example, [xgBoost](https://www.ibm.com/think/topics/xgboost), AdaBoost) builds a strong learner by sequentially correcting the errors of previous models, often balancing reduction of bias or variance with careful tuning.

### Hyperparameter tuning and model selection

Model complexity and regularization strength are often controlled through hyperparameters. Techniques like grid search or random search with cross-validation or Bayesian optimization can help find a model that balances bias and variance on held-out data.

Think Keynotes

### Power the agentic enterprise

Understand how AI-ready data platforms enable real-time insights and execution, while supporting secure, sovereign deployment across environments.

[Explore watsonx.data](https://www.ibm.com/products/watsonx-data)

## Applications to modern AI

The bias-variance tradeoff is not just theoretical. It plays a critical role in deep learning and large-scale AI systems. In the modern era of AI, the choice of neural network architecture plays a critical role in managing the tradeoff between bias and variance. Here's how two foundational architectures—CNNs and RNNs—navigate this balance in practice.

**1\. Convolutional neural networks (CNNs)**: CNNs are designed specifically for data with a spatial structure—most commonly, images. Their architectural features allow them to reduce variance while maintaining sufficient expressiveness to keep bias low.

- **Local receptive fields (Convolutions):** Instead of connecting every input pixel to every output neuron (as in fully connected networks), CNNs use small filters (kernels) that slide across the input. This enforces the assumption that local features are useful—a bias toward spatial locality.
- **Weight sharing:** Each filter (or kernel) is reused across the entire image, drastically reducing the number of trainable parameters. This limits overfitting, lowering variance, but introduces some bias by constraining the model’s flexibility.
- **Pooling layers (for example, max pooling):** These layers summarize feature maps and introduce translation invariance. While this reduces variance by ignoring minor fluctuations, it might increase bias by discarding some potentially useful details.
- **Hierarchical feature learning:** CNNs learn from low-level edges to high-level shapes layer by layer. This layered inductive bias allows generalization with fewer examples—helpful in data-scarce domains.

**2\. Recurrent neural networks (RNNs):** RNNs are tailored to sequential data such as text, speech or time series, where current outputs depend on previous elements. Their design tries to balance long-term dependencies (which reduce bias) and training stability (which controls variance).

- **Weight sharing over time:** RNNs use the same parameters at every time step, introducing a bias toward stationarity in sequences (assuming the same kind of patterns recur), but significantly reducing variance by limiting parameter growth.
- **Memory of past inputs:** RNNs maintain a hidden state h\_t that summarizes past information. In theory, this state allows the model to reduce bias by modeling long-range dependencies. However, in practice, vanishing gradients often prevent them from learning long-term relationships effectively, increasing bias.
- **Variants like long short-term memory (LSTM) and gated recurrent unit (GRU):** These architectures mitigate vanishing gradients by using gates, allowing better memory retention over time. As a result, they can lower bias further without a large increase in variance.
- **Training stability and overfitting:** Deep RNNs (many layers or long sequences) are prone to high variance—overfitting noise in training sequences. Techniques like dropout, gradient clipping and sequence bucketing are often used to control this.

### Techniques that control the tradeoff

- **Dropout:** Randomly turning off neurons during training adds noise, forcing the network to learn redundant representations—reducing overfitting and thus variance.
- **Batch normalization:** Helps stabilize and accelerate training, and often reduces variance by smoothing optimization.
- **Early stopping:** Prevents overfitting by halting training when validation loss starts increasing.
- **Transfer learning:** Pretrained models on large datasets often generalize better with fewer parameters to train, reducing variance on small datasets.
- **Scaling laws and modern observations:** Recent findings in large models (like [transformers](https://www.ibm.com/think/topics/transformer-model)) show that increasing data, compute and model size reduces test error—suggesting bias decreases faster than variance increases in high-capacity models. However, poor regularization or insufficient data can still lead to overfitting.

## Theoretical foundations

Let's dive into the mathematical foundations of the bias-variance tradeoff. Recall from the previous example, we aim to reduce the total error of predicted values and actual values. This error is composed of three components: bias, variance and irreducible error. We can analyze the expected squared prediction error of a model:

f^(x)

compared to the true function: f(x),

where f^(x) is learned from a training dataset D, and x is the true (unknown) function.

Let:

y=f(x)+ε,ε∼N(0,σ2)

this means for the function y=f(x)+ε, the error (denoted by ε ) is normally distributed with a mean of 0 and a variance of σ2, σ denotes the standard deviation of the distribution

f^(x) is the model’s predicted value at input x

The expectation (or mean) is taken over different training datasets D and noise ε. The symbol E is used to express "expectation," or "expected value," which is a true value of the mean of the distribution

We are interested in the expected prediction error at a single point x:

ED,ε\[(y-f^(x))2\]

Substitute:

y=f(x)+ε

So the expression becomes:

\=ED,ε\[(f(x)+ε-f^(x))2\]

Expanding the square:

$=ED,ε\[(f(x)-f^(x))2+2(f(x)-f^(x))ε+ε2\]$

Split the expectation by using linearity (linearity is a simple algebraic concept, for example, E\[A+B\]=E\[A\]+E\[B\]):

\=ED\[(f(x)-f^(x))2\]+2ED,ε\[(f(x)-f^(x))ε\]+Eε\[ε2\]

Now, since:

E\[ε\]=0⇒E\[(f(x)-f^(x))ε\]=0

E\[ε2\]=σ2

We get:

ED\[(f(x)-f^(x))2\]+σ2

### Decomposing the first term:

Add and subtract

ED\[f^(x)\]:

ED\[(f(x)-f^(x))2\]=ED\[(f(x)-ED\[f^(x)\]+ED\[f^(x)\]-f^(x))2\]

Let:

a=f(x)-ED\[f^(x)\]

b=ED\[f^(x)\]-f^(x)

Then:

ED\[(a+b)2\]=a2+ED\[b2\]+2aED\[b\]

Since ED\[b\]=0, the cross term vanishes, and we get:

\=(f(x)-ED\[f^(x)\])2+ED\[(f^(x)-ED\[f^(x)\])2\]

### Final bias-variance decomposition:

ED,ε\[(y-f^(x))2\]=$$(f(x)-ED\[f^(x)\])2+ED\[(f^(x)-ED\[f^(x)\])2\]+σ2

Here, the first term is bias2, second term is variance, and the third term is irreducible error

This shows that the total expected prediction error can be decomposed into:

\- **Bias²:** Error from erroneous assumptions in the model (for example, underfitted, overly simple model)

\- **Variance:** Error from sensitivity to training data (for example, overfitted, overly complex model)

\- **Irreducible noise:** Unavoidable randomness and error in the observations

## Conclusion and further reading

In summary, bias and variance are two fundamental sources of prediction error in machine learning. Understanding this tradeoff is not just a theoretical exercise—it directly shapes how we design, train and deploy ML models in practice.

Whether you're choosing between a simple linear model or a complex deep neural network, recognizing the balance between underfitting and overfitting is essential to building robust AI systems. While we focused on mean squared error (MSE) as our loss function, this tradeoff applies to a wide range of distributions and error metrics—making it a universal consideration across supervised learning.

In recent years, researchers have observed intriguing behavior in large, overparameterized models like deep neural networks. Despite their high capacity, these models often generalize well, even when they perfectly fit the training data—seemingly defying the traditional bias-variance framework.

This puzzling behavior is explored in works like "Reconciling modern machine learning and the bias-variance trade-off" by Belkin et al. (2019), which introduces the concept of double descent, and "A universal law of robustness via isoperimetry" by Bubeck et al., which proposes a geometric interpretation of generalization.

As we build more powerful AI systems, a deeper understanding of these dynamics becomes essential—not only for optimizing performance, but also for interpreting model behavior, ensuring fairness, and advancing responsible AI practices.

Link copied

## Resources

[![Podcast starring Cassie Kozyrkov: Right Data, right decisions](https://assets.ibm.com/is/image/ibm/1280x720_16x9_aiia_thumbnail_dataintelligence_s2_ep9_01-1:4x3?fmt=png-alpha&dpr=on%2C2.2222222222222223&wid=1584&hei=1188 "Think podcast cover with greenery backdrop")](https://www.ibm.com/think/podcasts/ai-in-action/decision-intelligence-data-driven)

[Podcast: Decision Intelligence: Thoughtful, data-driven choices](https://www.ibm.com/think/podcasts/ai-in-action/decision-intelligence-data-driven)

[

Learn about the concept of decision intelligencd and how data-driven decision-making can create real impact within your business

](https://www.ibm.com/think/podcasts/ai-in-action/decision-intelligence-data-driven)

Take the next step

Unify all your data for AI and analytics with IBM® watsonx.data™. Put your data to work, wherever it resides, with the hybrid, open data lakehouse for AI and analytics.

1. [Discover watsonx.data](https://www.ibm.com/products/watsonx-data)
2. [Explore data science solutions](https://www.ibm.com/data-science)

##### References

\[1\]: Hastie, T., Tibshirani, R., & Friedman, J. **[The Elements of Statistical Learning](https://hastie.su.domains/ElemStatLearn/).** Springer.

\[2\]: James, G., Witten, D., Hastie, T., & Tibshirani, R. **[An Introduction to Statistical Learning](https://www.stat.berkeley.edu/~rabbee/s154/ISLR_First_Printing.pdf).** Springer.

\[3\]: Belkin, M., Hsu, D., Ma, S., & Mandal, S. (2019). **" [Reconciling modern machine learning and the bias-variance trade-off.](https://arxiv.org/abs/1812.11118)"** Proceedings of the National Academy of Sciences\*, 116(32), 15849–15854.

\[4\]: Bubeck, S., Lee, Y. T., Price, E., & Razenshteyn, I. (2021). **["A universal law of robustness via isoperimetry."](https://arxiv.org/abs/2105.12806)** Advances in Neural Information Processing Systems, 34, 10167–10179.