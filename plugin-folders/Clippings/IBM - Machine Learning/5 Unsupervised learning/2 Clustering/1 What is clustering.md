---
title: What is clustering?
source: https://www.ibm.com/think/topics/clustering
author: null
published: 2024-11-22
created: 2026-08-31
description: "Clustering is an unsupervised machine learning algorithm that organizes and classifies different objects, data points, or observations into groups or clusters based on similarities or patterns."
---

## What is clustering?

Clustering is an unsupervised [machine learning](https://www.ibm.com/think/topics/machine-learning) algorithm that organizes and classifies different objects, data points, or observations into groups or clusters based on similarities or patterns.

There are a variety of ways to use clustering in machine learning from initial explorations of a dataset to monitoring ongoing processes. You may use it in exploratory data analysis with a new dataset to understand underlying trends, patterns, and outliers. Alternatively, you may have a larger dataset which needs to be split into multiple datasets or reduced using dimensionality reduction. In these cases clustering can be a step in preprocessing.

Examples of clusters can include genres of music, different groups of users, key segments of a market segmentation, types of network traffic on a server cluster, friend groups in a social network, or many other kinds of categories. The process of clustering can use just one feature of the data or it can use all of the features present in the data.

It’s helpful to think of clustering as trying to find natural groupings in data in order to see what categories might exist and what defines those categories. Clusters can help you find underlying relationships between data points to see what features or characteristics are shared across categories. Depending on the clustering algorithm used, you may be able to remove outliers from your data or label them as outliers. Clustering can also help in anomaly detection by detecting what data points are not contained within a cluster or are only weakly associated with a cluster and thus may be an anomaly in the data generating process.

Clustering can also be used to reduce the complexity of large datasets by reducing the number of dimensions of data. If you see that categories are defined by only two or three features, you may be able to remove extraneous features or use dimensionality reduction techniques like PCA. Clustering is also very useful in creating visualizations of the datasets to see emergent properties of the data as well as density and relationships between clusters.

Clustering algorithms are sometimes distinguished as performing hard clustering, where each data point belongs to only a single cluster and has a binary value of being either in or not in a cluster, or performing soft clustering where each data point is given a probability of belonging in each identified cluster. There is no one best clustering process, you’ll want to choose the approach that makes the most sense for your needs and the data that you’re working with.

## Types of clustering

There are many different clustering algorithms as there are multiple ways to define a cluster. Different approaches will work well for different types of models depending on the size of the input data, the dimensionality of the data, the rigidity of the categories and the number of clusters within the dataset. It’s worth noting that one algorithm may work very well for one dataset and very poorly on another. This section discusses five of the commonly used approaches to clustering. There are other techniques like spectral clustering or Mean-Shift clustering which are outside of the scope of this article.

### Centroid-based clustering

Centroid-based clustering is a type of clustering method that partitions or splits a data set into similar groups based on the distance between their centroids. Each cluster’s centroid, or center, is either the mean or median of all the points in the cluster depending on the data.

One of the most commonly used centroid-based clustering techniques is the k-means clustering algorithm. K-means assumes that the center of each cluster defines the cluster using a distance measure, mostly commonly Euclidean distance, to the centroid. To initialize the clustering, you provide a number of expected clusters, which represents the ‘K’ in K-means, and the algorithm attempts to find reasonable clusters across the data to match that number. The optimal k clusters in a given dataset is identified by iteratively minimizing the total distance between each point and its assigned cluster centroid.

K-means is a hard clustering approach, meaning each data point is assigned to a separate cluster and no probability associated with cluster membership. K-means works well when the clusters are of roughly equivalent size, and there are not significant outliers or changes in density across the data. K-means often performs poorly when the data is high dimensional or when clusters have significantly different sizes or densities. K-means is also especially sensitive to outliers since it tries to establish centroids based on the mean values of all values in the cluster and thus is susceptible to overfitting to include those outliers.

Another centroid based approach to K-means is K-medoids. Medoids are representative objects of a dataset or a cluster within a dataset whose sum of distances to other objects in the cluster is minimal. Instead of having an arbitrary centroid be the center of the graph, the algorithm creates clusters by using individual data points as the medoid or center of the cluster. Since the K-medoids algorithm uses extant data points rather than arbitrary centroids it is less sensitive to outliers.

### Hierarchical clustering

Hierarchical clustering, sometimes called connectivity-based clustering, groups data points together based on the proximity and connectivity of their attributes. This method determines clusters based on how close data points are to one another across all of the dimensions. The idea is that objects that are nearer are more closely related than those that are far from each other. Unlike k-means, there is no need to pre-specify the number of clusters. Instead, the clustering algorithm creates a graph network of the clusters at each hierarchical level. This network is hierarchical, meaning that any given node in it only has one parent node but may have multiple child nodes. Hierarchical clusters can be graphed with a dendrogram to help visually summarize and organize discovered clusters and the hierarchy that they may contain.

There are two approaches to performing hierarchical cluster analysis:

**Agglomerative:** In agglomerative clustering a bottom-up approach starts with individual data points and successively merges clusters by compute the proximity matrix of all the clusters at the current level of the hierarchy to create a tree-like structure. Once one level of clusters has been created where all the clusters have no or low inter-cluster similarity, the algorithm moves to the set of newly created clusters and repeats the process until there is one root node at the top of the hierarchical graph. There are a variety of choices possible in terms of how these clusters should be merged with one another with tradeoffs in terms of the quality and efficiency of the clustering. In single-linkage clustering, the shortest distance between any pair of data points in two clusters is used as a similarity measure. In all-pairs linkage, the average across all pairs of data points is used, whereas in sampled linkage, a sampling of the data points in the two clusters is used for calculating the average distance. In centroid-linkage, the distance between the centroids is used. One challenge with agglomerative methods is that they can exhibit chaining, where larger clusters are naturally biased toward having closer distances to other points and so continue to get larger and larger and attract more data points into their cluster. Another disadvantage is that agglomerative methods may be much slower than divisive methods of constructing the hierarchy.

**Divisive:** In divisive hierarchical clustering methods, a top-down approach successively partitions the data points into a tree-like structure. The first step is to split the dataset into clusters using a flat-clustering method like K-Means. The clusters with the largest Sum of Squared Errors (SSE) are then partitioned further using a flat clustering method. The algorithm stops either when it reaches individual nodes or some minimum SSE. Divisive partitioning allows greater flexibility in terms of both the hierarchical structure of the tree and the level of balance in the different clusters. It is not necessary to have a perfectly balanced tree in terms of the depths of the different nodes or a tree in which the degree of every branch is exactly two. This allows the construction of a tree structure which allows different tradeoffs in the balancing of the node depths and node weights (number of data points in the node). Divisive hierarchical clustering can be faster than agglomerative hierarchical clustering, especially when the data doesn’t require constructing the tree all the way down to individual data points.

### Distribution-based clustering

Distribution-based clustering, sometimes called probabilistic clustering, groups together data points based on their probability distribution. This approach assumes that there is a process generating normal distributions for each dimension of the data which create the cluster centers. It’s different from centroid-based clustering in that it doesn’t use a distance metric like a Euclidean or Manhattan distance. Instead, distribution based approaches look for a well-defined distribution which appears across each dimension. The cluster means are the means of the Gaussian distribution across each dimension. Distribution based clustering is a model-based approach to clustering because it requires fitting a distribution multiple times across each dimension to find clusters, which means that it can be computationally expensive when working with large data sets.

One commonly used approach to distribution-based clustering is to create Gaussian Mixture Model (GMM) through Expectation-Maximization. A GMM is named because of the assumption that each cluster is defined by a Gaussian Distribution, often called a normal distribution.

Consider a dataset with two distinct clusters, A and B, which are both defined by two different normal distributions: one along the x-axis and one along the y-axis. Expectation-Maximization begins a random guess for what those two distributions along each axis and then proceeds to improve iteratively by alternating two steps:

**Expectation:** Assign each data point to each of the clusters and compute the probability that it came from the Cluster A and the Cluster B.

**Maximization:** Update the parameters that define each cluster, a weighted mean location and a variance-covariance matrix, based on the likelihood of each data point being in the cluster. Then repeat the Expectation step until the equation converges on the distributions observed for each cluster.

Each data point is given a probability of being associated with a cluster. This means that clustering via Expectation Maximization is a soft clustering approach and that a given point may be probabilistically associated with more than one cluster. This makes sense in some scenarios, a song might be somewhat folk and somewhat rock or a user may prefer television shows in Spanish but sometimes also watch shows in English.

### Density-based clustering

Density-based clustering works by detecting areas where points are concentrated and where they are separated by areas that are empty or sparse. Unlike centroid based approaches, like K-means, or distribution-based approaches, like Expectation Maximization, density-based clustering can detect clusters of an arbitrary shape. This can be extremely helpful when clusters aren’t defined around a specific location or distribution. Unlike other clustering algorithms, such as K-means and hierarchical clustering, a density-based algorithm can discover clusters of any shape, size, or density in your data. Density-based clustering also can distinguish between data points which are part of a cluster and those which should be labeled as noise. Density-based clustering is especially useful when working with datasets with noise or outliers or when we don’t have prior knowledge about the number of clusters in the data.

DBSCAN is an example of a clustering algorithm which takes a density-based approach to clustering. It uses a density-based spatial clustering approach to create clusters with a density passed in by the user which centers around a spatial centroid. The area immediately around the centroid is referred to as a neighborhood and DBSCAN attempts to define neighborhoods of clusters that have the specified density. For each cluster, DBSCAN will define three types of data points:

**Core Points:** A data point is a core point if the neighborhood around that data point contains at least as many points as the user specified minimum number of points.

**Border Points:** A data point is a border point if the neighborhood around that data point contains less than the minimum number of data points but the neighborhood around that point contains a core point.

**Outlier:** A data point is an outlier if it is neither a core point nor a border point. Essentially, this is the “other” class.

HDBSCAN is a variant of DBSCAN which doesn’t require any parameters to be set; this can make it even more flexible than the original. HDBSCAN is less sensitive to noise and outliers in the data. Also, DBSCAN can sometimes have trouble identifying clusters with non-uniform density. This was a primary motivation for HDBSCAN and so it handles clusters of varying density much more effectively.

### Grid-based clustering

Grid-based clustering algorithms are not used as often as the previous four approaches but can be helpful in high dimensional clustering where other clustering algorithms may not be as performant. In this approach, the algorithm partitions a high-dimensional data set into cells. Each cell is assigned a unique identifier called a cell ID, and all data points falling within a cell are considered part of the same cluster.

Grid-based clustering is an efficient algorithm for analyzing large multidimensional datasets as it reduces the time needed to search for nearest neighbors, which is a common step in many clustering methods.

One popular grid-based clustering algorithm is called STING, which stands for STatistical INformation Grid. In STING, the spatial area is divided into rectangular cells and several levels of cells at different resolution levels. High-level cells are divided into several low-level cells. STING can be very efficient at computing clusters in big data scenarios where the datasets are extremely large because it simply partitions the dataset iteratively into finer grids and evaluates the number of points within that grid. A disadvantage of STING is that the boundaries of clusters need to be horizontally or vertically defined, the algorithm can’t detect non-rectangular cluster boundaries.

Another grid based algorithm which is particularly powerful with high dimensional data is the Clustering In Quest or CLIQUE algorithm. CLIQUE combines a grid-based and density-based approaches to clustering. In this algorithm the dataspace is divided into a grid and the relative density of points within the cells of the grid are compared and subspaces that have similar densities are merged. This approach finds dense units in all subspaces of interest and then measures whether similar clusters should be connected together. This means that CLIQUE can detect clusters of arbitrary shapes in high-dimensional data.

## Evaluating clustering

There are several evaluation metrics for cluster analysis and the selection of the appropriate metric depends on the type of clustering algorithm and the corresponding dataset. Evaluation metrics can be generally split into two main categories: Extrinsic and Intrinsic.

### Intrinsic measures

Intrinsic measures are evaluation metrics for cluster analysis that use only the information within the data set. These can be helpful when you’re working with unlabeled data. The quality of the analysis is based entirely on relationships between data points. They can be used when we do not have prior knowledge or labels of the data. Common intrinsic measures include:

**Silhouette score:** This metric measures the similarity and dissimilarity of each data point with respect to its own cluster and all other clusters. The metrics values range from -1 to +1. A high value indicates that the object is well matched to its own cluster and poorly matched to neighboring clusters.

**Davies-Bouldin index:** This metric calculates the ratio of the within-cluster distance to the between-cluster distance. The lower the index score, the better the clustering performance.

**Calinski–Harabasz index:** This is also known as the Variance Ratio Criterion, this measures the ratio of between-cluster variance and within-cluster variance. The higher the Calinski-Harabasz ratio, the more well-defined a cluster is.

These evaluation metrics can help us compare the performance of different clustering algorithms and models, optimize clustering parameters, and validate the accuracy and quality of the clustering results.

### Extrinsic measures

Extrinsic measures use ground truth or external information to assess the validity of the clustering algorithm’s performance. This requires some form of label data that confirms the class or cluster in which each data point belongs. In this case, you can compare the accuracy of your clustering analysis with metrics often used in classification accuracy. Common extrinsic measures include:

**F-score** (also called F-measure): This metric determines the accuracy of the clustering algorithm by looking at precision and recall when comparing a proposed clustering to a ground truth. In the case of an F-score, higher is better.

**Purity:** This metric measures the fraction of data points that are correctly assigned to the same class or cluster they belong to. In the case of a purity measure, higher is better.

**Rand index:** This is a measure of the similarity between the true and predicted labels of the clustering algorithm, ranging from 0 to 1. A higher value indicates a better clustering performance.

**Variation of Information** (also called Shared Information Distance): This measures the amount of information lost and gained between two clusterings. This can be between a ground truth clustering and a algorithm-generated clustering or between two different clusterings. A lower number is better, since that shows a smaller distance between two clustering results.

## Applications of clustering

There are many application areas where clustering is a valuable tool for data mining or exploratory data analysis, we can list only a small sample of the application areas here to give a sense of the importance of this type of analysis.

### Anomaly Detection

Clustering can help uncover anomalies by measuring which data points are not included in the clustering structure defined by the cluster analysis. Data points that belong to small or very sparse clusters or that are far away from their assigned cluster can be considered anomalies. Density-based methods like Expectation Maximization are used to identify data points in dense regions as normal and those in low-density regions as anomalies.

### Market Research

When trying to understand what customer personas or subsets of markets might exist, clustering can be a powerful tool to help perform customer segmentation. You may be able combine demographic data with customer behavior data to find what kinds of characteristics and purchasing patterns most often correlate.

### Image Segmentation

Images can have their pixels clustered in a variety of ways that can help cut the image into different sections to split a foreground from a background, detect objects using similarities in color and brightness, or split images into regions of interest for further processing. With images, clustering methods process the pixels in the image and define areas within the image that represent the cluster.

### Document Processing

Clustering analysis can be helpful in processing documents in multiple ways. Documents can be grouped by similarity to show which documents are most similar to one another. This can be based on document length, word frequency distribution, or other various ways of quantifying key characteristics about the document. Another common use case is to analyze clusters of sections of a document based on keyword frequency, sentence length, or distributions of terms. This can help in doing document summarization or in breaking larger documents into smaller datasets for further analysis.
