---
title: What is feature engineering?
source: https://www.ibm.com/think/topics/feature-engineering
author:
- '[[Jacob Murel Ph.D.]]'
- '[[Eda Kavlakoglu]]'
published: 2024-12-06
created: 2026-05-21
description: "What is feature engineering? Learn the methods and processes for transforming raw data into machine-readable variables"
---

## What is feature engineering?

Feature engineering preprocesses raw data into a machine-readable format. It optimizes ML model performance by transforming and selecting relevant features.

Feature engineering is the process of transforming raw data into relevant information for use by [machine learning](https://www.ibm.com/topics/machine-learning) models. In other words, feature engineering is the process of creating predictive model features. A feature—also called a dimension—is an input variable used to generate model predictions. Because model performance largely rests on the quality of data used during training, feature engineering is a crucial preprocessing technique that requires selecting the most relevant aspects of raw training data for both the predictive task and model type under consideration.<sup>1</sup>

Before proceeding, a quick note on terminology. Many sources use *feature engineering* and *feature extraction* interchangeably to denote the processing of creating model variables.<sup>2</sup> At times, sources also use *feature extraction* to refer to remapping an original feature space onto a lower-dimensional feature space.<sup>3</sup> *Feature selection*, by contrast, is a form of [dimensionality reduction](https://www.ibm.com/topics/dimensionality-reduction). Specifically, it is the processing of selecting a subset of variables in order to create a new model with the purpose of reducing [multicollinearity](https://www.ibm.com/topics/multicollinearity), and so maximize model generalizability and optimization.

## Feature engineering process

Given a model is only as good as the data on which it is based, data scientists spend a large portion of time on data preparation and feature creation in order to create high-quality models. Depending on the complexity of one’s raw data and the desired predictive model, feature engineering can require much trial and error.

A handful of sources and online tutorials break feature engineering down into discrete steps, the number and names of which typically vary. These steps can include feature understanding, structuring or construction, transformation, evaluation, optimization and the list goes on.<sup>4</sup> While such stratification can be useful for providing a general overview of the tasks involved in featuring engineering, it suggests that feature engineering is a linear process. In actual fact, feature engineering is an iterative process.

Feature engineering is context-dependent. It requires substantial data analysis and domain knowledge. This is because effective encoding for features can be determined by the type of model used, the relationship between predictors and output, as well as the problem a model is intended to address.<sup>5</sup> This is coupled by the fact that different kinds of datasets—for example text versus images—may be better suited for different feature engineering techniques.<sup>6</sup> Thus, it can be difficult to make specific remarks on how to best implement feature engineering within a given machine learning algorithms.

## Feature engineering techniques

Although there is no universally preferred feature engineering method or pipeline, there are a handful of common tasks used to create features from different data types for different models. Before implementing any of these techniques, however, one must remember to conduct a thorough data analysis to determine both the relevant features and appropriate number of features for addressing a given problem. Additionally, it is best to implement various data cleaning and preprocessing techniques, such as imputation for missing data or missing values, while also addressing outliers that can negatively impact model predictions.

### Feature transformation

Feature transformation is the process of converting one feature type into another, more readable form for a particular model. This consists of transforming continuous into categorical data, or vice-versa.

**Binning.** This technique essentially transforms continuous, numerical values into categorical features. Specifically, binning compares each value to the neighborhood of values surrounding it and then sorts data points into a number of bins. A rudimentary example of binning is age demographics, in which continuous ages are divided into age groups, for example 18-25, 25-30, and so on. Once values have been placed into bins, one can further smooth the bins by means, medians or boundaries. Smoothing bins replaces a bin’s contained values with bin-derived values. For instance, if we smooth a bin containing age values between 18-25 by the mean, we replace each value in that bin with the mean of that bin’s values. Binning creates categorical values from continuous ones. Smoothing bins is a form of local smoothing meant to reduce noise in input data.<sup>7</sup>

**One-hot encoding.** This is the inverse of binning; it creates numerical features from categorical variables. One-hot encoding maps categorical features to binary representations, which are used to map the feature in a matrix or vector space. Literature often refers to this binary representation as a *dummy variable*. Because one-hot encoding ignores order, it is best used for nominal categories. [Bag of words models](https://www.ibm.com/topics/bag-of-words) are an example of one-hot encoding frequently used in [natural language processing](https://www.ibm.com/topics/natural-language-processing) tasks. Another example of one-hot encoding is [spam filtering classification](https://developer.ibm.com/tutorials/awb-classifying-data-multinomial-naive-bayes-algorithm/) in which the categories *spam* and *not spam* are converted to 1 and 0 respectively.<sup>8</sup>

![Table illustrating one-hot encoding for spam classification](https://assets.ibm.com/is/image/ibm/screen3?ts=1763386614733&dpr=off)

### Feature extraction and selection

Feature extraction is a technique for creating a new dimensional space for a model by combining variables into new, surrogate variables or in order to reduce dimensions of the model’s feature space.<sup>9</sup> By comparison, feature selection denotes techniques for selecting a subset of the most relevant features to represent a model. Both feature extraction and selection are forms of dimensionality reduction, and so suitable for regression problems with a large number of features and limited available data samples.

**Principal component analysis.** [Principal component analysis](https://www.ibm.com/topics/principal-component-analysis) (PCA) is a common feature extraction method that combines and transforms a dataset’s original features to produce new features, called *principal components*. PCA selects a subset of variables from a model that together comprise the majority or all of the variance present in the model’s original set of variables. PCA then projects data onto a new space defined by this subset of variables.<sup>10</sup>

**Linear discriminant analysis.** [Linear discriminant analysis](https://www.ibm.com/topics/linear-discriminant-analysis) (LDA) is ostensibly similar to PCA in that it projects model data onto a new, lower dimensional space. As in PCA, this model space’s dimensions (or features) are derived from the initial model’s features. LDA differs from PCA, however, in its concern for retaining classification labels in the original dataset. While PCA produces new component variables meant to maximize data variance, LDA produces component variables primarily intended to maximize class difference in the data.<sup>11</sup>

### Feature scaling

Certain features have upper and lower bounds intrinsic to data that limits possible feature values, such as time-series data or age. But in many cases, model features may not have a limitation on possible values, and such large feature scales (being the difference between a features lowest and highest values) can negatively affect certain models. Feature scaling (sometimes called *feature normalization*) is a standardization technique to rescale features and limit the impact of large scales on models.<sup>12</sup> While feature transformation transforms data from one type to another, feature scaling transforms data in terms of range and distribution, maintaining its original data type.<sup>13</sup>

**Min-max scaling.** Min-max scaling rescales all values for a given feature so that they fall between specified minimum and maximum values, often 0 and 1. Each data point’s value for the selected feature (represented by *x*) is computed against the decided minimum and maximum feature values, *min(x)* and *max(x)* respectively, which produces the new feature value for that data point (represented by *x̃* ). Min-max scaling is calculated using the formula:<sup>14</sup>

![Min-max equation](https://assets.ibm.com/is/image/ibm/screen2?ts=1763386615128&dpr=off)

**Z-score scaling.** Literature also refers to this as *standardization* and *variance scaling*. Whereas min-max scaling scales feature values to fit within designated minimum and maximum values, z-score scaling rescales features so that they have a shared standard deviation of 1 with a mean of 0. Z-score scaling is represented by the formula:

![Z-score equation](https://assets.ibm.com/is/image/ibm/screen1?ts=1763386615275&dpr=off)

Here, a given feature value (*x*) is computed against the rescaled feature’s mean and divided by the standardized standard deviation (represented as *sqrt(var(x))*). Z-score scaling can be useful when implementing feature extraction methods like PCA and LDA, as these two methods require features to share the same scale.<sup>15</sup>

## Recent research

**Automation.** Automated feature engineering, admittedly, has been an ongoing area of research for a few decades.<sup>16</sup> Python libraries such as "tsflex" and "featuretools" help automate feature extraction and transformation for time series data. Developers continue to provide new packages and algorithms to automate feature engineering for linear regression models and other data types that increase model accuracy.<sup>17</sup> More recently, automated feature engineering has figured as one part of larger endeavors to build [automated machine learning](https://www.ibm.com/topics/automl) (AutoML) systems, which aim to make machine learning more accessible to non-experts.<sup>18</sup>

**Deep learning.** Feature engineering can be a laborious and time-consuming process, involving a significant amount of trial and error. [Deep learning](https://www.ibm.com/topics/deep-learning) allows the user to specify a small set of basic features that the neural network architecture aggregates into higher-level features, also called *representations*.<sup>19</sup> One such example is [computer vision](https://www.ibm.com/topics/computer-vision) image processing and pattern recognition, in which a model learns to [identify semantically meaningful objects](https://www.ibm.com/topics/object-detection) (for example cars, people, and so on) in terms of simple concepts (for example edges, contours, and so on) by concatenating feature maps.<sup>20</sup> Recent studies, however, have combined feature engineering with [neural networks](https://www.ibm.com/topics/neural-networks) and other deep learning techniques classification tasks, such as fraud detection, with promising results.<sup>21</sup>

## Footnotes

<sup>1</sup> Alice Zheng and Amanda Casari. *Feature Engineering for Machine Learning* [Feature engineering for machine learning]. O’Reilly. 2018. Sinan Ozdemir and Divya Susarla. *Feature Engineering Made Easy* [Feature engineering made easy]. Packt. 2018.

<sup>2</sup> Yoav Goldberg. *Neural Network Methods for Natural Language Processing* [Neural network methods for natural language processing]. Springer. 2022.

<sup>3</sup> Suhang Wang, Jiliang Tang, and Huan Liu. “Feature Selection” [Feature selection]. *Encyclopedia of Machine Learning and Data Mining*. Springer. 2017.

<sup>4</sup> Sinan Ozdemir. *Feature Engineering Bookcamp* [Feature engineering bootcamp]. Manning Publications. 2022. Sinan Ozdemir and Divya Susarla. *Feature Engineering Made Easy* [Feature engineering made easy]. Packt. 2018.

<sup>5</sup> Max Kuhn and Kjell Johnson. *Applied Predictive Modeling* [Applied predictive modeling]. Springer. 2016.

<sup>6</sup> Alice Zheng and Amanda Casari. *Feature Engineering for Machine Learning* [Feature engineering for machine learning]. O’Reilly. 2018.

<sup>7</sup> Jiawei Han. *Data Mining: Concepts and Techniques* [Data mining: concepts and techniques]. 3rd edition. 2012.

<sup>8</sup> Kevin Murphy. *Machine Learning: A Probabilistic Perspective* [Machine learning: a probabilistic perspective]. MIT Press. 2012. Soledad Galli. *Python Feature Engineering Cookbook* [Python feature engineering cookbook]. 2nd edition. Packt. 2022.

<sup>9</sup> Max Kuhn and Kjell Johnson. *Applied Predictive Modeling* [Applied predictive modeling]. Springer. 2016.

<sup>10</sup> I.T. Jolliffe. *Principal Component Analysis* [Principal component analysis]. Springer. 2002.

<sup>11</sup> Chris Albon. *Machine Learning with Python Cookbook* [Machine learning with Python cookbook]. O’Reilly. 2018.

<sup>12</sup> Alice Zheng and Amanda Casari. *Feature Engineering for Machine Learning* [Feature engineering for machine learning]. O’Reilly. 2018.

<sup>13</sup> Zahraa Abdallah, Lan Du, and Geoffrey Webb. “Data preparation” [Data preparation]. *Encyclopedia of Machine Learning and Data Mining*. Springer. 2017.

<sup>14</sup> Alice Zheng and Amanda Casari. *Feature Engineering for Machine Learning* [Feature engineering for machine learning]. O’Reilly. 2018.

<sup>15</sup> Zahraa Abdallah, Lan Du, and Geoffrey Webb. “Data preparation” [Data preparation]. *Encyclopedia of Machine Learning and Data Mining*. Springer. 2017. Alice Zheng and Amanda Casari. *Feature Engineering for Machine Learning* [Feature engineering for machine learning]. O’Reilly. 2018.

<sup>16</sup> James Kanter and Kalyan Veeramachaneni. “Deep feature synthesis: Towards automating data science endeavors” [Deep feature synthesis: toward automating data-science work]. *IEEE International Conference on Data Science and Advanced Analytics*. 2015. [https://ieeexplore.ieee.org/document/7344858](https://ieeexplore.ieee.org/document/7344858).

<sup>17</sup> Udayan Khurana, Deepak Turaga, Horst Samulowitz, and Srinivasan Parthasrathy. “Cognito: Automated Feature Engineering for Supervised Learning” [Cognito: automated feature engineering for supervised learning]. *IEEE 16th International Conference on Data Mining Workshops*. 2016. pp. 1304–130. [https://ieeexplore.ieee.org/abstract/document/7836821](https://ieeexplore.ieee.org/abstract/document/7836821). Franziska Horn, Robert Pack, and Michael Rieger. “The autofeat Python Library for Automated Feature Engineering and Selection” [The autofeat Python library for automated feature engineering and selection]. *Joint European Conference on Machine Learning and Knowledge Discovery in Databases*. 2019. pp. 111–120. [https://link.springer.com/chapter/10.1007/978-3-030-43823-4_10](https://link.springer.com/chapter/10.1007/978-3-030-43823-4_10).

<sup>18</sup> Ahmad Alsharef, Karan Aggarwal, Sonia, Manoj Kumar, and Ashutosh Mishra. “Review of ML and AutoML Solutions to Forecast Time-Series Data” [Review of ML and AutoML solutions for forecasting time-series data]. *Archives of Computational Methods in Engineering*. Vol. 29. 2022. pp. 5297–5311. [https://link.springer.com/article/10.1007/s11831-022-09765-0](https://link.springer.com/article/10.1007/s11831-022-09765-0). Sjoerd Boeschoten, Cagatay Catal, Bedir Tekinerdogan, Arjen Lommen, and Marco Blokland. “The automation of the development of classification models and improvement of model quality using feature engineering techniques” [Automation of classification-model development and quality improvement using feature-engineering techniques]. *Expert Systems with Applications*. Vol. 213. 2023. [https://www.sciencedirect.com/science/article/pii/S0957417422019303](https://www.sciencedirect.com/science/article/pii/S0957417422019303). Shubhra Kanti Karmaker, Mahadi Hassan, Micah Smith, Lei Xu, Chengxiang Zhai, and Kalyan Veeramachaneni. “AutoML to Date and Beyond: Challenges and Opportunities” [AutoML to date and beyond: challenges and opportunities]. *ACM Computing Surveys*. Vol. 54. No. 8. 2022. pp. 1-36. [https://dl.acm.org/doi/abs/10.1145/3470918](https://dl.acm.org/doi/abs/10.1145/3470918).

<sup>19</sup> Yoav Goldberg. *Neural Network Methods for Natural Language Processing* [Neural network methods for natural language processing]. Springer. 2022.

<sup>20</sup> Ian Goodfellow, Yoshua Bengio, and Aaron Courville. *Deep Learning*. MIT Press. 2016. [https://www.deeplearningbook.org/](https://www.deeplearningbook.org/).

<sup>21</sup> Xinwei Zhang, Yaoci Han, Wei Xu, and Qili Wang. “HOBA: A novel feature engineering methodology for credit card fraud detection with a deep learning architecture” [HOBA: a novel feature-engineering methodology for credit-card fraud detection using a deep-learning architecture]. *Information Sciences*. Vol. 557. 2021. pp. 302–316. [https://www.sciencedirect.com/science/article/abs/pii/S002002551930427X](https://www.sciencedirect.com/science/article/abs/pii/S002002551930427X). Daniel Gibert, Jordi Planes, Carles Mateu, and Quan Le. “Fusing feature engineering and deep learning: A case study for malware classification” [Fusing feature engineering and deep learning: a case study for malware classification]. *Expert Systems with Applications*. Vol. 207. 2022. [https://www.sciencedirect.com/science/article/pii/S0957417422011927](https://www.sciencedirect.com/science/article/pii/S0957417422011927). Ebenezerm Esenogho, Ibomoiye Domor Mienye, Theo Swart, Kehinde Aruleba, and George Obaido. “A Neural Network Ensemble With Feature Engineering for Improved Credit Card Fraud Detection” [A neural-network ensemble with feature engineering for improved credit-card fraud detection]. *IEEE Access*. Vol. 10. 2020. pp. 16400–16407. [https://ieeexplore.ieee.org/abstract/document/9698195](https://ieeexplore.ieee.org/abstract/document/9698195).
