---
title: What is few-shot learning?
source: https://www.ibm.com/think/topics/few-shot-learning
author: null
published: 2024-11-28
created: 2026-08-31
description: "Few-shot learning is a machine learning framework where an AI model learns to make accurate predictions by training on a very small number of labeled samples."
---

## What is few-shot learning?

Few-shot learning is a [machine learning](https://www.ibm.com/topics/machine-learning) framework in which an [AI model](https://www.ibm.com/topics/ai-model) learns to make accurate predictions by training on a very small number of labeled examples. It’s typically used to train models for classification tasks when suitable training data is scarce.

Few-shot learning (FSL) is a subset of what is sometimes referred to more generally as *n-shot learning*, a category of [artificial intelligence](https://www.ibm.com/think/topics/artificial-intelligence) that also includes *one-shot learning* (in which there is only one labeled example of each class to be learned) and *[zero-shot learning](https://www.ibm.com/think/topics/zero-shot-learning)* (in which there are no labeled examples at all). While one-shot learning is essentially just a challenging variant of FSL, zero-shot learning is a distinct learning problem that necessitates its own unique methodologies.

In principle, FSL aims to emulate the human ability to learn from a mere handful of examples. This stands in contrast to conventional [supervised learning](https://www.ibm.com/topics/supervised-learning), which typically uses many hundreds (or thousands) of labeled data points across many rounds of training to teach AI models to recognize classes of data. While powerful, supervised learning is impractical in some real-world settings: obtaining labeled examples is often difficult due to prohibitive costs, the domain-specific expertise needed to annotate data correctly or—in scenarios like unique handwriting, rare diseases or endangered and newly discovered species—the scarcity of existing samples.

While certain specific algorithms and neural network architectures have achieved notable success at FSL tasks, few-shot learning is defined by the nature of the learning problem rather than by the use of any specific method or model structure. Few-shot learning methods range widely, from adapting [pre-trained models](https://www.ibm.com/think/topics/pretrained-model) for use in similar tasks to using [generative AI](https://www.ibm.com/think/topics/generative-ai) to create new samples to *meta learning* methods that train models to generalize well to new [classification](https://www.ibm.com/think/topics/classification-machine-learning) problems and different classes of data, rather than perform any one specific task.

## How does few-shot classification work?

Though few-shot learning can utilize a wide variety of algorithms or neural network architectures, most methods are built around *transfer learning* or *meta learning* (or a combination of both).

While few-shot learning can also be applied to regression tasks (or even reinforcement learning), most FSL literature focuses on classification use cases. Some FSL methods can used alongside other solutions that address scarcity of labeled data: for example, in [semi-supervised learning](https://www.ibm.com/topics/semi-supervised-learning) methods that incorporate information from large amounts of unlabeled data alongside information from few-shot learning on the limited labeled samples available.<sup>1</sup>

### Transfer learning

Transfer learning-based methods focus on adapting a pre-trained model to learn new tasks or previously unseen classes of data.

When few labeled samples are available, using supervised learning to train a model from scratch—especially one with a large number of parameters, like the [convolutional neural networks (CNNs)](https://www.ibm.com/topics/convolutional-neural-networks) typically used in [computer vision](https://www.ibm.com/topics/computer-vision) or the transformer-based networks used in natural language processing (NLP)—often leads to [overfitting](https://www.ibm.com/topics/overfitting): the model might perform well on test data, but poorly on real-world data. But gathering a sufficiently large amount of data to avoid overfitting is often a bottleneck in model training.

Transfer learning offers a practical solution: leverage useful features and representations that a trained model has already learned. One simple approach is to *fine-tune* a classification model to perform the same task for a new class through supervised learning on a small number of labeled examples. More intricate approaches teach new skills through the design of relevant *downstream tasks*–often meta learning tasks—to a model that been pre-trained via [self-supervised *pretext tasks*](https://www.ibm.com/topics/self-supervised-learning): this is increasingly common in NLP, particularly in the context of [foundation models](https://research.ibm.com/blog/what-are-foundation-models).

More complex transfer learning approaches adapt a trained neural network via changes to the network architecture: for example, replacing or re-training the outer layers of a [neural network](https://www.ibm.com/topics/neural-networks), where final classification occurs, while maintaining the internal layers where feature extraction occurs. Freezing (or otherwise regularizing changes to) model weights for all but the outermost layers can ensure that subsequent updates don’t result in [“catastrophic forgetting”](https://research.ibm.com/publications/forget-me-not-reducing-catastrophic-forgetting-for-domain-adaptation-in-reading-comprehension) of already-learned knowledge. This allows for greatly expedited learning in a few-shot context.

Transfer learning is most successful when the model’s initial training is relevant to the new task. For example, a model trained on certain species of birds will generalize well to unseen species of birds after fine-tuning with only a few labeled samples, because the learned weights of the filters the CNN uses for convolutions are already optimized to capture features relevant to bird classification (like plumage, beaks, wing size, etc.)—but using few-shot learning to teach the same model to recognize vehicles will yield less satisfactory performance.

### Data-level approach

An alternative solution to the problem of limited labeled data samples is to generate additional training samples. This is particularly useful when real-world examples of a given class of data are exceedingly scarce, as may be the case when dealing with rare diseases or exotic species.

*Data generation*, via generative models like Generative Adversarial Networks (GANs) or [variational autoencoders (VAEs)](https://www.ibm.com/topics/autoencoder#Variational+autoencoders), can potentially yield enough samples resembling the original labeled samples to perform conventional supervised learning, provided the original samples had sufficient diversity to avoid overfitting.

*Data augmentation*, the process of creating new samples by applying different transformations to original samples, can be combined with other methods: for example, it can be used to create matching samples for use in metric meta learning in a process similar to [contrastive self-supervised learning](https://www.ibm.com/topics/self-supervised-learning).

### Meta learning

Unlike supervised learning or fine-tuning, in which a classifier is trained on the exact tasks it will be used for and the training set contains the same classes the model will be tested on, *[meta learning](https://www.ibm.com/think/topics/meta-learning)* takes a broader, more indirect approach. Whereas approaches built upon transfer learning adapt pre-trained models, meta learning methods often train systems end-to-end from scratch.

According to Santoro, et al, “meta learning” refers to scenarios in which multiple tasks are used to train a model at both a short-term and long-term level. Within each task, the model learns rapidly to make predictions relevant to the limited domain of that specific task; across tasks, the model gradually accrues knowledge by capturing the way patterns and task structure vary across target domains. This two-tiered process is often described as the model “learning to learn.” <sup>2</sup>

For example, the goal of many prominent meta learning methods is to train a model function, across multiple training episodes, to output a prediction for the degree of similarity between data points from any classes—including classes the model has not yet seen—to then use learnings from that process to solve downstream tasks (like specifically defined classification problems).

Some meta learning approaches work on a more abstract level, by training models to be easy to train. In traditional supervised learning, a model’s parameters (like weights and biases) are what’s “learned,” while the model’s [*hyper*parameters](https://www.ibm.com/think/topics/hyperparameter-tuning)—like the [learning rate](https://www.ibm.com/think/topics/learning-rate), or how parameters are initialized—are configured prior to training and not part of the learning process. Meta learning can approximate the benefits of transfer learning by learning ideal starting points: parameter initializations or other hyperparameter choices that will generalize well to different datasets in a minimal amount of training steps.

### N-way-K-shot classification

Though a wide variety of machine learning model architectures can be used for few-shot learning, the structure of FSL training and evaluation generally follows an *N-way-K-shot* framework, in which *N* represents the number of classes and *K* represents the number of examples (or “shots”) provided for each class.

In N-way-K-shot classification, the model undergoes multiple episodes of training. Each training episode consists of one or more *training tasks*. Models are evaluated via *test tasks*, whose structure mirrors that of the training tasks. Each training task (and test task) comprises two datasets:

- The **support set** contains K labeled training samples for each of the N classes. The model uses these support samples to learn generalized representations for each class. For example, the dataset for a *3-way-2-shot* classification task contains 3 classes of images and provides 2 examples of each. When *K*=1, the task is *one-shot learning*. When *K*=0, the problem is *zero-shot learning*—which typically requires unique solutions.
- The **query set** contains one or more new examples for each of the *N* classes. Using representations learned from the support set, the model predicts classification for each example in the query set. A *loss function* measures the divergence (“loss”) between the model’s predictions and the “correct” predictions; after each training episode, [model parameters](https://www.ibm.com/think/topics/model-parameters) are adjusted—optimized—to minimize loss.

Because the goal of meta-learning is to train models to generalize well to unseen data, rather than to recognize any specific classes of data, each training task typically includes different data classes than those used in any preceding training tasks.

To test the model’s ability to make accurate similarity predictions for heretofore unseen classes, the support set and query set used for testing must contain entirely new classes of data that the model has not yet been exposed to in training tasks.

![An example of a 3-way-2-shot classification task for few-shot learning, in which an algorithm is trained to distinguish images of different kinds of animals from one another](https://assets.ibm.com/is/image/ibm/ai-tasks-diagram?ts=1763387046599&dpr=off)   An example of a 3-way-2-shot classification task for few-shot learning

## Metric-based meta learning

Metric-based meta learning algorithms operate on principle similar to that of [*K-nearest neighbors*](https://www.ibm.com/topics/knn): rather than predicting classification by directly modeling the decision boundary between classes, metric-based approaches generate a continuous value (like a vector embedding) to represent a given data sample, and make inferences by learning a function that measures some *distance metric* representing the similarity between this value and the value of the different samples or classes it is being compared to.

### Metric-based FSL algorithms

#### Siamese networks

A relatively early development in metric-based algorithms, *Siamese networks* solve binary classification problems by using contrastive learning: shown two samples, Siamese networks predict whether it is positive (matching) or negative (non-matching) pair. The model’s loss function is used to minimize the distance between vector embeddings of positive pairs and maximize distance between embeddings of negative pairs. *Triplet loss* models are quite similar: given an “anchor” sample and two additional samples—one matching, one not–the model predicts which is a positive match and which is negative.

In both methods, it is important that training samples be relatively difficult to distinguish from one another—if not, the model will not be forced to learn parameters that yield more effective embeddings. Data augmentation is often used when matching samples are scarce.

#### Matching networks

Whereas Siamese networks can only solve binary classification tasks, *matching networks* can perform multi-way classification. As such, it’s considered one of the first dedicated few-shot learning algorithms.

Matching networks output an embedding for each sample in the support and query sets using an appropriate neural network (such as a CNN for image tasks or LLM for natural language tasks) and predict classification by measuring the [cosine distance](https://community.ibm.com/community/user/ai-datascience/blogs/moloy-de1/2020/06/18/points-to-ponder) between the embedding of the query sample and that of the available support samples.

#### Prototypical networks

*Prototypical networks* compute the average features of all samples available for each class in order to calculate a *prototype* for each class. Classification of a given data point is then determined by its relative proximity to the prototypes for each class. Unlike matching networks, Prototypical networks use [Euclidian distance](https://en.wikipedia.org/wiki/Euclidean_distance) rather than cosine distance.

Many refinements to this approach have been proposed: for example, Zhu and Koniusz proposed using [label propagation](https://www.ibm.com/topics/semi-supervised-learning#Transductive+learning) to improve the prototyping process.<sup>3</sup>

#### Relation networks

A *relation network* (RN) operates on the same general principal as matching and prototypical networks. RNs also utilize an embedding module that learns to compute embeddings for input images and class prototypes—but unlike those two algorithms, which pre-define the distance function used to compare embeddings, RNs add a *relation module* that learns a non-linear distance function that best suits the specific classification problems at hand.

## Optimization-based meta learning

Deep learning traditionally requires many iterative updates of model parameters through [backpropagation and gradient descent](https://www.ibm.com/topics/gradient-descent), which in turn depends on a huge quantity of labeled examples to populate training batches. To efficiently train a neural network from scratch for few-shot learning requires a way to optimize model weights in only a few update steps.

### Optimization-based FSL methods

Optimization-based meta learning approaches, also referred to as *gradient-based meta learning* (GMBL), aim to learn initial model parameters or hyperparameters for a neural network that can be efficiently fine-tuned for relevant tasks. They achieve by optimizing the process of gradient descent—that is, by *meta-optimizing* the process of optimization itself.

#### Model agnostic meta-learning (MAML)

MAML is among the most prominent optimization-based approaches, and has served as the foundation for a number of approaches derived from its core methodology. As its name suggests, model agnostic meta-learning doesn’t focus on a specific task or [AI model architecture](https://www.ibm.com/topics/ai-model): it can be used on any model that learns via gradient descent.

MAML entails two different levels of parameters updates across a set of varied FSL training tasks, *p*(*T*). In each training episode, a new task *T*<sub>i</sub> is randomly sampled from *p*(*T*); gradient descent, performed in *K* steps of size *α*, is used to optimize a vector of *task-specific* model parameters (*θ’*<sub>i</sub>) after each training task. Across multiple training episodes, a set of *meta-parameters* (***θ***) is optimized by applying gradient descent, in meta-steps of size *β*, to those task-specific parameters *θ’*<sub>i</sub>. In other words, whereas ordinary gradient descent calculates derivatives in order to optimize a model’s parameters for a given task, MAML calculates the *derivatives of the derivatives* (or “second order derivatives”) to optimize a model’s initial parameters for subsequent task-specific optimization.

Per the original paper, the goal therein is to “find model parameters that are sensitive to changes in the task, such that small changes in the parameters will produce large improvements on the loss function of any task drawn from *p*(*T*).” This yields benefits similar to those of transfer learning while circumventing the need for large amounts of labeled data for pre-training.

Proposed adaptations to MAML include:

- *First Order MAML (FOMAML)*: MAML’s reliance on second-order derivatives is computationally expensive and requires a great deal of memory. FOMAML simplifies the process via a series of assumptions that allow for meta-optimization using only first order derivatives.
- *Reptile*: Reptile presents a midway point between the sophistication of MAML and the simplicity of FOMAML: it uses first order derivatives, but implements unique rules for how parameters are updated.<sup>4  
 </sup>
- *Optimizing step size*: Variants like Meta-SGD<sup>5</sup> and Alpha MAML<sup>6</sup> add the ability to optimize step size and direction for *α* and *β*. Similarly, MAML++<sup>7</sup> introduces a number of modifications to increase stability and computational efficiency.

#### LTSM meta-learner

Meta-learning approaches can make use of RNN-based [long-short term memory (LSTM) networks](https://developer.ibm.com/tutorials/iot-deep-learning-anomaly-detection-1/) to train a meta-learner model to capture both short-term knowledge from each training task and long-term knowledge common to each task. This meta-learner is then used to train a neural network classifier.

#### Latent embedding optimization (LEO)

Rather than explicitly instantiating and updating a unique set of model meta-parameters *θ*, *latent embedding optimization* learns a generative distribution of task-specific model parameters in a manner similar to [variational autoencoders (VAEs)](https://www.ibm.com/topics/autoencoder#Variational+autoencoders), which serves the same purpose. Gradient optimization can then be performed within that learned, low-dimensional embedding space.

### Few-shot learning use cases

Few-shot learning techniques have a wide variety of applications, as many industries and research fields stand to benefit from the ability to learn quickly and effectively from relatively few examples.

While many prominent FSL algorithms were originally developed for (or proven on) image classification tasks, FSL can also be used for more complex [computer vision](https://www.ibm.com/think/topics/computer-vision) problems.

While object detection is a significantly more complex problem than image classification, as objects must be not only classified but also accurate localized, it generally takes image classification as a prerequisite. As such, many ideas used for classification can be adopted for few-shot object detection.<sup>8</sup>

Likewise, a number of model architectures have been proposed for few-shot [semantic segmentation](https://www.ibm.com/topics/image-segmentation#Semantic+segmentation).<sup>9</sup>

FSL can enable robots to quickly adapt to new environments and new tasks through both few-shot classification tasks<sup>10</sup> and reinforcement learning.<sup>11</sup>

FSL has shown promising results for [natural language processing](https://www.ibm.com/think/topics/natural-language-processing) (NLP), particularly through transfer learning: it’s an intuitive way to adapt [large language models](https://www.ibm.com/think/topics/large-language-models) (LLMs), pre-trained on a massive corpus of unlabeled data, to specific tasks like text classification and sentiment analysis that may require specific contextual understanding.

FSL’s potential to quickly acclimate a model to rare and unseen data classes is particularly promising for medical fields, in which the rarity of certain conditions or the expertise required to accurately annotate medical data (like MRIs or echocardiography) can make the acquisition of a large number of labeled samples prohibitively difficult.

## Footnotes

<sup>1</sup>  ["Realistic Evaluation of Deep Semi-Supervised Learning Algorithms"](https://arxiv.org/pdf/1804.09170.pdf) . arXiv. June 17, 2019   
 <sup>2</sup>  ["A survey on semi-supervised learning"](https://link.springer.com/article/10.1007/s10994-019-05855-6) . Springer. November 15, 2019   
 <sup>3</sup> " [Transductive active learning – A new semi-supervised learning approach based on iteratively refined generative models to capture structure in data](https://www.sciencedirect.com/science/article/abs/pii/S0020025514009050) ". Information Sciences (Volume 293). September 18, 2014   
 <sup>4</sup>  ["Semantic Segmentation with Active Semi-Supervised Learning"](https://arxiv.org/abs/2203.10730) . arXiv. October 16, 2022   
 <sup>5</sup>  ["Semi-supervised learning by Entropy Minimization"](https://papers.nips.cc/paper/2004/file/96f2b50b5d3613adf9c27049b2a888c7-Paper.pdf) . Advances in Neural Information Processing Systems 17. 2004   
 <sup>6</sup>  ["Density-based semi-supervised clustering"](https://www.researchgate.net/publication/220451675_Density-based_semi-supervised_clustering) . Data Mining and Knowledge Discovery. November 2010   
 <sup>7</sup>  ["Semi-Supervised Learning with Ladder Networks"](https://arxiv.org/abs/1507.02672) . arXiv. November 24, 2015   
 <sup>8</sup>  ["Learning with Pseudo-Ensembles"](https://arxiv.org/abs/1412.4864) . arXiv. December 16, 2014   
 <sup>9</sup>  ["Temporal Ensembling for Semi-Supervised Learning"](https://arxiv.org/abs/1610.02242) . arXiv. March 15, 2017   
 <sup>10</sup>  ["Improved Techniques for Training GANs"](https://arxiv.org/abs/1606.03498) . arXiv. June 10, 2016
