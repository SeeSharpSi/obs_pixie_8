---
title: "What is Machine Learning?"
source: "https://www.ibm.com/think/topics/machine-learning#7281535"
author:
  - "[[Dave Bergmann]]"
published: 1959-07-02
created: 2026-05-21
description: "Machine learning is the subset of AI focused on algorithms that analyze and “learn” the patterns of training data in order to make accurate inferences about new data."
tags:
  - "clippings"
---
Machine learning is the subset of artificial intelligence (AI) focused on algorithms that can “learn” the patterns of training data and, subsequently, make accurate *inferences* about new data. This pattern recognition ability enables machine learning models to make decisions or predictions without explicit, hard-coded instructions.

Machine learning has come to dominate the field of AI: it provides the backbone of most modern AI systems, from [forecasting](https://www.ibm.com/think/topics/forecasting) models to autonomous vehicles to [large language models (LLMs)](https://www.ibm.com/think/topics/large-language-models) and other [generative AI](https://www.ibm.com/think/topics/generative-ai) tools.

The central premise of machine learning (ML) is that if you optimize a model’s performance on a dataset of tasks that adequately resemble the real-world problems it will be used for—through a process called [model training](https://www.ibm.com/think/topics/model-training) —the model can make accurate predictions on the new data it sees in its ultimate use case.

Training itself is simply a means to an end: generalization, the translation of strong performance on training data to useful results in real-world scenarios, is the fundamental goal of machine learning. In essence, a trained model is applying patterns it learned from training data to infer the correct output for a real-world task: the deployment of an [AI model](https://www.ibm.com/think/topics/ai-model) is therefore called [AI inference](https://www.ibm.com/think/topics/ai-inference).

[Deep learning](https://www.ibm.com/think/topics/deep-learning), the subset of machine learning driven by large—or rather, “deep”— [artificial neural networks](https://www.ibm.com/think/topics/neural-networks?), has emerged over the past few decades as the state-of-the-art AI model architecture across nearly every domain in which AI is used. In contrast to the explicitly defined algorithms of traditional machine learning, deep learning relies on distributed “networks” of mathematical operations that provide an unparalleled ability to learn the intricate nuances of very complex data. Because deep learning requires very large amounts of data and computational resources, its advent has coincided with the escalated importance [“big data”](https://www.ibm.com/think/topics/big-data) and [graphics processing units (GPUs).](https://www.ibm.com/think/topics/gpu)

The discipline of machine learning is closely intertwined with that of [data science](https://www.ibm.com/think/topics/data-science). In a sense, machine learning can be understood as a collection of algorithms and techniques to automate data analysis and (more importantly) apply learnings from that analysis to the autonomous execution of relevant tasks.

The origin of the term (albeit not the core concept itself) is often attributed to Arthur L. Samuel’s 1959 article in IBM Journal, “Some Studies in Machine Learning Using the Game of Checkers.” In the paper’s introduction, Samuel neatly articulates machine learning’s ideal outcome: “a computer can be programmed so that it will learn to play a better game of checkers than can be played by the person who wrote the program.” <sup>1</sup>

### Machine learning vs. artificial intelligence

Though “machine learning” and “artificial intelligence” are often used interchangeably, they are not quite synonymous. In short: *all machine learning is AI, but not all AI is machine learning*.

In the popular imagination, “AI” is usually associated with science fiction—typically through depictions of what’s more properly called [artificial general intelligence (AGI)](https://www.ibm.com/think/topics/artificial-general-intelligence), like HAL 9000 in *2001: A Space Odyssey* or Ava in *Ex Machina* —or, more recently, with [*generative* AI](https://www.ibm.com/think/topics/generative-ai). But “artificial intelligence” is a catch-all term for any program that can use information to make decisions or predictions without active human involvement.

The most elementary AI systems are a series of if-then-else statements, with rules and logic programmed explicitly by a data scientist. At the simplest level, even a rudimentary thermostat is a rules-based AI system: when programmed with simple rules like

IF room\_temperature < 67, THEN turn\_on\_heater

and

IF room\_temperature > 72, THEN turn\_on\_air\_conditioner

the thermostat is capable of autonomous decision-making without further human intervention. At a more complex level, a large and intricate rules-based [decision tree](https://www.ibm.com/think/topics/decision-trees) programmed by medical experts could parse symptoms, circumstances and comorbidities to aid diagnosis or prognosis.<sup>2</sup>

Unlike in expert systems, the logic by which a machine learning model operates isn’t explicitly programmed—it’s *learned* through experience. Consider a program that filters email spam: rules-based AI requires a data scientist to manually devise accurate, universal criteria for spam; machine learning requires only the selection of an appropriate algorithm and an adequate dataset of sample emails. In training, the model is shown sample emails and predicts which are spam; the error of its predictions is calculated, and its algorithm is adjusted to reduce error; this process is repeated until the model is accurate. The newly trained ML model has *implicitly* learned how to identify spam.

As the tasks an AI system is to perform become more complex, rules-based models become increasingly brittle: it’s often impossible to explicitly define every pattern and variable a model must consider. Machine learning systems have emerged as the dominant mode of artificial intelligence because implicit learning patterns from the data itself is inherently more flexible, scalable and accessible.

## How machine learning works

Machine learning works through mathematical logic. The relevant characteristics (or "features") of each data point must therefore be expressed numerically, so that the data itself can be fed into a mathematical algorithm that will "learn" to map a given input to the desired output.

Data points in machine learning are usually represented in vector form, in which each element (or dimension) of a data point’s [vector embedding](https://www.ibm.com/think/topics/vector-embedding) corresponds to its numerical value for a specific feature. For data modalities that are inherently numerical, such as financial data or geospatial coordinates, this is relatively straightforward. But many data modalities, such as text, images, social media graph data or app user behaviors, are not inherently numerical, and therefore entail less immediately intuitive feature engineering to be expressed in an ML-ready way.

The (often manual) process of choosing which aspects of data to use in machine learning algorithms is called [feature selection](https://www.ibm.com/think/topics/feature-selection). [Feature extraction](https://www.ibm.com/think/topics/feature-extraction) techniques refine data down to only its most relevant, meaningful dimensions. Both are subsets of [feature engineering](https://www.ibm.com/think/topics/feature-engineering), the broader discipline of preprocessing raw data for use in machine learning. One notable distinction of deep learning is that it typically operates on raw data and automates much of the feature engineering—or at least the feature extraction—process. This makes deep learning more scalable, albeit less interpretable, than traditional machine learning.

### Machine learning model parameters and optimization

For a practical example, consider a simple [linear regression](https://www.ibm.com/think/topics/linear-regression) algorithm for predicting home sale prices based on a weighted combination of three variables: square footage, age of house and number of bedrooms. Each house is represented as a vector embedding with 3 dimensions:

\[square footage, bedrooms, age\]

. A 30-year-old house with 4 bedrooms and 1900 square feet could be represented as

\[1900, 4, 30\]

(though for mathematical purposes those numbers might first be scaled, or normalized, to a more uniform range).

The algorithm is a straightforward mathematical function:

```
Price = (A * square footage) + (B * number of rooms) – (C * Age) + Base Price
```

Here, $A$, $B$ and $C$ are the model parameters: adjusting them will adjust how heavily the model weighs each variable. The goal of machine learning is to find the optimal values for such model parameters: in other words, the parameter values that result in the overall function outputting the most accurate results. While most real-world instances of machine learning involve more complex algorithms with a greater number of input variables, the principle remains the same: optimizing the algorithm's adjustable parameters to yield greater accuracy.

## Types of machine learning

All machine learning methods can be categorized as one of three distinct learning paradigms: supervised learning, unsupervised learning or reinforcement learning, based on the nature of their training objectives and (often but not always) by the type of training data they entail.

- [Supervised learning](https://www.ibm.com/think/topics/supervised-learning) trains a model to predict the “correct” output for a given input. It applies to tasks that require some degree of accuracy relative to some external “ [ground truth,](https://www.ibm.com/think/topics/ground-truth)” such as classification or regression.
- [Unsupervised learning](https://www.ibm.com/think/topics/unsupervised-learning) trains a model to discern intrinsic patterns, dependencies and correlations in data. Unlike in supervised learning, unsupervised learning tasks don’t involve any external ground truth against which its outputs should be compared.
- [Reinforcement learning (RL)](https://www.ibm.com/think/topics/reinforcement-learning) trains a model to evaluate its environment and take an action that will garner the greatest reward. RL scenarios don’t entail the existence of a singular ground truth, but they do entail the existence of “good” and “bad” (or neutral) actions.

The end-to-end training process for a given model can, and often does, involve hybrid approaches that leverage more than one of these learning paradigms. For instance, unsupervised learning is often used to preprocess data for use in supervised or reinforcement learning. Large language models (LLMs) typically undergo their initial training (pre-training) and [fine-tuning](https://www.ibm.com/think/topics/fine-tuning) through variants of supervised learning, followed by more fine-tuning through RL techniques such as [reinforcement learning from human feedback (RLHF)](https://www.ibm.com/think/topics/rlhf).

In a similar but distinct practice, various [ensemble learning](https://www.ibm.com/think/topics/ensemble-learning) methods aggregate the outputs of multiple algorithms.

### Supervised learning

Supervised learning algorithms train models for tasks requiring accuracy, such as [classification](https://www.ibm.com/think/topics/classification-machine-learning) or regression. Supervised machine learning powers both state-of-the-art deep learning models and a wide array of traditional ML models still widely employed across industries.

- **Regression** models predict continuous values, such as price, duration, temperature or size. Examples of traditional regression algorithms include [linear regression](https://www.ibm.com/think/topics/linear-regression), polynomial regression and [state space models](https://www.ibm.com/think/topics/state-space-model).
- **Classification** models predict discrete values, such as the category (or *class*) a data point belongs to, a binary decision or a specific action to be taken. Examples of traditional classification algorithms include [support vector machines (SVMs)](https://www.ibm.com/think/topics/support-vector-machine), [Naïve Bayes](https://www.ibm.com/think/topics/naive-bayes) and [logistic regression](https://www.ibm.com/think/topics/logistic-regression).
- Many supervised ML algorithms can be used for either task. For instance, the output of what’s nominally a regression algorithm can subsequently be used to inform a classification prediction.

To be measured and optimized for accuracy, a model’s outputs must be compared to a *ground truth*: the ideal or “correct” output for any given input. In conventional supervised learning, that ground truth is provided by labeled data. An email spam detection model is trained on a dataset of emails that have each been labeled as

SPAM

or

NOT SPAM

. An [image segmentation](https://www.ibm.com/think/topics/image-segmentation) model is trained on images in which every individual pixel has been annotated by its classification. The goal of supervised learning is to adjust the model’s parameters until its outputs consistently match the ground truth provided by those labels.

Essential to supervised learning is the use of a [loss function](https://www.ibm.com/think/topics/loss-function) that measures the divergence (“loss”) between the model’s output and the ground truth across a batch of training inputs. The objective of supervised learning is defined mathematically as *minimizing the output of a loss function*. Once loss has been computed, various optimization algorithms—most of which involve calculating the [derivative](https://www.ibm.com/think/topics/backpropagation#Key+mathematical+concepts+for+backpropagation) (s) of the loss function—are used to identify parameter adjustments that will reduce loss.

Because this process traditionally requires a human in the loop to provide ground truth in the form of data annotations, it’s called “supervised” learning. As such, the use of labeled data was historically considered the definitive characteristic of supervised learning. But on the most fundamental level, the hallmark of supervised learning is the existence of some ground truth and the training objective of minimizing the output of loss function that measures divergence from it.

To accommodate a more versatile notion of supervised learning, modern ML terminology uses “supervision” or “supervisory signals” to refer generically to any source of ground truth.

#### Self-supervised learning

Labeling data can become prohibitively costly and time-consuming for complex tasks and large datasets. [Self-supervised learning](https://www.ibm.com/think/topics/self-supervised-learning) entails training on tasks in which a supervisory signal is obtained directly from *unlabeled* data—hence “self” supervised.

For instance, [autoencoders](https://www.ibm.com/think/topics/autoencoder) are trained to compress (or *encode*) input data, then reconstruct (or *decode*) the original input using that compressed representation. Their training objective is to minimize *reconstruction error*, using the original input itself as ground truth. Self-supervised learning is also the primary training method for LLMs: models are provided text samples with certain words hidden or masked and tasked with predicting the missing words.

Self-supervised learning is frequently associated with [transfer learning](https://www.ibm.com/think/topics/transfer-learning?), as it can provide [foundation models](https://www.ibm.com/think/topics/foundation-models) with broad capabilities that will then be [fine-tuned](https://www.ibm.com/think/topics/fine-tuning) for more specific tasks.

#### Semi-supervised learning

Whereas self-supervised learning is essentially supervised learning on unlabeled data, [semi-supervised learning](https://www.ibm.com/think/topics/semi-supervised-learning) methods use both labeled data and unlabeled data. Broadly speaking, semi-supervised learning comprises techniques that use information from the available labeled data to make assumptions about the unlabeled data points so that the latter can be incorporated into supervised learning workflows.

### Unsupervised learning

Unsupervised machine learning algorithms discern intrinsic patterns in unlabeled data, such as similarities, correlations or potential groupings. They’re most useful in scenarios where such patterns aren’t necessarily apparent to human observers. Because unsupervised learning doesn’t assume the preexistence of a known “correct” output, they don’t require supervisory signals or conventional loss functions—hence “unsupervised.”

Most unsupervised learning methods perform one of the following functions:

- [**Clustering**](https://www.ibm.com/think/topics/clustering) algorithms partition unlabeled data points into “clusters,” or groupings, based on their proximity or similarity to one another. They’re typically used for tasks like market segmentation or fraud detection. Prominent clustering algorithms include K-means clustering, Gaussian mixture models (GMMs) and density-based methods such as DBSCAN.
- **Association** algorithms discern correlations, such as between a particular action and certain conditions. For instance, e-commerce businesses such as Amazon use unsupervised [association](https://dataplatform.cloud.ibm.com/docs/content/wsd/nodes/associationrules.html?context=cpdaas) models to power recommendation engines.
- [**Dimensionality reduction**](https://www.ibm.com/think/topics/dimensionality-reduction) algorithms reduce the complexity of data points by representing them with a smaller number of features—that is, in fewer dimensions—while [preserving their meaningful characteristics](https://www.ibm.com/think/topics/latent-space). They’re often used for preprocessing data, as well as for tasks such as data compression or data visualization. Prominent dimensionality reduction algorithms include [autoencoders](https://www.ibm.com/think/topics/autoencoder), [principal component analysis (PCA)](https://www.ibm.com/think/topics/principal-component-analysis), [linear discriminant analysis (LDA)](https://www.ibm.com/think/topics/linear-discriminant-analysis) and [t-Distributed Stochastic Neighbor Embedding (t-SNE).](https://lvdmaaten.github.io/tsne/)

As their name suggests, unsupervised learning algorithms can be broadly understood as somewhat “optimizing themselves.” For example, [this animation](https://shabal.in/visuals/kmeans/6.html) demonstrates how a k-means clustering algorithm iteratively optimizes the centroid of each cluster on its own. The challenge of training unsupervised models therefore focuses on effective data preprocessing and properly [tuning hyperparameters](https://www.ibm.com/think/topics/hyperparameter-tuning) that influence the learning process but are not themselves learnable, such as the [learning rate](https://www.ibm.com/think/topics/learning-rate) or number of clusters.

### Reinforcement learning (RL)

Whereas supervised learning trains models by optimizing them to match ideal exemplars and unsupervised learning algorithms fit themselves to a dataset, [reinforcement learning](https://www.ibm.com/think/topics/reinforcement-learning) models are trained holistically through trial and error. They’re used prominently in robotics, video games, [reasoning models](https://www.ibm.com/think/topics/reasoning-model) and other use cases in which the space of possible solutions and approaches are particularly large, open-ended or difficult to define. In RL literature, an AI system is often referred to as an “agent.”

Rather than the independent pairs of input-output data used in supervised learning, reinforcement learning (RL) operates on interdependent state-action-reward data tuples. Instead of minimizing error, the objective of reinforcement learning is optimizing parameters to maximize reward.

A mathematical framework for reinforcement learning is built primarily on the following components:

- The **state space** contains all available information relevant to decisions that the model might make. The state typically changes with each action that the model takes.
- The **action space** contains all the decisions that the model is permitted to make at a moment. In a board game, for instance, the action space comprises all legal moves available at a given time. In text generation, the action space comprises the entire “vocabulary” of tokens available to an LLM.
- The **reward signal** is the feedback—positive or negative, typically expressed as a scalar value—provided to the agent as a result of each action. The value of the reward signal could be determined by explicit rules, by a r *eward function*, or by a separately trained *reward model*.
- A **policy** is the “thought process” that drives an RL agent’s behavior. Mathematically speaking, a policy ($π$) is a function that takes a state ( $s$ ) as input and returns an action ($a$ ): π(s)→a.

In *policy-based* RL methods like proximal policy optimization (PPO), the model learns a policy directly. In *value-based* methods like Q-learning, the agent learns a value function that computes a score for how “good” each state is, then chooses actions that lead to higher-value states. Consider a maze: a policy-based agent might learn “at this corner, turn left,” while a value-based agent learns a score for each position and simply moves to an adjacent position with a better score. Hybrid approaches, such as actor-critic methods, learn a value function that’s then used to optimize a policy.

In deep reinforcement learning, the policy is represented as a [neural network](https://www.ibm.com/think/topics/neural-networks).

## Deep learning

[Deep learning](https://www.ibm.com/think/topics/deep-learning) employs [artificial neural networks](https://www.ibm.com/think/topics/neural-networks) with many layers—hence “deep”—rather than the explicitly designed algorithms of traditional machine learning. Though neural networks were introduced early in the history of machine learning, it wasn’t until the late 2000s and early 2010s, enabled in part by advancements in [GPUs](https://www.ibm.com/think/topics/gpu), that they became dominant in most subfields of AI.

Loosely inspired by the human brain, neural networks comprise interconnected layers of “neurons” (or *nodes*), each of which performs its own mathematical operation (called an “activation function”). The output of each node’s activation function serves as input to each of the nodes of the following layer and so on until the final layer, where the network’s final output is computed. Crucially, the activation functions performed at each node are *nonlinear*, enabling neural networks to model complex patterns and dependencies.

![Neural network diagram with input layer, multiple hidden layers, and output layer connected by weighted links.](https://assets.ibm.com/is/image/ibm/deep-neural-network-diagram:2x1?fmt=png-alpha&dpr=on%2C2.2222222222222223&wid=1584&hei=792)

Each connection between two neurons is assigned a unique *weight*: a multiplier that increases or decreases one neuron’s contribution to a neuron in the following layer. These weights, along with unique *bias* terms added to each neuron's activation function, are the parameters to be optimized through machine learning.

The [**backpropagation**](https://www.ibm.com/think/topics/backpropagation) algorithm enables the computation of how *each individual node* contributes to the overall output of the loss function, allowing even millions or billions of model weights to be individually optimized through [gradient descent](https://www.ibm.com/think/topics/gradient-descent) algorithms. Because of the volume and granularity of updates required to achieve optimal results, deep learning requires very large amounts of data and computational resources compared to traditional ML.  
  
That distributed structure affords deep learning models their incredible power and versatility. Imagine training data as data points scattered on a 2-dimensional graph. Essentially, traditional machine learning aims to find a single curve that runs through every one of those data points; deep learning pieces together an arbitrary number of smaller, individually adjustable lines to form the desired shape. Neural networks are *universal approximators*: it has been theoretically proven that for any function, there exists a neural network arrangement that can reproduce it.<sup>3, 4</sup>

Having said that, just because something is *theoretically* possible doesn’t mean it’s practically achievable through existing training methods. For many years, adequate performance on certain tasks remained out of reach even for deep learning models—but over time, modifications to the standard neural network architecture have unlocked new capabilities for ML models.

### Convolutional neural networks (CNNs)

[Convolutional neural networks (CNNs)](https://www.ibm.com/think/topics/convolutional-neural-networks) add *convolutional layers* to neural networks. In mathematics, a convolution is an operation where one function modifies (or *convolves*) the shape of another. In CNNs, convolutional layers are used to extract important features from data by [applying weighted “filters”.](https://developer.ibm.com/articles/introduction-to-convolutional-neural-networks/) CNNs are primarily associated with computer vision models and image data, but have a number of other important use cases.

![Diagram of image convolution with a numbered input grid, a 3×3 filter matrix, and an output grid showing summed results.](https://assets.ibm.com/is/image/ibm/iclh-diagram-convolutional-neural-networks:16x9?fmt=png-alpha&dpr=on%2C2.2222222222222223&wid=1584&hei=891 "Matrix filter visualization with numeric grid")

### Recurrent neural networks (RNNs)

[Recurrent neural networks (RNNs)](https://www.ibm.com/think/topics/recurrent-neural-networks) are designed to work on sequential data. Whereas conventional feedforward neural networks map a single input to a single output, RNNs map a *sequence* of inputs to an output by operating in a recurrent loop in which the output for a given step in the input sequence serves as input to the computation for the following step. In effect this creates an internal “memory,” called the *hidden state*, that allows RNNs to understand context and order.

![Diagram comparing folded and unrolled recurrent neural networks, showing X and Y nodes expanded across time steps.](https://assets.ibm.com/is/image/ibm/what-are-recurrent-neural-networks-combined:16x9?dpr=on%2C2.2222222222222223&wid=1584&hei=891)

### Transformers

[Transformer models](https://www.ibm.com/think/topics/transformer-model), first introduced in 2017, are largely responsible for the advent of LLMs and other pillars of generative AI, achieving state-of-the-art results across most subdomains of machine learning. Like RNNs, transformers are ostensibly designed for sequential data, but clever workarounds have enabled most data modalities to be processed by transformers. The unique strength of transformer models comes from their innovative [attention mechanism](https://www.ibm.com/think/topics/attention-mechanism), which enables the models to selectively focus on the parts of the input data most relevant at a specific moment in a sequence.

### Mamba models

[Mamba models](https://www.ibm.com/think/topics/mamba-model) are a relatively new neural network architecture, first introduced in 2023, based on a unique variation of [state space models (SSMs)](https://www.ibm.com/think/topics/state-space-model). Like transformers, Mamba models provide an innovative means of selectively prioritizing the most relevant information at a given moment. Mamba has recently emerged as a rival to the transformer architecture, particularly for LLMs.

## Machine learning use cases

Most applications of machine learning fall into one or more of the following categories, which are defined primarily by their use cases and the data modalities they operate upon.

### Computer vision

Computer vision is the subdomain of AI concerned with image data, video data other data modalities that require a model or machine to “see,” from healthcare diagnostics to facial recognition to self-driving cars. Notable subfields of computer vision include image classification, [object detection](https://www.ibm.com/think/topics/object-detection), [image segmentation](https://www.ibm.com/think/topics/image-segmentation) and [optical character recognition (OCR](https://www.ibm.com/think/topics/optical-character-recognition)).

### Natural language processing (NLP)

The field of [natural language processing (NLP)](https://www.ibm.com/think/topics/natural-language-processing) spans a diverse array of tasks concerning text, speech and other language data. Notable subdomains of NLP include [chatbots](https://www.ibm.com/think/topics/chatbots), [speech recognition](https://www.ibm.com/think/topics/speech-recognition), [language translation,](https://www.ibm.com/think/topics/machine-translation) [sentiment analysis](https://www.ibm.com/think/topics/sentiment-analysis), [text generation](https://www.ibm.com/think/topics/text-generation), [summarization](https://www.ibm.com/think/topics/text-summarization) and [AI agents](https://www.ibm.com/think/topics/ai-agents). In modern NLP, large language models continue to advance the state of the art at an unprecedented pace.

### Time series analysis

[Time series models](https://www.ibm.com/think/topics/time-series-model) are applied anomaly detection, market analysis and related pattern recognition or prediction tasks. They use machine learning on historical data for a variety of forecasting use cases.

### Image generation

[Diffusion models](https://www.ibm.com/think/topics/diffusion-models), [variational autoencoders (VAEs)](https://www.ibm.com/think/topics/variational-autoencoder) and [generative adversarial networks (GANs)](https://www.ibm.com/think/topics/generative-adversarial-networks) can be used to generate original images that apply pixel patterns learned from training data.

### Win the enterprise AI race

Join Arvind Krishna to see how IBM is enabling AI-first enterprises through hybrid cloud and emerging quantum capabilities.

## Machine learning operations (MLOps)

[Machine learning operations (MLOps)](https://www.ibm.com/think/topics/mlops) is a set of practices for implementing an assembly line approach to building, deploying and maintaining machine learning models.

Careful curation and preprocessing of training data, as well as appropriate [model selection](https://www.ibm.com/think/topics/model-selection), are crucial steps in the MLOps pipeline. Thoughtful post-training validation, from the design of benchmark datasets to the prioritization of particular performance [metrics](https://www.ibm.com/docs/en/watsonx/saas?topic=models-evaluation-metrics), is necessary to ensure that a model generalizes well (and isn’t just [overfitting](https://www.ibm.com/think/topics/overfitting) the training data).

Following deployment, models must be monitored for [model drift](https://www.ibm.com/think/topics/model-drift), inference efficiency issues and other adverse developments. A well-defined practice of [model governance](https://www.ibm.com/think/topics/model-governance) is essential to continued efficacy, especially in regulated or fast-changing industries.

## Machine learning libraries

A number of open source tools, libraries and frameworks exist for building, training and testing machine learning projects. While such libraries offer an array of pre-configured modules and abstractions to streamline the process of building ML-based models and workflows, practitioners will need to familiarize themselves with commonly used programming languages—particularly [Python](https://developer.ibm.com/languages/python/) —to make full use of them.

Prominent open source libraries, particularly for building deep learning models, include [PyTorch](https://www.ibm.com/think/topics/pytorch), [TensorFlow](https://developer.ibm.com/components/tensorflow/), Keras and the Hugging Face Transformers library.

Notable open source [machine learning libraries](https://www.ibm.com/think/topics/machine-learning-libraries) and toolkits focused on traditional ML include Pandas, [Scikit-learn](https://www.ibm.com/think/topics/scikit-learn), [XGBoost](https://www.ibm.com/think/topics/xgboost), [Matplotlib](https://dataplatform.cloud.ibm.com/exchange/public/entry/view/55f7f605960d9a4d578aeeaa2b62bdea), SciPy and NumPy among many others.

IBM itself maintains and updates a significant library of [tutorials](https://developer.ibm.com/technologies/machine-learning/tutorials/) for beginners and advanced ML practitioners alike.

## Author

Senior Staff Writer, AI Models

IBM Think

[Data science and MLOps for data leaders](https://www.ibm.com/forms/mkt-51585)

[

Join forces with other leaders to drive the three essential pillars of MLOps and trustworthy AI: trust in data, trust in models and trust in processes.

](https://www.ibm.com/forms/mkt-51585)

Next step in your AI journey

## Resources

[Types of Machine Learning Explained](https://www.ibm.com/think/topics/machine-learning-types)

[

Learn about the main categories of machine learning, from supervised and unsupervised learning to reinforcement, semi\_supervised, and self\_supervised approaches.

](https://www.ibm.com/think/topics/machine-learning-types)

1\. [“Some Studies in Machine Learning Using the Game of Checkers,”](https://people.csail.mit.edu/brooks/idocs/Samuel.pdf) *IBM Journal* (accessed through MIT), 3 July 1959  
2\. [“Using Decision Trees as an Expert System for Clinical Decision Support for COVID-19,“](https://www.i-jmr.org/2023/1/e42540) *Interactive Journal of Medical Research, Vol 12*, 30 January 2023  
3\. [“Kolmogorov’s Mapping Neural Network Existence Theorem,“](https://cs.uwaterloo.ca/~y328yu/classics/Hecht-Nielsen.pdf) *Proceedings of the IEEE First International Conference on Neural Networks* (accessed through University of Waterloo)*,* 1987  
4\. [“Multilayer Feedforward Networks with a Non-Polynomial Activation Function Can Approximate Any Function,“](https://archive.nyu.edu/bitstream/2451/14329/1/IS-92-13.pdf) Center for Research on Information Systems (New York University), March 1992