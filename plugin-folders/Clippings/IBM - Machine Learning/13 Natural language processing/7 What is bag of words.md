---
title: What is bag of words?
source: https://www.ibm.com/think/topics/bag-of-words
author:
- '[[Jacob  Murel Ph.D.]]'
- '[[Eda Kavlakoglu]]'
published: 2024-12-03
created: 2026-08-31
description: "What is bag of words? Learn how this feature extraction technique helps process raw text data for machine learning algorithms."
---

Bag of words featurization quantifies the frequency of words in text documents for processing in machine learning models. Its variation TF-IDF generates models that further account for word frequency across a corpus of documents.

Bag of words (BoW; also stylized as *bag-of-words*) is a feature extraction technique that models text data for processing in information retrieval and [machine learning](https://www.ibm.com/topics/machine-learning) algorithms. More specifically, BoW models are an unstructured assortment of all the known words in a text document defined solely according to frequency while ignoring word order and context.<sup>1</sup> Bag of words is one of several steps in many [text mining](https://www.ibm.com/topics/text-mining) pipelines.  
 [](#f01)

Most [natural language processing (NLP)](https://www.ibm.com/topics/natural-language-processing) packages come loaded with functions to create bag of words models, such as scikit-learn’s [CountVectorizer function](https://www.ibm.com/reference/python/countvectorizer).

## How bag of words models works

Bag of words featurization may, at times, be considered a beginner-level form of text processing, given its ostensible conceptual simplicity in counting words across a given text set. Bag of words models are more involved however.

Understanding bag of words featurization demands an, at least beginner, understanding of vector spaces. A vector space is a multi-dimensional space in which points are plotted. In a bag of words approach, each individual word becomes a separate dimension (or axis) of the vector space. If a text set has *n* number of words, the resulting vector space has *n* dimensions, one dimension for each unique word in the text set. The model then plots each separate text document as a point in the vector space. A point’s position along a certain dimension is determined by the number of times that dimension’s word appears within the point’s document.

For example, assume we have a text set in which the contents of two separate documents are respectively:

**Document 1:** *A rose is red, a violet is blue*

**Document 2:** *My love is like a red, red rose*

Because it is difficult to imagine anything beyond a three-dimensional space, we will limit ourselves to just that. A vector space for a corpus containing these two documents would have separate dimensions for *red*, *rose*, and *violet*. A three-dimensional vector space for these words may look like:

![Vector space with red, rose, and violet as feature-dimensions](https://assets.ibm.com/is/image/ibm/bag-of-words-figure2?ts=1763392096351&dpr=off)

Since *red*, *rose*, and *violet* all occur once in Document 1, the vector for that document in this space will be (1,1,1). In Document 2, *red* appears twice, *rose* once, and *violet* not at all. Thus, the vector point for Document 2 is (2,1,0). Both of these document-points will be mapped in the three-dimensional vector space as:

![3D vector space with two documents as points ](https://assets.ibm.com/is/image/ibm/bag-of-words-figure3?ts=1763392096496&dpr=off)

Note that this figure visualizes text documents as data vectors in a three-dimensional feature space. But bag of words can also represent words as feature vectors in a data space. A feature vector signifies the value (occurrence) of a given feature (word) in a specific data point (document). So the feature vectors for *red*, *rose*, and *violet* in Documents 1 and 2 would look like:<sup>2</sup>

![Feature vector space for red, rose, and violet in two documents](https://assets.ibm.com/is/image/ibm/bag-of-words-figure4?ts=1763392096642&dpr=off)

Note that the order of words in the original documents is irrelevant. For a bag of words model, all that matters is each word’s number of occurrences across the text set.

## Why use bag of words models

Because bag of words models only quantify the frequency of words in a given document, bag of words is often described as a simple modelling technique. But bag of words assists in many NLP tasks, most notably document classification. Indeed, literature often discusses bag of words alongside statistical classifiers like [Naïve Bayes](https://www.ibm.com/topics/naive-bayes).<sup>3</sup>

Text classification tasks interpret those words with high frequency in a document as representing the document’s main ideas.<sup>4</sup> This is not an unreasonable assumption. For example, if some of the most frequent words in a document are *president*, *voters*, and *election*, there is a high probability the document is a political text, specifically discussing a presidential election. Text classification with bag of words then extrapolates that documents with similar content are similar in type.

## Limitations of bag of words models

Although probabilistic classifiers using a bag of words approach prove largely effective, bag of words has several disadvantages.

**Word correlation.** Bag of words assumes words are independent of one another in a document or corpus. *Election* is more likely to appear in shared context with *president* then *poet*. In measuring individual term frequency, bag of words does not account for correlations in usage between words. Because bag of words extracts each word in a document as a feature of the bag of words model, with term frequency being that feature’s weight, two or more correlated words can theoretically induce [multicollinearity](https://www.ibm.com/topics/multicollinearity) in statistical classifiers using that model. Nevertheless, Naïve Bayes’ simplifying assumption has shown to produce robust models despite such potential shortcomings.<sup>5</sup>

**Compound words.** Word correlation extends to bag of words representations of compound phrases, in which two or more words operate as one semantic unit. For instance, a simple Bag of words model may represent *Mr. Darcy* as two unique and unrelated words even though they function in tandem. Such a bag of words representation fails to reflect the semantic and syntactic nature of multi-word concepts.

**Polysemous words.** Many words have multiple, markedly different meanings. For instance, *bat* can signify a sports instrument or animal, and these meanings usually occur in significantly different contexts. Similarly, words can change meaning depending on placement of its stress in spoken language—for example CON-tent versus con-TENT. Because bag of words does not regard context and meaning when modeling words, it collapses all of these distinct meanings under one word, thereby eliding potentially significant information on a text’s subject (and so potential classification).

**Sparsity.** In a bag of words model, each word is a feature, or dimension, of the model, and each so-called document is a vector. Because a document does not use every word in the generated model’s vocab, many of the feature values for a given vector may be zero. When the majority of values for vectors are zero, the model is sparse (if representing vectors as a matrix, this is called a sparse matrix). Model sparsity results in high dimensionality, which, in turn leads to [overfitting](https://www.ibm.com/topics/overfitting) on training data.<sup>6</sup>

## Modifications

**Bag of n-grams.** Adopting n-grams rather than words can correct for a number disadvantages inherent to bag of words models. Rather than creating a model where each word is a feature, one can use n-grams as vector features. In this context, *n* refers to the number of words that are treated as one semantic unit, perhaps the most common in bag of n-grams is bigrams (that is, two words). Word-bigrams are useful in that they can account for compound words, such as *New York* or *Eiffel Tower*. Of course, not all word-bigrams are informative, for example *on the* or *of the*. Nevertheless, this is one means of account for issues such as compound words and word correlation.<sup>7</sup>

**Text normalization techniques.** Raw text data may need to be normalized to improve the structure and function of bag of words models. When creating a Bag of words, or bag of n-grams, model, words like articles (for example, *a*, *the*, etc.) and prepositions (for example, *from*, *of*, *on*, etc.) may have the highest number of occurrences. These words do not provide much information on a document’s content or type, and so are largely useless in classification tasks. Text preprocessing techniques like stopword removal (often used in [stemming](https://www.ibm.com/topics/stemming)) can help remove irrelevant words from text datasets to help improve the structure of bag of words models. Fortunately, many python libraries and packages, such as NLTK or sklearn come with functions to conduct common preprocessing techniques.

**Hashing.** Feature hashing essentially converts individual words from input text data to a fixed size numerical set. This fixed range of numbers is then used to construct the vector space for the bag of words model. Limiting the range of numbers, and so model dimensions, to a fixed size helps prevent sparsity and high dimensionality. A key disadvantage of hashing is so-called collisions. A hashing collision occurs when two unrelated tokens are mapped onto the same integer. Another disadvantage with hashing is that it does not account for polysemous words.<sup>8</sup>

### TF-IDF

With standard bag of words models, semantically irrelevant words (for example, *the*, *some*, etc.) can have the highest term frequency, and so greatest weight in a model. Term frequency-inverse document frequency (TF-IDF) aims to correct for this. While bag of words counts only the number of times a word appears in one document, TF-IDF accounts for the word’s prevalence throughout every document in a text set. TF-IDF is represented in the equation:

![TF-IDF equation](https://assets.ibm.com/is/image/ibm/bag-of-words-figure1?ts=1763392097595&dpr=off)

In this equation, the first term is the value calculated by the bag of words model, that is term frequency. The second term represents inverse document frequency. *N* equals the total number of documents in the text set, and *n* equals the number of documents in which a given word appears. The more documents in which a given word appears, the greater TF-IDF reduces that word’s weight. In this way, TF-IDF is an example of feature scaling in machine learning models.<sup>9</sup>

Much like general bag of words models, NLP packages often have pre-exsiting functions for implementing TF-IDF, such as scikit-learn’s tfidfvectorizer function.

## Recent research

Variations of bag of words models are used in a variety of NLP tasks. For instance, the [neural network](https://www.ibm.com/topics/neural-networks) word2vec uses continuous bag of words to produce word embedding models.<sup>10</sup> [Sentiment analysis](https://www.ibm.com/topics/sentiment-analysis) and classification can also make use of bag of words models.<sup>11</sup>

Initial research for a large amount of NLP techniques focuses on English or other Latin script languages, such as Spanish or French. More recently, researchers have turned to other languages, such as Arabic. Recent studies have examined the efficacy of bag of words models alongside other NLP tools such as word2vec for sentiment analysis and classification of Arabic texts with promising results.<sup>12</sup> Others show the potential of Naïve Bayes classifiers based on bag of words models for word sense disambiguation of Sanskrit texts.<sup>13</sup>

Bag of words approaches have been tested in algorithms for detecting hate speech on social media platforms with varying success. One study compares bag of words with word2vec and deep learning classifiers like BERT, arguing that BERT outperforms bag of words and that TF-IDF does not significantly improve predictions from bag of words models.<sup>14</sup> By contrast, a later study presents an algorithm using bag of words and Naïve Bayes for hate speech detection with an accuracy of approximately 99%.<sup>15</sup> Differences in data size and sampling, as well as text preprocessing, may contribute to the gap in such findings. Indeed, other studies suggest comparative performance between BERT and classifiers using bag of words depends on dataset classification category sizes.<sup>16</sup>

More recently, computer vision communities have adopted their own variation of bag of words for feature extraction in image classification and retrieval tasks. This approach detects and extracts image features and clusters similar patches together as “codewords.” Many of the challenges plaguing bag of words approaches for image classification are the same as those in other computer vision tasks: for example objects with similar colors or backgrounds, occluded and overlapping objects, intra-class variation, and so on.<sup>17</sup>

## Footnotes

<sup>1</sup> Ruslan Mitkov (ed.), *Oxford Handbook of Computational Linguistics*, 2<sup>nd</sup> edition, Oxford University Press, 2014.  

 <sup>2</sup> Alice Zheng and Amanda Casari, *Feature Engineering for Machine Learning*, O’Reilly, 2018.  

 <sup>3</sup> Daniel Jurafsky and James Martin, *Speech and Language Processing: An Introduction to Natural Language Processing, Computational Linguistics, and Speech Recognition*, 3<sup>rd</sup> edition, 2023, [https://web.stanford.edu/~jurafsky/slp3](https://web.stanford.edu/~jurafsky/slp3/). Christopher Manning and Hinrich Schütze, *Foundations of Statistical Natural Language Processing*, MIT Press, 2000.  

 <sup>4</sup> Dongyang Yan, Keping Li, Shuang Gu, and Liu Yang, “Network-Based Bag-of-Words Model for Text Classification,” *IEEE Access*, Vol. 8, 2020, pp. 82641-82652, [https://ieeexplore.ieee.org/document/9079815](https://ieeexplore.ieee.org/document/9079815).  

 <sup>5</sup> Christopher Manning and Hinrich Schütze, *Foundations of Statistical Natural Language Processing*, MIT Press, 2000.  

 <sup>6</sup> Dani Yogatama, “Sparse Models of Natural Language Text,” doctoral thesis, Carnegie Mellon University, 2015, [https://lti.cmu.edu/people/alumni/alumni-thesis/yogatama-dani-thesis.pdf](https://lti.cmu.edu/people/alumni/alumni-thesis/yogatama-dani-thesis.pdf)  

 <sup>7</sup> Yoav Goldberg, *Neural Network Methods for Natural Language Processing*, Springer, 2022.  

 <sup>8</sup> Alice Zheng and Amanda Casari, *Feature Engineering for Machine Learning*, O’Reilly, 2018.  

 <sup>9</sup> Alice Zheng and Amanda Casari, *Feature Engineering for Machine Learning*, O’Reilly, 2018.  

 <sup>10</sup> Tomas Mikolov, Kai Chen, Greg Corrado, and Jeffrey Dean, “Efficient Estimation of Word Representations in Vector Space,” *Workshop Track Proceedings of 1st International Conference on Learning Representations* (ICLR), 2013, [https://arxiv.org/abs/1301.3781](https://arxiv.org/abs/1301.3781).  

 <sup>11</sup> Tan Thongtan and Tanasanee Phienthrakul, “Sentiment Classification Using Document Embeddings Trained with Cosine Similarity,” *Proceedings of the 57th Annual Meeting of the Association for Computational Linguistics: Student Research Workshop*, 2019, pp. 407-414, [https://aclanthology.org/P19-2057/](https://aclanthology.org/P19-2057/).  

 <sup>12</sup> Huda Abdulrahman Almuzaini and Aqil M. Azmi, “Impact of Stemming and Word Embedding on Deep Learning-Based Arabic Text Categorization,” *IEEE Access*, Vol. 8, 2020, pp. 127913-127928, [https://ieeexplore.ieee.org/abstract/document/9139948](https://ieeexplore.ieee.org/abstract/document/913994). Mohammed Kasri, Marouane Birjali, and Abderrahim Beni-Hssane, “A comparison of features extraction methods for Arabic sentiment analysis,” *Proceedings of the 4th International Conference on Big Data and Internet of Things* (BDIoT ‘19), 2019, [https://dl.acm.org/doi/abs/10.1145/3372938.3372998](https://dl.acm.org/doi/abs/10.1145/3372938.3372998).  

 <sup>13</sup> Archana Sachindeo Maurya, Promila Bahadur, and Srishti Garg, “Approach Toward Word Sense Disambiguation for the English-To-Sanskrit Language Using Naïve Bayesian Classification,” *Proceedings of Third Doctoral Symposium on Computational Intelligence*, 2023, pp. 477–491, [https://link.springer.com/chapter/10.1007/978-981-19-3148-2_40](https://link.springer.com/chapter/10.1007/978-981-19-3148-2_40).  

 <sup>14</sup> Joni Salminen, Maximilian Hopf, Shammur A. Chowdhury, Soon-gyo Jung, Hind Almerekhi, and Bernard J. Jansen, “Developing an online hate classifier for multiple social media platforms,” *Human-centric Computing and Information Sciences*, Vol. 10, 2020, [https://hcis-journal.springeropen.com/articles/10.1186/s13673-019-0205-6](https://hcis-journal.springeropen.com/articles/10.1186/s13673-019-0205-6).  

 <sup>15</sup> Yogesh Pandey, Monika Sharma, Mohammad Kashaf Siddiqui, and Sudeept Singh Yadav, “Hate Speech Detection Model Using Bag of Words and Naïve Bayes,” *Advances in Data and Information Sciences*, 2020, pp. 457–470, [https://link.springer.com/chapter/10.1007/978-981-16-5689-7_40](https://link.springer.com/chapter/10.1007/978-981-16-5689-7_40).  

 <sup>16</sup> Paula Fortuna, Juan Soler-Company, and Leo Wanner, “How well do hate speech, toxicity, abusive and offensive language classification models generalize across datasets?,” Information Processing and Management, Vol. 58, 2021, [https://www.sciencedirect.com/science/article/pii/S0306457321000339](https://www.sciencedirect.com/science/article/pii/S0306457321000339).  

 <sup>17</sup> Wisam A. Qader, Musa M. Ameen, and Bilal I. Ahmed, “An Overview of Bag of Words: Importance, Implementation, Applications, and Challenges,” *Proceedings of the Fifth International Engineering Conference on Developments in Civil & Computer Engineering Applications* (IEC2019), 2019, pp. 200-204, [https://ieeexplore.ieee.org/document/8950616](https://ieeexplore.ieee.org/document/8950616).
