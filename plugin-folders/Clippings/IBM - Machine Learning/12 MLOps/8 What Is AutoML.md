---
title: What is AutoML?
source: https://www.ibm.com/think/topics/automl
author:
- '[[Ivan Belcic]]'
- '[[Cole Stryker]]'
published: 2025-01-03
created: 2026-08-31
description: "Automated machine learning (AutoML) is the practice of automating the end-to-end development of machine learning models (ML models)."
---

## What is AutoML?

Automated [machine learning](https://www.ibm.com/think/topics/machine-learning) (AutoML) is the practice of [automating](https://www.ibm.com/think/topics/automation) the end-to-end development of machine learning models (ML models). AutoML enables non-experts to create and implement [artificial intelligence (AI)](https://www.ibm.com/think/topics/artificial-intelligence) systems while streamlining AI workflows for [data scientists](https://www.ibm.com/think/topics/data-science) and developers.

AutoML tools simplify the process of building ML models. Users benefit from an intuitive interface through which they can create, train, validate and deploy [generative AI](https://www.ibm.com/think/topics/generative-ai) models and other [deep learning](https://www.ibm.com/think/topics/deep-learning) systems. AutoML facilitates AI implementation in regulated industries with its explainable and reproducible results.

Without AutoML, every step in the machine learning (ML) workflow—data preparation, data preprocessing, feature engineering and hyperparameter optimization—must be manually carried out. AutoML [democratizes machine learning](https://www.ibm.com/think/insights/democratizing-ai) by making it accessible to anyone who is interested in exploring its potential. Meanwhile, experienced [MLOps](https://www.ibm.com/think/topics/mlops) teams and data science professionals can automate the routine aspects of machine learning workflows while focusing on more demanding learning tasks.

## How does AutoML work?

[AutoML](https://developer.ibm.com/series/get-started-autoai) solutions work by constructing numerous [machine learning pipelines](https://www.ibm.com/think/topics/machine-learning-pipeline) to handle the intended task, then identifying the optimal choice. Model evaluation and model selection are automated as part of the iterative process of choosing the best model for the job. [Data visualization](https://www.ibm.com/think/topics/data-visualization) tools bring even more ease-of-use to the AutoML process.

The difference between AutoML and traditional machine learning is that AutoML automates nearly every stage of the machine learning pipeline. Traditional pipelines are time-consuming, resource-intensive and prone to human error. By comparison, advancements in AutoML have led to greater efficiency and better results.

A typical machine learning pipeline consists of the following steps:

### Data preparation and pre-processing

Data preparation is the process of collecting raw data and integrating it into a training dataset. Data preparation helps ensure that training data is free from bias and is what sets a model up for success: accurate data leads to accurate predictions and insights. As enterprises link AI systems with proprietary data stores, such as through [retrieval-augmented generation (RAG)](https://www.ibm.com/think/topics/retrieval-augmented-generation), data preparation is critical for reliable AI implementation.

Users connect the AutoML platform with the source of the training data—ideally a large dataset containing data that is ready for use in training. The data preparation phase occurs before an AutoML solution is deployed.

The AutoML solution steps in to further preprocess and clean the data. More thorough data preprocessing leads to better [AI model](https://www.ibm.com/think/topics/ai-model) performance.

When manually building models for [supervised learning](https://www.ibm.com/think/topics/supervised-learning) and [semi-supervised learning](https://www.ibm.com/think/topics/semi-supervised-learning) tasks, the training data must be manually labeled. Features and outputs must be selected based on the model’s intended use case. AutoML solutions can handle feature engineering on behalf of users to select the data features that are most likely to improve model performance.

#### Feature engineering

Data features or variables are the attributes of a dataset that machine learning models use to make decisions and predictions. For example, for a computer vision model built to identify plant species, data features might include leaf shape and color.

[Feature engineering](https://www.ibm.com/think/topics/feature-engineering) is the transformative process by which a data scientist draws new information from input data and prepares it for machine learning. Good engineering and feature selection can determine the difference between acceptable and high-quality model performance.

Automated feature engineering automates the process of exploring the feature space, filling missing values and selecting features to use. Manually building a single feature can take hours, and the number of features required for a bare minimum accuracy score—let alone a production-level accuracy baseline—can reach into the hundreds. Automated feature engineering reduces this phase from days to minutes.

In addition to the efficiency benefits, automated feature efficiency also increases [AI explainability](https://www.ibm.com/think/topics/explainable-ai)—important for strictly regulated industries such as healthcare or finance. Greater feature clarity makes models more compelling and actionable by discovering new organizational KPIs.

### Model selection, hyperparameter tuning and model training

What type of model is best for the intended use case? With traditional machine learning, model selection requires expert knowledge of AI model types along with their respective capabilities and limitations.

AutoML tools improve on traditional processes by automatically building and training several models simultaneously with a range of algorithms and hyperparameter configurations. Many AutoML solutions combine multiple models in a process known as [ensemble learning](https://www.ibm.com/think/topics/ensemble-learning).

#### Neural architecture search (NAS)

One of the most complicated, error-prone and time-consuming tasks when building deep neural networks is the creation of the neural architecture. Advanced tasks require multi-layered networks with complex hyperparameter configurations.

Neural architecture search (NAS) automates this process, reducing the time spent and potential for error. With the use of advanced algorithms, NAS identifies the optimal architecture based on the context and dataset. Recent advancements in NAS focus on the development of more efficient techniques to reduce the associated computational costs.

#### Hyperparameter optimization

Hyperparameters are the rules that govern the model’s learning process. Unlike the internal parameters that a model updates during training, hyperparameters are external to the model and are configured by data scientists. [Neural network](https://www.ibm.com/think/topics/neural-networks) structure is also defined by hyperparameters.

In small-scale data modeling contexts, hyperparameters can be manually configured and optimized through trial and error. But with deep learning applications, the number of hyperparameters grows exponentially. Automated hyperparameter optimization allows teams to iterate and experiment to discover the best hyperparameters across features and models.

[Hyperparameter tuning](https://www.ibm.com/think/topics/hyperparameter-tuning) is automated through advanced algorithms such as Bayesian optimization. Automated hyperparameter tuning frees data scientists to focus on the *why* of model creation rather than the *how* during the machine learning process*.* [Analytics](https://www.ibm.com/consulting/analytics) teams can instead focus on optimizing models for designated use cases—for example, to minimize false negatives in medical testing.

### Validation and testing

Data scientists need to validate a [machine learning algorithm](https://www.ibm.com/think/topics/machine-learning-algorithms)’s progress during training. After training, the model is tested with new data to evaluate its performance before real-world deployment. The model’s performance is evaluated with metrics including a confusion matrix, F1 score, ROC curve and others.

When training is complete, the AutoML tool tests each model to identify which performs best on the training and test datasets, then automatically selects the top-performing model for deployment.

### Model deployment

Model creation is just the first step in the product timeline. Completed models need to be made available to users, monitored for performance and maintained over time to help ensure reliability and accuracy. Without automation, development teams must write scripts and build systems to integrate the model into their operations and deliver it to its user base.

Many AutoML solutions include deployment tools for seamless real-world integration. Models can be deployed as a service accessible through a website, app or [API](https://www.ibm.com/think/topics/api) connection. AutoML platforms can automate model deployment into pre-existing product offerings, manage scaling, updates and versioning, and increase explainability with data visualization.

## AutoML use cases

The diverse array of AutoML tools means that the technique can be applied to a wide range of machine learning tasks, including:

- Classification

- Regression

- Computer vision

- Natural language processing

### Classification

[Classification](https://www.ibm.com/think/topics/classification-machine-learning) is the machine learning task of assigning data inputs into designated categories. Predictive models use input data features to predict the correct labels, or outputs. AutoML systems can build and test an array of algorithms, such as random forests and support vector machines (SVM), to process tabular data.

AutoML tools automatically detect patterns in labeled datasets and can design models for common classification tasks such as [fraud detection](https://www.ibm.com/think/topics/fraud-detection) and email spam filtering.

### Regression

Regression in machine learning is the challenge of using historical data to predict future values. [Linear regression](https://www.ibm.com/think/topics/linear-regression) predicts the value of a dependent variable based on one or more independent variables—for example, with risk analysis or market [forecasting](https://www.ibm.com/think/topics/forecasting). [Logistic regression](https://www.ibm.com/think/topics/logistic-regression) predicts the probability of a future event, such as a patient’s likelihood of contracting an illness, as opposed to a discrete value.

AutoML streamlines the process of establishing relationships between input variables and the target variables, notably with complex multivariate tasks.

### Computer vision

[Computer vision](https://www.ibm.com/think/topics/computer-vision) is the use of computers to process visual data, such as images and video. AutoML systems can generate models geared for vision-based classification tasks including [object detection](https://www.ibm.com/think/topics/object-detection), image classification and intelligent [optical character recognition](https://www.ibm.com/think/topics/optical-character-recognition). Use cases can cover content moderation and filtering, image tagging and other related tasks.

AutoML systems can also [fine-tune](https://www.ibm.com/think/topics/fine-tuning) models for use in more advanced computer vision contexts, such as with self-driving automobiles.

### Natural language processing (NLP)

[Natural language processing (NLP)](https://www.ibm.com/think/topics/natural-language-processing) enables AI systems to interpret textual inputs, such as user prompts and legal documents. [Chatbot](https://www.ibm.com/think/topics/chatbots) creation, multi-class and multi-label text classification, customer sentiment analysis, named entity recognition and language translation are all examples of complex NLP tasks that can be easily handled with AutoML.

Data scientists can create custom models with AutoML that are automatically optimized for strong performance in their intended use cases. Otherwise, when building NLP models manually, data scientists must either start from scratch or base their models on previous ones that might not perform as well as a tailored, automatically generated model.

## AutoML limitations

While AutoML brings many benefits to AI developers, it is not a wholesale replacement for human knowledge, experience, skills and creativity. The limitations of AutoML include:

- **High costs:** The more demanding the task, the more advanced the corresponding model must be. AutoML costs can quickly spiral out of control when the technique is applied to creating large, complex models.

- **Lack of** [**interpretability**](https://www.ibm.com/think/topics/interpretability)**:** AutoML-generated models can sometimes fall into the trap of “[black box AI](https://www.ibm.com/think/topics/black-box-ai),” where the model’s inner workings are obtuse. Human developers can build models that are designed in accordance with the principles of [explainable AI](https://www.ibm.com/think/topics/explainable-ai), but this isn’t guaranteed with AutoML solutions.

- **Risk of overfitting:** [Overfitting](https://www.ibm.com/think/topics/overfitting)—where a trained model hews too closely to its training data and fails to transfer its learning to real-world data—can be mitigated with human intervention and careful monitoring of the learning process.

- **Limited control:** Developers sacrifice control for efficiency with automation. In niche cases where highly customized models are needed, AutoML solutions can struggle to deliver an appropriate model.

- **Data reliance:** An AI model is as strong as its training data. Both human-made and AutoML-created models cannot perform well if they are not provided with high-quality data.

## AutoML tools

AI model creators have a wide range of AutoML tools at their fingertips. Options include:

- **AutoKeras:** An [open source](https://www.ibm.com/think/topics/open-source) tool built on the Keras library and TensorFlow.

- **Auto-PyTorch:** An AutoML solution designed to automate machine learning projects created with PyTorch.

- **Google Cloud AutoML:** Google’s AutoML solution available on its Cloud platform for machine learning.

- **Lale<sup>[1](#footnotes1)</sup>:** An open source semi-automated Python library that integrates seamlessly with scikit-learn pipelines.

- **Microsoft Azure AutoML:** Developers using Microsoft Azure can benefit from its AutoML capabilities.

- **Auto-Sklearn:** An open source AutoML platform based on the scikit-learn library.

## Footnotes

1. [Library for Semi-Automated Data Science](https://github.com/IBM/lale), Hirzel et al, IBM/lale, August 28, 2024[](https://github.com/IBM/lale/releases/tag/v0.8.4)
