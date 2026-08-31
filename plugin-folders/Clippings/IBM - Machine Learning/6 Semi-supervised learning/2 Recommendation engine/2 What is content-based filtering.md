---
title: What is content-based filtering?
source: https://www.ibm.com/think/topics/content-based-filtering
author:
- '[[Jacob  Murel Ph.D.]]'
- '[[Eda Kavlakoglu]]'
published: 2024-11-27
created: 2026-08-31
description: "Content-based filtering retrieves information using item features relevant to a query based on features of other items a user expresses interest in."
---

## What is content-based filtering?

Content-based filtering is one of two main types of recommender systems. It recommends items to users according to individual item features.

Content-based filtering is an information retrieval method that uses item features to select and return items relevant to a user’s query. This method often takes features of other items in which a user expresses interest into account.<sup>1 </sup>*Content-based* is a bit of a misnomer however. Some content-based recommendation algorithms match items according to descriptive features (for example, metadata) attached to items rather than the actual content of an item.<sup>2</sup> Nevertheless, several content-based methods—for example content-based image retrieval or natural language processing applications—do match items according to intrinsic item attributes.

### Content-based filtering vs collaborative filtering

Content-based filtering is one of two primary types of recommendation systems. The other is the collaborative filtering method. This latter approach groups users into distinct groups based on their behavior. Using general group characteristics, it then returns specific items to a whole group on the principle that similar users (behavior-wise) are interested in similar items.<sup>3</sup>

Both methods have witnessed many real-world applications in recent years, from e-commerce like Amazon to social media to streaming services. Together, collaborative and content-based systems form hybrid recommender systems. In fact, in 2009, Netflix adopted a hybrid recommender system through its Netflix prize competition.

## How content-based filtering works

Content-based recommender systems (CBRSs) incorporate machine learning algorithms and data science techniques to recommend new items and answer queries.

### Components of content-based filtering

In CBRSs, the recommendation engine essentially compares a user profile and item profile to predict user-item interaction and recommend items accordingly.

- **The *item profile*** is an item’s representation in the system. It consists of an item’s feature set, which can be internal structured characteristics or descriptive metadata. For instance, a streaming service can store movies according to genre, release date, director, and so forth.
- **The *user profile*** represents user preferences and behavior. It can consist of representations of those items in which a user has previously shown interest. It also consists of user data of their past interactions with the system (for example, user likes, dislikes, ratings, queries, etc.).<sup>4</sup>

### Item representations

CBRSs often represent items and users as embeddings in a vector space. Items are converted to vectors using metadata descriptions or internal characteristics as features. For example, say we build item profiles to recommend new novels to users as part of an online bookshop. We then create profiles for each novel using representative metadata, such as author, genre, etc. A novel’s value for a given category can be represented with Boolean values, where 1 indicates the novel’s presence in that category and 0 indicates its absence. With this system, we can potentially represent a small handful of novels according to genre:

