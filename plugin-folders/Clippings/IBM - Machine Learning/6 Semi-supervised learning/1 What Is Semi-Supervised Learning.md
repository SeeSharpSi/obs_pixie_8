---
title: What is semi-supervised learning?
source: https://www.ibm.com/think/topics/semi-supervised-learning
author:
- '[[Dave Bergmann]]'
published: 2024-12-16
created: 2026-08-31
description: "Semi-supervised learning is a type of machine learning that combines supervised and unsupervised learning by using labeled and unlabeled data to train AI models."
---

## What is semi-supervised learning?

Semi-supervised learning is a branch of [machine learning](https://www.ibm.com/think/topics/machine-learning) that combines [supervised](https://www.ibm.com/think/topics/supervised-learning) and [unsupervised learning](https://www.ibm.com/think/topics/unsupervised-learning) by using both labeled and unlabeled data to train [artificial intelligence (AI) models](https://www.ibm.com/think/topics/ai-model) for classification and regression tasks.

Though semi-supervised learning is generally employed for the same use cases in which one might otherwise use supervised learning methods, it’s distinguished by various techniques that incorporate unlabeled data into model training, in addition to the labeled data required for conventional supervised learning.

Semi-supervised learning methods are especially relevant in situations where obtaining a sufficient amount of labeled data is prohibitively difficult or expensive, but large amounts of unlabeled data are relatively easy to acquire. In such scenarios, neither fully supervised nor unsupervised learning methods will provide adequate solutions.

### Labeled data and machine learning

Training AI models for prediction tasks like classification or regression typically requires *labeled data*: annotated data points that provide necessary context and demonstrate the correct predictions (output) for each sample input. During training, a *loss function* measures the difference (loss) between the model’s predictions for a given input and the “ground truth” provided by that input’s label. Models *learn* from these labeled examples by using techniques like [gradient descent](https://www.ibm.com/think/topics/gradient-descent) that update model weights to minimize loss. Because this machine learning process actively involves humans, it is called “supervised” learning.

Properly labeling data becomes increasingly labor-intensive for complex AI tasks. For example, to train an image classification model to differentiate between cars and motorcycles, hundreds (if not thousands) of training images must be labeled “car” or “motorcycle”; for a more detailed [computer vision](https://www.ibm.com/think/topics/computer-vision) task, like [object detection](https://www.ibm.com/docs/en/masv-and-l/maximo-vi/cd?topic=scenarios-scenario-detecting-objects-in-videos), humans must not only annotate the object(s) each image contains, but where each object is located; for even more detailed tasks, like [image segmentation](https://www.ibm.com/think/topics/image-segmentation), data labels must annotate *specific pixel-by-pixel boundaries* of different image segments for each image.

Labeling data can thus be particularly tedious for certain use cases. In more specialized machine learning use cases, like drug discovery, genetic sequencing or protein classification, data annotation is not only extremely time-consuming, but also requires very specific domain expertise.

Semi-supervised learning offers a way to extract maximum benefit from a scarce amount of labeled data while also making use of relatively abundant unlabeled data.

## Semi-supervised learning vs. supervised learning vs. unsupervised learning

Semi-supervised learning can be thought of as a hybrid of or middle ground between supervised learning and unsupervised learning.

### Semi-supervised learning vs supervised learning

The primary distinction between semi- and fully supervised machine learning is that the latter can only be trained using fully labeled datasets, whereas the former uses both labeled and unlabeled data samples in the training process. Semi-supervised learning techniques modify or supplement a supervised algorithm—called the “base learner,” in this context—to incorporate information from unlabeled examples. Labeled data points are used to ground the base learner’s predictions and add structure (like how many classes exist and the basic characteristics of each) to the learning problem.

The goal in training any classification model is for it to learn an accurate *decision boundary*: a line*—*or, for data with more than two dimensions, a “surface” or hyperplane—separates data points of one classification category from data points belonging to a different classification category. Though a fully supervised classification model can technically learn *a* decision boundary using only a few labeled data points, it might not generalize well to real-world examples, making the model's predictions unreliable.

The classic “half-moons” dataset visualizes the shortcomings of supervised models relying on too few labeled data points. Though the “correct” decision boundary would separate each of the two half-moons, a supervised learning model is likely to [overfit](https://www.ibm.com/think/topics/overfitting) the few labeled data points available. The unlabeled data points clearly convey helpful context, but a traditional supervised algorithm cannot process unlabeled data.

![Two graphs showing different results from supervised and semi-supervised learning](https://assets.ibm.com/is/image/ibm/semi-supervised-vs-supervised-half-moon?ts=1772488172225&dpr=off)   Using only the very limited labeled data points available, a supervised model may learn a decision boundary that will generalize poorly and be prone to misclassifying new examples.

### Semi-supervised learning vs unsupervised learning

Unlike semi-supervised (and fully supervised) learning, unsupervised learning algorithms use neither labeled data nor loss functions. Unsupervised learning eschews any “ground truth” context against which model accuracy can be measured and optimized.

An increasingly common semi-supervised approach, particularly for large language models, is to “pre-train” models via unsupervised tasks that require the model to learn meaningful representations of unlabeled data sets. When such tasks involve a “ground truth” and loss function (*without* manual data annotation), they’re called [self-supervised learning](https://www.ibm.com/think/topics/self-supervised-learning). After subsequent “supervised fine tuning” on a small amount of labeled data, pre-trained models can often achieve performance comparable to fully supervised models.

While unsupervised learning methods can be useful in many scenarios, that lack of context can make them ill-suited to classification on their own. Take, for example, how a typical [clustering](https://www.ibm.com/docs/en/spss-modeler/18.4.0?topic=nodes-clustering-models) algorithm—grouping data points into a pre-determined number of clusters based on their proximity to one another—would treat the half-moon dataset.

![Two graphs showing different results from unsupervised and semi-supervised learning](https://assets.ibm.com/is/image/ibm/semi-supervised-vs-unsupervised?ts=1772488172604&dpr=off)   A typical unsupervised algorithm, k-means clustering, might incorrectly group data points together based only on their relative closeness to "average" datapoints (centroids).

### Semi-supervised learning vs self-supervised learning

Both semi- and [self-supervised learning](https://www.ibm.com/think/topics/self-supervised-learning) aim to circumvent the need for large amounts of labeled data—but whereas semi-supervised learning involves *some* labeled data, self-supervised learning methods like [autoencoders](https://www.ibm.com/think/topics/autoencoder) are truly unsupervised.

While supervised (and semi-supervised) learning requires an external “ground truth,” in the form of labeled data, self-supervised learning tasks derive the ground truth from the underlying structure of unlabeled samples. Many self-supervised tasks are not useful unto themselves: their utility lies in teaching models data representations useful for the purposes of subsequent “downstream tasks.” As such, they are often called “pretext tasks.”

When combined with supervised downstream tasks, self-supervised pretext tasks thus comprise part of a semi-supervised learning process: a learning method using both labeled and unlabeled data for model training.

## How does semi-supervised learning work?

Semi-supervised learning relies on certain assumptions about the unlabeled data used to train the model and the way data points from different classes relate to one another.

A necessary condition of semi-supervised learning (SSL) is that the unlabeled examples used in model training must be relevant to the task the model is being trained to perform. In more formal terms, SSL requires that the distribution *p(x)* of the input data must contain information about the posterior distribution *p(y|x)—*that is, the conditional probability of a given data point (*x*) belonging to a certain class (*y*). So, for example, if one is using unlabeled data to help train an image classifier to differentiate between pictures of cats and pictures of dogs, the training dataset should contain images of both cats and dogs—and images of horses and motorcycles will not be helpful.

Accordantly, while a 2018 study of semi-supervised learning algorithms found that “increasing the amount of unlabeled data tends to improve the performance of SSL techniques,” it also found that “adding unlabeled data from a mismatched set of classes can actually *hurt* performance compared to not using any unlabeled data at all."<sup> 1</sup>[](#_ftn1)

The basic condition of *p(x)* having a meaningful relationship to *p(x|y)* gives rise to multiple **assumptions** about the nature of that relationship. These assumptions are the driving force behind most, if not all, SSL methods: generally speaking, any semi-supervised learning algorithm relies on one or more of the following assumptions being explicitly or implicitly satisfied.

### Cluster assumption

The *cluster assumption* states that data points belonging to the same *cluster–*a set of data points more similar to each other than they are to other available data points–will also belong to the same class.

Though sometimes considered to be its own independent assumption, the clustering assumption has also been described by van Engelen and Hoos as “a generalization of the other assumptions."<sup>2</sup>[](#_ftn1) In this view, the determination of data point clusters depends on which notion of similarity is being used: the smoothness assumption, low-density assumption and manifold assumption each simply leverage a different definition of what comprises a “similar” data point.

### Smoothness assumption

The *smoothness assumptions* states that if two data points, *x* and *x’*, are close to each other in the input space—the set of all possible values for *x*–then their labels, *y* and *y’*, should be the same.

This assumption, also known as the *continuity assumption*, is common to most supervised learning: for example, classifiers learn a meaningful approximation (or “representation”) of each relevant class during training; once trained, they determine the classification of new data points via which representation they most closely resemble.

In the context of SSL, the smoothness assumption has the added benefit of being applied *transitively* to unlabeled data. Consider a scenario involving three data points:

- a labeled data point, ***x*<sub>1</sub>**
- an unlabeled data point, ***x*<sub>2</sub>***,* that’s close to ***x*<sub>1</sub>**
- another unlabeled data point, ***x*<sub>3</sub>**, that’s close to ***x*<sub>2</sub>** but not close to ***x*<sub>1</sub>**

The smoothness assumption tells us that *x*<sub>2</sub> should have the same label as *x*<sub>1</sub>. It also tells us that *x*<sub>3</sub> should have the same label as *x*<sub>2</sub>. Therefore, we can assume that *all three* data points have the same label, because *x*<sub>1</sub>’s label is transitively propagated to *x*<sub>3</sub> because of *x*<sub>3</sub>’s proximity to *x*<sub>2</sub>.

### Low-density assumption

The *low-density assumption* states that the decision boundary between classes should not pass through high-density regions. Put another way, the decision boundary should lie in an area that contains few data points.

The low-density assumption could thus be thought of as an extension of the cluster assumption (in that a high-density cluster of data points represents a class, rather than the boundary between classes) and the smoothness assumption (in that if multiple data points are near each other, they should share a label, and thus fall on the same side of the decision boundary).

This diagram illustrates how the smoothness and low-density assumptions can inform a far more intuitive decision boundary than would be possible with supervised methods that can only consider the (very few) labeled data points.

![A diagram displaying the smoothness assumption and low-density assumption in semi-supervised learning](https://assets.ibm.com/is/image/ibm/supervised-vs-optimal-decision-boundary?ts=1772488173947&dpr=off)   Source: van Engelen, et al (2018)

### Manifold assumption

The *manifold assumption* states that the higher-dimensional input space comprises multiple lower dimensional manifolds on which all data points lie, and that data points on the same manifold share the same label.

For an intuitive example, consider a piece of paper crumpled up into a ball. The location of any points on the spherical surface can only mapped with three-dimensional *x,y,z* coordinates. But if that crumpled up ball is now flattened back into a sheet of paper, those same points can now be mapped with two-dimensional *x,y* coordinates. This is called *dimensionality reduction*, and it can be achieved mathematically using methods like autoencoders or [convolutions](https://developer.ibm.com/articles/introduction-to-convolutional-neural-networks/).

In machine learning, dimensions correspond not to the familiar *physical* dimensions, but to each attribute or feature of data. For example, in machine learning, a small RGB image measuring 32x32 pixels has *3,072* dimensions: 1,024 pixels, each of which has three values (for red, green and blue). Comparing data points with so many dimensions is challenging, both because of the complexity and computational resources required and because most of that high-dimensional space does not contain information meaningful to the task at hand.

The manifold assumption holds that when a model learns the proper dimensionality reduction function to discard irrelevant information, disparate data points converge to a more meaningful representation for which the other SSL assumptions are more reliable.

![A diagram showing the manifold assumption in semi-supervised learning](https://assets.ibm.com/is/image/ibm/semi-supervised-manifold?ts=1772488174310&dpr=off)   Mapping the data points to a lower-dimensional manifold can provide a more accurate decision boundary, which can then be translated back to higher-dimensional space. (source: van Engelen, et al, 2018)

## Transductive learning

Transductive learning methods use available labels to discern label predictions for a given set of unlabeled data points, so that they can be used by a supervised base learner.

Whereas *inductive* methods aim to train a classifier that can model the entire (labeled and unlabeled) input space, transductive methods aim only to yield label predictions for unlabeled data. The algorithms used for transductive learning are largely unrelated to the algorithm(s) to be used by the supervised classifier model to be trained using this newly labeled data.

### Label propagation

Label propagation is a graph-based algorithm that computes label assignments for unlabeled data points based on their relative proximity to labeled data points, using the smoothness assumption and cluster assumption.

The intuition behind the algorithm is that one can map a fully connected graph in which the nodes are all available data points, both labeled and unlabeled. The closer two nodes are based on some chosen measure of distance, like [Euclidian distance](https://en.wikipedia.org/wiki/Euclidean_distance), the more heavily the edge between them is weighted in the algorithm. Starting from the labeled data points, labels then iteratively *propagate* through neighboring unlabeled data points, using the smoothness and cluster assumptions.

![A diagram demonstrating label propagation for semi-supervised learning](https://assets.ibm.com/is/image/ibm/semi-supervised-label-propagation?ts=1772488175069&dpr=off)   LEFT: original labeled and unlabeled data points. RIGHT: using label propagation, the unlabeled data points have been assigned pseudo-labels.

### Active learning

Active learning algorithms do not automate the labeling of data points: instead, they are used in SSL to determine which unlabeled samples would provide the most helpful information if manually labeled.<sup>3</sup>[](#_ftn1) The use of active learning in semi-supervised settings has achieved promising results: for example, a recent study found that it more than halved the amount of labeled data required to effectively train a model for [semantic segmentation](https://www.ibm.com/think/topics/image-segmentation).<sup>4</sup>[](#_ftn2)[](#_ftn2)

## Inductive learning

Inductive methods of semi-supervised learning aim to directly train a classification (or regression) model, using both labeled and unlabeled data.

Inductive SSL methods can generally be differentiated by the way in which they incorporate unlabeled data: via a pseudo-labeling step, an unsupervised pre-processing step, or by direct incorporation into the model’s objective function.

### Wrapper methods

A relatively simple way to extend existing supervised algorithms to a semi-supervised setting is to first train the model on the available labeled data—or simply use a suitable pre-existing classifier—and then generate *pseudo-label* predictions for unlabeled data points. The model can then be re-trained using both the originally labeled data and the pseudo-labeled data, not differentiating between the two.

The primary benefit of wrapper methods, beyond their simplicity, is that they are compatible with nearly any type of supervised base learner. Most wrapper methods introduce some regularization techniques to reduce the risk of reinforcing potentially inaccurate pseudo-label predictions.

#### Self-training

Self-training is a basic wrapper method. It requires *probabilistic*, rather than deterministic, pseudo-label predictions: for example, a model that outputs “85 percent dog, 15 percent cat” instead of simply outputting “dog.”

Probabilistic pseudo-label predictions allow self-training algorithms to accept only predictions that exceed a certain confidence threshold, in a process akin to entropy minimization.<sup>5</sup> This process can be done iteratively, to either optimize the pseudo-classification process or reach a certain number of pseudo-labeled samples.

#### Co-training

Co-training methods extend the self-training concept by training *multiple* supervised base learners to assign pseudo-labels.

The diversification is intended to reduce the tendency to reinforce poor initial predictions. It’s therefore important that the predictions of each base learner not be strongly correlated with one another. A typical approach is to use different algorithms for each classifier. Another is for each classifier to focus on a different subset of the data: for example, in video data, training one base learner on visual data and the other on audio data.

### Unsupervised pre-processing

Unlike wrapper methods (and intrinsically semi-supervised algorithms), which use labeled and unlabeled data simultaneously, some SSL methods use unlabeled and labeled data in separate stages: an unsupervised pre-processing stage, followed by a supervised stage.

Like wrapper methods, such techniques can essentially be used for any supervised base learner. But in contrast to wrapper methods, the “main” supervised model is ultimately trained only on originally (human-annotated) labeled data points.

Such pre-processing techniques range from extracting useful features from unlabeled data to pre-clustering unlabeled data points to using “pre-training” to determine the initial parameters of a supervised model (in a process akin to the pretext tasks performed in [self-supervised learning](https://www.ibm.com/think/topics/self-supervised-learning)).

#### Cluster-then-label

One straightforward semi-supervised technique involves clustering all data points (both labeled and unlabeled) using an unsupervised algorithm. Leveraging the clustering assumption, those clusters can be used to help train an independent classifier model—or, if the labeled data points in a given cluster are all of the same class, pseudo-labeling the unlabeled data points and proceeding in a manner similar to wrapper methods.

As demonstrated by the “half-moons” example earlier in this article, simple methods (like k-nearest neighbors) may yield inadequate predictions. More refined clustering algorithms, like DBSCAN (which implements the low-density assumption),<sup>6</sup> have achieved greater reliability.

#### Pre-training and feature extraction

Unsupervised (or self-supervised) pre-training allows models to learn useful representations of the input space, reducing the amount of labeled data needed to fine tune a model with supervised learning.

A common approach is to employ a neural network, often an [autoencoder](https://www.ibm.com/think/topics/autoencoder), to learn an embedding or feature representation of the input data—then using these learned features to train a supervised base learner. This often entails dimensionality reduction, helping to make use of the manifold assumption.

### Intrinsically semi-supervised methods

Some SSL methods directly unlabeled data into the objective function of the base learner, rather than processing unlabeled data in a separate pseudo-labeling or pre-processing step.

#### Semi-supervised support vector machines

When data points of different categories are not linearly separable–when no straight line can neatly, accurately define the boundary between categories—[support vector machine (SVMs)](https://www.ibm.com/docs/en/spss-modeler/saas?topic=models-how-svm-works) algorithms map data to a higher-dimensional feature space in which the categories can be separated by a hyperplan*e*. In determining this decision boundary, SVM algorithms maximize the *margin* between the decision boundary and the data points closest to it. This, in practice, applies the *low-density assumption.*

In a supervised setting, a regularization term penalizes the algorithm when labeled data points falls on the wrong side of the decision boundary. In semi-supervised SVMs (S3VMs), this isn’t possible for unlabeled data points (whose classification is unknown)—thus, S3VMs also penalize data points that lie within the prescribed margin.

#### Intrinsically semi-supervised deep learning models

A variety of neural network architectures have been adapted for semi-supervised learning. This is achieved by adding or modifying the loss terms typically used in these architectures, allowing for the incorporation of unlabeled data points in training.

Proposed semi-supervised deep learning architectures include ladder networks,<sup>7</sup> pseudo-ensembles,<sup>8</sup> temporal ensembling,<sup>9</sup> and select modifications to generative adversarial networks (GANS).<sup>10</sup>

## Footnotes

<sup>1</sup> [“Realistic Evaluation of Deep Semi-Supervised Learning Algorithms”](https://arxiv.org/pdf/1804.09170.pdf). arXiv. June 17, 2019.  
 <sup>2</sup> [“A survey on semi-supervised learning”](https://link.springer.com/article/10.1007/s10994-019-05855-6) . Springer. November 15, 2019.  
 <sup>3</sup> “[Transductive active learning – A new semi-supervised learning approach based on iteratively refined generative models to capture structure in data”](https://www.sciencedirect.com/science/article/abs/pii/S0020025514009050). Information Sciences (volume 293). September 18, 2014.  
 <sup>4</sup> [“Semantic Segmentation with Active Semi-Supervised Learning”](https://arxiv.org/abs/2203.10730). arXiv. October 16, 2022.  
 <sup>5</sup> [“Semi-supervised learning by Entropy Minimization”](https://papers.nips.cc/paper/2004/file/96f2b50b5d3613adf9c27049b2a888c7-Paper.pdf). Advances in Neural Information Processing Systems 17. 2004.  
 <sup>6</sup> [“Density-based semi-supervised clustering”](https://www.researchgate.net/publication/220451675_Density-based_semi-supervised_clustering). Data Mining and Knowledge Discovery. November 2010.  
 <sup>7</sup> [“Semi-Supervised Learning with Ladder Networks”](https://arxiv.org/abs/1507.02672) . arXiv. November 24, 2015.  
 <sup>8</sup> [“Learning with Pseudo-Ensembles”](https://arxiv.org/abs/1412.4864) . arXiv. December 16, 2014.  
 <sup>9</sup> [“Temporal Ensembling for Semi-Supervised Learning”](https://arxiv.org/abs/1610.02242) . arXiv. March 15, 2017.  
 <sup>10</sup> [“Improved Techniques for Training GANs”](https://arxiv.org/abs/1606.03498). arXiv. June 10, 2016.
