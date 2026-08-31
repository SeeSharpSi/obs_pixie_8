---
title: What is model drift?
source: https://www.ibm.com/think/topics/model-drift
author: null
published: 2024-11-21
created: 2026-08-31
description: "Model drift refers to the degradation of model performance due to changes in data or changes in relationships between input and output variables."
---

## What is model drift?

Model drift refers to the degradation of [machine learning](https://www.ibm.com/think/topics/machine-learning) model performance due to changes in data or in the relationships between input and output variables. Model drift—also known as model decay—can negatively impact model performance, resulting in faulty decision-making and bad predictions.

To detect and [mitigate drift](https://www.ibm.com/products/watson-studio/drift), organizations can monitor and manage performance on their data and artificial intelligence (AI) platform. If not properly monitored over time, even the most well-trained, unbiased AI model can “drift” from its original parameters and produce unwanted results when deployed. Drift detection is a core component of strong [AI governance](https://www.ibm.com/topics/ai-governance).

Models built with [historical data](https://www.ibm.com/docs/en/spss-modeler/18.3.0?topic=nuggets-continuous-machine-learning) can quickly become stagnant. Often, new data points are always coming in—new variations, new patterns, new trends—that the old historical data cannot capture. If an AI model’s training doesn’t align with incoming data, it can’t accurately interpret that data or use that live data to reliably make accurate predictions.

If drift isn’t detected and mitigated quickly, it can digress further, increasing the harm to operations. Drift detection empowers organizations to continually receive accurate output from their models.

## Causes of model drift

The world is constantly changing, so with constantly changing data, the models used to make sense of the world must be constantly reviewed and updated. Here are 3 types of model drift that need to be addressed, each with a different cause.

### 1. Concept drift

Concept drift occurs when there is a divergence between the input variables and the target variable, at which point the algorithm begins to provide incorrect answers because the definitions are no longer valid. The shift in independent variables can take effect over various periods that are:

#### Seasonal

The concept drift reoccurs and recedes regularly, such as for the seasonality of buying behavior in response to weather changes. In wintry climates, snow shovel and snow blower sales will normally increase in the late autumn and early winter. Geographic adjustments must also be made for expected snowfall.

#### Sudden

An unexpected development can drive new buying patterns. An example would be the sudden publicity around ChatGPT creating increased demand for AI hardware and software products, and a boost to the stock value of AI-related companies. A forecasting model trained before those news stories were published might not predict subsequent results.

Another example is the arrival of the Covid-19 pandemic, which also created a sudden shift in behavior: sales of games and exercise equipment spiked, while restaurants and hotels saw far fewer visitors.

#### Gradual

Some drift happens gradually or at an expected pace. For example, spammers and hackers have used various tools and tricks over the years. As protective software and spam filters have improved, bad actors have advanced accordingly. Any AI designed to protect digital interactions needs to keep pace; a static model will soon be useless.

### 2. Data drift

Data drift— also known as covariate shift—happens when the underlying data distribution of the input data has changed. In retail, the sales of a product might be impacted by the introduction of another new product or the retirement of a competing product. Or if a website is first adopted by young people, but then gains acceptance from older people, the original model based on the usage patterns of younger users might not perform as well with the older user base.

### 3. Upstream data change

An upstream data change occurs when there is a change in the data pipeline. For example, upstream data might be changed to a different currency, such as USD versus euros or measurements in miles rather than kilometers or temperatures in Fahrenheit instead of Celsius. Such a change would throw off a model that wasn’t built to account for the change in how the data was labeled.

## How can drift be detected?

Businesses and data scientists can use various data drift detection methods to stay on top of machine learning model drift and correct course before their models become obsolete.

Many of the most popular are time distribution-based methods that measure potential deviations between two probability distributions. If the results are noticeably divergent, then the statistical properties of the input data have likely changed, resulting in data drift.

Data drift detection is a core aspect of [data observability](https://www.ibm.com/topics/data-observability), which is the practice of continually monitoring the quality and reliability of data flowing through an organization. The Python coding language is especially popular in data science for use in the creation of open source drift detectors.

### Kolmogorov-Smirnov (K-S) test

The Kolmogorov-Smirnov (K-S) test measures whether two data sets originate from the same distribution. In the field of data science, the K-S test is nonparametric, which means that it does not require the distribution to meet any preestablished assumptions or criteria.

Data scientists use the Kolmogorov-Smirnov test for two primary reasons:

- To determine whether a data sample comes from a certain population.
- To compare two data samples and see whether they originate from the same population.

If the results of the K-S test show that two data sets appear to come from different populations, then data drift has likely occurred, making the K-S test a reliable drift detector.

### Wasserstein distance

Wasserstein distance, named for mathematician Leonid Vaserstein, uses a simple metaphor as a visualization of data drift severity. It imagines two small piles of earth, with data drift as the amount of work required to create one pile from dirt taken from the other. For this reason, the Wasserstein distance is also known in computer and data science as the earth mover’s distance (EMD).

As a drift detection method, Wasserstein distance compares training data to new input data being fed into a machine learning model. It excels in identifying complex relationships between features and can navigate outliers for consistent results.

### Population stability index

The population stability index (PSI) compares the distribution of a categorical feature across two data sets to determine the degree to which the distribution has changed over time.

A larger divergence in distribution, represented by a higher PSI value, indicates the presence of model drift. PSI can evaluate both independent and dependent features; those which change based on other variables.

If the distribution of one or more categorical features returns a high PSI, the machine model is likely in need of recalibration or even rebuilding.

## Best practices to avoid model drift

Businesses can better manage data drift detection and remediation by following these best practices:

### Automate drift detection

The accuracy of an AI model can degrade within days of deployment because production data diverges from the model’s training data. This can lead to incorrect predictions and significant risk exposure.

To protect against model drift and bias, organizations should use an AI drift detector and monitoring tools that automatically detect when a model’s accuracy decreases (or drifts) below a preset threshold.

This program for detecting model drift should also track which transactions caused the drift, enabling them to be relabeled and used to retrain the model, restoring its predictive power during runtime.

Statistical drift detection uses statistical metrics to compare and analyze data samples. This is often easier to implement because most of the metrics are already in use within the enterprise. Model-based drift detection measures the similarity between a point or groups of points versus the reference baseline.

### Automate model testing

Organizations should test their AI models, especially generative AI models, periodically throughout their lifecycle. This testing ideally includes:

1. Validation of models in preproduction with tests to detect bias and drift, and then generating test reports.
2. Transferring the successful predeployment test configurations for a model to the deployed version of the model and continued automated testing.
3. Synchronizing model, data and test result information with systems of record.
4. Automation that can provide consistent and reliable notifications and provide more time for teams to focus on model development instead of model monitoring.

### Manage in a unified environment

According to [a Forrester Total Economic Impact study](https://www.ibm.com/account/reg/signup?formid=urx-47469), “By building, running and managing models in a unified data and AI environment, [organizations] can ensure that the AI models remain fair, explainable and compliant anywhere. This end-to-end AI approach also uniquely empowers an organization to detect and help correct model drift and bias, and manage model risk when an AI model is in production.”

A best practice is to manage all models from a central dashboard. An integrated approach can help an organization track metrics continually and alert teams to drift in accuracy and data consistency through development, validation and deployment. A centralized, holistic view can help organizations break down silos and provide more transparency across the entire data lineage.

### Perform continual drift monitoring

Detect drift scenarios and magnitude through an AI model that compares production and training data and model predictions in real time. This way, drift can be found quickly and retraining can begin immediately. This detection is iterative, just as [machine learning operations](https://www.ibm.com/think/topics/mlops) (MLOps) are iterative.

### Analyze the root cause

Time-based analysis helps see how drift evolved and when it occurred. For example, if checks are run weekly, that will show how drift evolved each day.

Analyzing timelines can also be helpful to determine whether the drift was gradual or sudden. The [explainable AI](https://www.ibm.com/topics/explainable-ai) approach applies this transparency to AI use and helps organizations monitor how and why their models delivered the results that they did.

### Retrain models

Use a new training data set that has more recent and relevant samples added to it. The goal is to get your large language models (LLM) back into production quickly and correctly. If retraining the model doesn’t resolve the issue, then a new model may be needed. [Large language model operations (LLMOps)](https://www.ibm.com/topics/llmops) techniques can aid organizations in monitoring and retraining their LLMs.

### Update ML models in real time

Rather than train a model with batch data, organizations can practice “online learning” by having their [machine learning](https://research.ibm.com/publications/machine-learning-model-drift-detection-via-weak-data-slices) (ML) models updated using the latest real-world data when it is available.

### Verify the input data

A model can appear to drift because the data used to train it is different from the actual production data that will be used. In a medical use case, if high-resolution scans are used in training, but only low-resolution scans are available in the field, then the results are incorrect.
