---
title: Model selection in machine learning
source: https://www.ibm.com/think/topics/model-selection
author:
- '[[Ivan Belcic]]'
- '[[Cole Stryker]]'
published: 2025-07-15
created: 2026-08-31
description: "Model selection in machine learning is the process of choosing the most appropriate machine learning model for the selected task. The selected model is usually the one that generalizes best to unseen data while most successfully meeting relevant performance metrics."
---

## What is model selection in machine learning?

Model selection in machine learning is the process of choosing the most appropriate machine learning model (ML model) for the selected task. The selected model is usually the one that generalizes best to unseen data while most successfully meeting relevant model performance metrics.

The ML model selection process is a comparison of different models from a pool of candidates. Machine learning specialists evaluate how each ML model performs, then choose the best model based on a set of evaluation metrics.

Central to most machine learning tasks is the challenge of recognizing patterns in data, then making predictions on new data based on those patterns. Choosing the best-performing predictive model leads to more accurate predictions and a more reliable ML application.

## Why is model selection important?

[AI model](https://www.ibm.com/think/topics/ai-model) selection is important because it determines how well the [machine learning](https://www.ibm.com/think/topics/machine-learning) system will perform. Different models each have strengths and weaknesses, and choosing the right one directly affects project success. Model selection is an early stage in the greater [machine learning pipeline](https://www.ibm.com/think/topics/machine-learning-pipeline) for creating and deploying ML models.

Some tasks call for complex models that can capture the details of a large [dataset](https://www.ibm.com/think/topics/dataset), but which can struggle with generalization to new data. They might also come with higher compute and resource demands. Other tasks are better for smaller, simple models designed for one specific purpose.

Choosing the right model for the job can:

- **Optimize efficiency:** The strongest among all the candidate models will balance the trade-off between performance and generalizability with complexity and resource usage.
- **Maximize model performance:** A tool is only as strong as the task to which it is applied. Testing and evaluating candidate models reveals the best-performing model for the job, giving the AI application its best chance at real-world viability.
- **Drive project success:** Model complexity directly affects training time and resource requirements as well as outcomes. Predictive models run from simple to complex. Simpler models are quicker and cheaper to train, while complex models require more data, money and time.

## The model selection process

The model selection process is designed to produce a model that is custom-fit to the target use case. Machine learning specialists outline the problem, choose from the types of models likely to perform well and finally train and test candidate models to identify the best overall choice.

The stages of the model selection process typically include:

- Establishing the ML challenge
- Choosing candidate models
- Determining model evaluation metrics
- Model training and evaluation

### Establishing the ML challenge

Depending on the nature of task, some [machine learning algorithms](https://www.ibm.com/think/topics/machine-learning-algorithms) are better choices than others. ML challenges usually fall into one of three categories:

- **Regression problems** task models with identifying the relationships between input features and a selected continuous output variable, such as a price. Examples of regression problems include predicting salary benchmarks or the likelihood of natural disasters based on weather conditions. The model’s predictions are based on relevant input features, such as the time of year or demographic information. [Time series forecasting](https://www.ibm.com/think/insights/time-series-forecasting) is a type of regression challenge that predicts the value of a variable over time. [Time series models](https://www.ibm.com/think/topics/time-series-model) are a compute-efficient model class specializing in this challenge.
- [**Classification**](https://www.ibm.com/think/topics/classification-models) **problems** sort data points into categories based on a set of input variables. Examples of classification problems include object recognition and email spam filters. The [training set](https://www.ibm.com/think/topics/training-data) might include data points with labeled outputs so the model can learn the association between inputs and outputs. This practice is known as [supervised learning](https://www.ibm.com/think/topics/supervised-learning).
- [**Clustering**](https://www.ibm.com/think/topics/clustering) **problems** group data points based on similarities. Clustering isn’t quite the same as classification in that the goal is to discover groups within the data points, rather than sort the data points into known categories. Models must discern similarities themselves in an [unsupervised learning](https://www.ibm.com/think/topics/unsupervised-learning) environment. Market segmentation is an example of a clustering challenge.

### Determining model evaluation metrics

The testing process compares candidate models and assesses their performance against a set of pre-selected evaluation metrics. While many metrics exist, some are better for certain types of ML challenges than others.

Model evaluation metrics for classification include:

- **Accuracy:** the percentage of correct predictions out of the total predictions made.
- **Precision:** the ratio of true positive predictions among all positive predictions, measuring the accuracy of positive predictions.
- **Recall:** the ratio of true positive predictions among all actual positive instances, measuring the model’s proficiency in identifying positive instances.
- **F1 score:** combines precision and recall for an overall look at the model’s ability to recognize and correctly classify positive instances.
- **Confusion matrix:** summarizes the performance of a classifier model by displaying true positives, false positives, true negatives and false negatives in a table.
- **AUC-ROC:** a graph that plots the true positive and false positive rates as a receiver operating characteristic (ROC) curve. The area under the curve (AUC) shows the model’s performance.

Regression evaluation metrics include:

- **Mean squared error (MSE):** averages the difference between the squares of the differences between predicted and actual values. MSE is highly sensitive to outliers and severely penalizes large errors.
- **Root mean squared error (RMSE):** the square root of MSE, displaying the error rate in the same units as the variable and increasing the interpretability of the metric. MSE displays the same error in units squared.
- **Mean absolute error (MAE):** the mean of the differences between actual and practiced values for the target variable. MAE is less sensitive than MSE.
- **Mean absolute percentage error (MAPE):** conveys the mean absolute error as a percentage rather than in the units of the predicted variable, making it easier to compare models.
- **R-squared:** gives a benchmark measurement of the model’s performance between 0 and 1. However, the r-squared value can be artificially inflated by the addition of more features.
- **Adjusted r-squared:** reflects the contributions of features which improve the model’s performance while ignoring irrelevant features.

### Model training and evaluation

[Data scientists](https://www.ibm.com/think/topics/data-science) prepare for model training and evaluation by dividing the available data into several sets. The training dataset is used for model training, during which candidate models learns to recognize patterns and relationships in the data points. Then, the model’s performance is checked with a different portion of the dataset.

The simplest and quickest form of testing is the train-test split. Data scientists split the dataset into two portions, one for training and one for testing. The model is not exposed to the test split until after training—the test set serves as a stand-in for the new, unseen data the model will process in the real world.

## Model selection techniques

Model creators have access to a wide range of model selection techniques. Some pertain to the initial setup and architecture of the model, in turn influencing its behavior. Others provide a more nuanced and rigorous model evaluation or predict how models will perform on a specified dataset.

Model selection techniques include:

- Hyperparameter tuning
- Cross-validation
- Bootstrapping
- Information criteria

### Hyperparameter tuning

[Hyperparameter tuning](https://www.ibm.com/think/topics/hyperparameter-tuning) is the process of optimizing a model’s hyperparameters, which are external settings that determine the model’s structure and behavior. Models also have internal parameters that update in real time during training. Internal parameters govern how a model processes data. Complex models, such as those used for [generative AI](https://www.ibm.com/think/topics/generative-ai) (genAI), can have over one trillion parameters.

Hyperparameter tuning is not the same as [fine-tuning](https://www.ibm.com/think/topics/fine-tuning) a model, which is when a model is further trained or adjusted after the initial training stage (known as pre-training).

Several notable hyperparameter tuning techniques are:

- **Grid search:** Every possible hyperparameter combination is trained, tested and evaluated. An exhaustive, brute-force method, grid search is likely to discover the single best hyperparameter combination. However, it is time-consuming and resource-intensive.
- **Random search:** Samples of hyperparameter combinations are selected at random, with each sample in the subset being used to train and test a model. Random search is an alternative to grid search when the latter is unfeasible.
- **Bayesian optimization:** A probabilistic model is used to predict which hyperparameter combinations are the most likely to result in top model performance. Bayesian optimization is an iterative method that improves with each round of training and testing, and it works well with large hyperparameter spaces.

### Cross validation

In the k-fold cross-validation resampling system, the data is divided into *k* sets, or folds. The training data comprises *k*-1 subsets, and the model is validated on the remaining set. The process iterates so that each subset serves as the validation set. Data points are sampled without replacement, which means that each data point appears once per iteration.

K-fold cross validation provides a more holistic overview of a model’s performance than a single train-test split.

### Bootstrapping

Bootstrapping is a resampling technique similar to cross-validation, except that the data points are sampled with replacement. This means that sampled data points can appear in multiple folds.

### Information criteria

Information criteria compare the degree of model complexity with its chances of overfitting or underfitting the dataset. [Overfitting](https://www.ibm.com/think/topics/overfitting) means that the model adapts too closely to the training set and cannot generalize to new data. [Underfitting](https://www.ibm.com/think/topics/underfitting) is the inverse, where a model is insufficiently complex to capture relationships between data points.

The Akaike Information Criterion (AIC) and Bayesian Information Criterion (BIC) both incentivize adopting the model with the lowest possible complexity that can adequately handle the dataset.

## Factors affecting model selection

Model performance is far from the sole determinant of what makes a model “best.” Other factors can be equally, if not more, relevant to the decision.

- **Data complexity:** The more complex a dataset, the more complex the model needed to process it. But applying too complex a model can lead to overfitting. And a model that is too simple can fail to adequately capture the patterns in the data. The appropriate model will capably and efficiently process data while avoiding overfitting.
- **Data quality:** Data preprocessing and [feature selection](https://www.ibm.com/think/topics/feature-selection) are two data science processes that prepare data for machine learning applications. Outliers, missing data and other blockers affect some models more than others, but they can be overcome with [synthetic data](https://www.ibm.com/think/topics/synthetic-data), regularization and other countermeasures.
- **Interpretability:** [Interpretability](https://www.ibm.com/think/topics/intelligent-automation) or explainability is the degree to which a model’s workings can be understood by human observers. A “black box” model has little to no interpretability—its decision-making workflow is largely a mystery. With sensitive business applications such as [intelligent automation](https://www.ibm.com/think/topics/intelligent-automation) and AI-powered decision-making, interpretability is a priority for organizations adhering to responsible AI use guidelines. Certain industries such as healthcare and finance have extensive data privacy and other regulations, further emphasizing the need for clear interpretability.
- **Efficiency and resource use:** Practical limitations such as compute availability and finances can rule out some models entirely. Deep neural networks require massive amounts of data—and money—to train and operate. While such models are exciting, they are not right for every job. AIC and BIC can help ML project leaders make informed decisions and keep model complexity down.

## LLM selection

LLMs are the core artificial intelligence models for many business applications, such as [AI agents](https://www.ibm.com/think/topics/ai-agents), [RAG](https://www.ibm.com/think/topics/retrieval-augmented-generation)-powered [question-answering](https://www.ibm.com/think/topics/text-generation) or customer service [chatbots](https://www.ibm.com/think/topics/chatbots) with automated [text generation](https://www.ibm.com/think/topics/text-generation). [Natural language processing (NLP)](https://www.ibm.com/think/topics/natural-language-processing) is the use of machine learning algorithms to understand and generate human language, and LLMs are a specific type of NLP model.

Notable LLMs include OpenAI’s [GPT](https://www.ibm.com/think/topics/gpt) family—such as [GPT-4o](https://www.ibm.com/think/topics/gpt-4o) and GPT-3.5, some of the models behind ChatGPT—as well as Anthropic’s [Claude](https://www.ibm.com/think/topics/claude-ai), Google’s [Gemini](https://www.ibm.com/think/topics/google-gemini) and Meta’s Llama 3. All LLMs are capable of handling complex tasks, but the specific needs of a machine learning project can help dictate the right LLM for the job.

Choosing the right LLM comes down to a range of factors including:

- **Specific use case:** The machine learning challenge directly affects the LLM selection process. One LLM might be better with lengthy document comprehension and summarization, while another might be easier to fine-tune for domain-specific uses.
- **Performance:** Just like other models, LLMs can be benchmarked against each other to evaluate performance. LLM benchmarks include metrics for [reasoning](https://www.ibm.com/think/topics/ai-reasoning), coding, math, latency, comprehension and general knowledge. Weighing the needs of a project versus benchmark performance can help determine the best LLM to choose for high-quality outputs.
- **Open versus closed source:** Open source models enable observers to monitor how the model reaches its decisions. Different LLMs can be prone to biases and hallucinations in various ways: when they generate predictions that do not reflect real-world outcomes. When content moderation and bias prevention are paramount, limiting choices to open source providers can help shape the LLM selection process.
- **Resource use and cost:** LLMs are resource-hungry models. Many LLMs are powered by hyperscale datacenters filled with hundreds of thousands of graphics processing units (GPUs) or more. LLM providers also charge differently for [API](https://www.ibm.com/think/topics/api) connections to their models. The scalability of a model and its pricing system directly affects project scope.
