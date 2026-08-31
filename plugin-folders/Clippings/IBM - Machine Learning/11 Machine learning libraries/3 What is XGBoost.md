---
title: What is XGBoost?
source: https://www.ibm.com/think/topics/xgboost
author:
- '[[Eda Kavlakoglu]]'
- '[[Erika Russi]]'
published: 2024-12-03
created: 2026-08-31
description: "XGBoost (eXtreme Gradient Boosting) is an open-source machine learning library that uses gradient boosted decision trees, a supervised learning algorithm that uses gradient descent."
---

## What is XGBoost?

XGBoost (eXtreme Gradient Boosting) is a distributed, open-source [machine learning library](https://www.ibm.com/think/topics/machine-learning-libraries) that uses gradient boosted [decision trees](https://www.ibm.com/think/topics/decision-trees), a supervised learning [boosting](https://www.ibm.com/think/topics/boosting) algorithm that makes use of [gradient descent](https://www.ibm.com/think/topics/gradient-descent). It is known for its speed, efficiency and ability to scale well with large datasets.

Developed by Tianqi Chen from the University of Washington, XGBoost is an advanced implementation of gradient boosting with the same general framework; that is, it combines weak learner trees into strong learners by adding up residuals. The library is available for C++, Python, R, Java, Scala and Julia.<sup>1</sup>

### Decision trees vs. boosting

[Decision trees](https://www.ibm.com/topics/decision-trees) are used for [classification](https://www.ibm.com/think/topics/classification-machine-learning) or [regression](https://www.ibm.com/think/topics/logistic-regression) tasks in [machine learning](https://www.ibm.com/think/topics/machine-learning). They use a hierarchical tree structure where an internal node represents a feature, the branch represents a decision rule­ and each leaf node represents the outcome of the dataset.

Because decision trees are prone to [overfitting,](https://www.ibm.com/topics/overfitting) ensemble methods, like boosting, can often be used to create more robust models. [Boosting](https://www.ibm.com/topics/boosting) combines multiple individual weak trees—that is, models that perform slightly better than random chance, to form a strong learner. Each weak learner is trained sequentially to correct the errors made by the previous models. After hundreds of iterations, weak learners are converted into strong learners.

[Random forests](https://www.ibm.com/topics/random-forest) and boosting algorithms are both popular ensemble learning techniques that use individual learner trees to improve predictive performance. Random forests are based on the concept of bagging (bootstrap aggregating) and train each tree independently to combine their predictions, while boosting algorithms use an additive approach where weak learners are sequentially trained to correct the previous models’ mistakes.

![Boosting - sequential ensemble learning](https://assets.ibm.com/is/image/ibm/6-1_sequential-ensemble-learning_boosting?ts=1763387076770&dpr=off)

### Gradient boosted decision trees

Gradient boosted decision trees are a type of boosting algorithm that uses [gradient descent](https://www.ibm.com/topics/gradient-descent). Like other boosting methodologies, gradient boosting starts with a weak learner to make predictions. The first decision tree in gradient boosting is called the base learner. Next, new trees are created in an additive manner based on the base learner’s mistakes. The algorithm then calculates the residuals of each tree’s predictions to determine how far off the model’s predictions were from reality. Residuals are the difference between the model’s predicted and actual values. The residuals are then aggregated to score the model with a loss function.

In machine learning, [loss functions](https://www.ibm.com/think/topics/loss-function) are used to measure a model’s performance. The gradient in gradient boosted decision trees refers to gradient descent. Gradient descent is used to minimize the loss (i.e. to improve the model’s performance) when we train new models. Gradient descent is a popular optimization algorithm used to minimize the loss function in machine learning problems. Some examples of loss functions include mean squared error or mean absolute error for regression problems, cross-entropy loss for classification problems or custom loss functions may be developed for a specific use case and dataset.

## Features of XGBoost

Below is a discussion of some of XGBoost’s features in Python that make it stand out compared to the normal gradient boosting package in scikit-learn<sup>2</sup>:

- **Parallel and distributed computing:** The library stores data in in-memory units called blocks. Separate blocks can be distributed across machines or stored on external memory using out-of-core computing. XGBoost also allows for more advanced use cases, such as distributed training across a cluster of computers to speed up computation. XGBoost can also be implemented in its distributed mode using tools like Apache Spark, Dask or Kubernetes.”
- **Cache-aware prefetching algorithm:** XGBoost uses a cache-aware prefetching algorithm which helps reduce the runtime for large datasets. The library can run more than ten times faster than other existing frameworks on a single machine. Due to its impressive speed, XGBoost can process billions of examples using fewer resources, making it a scalable tree boosting system.
- **Built in regularization:** XGBoost includes [regularization](https://www.ibm.com/topics/regularization) as part of the learning objective, unlike regular gradient boosting. Data may also be regularized through hyperparameter tuning. Using XGBoost’s built in regularization also allows the library to give better results than the regular scikit-learn gradient boosting package.
- **Handling missing values:** XGBoost uses a sparsity-aware algorithm for sparse data. When a value is missing in the dataset, the data point is classified into the default direction and the algorithm learns the best direction to handle missing values.

## How XGBoost works

In this section, we will go over how to use the XGBoost package, how to select hyperparameters for the XGBoost tree booster, how XGBoost compares to other boosting implementations and some of its use cases.

### Splitting your data and converting to DMatrix format

Assuming you’ve already performed an [exploratory data analysis](https://www.ibm.com/topics/exploratory-data-analysis) on your data, continue with splitting your data between a training dataset and testing dataset. Next, convert your data into the DMatrix format that XGBoost expects<sup>3</sup>. DMatrix is XGBoost's internal data structure optimized for memory efficiency and training speed<sup>4</sup>**.**

### Generate and evaluate the model

Next, instantiate an XGBoost model and, depending on your use case, select which objective function you’d like to use via the “object” hyperparameter. For example, if you have a multi-class classification task, you should set the objective to “multi:softmax”<sup>5</sup>. Alternatively, if you have a binary classification problem, you can use the [logistic regression](https://www.ibm.com/topics/logistic-regression) objective “binary:logistic”. Now you can use your training set to train the model and predict classifications for the data set aside as the test set. Assess the performance of the model by comparing the predicted values with the test set’s actual values. You may use metrics such as accuracy, precision, recall or f-1 score to evaluate your model. You may also want to visualize your true positives, true negatives, false positives and false negatives using a [confusion matrix](https://www.ibm.com/topics/confusion-matrix).

### Hyperparameter tuning

Next, you may want to iterate through a combination of hyperparameters to help improve the performance of your model. Hyperparameter tuning is the optimization process for a machine learning algorithm’s hyperparameters. The best hyperparameters can be found using grid search and cross-validation methods, which will iterate through a dictionary of possible [hyperparameter tuning](https://www.ibm.com/think/topics/hyperparameter-tuning) options.

### Selected hyperparameters for gradient boosted trees in XGBoost

Below is an explanation of some of the hyperparameters available to tune for gradient boosted trees in XGBoost:

- **[Learning rate](https://www.ibm.com/think/topics/learning-rate)** (also known as the “step size” or the “shrinkage”), is the most important gradient boosting hyperparameter. In the XGBoost library, it is known as “eta”, should be a number between 0 and 1 and the default is 0.3<sup>6</sup>. The learning rate determines the rate at which the boosting algorithm learns from each iteration. A lower value of eta means slower learning, as it scales down the contribution of each tree in the ensemble, thus helping to prevent overfitting. Conversely, a higher value of eta speeds up learning, but it may lead to overfitting if not carefully tuned.
- The **n_estimators** hyperparameter specifies the number of trees to be built in the ensemble. Each boosting round adds a new tree to the ensemble and the model slowly learns to correct the errors made by the previous trees. N_estimators directs the complexity of the model and influences both the training time and the model’s ability to generalize to unseen data. Increasing the value of n_estimators typically increases the complexity of the model, as it allows the model to capture more intricate patterns in the data. However, adding too many trees can lead to overfitting. Generally speaking, as n_estimators goes up, the learning rate should go down.
- **Gamma** (also known as Lagrange multiplier or the minimum loss reduction parameter) controls the minimum amount of loss reduction required to make a further split on a leaf node of the tree. A lower value means XGBoost stops earlier but may not find the best solution; while a higher value means XGBoost continues training longer, potentially finding better solutions, but with greater risk of overfitting. There is no upper limit for the gamma. The default in XGBoost is 0 and anything over 10 is considered high.
- **Max_depth** represents how deeply each tree in the boosting process can grow during training. A tree’s depth refers to the number of levels or splits it has from the root node to the leaf nodes. Increasing this value will make the model more complex and more likely to overfit. In XGBoost, the default max_depth is 6, which means that each tree in the model is allowed to grow to a maximum depth of 6 levels.

## Comparing XGBoost to other boosting algorithms

XGBoost is one of many available open-source boosting algorithms. In this section, we’ll compare XGBoost to three other boosting frameworks.

### XGBoost vs. AdaBoost

AdaBoost is an early boosting algorithm invented by Yoav Freund and Robert Schapire in 1995<sup>7</sup>. In AdaBoost, more emphasis is made on incorrect predictions through a system of weights that affect those harder to predict data points more significantly. First, each data point in the dataset is assigned a specific weight. As the weak learners correctly predict an example, the example’s weight is reduced. But if learners get an example wrong, the weight for that data point increases. As new trees are created, their weights are based on the misclassifications of the previous learner trees. As the number of learners increases, the samples that are easy to predict will be used less for future learners while those data points that are harder to predict will be weighted more prominently. Gradient boosting and XGBoost tend to be stronger alternatives to AdaBoost due to their accuracy and speed.

### XGBoost vs. CatBoost

CatBoost is another gradient boosting framework. Developed by Yandex in 2017, it specializes in handling categorical features without any need for preprocessing and generally performs well out-of-the-box without the need to perform extensive hyperparameter tuning<sup>8</sup>. Like XGBoost, CatBoost has built in support for handling missing data. CatBoost is especially useful for datasets with many categorical features. According to Yandex, the framework is used for search, recommendation systems, personal assistants, self-driving cars, weather prediction and other tasks.

### XGBoost vs. LightGBM

LightGBM (Light Gradient Boosting Machine) is the final gradient boosting algorithm we will review. LightGBM was developed by Microsoft and first released in 2016<sup>9</sup>. Where most decision tree learning algorithms grow trees depth-wise, LightGBM uses a leaf-wise tree growth strategy<sup>10</sup>. Like XGBoost, LightGBM exhibits fast model training speed and accuracy and performs well with large datasets.

### Applications of XGBoost

XGBoost and gradient boosted decision trees are used across a variety of data science applications, including:

- **Learning to rank:** One of the most popular use cases for the XGBoost algorithm is as a ranker. In information retrieval, the goal of learning to rank is to serve users content ordered by relevance. In XGBoost, the XGBRanker is based on the LambdaMART algorithm<sup>11</sup>.
- **Advertisement click through rate prediction:** Researchers used an XGBoost trained model to determine how frequently online ads had been clicked in 10 days of click through data. The goal of the research was to measure the effectiveness of online ads and pinpoint which ads work well<sup>12</sup>.
- **Store sales prediction:** XGBoost may be used for predictive modeling, as demonstrated in this paper where sales from 45 Walmart stores were predicted using an XGBoost model<sup>13</sup>.
- **Malware classification:** Using an XGBoost classifier, engineers at the Technical University of Košice were able to classify malware accurately, as shown in their paper<sup>14</sup>.
- **Kaggle competitions:** XGBoost has been a popular winning algorithm in Kaggle competitions, as noted on the DMLC [Distributed (Deep) Machine Learning Community] page featuring a list of recent Kaggle competition winners who used XGBoost for their entries<sup>15</sup>.

## Footnotes

<sup>1</sup> “Scalable and Flexible Gradient Boosting”. [https://xgboost.ai/](https://xgboost.ai/).

<sup>2</sup> Tianqi Chen and Carlos Guestrin. “XGBoost: A Scalable Tree Boosting System”. University of Washington. June 10, 2016. [https://arxiv.org/pdf/1603.02754](https://arxiv.org/pdf/1603.02754).

<sup>3</sup> “XGBoost Python Package Introduction, Data Interface”. [https://xgboost.readthedocs.io/en/stable/python/python_intro.html#data-interface](https://xgboost.readthedocs.io/en/stable/python/python_intro.html#data-interface).

<sup>4</sup> “XGBoost API Reference, Core Data Structure”. [https://xgboost.readthedocs.io/en/stable/python/python_api.html#module-xgboost.core](https://xgboost.readthedocs.io/en/stable/python/python_api.html#module-xgboost.core).

<sup>5</sup> “XGBoost Parameters, Learning Task Parameters”. [https://xgboost.readthedocs.io/en/stable/parameter.html#learning-task-parameters](https://xgboost.readthedocs.io/en/stable/parameter.html#learning-task-parameters).

<sup>6</sup> “XGBoost Parameters for Tree Booster”. [https://xgboost.readthedocs.io/en/stable/parameter.html#parameters-for-tree-booster](https://xgboost.readthedocs.io/en/stable/parameter.html#parameters-for-tree-booster).

<sup>7</sup> Yoav Freund and Robert E. Schapire. “A Decision-Theoretic Generalization of On-line Learning and an Application to Boosting”. *Journal of Computer and System Sciences*. Vol. 55. pp. 119–139. August 1997.

<sup>8</sup> “CatBoost is a high-performance open source library for gradient boosting on decision trees”. [https://catboost.ai/](https://catboost.ai/).

<sup>9</sup> Qi Meng, Guolin Ke, Taifeng Wang, Wei Chen, Qiwei Ye, Zhi-Ming Ma, and Tie-Yan Liu. “A Communication-Efficient Parallel Algorithm for Decision Tree”. Peking University, Microsoft Research, and the Chinese Academy of Mathematics and Systems Science. November 4, 2016. [https://arxiv.org/pdf/1611.01276](https://arxiv.org/pdf/1611.01276).

<sup>10</sup> “LightGBM Features, Leaf-wise (Best-first) Tree Growth”. [https://lightgbm.readthedocs.io/en/latest/Features.html#leaf-wise-best-first-tree-growth](https://lightgbm.readthedocs.io/en/latest/Features.html#leaf-wise-best-first-tree-growth).

<sup>11</sup> “XGBoost Tutorials, Learning to Rank Overview”. [https://xgboost.readthedocs.io/en/latest/tutorials/learning_to_rank.html#overview](https://xgboost.readthedocs.io/en/latest/tutorials/learning_to_rank.html#overview).

<sup>12</sup> AlAli Moneera, AlQahtani Maram, AlJuried Azizah, Taghareed AlOnizan, Dalia Alboqaytah, Nida Aslam, and Irfan Ullah Khan. “Click-through Rate Effectiveness Prediction on Mobile Ads Using Extreme Gradient Boosting”. College of Computer Science and Information Technology, Imam Abdulrahman bin Faisal University. September 12, 2020. [https://www.techscience.com/cmc/v66n2/40673/html](https://www.techscience.com/cmc/v66n2/40673/html).

<sup>13</sup> Yetunde Faith Akande, Joyce Idowu, Abhavya Gautam, Sanjay Misra, Oluwatobi Noah Akande, and Ranjan Kumar Behera. “Application of XGBoost Algorithm for Sales Forecasting Using Walmart Dataset”. Landmark University, Ladoke Akintola University of Technology, Brandan University, Covenant University, and XIM University. June 2022. [https://www.researchgate.net/publication/361549465_Application_of_XGBoost_Algorithm_for_Sales_Forecasting_Using_Walmart_Dataset](https://www.researchgate.net/publication/361549465_Application_of_XGBoost_Algorithm_for_Sales_Forecasting_Using_Walmart_Dataset).

<sup>14</sup> Jakub Palša, Norbert Ádám, Ján Hurtuk, Eva Chovancová, Branislav Madoš, Martin Chovanec, and Stanislav Kocan. “MLMD—A Malware-Detecting Antivirus Tool Based on the XGBoost Machine Learning Algorithm”. *Applied Sciences* (MDPI). Vol. 12, 6672. July 1, 2022. [https://www.mdpi.com/2076-3417/12/13/6672](https://www.mdpi.com/2076-3417/12/13/6672).

<sup>15</sup> “Distributed (Deep) Machine Learning Community XGBoost Machine Learning Challenge Winning Solutions”. [https://github.com/dmlc/xgboost/tree/master/demo#machine-learning-challenge-winning-solutions](https://github.com/dmlc/xgboost/tree/master/demo#machine-learning-challenge-winning-solutions).
