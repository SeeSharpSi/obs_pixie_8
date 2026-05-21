---
title: What Are Machine Learning Algorithms?
source: https://www.ibm.com/think/topics/machine-learning-algorithms#7281537
author:
  - "[[Dave Bergmann]]"
published: 2019-11-18
created: 2026-05-21
description: A machine learning algorithm is the procedure and mathematical logic through which an AI model learns patterns in training data and applies to them to new data.
tags:
  - clippings
---
## Think Newsletter

## Author

Senior Staff Writer, AI Models

IBM Think

A machine learning algorithm is the procedure and mathematical logic through which a “machine”—an [artificial intelligence](https://www.ibm.com/think/topics/artificial-intelligence) (AI) system—learns to identify patterns in training data and apply that pattern recognition to make accurate predictions on new data. [Machine learning](https://www.ibm.com/think/topics/machine-learning) algorithms are the fundamental building blocks of modern AI and [data science](https://www.ibm.com/think/topics/data-science), from simple [linear regression](https://www.ibm.com/think/topics/linear-regression) models to cutting edge deep learning techniques.

The terms “algorithm” and “model” are often used interchangeably, but represent distinct (albeit related) concepts. *Algorithm* is a generic term for a step-by-step process, usually described in mathematical language or [pseudocode](https://www.ibm.com/docs/en/taw/1.3.0?topic=filters-filter-multiple-levels-shown-as-pseudocode), to perform some function or purpose. In the context of artificial intelligence, an [*AI model*](https://www.ibm.com/think/topics/ai-model) is any program that receives input data and outputs a prediction or decision without further human intervention.

A *machine learning algorithm* is a defined set of steps used to [train a machine learning model](https://www.ibm.com/think/topics/model-training) so that it can make useful predictions in its real-world use case. It comprises not only the way the model maps an input data point to its corresponding output, but also the process of optimizing the model’s predictions to “fit” a training dataset of relevant examples. It’s an *algorithm* that enables a *machine* to *learn* from data*.*

In straightforward terms, the outcome of applying a machine learning algorithm to a dataset is a trained model. “Training” can be understood as an iterative process of updating the [model’s parameters](https://www.ibm.com/think/topics/model-parameters) —the adjustable aspects of the mathematical logic the model uses to make predictions or decisions about input data—in a way that yields more useful outputs.

Though there exist machine learning (ML) algorithms designed explicitly for training models to perform a single specific task, that’s an exception rather than a rule. Generally speaking, each ML algorithm has particular mathematical or practical qualities that are useful for certain *types* of tasks (or certain types or quantities of data). In many cases, the same machine learning technique can be used to train models for multiple (albeit similar) tasks. Conversely, there are almost always multiple ML algorithms well suited to training a model for any given task.

The central benefit of ML algorithms is that they enable AI models to learn *implicitly* from experience. This is in contrast to “classic” or “rules-based” AI techniques, which require a data scientist, subject matter expert or ML engineer to manually and explicitly program the model’s decision-making logic. Over the past few decades, machine learning systems have emerged as the dominant mode of artificial intelligence and data analysis over rules-based AI because, among other reasons, implicit data-driven machine learning is inherently more flexible, scalable and accessible.

Having said that, it’s essential to note that fitting a model to its training data is merely a means to an end. The fundamental premise of machine learning is that if you optimize a model’s performance on sample tasks that adequately resemble the real-world problems it will be used for, the trained model will also perform well on *new* data it hasn’t seen in training. The ultimate goal of machine learning is *generalization,* the translation of performance on training data to new, unseen data. A myopic focus on training unto itself risks [overfitting](https://www.ibm.com/think/topics/overfitting), a phenomenon in which a model’s knowledge is so thoroughly tailored to patterns in its training data that it can’t generalize, yielding a model that excels in training but fails in real-world scenarios.

Training a useful machine learning model therefore entails not only selecting and configuring an appropriate type of ML algorithm, but also the proper curation of training data and thoughtful validation of post-training performance.

## Types of machine learning algorithms

Machine learning algorithms can be sorted into three fundamental categories: *supervised learning, unsupervised learning* or *reinforcement learning.* Each of these learning paradigms are differentiated primarily by their distinct objectives, the types of training tasks those objectives entail, and the techniques used to optimize performance on those tasks.

- [**Supervised learning**](https://www.ibm.com/think/topics/supervised-learning) algorithms train a model to predict the “correct” output for a given input: in other words, to learn to relationship between independent variables (the features of input data) and dependent variables (the output, or “target”). They’re used to train models for tasks that require some degree of accuracy relative to some known “ [ground truth,](https://www.ibm.com/think/topics/ground-truth)” such as classification or regression. That ground truth typically (but not always) comes in the form of *labeled data*: data that has been annotated to provide context to the model—for instance, a dataset comprising labeled
	\[input, output\]
	pairings.
- [**Unsupervised learning**](https://www.ibm.com/think/topics/unsupervised-learning) algorithms train a model to discern intrinsic patterns, dependencies and correlations in unlabeled data sets. Unlike in supervised learning, unsupervised learning doesn’t entail the existence of any external ground truth against which its outputs should be compared.
- [**Reinforcement learning (RL)**](https://www.ibm.com/think/topics/reinforcement-learning) **algorithms** train a model, through trial and error, to evaluate its environment and take an action that will garner the greatest reward. Reinforcement learning is well suited to scenarios that don’t entail the existence of any singular ground truth, but do entail the “good” actions (to be rewarded) and “bad” actions (to be penalized). Whereas the objective of supervised learning algorithms is to optimize parameters in a way that minimizes error, the objective of reinforcement learning algorithms is to optimize model parameters in a way that maximizes reward.

Though there aren’t any ML algorithms that fit *none* of these three paradigms, there are some learning methods whose categorization is relatively ambiguous. For instance, [*semi* -supervised learning](http://www.ibm.com/think/topics/semi-supervised-learning) combines both supervised and unsupervised learning; [*self* -supervised learning](https://www.ibm.com/think/topics/self-supervised-learning) manipulates input data and designs training tasks in a way that enables supervised learning with unlabeled data.

A model can be trained with more than one type of machine learning algorithm. For instance, [large language models (LLMs)](https://www.ibm.com/think/topics/large-language-models) typically undergo their initial training ([“pre-training”](https://www.ibm.com/think/topics/pretrained-model)) through self-supervised learning, but are then [fine-tuned](https://www.ibm.com/think/topics/fine-tuning) through both conventional supervised learning algorithms as well as reinforcement learning algorithms. Likewise, ensemble learning algorithms entail the aggregation of multiple models into a single “final” model.

Machine learning algorithms are not one-size-fits-all: every algorithm has various *hyperparameters* that must configured to best suit a model to the specific scenario and dataset they are to operate within. For an analogy, consider pizza: a basic “algorithm” for making pizza could be defined as ladling tomato sauce on top of circular dough, placing mozzarella cheese on top of that sauce and baking it in an oven—but there are a near-infinite number of ways that “algorithm” could be specifically configured to accommodate specific tastes, ingredients, budgets or constraints.

Think Keynotes

### Win the enterprise AI race

Join Arvind Krishna to see how IBM is enabling AI-first enterprises through hybrid cloud and emerging quantum capabilities.

## Supervised learning algorithms

The formal objective of any supervised machine learning algorithm is to optimize [model parameters](https://www.ibm.com/think/topics/model-parameters) in a way that minimizes the output of a [***loss function***](https://www.ibm.com/think/topics/loss-function) that measures the divergence (“loss”) between a model’s predicted output for each input and the ground truth output for each of those inputs.

In conventional supervised learning, that ground truth is provided by labeled data. For instance, training a model that detects spam emails typically requires a human annotator to manually review a corpus of example emails and label each as “SPAM” or “NOT SPAM.” The goal of training the model is to adjust model parameters until the model’s output predictions for a given email consistently align with how the human labeled that email. Because this method entails direct human oversight of what the machine learns, it’s called “supervised” learning. Supervised learning, in turn, is often defined simply as *machine learning that uses labeled data*.

But some instances—particularly in modern deep learning—require such large datasets and such complex data points that obtaining enough labeled training data becomes prohibitively time- and labor-intensive. Self-supervised learning, developed largely to address such scenarios, devises training tasks such that a label (or “pseudo-label”) can be *inferred* from unlabeled data. This strains the conventional definition of supervised learning as requiring labeled data. Supervised learning algorithms are therefore better and more broadly defined as machine learning methods that involve some ground truth (or “supervisory signal”) to optimize toward and some loss function that compares model outputs to the ground truth.

Supervised learning algorithms are used to train a model for *classification* tasks, *regression* tasks or both.

- [**Classification**](https://www.ibm.com/think/topics/classification-machine-learning) entails discrete predictions, such as the specific category a data point belongs to. Classification tasks are either *binary—* ”yes”or “no”*, “* approve”or “reject*,” “* spam” or “not spam” *—* or *multi-class.* Some classification algorithms are only suited to binary classification, but any multi-class classifier can perform binary classification.
- **Regression** is used to predict *continuous* values, such as quantities, prices, duration or temperature. They’re used in time series analysis, forecasting, pricing and probability prediction, among many other use cases.

Many supervised learning algorithms can be used train to train models for regression *or* classification. For example, a model could use regression to predict the probability that a given data point belongs to each potential category, then output the category with the highest probability.

### Common regression algorithms

- [**Linear regression**](https://www.ibm.com/think/topics/linear-regression) is among the basic and widely-used machine learning algorithms. Linear regression algorithms compute an output (dependent variable) as a weighted combination of one or more input variables (independent variables). By learning the optimal weighting for each input variable, the algorithm yields the “line of best fit” for the data points seen in training. There exist a wide array of variants and extensions of linear regression that use similar logic to model more mathematically varied relationships between dependent and independent variables, such as *polynomial regression* (which models non-linear, curving relationships)or *quantile regression* (which models relationships at specific points in a dataset’s distribution).
- [**Decision tree**](https://www.ibm.com/think/topics/decision-trees) **algorithms** reach final output predictions through a branching sequence of if-then-else decisions that can be visualized as a tree-like diagram. They can be utilized for both regression and classification. Unlike in most supervised learning algorithms, the objective of the algorithm is not to optimize its output predictions by minimizing a single, global loss function, but rather to optimize the predictive power of each individual branching node of the tree.
- [**State space models (SSMs)**](https://www.ibm.com/think/topics/state-space-model) model dynamic systems and sequential data through two interrelated equations: one, the *state equation,* describes the internal dynamics (“state”) of a system that aren’t directly observable; the other, the *output equation,* describes how those internal dynamics relate to observable results—that is, to system outputs. They’re used across diverse fields, from electrical engineering to financial forecasting to [natural language processing (NLP).](https://www.ibm.com/think/topics/natural-language-processing)

### Common classification algorithms

- [**Naïve Bayes**](http://www.ibm.com/think/topics/naive-bayes) classifiers operate on the logic of [Bayes’ Theorem](https://ibm.com/topics/naive-bayes), which is essentially a mathematical formulation of the idea that information from later events (such as an outcome) can be used to update understanding of earlier events (such as inputs). In other words, the model learns the relative importance of a given input variable based on how strongly it correlates with specific outcomes. Its eponymous "naive" assumption is that all features contributing to a classification are independent of each other. This simplification makes the algorithm fast and effective for straightforward tasks like spam detection.
- [**Logistic regression**](https://www.ibm.com/think/topics/logistic-regression) adapts the linear regression algorithm to solve binary classification problems by feeding the weighted sum of input features into a [sigmoid function](http://community.ibm.com/community/user/ai-datascience/blogs/pavan-saish-naru/2023/01/27/optimization-hyperparameters), which squashes any input into a value between 0 and 1. The resulting value can be interpreted as the probability of a given event—in this case, a specific classification—occurring.
- [**K-nearest neighbor** (KNN)](https://www.ibm.com/think/topics/knn) algorithms classify data points based on their proximity in the [vector embedding space](https://www.ibm.com/think/topics/vector-embedding) to other, already-classified—that is, labeled—data points, with the assumption that similar data points can be found near each other. The *k* refers to how many neighboring data points are taken into consideration: for example, in a KNN algorithm where *k = 5,* the input data point will be compared to its 5 nearest neighbors and classified according to whichever category is represented most among those 5 neighboring data points.
- [**Support vector machines (SVMs)**](https://www.ibm.com/think/topics/support-vector-machine) are powerful models that ostensibly perform binary classification but can also be adapted for multi-class classification problems. An SVM algorithm’s goal is not to directly learn how to categorize data points: instead, its goal is to learn the optimal *decision boundary* to separate two categories of labeled data points in order to then classify new data points based on which side of the boundary they fall. The SVM algorithm defines this boundary as the hyperplane that maximizes the margin(or gap) between data points of opposite classes, a concept akin to the *low-density assumption* in [semi-supervised learning](https://www.ibm.com/think/topics/semi-supervised-learning). Logically, the only data points that can support the computation of that hyperplane are the data points from each class that are closest to the boundary. The vector embeddings of those boundary-adjacent data points are therefore called *support vectors.*

### Self-supervised learning algorithms

The goal of [self-supervised learning](https://www.ibm.com/think/topics/self-supervised-learning) algorithms is to perform supervised learning without requiring labeled data through designing tasks that use the structure of unlabeled data itself for supervisory signals. Self-supervised learning techniques generally fall into one of two subsets: *self-prediction* or *contrastive learning.*

#### Self-prediction

Self-predictionalgorithms train a model to predict one aspect of a data point when given other information about that data point. Yann LeCun articulated the goal of such methods in simple terms: “pretend there is a part of the input you don’t know and predict that.” <sup>1</sup> For example:

- Predict *any part of the input* from *any other part*
- Predict the *future* from the *past*
- Predict the *masked* from the *visible*
- Predict any *occluded part* from all *available parts*

Models trained using self-prediction are typically generative, rather than discriminative. Prominent examples of machine learning models trained used self-prediction algorithms include [autoencoders](https://www.ibm.com/topics/autoencoder) and [large language models (LLMs)](https://www.ibm.com/think/topics/large-language-models):

- Autoencoders are tasked with reconstructing the original input after compressing it down to only its latent variables. The original input serves as ground truth.
- Autoregressive LLMs—the text generating models that rose to fame following the launch of ChatGPT—are tasked with iteratively predicting the next token in a sequence, given only the previous tokens in that sequence. For each prediction, the actual next token in the sequence serves as ground truth.

#### Contrastive learning

Contrastive learning algorithms provide models with multiple data samples and task them with predicting how different (or similar) they are. Pairings of data points are often created via *data augmentation*: transforming or perturbing unlabeled data to create new instances or augmented views. For example, common augmentation techniques for image data include rotation, random cropping, flipping, noising, filtering and colorizations.

Contrastive learning is used prominently in the training of [computer vision](https://www.ibm.com/think/topics/computer-vision) models: for example, it can help a model learn to recognize the same object when viewed from different angles. It’s also essential in the training of [multimodal AI](https://www.ibm.com/think/topics/multimodal-ai): for example, it can help a model learn to “translate” vector embeddings from one data modality (like text) to another (like speech or images).

## Unsupervised learning algorithms

[Unsupervised machine learning](https://www.ibm.com/topics/unsupervised-learning) is used to teach models to discover intrinsic patterns, correlations and structure in unlabeled data. Unlike supervised learning, which entails the existence of “correct” answers the model should learn to output, or reinforcement learning, which entails a spectrum of “good” and “bad” actions a model could take, unsupervised learning is most useful in scenarios where the ideal output isn’t known in advance.

These objectives are not governed by any predefined ground truth or reward structure—hence “unsupervised.” Unsupervised learning algorithms therefore don’t involve loss functions, as their tasks don’t entail a known ideal output to measure against and optimize toward. The success of the learning process is governed primarily by manual [*hyperparameter tuning*](https://www.ibm.com/think/topics/hyperparameter-tuning)*,* rather than through algorithms that optimize the model’s internal parameters.

There are three fundamental subsets of unsupervised learning algorithms: *clustering* algorithms, *association* algorithms and *dimensionality reduction* algorithms.

### Clustering algorithms

[Clustering algorithms](https://www.ibm.com/think/topics/clustering) partition unlabeled data points into “clusters,” or groupings, based on their proximity or similarity to one another, for tasks such as market segmentation. They can also be used as predictive models for [anomaly detection](https://www.ibm.com/think/topics/machine-learning-for-anomaly-detection) by learning the clusters that all data points *should* be sorted into and identifying when an outlier data point does not fit neatly into any of those clusters.

- [**K-means clustering**](https://www.ibm.com/think/topics/k-means-clustering) algorithms partitions data into *k* clusters in a given data point will be assigned to the cluster whose center (*centroid*) it’s closes to. The process begins with an initial placement of *k* centroids, which is often randomized (but can also be determined by specified rules). Each data point is assigned to the cluster of the nearest centroid. Each centroid is then relocated to the position representing the average (*mean*) of all the data points that were just assigned to it; the data points are once again clustered according to the nearest centroid, and the position of each centroid are again adjusted. This process repeats iteratively until the location of each cluster’s centroid has stabilized.
- **Gaussian mixture models (GMMs)** are a “soft” clustering algorithm. A GMM assumes that a dataset is a mixture of multiple Gaussian—that is, classic “normal" or “bell curve”—distributions, and predicts the probability that a given data point belongs to each of those normally distributed clusters. The GMM algorithm is designed to learn the parameters for each Gaussian distribution—specifically, each distribution’s mean, variance and weight—that best fit the training dataset.
- **DBSCAN (Density-Based Spatial Clustering Applications with Noise)** creates clusters out of data points that are closely packed together. Rather than grouping all data points into clusters, it marks data points located alone in low-density regions as outliers. It identifies areas as dense enough to belong to a cluster based on whether a certain number of neighboring data points are located within a specified radius. Unlike k-means, DBSCAN can find arbitrarily shaped clusters and doesn't require the number of clusters to be specified beforehand.

### Association algorithms

- Association algorithms identify correlations between variables in large datasets. They’re used prominently in tasks like market basket analysis or product recommendation engines: for instance, an e-commerce service might use association algorithms to identify which items are frequently purchased in combination with one another and use that information to dynamically promote related items in their inventory.
- The [***apriori* algorithm**](https://www.ibm.com/think/topics/apriori-algorithm) is a classic association method. The algorithm makes multiple passes over the dataset using a "bottom-up" approach, exploring the frequency of progressively larger combinations of individual items and pruning combinations that appear infrequently. The *a priori* principle holds that if a larger grouping of items is deemed frequent, any subset of that grouping must also be frequent; conversely, if a smaller grouping of items is deemed infrequent, then any superset including that smaller grouping must also be infrequent. While it’s simple and highly adaptable, the apriori algorithm can become memory intensive and computationally expensive.
- **Dynamic itemset counting (DIC)** is a more compute-efficient association method, though it operates through logic similar to that of the classic apriori algorithm. Rather than exploring the entire dataset with each pass, it starts with only a subset of the database and then periodically adds new items, “dynamically” expanding its focus.

Other notable association algorithms include **CHARM** (short for Closed Association Rule Mining—the authors of the CHARM paper note that “the H is gratuitous”) <sup>2</sup> and **CARMA** (Continuous Association Rule Mining Algorithm).<sup>3</sup>

### Dimensionality reduction algorithms

[Dimensionality reduction](https://www.ibm.com/think/topics/dimensionality-reduction) algorithms are designed to take in a data point and output a more efficient representation of that data point. More specifically, they’re designed to learn a mapping of high-dimensional data points to a space where they can be accurately described using fewer features: in other words, to *reduce* the number of *dimensions* needed to represent data effectively.

Dimensionality reduction is often performed as a data preprocessing step, helping to reduce complexity and noise in data in order to improve predictions or decrease computational demands. It’s also an essential step in the modeling of a dataset’s [***latent space***](https://www.ibm.com/think/topics/latent-space): a compressed (*lower-dimensional)* representation of data retaining only the subset of features most relevant to the task at hand. Other common dimensionality reduction use cases include data compression and data visualization.

- [**Principal component analysis (PCA)**](https://www.ibm.com/think/topics/principal-component-analysis) simplifies complex datasets by summarizing the data’s original variables—many of which are often correlated with one another, and thus somewhat redundant—as a smaller subset of uncorrelated variables, each of which is a linear combination of original variables. More specifically, the algorithm prioritizes the data’s *principal components*: the linear combinations of variables that have the most variance compared to other linear combinations.
- **t-distributed Stochastic Neighbor Embedding (t-SNE)** is a non-linear dimensionality reduction algorithm commonly used for data visualization purposes. It’s used almost exclusively to represent data in either 2 or 3 dimensions, with the primary goal of ensuring that data points close to each other in high-dimensional space remain close to each other in the new lower-dimensional space.
- [**Autoencoders**](https://www.ibm.com/think/topics/autoencoder) are a type of encoder-decoder neural network architecture trained through what might more commonly be considered a *self-* supervised learning algorithm (in that its objective is to minimize a loss function)—but they nevertheless perform dimensionality reduction of unlabeled data, in this case modeling its latent space. The encoder comprises a series of progressively smaller layers, forcing input data to pass through a “bottleneck” that “squeezes” the data into fewer and fewer dimensions before it reaches the decoder. The decoder, which comprises a series of progressively *larger* layers, is then tasked with reconstructing the original data using this compressed representation, with the objective of minimizing *reconstruction loss*. This forces the encoder to learn to extract and pass through only the information most conducive to accurately reconstructing the original input.

## Semi-supervised learning algorithms

Semi-supervised learning, which is generally employed for the same use cases as supervised learning methods, is distinguished by techniques to incorporate unlabeled data into model training alongside a subset of labeled data. They’re especially useful in situations where obtaining enough labeled data is prohibitively difficult or expensive, but relevant unlabeled data is relatively easy to acquire.

The unlabeled examples used in semi-supervised learning must be relevant to the task the model is being trained to perform. For example, when training an image classifier to differentiate between pictures of cats and dogs, the inclusion of unlabeled images of cats and dogs will aid training—but images of horses and motorcycles will not. This condition informs a series of *assumptions* about how data points relate to one another that provide the formal logic of semi-supervised methods.

Semi-supervised learning algorithms are generally categorized as *transductive, inductive* or *inherently self-supervised.*

- **Transductive methods** focus on classifying the unlabeled data points available during training so that they can subsequently be applied to conventional supervised learning algorithms. *Label propagation*, for example, is a graph-based method that infers “pseudo-labels” for unlabeled data by “propagating” known labels to the data point lying on neighboring nodes of the graph.
- **Inductive methods** aim to build a generalizable model that can classify both the unlabeled data present during training as well as any new, unseen data points. In *self-training*, a model is first trained with conventional supervised learning on a small labeled dataset; the model is then tasked with making probabilisticpredictions about unlabeled data points; only predictions above a certain threshold of confidence are accepted. *Co-training* extends self-training with [ensemble learning](https://www.ibm.com/think/topics/ensemble-learning), training different types of base learners on different features of the data. *Cluster-then-label* methods perform unsupervised clustering on all available data points, then assign labels to each cluster based on which label is most frequently represented within that cluster.
- Some algorithms, such as **ladder networks** <sup>4</sup> or **semi-supervised** **support vector machines (S3VMs)** <sup>5</sup> are inherently designed for semi-supervised learning (whereas transductive and inductive methods adapt or add extra steps to conventional supervised algorithms).

## Reinforcement learning algorithms

[Reinforcement learning](https://www.ibm.com/think/topics/reinforcement-learning) (RL) algorithms are suited for tasks in which there’s no singular “correct” output (or action), but there are “good” outputs. They’re used prominently in robotics, video games, [reasoning models](https://www.ibm.com/think/topics/reasoning-model) and other use cases in which the space of possible solutions and approaches are particularly large, open-ended or difficult to define. In the parlance of RL, the entity being trained is usually referred to as an “agent.”

Rather than a supervisory signal and explicitly defined tasks, they entail a *reward signal* that allows models to learn holistically through trial and error. That reward signal can come from a reward function, a separately trained reward model, or a rules-based reward system.

RL algorithms optimize a *policy.* Mathematically speaking, a policy ( π ) is a function that takes a *state* ( *s* ) as input and returns an *action* ( *a* ): π(s)→a. The goal of an RL algorithm is to learn the policy that takes the action that will garner the maximum reward for any given state.

RL algorithms can be *value-based* or *policy-based.* In policy-based algorithms, a model learns an optimal policy directly. In value-based algorithms, the agent learns a value function that computes a score for how “good” each state is—typically based on the potential reward for actions that can be taken from that state—then chooses actions that lead to higher-value states. Hybrid approaches learn a value function that, in turn, is then used to optimize a policy.

Notable reinforcement algorithms include:

- *Q-learning,* derived from value-based methods
- *Proximal policy optimization (PPO),* a policy-based method used prominently in [reinforcement learning from human feedback (RLHF)](https://www.ibm.com/think/topics/rlhf)  
	*Actor-critic* and derivatives such as *advantage actor-critic* (A2C), which use a hybrid of value- and policy-based methods
- *REINFORCE* (short for REward Increment = Nonnegative Factor × Offset Reinforcement × Characteristic Eligibility), a seminal policy-based method

## Ensemble learning algorithms

[Ensemble learning](https://www.ibm.com/think/topics/ensemble-learning) refers to techniques that combine multiple machine learning algorithms—often referred to as “learners” in this context—to achieve more accurate or more reliable performance than would be possible through any of its constituent algorithms alone.

Ensemble learning algorithms typically utilize *boosting, stacking* or *bagging* techniques.

### Boosting

[Boosting algorithms](https://www.ibm.com/think/topics/boosting) build models sequentially, where each subsequent new model is trained to correct the errors of the previous model. The progression of initially weak" learners eventually culminates in a single, highly accurate "strong" learner.

- **Adaptive boosting** (**AdaBoost**)gives more weight to instances that were originally misclassified by the previous model, ensuring that updates to the subsequent model prioritize improve performance on those training examples. The final prediction is determined by weighted majority vote, with the later, more accurate models having more influence over the final output.
- **Gradient boosting** focuses on the *errors* made by previous learners, rather than on the *data points* on which the previous models erred. More specifically, it trains each model to correct—that is, predict—the errors made by the prior model on a given data point. By aggregating the predictions of each subsequent model, the ensemble can ultimately reverse engineer the correct output for the original data point. [**XGBoost**](https://www.ibm.com/think/topics/xgboost) (short for eXtreme Gradient Boosting) is an open source [machine learning library](https://www.ibm.com/think/topics/machine-learning-libraries) for efficient implementation of gradient boosting.

### Bagging

[Bagging](https://www.ibm.com/think/topics/bagging) algorithms, also known as *bootstrap aggregation,*train multiple models in parallel on different randomly sampled subsets of the training dataset, then combine their predictions through voting (in classification problems) or averaging (in regression problems). This approach is highly effective at reducing variance and preventing overfitting.

The [**random forest**](https://www.ibm.com/think/topics/random-forest) algorithm, for instance, uses bagging to construct ensembles of uncorrelated decision tree models.

### Stacking

Stacking algorithms combine predictions from multiple base learners—each of which often specialize in a particular type of prediction—then trains a final "meta-model" on the outputs of these base models to learn how to best combine their predictions for a more accurate and robust final output.

In the related technique of [**knowledge distillation**](https://www.ibm.com/think/topics/knowledge-distillation)**,** the final model is trained not only on the final output predictions (“hard targets”) of the base learners, but also on their intermediate outputs (“logits” or “soft targets”), in attempt to replicate their “thought processes.”

## Deep learning algorithms

[Deep learning](https://www.ibm.com/think/topics/deep-learning) is a subset of [machine learning](https://www.ibm.com/think/topics/machine-learning?) defined by the usage of multilayered artificial [neural networks](https://www.ibm.com/think/topics/neural-networks?), typically trained through supervised learning on labeled data or (as is often the case for [generative AI](https://www.ibm.com/think/topics/generative-ai) models in particular) through self-supervised learning on unlabeled data. In deep reinforcement learning, a deep neural network serves as the *policy* of an RL agent. Deep learning has powered most state-of-the-art advancements in [artificial intelligence](https://www.ibm.com/think/topics/artificial-intelligence?) since the early 2010s. Among its most important strengths is its ability to automate the process of [feature engineering](https://www.ibm.com/think/topics/feature-engineering), which is often manual in traditional machine learning.

Unlike the explicitly defined algorithms of “traditional” [machine learning](https://www.ibm.com/think/topics/machine-learning-algorithms), deep learning models comprise many interconnected layers of “neurons” (or “nodes”) that each perform a mathematical operation (called an “activation function”). The input to each neuron’s activation function is a weighted combination of the outputs of the activation functions of each of the neurons of the previous layer. The neurons in the final layer compute the model’s final output. Crucially, the activation functions performed at each node are *nonlinear*, enabling neural networks to model complex patterns and dependencies. Though neural networks in modern AI are most commonly associated with cutting-edge [deep learning](https://www.ibm.com/think/topics/deep-learning), “non-deep” neural networks such as [restricted Boltzmann machines](https://developer.ibm.com/tutorials/build-a-recommendation-engine-with-a-restricted-boltzmann-machine-using-tensorflow/) have been in use for decades.

It’s the distributed structure of deep learning algorithms that provides their incredible power and versatility. Imagine training data as data points scattered on a 2-dimensional graph, and the goal of [model training](https://www.ibm.com/think/topics/model-training) to be finding a line that runs through each of those data points. Whereas traditional machine learning algorithms attempt this feat with a single mathematical function that yields a single line (or curve), deep learning algorithms can piece together an arbitrary number of smaller, individually adjustable lines to form the desired shape. Deep neural networks are *universal approximators*: it has been proven theoretically that for any function, there exists a neural network arrangement that can reproduce it.<sup>6</sup>

### Architectures vs. algorithms

- In the context of deep learning, specific model types are often referred to by their “architectures,” a concept related to but distinct from algorithms.
- A neural network *architecture* refers to its layout: the number and size of layers; the use of specialized layers; the choice(s) of activation functions. The same neural network architecture can often be trained to perform one of multiple kinds of tasks or process one of multiple data modalities.
- A deep learning *algorithm* comprises not only the neural network architecture used for a model, but the task it’s being trained to perform and the steps taken to optimize it for that task.

Consider autoencoders: architecture-wise, an autoencoder is an *encoder-decoder* model—its encoder network features progressively smaller layers, while its decoder network features progressively larger layers. But an autoencoder is only one of many encoder-decoder models: for instance, [image segmentation](https://www.ibm.com/topics/image-segmentation) models have a very similar architecture, in which progressive smaller [convolutional](https://www.ibm.com/think/topics/convolutional-neural-networks) layers downsample data to isolate and segment key features, followed by progressively larger layers that upsample the (segmented) data back to its original size.

What makes an autoencoder an autoencoder is not (just) its architecture, but the algorithm used to train it: an autoencoder is *tasked with reconstructing the original input,* and optimized through model training to *minimize a function that measures reconstruction loss* (often modified by additional [regularization](https://www.ibm.com/think/topics/regularization) terms)*.* A model that has an identical architecture but is trained to perform a different task and optimized for a different objective is not an autoencoder.

Link copied

[Data science and MLOps for data leaders](https://www.ibm.com/forms/mkt-51585)

[

Join forces with other leaders to drive the three essential pillars of MLOps and trustworthy AI: trust in data, trust in models and trust in processes.

](https://www.ibm.com/forms/mkt-51585)

## Resources

[Level up your ML expertise](https://developer.ibm.com/technologies/machine-learning/courses/)

[

Learn fundamental concepts and build your skills with hands-on labs, courses, guided projects, trials and more.

](https://developer.ibm.com/technologies/machine-learning/courses/)

Take the next step

Whether you choose to customize pre-built apps and skills or build and deploy custom agentic services using an AI studio, the IBM watsonx platform has you covered.

1. [Explore watsonx Orchestrate](https://www.ibm.com/products/watsonx-orchestrate)
2. [Explore watsonx.ai](https://www.ibm.com/products/watsonx-ai)

##### Footnotes

*<sup>All links reside outside IBM.com.</sup>  
*1\. [“Energy-Based Self-Supervised Learning,”](https://helper.ipam.ucla.edu/publications/mlpws4/mlpws4_15927.pdf) Yann LeCun (accessed via UCLA), 19 November 2019  
2\. [“CHARM: An Efficient Algorithm for Closed Itemset Mining,”](https://epubs.siam.org/doi/epdf/10.1137/1.9781611972726.27) *Proceedings of the 2002 SIAM International Conference on Data Mining  
*3\. [“Online Association Rule Mining,”](https://dl.acm.org/doi/10.1145/304182.304195) *Proceedings of the 1999 ACM SIGMOD International Conference on Management of Data,* 1 June 1999  
4\. [“Semi-Supervised Learning with Ladder Networks,”](https://arxiv.org/pdf/1507.02672) arXiv, 24 November 2015  
5\. [“Kolmogorov’s Mapping Neural Network Existence Theorem,”](https://cs.uwaterloo.ca/~y328yu/classics/Hecht-Nielsen.pdf) *Proceedings of the IEEE First International Conference on Neural Networks* (accessed through University of Waterloo)*,* 1987  
6\. [“Multilayer Feedforward Networks with a Non-Polynomial Activation Function Can Approximate Any Function,”](https://archive.nyu.edu/bitstream/2451/14329/1/IS-92-13.pdf) Center for Research on Information Systems (New York University), March 1992#5/21/2026