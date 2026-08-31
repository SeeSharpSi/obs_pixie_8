---
title: What are support vector machines (SVMs)?
source: https://www.ibm.com/think/topics/support-vector-machine
author:
- '[[Eda Kavlakoglu]]'
published: 2024-12-16
created: 2026-08-31
description: "SVM is a supervised ML algorithm that classifies data by finding an optimal line or hyperplane to maximize distance between each class in N-dimensional space."
---

## What are SVMs?

A support vector machine (SVM) is a [supervised machine learning](https://www.ibm.com/topics/supervised-learning) algorithm that classifies data by finding an optimal line or hyperplane that maximizes the distance between each class in an N-dimensional space.

SVMs were developed in the 1990s by Vladimir N. Vapnik and his colleagues, and they published this work in a paper titled "Support Vector Method for Function Approximation, Regression Estimation, and Signal Processing"<sup>1</sup> in 1995.

SVMs are commonly used within classification problems. They distinguish between two classes by finding the optimal hyperplane that maximizes the margin between the closest data points of opposite classes. The number of features in the input data determine if the hyperplane is a line in a 2-D space or a plane in a n-dimensional space. Since multiple hyperplanes can be found to differentiate classes, maximizing the margin between points enables the algorithm to find the best decision boundary between classes. This, in turn, enables it to generalize well to new data and make accurate classification predictions. The lines that are adjacent to the optimal hyperplane are known as support vectors as these vectors run through the data points that determine the maximal margin.

The SVM algorithm is widely used in [machine learning](https://www.ibm.com/think/topics/machine-learning) as it can handle both linear and nonlinear classification tasks. However, when the data is not linearly separable, kernel functions are used to transform the data higher-dimensional space to enable linear separation. This application of kernel functions can be known as the “kernel trick”, and the choice of kernel function, such as linear kernels, polynomial kernels, radial basis function (RBF) kernels, or sigmoid kernels, depends on data characteristics and the specific use case.

![Finding the max margin to generate optimal hyperplane ](https://assets.ibm.com/is/image/ibm/3-1_svm_optimal-hyperplane_max-margin_support-vectors-2-1?ts=1763386649893&dpr=off)

## Types of SVM classifiers

### Linear SVMs

Linear SVMs are used with linearly separable data; this means that the data do not need to undergo any transformations to separate the data into different classes. The decision boundary and support vectors form the appearance of a street, and Professor Patrick Winston from MIT uses the analogy of “[fitting the widest possible street](https://ocw.mit.edu/courses/6-034-artificial-intelligence-fall-2010/resources/mit6_034f10_svm/)“<sup>2</sup> to describe this quadratic optimization problem. Mathematically, this separating hyperplane can be represented as:

*wx + b = 0*

where *w* is the weight vector, *x* is the input vector, and *b* is the bias term.

There are two approaches to calculating the margin, or the maximum distance between classes, which are hard-margin classification and soft-margin classification. If we use a hard-margin SVMs, the data points will be perfectly separated outside of the support vectors, or “off the street” to continue with Professor Hinton’s analogy. This is represented with the formula,

(wx<sub>j</sub> + b) y<sub>j</sub> ≥ a,

and then the margin is maximized, which is represented as: max ɣ= a / ||w||, where a is the margin projected onto *w*.

Soft-margin classification is more flexible, allowing for some misclassification through the use of slack variables (`ξ`). The hyperparameter, C, adjusts the margin; a larger C value narrows the margin for minimal misclassification while a smaller C value widens it, allowing for more misclassified data<sup>3</sup>.

### Nonlinear SVMs

Much of the data in real-world scenarios are not linearly separable, and that’s where nonlinear SVMs come into play. In order to make the data linearly separable, preprocessing methods are applied to the training data to transform it into a higher-dimensional feature space. That said, higher dimensional spaces can create more complexity by increasing the risk of overfitting the data and by becoming computationally taxing. The “kernel trick” helps to reduce some of that complexity, making the computation more efficient, and it does this by replacing dot product calculations with an equivalent kernel function<sup>4</sup>.

There are a number of different kernel types that can be applied to classify data. Some popular kernel functions include:

- Polynomial kernel
- Radial basis function kernel (also known as a Gaussian or RBF kernel)
- Sigmoid kernel

### Support vector regression (SVR)

Support vector regression (SVR) is an extension of SVMs, which is applied to regression problems (i.e. the outcome is continuous). Similar to linear SVMs, SVR finds a hyperplane with the maximum margin between data points, and it is typically used for time series prediction.

SVR differs from [linear regression](https://www.ibm.com/topics/linear-regression) in that you need to specify the relationship that you’re looking to understand between the independent and dependent variables. An understanding of the relationships between variables and their directions is valuable when using linear regression. This is unnecessary for SVRs as they determine these relationships on their own.

## How SVMs work

In this section, we will discuss the process of building a SVM classifier, how it compares to other supervised learning algorithms and its applications within industry today.

### Building a SVM classifier

#### Split your data

As with other machine learning models, start by splitting your data into a training set and testing set. As an aside, this assumes that you’ve already conducted an [exploratory data analysis](https://www.ibm.com/topics/exploratory-data-analysis) on your data. While this is technically not necessary to build a SVM classifier, it is good practice before using any machine learning model as this will give you an understanding of any missing data or outliers.

#### Generate and evaluate the model

Import an SVM module from the library of your choosing, like [scikit-learn](https://scikit-learn.org/stable/modules/svm.html). Train your training samples on the classifier and predict the response. You can evaluate performance by comparing accuracy of the test set to the predicted values. You may want to use other evaluation metrics, like f1-score, precision, or recall.

#### Hyperparameter tuning

Hyperparameters can be tuned to improve the performance of an SVM model. Optimal hyperparameters can be found using grid search and cross-validation methods, which will iterate through different kernel, regularization (C), and gamma values to find the best combination.

### SVMs vs. other supervised learning classifiers

Different machine learning classifiers can be used for the same use case. It's important to test out and evaluate different models to understand which ones perform the best. That said, it can be helpful to understand the strengths and weaknesses of each to assess its application for your use case.

#### SVMs vs naive bayes

Both Naive Bayes and SVM classifies are commonly used for text classification tasks. SVMs tend to perform better than Naive Bayes when the data is not linearly separable. That said, SVMs have to tune for different hyperparameters and can be more computationally expensive.

#### SVMs vs logistic regression

SVMs typically perform better with high-dimensional and unstructured datasets, such as image and text data, compared to logistic regression. SVMs are also less sensitive to overfitting and easier to interpret. That said, they can be more computationally expensive.

#### SVMs vs decision trees

SVMs perform better with high-dimensional data and are less prone to overfitting compared to decision trees. That said, decision trees are typically faster to train, particularly with smaller datasets, and they are generally easier to interpret.

#### SVM vs. neural networks

Similar to other model comparisons, SVMs are more computationally expensive to train and less prone to overfitting, but neural networks are considered more flexible and scalable.

### Applications of SVMs

While SVMs can be applied for a number of tasks, these are some of the most popular applications of SVMs across industries.

SVMs are commonly used in natural language processing (NLP) for tasks such as sentiment analysis, spam detection, and topic modeling. They lend themselves to these data as they perform well with high-dimensional data.

SVMs are applied in image classification tasks such as object detection and image retrieval. It can also be useful in security domains, classifying an image as one that has been tampered with.

SVMs are also used for protein classification, gene expression analysis, and disease diagnosis. SVMs are often applied in [cancer research](https://pmc.ncbi.nlm.nih.gov/articles/PMC5822181/#R4) because they can detect subtle trends in complex datasets.

SVMs can analyze layered geophysical structures underground, filtering out the 'noise' from electromagnetic data. They have also helped to predict the seismic liquefaction potential of soil, which is relevant to field of civil engineering.

## Footnotes

*<sup>All links are located outside ibm.com</sup>*

<sup>1</sup> [Support Vector Method for Function Approximation, Regression Estimation, and Signal Processing](https://proceedings.neurips.cc/paper_files/paper/1996/file/4f284803bd0966cc24fa8683a34afc6e-Paper.pdf)

<sup>2 </sup>[Lecture 16 notes on Support Vector Machines](https://ocw.mit.edu/courses/6-034-artificial-intelligence-fall-2010/resources/mit6_034f10_svm/), Patrick Winston, MIT, 2010

<sup>3 </sup>[Introduction to Support Vector Machines](https://home.work.caltech.edu/~boswell/IntroToSVM.pdf). Boswell, Dustin. Caltech. 2002

<sup>4 </sup>[Support vector machines](https://people.csail.mit.edu/dsontag/courses/ml14/slides/lecture2.pdf). Sontag. David. New York University
