---
title: What is hierarchical clustering?
source: https://www.ibm.com/think/topics/hierarchical-clustering
author:
- '[[Joshua Noble]]'
published: 2024-08-05
created: 2026-08-31
description: "Hierarchical clustering is an unsupervised machine learning algorithm that groups data into nested clusters to help find patterns and connections in datasets."
---

## What is hierarchical clustering?

Hierarchical clustering is an unsupervised machine learning algorithm that groups data into a tree of nested clusters. The main types include agglomerative and divisive. Hierarchical cluster analysis helps find patterns and connections in datasets. Results are presented in a dendrogram diagram showing the distance relationships between clusters.

Clustering is an [unsupervised machine learning](https://www.ibm.com/think/topics/unsupervised-learning) technique used in data analysis to detect and group similar objects. Hierarchical cluster analysis (HCA), or hierarchical clustering, groups objects into a cluster hierarchy without enforcing a linear order within them. Many disciplines, such as biology, image analysis and the social sciences, use hierarchical clustering methods to explore and recognize patterns in datasets. Use cases include categorizing populations in clinical research, customer segmentation and detecting communities of nodes in network models.

There are two types of hierarchical clustering:

- Agglomerative or bottom-up approach<sup>1</sup> that repeatedly merges clusters into larger ones until a single cluster emerges.

- Divisive or top-down approach that<sup>2 </sup>starts with all data in a single cluster and continues to split out successive clusters until all clusters are singletons.

Hierarchical clustering analysis has high computational costs. While using a [heap](https://www.ibm.com/docs/en/i/7.5?topic=memory-heap-overview) can reduce computation time, memory requirements are increased. Both the divisive and agglomerative types of clustering are “greedy,” meaning that the algorithm decides which clusters to merge or split by making the locally optimal choice at each stage of the process. It is also possible to apply a stop criterion, where the algorithm stops agglomeration or splitting clusters when it reaches a predetermined number of clusters.

A tree-like diagram called a dendrogram<sup>3</sup> is often used to visualize the hierarchy of clusters. It displays the order in which clusters have been merged or divided and shows the similarity or distance between data points. Dendrograms can also be understood as a nested list of lists<sup>4</sup> with attributes.

![Scatter plot of points A to F on the left and the resulting dendrogram tree structure on the right](https://assets.ibm.com/is/image/ibm/ICLH_Diagram_Batch_02_14A-UnsupervisedLearning?ts=1763387511356&dpr=off)

## How hierarchical clustering works

Hierarchical clustering algorithms use the concept of a dissimilarity matrix to decide which clusters to merge or divide. Dissimilarity is the distance between two data points as measured by a chosen linkage method. The values in a dissimilarity matrix express:

- The distance<sup>5</sup>, a Euclidean distance as an example, between single points in a set

- A linkage clustering criterion, which specifies dissimilarity as a function of the pairwise distances of points across sets

### Linkage methods

Let’s explore the most common Euclidean distance linkage methods. Examples of other [distance metrics](https://www.ibm.com/think/topics/knn) that can be used include Minkowski, Hamming, Mahalanobis, Hausdorf and Manhattan distance. Note that each linkage method generates different clusters from the same dataset. Selecting the appropriate linkage clustering method depends on factors such as the type of data being clustered, data density, cluster shape and whether there are outliers or noise in the dataset.

#### Min (single) linkage

The single linkage method analyzes pairwise distances between items in two clusters and then uses the minimum distance between the clusters. The min method handles nonelliptical cluster shapes well but will be impacted by noise and outliers. It has a limitation known as the chaining effect<sup>6</sup>. A few points creating a bridge between a cluster pair can result in the two clusters merging into one. The min linkage criteria can be represented as:

mina∈A,b∈Bd(a,b)

where **A** and **B** are two sets of observations and **d** is a distance function.

#### Max (complete) linkage

Cluster distances can also be calculated based on the points that are furthest away from each other. The max method is less sensitive than the min method to noise and outliers, but using it can skew the results when there are globular or large clusters. Max-linkage often produces more spherical clusters than min-linkage. The max linkage can be represented in the formula:

maxa∈A,b∈Bd(a,b)

where **A** and **B** are two sets of observations and **d** is distance.

#### Average linkage

These methods, introduced by Sokal and Michener<sup>7 </sup>, define the distance between clusters as the average distance between pairs across all pairs of points in the clusters. The algorithm can be either the unweighted pair group method with arithmetic mean (UPGMA) or the weighted pair group method with arithmetic mean (WPGMA). The meaning of "unweighted" here is that all distances contribute equally to each average.

UPGMA is represented by the formula

1∣A∣·∣B∣∑a∈A∑b∈Bd(a,b)

where *A* and *B* are two sets of observations and *d* is distance.

WPGMA is represented by the formula

d(i∪j,k)=d(i,k)+d(j,k)2

where **i** and **j** are the closest clusters being combined in each step to form a new cluster of the union of **i** and **j**. We can then calculate the distance to another cluster **k**, which is the arithmetic mean of the average distances between data points in **k** and **i** and **k** and **j.**

#### Centroid linkage

Here, we use the distance between cluster centers or centroids. The distance between centroids is calculated by using a distance function:

∥μA-μB∥2

where **μ<sub>A</sub>** is the centroid of **A** and **μ<sub>B</sub>** is the centroid of **B**.

#### Ward's minimum variance method

Joe H. Ward introduced the minimal increase of sum of squares (MISSQ) method<sup>8</sup> in the 1960s. Every data point starts in its own cluster. This approach means that the sum of squares between data points is initially at zero, then increases as we merge clusters. Ward's method minimizes the sum of the squared distances of the points from the cluster centers as they are merged. Ward's method is a good choice for quantitative variables<sup>9</sup>, and it is less affected by noise or outliers. It can be represented as:

∣A∣·∣B∣A∪B∥μA-μB∥2=∑x∈A∪B∥x-μA∪B∥2-∑x∈A∥x-μA∥2-∑x∈B∥x-μB∥2

where the mean of A and mean of B are the centroids of **A** and **B** respectively, and **x** is a data point that belongs to the union of **A** and **B**

#### Lance-Williams algorithm

Ward's minimum variance method can be refined by using a Lance-Williams algorithm. These algorithms use a recursive formula to update cluster distances and find the optimal closest cluster pair to merge.

### Agglomerative clustering steps

In agglomerative hierarchical clustering, also known as agglomerative nesting (AGNES), each data point starts as a cluster. The algorithm uses a selected linkage clustering criterion based on a dissimilarity matrix to decide which pair of clusters to join. The algorithm moves up the hierarchy and keeps pairing clusters until everything has been linked together, creating a hierarchical series of nested clusters. Roughly speaking the agglomerative clustering steps<sup>10</sup> are:

1. Compute the dissimilarity matrix by using a particular distance metric.

2. Assign each data point to a cluster.

3. Merge the clusters based on a linkage criterion for the similarity between clusters.

4. Update the distance matrix.

5. Repeat steps 3 and 4 until a single cluster remains or any stop criterion is met.

### Divisive clustering steps

The principles behind divisive hierarchical clustering were developed by Macnaughton-Smith and others<sup>11</sup> in 1964 and explored further by Kaufman and Rousseeuw with their DIANA (Divisive ANAlysis clustering) algorithm<sup>12</sup> in 1990. Divisive clustering uses the opposite approach to agglomerative clustering. All data points start in a single cluster that is repeatedly split into more clusters. Splitting occurs until either all the remaining clusters are singletons or a stop criterion such as a predefined number of clusters is met. Divisive methods are better at identifying large clusters<sup>13</sup> and can be more accurate than agglomerative methods because the algorithm considers the entire dataset distribution from the start of the process.

To improve efficiency, divisive methods use flat clustering algorithms such as k-means to split the dataset into clusters. The number of clusters must be specified upfront. The k-means algorithm splits clusters by minimizing the within-cluster sum of squares between centroid points. This is known as the inertia criterion<sup>14</sup>. The divisive clustering steps<sup>15</sup> are:

1. Start with all data points for a dataset size N (d1, d2, d3 ... dN) in one cluster.

2. Split the cluster into two dissimilar or heterogeneous clusters by using a flat clustering method such as the k-means algorithm.

3. Repeat step 2, choosing the best cluster to split and removing the outliers from the least cohesive cluster after each iteration.

4. Stop when each example is in its own single cluster, otherwise repeat step 3.

## Interpreting hierarchical clustering results

Cluster results are typically presented in a dendrogram (binary tree structure). The **x**-axis in the dendrogram represents the data points and the **y**-axis, or the height of the lines, shows how far apart the clusters were when they were merged.

You can use a dendrogram to decide how many clusters<sup>16</sup> will be in your final clustering model. One strategy is identifying the natural cutoff point in the tree where the branches dwindle and become longer. Alternatively, the number of clusters is given by the number of vertical lines crossed when a horizontal line cuts the dendrogram.

In the example image shown here, the horizontal line **H1** cuts two vertical lines. This shows that there are two clusters at this point in the process—one cluster with points 5, 8, and 2 and one cluster with the remaining points. The further the horizontal line can move up or down without cutting other horizontal lines in the dendrogram, the better the selection of this number of clusters is for your clustering model. In the example below, the horizontal line **H2** selects four clusters. **H2** is not able to move up and down as far as **H1** before it cuts other horizontal lines. This scenario shows that the two-cluster choice (**H1**) is probably more appropriate for your clustering model.

![Dendrogram diagram, plotting data points (x-axis) and the height of the lines shows how far apart the clusters were when they were merged (y-axis)](https://assets.ibm.com/is/image/ibm/7-1_dendrogram-diagram-with-h1-h2-lines?ts=1763387513259&dpr=off)   Cutting a dendrogram with horizontal lines to determine the number of clusters

A robust clustering model<sup>17</sup> creates clusters with high intraclass similarity and low interclass similarity. However, it can be difficult to define cluster quality, and your selection of linkage criterion and cluster numbers can significantly impact your results. Thus, when building a clustering model, try out different options and select those that best help you explore and reveal patterns in the dataset for future consideration. Factors to consider<sup>18</sup> include:

- The number of clusters that are practical or logical for the dataset (given dataset size, cluster shapes, noise and so on)

- Statistics, such as the mean, maximum and minimum values for each cluster

- The best dissimilarity metric or linkage criterion to apply

- The impact of any outliers or outcome variables

- Any specific domain or dataset knowledge

Other methods to help determine the optimal number of clusters<sup>19</sup> include:

- The elbow method, where you plot the within-cluster sum of squares against the number of clusters and determine the "elbow" (the point where the plot levels off)

- Gap statistic, where you compare the actual within-cluster sum of squares to the expected within-cluster sum of squares for a null reference distribution and identify the largest gap.

## Use cases for hierarchical clustering

Hierarchical clustering provides data scientists with insights into the structure and relationships within datasets and it can be applied in various use cases.

### Business

Hierarchical clustering can help analyze trends and segment customer data—-for example, grouping by product choice, demographic, purchasing behavior, risk profile or interactions with social media.

### Clinical research and bioinformatics

Patient cohorts for clinical research can run into the thousands. Hierarchical clustering helps categorize mixed populations into more homogeneous groups<sup>20</sup> by using, for example, diagnostic criteria, physiological responses or DNA mutations. It can also be applied to group species by biological features to understand evolutionary development.

### Image and information processing

Hierarchical clustering is used in image-based text recognition applications to group handwritten characters by their shape. It is also used to store and retrieve information by using certain criteria or to categorize search results.

### Implementing hierarchical clustering in Python or R

Both Python and the R programming language are widely used in data science. Python is flexible and can handle a broad spectrum of tasks. Alternatively, R is specifically designed for statistical computing and provides rich options for visualizing your hierarchical clustering analysis.

Python provides the AgglomerativeCluster function<sup>21</sup> (see also agglomerative clustering examples<sup>22</sup> on sklearn), and SciPy provides a function to plot dendrograms<sup>23</sup>. Packages such as dendextend<sup>24</sup> enhance R's dendrogram functionality, improving sensitivity analysis and enabling you to compare and manipulate different dendrograms. For a hands-on experience, check out our step-by-step tutorials: [how to implement hierarchical clustering in Python](https://developer.ibm.com/tutorials/awb-implement-hierarchical-clustering-python/) and [how to implement hierarchical clustering in R](https://developer.ibm.com/tutorials/awb-implement-hierarchical-clustering-in-r/).

## Footnotes

<sup>1</sup> Murtagh, F., Legendre, P., “Ward’s Hierarchical Agglomerative Clustering Method: Which Algorithms Implement Ward’s Criterion?,” 2014, *J Classif* 31, 274–295, [https://link.springer.com/article/10.1007/s00357-014-9161-z](https://link.springer.com/article/10.1007/s00357-014-9161-z)

<sup>2</sup> Kaufman, L.; Rousseeuw, P. J., Finding Groups in Data: An Introduction to Cluster Analysis. Wiley. Chp 6. Divisive Analysis (Program DIANA) pp. 253–279, [https://onlinelibrary.wiley.com/doi/book/10.1002/9780470316801](https://onlinelibrary.wiley.com/doi/book/10.1002/9780470316801)

<sup>3</sup> Galili, T., “Introduction to dendextend,” The Comprehensive R Archive Network, 2023, [https://cran.r-project.org/web/packages/dendextend/index.html](https://cran.r-project.org/web/packages/dendextend/index.html)

<sup>4</sup> Lecture Notes from Penn State Eberly College of Science, “Hierarchical Clustering”, [https://online.stat.psu.edu/stat555/node/85/](https://online.stat.psu.edu/stat555/node/85/)

<sup>5, 17 </sup>Maimon, O., Rokach, L., *Data Mining and Knowledge Discovery Handbook*, 2010 2nd ed, Springer, [https://link.springer.com/book/10.1007/978-0-387-09823-4](https://link.springer.com/book/10.1007/978-0-387-09823-4)

<sup>6</sup> Sokal, R, Michener, C., “A statistical method for evaluating systematic relationships,” 1958, University of Kansas Science Bulletin, 38: 1409–1438, [https://archive.org/details/cbarchive_33927_astatisticalmethodforevaluatin1902/page/n1/mode/2up](https://archive.org/details/cbarchive_33927_astatisticalmethodforevaluatin1902/page/n1/mode/2up)

<sup>7 </sup>Ward, J. H., “Hierarchical Grouping to Optimize an Objective Function,” 1963, *Journal of the American Statistical Association*, 58 (301): 236–244, [https://www.tandfonline.com/doi/abs/10.1080/01621459.1963.10500845](https://www.tandfonline.com/doi/abs/10.1080/01621459.1963.10500845).

<sup>8</sup> Lecture Notes from Penn State Eberly College of Science, “Applied Multivariate Statistical Analysis”, [https://online.stat.psu.edu/stat505/lesson/14/14.7](https://online.stat.psu.edu/stat505/lesson/14/14.7)

<sup>9, 15</sup> Shetty P. and Singh S., “Hierarchical Clustering: A Survey,” *International Journal of Applied Research,* Vol 7 Issue 4, Part C, 2021, [https://www.allresearchjournal.com/archives/?year=2021&vol=7&issue=4&part=C&ArticleId=8484](https://www.allresearchjournal.com/archives/?year=2021&vol=7&issue=4&part=C&ArticleId=8484)

<sup>10 </sup>Macnaugton-Smith, P., Williams, W., Dale, M., et al., “Dissimilarity Analysis: a new Technique of Hierarchical Sub-division,” *Nature* 202, 1034–1035 (1964), [https://www.nature.com/articles/2021034a0](https://www.nature.com/articles/2021034a0)

<sup>12</sup> Boehmke, B., Greenwell, B., *Hands-On Machine Learning with R,* Taylor and Francis, 2020, [https://bradleyboehmke.github.io/HOML/](https://bradleyboehmke.github.io/HOML/)

<sup>13</sup> Cavalli-Sforza, L. L., and Edwards A. W. F., “Phylogenetic analysis: models and estimation procedures,” 1967, *Evolution* 21: 550–570 and Am. J. Hum. Genet. 19: 233–257, [https://pmc.ncbi.nlm.nih.gov/articles/PMC1706274/](https://pmc.ncbi.nlm.nih.gov/articles/PMC1706274/)

<sup>14 </sup>Sci-kit learn 1.3.2, 2.3 Clustering, [https://scikit-learn.org/stable/modules/clustering.html](https://scikit-learn.org/stable/modules/clustering.html)

<sup>16</sup> Lecture notes from MIT OpenCourseWare, 2017, [https://ocw.mit.edu/courses/15-071-the-analytics-edge-spring-2017/pages/clustering/recommendations-worth-a-million-an-introduction-to-clustering/video-5-hierarchical-clustering/](https://ocw.mit.edu/courses/15-071-the-analytics-edge-spring-2017/pages/clustering/recommendations-worth-a-million-an-introduction-to-clustering/video-5-hierarchical-clustering/)

<sup>18</sup> Lecture notes from the University of Washington, 2001, [https://courses.cs.washington.edu/courses/csep546/04au/pdf-slides/10.pdf](https://courses.cs.washington.edu/courses/csep546/04au/pdf-slides/10.pdf)

<sup>19</sup> Boehmke, B., University of Cincinnati Business Analytics R Programming Guide, [https://uc-r.github.io/hc_clustering#algorithms](https://uc-r.github.io/hc_clustering#algorithms)

<sup>20</sup> QCBS R Workshop Series, [https://r.qcbs.ca/workshop09/book-en/clustering.html](https://r.qcbs.ca/workshop09/book-en/clustering.html)

<sup>21</sup> Zhongheng Zhang et al., “Hierarchical cluster analysis in clinical research with heterogeneous study population: highlighting its visualization with R,” *Annals of Translational Medicine*. 2017 Feb; 5(4): 75, [https://atm.amegroups.org/article/view/13789/14063](https://atm.amegroups.org/article/view/13789/14063)

<sup>22, 23</sup> Scit-kit learn 1.3.2 documentation, [https://scikit-learn.org/stable/modules/generated/sklearn.cluster.AgglomerativeClustering.html](https://scikit-learn.org/stable/modules/generated/sklearn.cluster.AgglomerativeClustering.html)

<sup>24</sup> SciPy Manual v1.11.4, [https://docs.scipy.org/doc/scipy/reference/generated/scipy.cluster.hierarchy.dendrogram.html](https://docs.scipy.org/doc/scipy/reference/generated/scipy.cluster.hierarchy.dendrogram.html)
