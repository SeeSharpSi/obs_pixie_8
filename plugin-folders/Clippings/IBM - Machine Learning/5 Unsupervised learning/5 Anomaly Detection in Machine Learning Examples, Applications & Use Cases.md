---
title: "Anomaly detection in machine learning: Finding outliers for optimization of business functions"
source: https://www.ibm.com/think/topics/machine-learning-for-anomaly-detection
author:
- '[[Camilo Quiroz-Vázquez]]'
published: 2024-07-18
created: 2026-08-31
description: "Powered by AI, machine learning techniques are leveraged to detect anomalous behavior through three different detection methods."
---

As organizations collect larger data sets with potential insights into business activity, detecting anomalous data, or outliers in these data sets, is essential in discovering inefficiencies, rare events, the root cause of issues, or opportunities for operational improvements. But what is an anomaly and why is detecting it important?

Types of anomalies vary by enterprise and business function. [Anomaly detection](https://www.ibm.com/think/topics/anomaly-detection) simply means defining “normal” patterns and metrics—based on business functions and goals—and identifying data points that fall outside of an operation’s normal behavior. For example, higher than average traffic on a website or application for a particular period can signal a [cybersecurity](https://www.ibm.com/think/topics/cybersecurity) threat, in which case you’d want a system that could automatically trigger fraud detection alerts. It could also just be a sign that a particular marketing initiative is working. Anomalies are not inherently bad, but being aware of them, and having data to put them in context, is integral to understanding and protecting your business.

The challenge for IT departments working in data science is making sense of expanding and ever-changing data points. In this blog we’ll go over how machine learning techniques, powered by artificial intelligence, are leveraged to detect anomalous behavior through three different anomaly detection methods: supervised anomaly detection, unsupervised anomaly detection and semi-supervised anomaly detection.

## Supervised learning

Supervised learning techniques use real-world input and output data to detect anomalies. These types of anomaly detection systems require a data analyst to label data points as either normal or abnormal to be used as training data. A machine learning model trained with labeled data will be able to detect outliers based on the examples it is given. This type of machine learning is useful in known outlier detection but is not capable of discovering unknown anomalies or predicting future issues.

Common machine learning algorithms for supervised learning include:

- [**K-nearest neighbor (KNN) algorithm**](https://www.ibm.com/think/topics/knn)**:** This algorithm is a density-based classifier or regression modeling tool used for anomaly detection. Regression modeling is a statistical tool used to find the relationship between labeled data and variable data. It functions through the assumption that similar data points will be found near each other. If a data point appears further away from a dense section of points, it is considered an anomaly.
- **Local outlier factor (LOF**): Local outlier factor is similar to KNN in that it is a density-based algorithm. The main difference being that while KNN makes assumptions based on data points that are closest together, LOF uses the points that are furthest apart to draw its conclusions.

## Unsupervised learning

Unsupervised learning techniques do not require labeled data and can handle more complex data sets. Unsupervised learning is powered by [deep learning](https://www.ibm.com/think/topics/deep-learning) and [neural networks](https://www.ibm.com/think/topics/neural-networks) or auto encoders that mimic the way biological neurons signal to each other. These powerful tools can find patterns from input data and make assumptions about what data is perceived as normal.

These techniques can go a long way in discovering unknown anomalies and reducing the work of manually sifting through large data sets. However, data scientists should monitor results gathered through unsupervised learning. Because these techniques are making assumptions about the data being input, it is possible for them to incorrectly label anomalies.

[Machine learning](https://www.ibm.com/think/topics/machine-learning) algorithms for unstructured data include:

**K-means:** This algorithm is a data visualization technique that processes data points through a mathematical equation with the intention of clustering similar data points. “Means,” or average data, refers to the points in the center of the cluster that all other data is related to. Through data analysis, these clusters can be used to find patterns and make inferences about data that is found to be out of the ordinary.

**Isolation forest:** This type of anomaly detection algorithm uses unsupervised data. Unlike supervised anomaly detection techniques, which work from labeled normal data points, this technique attempts to isolate anomalies as the first step. Similar to a “[random forest](https://www.ibm.com/topics/random-forest#:~:text=Random%20forest%20is%20a%20commonly,both%20classification%20and%20regression%20problems.),” it creates “decision trees,” which map out the data points and randomly select an area to analyze. This process is repeated, and each point receives an anomaly score between 0 and 1, based on its location to the other points; values below .5 are generally considered to be normal, while values that exceed that threshold are more likely to be anomalous.**<sup> </sup>**Isolation forest models can be found on the free machine learning library for Python, [scikit-learn](https://scikit-learn.org/stable/).

**One-class support vector machine (SVM):** This anomaly detection technique uses training data to make boundaries around what is considered normal. Clustered points within the set boundaries are considered normal and those outside are labeled as anomalies.

## Semi-supervised learning

Semi-supervised anomaly detection methods combine the benefits of the previous two methods. Engineers can apply unsupervised learning methods to automate feature learning and work with unstructured data. However, by combining it with human supervision, they have an opportunity to monitor and control what kind of patterns the model learns. This usually helps to make the model’s predictions more accurate.

[Linear regression](https://www.ibm.com/topics/linear-regression#:~:text=Resources-,What%20is%20linear%20regression%3F,is%20called%20the%20independent%20variable.): This predictive machine learning tool uses both dependent and independent variables. The independent variable is used as a base to determine the value of the dependent variable through a series of statistical equations. These equations use labeled and unlabeled data to predict future outcomes when only some of the information is known.

## Anomaly detection use cases

Anomaly detection is an important tool for maintaining business functions across various industries. The use of supervised, unsupervised and semi-supervised learning algorithms will depend on the type of data being collected and the operational challenge being solved. Examples of anomaly detection use cases include:

## Supervised learning use cases:

### Retail

Using labeled data from a previous year’s sales totals can help predict future sales goals. It can also help set benchmarks for specific sales employees based on their past performance and overall company needs. Because all sales data is known, patterns can be analyzed for insights into products, marketing and seasonality.

### Weather forecasting

By using historical data, supervised learning algorithms can assist in the prediction of weather patterns. Analyzing recent data related to barometric pressure, temperature and wind speeds allows meteorologists to create more accurate forecasts that take into account changing conditions.

## Unsupervised learning use cases:

### Intrusion detection system

These types of systems come in the form of software or hardware, which monitor network traffic for signs of security violations or malicious activity. Machine learning algorithms can be trained to detect potential attacks on a network in real-time, protecting user information and system functions.

These algorithms can create a visualization of normal performance based on time series data, which analyzes data points at set intervals for a prolonged amount of time. Spikes in network traffic or unexpected patterns can be flagged and examined as potential security breaches.

### Manufacturing

Making sure machinery is functioning properly is crucial to manufacturing products, optimizing quality assurance and maintaining supply chains. Unsupervised learning algorithms can be used for predictive maintenance by taking unlabeled data from sensors attached to equipment and making predictions about potential failures or malfunctions. This allows companies to make repairs before a critical breakdown happens, reducing machine downtime.

## Semi-supervised learning use cases:

### Medical

Using machine learning algorithms, medical professionals can label images that contain known diseases or disorders. However, because images will vary from person to person, it is impossible to label all potential causes for concern. Once trained, these algorithms can process patient information and make inferences in unlabeled images and flag potential reasons for concern.

### Fraud detection

Predictive algorithms can use semi-supervised learning that require both labeled and unlabeled data to detect fraud. Because a user’s credit card activity is labeled, it can be used to detect unusual spending patterns.

However, fraud detection solutions do not rely solely on transactions previously labeled as fraud; they can also make assumptions based on user behavior, including current location, log-in device and other factors that require unlabeled data.

## Observability in anomaly detection

Anomaly detection is powered by solutions and tools that give greater observability into performance data. These tools make it possible to quickly identify anomalies, helping prevent and remediate issues. IBM® Instana™ Observability leverages artificial intelligence and machine learning to give all team members a detailed and contextualized picture of performance data, helping to accurately predict and proactively troubleshoot errors.

IBM watsonx.ai™ offers a powerful generative AI tool that can analyze large data sets to extract meaningful insights. Through fast and comprehensive analysis, IBM watson.ai can identify patterns and trends which can be used to detect current anomalies and make predictions about future outliers. Watson.ai can be used across industries for a variety business needs.
