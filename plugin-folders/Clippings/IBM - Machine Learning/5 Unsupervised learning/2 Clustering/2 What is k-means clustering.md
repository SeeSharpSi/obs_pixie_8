---
title: What is k-means clustering?
source: https://www.ibm.com/think/topics/k-means-clustering
author:
- '[[Eda Kavlakoglu]]'
- '[[Vanna Winland]]'
published: 2024-11-27
created: 2026-08-31
description: "K-Means clustering is an unsupervised learning algorithm used for data clustering, which groups unlabeled data points into groups or clusters."
---

## What is k-means clustering?

K-means clustering is an unsupervised learning algorithm used for data [clustering](https://www.ibm.com/think/topics/clustering), which groups unlabeled data points into groups or clusters.

It is one of the most popular clustering methods used in machine learning. Unlike [supervised learning](https://www.ibm.com/think/topics/supervised-vs-unsupervised-learning), the training data that this algorithm uses is unlabeled, meaning that data points do not have a defined classification structure.

While various types of clustering algorithms exist, including exclusive, overlapping, hierarchical and probabilistic, the k-means clustering algorithm is an example of an exclusive or “hard” clustering method. This form of grouping stipulates that a data point can exist in just one cluster. This type of cluster analysis is commonly used in data science for market segmentation, document clustering, image segmentation and image compression. The k-means algorithm is a widely used method in cluster analysis because it is efficient, effective and simple.

K-means is an iterative, [centroid-based clustering algorithm](https://www.ibm.com/think/topics/clustering) that partitions a dataset into similar groups based on the distance between their centroids. The centroid, or cluster center, is either the mean or median of all the points within the cluster depending on the characteristics of the data.

## How does k-means clustering work?

K-means clustering is an iterative process to minimize the sum of distances between the data points and their cluster centroids.

The k-means clustering algorithm operates by categorizing data points into clusters by using a mathematical distance measure, usually euclidean, from the cluster center. The objective is to minimize the sum of distances between data points and their assigned clusters. Data points that are nearest to a centroid are grouped together within the same category. A higher k value, or the number of clusters, signifies smaller clusters with greater detail, while a lower k value results in larger clusters with less detail.

### Initialize k

The conventional k-means clustering algorithm requires a few steps. The first step is to initialize *k* centroids where *k* is equal to the number of clusters chosen for a specific dataset. This approach uses either random selection or initial centroid sampling methods.

### Assign centroids

The next step includes a two-step iterative process based on the expectation maximization machine learning algorithm.<sup>1 </sup>The expectation step assigns each data point to its closest centroid based on distance (again, usually euclidean). The maximization step computes the mean of all the points for each cluster and reassigns the cluster center, or centroid. This process repeats until the centroid positions have reached convergence or the maximum number of iterations have been reached.

K-means clustering is simple yet sensitive to initial conditions and outliers. It is important to optimize the centroid initialization and the number of clusters k, to achieve the most meaningful clusters. There are several ways to evaluate and optimize clustering components of the algorithm by using evaluation metrics and initial centroid sampling methods.

## Cluster evaluation metrics

Quality clusters contain at least two properties:

1. **All data points within a cluster should be similar.**
2. **Clusters should be distinct from each other.**

These properties are achieved by minimizing the intracluster distance and maximizing the intercluster distance of all data points in a dataset. In other words, the more compact and isolated a cluster is from other clusters, the better. The goal of the k-means clustering algorithm is to minimize the sum of squared errors (SSE).<sup>2</sup> Computing the SSE of the squared euclidean distance of each point to its closest centroid evaluates the quality of the cluster assignments by measuring the total variation within each cluster.

Cluster evaluation metrics check the quality and provide different perspectives to analyze clustering results. This helps in selecting the optimal number of clusters and centroid initialization. The following evaluation metrics are common ways to measure the intra and intercluster distances in clustering.

### Inertia

The k-means clustering algorithm aims to choose centroids, or cluster centers, that minimize inertia, an evaluation metric that measures how well a dataset has been clustered based on distance metrics. Inertia is calculated by measuring the distance between a datapoint and its centroid, squaring the distance and summing those squares for each data point in the cluster. The sum or inertial value is the intracluster distance. The lower the sum the better because it means that the datapoints within the cluster are compact or more similar.<sup>3</sup>

### The Dunn index

The second property is measured with the Dunn index. The Dunn index represents the relationship between the minimum intercluster distance and the maximum intracluster distance. Clusters with a high intercluster distance indicate better quality because it means that the clusters are as different from each other as possible.<sup>4</sup>

## Optimizing k-means performance

Optimization is important when using k-means to achieve the best clustering results.

The k-means algorithm is nondeterministic due to its random initialization step. This method implies that if the algorithm is performed twice on identical data, the cluster assignments might differ. To achieve optimal clustering results, properly selecting the initial centroids and the optimum number of clusters improves the accuracy and the speed of the k-means algorithm.

### Initializing the cluster centroids

Each cluster is represented by a centroid, a data point that represents the cluster center. K-means groups together similar data points into clusters by minimizing the distance between data points in a cluster with their centroid or k mean value. The primary goal of the k-means algorithm is to minimize the total distances between points and their assigned cluster centroid. The algorithm operates iteratively, and initial partition selection can greatly impact the resulting clusters.

Random initialization risks yielding inconsistent results. Centroid initialization methods exist to mitigate these risks. A study by NUS Computing explains and compares methods such as the popular k-means++ to random initialization.<sup>5</sup>

### K-means ++

K-means++ is a k-means algorithm that optimizes the selection of the initial cluster centroid or centroids. Developed by researchers Arthur and Vassilvitskii, k-means++ improves the quality of the final cluster assignment.<sup>6</sup>

The first step to initialization by using the k-means++ method is to choose one centroid from the data set. For each subsequent centroid, calculate the distance of each data point from its closest cluster center. The subsequent centroid is selected by considering the likelihood that a point is at a proportional distance from the nearest centroid chosen earlier. The process executes iterations until the chosen number of cluster centers have been initialized.

Here is a [tutorial](https://developer.ibm.com/tutorials/awb-k-means-clustering-in-python/) from IBM Developer that uses the k-means++ method for initialization.

### Choosing the optimal number of clusters

Ideally, the k-means algorithm iterates until the optimal number of clusters are reached. The maximum number of iterations are met once the centroids have achieved convergence.

### The elbow method

One method to achieve the optimal number of clusters is the elbow method. The elbow method is a graphical method for finding the optimum number of clusters within a k-means clustering algorithm. It measures the euclidean distance between each data point and its cluster center and chooses the number of clusters based on where change in “within cluster sum of squares” (WCSS) levels off. This value represents the total variance within each cluster that gets plotted against the number of clusters.<sup>7</sup>

The first step of the elbow method is to calculate the WCSS for each cluster (k). Then, the WCSS value is plotted along the y-axis and the number of clusters is plotted on the x-axis. As the number of clusters increases, the plot points should form a consistent pattern. From this pattern, results a range for the optimum number of clusters.<sup>8</sup> When deciding on the number of clusters, consider the computational costs. The higher the number of clusters, the more processing power is needed especially with large datasets.

This method isn’t necessarily the best, especially for datasets with high dimensionality or irregular shape. Another method for choosing the optimum number of clusters is the silhouette analysis.<sup>9</sup>

![Illustrated graph for k Means Clustering](https://assets.ibm.com/is/image/ibm/k-means-clustering-graph?ts=1783346872954&dpr=off)

## Applications in machine learning

The k-means clustering algorithm is used in almost every domain and industry. It’s typically applied to machine learning data that has few dimensions, is numeric and can be easily portioned.

Researchers have integrated k-means clustering with deep learning methods such as [CNNs](https://www.ibm.com/think/topics/convolutional-neural-networks) and [RNNs](https://www.ibm.com/think/topics/recurrent-neural-networks) to enhance the performance of various machine learning tasks such as computer vision, NLP and many other domains. Here is a list of common k-means clustering applications:

Customer segmentation: The practice of dividing a company’s customers into groups based on common characteristics that reflect similarity. This strategy allows companies to target specific clusters or groups of customers for specific advertising campaigns.

Document classification: A procedure for allocating various classes or categories to documents. This method is used by many organizations to moderate content. Check out this [Watson Discover documentation](https://cloud.ibm.com/docs/discovery-data?topic=discovery-data-cm-doc-classifier) to build a document classifier.

Image segmentation: A computer vision technique that divides a digital image into distinct sets of pixels. This research dives into how k-means models are used to help identify boundaries in medical images.<sup>10</sup>

Recommendation engines: Applications all over the web use recommendation engines. [Principal component analysis](https://www.ibm.com/think/topics/principal-component-analysis) and k-means clustering techniques are used to build product recommendation for e-commerce businesses.<sup>11</sup>

## Training k-means models with python

For a hands-on learning experience, check out the [tutorial](https://developer.ibm.com/tutorials/awb-k-means-clustering-in-python/) that explains the fundamentals of performing k-means clustering in Python by using [IBM Watson Studio](https://www.ibm.com/products/watson-studio) on [watsonx.ai](https://www.ibm.com/products/watsonx-ai).

This tutorial uses a module from the scikit-learn (sklearn) library that performs k-means clustering. The module includes built-in optimization techniques that are manipulated by its class parameters. The class for the module looks like this:

```

***class* sklearn.cluster.KMeans**(***n_clusters=**8*, ***, ***init=**'k-means++'*, ***n_init=**'auto'*, ***max_iter=**300*, ***tol=**0.0001*, ***verbose=**0*, ***random_state=**None*, ***copy_x=**True*, ***algorithm=**'lloyd'*)[<sup>12</sup>](#f12)
```

The parameters include the number of clusters to form and the number of centroids to generate (n_clusters). There are two initialization methods availablek-means++andrandom. It also includes attributes for setting the maximum number of iterations. Each iteration begins by partitioning the dataset into the value of the n_clustersparameter.

These libraries are used to generate a test data set and perform clustering:

```

import pandas as pd 
import sklearn
import matplotlib.pyplot as plt
import seaborn as sns
import numpy

from sklearn.cluster import KMeans
from sklearn.datasets import make_blobs
from sklearn.decomposition import PCA
from sklearn.preprocessing import StandardScaler
```

## Advantages and disadvantages

### Advantages

Some common benefits of k-means clustering in machine learning applications include:

**Simple:** K-means clustering is simple to understand and to put in practice. It is the most popular unsupervised machine learning technique.

**Fast:** K-means clustering is designed with a computationally simple iterative approach. The k-means clustering algorithm is faster than hierarchical clustering that involves building a tree-like structure of clusters and requires computing pairwise distance between all datapoints.

**Scalable:** K-means is also easily scalable to large datasets and generalizes to clusters of different shapes and sizes, which is ideal for cluster analysis. Since the algorithm is so computationally efficient, it is more scalable and suitable for large datasets compared to other methods.

### Disadvantages

Some common challenges associated with k-means clustering include:

**Dependence on input parameters:** K-means clustering depends on properly set input parameters. Initializing the proper centroid and number of clusters is impeccable for gaining meaningful cluster results. A bad centroid initialization might lead to increased run time and low-quality cluster assignments. Much research has gone into improving the centroid initialization procedure for better clustering results and faster convergence time.

**Possible underperformance on certain datasets:** K-means performs effectively when the dataset contains clusters that are similar in size and there are no notable outliers or density variations. K-means performs poorly when the dataset contains many variations or is highly dimensional. Data that does not align with certain dataset assumptions might cause k-means to produce low-quality clusters.<sup>13</sup> For example, unevenly sized clusters might skew the centroids toward the larger clusters leading to bias and misclassification among the smaller clusters. To solve this problem, k-means can be generalized using probabilistic models like [Gaussian Mixture node.](https://www.ibm.com/docs/en/spss-modeler/saas?topic=nodes-gaussian-mixture-node)

**Significant outlier impact:** Outliers have a significant impact on the results of k-means clustering. Different clusters should be far apart, but not so far apart as to skew the data points. It is important to consider the data assumptions before applying k-means. K-means is especially sensitive to outliers since it aims to determine centroids by averaging values with a cluster. This sensitivity makes it prone to overfitting to include these outliers.

## Footnotes

1 Todd K. Moon. "The Expectation Maximization Algorithm". IEE Signal Processing Magazine. [https://ieeexplore.ieee.org/document/543975](https://ieeexplore.ieee.org/document/543975) (external link to ibm.com)

2 Kevin Arvai. "K-Means Clustering in Python: A Practical Guide". [https://realpython.com/k-means-clustering-python/#:~:text=Understanding%20the%20K%2DMeans%20Algorithm,-Conventional%20k%2Dmeans&text=The%20quality%20of%20the%20cluster,point%20to%20its%20closest%20centroid.](https://realpython.com/k-means-clustering-python/#:~:text=Understanding%20the%20K%2DMeans%20Algorithm,-Conventional%20k%2Dmeans&text=The%20quality%20of%20the%20cluster,point%20to%20its%20closest%20centroid.) (external link to ibm.com)

3 "Clustering: K-Means". [https://www.codecademy.com/learn/dspath-unsupervised/modules/dspath-clustering/cheatsheet](https://www.codecademy.com/learn/dspath-unsupervised/modules/dspath-clustering/cheatsheet) (external link to ibm.com)

4 "Dunn Index". [https://ruivieira.dev/dunn-index.html](https://ruivieira.dev/dunn-index.html) (external link to ibm.com)

5 Xiangyuan, Siyuan, Hao. "A survey on k-means initialization methods". [https://www.comp.nus.edu.sg/~arnab/randalg20/HLW.pdf](https://www.comp.nus.edu.sg/~arnab/randalg20/HLW.pdf) (external link to ibm.com)

6 Arthur, Vassilvitskii. "k-means++: The Advantages of Careful Seeding". Stanford. [https://theory.stanford.edu/~sergei/papers/kMeansPP-soda.pdf](https://theory.stanford.edu/~sergei/papers/kMeansPP-soda.pdf) (external link to ibm.com)

7 Gutierrez. "Unsupervised Learning: Evaluating Clusters". [https://opendatascience.com/unsupervised-learning-evaluating-clusters/](https://opendatascience.com/unsupervised-learning-evaluating-clusters/) (external link to ibm.com)

8 "K-means clustering using Python on IBM watsonx.ai". [https://developer.ibm.com/tutorials/awb-k-means-clustering-in-python/](https://developer.ibm.com/tutorials/awb-k-means-clustering-in-python/) . Step 4 (external link to ibm.com)

9 Shutaywi, Kachouie. "Silhouette Analysis for Performance Evaluation in Machine Learning with Applications in Clustering." June 2021. [https://www.mdpi.com/1099-4300/23/6/759](https://www.mdpi.com/1099-4300/23/6/759) (external link to ibm.com)

10 Dhanachandra, Manglem, Chanu. "Image Segmentation Using K-means Clustering Algorithm and Subtractive Clustering Algorithm". ScienceDirect. Vol 54. PP. 764-771. [https://www.sciencedirect.com/science/article/pii/S1877050915014143](https://www.sciencedirect.com/science/article/pii/S1877050915014143) (external link to ibm.com)

11 Bagus Mulyawan et al. "Recommendation Product Based on Customer Categorization with K-Means Clustering Method". 2019 IOP Conf. Ser.: Mater. Sci. Eng. 508 012123 [https://iopscience.iop.org/article/10.1088/1757-899X/508/1/012123/pdf#:~:text=The%20K%2DMeans%20algorithm%20is,group%20customer%20based%20on%20attributes.](https://iopscience.iop.org/article/10.1088/1757-899X/508/1/012123/pdf#:~:text=The%20K%2DMeans%20algorithm%20is,group%20customer%20based%20on%20attributes.) (external link to ibm.com)

12 scikit-learn. [https://github.com/scikit-learn/scikit-learn/blob/5491dc695/sklearn/cluster/_kmeans.py#L1193](https://github.com/scikit-learn/scikit-learn/blob/5491dc695/sklearn/cluster/_kmeans.py#L1193) (external link to ibm.com)

13 "Demonstration of k-means assumptions". [https://scikit-learn.org/stable/auto_examples/cluster/plot_kmeans_assumptions.html](https://scikit-learn.org/stable/auto_examples/cluster/plot_kmeans_assumptions.html)(external link to ibm.com)
