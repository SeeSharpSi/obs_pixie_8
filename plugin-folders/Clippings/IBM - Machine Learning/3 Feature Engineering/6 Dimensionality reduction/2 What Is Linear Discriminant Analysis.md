---
title: What is linear discriminant analysis (LDA)?
source: https://www.ibm.com/think/topics/linear-discriminant-analysis
author: null
published: 2024-12-03
created: 2026-05-21
description: "Linear discriminant analysis (LDA) is an approach used in supervised machine learning to solve multi-class classification problems."
---

## What is LDA?

Linear discriminant analysis (LDA) is an approach used in supervised machine learning to solve multi-class classification problems. LDA separates multiple classes with multiple features through data [dimensionality reduction](https://www.ibm.com/think/topics/dimensionality-reduction). This technique is important in data science as it helps optimize [machine learning](https://www.ibm.com/think/topics/machine-learning) models.

Linear discriminant analysis, also known as normal discriminant analysis (NDA) or discriminant function analysis (DFA), follows a generative model framework. This means LDA algorithms model the data distribution for each class and use [Bayes' theorem](https://plato.stanford.edu/entries/bayes-theorem/)<sup>1</sup> to classify new data points. Bayes calculates conditional probabilities—the probability of an event given some other event has occurred. LDA algorithms make predictions by using Bayes to calculate the probability of whether an input data set will belong to a particular output. For a review of Bayesian statistics and how it impacts supervised learning algorithms, see [Naïve Bayes classifiers](https://www.ibm.com/topics/naive-bayes).

LDA works by identifying a linear combination of features that separates or characterizes two or more classes of objects or events. LDA does this by projecting data with two or more dimensions into one dimension so that it can be more easily classified. The technique is, therefore, sometimes referred to as dimensionality reduction. This versatility ensures that LDA can be used for multi-class data classification problems, unlike [logistic regression](https://www.ibm.com/topics/logistic-regression?mhq=logistic%20regression&mhsrc=ibmsearch_a), which is limited to binary classification. LDA is thus often applied to enhance the operation of other learning classification algorithms such as [decision tree](https://www.ibm.com/topics/decision-trees), [random forest](https://www.ibm.com/topics/random-forest) or support vector machines (SVM).

![Graph showing the effect on a data cluster before and after applying LDA methods](https://assets.ibm.com/is/image/ibm/applying-linear-discriminant-analysis-lda-to-a-data-cluster?ts=1763386304141&dpr=off)

### The origin of linear discriminant analysis

Linear discriminant analysis (LDA) is based on Fisher’s linear discriminant, a statistical method developed by Sir Ronald Fisher in the 1930s and later simplified by C. R. Rao as a multi-class version. Fisher's method aims to identify a linear combination of features that discriminates between two or more classes of labeled objects or events.

Fisher’s method reduces dimensions by separating classes of projected data. Separation means maximizing the distance between the projected means and minimizing the projected variance within classes.

### A practical application of LDA

Suppose that a bank is deciding whether to approve or reject loan applications. The bank uses two features to make this decision: the applicant's credit score and annual income.

Here, the two features or classes are plotted on a 2-dimensional (2D) plane with an X-Y axis. If we tried to classify approvals using just one feature, we might observe overlap. By applying LDA, we can draw a straight line that completely separates these two class data points. LDA achieves this by using the X–Y axis to create a new axis, separating the different classes with a straight line and projecting data onto the new axis.

To create this new axis and reduce dimensionality, LDA follows these criteria:

- Maximize the distance between the means of two classes.
- Minimize the variance within individual classes.

### Properties and assumptions of LDA

LDAs operate by projecting a feature space, that is, a dataset with n-dimensions, onto a smaller space "k", where k is less than or equal to n – 1, without losing class information. An LDA model comprises the statistical properties that are calculated for the data in each class. Where there are multiple features or variables, these properties are calculated over the [multivariate Gaussian distribution](https://online.stat.psu.edu/stat508/lesson/9/9.2/9.2.2)<sup>3</sup>.

The multivariates are:

- Means
- Covariance matrix, which measures how each variable or feature relates to others within the class

The statistical properties that are estimated from the data set are fed into the LDA function to make predictions and create the LDA model. There are some constraints to bear in mind, as the model assumes the following:

- The input dataset has a Gaussian distribution, where plotting the data points gives a bell-shaped curve.
- The data set is linearly separable, meaning LDA can draw a straight line or a decision boundary that separates the data points.
- Each class has the same covariance matrix.

For these reasons, LDA may not perform well in high-dimensional feature spaces.

## Role of eigenvectors and eigenvalues

Dimensionality reduction involves separating data points with a straight line. Mathematically, linear transformations are analyzed using eigenvectors and eigenvalues. Imagine you have mapped out a data set with multiple features, resulting in a multi-dimensional scatterplot. Eigenvectors provide the "direction" within the scatterplot. Eigenvalues denote the importance of this directional data. A high eigenvalue means the associated eigenvector is more critical.

During dimensionality reduction, the eigenvectors are calculated from the data set and collected in two scatter-matrices:

- Between-class scatter matrix (information about the data spread within each class)
- Within-class scatter matrix (how classes are spread between themselves).

## Preparing to implement linear discriminant analysis

To use LDA effectively, it’s essential to prepare the data set beforehand. These are the steps and best practices for implementing LDA:

### 1. Preprocess the data to ensure that it is normalized and centered

This is achieved by passing the n-component parameter of the LDA, which identifies the number of linear discriminants to retrieve.

### 2. Choose an appropriate number of dimensions for the lower-dimensional space

This is achieved by passing the n-component parameter of the LDA, which identifies the number of linear discriminants to retrieve.

### 3. Regularize the model

Regularization aims to prevent [overfitting](https://www.ibm.com/topics/overfitting), where the statistical model fits exactly against its training data and undermines its accuracy.

### 4. Using cross-validation to evaluate model performance

You can evaluate classifiers such as LDA by plotting a confusion matrix, with actual class values as rows and predicted class values as columns. A confusion matrix makes it easy to see whether a classifier is confusing two classes—that is, mislabeling one class as another. For example, consider a 10 x 10 confusion matrix predicting images from zero through 9. Actuals are plotted in rows on the y-axis. Predictions are plotted in columns on the x-axis. To see how many times a classifier confused images of 4s and 9s in the 10 x 10 confusion matrix example, you would check the 4<sup>th</sup> row and the 9<sup>th</sup> column.

![a confusion matrix, plotting actuals versus predictions](https://assets.ibm.com/is/image/ibm/ConfusionMatrixExample?ts=1763386305637&dpr=off)

## How the linear discriminant function works

The linear discriminant function helps make decisions in classification problems by separating data points based on features and classifying them into different classes or categories. The computation process can be summarized in these key steps:

### Calculate the between-class variance

The between-class variance is the separability between classes—the distance between the class means.

### Calculate the within-class variance

The within-class variance is the distance between class means and samples.

### Project the data into a lower-dimensional space

This maximizes the between-class variance and minimizes the within-class variance. We can represent the linear discriminant function for two classes mathematically with the following.

**δ(x) = x * ( σ<sup>2</sup> * (μ<sub>0</sub>-μ<sub>1</sub>) - 2 * σ<sup>2</sup> * (μ<sub>0</sub><sup>2</sup>-μ<sub>1</sub><sup>2</sup>) + ln(P(w<sub>0</sub>) / P(w<sub>1</sub>)))**

Where:

- **δ(x)** represents the linear discriminant function.
- **x** represents the input data point.
- **μ<sub>0</sub>** and **μ<sub>1</sub>** are the means of the two classes.
- **σ<sup>2</sup>** is the common within-class variance.
- **P(ω<sub>0</sub>)** and **P(ω<sub>1</sub>)** are the prior probabilities of the two classes.

### Applying LDA with an example

Let's use the equation to work through a loan approval example. To recap, the bank is deciding whether to approve or reject loan applications. The bank uses two features to make this decision: the applicant's credit score (x) and annual income. The bank has collected historical data on previous loan applicants and whether the loans were approved.

- **Class ω<sub>0</sub>** represents "Loan rejected."
- **Class ω<sub>1</sub>** represents "Loan approved."

Using the linear discriminant function, the bank can calculate a score (**δ(x)**) for each loan application.

The equation for the linear discriminant function might look similar to this:

**δ(x) = x * ( σ<sup>2</sup> * (μ<sub>0</sub>-μ<sub>1</sub>) - 2 * σ<sup>2</sup> * (μ<sub>0</sub><sup>2</sup>-μ<sub>1</sub><sup>2</sup>) + ln(P(w<sub>0</sub>) / P(w<sub>1</sub>)))**

- **x** represents the applicant's credit score and annual income.
- **μ<sub>0</sub>** and **μ<sub>1</sub>** are the means of these features for the two classes: "Loan rejected" and "Loan approved."
- **σ<sup>2</sup>** is the common within-class variance.
- **P(ω<sub>0</sub>)** is the prior probability of "Loan rejected", and **P(ω1)** is the prior probability of "Loan approved".

The bank computes the linear discriminant function for each loan application.

- If **δ(x)** is positive, it suggests that the loan application is more likely to be approved.
- If **δ(x)** is negative, it suggests that the loan application is more likely to be rejected.

The bank can thus automate its loan approval process, making quicker and more consistent decisions while minimizing human bias.

### Applications of linear discriminant analysis

These are typical scenarios where LDA can be applied to tackle complex problems and help organizations make better decisions.

To mitigate risk, financial institutions must identify and minimize credit default. LDA can help identify applicants who might be likely to default on loans from those who are creditworthy by sifting through financial factors and behavior data.

Fast and accurate disease diagnosis is crucial for effective treatment. Hospitals and healthcare providers must interpret an immense amount of medical data. LDA helps simplify complex data sets and improve diagnostic accuracy by identifying patterns and relationships in patient data.

For effective marketing, e-commerce businesses must be able to categorize diverse customer bases. LDA is pivotal in segmenting customers, enabling e-commerce companies to tailor their marketing strategies for different customer groups. The outcome is more personalized shopping experiences, increasing customer loyalty and sales.

Producing high-quality goods while minimizing defects is a fundamental challenge. Sensor data from machinery can be used with LDA to identify patterns associated with defects. By detecting irregularities in real-time, manufacturers can take immediate corrective actions, and they can improve product quality and reduce wastage.

You can maximize your advertising budget by targeting the right audience with personalized content, but identifying those respective audience segments can be difficult. LDA can simplify this process by classifying customer attributes and behaviors, enhancing the customization of advertising campaigns. This approach can lead to a higher return on investment (ROI) and a better customer experience.

## Linear discriminant analysis and Python

To delve deeper into linear discriminant analysis with Python and leverage the [scikit-learn](https://scikit-learn.org/stable/) library, you can explore this tutorial [Learn classification algorithms using Python and scikit-learn](https://developer.ibm.com/tutorials/learn-classification-algorithms-using-python-and-scikit-learn/) in IBM watsonx™. The tutorial helps you with the basics of solving a classification-based machine learning problem using Python and [scikit-learn](https://scikit-learn.org/stable/) (also known as sklearn).

For the step-by-step tutorial, you will first import the necessary Python libraries to work with the Iris dataset, perform data preprocessing, and create and evaluate your LDA model:

**<Python code snippet>**

```

import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
import sklearn
import seaborn as sns
from sklearn.preprocessing import StandardScaler, LabelEncoder
from sklearn.model_selection import train_test_split
from sklearn.discriminant_analysis import LinearDiscriminantAnalysis
from sklearn.ensemble import RandomForestClassifier
from sklearn.metrics import accuracy_score, confusion_matrix
```

If the libraries are not installed, you can resolve this using pip install.

See also this [scikit-learn](https://scikit-learn.org/stable/modules/generated/sklearn.discriminant_analysis.LinearDiscriminantAnalysis.html#examples-using-sklearn-discriminant-analysis-lineardiscriminantanalysis) documentation for an overview of key parameters, attributes and general examples of Python implementations using sklearn.discriminant_analysis.LinearDiscriminantAnalysis.

## Advantages and disadvantages of using linear discriminant analysis

Understanding the advantages and limitations of linear discriminant analysis (LDA) is crucial when applying it to various classification problems. Knowledge of tradeoffs helps data scientists and machine learning practitioners make informed decisions about its suitability for a particular task.

### Key advantages

- **Use simplicity and efficiency of computation:** LDA is a simple yet powerful algorithm. It's relatively easy to understand and implement, making it accessible to those new to machine learning. Also, its efficient computation ensures quick results.
- **Manage high-dimensional data:** LDA is effective where the number of features is larger than the number of training samples. Therefore, LDA is valuable in applications such as text analysis, image recognition and genomics, where data is often high-dimensional.
- **Handle multicollinearity:** LDA can address [multicollinearity](https://www.ibm.com/topics/multicollinearity), which is the presence of high correlations between different features. It transforms the data into a lower-dimensional space while maintaining information integrity.

### Key disadvantages

**- Shared mean distributions:** LDA encounters challenges when class distributions share means. LDA struggles to create a new axis that linearly separates both classes. As a result, LDA might not effectively discriminate between classes with overlapping statistical properties. For example, imagine a scenario in which two species of flowers have highly similar petal length and width. LDA may find it difficult to separate these species based on these features alone. Alternative techniques, such as nonlinear discriminant analysis methods, are preferred here.

**- Not suitable for unlabeled data:** LDA is applied as a supervised learning algorithm–that is, it classifies or separates labeled data. In contrast, principal component analysis (PCA), another dimension reduction technique, ignores class labels and preserves variance.

## Footnotes

<sup>1</sup> [James Joyce. *Bayes' Theorem.* Stanford Encyclopedia of Philosophy. 2003](https://plato.stanford.edu/entries/bayes-theorem/)

<sup>2</sup>Dan A. Simovici. Lecture notes on Fisher Linear Discriminant Analysis. 2013

<sup>3 </sup>[Penn State Eberly College of Science. Linear Discriminant Analysis. 2023](https://online.stat.psu.edu/stat508/)

<sup>4 </sup>[J. T. Oates. Lecture notes on Linear Discriminant Analysis. 2014](https://courses.cs.umbc.edu/graduate/678/fall14/LDA.pdf)

<sup>5 </sup>[Guangliang Chen. Lecture notes on Linear Discriminant Analysis (LDA). 2020](https://www.sjsu.edu/faculty/guangliang.chen/Math253S20/lec11lda.pdf)

<sup>6, 7 </sup>[scikit-learn. Linear and Quadratic Discriminant Analysis. 2023](https://scikit-learn.org/stable/modules/lda_qda.html)
