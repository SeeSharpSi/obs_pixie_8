---
title: What is principal component analysis (PCA)?
source: https://www.ibm.com/think/topics/principal-component-analysis
author: null
published: 2024-12-10
created: 2026-05-21
description: "Principal component analysis (PCA) reduces the number of dimensions in large datasets to principal components that retain most of the original information."
---

## What is principal component analysis (PCA)?

Principal component analysis, or PCA, reduces the number of dimensions in large datasets to principal components that retain most of the original information. It does this by transforming potentially correlated variables into a smaller set of variables, called principal components.

Karl Pearson is credited with the development of PCA in 1901, but it gained popularity with the increased availability of computers, which allowed for multivariate statistical computations<sup>1 </sup>at scale. PCA is very effective for visualizing and exploring high-dimensional datasets, or data with many features, as it can easily identify trends, patterns, or outliers.

PCA is commonly used for data preprocessing for use with machine learning algorithms. It can extract the most informative features from large datasets while preserving the most relevant information from the initial dataset. This reduces model complexity as the addition of each new feature negatively impacts model performance, which is also commonly referred to as the “curse of dimensionality.”

By projecting a high-dimensional dataset into a smaller feature space, PCA also minimizes, or altogether eliminates, common issues such as [multicollinearity](https://www.ibm.com/think/topics/multicollinearity) and [overfitting](https://www.ibm.com/think/topics/overfitting). Multicollinearity occurs when two or more independent variables are highly correlated with one another, which can be problematic for causal modeling. Overfit models will generalize poorly to new data, diminishing their value altogether. PCA is a commonly used approach within regression analysis but it is also leveraged for a variety of use cases, such as pattern recognition, signal processing, image processing, and more.

While there are other variations of PCA, such as principal component regression and kernel PCA, the scope of this article will focus on the primary method within current literature.

## PCA vs. LDA vs. factor analysis

PCA is a dimension reduction technique like [linear discriminant analysis](https://www.ibm.com/think/topics/linear-discriminant-analysis) (LDA). In contrast to LDA, PCA is not limited to [supervised learning](https://www.ibm.com/think/topics/supervised-learning) tasks. For [unsupervised learning](https://www.ibm.com/think/topics/unsupervised-learning) tasks, this means PCA can reduce dimensions without having to consider class labels or categories. PCA is also closely related to factor analysis. They both reduce the number of dimensions or variables in a dataset while minimizing information loss. PCA breaks down variables into a subset of linearly independent principal components. Factor analysis, however, is generally used to understand underlying data structures, focusing on latent variables, or unmeasured factors, that capture a variable’s spread.

## PCA vs. K-means clustering

PCA and [k-means clustering](https://www.ibm.com/think/topics/k-means-clustering) are both unsupervised machine learning techniques used for data analysis, but they have different goals and methods. PCA is used to reduce the dimensionality of the data, while k-means clustering groups data points together based on similarity. The technique you select depends on the specific dataset and goals of your analysis.

PCA creates new variables, such as principal components, that are linear combinations of the original variables. PCA takes a dataset with multiple variables as input, and it produces a dataset into a lower subspace, that is, a reduced dataset with fewer variables. It is often used in [exploratory data analysis](https://www.ibm.com/think/topics/exploratory-data-analysis) for building predictive models, but it is also used in data preprocessing for dimensionality reduction.

K-means is a clustering algorithm that assigns data points to clusters based on their distance from the cluster centers. It takes a dataset with one or more variables as input, and it produces a set of clusters with similar data points. It is often used to cluster data for a variety of use cases, such as image segmentation, customer segmentation, and [anomaly detection](https://www.ibm.com/think/topics/anomaly-detection).

## How principal component analysis works

PCA summarizes the information content of large datasets into a smaller set of uncorrelated variables known as principal components. These principal components are linear combinations of the original variables that have the maximum variance compared to other linear combinations. These components capture as much information from the original dataset as possible.

This statistical technique involves both linear algebra and matrix operations, and it transforms the original dataset into a new coordinate system that is structured by the principal components. The eigenvectors and eigenvalues from the covariance matrix that underpin the principal components allow for the analysis of these linear transformations.

Imagine you have mapped out a dataset with multiple features, resulting in a multi-dimensional scatterplot. Eigenvectors provide the direction of variance in the scatterplot. Eigenvalues are the coefficients of the eigenvectors; these denote the importance of this directional data. Therefore, a high eigenvalue means that the corresponding eigenvector is more critical. Since principal components represent the directions of maximum variance in the data, they are also the eigenvectors of the covariance matrix.

Two major components are calculated in PCA: the first principal component (PC1) and the second principal component (PC2).

### First principal component

The first principal component (PC1) is the direction in space along which the data points have the highest or most variance. It is the line that best represents the shape of the projected points. The larger the variability captured in the first component, the larger the information retained from the original dataset. No other principal component can have a higher variability.

### Second principal component

We calculate the second principal component (PC2) in the same way as PC1. PC2 accounts for the next highest variance in the dataset and must be uncorrelated with PC1. That is, PC2 must be orthogonal, that is perpendicular, to PC1. This relationship can also be expressed as the correlation between PC1 and PC2 equals zero.

A scatterplot is typically used to show the relationship between PC1 and PC2 when PCA is applied to a dataset. PC1 and PC2 axis will be perpendicular to each other.

If there are any subsequent components, then they would also retain the same properties, where they would not be correlated with other components and explain any remaining variation.

## Calculating principal components

The PCA computation process is summarized in the steps below, showing that how the principal components are calculated and how they relate to the original data.

### Standardize the range of continuous initial variables

Since PCA can bias towards specific features, it is important to evaluate whether normalization of data is needed. Data should reflect a normal distribution with a mean of zero and a standard deviation of one.

In this step, the mean values of the variables are calculated and subtracted from the original dataset so that each variable contributes equally to the analysis. This value is then divided by the standard deviation for each variable so that all variables use the same scale.

### Compute the covariance matrix to identify correlations

Covariance (cov) measures how strongly correlated two or more variables are. The covariance matrix summarizes the covariances associated with all pair combinations of the initial variables in the dataset. Computing the covariance matrix helps identify the relationships between the variables–that is, how the variables vary from the mean with respect to each other. This data matrix is a symmetric matrix, meaning the variable combinations can be represented as d × d, where d is the number of dimensions. For example, for a 3-dimensional dataset, there would be 3 × 3 or 9 variable combinations in the covariance matrix.

The sign of the variables in the matrix tells us whether combinations are correlated:

- Positive (the variables are correlated and increase or decrease at the same time)
- Negative (the variables are not correlated, meaning that one decreases while the other increases)
- Zero (the variables are not related to each other)

### Compute the eigenvectors and eigenvalues of the covariance matrix

Here, we calculate the eigenvectors (principal components) and eigenvalues of the covariance matrix. As eigenvectors, the principal components represent the directions of maximum variance in the data. The eigenvalues represent the amount of variance in each component. Ranking the eigenvectors by eigenvalue identifies the order of principal components.

### Select the principal components

Here, we decide which components to keep and those to discard. Components with low eigenvalues typically will not be as significant. Scree plots usually plot the proportion of total variance explained and the cumulative proportion of variance. These metrics help one to determine the optimal number of components to retain. The point at which the Y axis of eigenvalues or total variance explained creates an "elbow" will generally indicate how many PCA components that we want to include.

### Transform the data into the new coordinate system

Finally, the data is transformed into the new coordinate system defined by the principal components. That is, the feature vector created from the eigenvectors of the covariance matrix projects the data onto the new axes defined by the principal components. This creates new data, capturing most of the information but with fewer dimensions than the original dataset.

## Interpreting PCA results

A PCA plot is a scatter plot created by using the first two principal components as axes. The first principal component (PC1) is the x-axis, and the second principal component (PC2) is the y-axis. The scatter plot shows the relationships between observations (data points) and the new variables (the principal components). The position of each point shows the values of PC1 and PC2 for that observation.

The direction and length of the plot arrows indicate the loadings of the variables, that is, how each variable contributes to the principal components. If a variable has a high loading for a particular component, it is strongly correlated with that component. This can highlight which variables have a significant impact on data variations.

The number of principal components that remain after applying PCA can help you interpret the data output. The first principal component explains the most data variance, and each later component accounts for less variance. Thus, the number of components can indicate the amount of information retained from the original dataset. Fewer components after applying PCA could mean that you didn’t capture much data variation. More components indicate more data variation, but the results may be harder to interpret. You can decide the optimal number of components to retain using either a scree plot or the cumulative explained variance.

## Applications of principal component analysis

Applying PCA can help preprocess or extract the most informative features from datasets with many variables. Preprocessing reduces complexity while preserving relevant information. Common scenarios that use PCA include:

PCA reduces image dimensionality while retaining essential information. It helps create compact representations of images, making them easier to store and transmit.

PCA helps to visualize high-dimensional data by projecting it into a lower-dimensional space, such as a 2D or 3D plot. This simplifies data interpretation and exploration.

PCA can remove noise or redundant information from data by focusing on the principal components that capture the underlying patterns.

## Predicting breast cancer

PCA has also had applications within healthcare. For example, it has assisted in diagnosing diseases earlier and more accurately. The paper Breast Cancer Prediction using Principal Component Analysis with Logistic Regression analyses a well-known [breast cancer dataset](https://archive.ics.uci.edu/dataset/17/breast+cancer+wisconsin+diagnostic)<sup>2 </sup>collected from patients at the University of Wisconsin Hospitals, Madison. The study’s author, Akbar, uses PCA to reduce the dimensions of the six different data attributes:

- mean_radius of a breast lump
- mean_texture of the X-ray image
- mean_perimeter of the lump
- mean_area of the lump
- mean_smoothness of the image
- diagnosis (whether the patient has been diagnosed with cancer or not).

A supervised learning classification algorithm, logistic regression, was then applied to predict whether breast cancer is present.

## When to use principal component analysis

There are many other dimensionality reduction techniques available, including [linear discriminant analysis](https://www.ibm.com/think/topics/linear-discriminant-analysis), [random forest](https://www.ibm.com/think/topics/random-forest), uniform manifold approximation and projection (UMAP), and t-distributed stochastic neighbor (t-SNE). Consider the following factors to decide if PCA is the right approach for your analysis:

- **Linearity:** PCA is a linear technique, while other techniques such as t-SNE and UMAP are non-linear. This means that PCA is better suited for datasets with linear relationships between variables. Non-linear techniques are better suited for datasets with non-linear or more complex relationships between variables.
- **Computation:** PCA uses matrix operations for computation to efficiently manage large datasets. Other techniques, such as t-SNE and UMAP, are expensive and may not be suitable for large datasets.
- **Information preservation:** PCA preserves the maximum amount of variance in the data. t-SNE and UMAP focus on preserving the local structure of the data. PCA is, therefore, better suited for identifying the most important data variables. Non-linear techniques are better suited for visualizing the data in lower dimensions.
- **Feature extraction:** PCA is a feature extraction technique. It produces new variables that are linear combinations of the original variables. Other techniques (such as UMAP and t-SNE) do not create new variables. This means PCA can identify the most important variables in the data. Non-linear techniques are better suited for visualizing the data in lower dimensions.

## Footnotes

<sup>1</sup>[Andrzej Maćkiewicz and Waldemar Ratajczak. Principal Components Analysis (PCA). *Computers & Geosciences.* Vol. 19. No. 3. 1993](https://www.sciencedirect.com/science/article/abs/pii/009830049390090R?via%3Dihub).

<sup>2 </sup>[Wolberg, William, Mangasarian, Olvi, Street, Nick and Street, W (1995). Breast Cancer Wisconsin (Diagnostic). *UCI Machine Learning Repository*](https://archive.ics.uci.edu/dataset/17/breast+cancer+wisconsin+diagnostic).
