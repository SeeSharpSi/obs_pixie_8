---
title: What is stochastic gradient descent?
source: https://www.ibm.com/think/topics/stochastic-gradient-descent
author:
- '[[Anna Gutowska]]'
published: 2025-10-16
created: 2026-08-31
description: "Stochastic gradient descent (SGD) is an optimization algorithm commonly used to improve the performance of machine learning models. It is a variant of the traditional gradient descent algorithm."
---

Stochastic gradient descent (SGD) is an optimization algorithm commonly used to improve the performance of [machine learning](https://www.ibm.com/think/topics/machine-learning) models. It is a variant of the traditional [gradient descent](https://www.ibm.com/think/topics/gradient-descent) algorithm, with a key modification: instead of relying on the entire dataset to compute the gradient at each step, SGD uses a single data sample at a time.

## Gradient descent explained

[Gradient descent (GD)](https://www.ibm.com/think/topics/gradient-descent) is an optimization algorithm that iteratively minimizes an objective function. In the context of [machine learning (ML)](https://www.ibm.com/think/topics/machine-learning), gradient descent is fundamental to improving the performance of supervised learning models during their training phase. Machine learning models, like [neural networks](https://www.ibm.com/think/topics/neural-networks), are complex, nonlinear and high-dimensional. Hence, there is no normal equation for such models that can compute the optimal weights, unlike in [linear regression](https://www.ibm.com/think/topics/linear-regression). Instead, approximation methods like the variants of gradient descent, Newton’s methods and expectation maximization can be used, among others.

Every model has a [loss function](https://www.ibm.com/think/topics/loss-function), sometimes called a cost function. This function measures how far a model’s predictions are from the true data points. Think of this as a measure of how “wrong” the model’s predictions are. For example, the mean-squared error often serves as the loss function in regression problems. The [model training](https://www.ibm.com/think/topics/model-training) phase is designed to find the parameter values that minimize this loss. Gradient descent is often the optimization technique used in training for this reason. The algorithm computes the gradient, or the slope, of the loss with respect to the model’s parameters. With this gradient, it then takes a step in the opposite direction to reduce the loss. The learning rate (also referred to as step size or the alpha) is the size of the steps and it remains fixed for all [model parameters](https://www.ibm.com/think/topics/model-parameters). This process repeats until the model achieves convergence near a minimum.

![Graphical representation of convergence](https://assets.ibm.com/is/image/ibm/ICLH_Diagram_Batch_01_04-GradientDescent?ts=1772123532728&dpr=off)   Graphical representation of convergence

Convergence ideally occurs at the global minimum. In the following visualization, you can see that the loss value is lower at a local minimum than in its immediate surrounding area, but not necessarily the lowest value overall. The global minimum is the absolute lowest value of the loss function across its entire domain, representing the best possible solution for the problem.

![Local and global minimum in 3-dimensional space](https://assets.ibm.com/is/image/ibm/local-to-global-minimum?ts=1772123533012&dpr=off)   Local and global minimum in 3-dimensional space

If the learning rate is not small enough, the algorithm will often converge at a local minimum. A well-chosen rate is essential for minimizing the loss function and achieving convergence at a global minimum.

![Effect of learning rate on convergence ](https://assets.ibm.com/is/image/ibm/ICLH_Diagram_Batch_03_21-AI-ML-GradientDescent?ts=1772123533293&dpr=off)   Effect of learning rate on convergence

This visualization depicts the effect of the learning rate on convergence. A small learning rate leads to slow but stable convergence (left), while a large learning rate might cause overshooting and instability (right).

## From GD to SGD

The key differentiator between traditional gradient descent and stochastic gradient descent is that SGD updates model weights by using a single training example at a time. The example is randomly picked at each iteration.<sup>1</sup> Gradient descent uses the entire training [dataset](https://www.ibm.com/think/topics/dataset) to compute the gradient before each parameter update. This difference in data usage is what makes SGD much less computationally expensive and easier to scale for large datasets. Alternatively, the convergence behavior of SGD is noisier than the noise of GD because the one example datapoint might not be a good representation of the dataset. This misrepresentation updates the points in a slightly “wrong” direction. However, this randomness is what makes SGD faster and sometimes better for nonconvex optimization problems because it can escape shallow local minima, or saddle points.[](https://www.ibm.com/think/topics/dataset)

Strictly speaking, SGD was originally defined to update parameters by using exactly one training sample at a time. In modern usage, the term “SGD” is used loosely to mean “minibatch gradient descent,” a variant of GD in which small batches of training data are used at a time. The major advantage to using subsets of data rather than a singular sample is a lower noise level, because the gradient is equal to the average of losses from the minibatch. For this reason, minibatch gradient descent is the default in [deep learning](https://www.ibm.com/think/topics/deep-learning). Contrarily, strict SGD is rarely used in practice. These terms are even conflated by most [machine learning libraries](https://www.ibm.com/think/topics/machine-learning-libraries) such as [PyTorch](https://www.ibm.com/think/topics/pytorch) and TensorFlow; optimizers are often called “SGD,” even though they typically use minibatches.

The following illustration provides a clearer depiction of how increasing the sample size of training data reduces oscillations and “noise.”

![Variants of gradient descent](https://assets.ibm.com/is/image/ibm/gradient-descent-variants?ts=1772123533866&dpr=off)

There are several other variants of GD that are built on basic gradient descent by adding mechanisms to improve speed, stability and convergence.

### Momentum-based methods:

By accumulating momentum in dimensions with consistent gradients and dampening updates in dimensions with changing gradients, momentum helps SGD converge faster and with less oscillation.<sup>2</sup>

![SGD with and without momentum](https://assets.ibm.com/is/image/ibm/sgd-with-and-without-momentum?ts=1772123534330&dpr=off)

- **Momentum gradient descent**: Incorporates a “velocity” term, an average of previous gradients that gives more importance to recent ones. This approach reduces zigzagging, or oscillations, helping the algorithm move faster in the right direction.
- **NAG (Nesterov accelerated gradient)**: An improved momentum method that speeds up and smooths convergence by “looking ahead” at where the parameters are headed before computing the gradient. In other words, it anticipates the future gradient and uses this information to inform the current update step.<sup>3</sup>

### Adaptive learning rate methods:

Adaptive learning rate methods, such as AdaGrad and RMSProp, are unique in that they adapt the learning rate for each parameter individually. This approach is in contrast to SGD methods, which use a fixed learning rate for all parameters.

- **AdaGrad (adaptive gradient algorithm)**: Adapts the learning rate for each parameter based on its previous gradients. Features that appear less often receive higher learning rates, and frequent features receive lower rates. This approach means that infrequent features are learned quicker than with SGD. This adaptive learning rate means it is a great method for [natural language processing (NLP)](https://www.ibm.com/think/topics/natural-language-processing) and recommendation systems with sparse data, in which there is a large discrepancy in feature frequency.<sup>2  
 </sup>
- **RMSProp (Root Mean Square Propagation)**: Another adaptive learning rate optimization technique that scales the learning rate for each parameter by using a moving average of recent squared gradients. Past gradient knowledge is discarded and only current gradient knowledge is preserved<sup>.4 </sup>The learning rate becomes larger for parameters with small gradients and smaller for those with large gradients. This method eliminates the diminishing learning rate problem with AdaGrad. RMSProp helps keep training stable in deep learning, especially for models like recurrent neural networks (RNNs), and it works well on problems where the objective keeps changing, such as in [reinforcement learning](https://www.ibm.com/think/topics/reinforcement-learning).

### Hybrid methods:

- **Adam (adaptive moment estimation)**: Combines momentum-based GD with RMSProp by tracking both the past gradients and the average of squared gradients.<sup>4 </sup>This combination allows for a fast convergence rate even for noisy and sparse datasets.<sup>3</sup> Additionally, the default [hyperparameters](https://www.ibm.com/think/topics/hyperparameter-tuning) like a learning rate of 0.001 in many frameworks, work well right away. For very large-scale datasets, however, SGD with momentum can lead to better generalization. The aggressive per-parameter adjustments of Adam can result in overfitting of the training data or settling into sharp minima that don’t generalize as well.

SGD and other GD variants are useful when training time is the bottleneck.<sup>5</sup>

| Variant | Data used per step | Key feature | Common use |
| --- | --- | --- | --- |
| GD | All data | Stable but slow | Small datasets |
| SGD | 1 sample for classic SGD | Noisy but fast | Online learning |
| Mini-Batch GD | Few samples | Balanced and scalable | Deep learning |
| Momentum | Batch/mini-batch | Accelerates in right direction | Neural nets |
| NAG | Batch/mini-batch | Look-ahead momentum | Faster convergence |
| AdaGrad | Mini-batch | Adaptive learning rates | Sparse data |
| RMSProp | Mini-batch | Fixes AdaGrad decay | RNNs, deep nets |
| Adam | Mini-batch | Momentum + RMSProp | Default choice today |

## Understanding the math

The goal of SGD is to find parameters $\theta$ that make our model’s predictions as close as possible to the true values $y$ . In other words, we want to minimize the loss function, $L(\theta)$ .

In the case of linear regression, those parameters are $w$ (weight) and $b$ (bias). So in this case, minimizing $L(\theta)$ is the same as minimizing $L(w,b)$ .

$$ \hat{y_i} = w \cdot x_i + b $$

$$ L(w,b) = \frac{1}{n}\sum_{i=1}^{n} \left(y_i-\hat{y_i}\right)^2 $$

A commonly used analogy when teaching gradient descent is that GD is like walking downhill on a mountain until you reach a valley (the minimum loss). Envision the gradient of the loss function,

$\nabla L$ , points uphill and to go downhill, we must step in the opposite direction.

The general update rule for a parameter $\theta$ is:

$$ \theta := \theta - \eta \cdot \nabla_\theta L(\theta) $$

where $\eta$ is the learning rate and $\nabla_\theta L(\theta)$ is the gradient of the loss with respect to $\theta$ .

SGD uses just one randomly chosen sample $(x_i,y_i)$ to approximate the gradient:

$$ \nabla_\theta L(\theta) \approx \nabla_\theta \ell(x_i,y_i;\theta) $$

Note, lowercase $\ell(x_i,y_i;\theta)$ represents the loss of a single training example. Whereas uppercase $L(\theta)$ is the overall loss function (the average of all individual losses across the dataset). This global error is what we’re really trying to minimize in training.

### Example: Linear regression with SGD

Let’s finish walking through the example of linear regression with SGD.

For one sample $(x_i,y_i)$ , the prediction is:

$$ \hat{y_i} = w \cdot x_i + b $$

The local loss is the squared error for one sample:

$$ \ell(x_i,y_i;w,b) = \left(y_i - \left(wx_i +b\right)\right)^2 $$

Now during [backpropagation](https://www.ibm.com/think/topics/backpropagation), the model’s parameters are updated by using the chain rule that computes the gradients of the loss function with respect to each parameter.<sup>5</sup> The gradients (derivates) are:

$$ \frac{\partial \ell}{\partial w}=-2x_i(y_i-(wx_i+b)) $$

$$ \frac{\partial \ell}{\partial b}=-2(y_i-(wx_i+b)) $$

With SGD, we update each of these parameters, $w$ and $b$ , by using the following rules:

$$ w:= w-\eta \cdot (-2x_i(y_i-(wx_i+b))) $$

$$ b := b - \eta \cdot (-2(y_i-(wx_i+b))) $$

Instead of calculating a heavy average gradient across the entire dataset, SGD uses a lightweight random estimate.

## Simple Python implementation of SGD

When working with machine learning frameworks, there are built-in SGD optimizer classes one can use. For example, `torch.optim.SGD` for [PyTorch](https://www.ibm.com/think/topics/pytorch), `tf.keras.optimizers.SGD` for Keras built into TensorFlow, and `SGDRegressor` for [Scikit-learn](https://www.ibm.com/think/topics/scikit-learn).

For learning purposes, let’s walk through a simple Python implementation of SGD from scratch.

To reiterate, our objective is to find the best parameters (model weights) that minimize the loss function (a measure of how wrong our predictions are). We will update one sample at a time or a very small batch size.

To start, we can initialize the parameter values (weights) randomly. Next, we can select a random data point $(x,y)$ . From there, we compute the prediction and the error. For this simple demonstration, let’s try to fit a simple line: $y=mx+b$ . The next step in the process is [backpropagation](https://www.ibm.com/think/topics/backpropagation), in which the gradients of the loss function are computed with respect to the parameters. These gradients (derivatives) are then used to update the parameters during the SGD optimization process. Because the gradient points to the direction of increase of the loss function, SGD subtracts each gradient from its respective current parameter value. We can think of this as moving in the opposite direction of the gradient to decrease the loss function. Hence, the “descent” in stochastic gradient descent. We repeat these steps until a fixed number of epochs or once the loss is less than the tolerance. The latter would mean that the loss is hardly changing and no longer are we improving the objective function. In other words, we stop once the algorithm converges.

`import numpy as np   

 def stochastic_gradient_descent(X, y, lr=0.01, epochs=100, tol=1e-6):   
 “””   
 Perform Stochastic Gradient Descent (SGD) to fit a line y = w*x + b   

 Parameters:   
 X (ndarray): Input features   
 y (ndarray): Target values   
 lr (float): Learning rate (step size for updates)   
 epochs (int): Number of iterations through the dataset   

 Returns:   
 w (float): Learned weight   
 b (float): Learned bias   
 “””   
 # Initialize parameters randomly   
 w = np.random.randn()   
 b = np.random.randn()   

 n = len(X)   

 prev_loss = float(‘inf’)   

 for epoch in range(epochs):   
 # Shuffle the data for each epoch   
 indices = np.arange(n)   
 np.random.shuffle(indices)   

 for i in indices:   
 xi = X[i]   
 yi = y[i]   

 # Prediction   
 y_pred = w * xi + b   

 # Compute gradients (derivatives)   
 dw = -2 * xi * (yi - y_pred) # derivative wrt w   
 db = -2 * (yi - y_pred) # derivative wrt b   

 # Update parameters   
 w -= lr * dw   
 b -= lr * db   

 # Compute loss at the end of the epoch   
 loss = np.mean((y - (w*X + b))**2)   

 # Check stopping condition   
 if abs(prev_loss - loss) < tol:   
 print(f”Stopped early at epoch {epoch+1}”)   
 break   

 prev_loss = loss   

 return w, b`

## Applications of SGD

SGD is the most common optimization method for training deep [neural networks](https://www.ibm.com/think/topics/neural-networks). In [deep learning](https://www.ibm.com/think/topics/deep-learning), a subset of machine learning within the broader field of [data science](https://www.ibm.com/think/topics/data-science), the objective is for computers to simulate the complex decision-making power of the human brain. Traditional ML models use simple neural networks consisting of one or two layers. Whereas deep learning models use three or more layers. Typically, hundreds or thousands of layers are needed to train the models. Given SGD’s ease to scale for large training sets, it is often the go-to approach for training deep neural networks. Other applications of SGD training include [ridge regression](https://www.ibm.com/think/topics/ridge-regression), regularized [logistic regression](https://www.ibm.com/think/topics/logistic-regression) and the optimization of the hinge loss function used in [support vector machines (SVMs)](https://www.ibm.com/think/topics/support-vector-machine) with a linear kernel.

## Conclusion

SGD is a variant of GD that minimizes a machine learning model’s loss function by using a single data sample at a time. This approach is unlike GD, which depends on the entire dataset at each step to compute the gradient. There are several other GD variants that can be grouped as momentum-based or adaptive learning methods. Momentum gradient descent and Nesterov accelerated gradient are examples of the former. These methods leverage accumulated momentum in dimensions with consistent gradients and dampen updates in dimensions with changing gradients. Thus, helping SGD converge faster and with less oscillation. Adaptive learning rate methods such as AdaGrad and RMSProp adapt the learning rate for each parameter individually, unlike traditional SGD, which uses a fixed learning rate. In addition, hybrid methods like Adam offer a powerful alternative by combining the strengths of momentum-based GD and RMSProp.

## Footnotes

<sup>1 </sup>Bottou, L. (2010). [Large-Scale Machine Learning with Stochastic Gradient Descent](https://link.springer.com/chapter/10.1007/978-3-7908-2604-3_16). *Lechevallier, Y., Saporta, G. (eds) Proceedings of COMPSTAT’2010.* Physica-Verlag HD.

<sup>2 </sup>Ruder, S. (2016). [An overview of gradient descent optimization algorithms](https://arxiv.org/abs/1609.04747).

<sup>3 </sup>Tian, Y., Zhang, Y., & Zhang, H. (2023). [Recent Advances in Stochastic Gradient Descent in Deep Learning](https://www.mdpi.com/2227-7390/11/3/682). *Mathematics, 11*(3), 682.

<sup>4 </sup>Haji, S. H., & Abdulazeez, A. M. (2021). Comparison of optimization techniques based on gradient descent algorithm: A review. *PalArch’s Journal of Archaeology of Egypt/Egyptology*, 18(4), 2715-2743.

<sup>5 </sup>Bottou, L. (2012). [Stochastic Gradient Descent Tricks](https://link.springer.com/chapter/10.1007/978-3-642-35289-8_25). *Montavon, G., Orr, G.B., Müller, KR. (eds) Neural Networks: Tricks of the Trade*. Lecture Notes in Computer Science, vol 7700. Springer, Berlin, Heidelberg.
