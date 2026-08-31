---
title: What is collaborative filtering?
source: https://www.ibm.com/think/topics/collaborative-filtering
author:
- '[[Jacob  Murel Ph.D.]]'
- '[[Eda Kavlakoglu]]'
published: 2024-11-21
created: 2026-08-31
description: "Collaborative filtering groups users based on behavior and uses general group characteristics to recommend items to a target user."
---

## What is collaborative filtering?

Collaborative filtering is a type of recommender system. It groups users based on similar behavior, recommending new items according to group characteristics.

Collaborative filtering is an information retrieval method that recommends items to users based on how other users with similar preferences and behavior have interacted with that item. In other words, collaborative filtering algorithms group users based on behavior and use general group characteristics to recommend items to a target user. Collaborative recommender systems operate on the principle that similar users (behavior-wise) share similar interests and similar tastes.<sup>1</sup>

### Collaborative filtering vs content-based filtering

Collaborative filtering is one of two primary types of recommender systems, the other being content-based recommenders. This latter method uses item features to recommend similar items as the items with which a particular user has positively interacted in the past.<sup>2</sup> While collaborative filtering focuses on user similarity to recommend items, content-based filtering recommends items exclusively according to item profile features. Content-based filtering targets recommendations to one specific user’s preferences rather than a group or type as in collaborative filtering.

Both methods have witnessed many real-world applications in recent years, from e-commerce like Amazon to social media to streaming services. Together, collaborative and content-based systems form hybrid recommender systems. In fact, in 2009, Netflix adopted a hybrid recommender system through its Netflix prize competition.

## How collaborative filtering works

Collaborative filtering uses a matrix to map user behavior for each item in its system. The system then draws values from this matrix to plot as data points in a vector space. Various metrics then measure the distance between points as a means of calculating user-user and item-item similarity.

### User-item matrix

In a standard setting of collaborative filtering, we have a set of *n* users and a set of *x* items. Each user’s individual preference for each item is displayed in a user-item matrix (sometimes called a user rating matrix). Here, users are represented in rows and items in columns. In the *R<sub>ij</sub>* matrix, a given value represents the behavior of user *u* toward item *i*. These values may be continuous numbers provided by users (for example ratings) or binary values that signify whether a given user viewed or purchased the item. Here is an example user-time matrix for a bookshop website:

