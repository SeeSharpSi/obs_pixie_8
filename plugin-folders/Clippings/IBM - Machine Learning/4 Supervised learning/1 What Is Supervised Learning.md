---
title: What is supervised learning?
source: https://www.ibm.com/think/topics/supervised-learning
author:
- '[[Ivan Belcic]]'
- '[[Cole Stryker]]'
published: 2024-12-16
created: 2026-05-21
description: "Supervised learning is a machine learning technique that uses labeled data sets to train artificial intelligence algorithms models to identify the underlying patterns and relationships between input features and outputs. The goal of the learning process is to create a model that can predict correct outputs on new real-world data."
---

## What is supervised learning?

Supervised learning is a [machine learning](https://www.ibm.com/think/topics/machine-learning) technique that uses labeled data sets to train [artificial intelligence](https://www.ibm.com/think/topics/artificial-intelligence) (AI) models to identify the underlying patterns and relationships. The goal of the learning process is to create a model that can predict correct outputs on new real-world data.

Labeled data sets consist of sample data points along with the correct outputs or answers. As input data is fed into the [machine learning algorithm](https://www.ibm.com/think/topics/machine-learning-algorithms), it adjusts its parameters until the model has been fitted appropriately. Labeled training data provides a “[ground truth](https://www.ibm.com/think/topics/ground-truth),” explicitly teaching the model to identify the relationships between features and [data labels](https://www.ibm.com/think/topics/data-labeling).

Supervised machine learning helps organizations solve various real-world problems at scale, such as classifying spam or predicting stock prices. It can be used to build highly accurate machine learning models.

### What is ground truth data?

Ground truth data is verified against real-world outcomes, often through human annotation or measurement, and is used to train, validate and test models. As the name implies, ground truth data has been confirmed to be true—it is reflective of real-world values and outcomes. Ground truth reflects the ideal outputs for any given input data.

Supervised learning relies on ground truth data to teach a model the relationships between inputs and outputs. The labeled datasets used in supervised learning are ground truth data. Trained models apply their understanding of the that data to make predictions based on new, unseen data.

## How supervised learning works

Supervised learning techniques use a labeled training dataset to understand the relationships between inputs and output data. Data scientists manually create ground truth training datasets containing input data along with the corresponding labels. Supervised learning trains the model to apply the correct outputs to unseen data in real-world use cases.

During training, the model’s algorithm processes large datasets to explore potential correlations between inputs and outputs. Then, model performance is evaluated with test data to find out whether it was trained successfully. Cross-validation is the process of testing a model using a different portion of the dataset.

The [gradient descent](https://www.ibm.com/think/topics/gradient-descent) family of algorithms, including stochastic gradient descent (SGD), are the most commonly used optimization algorithms, or learning algorithms, when training [neural networks](https://www.ibm.com/think/topics/neural-networks) and other machine learning models. The model’s optimization algorithm assesses accuracy through the [loss function](https://www.ibm.com/think/topics/loss-function): an equation that measures the discrepancy between the model’s predictions and actual values.

The loss function measures how far off predictions are from actual values. Its gradient indicates the direction in which the model’s parameters should be adjusted to reduce error. Throughout training, the optimization algorithm updates the model’s parameters—its operating rules or “settings”—to optimize the model.

Because large datasets typically contain many features, data scientists can simplify this complexity through [dimensionality reduction](https://www.ibm.com/think/topics/dimensionality-reduction). This data science technique reduces the number of features to those most crucial for predicting data labels, which preserves accuracy while increasing efficiency.

### An example of supervised learning in action

As an example of supervised learning, consider an image classification model created to recognize images of vehicles and determine which type of vehicle they are. Such a model can power the CAPTCHA tests many websites use to detect spam bots.

To train this model, [data scientists](https://www.ibm.com/think/topics/data-science) prepare a labeled training dataset containing numerous vehicle examples along with the corresponding vehicle type: car, motorcycle, truck, bicycle and more. The model’s algorithm attempts to identify the patterns in the training data that cause an input—vehicle images—to receive a designated output—vehicle type.

The model’s guesses are measured against actual data values in a test set to determine whether it has made accurate predictions. If not, the training cycle continues until the model’s performance has reached a satisfactory level of accuracy. The principle of generalization refers to a trained model’s ability to make appropriate predictions on new data from the same distribution as its training data.

## Types of supervised learning

Supervised learning tasks can be broadly divided into classification and regression problems:

### Classification

[Classification in machine learning](https://www.ibm.com/think/topics/classification-machine-learning) uses an algorithm to sort data into categories. It recognizes specific entities within the dataset and attempts to determine how those entities should be labeled or defined. Common classification algorithms are linear classifiers, support vector machines (SVM), [decision trees](https://www.ibm.com/think/topics/decision-trees), k-nearest neighbor (KNN), [logistic regression](https://www.ibm.com/think/topics/logistic-regression) and random forest.

Neural networks excel at handling complex classification problems. A [neural network](https://www.ibm.com/think/topics/neural-networks) is a [deep learning](https://www.ibm.com/think/topics/deep-learning) architecture that processes training data with layers of nodes that mimic the human brain. Each node is made up of inputs, weights, a bias (or threshold) and an output. If an output value exceeds a preset threshold, the node “fires” or activates, passing data to the next layer in the network.

### Regression

Regression is used to understand the relationship between dependent and independent variables. In regression problems, the output is a continuous value, and models attempt to predict the target output. Regression tasks include projections for sales revenue or financial planning.

Regression algorithms include [linear regression](https://www.ibm.com/think/topics/linear-regression), [lasso regression](https://www.ibm.com/think/topics/lasso-regression), [ridge regression](https://www.ibm.com/think/topics/ridge-regression) and polynomial regression are three examples of regression algorithms.

### Ensemble learning

[Ensemble learning](https://www.ibm.com/think/topics/ensemble-learning) is a meta-approach to supervised learning in which multiple models are trained on the same classification or regression task. The results of all the models in the pool are aggregated to discover the best overall approach to solving the challenge.

The individual algorithms within the larger ensemble model are known as *weak learners* or *base models*. Some weak learners have high bias, while others have high variance. In theory, the results mitigate the [bias-variance tradeoff](https://www.ibm.com/think/topics/bias-variance-tradeoff) by combining the best parts of each.

## Supervised learning algorithms

Optimization algorithms such as gradient descent train a wide range of machine learning algorithms that excel in supervised learning tasks.￼

- **Naive Bayes:** [Naive Bayes](https://www.ibm.com/think/topics/naive-bayes) is a classification algorithm that adopts the principle of class conditional independence from Bayes’ theorem. This means that the presence of one feature does not impact the presence of another in the probability of an outcome, and each predictor has an equal effect on that result.

Naïve Bayes classifiers include multinomial, Bernoulli and Gaussian Naive Bayes. This technique is often used in text classification, spam identification and recommendation systems.

- **Linear regression:** Linear regression is used to identify the relationship between a continuous dependent variable and one or more independent variables. It is typically used to make predictions about future outcomes.

Linear regression expresses the relationship between variables as a straight line. When there is one independent variable and one dependent variable, it is known as simple linear regression. As the number of independent variables increases, the technique is referred to as multiple linear regression.

- **Nonlinear regression:** Sometimes, an output cannot be reproduced from linear inputs. In these cases, outputs must be modeled with a nonlinear function. Nonlinear regression expresses a relationship between variables through a nonlinear, or curved, line. Nonlinear models can handle complex relationships with many parameters.

- **Logistic regression:** Logistic regression handles categorical dependent variables—when they have binary outputs, such as *true or false* or *positive or negative*. While linear and logistic regression models seek to understand relationships between data inputs, logistic regression mainly solves binary classification problems, such as spam identification.

- **Polynomial regression:** Similar to other regression models, polynomial regression models a relationship between variables on a graph. The functions used in polynomial regression express this relationship though an exponential degree. Polynomial regression is a special case of regression where input features are raised to powers, allowing linear models to fit nonlinear patterns.

- **Support vector machine (SVM):** A [support vector machine](https://www.ibm.com/think/topics/support-vector-machine) is used for both data classification and regression. That said, it usually handles classification problems. Here, SVM separates the classes of data points with a decision boundary or hyperplane. The goal of the SVM algorithm is to plot the hyperplane that maximizes the distance between the groups of data points.

- **K-nearest neighbor:** [K-nearest neighbor (KNN)](https://www.ibm.com/think/topics/knn) is a nonparametric algorithm that classifies data points based on their proximity and association to other available data. This algorithm assumes that similar data points can be found near each other when plotted mathematically.

Its ease of use and low calculation time make it efficient when used for recommendation engines and image recognition. But as the test dataset grows, the processing time lengthens, making it less appealing for classification tasks.

- **Random forest:** [Random forest](https://www.ibm.com/think/topics/random-forest) is a flexible supervised machine learning algorithm used for both classification and regression purposes. The “forest” references a collection of uncorrelated [decision trees](https://www.ibm.com/think/topics/decision-trees) which are merged to reduce variance and increase accuracy.

## Supervised learning versus other learning methods

Supervised learning is not the only learning method for training machine learning models. Other [types of machine learning](https://www.ibm.com/think/topics/machine-learning-types) include:

- Unsupervised learning

- Semi-supervised learning

- Self-supervised learning

- Reinforcement learning

### Supervised versus unsupervised learning

The [difference between supervised learning and unsupervised learning](https://www.ibm.com/think/topics/supervised-vs-unsupervised-learning) is that [unsupervised machine learning](https://www.ibm.com/think/topics/unsupervised-learning) uses unlabeled data without any objective ground truth. The model is left to discover patterns and relationships in the data on its own. Many [generative AI](https://www.ibm.com/think/topics/generative-ai) models are initially trained with unsupervised learning and later with supervised learning to increase domain expertise.

Unsupervised learning can help solve for clustering or association problems in which common properties within a dataset are uncertain. Common clustering algorithms are hierarchical, K-means and Gaussian mixture models.

#### Pros of unsupervised learning

- **Exploratory analysis:** Unsupervised learning is useful when “what to look for” isn’t known. It can find hidden structures or anomalies in data that humans might not expect.
- **No data labeling:** Most real-world data is unlabeled, and labeling data takes a lot of time and effort.
- **Flexibility:** Unsupervised learning models can quickly adapt to new data due to their ability to process data autonomously.
- **Scalability:** Without the need for ground truth labels, unsupervised learning techniques are easily scalable to massive datasets.

#### Cons of unsupervised learning

- **Imprecise outcomes:** Without the foundation of ground truth, it is less immediately clear whether an unsupervised learning model has been trained correctly.
- **Sensitivity:** Noisy datasets can adversely affect training outcomes. [Feature engineering](https://www.ibm.com/think/topics/feature-engineering) can help normalize datasets for smoother unsupervised learning.
- **Reliance on good data:** All training needs good data. But without any objective ground truth, bias or other errors in the data can result in models that reinforce those misunderstandings.

### Supervised versus semi-supervised learning

[Semi-supervised learning](https://www.ibm.com/think/topics/semi-supervised-learning) involves training a model on a small portion of labeled input data along with a larger portion of unlabeled data. Because it can be time-consuming and costly to rely on domain expertise to label data appropriately for supervised learning, semi-supervised learning can be an appealing alternative.

#### Pros of semi-supervised learning

- **Less reliant on labeling:** Compared to supervised learning, semi-supervised learning requires less labeling, which lowers the barriers to entry for model training.
- **Hidden pattern discovery:** Like unsupervised learning, semi-supervised learning’s use of unlabeled data can lead to the discovery of patterns, relationships and anomalies that might otherwise go unnoticed.
- **More flexible:** Semi-supervised learning creates a foundation through ground truth data, then augments that with unlabeled datasets to make models more generalizable.

#### Cons of semi-supervised learning

- **Noise sensitivity:** Unlabeled datasets with high degrees of noise can throw off the training results, weakening model performance.
- **Bias sensitivity:** if unlabeled datasets aren’t screen for implicit bias, those biases can be transferred to the models being trained.
- **More complex:** Bringing labeled and unlabeled data together in a single training process can involve complex [data processing](https://www.ibm.com/think/topics/data-processing) techniques or require more computational resources.

### Supervised versus self-supervised learning

[Self-supervised learning](https://www.ibm.com/think/topics/self-supervised-learning) (SSL) is often described as bridging supervised and unsupervised learning. Rather than use the manually created labels of supervised learning datasets, SSL tasks are configured so that the model can generate its own supervisory signals—implicit or pseudo-labels—and discern ground truth from unstructured data. Then, the model’s loss function uses those labels in place of actual labels to assess model performance.

SSL is often used with [transfer learning](https://www.ibm.com/think/topics/transfer-learning), a process in which a [pretrained model](https://www.ibm.com/think/topics/pretrained-model) is applied to a downstream task. Self-supervised learning sees widespread use in computer vision and [natural language processing (NLP)](https://www.ibm.com/think/topics/natural-language-processing) tasks requiring large datasets that are prohibitively expensive and time-consuming to label.

#### Pros of self-supervised learning

- **Efficiency:** Rather than have data scientists label data points, SSL automates the labeling process by transferring the task to the model.
- **Scalability:** SSL’s lower reliance on manual data labeling lends it well to scaling with larger pools of unlabeled data.
- **Low reliance on labeling:** In cases where labeled ground truth data is sparse, SSL makes up the shortfall through model-generated understanding.
- **Versatility:** Self-supervised models learn rich, transferable features that can be fine-tuned for many domain-specific and multimodal tasks.

#### Cons of self-supervised learning

- **Compute-intensive:** Processing unlabeled data sets and generating labels takes a lot of computing power.
- **Complex:** The process of creating pretext tasks for supervised learning—the initial learning phase—requires a high degree of expertise.
- **Potentially unreliable:** Like any learning technique that removes human supervision, the results hinge on the data being free of excess noise, implicit bias and other factors that can negatively affect the model’s understanding.

### Supervised versus reinforcement learning

[Reinforcement learning](https://www.ibm.com/think/topics/reinforcement-learning) trains autonomous agents, such as robots and self-driving cars, to make decisions through environmental interactions. Reinforcement learning does not use labeled data and also differs from unsupervised learning in that it teaches by trial-and-error and reward, not by identifying underlying patterns within datasets.

#### Pros of reinforcement learning

- **Solves complex tasks:** The trial-and-error training process can lead a model to figure out how to approach complex strategic challenges.
- **Not reliant on labeling:** Models learn experientially, not theoretically through matching inputs with outputs.
- **Self-correcting:** Models hone their own behavior as they get things wrong during training.
- **Adaptable:** Models can adapt to new information and changing circumstances in which outcomes are not predefined.

#### Cons of reinforcement learning

- **Prone to inconsistent results:** Trial-and-error learning can seem haphazard and unpredictable, especially when first beginning training.
- **Environmental data needs:** Reinforcement learning requires models to learn from the consequences of their actions, which in turn requires large amounts of environmental data. However, agents can also learn in simulated environments.
- **Reward hacking:** Models can exploit loopholes in the reward algorithm to generate rewards without adequately accomplishing their tasks.
- **Task-specific:** Reinforcement learning excels in training models for a specific function. Those models can struggle to transfer what they have learned to new tasks.

## Real-world supervised learning use cases

Supervised learning models can build and advance business applications, including:

- **Image- and object-recognition:** Supervised learning algorithms can be used to locate, isolate and categorize objects out of videos or images, making them useful with [computer vision](https://www.ibm.com/think/topics/computer-vision) and image analysis tasks.

- **Predictive** [**analytics**](https://www.ibm.com/consulting/analytics)**:** Supervised learning models create predictive analytics systems to provide insights. This allows enterprises to anticipate results based on an output variable and make data-driven decisions, in turn helping business leaders justify their choices or pivot for the benefit of the organization.

Regression also allows healthcare providers to predict outcomes based on patient criteria and historical data. A predictive model might assess a patient’s risk for a specific disease or condition based on their biological and lifestyle data.

- **Customer sentiment analysis:** Organizations can extract and classify important pieces of information from large volumes of data—including context, emotion and intent—with minimal human intervention. [Sentiment analysis](https://www.ibm.com/think/topics/sentiment-analysis) gives a better understanding of customer interactions and can be used to improve brand engagement efforts.

- **Customer segmentation:** Regression models can predict customer behavior based on various traits and historical trends. Businesses can use predictive models to segment their customer base and create buyer personas to improve marketing efforts and product development.

- **Spam detection:** Spam detection is another example of a supervised learning model. Using supervised classification algorithms, organizations can train databases to recognize patterns or anomalies in new data to organize spam and non-spam-related correspondences effectively.

- **Forecasting:** Regressive models excel at [forecasting](https://www.ibm.com/think/topics/forecasting) based on historical trends, making them suitable for use in the financial industries. Enterprises can also use regression to predict inventory needs, estimate employee salaries and avoid potential supply chain hiccups.

- **Recommendation engines:** With supervised learning models in play, content providers and online marketplaces can analyze customer choices, preferences and purchases and build [recommendation engines](https://www.ibm.com/think/topics/recommendation-engine) that offer tailored recommendations more likely to convert.

## Challenges of supervised learning

Although supervised learning can offer businesses advantages such as deep data insights and improved automation, it might not be the best choice for all situations.

- **Personnel limitations:** Supervised learning models can require certain levels of expertise to structure accurately.

- **Human involvement:** Supervised learning models are incapable of self-learning. Data scientists must validate the models’ performance output.

- **Time requirements:** Training datasets are large and must be manually labeled, which makes the supervised learning process time-intensive.

- **Inflexibility:** Supervised learning models struggle to label data outside the bounds of their training datasets. An unsupervised learning model might be more capable of dealing with new data.

- **Bias:** Datasets risk a higher likelihood of human error and bias, resulting in algorithms learning incorrectly. Bias can arise from imbalanced training datasets, poor annotation practices or historical inequities reflected in the data.

- **Overfitting:** Supervised learning can sometimes result in [overfitting](https://www.ibm.com/think/topics/overfitting): where a model becomes too closely tailored to its training dataset. High accuracy in training can indicate overfitting as opposed to generally strong performance. Avoiding overfitting requires that models be tested with data that is different from the training data.
