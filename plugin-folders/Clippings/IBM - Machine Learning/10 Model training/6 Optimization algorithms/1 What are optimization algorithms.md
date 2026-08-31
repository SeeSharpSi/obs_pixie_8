---
title: What are optimization algorithms?
source: https://www.ibm.com/think/topics/optimization-algorithms
author:
- '[[Anna Gutowska]]'
published: 2026-04-28
created: 2026-08-31
description: "At a high level, optimization algorithms address optimization problems iteratively by exploring a search space to find variable values that best satisfy given constraints. This process is known as the optimization process, and the goal is usually framed as minimization of a loss function or maximization of an objective function."
---

## Optimization algorithms explained

In computer science, there is a perpetual theme of optimization—finding the best choice among possible solutions. In [machine learning](https://www.ibm.com/think/topics/machine-learning) and [deep learning](https://www.ibm.com/think/topics/deep-learning) specifically, we want to train our [neural networks](https://www.ibm.com/think/topics/neural-networks) in a way that optimizes both the training time and model performance. That is where optimization algorithms come in.

At a high level, optimization algorithms address optimization problems iteratively by exploring a search space to find variable values that best satisfy given constraints. This process is known as the optimization process, and the goal is usually framed as minimization of a [loss function](https://www.ibm.com/think/topics/loss-function) or maximization of an objective function.

In this explainer, we explore what optimization algorithms are in the field of [artificial intelligence](https://www.ibm.com/think/topics/artificial-intelligence), how they are categorized and why different classes of methods are used in different settings.

## Objective functions

An optimization algorithm is a procedure for finding values of variables that minimize or maximize an objective function, often under a set of constraints.

Formally, an optimization problem can be written as:

$\min_{x \in X} f(x) \quad $ subject to $g_i(x) \leq 0,\; h_j(x) = 0$

- ***x*** represents decision variables.
- ***X*** is the feasible space (the domain x must belong to).
- ***f(x)*** is the objective (or loss) function.
- ***g**<sub>i</sub>*<sub> </sub>and ***h**<sub>j</sub>*<sub> </sub>encode inequality and equality constraints

In real-world practice, many machine learning problems are unconstrained, with constraints absorbed into the objective function through [regularization](https://www.ibm.com/think/topics/regularization). Regardless of form, optimization algorithms typically operate iteratively, gradually improving the solution by exploring the search space.

## Key ways to classify optimization algorithms

There are many ways to group optimization algorithms. One of the most intuitive distinctions is based on how much an algorithm knows about the objective function it is trying to optimize. These groups of methods are either deterministic or randomized.

Deterministic algorithms iterate according to well-defined rules and produce the same result given the same initialization, suitable for well-structured or convex problems. Randomized ones, alternatively, use a random selection process suitable for complex or nonconvex settings to better explore the search space.

Optimization methods can also be grouped into zero-order, first-order and second-order algorithms, based on which derivatives of the objective function are used.<sup>1</sup>

### Zero‑order optimization methods

Zero‑order methods do not use gradient or curvature information. They rely solely on evaluating the objective function at sampled points, making them suitable for problems when the gradient and Hessian information (that is, a square matrix of second-order partial derivatives capturing local curvature) are difficult to obtain.

As a result, these methods make very few assumptions about the structure of the problem. For example, when no explicit functions are provided.<sup>2</sup> Examples include random search, genetic algorithms, particle swarm optimization and other derivative‑free metaheuristic methods or evolutionary algorithms.

### First‑order optimization methods

First-order methods use first‑order derivative information, typically gradients, to guide the optimization process regarding the parameters. They dominate modern machine learning due to their scalability in high-dimensional settings.

The canonical example is gradient descent, where [model parameters](https://www.ibm.com/think/topics/model-parameters) are updated by moving opposite to the gradient, scaled by a [learning rate](https://www.ibm.com/think/topics/learning-rate) that controls the step size. In machine learning, this approach is especially popular because it is computationally efficient and scales well to high‑dimensional, large‑scale problems.

**[Gradient descent](https://www.ibm.com/think/topics/gradient-descent)** uses the entire training [dataset](https://www.ibm.com/think/topics/dataset) to compute the gradient before each parameter update. A widely used variant is **[stochastic gradient descent (SGD)](https://www.ibm.com/think/topics/stochastic-gradient-descent)**, which estimates gradients by using a randomly selected data point or mini-batch from the training data.

This stochastic optimization introduces randomness into the process, reducing per‑iteration cost and often helping the algorithm escape shallow local minima in nonconvex landscapes. Common adaptive extensions of SGD adjust learning rates automatically to improve stability, convergence and model generalization. Some examples of adaptive learning rate methods are:<sup>3,4</sup>

- **AdaGrad** adjusts learning rates per [hyperparameter](https://www.ibm.com/think/topics/hyperparameter-tuning) based on accumulated historical gradients, benefiting sparse features but often leading to overly small learning rates.
- **RMSProp** mitigates this issue by using an exponentially weighted moving average of squared gradients, discarding distant history.
- **Adam** **(Adaptive Moment Estimation)** combines momentum with RMSProp-style adaptation by tracking both first and second moments of gradients, achieving fast and stable convergence across many tasks, including natural language processing.<sup>5</sup>

First‑order methods rely only on gradient information, which makes them memory‑efficient and robust. Although they might converge more slowly near an optimum than higher‑order methods, their scalability makes them the default choice for deep learning.

### Second‑order optimization methods

Second‑order optimization methods use both first‑order information (gradients) and second‑order information, such as curvature, typically captured by the Hessian matrix.

A classic example is **Newton’s method**, where parameter updates are scaled by the inverse Hessian. In convex optimization problems, this approach can lead to rapid and reliable convergence to the global optimum. However, computing and storing the Hessian is infeasible for large-scale models, making pure second‑order methods impractical for most modern machine learning models.

To address this limitation, **quasi‑Newton methods** approximate the Hessian (or its inverse) using information from previous iterations. Popular examples include BFGS and L‑BFGS (limited‑memory BFGS). These methods retain many benefits of second‑order optimization while dramatically reducing memory and computational costs. They are commonly used for smaller‑scale problems or well‑behaved objectives where precision and fast convergence are priorities.

## Caveats to consider

It’s important to remember that optimization algorithms do not always find the absolute optimal solution. In a convex optimization problem, any local optimum is guaranteed to be a global optimum. This guarantee makes convex optimization mathematically relatively easy to solve. However, most modern machine learning systems, especially deep neural networks, lead to nonconvex problems.

In nonconvex settings, the optimization landscape is much more complicated, with many local minima and saddle points. As a result, optimization algorithms are not necessarily aiming for the global optimum, but rather for solutions that perform well enough in practice. Outcomes can vary depending on initialization, randomness and even how long the algorithm is run.

![Diagram of Gradient Descent](https://assets.ibm.com/is/image/ibm/ICLH_Diagram_Batch_03_22-AI-ML-GradientDescent?ts=1777384396288&dpr=off)

Not all problems are smooth or differentiable, which limits where gradient-based methods apply. So, what happens when gradients don’t exist? In combinatorial optimization and discrete search problems, for instance, a different toolkit is required—metaheuristic approaches such as genetic algorithms, particle swarm optimization, simulated annealing and local search methods.

These approaches explore the search space by using probabilistic or biologically inspired strategies and often introduce search bias to focus computation on promising regions. While this bias can significantly improve efficiency and scalability, it is often at the cost of guaranteed finding the global optimum.

## Best practices for benchmarking

Comparing optimization algorithms can be difficult. Meaningful evaluation requires careful experimental design. Some widely accepted best practices include:<sup>6</sup>

- Clearly define the goal of the comparison.
- Use a diverse, sufficiently large and unbiased test set.
- Ensure fair experimental conditions (for example, the same environment, stopping criteria, initialization and so on).
- Carefully tune model parameters without bias.
- Use appropriate performance metrics aligned with the goal.
- Run multiple trials and apply statistical analysis.
- Evaluate efficiency, robustness and output quality.
- Use rich reporting methods (performance profiles, convergence plots).
- Ensure reproducibility and transparency.
- Avoid common benchmarking pitfalls like small datasets, cherry-picking and inconsistent setups.

## Conclusion

Optimization algorithms are not one-size-fits-all methods. Choosing the right algorithm depends on the structure of the problem at hand. In the decision-making process, it is important to consider whether the objective is convex or nonconvex, continuous or discrete, smooth or noisy.

Gradient-based methods remain popular for differentiable problems, offering speed and precision when the landscape cooperates. For rougher terrain, metaheuristic approaches adaptively find good-enough solutions where exact methods fail entirely. The practical takeaway is to understand your problem before reaching for an optimization algorithm.

## Footnotes

<sup>1 </sup>Ye, Yinyu. (n.d.). Optimization Algorithm Review and Project Discussions (Lecture 16). *Stanford University*, 2022. Lecture Slides.

<sup>2 </sup>Malik, H., Iqbal, A., Joshi, P., Agrawal, S., & Bakhsh I. F. (2020). Metaheuristic and Evolutionary Computation: Algorithms and Applications. *Springer Nature Singapore*.

<sup>3 </sup>Ruder, S. (2017). An overview of gradient descent optimization algorithms. *arXiv*. https://arxiv.org/abs/1609.04747

<sup>4 </sup>Haji, S. H., & Abdulazeez, A. M. (2021). Comparison of optimization techniques based on gradient descent algorithm: A review. *PalArch’s Journal of Archaeology of Egypt/Egyptology*, 18(4), 2715-2743.

<sup>5 </sup>Tian, Y., Zhang, Y., & Zhang, H. (2023). Recent Advances in Stochastic Gradient Descent in Deep Learning. *Mathematics*, 11(3), 682.

<sup>6 </sup>Beiranvand, V., Hare, W. & Lucet, Y. (2017). Best practices for comparing optimization algorithms. *Optim Eng* **18**, 815–848. https://doi.org/10.1007/s11081-017-9366-1
