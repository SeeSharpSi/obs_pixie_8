---
title: What is classification in machine learning?
source: https://www.ibm.com/think/topics/classification-machine-learning
author:
- '[[Ivan Belcic]]'
published: 2024-10-10
created: 2026-08-31
description: "Classification in machine learning is a predictive modeling process by which machine learning models use classification algorithms to predict the correct label for input data."
---

## What is classification in machine learning?

Classification in machine learning is a predictive modeling process by which [machine learning](https://www.ibm.com/topics/machine-learning) models use classification algorithms to predict the correct label for input data.

As [AI models](https://www.ibm.com/topics/ai-model) learn to analyze and classify data in their training datasets, they become more proficient at identifying various data types, discovering trends and making more accurate predictions.

At the end of the model training process, the model’s performance is evaluated by using test data. After the model performs consistently well, it’s introduced to unseen real-world data. The trained [neural networks](https://www.ibm.com/topics/neural-networks) apply what they learned during training to make successful predictions with new data.

## What are classification models?

A classification model is a type of machine learning model that sorts data points into predefined groups called classes. Classifiers learn class characteristics from input data, then learn to assign possible classes to new unseen data according to those learned characteristics.<sup>[1](#footnotes1)</sup>

## What are classification algorithms?

A classification algorithm is a categorization-focused [machine learning algorithm](https://www.ibm.com/think/topics/machine-learning-algorithms) that sorts input data into different classes or categories. [Artificial intelligence (AI)](https://www.ibm.com/topics/artificial-intelligence) models use classification algorithms to process input datasets against a specified classifier that sets the criteria for how the data should be sorted. Classification algorithms are widely used in [data science](https://www.ibm.com/topics/data-science) for forecasting patterns and predicting outcomes.

## How do classification models work?

Though no two machine learning classification algorithms are exactly alike, they all follow the same general two-step data classification process:

1. Learning
2. Classification

### Step 1: Learning

Classification has traditionally been a type of [supervised machine learning](https://www.ibm.com/topics/supervised-learning), which means it uses [labeled data](https://www.ibm.com/topics/data-labeling) to train models. In supervised learning, each data point in the training data contains input variables (also known as independent variables or features), and an output variable, or label.

In classification training, the model’s job is to understand the relationships between features and class labels, then apply those criteria to future datasets. Classification models use each data point’s features along with its class label to decode what features define each class. In mathematical terms, the model considers each data point as a tuple *x*. A tuple is an ordered numerical sequence that is represented as *x = (x1,x2,x3…xn).*

Each value in the tuple is a feature of the data point. By mapping training data with this equation, a model learns which features are associated with each class label.

The purpose of training is to minimize errors during predictive modeling. [Gradient descent](https://www.ibm.com/topics/gradient-descent) algorithms train models by minimizing the gap between predicted and actual results. Models can later be [fine-tuned](https://www.ibm.com/topics/fine-tuning) with more training to perform more specific tasks.

[Unsupervised learning](https://www.ibm.com/topics/unsupervised-learning) approaches to classification problems have been a key focus of recent research. Unsupervised learning methods enable models to discover patterns in unlabeled data by themselves. The lack of labels is what differentiates [unsupervised learning and supervised learning](https://www.ibm.com/think/topics/supervised-vs-unsupervised-learning).

Meanwhile, [semisupervised learning](https://www.ibm.com/topics/semi-supervised-learning) combines labeled and unlabeled data to train models for classification and regression purposes. In situations where obtaining large datasets of labeled data is not feasible, semisupervised learning is a viable alternative.

### Step 2: Classification

The second step in classification tasks is classification itself. In this phase, users deploy the model on a test set of new data. Previously unused data is used to evaluate model performance to avoid [overfitting](https://www.ibm.com/topics/overfitting): when a model leans too heavily on its training data and becomes unable to make accurate predictions in the real world.

The model uses its learned predicted function to classify new data across distinct classes according to each sample’s features. Users then evaluate model accuracy according to the number of correctly predicted test data samples.<sup>[2](#footnotes2)</sup>

## What types of classification are there?

Classification-based predictive modeling tasks are distinguished from each other based on the number of categories and the degree to which the categories are exclusive:

- **Binary classification** sorts data into two exclusive categories.

- **Multiclass classification** sorts data into more than two exclusive categories.

- **Multilabel classification** sorts data into nonexclusive categories.

- **Imbalanced** classification has an unequal distribution of data points across categories.

### Binary classification

In binary classification problems, a model predicts whether data fits into one of two classes. The learning techniques that are applied during training have models assess the features in the training data and predict which of two possible labels apply to each data point: positive or negative, true or false, and yes or no.

For example, a spam filter classifies emails as *spam* or *not spam.* In addition to spam detection, binary classification models make reliable behavioral predictors: will a potential customer churn or buy a certain product? They are also useful in [natural language processing](https://www.ibm.com/topics/natural-language-processing) (NLP), [sentiment analysis](https://www.ibm.com/topics/sentiment-analysis), image classification and [fraud detection](https://www.ibm.com/topics/fraud-detection).

### Multiclass classification

Multiclass classification problems classify data with more than two class labels, all of which are mutually exclusive. In this way, multiclass challenges are similar to binary classification tasks, except with more classes.

Multiclass classification models have many real-world use cases. In addition to determining whether emails are spam or not spam, a multiclass classification solution would also be able to determine whether emails are promotional or high-priority. An image classifier might classify images of pets by using a myriad of class labels, such as *dog*, *cat*, *llama*, *platypus and more*.

The goal of a multiclass classification learning method is to teach a model to assign input data accurately to a wider range of possible categories. A common objective function in multiclass training is categorical cross-entropy loss, which assesses the gap between the model’s predictions with test data versus the correct labels for each data point.

### Multilabel classification

Multilabel classification is used in situations where multiple nonexclusive labels can be assigned to each data point. Unlike exclusivity-based classification types, multilabel classification allows for the possibility that data points exhibit characteristics of more than one category—a closer reflection of the real-world ambiguity in big data collections.

Multilabel classification tasks are often accomplished by combining the predictions of several binary or multiclass classification models.

### Imbalanced classification

Imbalanced classification, in which some categories contain more data points than others, requires a specialized approach. As certain groups amass more data points, some classification models become biased toward those groups and increasingly predict in their favor.

Countermeasures include algorithms configured to more heavily weigh the cost of incorrect predictions, or sampling methods that either eliminate majority samples or oversample from underrepresented groups.

## Discrete and continuous predictions

Predictive models output two types of predictions:

- **Discrete predictions** definitively sort data into distinct categories.

- **Continuous predictions** assign a class based on a probability.

### Discrete predictions

Discrete predictions are the predicted class labels for each data point. For example, a healthcare predictor can classify medical patients as *diabetic* or *nondiabetic* based on health data. The classes *diabetic* and *nondiabetic* are the discrete categorical predictions.

### Continuous predictions

Continuous classifiers assign class predictions as continuous probabilities called confidence scores. These probabilities are values between 0 and 1, representing percentages. The diabetes predictor model might classify a patient as *diabetic* with a 0.82 probability. The model believes that the patient has an 82% chance of having diabetes.

Researchers typically evaluate models by using discrete predictions while using continuous predictions as thresholds. A classifier ignores any prediction under a certain threshold. If our diabetes predictor has a threshold of 0.4 (40%) and classifies a patient as diabetic with a probability of 0.35 (35%), then the model will ignore that label and not assign the patient to the *diabetic* class.<sup>[3](#footnotes3)</sup>

## Classification versus regression

The difference between classification and regression is that while classification predicts a data point’s category, regression predicts an associated real numerical value. Both classification and regression are types of predictive modeling but with distinct use cases.

Classification models sort data points into categories. Classification is the process of training a [deep learning](https://www.ibm.com/topics/deep-learning) model to discover the function that categorizes data points.

Regression models consider various data points to predict a continuous numerical value for another variable. For example, a regression model in the workplace might predict a worker’s salary based on age, experience, location and education.

In practice, the two are often closely related. For example, the logistic regression algorithm uses regression to fulfill classification tasks.

## Types of classification algorithms

There are many different types of classification algorithms. While they have overlapping use cases, some are more suited to particular applications than others. Some of the most popular classification algorithms include:

- Logistic regression

- Decision tree

- Random forest

- Support vector machine (SVM)

- K-nearest neighbors

- Naive Bayes

Many of these algorithms can be readily implemented in Python with the use of scikit-learn libraries. Meanwhile, ensemble methods and transformer models are newer developments being applied to classification problems.

### Logistic regression

[Logistic regression](https://www.ibm.com/topics/logistic-regression) algorithms are often used to perform classification tasks. [Logistic regression](https://www.ibm.com/topics/logistic-regression) is a probability classifier derived from [linear regression](https://www.ibm.com/topics/linear-regression) models. Linear regression uses one or more independent variables to predict the value of an independent variable. This value can be any continuous rational number.

Logistic regression is a modification to the linear regression such as the output value (or independent variable) is limited to any value between 0 and 1. It does this by applying a logit—or log odds—transformation to the standard linear regression formula.<sup>[4](#footnotes4)</sup>

![logit equation for logistic regression](https://assets.ibm.com/is/image/ibm/class-models-logit-reg-formula?ts=1763388178532&dpr=off)

Logistic regression models are used for binary classification in multivariate regression problems: when considering multiple variables, does the data point belong to one category or the other? Common applications are fraud detection and biomedical predictions. For instance, logistic regression has been implemented to help predict patient mortality induced by trauma and coronary heart disease.<sup>[5](#footnotes5)</sup>

### Decision tree

Used for both classification and regression, [decision trees](https://www.ibm.com/topics/decision-trees) split datasets into progressively smaller groups in a series of binary classification judgments. The resulting structure resembles a tree, branching outward from an initial judgment into subsequent leaves or nodes.

![A diagram of a decision tree algorithm](https://assets.ibm.com/is/image/ibm/Decision-Tree?ts=1763388178858&dpr=off)

The flowchart-like nature of decision trees makes them one of the more intuitive models for business users to understand. Easy to visualize, decision trees bring transparency to the classification process by clearly representing the decision processes and criteria used to categorize data.

### Random forest

The [random forest](https://www.ibm.com/topics/random-forest) is an ensemble technique combining the output of multiple decision trees into a single result. The resulting “forest” improves prediction accuracy over that of a single tree while countering overfitting. Like decision trees, random forests can handle both classification and regression tasks.

![A diagram of a random forest algorithm](https://assets.ibm.com/is/image/ibm/ICLH_Diagram_Batch_03_27-RandomForest?ts=1763388179193&dpr=off)

Random forest algorithms create multiple decision trees for each task, aggregate the prediction of all the trees, then choose the most popular answer as the definitive result. Each tree considers a random subset of data features, helping ensure low correlation between trees.

### Support vector machine (SVM)

[Support vector machine (SVM)](https://www.ibm.com/topics/support-vector-machine) algorithms plot data points into a multidimensional space, with the number of dimensions corresponding to the number of features in the data. The algorithm’s goal is to discover the optimal line—also known as a hyperplane or decision boundary—that best divides the data points into categories.

The optimal hyperplane is the one with the widest margin, which is the distance between the hyperplane and the nearest data points in each class. These nearby data points are known as support vectors. Models that separate data with a hyperplane are linear models, but SVM algorithms can also handle nonlinear classification tasks with more complex datasets.

Logistic regression, decision trees, random forests and SVM algorithms are all examples of eager learners: algorithms that construct models from training data and then apply those models to future predictions. Training takes longer, but after the algorithm builds a good model, predictions are quicker.

### K-nearest neighbors (KNN)

[K-nearest neighbors (KNN)](https://www.ibm.com/topics/knnhttps:/www.ibm.com/topics/knn) algorithms map data points onto a multidimensional space. It then groups those data points with similar feature values into separate groups, or classes. To classify new data samples, the classifier looks at the *k* number of points nearest to the new data, counts the members of each class comprising the neighboring subset, and returns that proportion as the class estimate for the new data point.

In other words, the model assigns a new data point to whichever class comprises the majority of that point’s neighbors. KNN models are lazy learners: algorithms that don’t immediately build a model from training data, but instead refer to training data and compare new data to it. It typically takes longer for these models to make predictions than eager learners.

KNN models typically compare distance between data points with Euclidean distance:<sup>[6](#footnotes6)</sup>

![Euclidean distance equation](https://assets.ibm.com/is/image/ibm/content-based-filtering-euclidean-distance?ts=1763388179811&dpr=off)

Approximate nearest neighbor (ANN) is a variant of KNN. In high-dimensional data spaces, it is computationally expensive to find a data point’s exact neighbors. [Dimensionality reduction](https://www.ibm.com/topics/dimensionality-reduction) and ANN are two solutions to this issue.

Rather than find a data point’s exact nearest neighbor, ANN finds an approximate nearest neighbor within a given distance. Recent research has shown promising results for ANN in the context of multilabel classification.<sup>[7](#footnotes7)</sup>

### Naive Bayes

Based on Bayes’ theorem, [Naive Bayes](https://www.ibm.com/topics/naive-bayes) classifiers calculate posterior probability for class predictions. Naive Bayes updates initial class predictions, or prior probabilities, with each new piece of data. [](#footnotes8)

With a diabetes predictor, the patient’s medical data—blood pressure, age, blood sugar levels, and more—are the independent variables. A Bayesian classifier combines the current prevalence of diabetes across a population (prior probability) with the conditional probability of the patient’s medical data values appearing in someone with diabetes.

Naive Bayes classifiers follow the Bayes’ Rule equation:<sup>[8](#footnotes8)</sup>

![Bayes rule equation](https://assets.ibm.com/is/image/ibm/class-models-bayes-formula?ts=1763388180189&dpr=off)

Naive Bayes is known as a generative classifier. By using an observation’s variable values, the Bayesian classifier calculates which class is most likely to have generated the observation.

[Natural language processing](https://www.ibm.com/topics/natural-language-processing) (NLP) researchers have widely applied Naïve Bayes for text classification tasks, such as [sentiment analysis](https://www.ibm.com/topics/sentiment-analysis). Using a [bag of words](https://www.ibm.com/topics/bag-of-words) model, in which each word constitutes a variable, the Naive Bayes classifier predicts whether a positive or negative class produced the text in question.<sup>[9](#footnotes9)</sup>

### Ensemble methods

Ensemble methods and machine learning techniques combine multiple smaller models into a single classifier for improved results. Deep ensemble methods bring multiple deep learning models together to create even more powerful ensemble classifiers. Ensembles with deep learners can handle complex multilabel classification tasks.

Gradient boosting is an ensemble method shown to increase prediction accuracy. It is a type of [boosting](https://www.ibm.com/topics/boosting), an ensemble technique in which multiple weak learners learn from each other in sequence to improve results with each iteration.

### Transformer models in classification

While typically used for NLP tasks, transformer models have also been applied to classification problems. Transformer models such as GPT and Claude use self-attention mechanisms to focus on the most relevant parts of an input dataset. [Positional encoding](https://www.ibm.com/think/topics/positional-encoding) is used to inform the model about where in a sequence each data point lies.

## Classification learning evaluation methods

Researchers and developers choose certain evaluation metrics for classification models depending on the specific classification task. All measure the accuracy with which learners, or classifiers, accurately predict model classes.

Some of the most popular evaluation metrics are:

- Accuracy

- Precision

- Recall

- F1 score

- Confusion matrix

- ROC curve

True positives (TP) are those data samples the model correctly predicts in their respective class. False positives (FP) are those negative-class instances incorrectly identified as positive cases. False negatives (FN) are actual positive instances erroneously predicted as negative. True negatives (TN) are the actual negative class instances the model accurately classifies as negative.

### Accuracy

Accuracy is the ratio of true positives to all predictions in the dataset. It measures how often a machine learning model correctly predicts an outcome—in this case, the right class for a data point.

Accuracy gives a high-level overview of a model’s performance, but doesn’t reveal if a model is better at predicting certain classes over others. In cases where datasets are highly imbalanced, focusing on accuracy can lead a model to ignore all smaller datasets and predict all outcomes as the majority class. In this situation, the overall accuracy will still be high.

A spam filter would have high accuracy if most of its guesses are correct, even if it misses most of the actual spam emails.

### Precision

Precision, or *positive predicted value (PPV)*, is the proportion of positive class predictions that belong to the specified class. Precision reveals whether a model is correctly predicting for the target class, making it useful for imbalanced classification tasks or when the cost of false positives is high.

In a spam filter, precision shows how many of the detected spam emails are spam. Models that incorrectly classify data as false positives have low precision, while models with fewer false positives have high precision.<sup>[10](#footnotes10)</sup>

![Precision formula](https://assets.ibm.com/is/image/ibm/equation-pre?ts=1763388181392&dpr=off)

### Recall

Also known as *sensitivity* or *true positive rate* (TPR), recall denotes the percentage of class instances detected by a model. Recall shows how often a model detects members of the target class in the dataset. For a spam filter, recall shows the amount of actual spam emails that the model identifies as spam.<sup>[11](#footnotes11)</sup>

![The image displays the mathematical formula for recall in a clean, minimal design. The text shows 'Recall =' followed by the fraction 'TP / TP + FN'. This represents recall as true positives divided by the sum of true positives and false negatives. The typography is simple and clear on a light background, emphasizing the equation.](https://assets.ibm.com/is/image/ibm/equation-rec?ts=1787568252660&dpr=off)

### F1 score

Precision and recall share an inverse relationship. As a classifier returns more true positives showing increased recall, it can misclassify noninstances, generating false positives and decreasing precision. The F1 score resolves this tradeoff by combining precision and recall to represent a model’s total class-wise accuracy.<sup>[12](#footnotes12)</sup>

![F-score formula](https://assets.ibm.com/is/image/ibm/equation-f1?ts=1763388181980&dpr=off)

## Data visualization and model evaluation

Data visualization tools help illustrate findings in data analysis. Data scientists and machine learning researchers use two primary tools for visualizing classifier performance:

- **The confusion matrix**, a table showing predicted versus real values.

- **The ROC curve**, a graph depicting the proportion of true positives to true negatives.

### Confusion matrix

The [confusion matrix](https://www.ibm.com/topics/confusion-matrix) is a table representing both the predicted and actual values of a class. The boxes of the matrix depict the numbers of true positives, false positives, false negatives and true negatives. The total of these values is the model’s total number of predictions.<sup>[13](#footnotes13)</sup>

![sample binary confusion matrix](https://assets.ibm.com/is/image/ibm/binary-matrix?ts=1763388182423&dpr=off)

### ROC curve

A receiver operating characteristic (ROC) curve visualizes the proportion of true positives to true negatives. The chart plots the true positive rate against the true negative rate for each threshold used in model classification. The area under curve (AUC) statistic arises from the ROC curve.

AUC measures how likely a randomly selected positive has a higher confidence score than a random negative. AUC values range from 0 to 1. A score of 0 signifies that the model scores all negatives with higher probabilities than positives, while 1 means that the model scores every positive with higher probability.<sup>[14](#footnotes14)</sup>

## Footnotes

1. Chris Drummond, “Classification,” *Encyclopedia of Machine Learning and Data Mining*, Springer, 2017.

2. Jaiwei Han, Micheline Kamber, and Jian Pei, *Data Mining: Concepts and Techniques*, 3rd edition, Morgan Kaufman, 2012.

3. Max Kuhn and Kjell Johnson, *Applied Predictive Modeling*, Springer, 2016.

4. Max Kuhn and Kjell Johnson, *Applied Predictive Modeling*, Springer, 2016. Gareth James, Daniela Witten, Trevor Hastie, Robert Tibshirani, and Jonathan Taylor, *An Introduction to Statistical Learning with Applications in Python*, Springer, 2023

5. Lisa X. Deng, Abigail May Khan, David Drajpuch, Stephanie Fuller, Jonathan Ludmir, Christopher E. Mascio, Sara L. Partington, Ayesha Qadeer, Lynda Tobin, Adrienne H. Kovacs, and Yuli Y. Kim, "Prevalence and Correlates of Post-traumatic Stress Disorder in Adults With Congenital Heart Disease," *The American Journal of Cardiology*, Vol. 117, No. 5, 2016, pp. 853-857, [https://www.sciencedirect.com/science/article/abs/pii/S0002914915023590](https://www.sciencedirect.com/science/article/abs/pii/S0002914915023590)

6. Max Kuhn and Kjell Johnson, *Applied Predictive Modeling*, Springer, 2016. Kevin Murphy, *Machine Learning: A Probabilistic Perspective*, MIT Press, 2012.

7. Ville Hyvönen, Elias Jääsaari, Teemu Roos, “A Multilabel Classification Framework for Approximate Nearest Neighbor Search,” *Journal of Machine Learning Research*, Vol. 25, No. 46, 2024, pp. 1−51, [https://www.jmlr.org/papers/v25/23-0286.html](https://www.jmlr.org/papers/v25/23-0286.html)

8. Max Kuhn and Kjell Johnson, *Applied Predictive Modeling*, Springer, 2016. William Bolstad and James Curran, *Introduction to Bayesian Statistics*, 3rd edition, Wiley, 2016.

9. Daniel Jurafsky and James Martin, *Speech and Language Processing: An Introduction to Natural Language Processing, Computational Linguistics, and Speech Recognition*, 3rd edition, 2023.

10. Ethan Zhang and Yi Zhang, “Precision,” *Encyclopedia of Database Systems*, Springer, 2018.

11. Ethan Zhang and Yi Zhang, “Recall,” *Encyclopedia of Database Systems*, Springer, 2018.

12. Ben Carterette, “Precision and Recall,” *Encyclopedia of Database Systems*, Springer, 2018.

13. Kai Ming Ting, “Confusion matrix,” *Encyclopedia of Machine Learning and Data Mining*, Springer, 2017.

14. Peter Flach, “ROC Analysis,” *Encyclopedia of Machine Learning and Data Mining*, Springer, 2017.