![Table illustrating the user-item matrix](https://assets.ibm.com/is/image/ibm/table-collaborative-filtering?ts=1763386748135&dpr=off)

This matrix displays user ratings for different books available. A collaborative filtering algorithm compares user’s provided ratings for each book. By identifying similar users or items based on those ratings, it predicts ratings for books a target user has not seen—represented by *null* in the matrix—and recommend (or not recommend) those books to the target user according.  

 The example matrix used here is full given it's restricted to four users and four items. However, in real world scenarios known users’ preferences for items are often limited, leaving the user-item matrix sparse.<sup>3</sup>

### Similarity measures

How does a collaborative recommendation algorithm determine similarity between various users? As mentioned, proximity in vector space is a primary method. But the specific metrics used to determine that proximity may vary. Two such metrics are cosine similarity and Pearson correlation coefficient.

### Cosine similarity

Cosine similarity signifies the measurement of the angle between two vectors. Compared vectors comprise a subset of ratings for given user or item. The cosine similarity score can be any value between -1 and 1. The higher the cosine score, the more alike two items are considered. Some sources recommend this metric for high-dimensional feature spaces. In collaborative filtering, vector points are pulled directly from the user-item matrix. Cosine similarity is represented by this formula, where *x* and *y* signify two vectors in vector space:<sup>4</sup>

![Illustration of the cosine similarity formula](https://assets.ibm.com/is/image/ibm/cosine-collaborative-filtering?ts=1763386748626&dpr=off)

### Pearson correlation coefficient (PCC)

PCC helps measure similarity between items or users by computing the correlation between two users’ or items’ respective ratings. PCC ranges between -1 and 1, which signify negative to identical correlation. Unlike cosine similarity, PCC uses all the ratings for a given user or item. For example, if calculating PCC between two users, we use this formula, in which *a* and *b* are different users, and *r<sub>ai</sub>* and *r<sub>bi</sub>* are that user's rating for item *i*:<sup>5</sup>

![Illustration of the Pearson correlation coefficient](https://assets.ibm.com/is/image/ibm/pcc-formula?ts=1763386748920&dpr=off)

## Types of collaborative recommender systems

There are two primary types of collaborative filtering systems: memory-based and model-based.

### Memory-based

Memory-based recommender systems, or neighbor-based systems, are extensions of [k-nearest neighbors classifiers](https://www.ibm.com/think/topics/knn) because they attempt to predict a target user’s behavior toward a given item based on similar users or set of items. Memory-based systems can be divided into two sub-types:

- ***User-based filtering*** recommends items to a target user based on the preferences of behaving users. The recommendation algorithm compares a target user’s past behavior to other users. Specifically, the system assigns each user a weight representing their perceived similarity with the target user—this is the target user’s neighbors. It then selects *n* users with the highest weights and computes a prediction of the target user’s behavior (e.g. movie rating, purchase, dislikes, etc.) from a weighted average of the selected neighbors’ behavior. The system then recommends items to the target user based on this prediction. The principle is that, if the target user behaved similarly to this group in the past, they will behave similarly with unseen items. User-based similarity functions are computed between rows in the user-item matrix.<sup>6</sup>
- ***Item-based filtering*** recommends new items to a target user based on that user’s behavior toward similar items. Note, however, that in comparing items, the collaborative system does not compare item features (as in content-based filtering) but instead how users interact with those items. For instance, in a movie recommendation system, the algorithm may identify similar movies based on correlations between all user ratings for each movie (correcting for each user’s average rating). The system will then recommend a new movie to a target user based on correlated ratings. That is, if the target user rated movie *a* and *b* highly but has not seen movie *c*, and other users who rated the former two highly also rated movie *c* highly, the system will recommend movie *c* to the target user. In this way, item-based filtering calculates item similarity through user behavior. Item-based similarity functions are computed between columns in the user-item matrix.<sup>7</sup>

### Model-based

At times, literature describes memory-based methods as instance-based learning methods. This points to how user and item-based filtering make predictions specific to a given instance of user-item interaction, such as a target user’s rating for an unseen movie.

By contrast, model-based methods create a predictive machine learning model of the data. The model uses present values in the user-item matrix as the training dataset and produces predictions for missing values with the resultant model. Model-based methods thus use data science techniques and machine learning algorithms such as [decision trees](https://www.ibm.com/think/topics/decision-trees), [Bayes classifiers](https://www.ibm.com/think/topics/naive-bayes), and [neural networks](https://www.ibm.com/think/topics/neural-networks) to recommend items to users.<sup>8</sup>

Matrix factorization is a widely discussed collaborative filtering method often classified as a type of latent factor model. As a latent factor model, matrix factorization assumes user-user or item-item similarity can be determined through a select number of features. For instance, a user’s book rating may be predicted using only book genre and user age or gender. This lower-dimensional representation thereby aims to explain, for example, book ratings by characterizing items and users according to a few select features pulled from user feedback data.<sup>9</sup> Because it reduces the features of a given vector space, matrix factorization also serves as a [dimensionality reduction](https://www.ibm.com/think/topics/dimensionality-reduction) method.<sup>10</sup>

## Advantages and disadvantages of collaborative filtering

### Advantages

Compared to content-based systems, collaborative filtering is more effective at providing users with novel recommendations. Collaborative-based methods draw recommendations from a pool of users who share interests with one target user. For instance, if a user group liked the same set of items as the target user, but also liked an additional item unknown to the target user because it shares no features with the previous set of items, a collaborative filtering system recommends this novel item to the user. Collaborative filtering can recommend items that a target user may have not considered but that nevertheless appeal to their user type.<sup>11</sup>

### Disadvantages

The cold start problem is perhaps the most widely cited disadvantage of collaborative filtering systems. It occurs when a new user (or even a new item) enters the system. That user’s lack of item-interaction history prevents the system from being able to evaluate the new user’s similarity or association with existing users. By contrast, content-based systems are more adept at handling new items, although they also struggle with recommendations for new users.<sup>12</sup>  

 Data sparsity is another chief problem that can plague collaborative recommendation systems. As mentioned, recommender systems typically lack data on user preferences for most items in the system. This means that most of the system’s feature space is empty, a condition called data sparsity. As data sparsity increases, vector points become so dissimilar that predictive models become less effective at identifying explanatory patterns.<sup>13</sup> This is a primary reason why matrix factorization—and related latent factor methods such as singular value decomposition—is popular in collaborative filtering, as it alleviates data sparsity by reducing features. Other methods implemented for resolving this issue may also involve users themselves assessing and providing information on their own interests, which the system can then use to filter recommendations.

## Recent research

While past studies have approached recommendation as a prediction or classification problem, a substantive body of recent research argues that it is understood as a sequential, decision-making problem. In this paradigm, reinforcement learning might be more suitable for addressing recommendation. This approach argues that recommendation updates in real-time according to user-item interaction; as the user skips, clicks, rates, purchases suggested items, the model develops an optimal policy from this feedback to recommend new items.<sup>14</sup> Recent studies propose a wide variety of reinforcement learning applications to address mutable, long-term user interests, which pose challenges for both content-based and collaborative filtering.<sup>15</sup>

## Footnotes

<sup>1 </sup>"Collaborative Filtering". *Encyclopedia of Machine Learning and Data Mining*. Springer. 2017. Mohamed Sarwat and Mohamed Mokbel. "Collaborative Filtering". *Encyclopedia of Database Systems*. Springer. 2018.

<sup>2</sup> Prem Melville and Vikas Sindhwani. "Recommender Systems". *Encyclopedia of Machine learning and Data Mining*. Springer. 2017.

<sup>3</sup> YUE SHI, MARTHA LARSON and ALAN HANJALIC. "Collaborative Filtering beyond the User-Item Matrix: A Survey of the State of the Art and Future Challenges". ACM Computing Surveys. Vol. 47, No. 1. 2014. https://dl.acm.org/doi/10.1145/2556270. Kim Falk. *Practical Recommender Systems*. Manning Publications. 2019.

<sup>4</sup> Elsa Negre. *Information and Recommender Systems*. Vol. 4. Wiley-ISTE. 2015. Sachi Nandan Mohanty, Jyotir Moy Chatterjee, Sarika Jain, Ahmed A. Elngar and Priya Gupta. *Recommender System with Machine Learning and Artificial Intelligence*. Wiley-Scrivener. 2020.

<sup>5</sup> Kim Falk. *Practical Recommender Systems*. Manning Publications. 2019. J. Ben Schafer, Dan Frankowski, Jon Herlocker and Shilad Sen. "Collaborative Filtering Recommender Systems". *The Adaptive Web: Methods and Strategies of Web Personalization*. Springer. 2007.

<sup>6</sup> Charu Aggarwal. *Recommender Systems: The Textbook*. Springer. 2016. Prem Melville and Vikas Sindhwani. "Recommender Systems". *Encyclopedia of Machine Learning and Data Mining*. Springer. 2017.

<sup>7</sup> Charu Aggarwal. *Recommender Systems: The Textbook*. Springer. 2016. Kim Falk. *Practical Recommender Systems*. Manning Publications. 2019.

<sup>8</sup> Charu Aggarwal. *Recommender Systems: The Textbook*. Springer. 2016.

<sup>9</sup> Prem Melville and Vikas Sindhwani. "Recommender Systems". *Encyclopedia of Machine Learning and Data Mining*. Springer. 2017. Yehuda Koren, Steffen Rendle and Robert Bell. "Advances in Collaborative Filtering". *Recommender Systems Handbook*. 3rd edition. Springer. 2022.

<sup>10</sup> Charu Aggarwal. *Recommender Systems: The Textbook*. Springer. 2016.

<sup>11</sup> Sachi Nandan Mohanty, Jyotir Moy Chatterjee, Sarika Jain, Ahmed A. Elngar and Priya Gupta. *Recommender System with Machine Learning and Artificial Intelligence*. Wiley-Scrivener. 2020. Charu Aggarwal. *Recommender Systems: The Textbook*. Springer. 2016.

<sup>12</sup> Charu Aggarwal. *Recommender Systems: The Textbook*. Springer. 2016. Ian Goodfellow, Yoshua Bengio and Aaron Courville. *Deep Learning*. MIT Press. 2016.

<sup>13</sup> Ian Goodfellow, Yoshua Bengio and Aaron Courville. *Deep Learning*. MIT Press. 2016.

<sup>14</sup> Guy Shani, David Heckerman, Ronen I. Brafman. "An MDP-Based Recommender System". *Journal of Machine Learning Research*. Vol. 6. No. 43. 2005. pp. 1265−1295. [https://www.jmlr.org/papers/v6/shani05a.html](https://www.jmlr.org/papers/v6/shani05a.html). Yuanguo Lin, Yong Liu, Fan Lin, Lixin Zou, Pengcheng Wu, Wenhua Zeng, Huanhuan Chen, and Chunyan Miao. "A Survey on Reinforcement Learning for Recommender Systems". *IEEE Transactions on Neural Networks and Learning Systems*. 2023. [https://ieeexplore.ieee.org/abstract/document/10144689](https://ieeexplore.ieee.org/abstract/document/10144689). M. Mehdi Afsar, Trafford Crump, and Behrouz Far. "Reinforcement Learning based Recommender Systems: A Survey". ACM Computing Surveys. Vol. 55. No. 7. 2023. [https://dl.acm.org/doi/abs/10.1145/3543846](https://dl.acm.org/doi/abs/10.1145/3543846).

<sup>15</sup> Xinshi Chen, Shuang Li, Hui Li, Shaohua Jiang, Yuan Qi, Le Song. "Generative Adversarial User Model for Reinforcement Learning Based Recommendation System". *Proceedings of the 36th International Conference on Machine Learning*. *PMLR*. No. 97. 2019. pp. 1052-1061. [http://proceedings.mlr.press/v97/chen19f.html](https://proceedings.mlr.press/v97/chen19f.html). Liwei Huang, Mingsheng Fu, Fan Li, Hong Qu, Yangjun Liu and Wenyu Chen. "A deep reinforcement learning based long-term recommender system". Knowledge-Based Systems. Vol. 213. 2021. [https://www.sciencedirect.com/science/article/abs/pii/S0950705120308352](https://www.sciencedirect.com/science/article/abs/pii/S0950705120308352).