![Illustration of an item representations table](https://assets.ibm.com/is/image/ibm/content-based-filtering-table-1?ts=1763386388329&dpr=off)

Here, each genre is a different dimension of our vector space, with the values in a given novel’s representing its position in that vector space. For example, Little Women is located at (1,0,1), Northanger Abbey at (0,0,1), and so forth. We can visualize this sample vector space as:

![Illustration of a specific position within a vector space](https://assets.ibm.com/is/image/ibm/content-based-filtering-bow-graphic?ts=1763386388482&dpr=off)

The closer two novel-vectors are in vector space, the more similar our system considers them to be according to the provided features.<sup>5</sup> Peter Pan and Treasure Island share the exact same features, appearing at the same vector point (1,1,0). According to our system, then, they are identical. Indeed, they share many plot devices (for example, isolated islands and pirates) and themes (for example, growing up or resistance thereto). By contrast, although *Little Women* is also a children’s novel, it is not adventure but a bildungsroman (coming-of-age). Although *Little Women* is a children’s novel like *Peter Pan* and *Treasure Island*, it lacks their feature values for adventure and possesses a feature value of 1 for bildungsroman, which the latter two lack. This positions *Little Women* closer to *Northanger Abbey* in vector space, as they share the same feature values for the adventure and bildungsroman features.

Because of their similarity in this space, if a user has previously purchased *Peter Pan*, the system will recommend those novels closest to *Peter Pan*—such as *Treasure Island*—to that user as a potential future purchase. Note that were we to add more novels and genre-based features (for example, fantasy, gothic, etc.) novel positions in the vector space will move. For instance, if adding a fantasy genre dimension, *Peter Pan* and *Treasure Island* may move marginally from another given the former is often considered fantasy while the latter is not.

Note that item vectors may also be created using items’ internal characteristics as features. For instance, we can convert raw text items (for example, news articles) into a structured format and map them onto a vector space, such as a "bag of words model". In this approach, each word used throughout the corpus becomes a different dimension of the vector space, and articles that use similar keywords appear closer to one another in the vector space.

### Similarity metrics

How does a content-based filtering system determine similarity between any number of items? As mentioned, proximity in vector space is a primary method. The specific metrics used to determine that proximity, however, may vary. Common metrics include:

**Cosine similarity** signifies the measurement of the angle between two vectors. It can be any value between -1 and 1. The higher the cosine score, the more alike two items are considered. Some sources recommend this metric for high-dimensional feature spaces. Cosine similarity is represented by this formula, where *x* and *y* signify two item-vectors in the vector space:<sup>7</sup>

![Illustration of the cosine similarity formula](https://assets.ibm.com/is/image/ibm/content-based-filtering-cosine-similarity?ts=1763386388807&dpr=off)

**Euclidean distance** measures the length of a hypothetical line segment joining two vector points. Euclidean distance scores may be as low as zero with no upper limit. The smaller two item-vectors’ Euclidean distance, the more similar they are considered. Euclidean distance is calculated with this formula, where *x* and *y* represent two item-vectors:<sup>8</sup>

![Illustration of the Euclidean distance formula](https://assets.ibm.com/is/image/ibm/content-based-filtering-euclidean-distance?ts=1763386388961&dpr=off)

**Dot product** is the product of the cosine of the angle between two vectors and each vectors respective Euclidean magnitude from a defined origin. In other words, it is the cosine of two vectors multiplied by each vector’s projected length—length being a vector’s displacement from a defined origin, such as (0,0). Dot product is best used for comparing item’s with notably different magnitudes—for example think popularity of books or movies. It is represented by this formula, in which *d* and *q* again represent two item-vectors:<sup>9</sup>

![Illustration of the dot product formula](https://assets.ibm.com/is/image/ibm/content-based-filtering-dot-product?ts=1763386389110&dpr=off)

Note that these metrics are sensitive to how the compared vectors are weighted, as different weightings can significantly affect these scoring functions.<sup>10</sup> Other possible metrics for determining vector similarity are the Pearson correlation coefficient (or Pearson’s correlation) and Jaccard similarity, and dice index.<sup>11</sup>

### User-item interaction prediction

CBRSs create a user-based classifier or regression model to recommend items to a specific user. To start, the algorithm takes descriptions and features of those items in which a particular user has previously shown interest—that is the user profile. These items constitute the training dataset used to create a classification or regression model specific to that user. In this model, item attributes are the independent variables, with the dependent variable being user behavior (for example, user ratings, likes, purchases, etc.). The model trained on this past behavior aims to predict future user behavior for possible items and recommend items according to the prediction.<sup>12</sup>

## Advantages and disadvantages of content-based filtering

### Advantages

The cold-start problem essentially consists of how a system handles new users or new items. Both pose a problem in collaborative filtering because it recommends items by grouping users according to inferred similarities of behavior and preference. New users do not have an evidenced similarity with others, however, and new items do not have enough user interaction (for example, ratings) for recommending them. While content-based filtering struggles with new users, it nevertheless adeptly handles incorporating new items. This is because it recommends items based on internal or metadata characteristics rather than past user interaction.<sup>13</sup>  

 Content-based filtering enables greater degree of transparency by providing interpretable features that explain recommendations. For example, a movie recommendation system may explain why a certain movie is recommended, such as genre or actor overlap with previously watched movies. The user may therefore make a more informed decision on whether to watch the recommended movie.<sup>14</sup>

### Disadvantages

One chief disadvantage of content-based filtering is feature limitation. Content-based recommendations are derived exclusively from the features used to describe items. A system’s item features may not be able to capture what a user likes however. For instance, returning to the movie recommendation system example, assume a user watches and likes the 1944 movie *Gaslight*. A CBRS may recommend other movies directed by George Cukor or starring Ingrid Bergman, but those movies may not be similar to *Gaslight*. If the user rather relishes some specific plot device (for example, deceptive husband) or production element (for example, cinematographer) not represented in the item profile, the system will not present suitable recommendations. Accurate differentiation between a user’s potential likes and dislikes cannot be accomplished with insufficient data.<sup>15</sup>  

 Because content-based filtering only recommends items based on a user’s previously evidenced interests, its recommendations are often similar to items a user liked in the past. In other words, CBRSs lack a methodology for exploring the new and unpredicted. This is overspecialization. In contrast, because collaborative-based methods draw recommendations from a pool of users who have similar likes to one given user, they can often recommend items that a user may have not considered, appears with different features than a user’s previously liked items but that retain a some unrepresented element that appeals to a user type.<sup>16</sup>

## Recent research

While past studies have approached recommendation as a prediction or classification problem, a substantive body of recent research argues that it be understood as a sequential, decision-making problem. In this paradigm, reinforcement learning may be more suitable for addressing recommendation. This approach argues that recommendation be updated in real-time according to user-item interaction; as the user skips, clicks, rates, purchases suggested items, the model develops an optimal policy from this feedback in order to recommend new items.<sup>17</sup> Recent studies propose a wide variety of reinforcement learning applications to address mutable, long-term user interests, which pose challenges for both content-based and collaborative filtering.<sup>18</sup>

## Footnotes

<sup>1</sup> Melville, P. and Sindhwani, V. “Recommender Systems,” *Encyclopedia of Machine learning and Data Mining*, Springer, 2017.

<sup>2</sup> Aggarwal, C. “*Recommender Systems: The Textbook”*, Springer, 2016.

<sup>3</sup> Sarwat, M. and Mokbel, M. “Collaborative Filtering,” *Encyclopedia of Database Systems*, Springer, 2018.  
 Sarwat, M. and Mokbel, M. “Collaborative Filtering,” *Encyclopedia of Machine Learning and Data Mining*, Springer, 2017.

<sup>4, 6</sup> Pazzani, M.J. and Billsus, D. “Content-Based Recommendation Systems,” *The Adaptive Web: Methods and Strategies of Web Personalization*, Springer, 2007.

<sup>5</sup> Negre, E. “*Information and Recommender Systems”*, Vol. 4, Wiley-ISTE, 2015.

<sup>7, 11</sup> Negre, E. “*Information and Recommender Systems”*, Vol. 4, Wiley-ISTE, 2015.  
 Mohanty, S. N. et all. “*Recommender System with Machine Learning and Artificial Intelligence”*, Wiley-Scrivener, 2020.

<sup>8</sup> Banik, R. “*Hands-On Recommendation Systems with Python”*, Packt Publishing, 2018.   
 Negre, E. “*Information and Recommender Systems”*, Vol. 4, Wiley-ISTE, 2015.

<sup>9</sup> Kuhn, M. and Johnson, K. “*Applied Predictive Modeling”*, Springer, 2016.

<sup>10</sup> Mei, Q. and Radev, D. “Information Retrieval,” *Oxford Handbook of Computational Linguistics*, Second Edition, Oxford University Press, 2016.

<sup>12</sup> Aggarwal, C. “*Recommender Systems: The Textbook”*, Springer, 2016.  
 Ricci, F., Rokach, L. and Shapira, B. “*Recommender Systems Handbook”*, Third Edition, Springer 2022.

<sup>13</sup> Aggarwal, C. “Recommender Systems: The Textbook”, Springer, 2016.  
 Goodfellow, I., Bengio, Y. and Courville, A. “Deep Learning”, MIT Press, 2016.

<sup>14, 16</sup> Mohanty, S. N. et all. “Recommender System with Machine Learning and Artificial Intelligence”, Wiley-Scrivener, 2020.  
 Aggarwal, C. “Recommender Systems: The Textbook”, Springer, 2016.

<sup>15</sup> Han, J. Kamber, M. and Pei, J. “*Data Mining: Concepts and Techniques”*, Third Edition, Elsevier, 2012.  
 Mohanty, S. N. et all. “Recommender System with Machine Learning and Artificial Intelligence”, Wiley-Scrivener, 2020.

<sup>17</sup> Shani, G., Heckerman, D. and Brafman, R. I. [“An MDP-Based Recommender System”](https://www.jmlr.org/papers/v6/shani05a.html), 2005.  
 Lin, Y. et all. [“A Survey on Reinforcement Learning for Recommender Systems”](https://ieeexplore.ieee.org/abstract/document/10144689.), 2023.  
 M.M. Afsar et al. [“Reinforcement learning based recommender systems: A survey”](https://dl.acm.org/doi/abs/10.1145/3543846), ACM Computing Surveys, 2023.

<sup>18</sup> Chen, X. et all. [“Generative Adversarial User Model for Reinforcement Learning Based Recommendation System”](http://proceedings.mlr.press/v97/chen19f.html), 2019.   
 Huang, L. et all. [“A deep reinforcement learning based long-term recommender system](https://www.sciencedirect.com/science/article/abs/pii/S0950705120308352)”, 2021
