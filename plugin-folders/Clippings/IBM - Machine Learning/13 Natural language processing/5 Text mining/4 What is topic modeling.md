---
title: What is topic modeling?
source: https://www.ibm.com/think/topics/topic-modeling
author:
- '[[Jacob  Murel Ph.D.]]'
- '[[Eda Kavlakoglu]]'
published: 2024-11-27
created: 2026-08-31
description: "Topic models are an unsupervised NLP method for summarizing text data through word groups. They assist in text classification and information retrieval tasks."
---

## What is topic modeling?

In [natural language processing](https://www.ibm.com/topics/natural-language-processing) (NLP), topic modeling is a [text mining](https://www.ibm.com/topics/text-mining) technique that applies [unsupervised learning](https://www.ibm.com/topics/unsupervised-learning) on large sets of texts to produce a summary set of terms that represent the collection’s overall primary set of topics.<sup>1 </sup>Topic models assist in text classification and information retrieval tasks.

Topic models specifically identify common keywords or phrases in a text dataset and group those words under a number of topics. They aim to uncover the latent topics or themes characterizing a set of documents. In this way, topic models are a machine learning-based form of text analysis used to thematically annotate large text corpora.<sup>2</sup>

Users can readily generate topic models using scikit-learn’s [Natural Language Toolkit (NLTK)](https://www.nltk.org/) and gensim in Python.

## How topic modeling works

As an unsupervised learning method, topic models do not require user-generated labels of training data, as in [supervised](https://www.ibm.com/topics/supervised-learning) text classification tasks. Rather, topic models generate, and by extension annotate, large collections of document with thematic information in the form of word groups known as topics.<sup>3</sup> But how do topic models produce these groups of words?

Topic modeling essentially treats each individual document in a collection of texts as a [bag of words](https://www.ibm.com/topics/bag-of-words) model. This means that the topic modeling algorithm ignores word order and context, simply focusing on how often words occur, and how often they co-occur, within each individual document.<sup>4</sup>

Most topic modeling approaches begin by generating a document-term matrix. This matrix models the text dataset with documents as rows and individual words as columns, or vice-versa. Values in the matrix indicate the frequency with which a given word appears in each document. This matrix can then be used to generate a vector space, where *n* words equals *n* dimensions. A given row’s value indicates that document’s position in the vector space. Documents that use words in similar groups and with comparable frequency will thus reside closer together in vector space. From here, topic models treat proximity in vector space as documents sharing similar conceptual content or topics.<sup>5</sup>

Topic models are not synonymous with bag of words however. While the latter merely counts the presence of words within a collection of documents, topic models group commonly co-occurring words into sets of topics. Each topic is modeled as a probability distribution across a vocabulary of words. Each document in the collection is then represented in terms of those topics.<sup>6</sup> In this way, topic models essentially attempt to reverse engineer the discourses (that is, topics) that produced the documents in question.<sup>7</sup>

## Types of topic modeling algorithms

Topic modeling algorithms are not so much alternative methods to one task as they are sequential developments meant to resolve issues initially found in bag of words models. Term frequency-inverse document frequency (TF-IDF) is a modification of bag of words intended to address the issues resulting from common yet semantically irrelevant words by accounting for each word’s prevalence throughout every document in a text set. Latent semantic analysis builds on TF-IDF with the principal intent of addressing polysemy and synonymy. This gave birth to probabilistic latent semantic analysis, from which grew latent Dirichlet allocation. This latter’s distinguishing characteristic is that all documents in a collection share the same set of topics, albeit in different proportions.<sup>8</sup>

### Latent semantic analysis

Latent semantic analysis (LSA) (also called latent semantic indexing) deploys a technique known as singular value decomposition in order to reduce sparsity in the document-term matrix. This alleviates problems resulting from polysemy and synonymy—that is, single words with multiple meanings or multiple words with a single shared meaning.

Data sparsity essentially denotes when a majority of data values in a given dataset are null (that is, empty). This happens regularly when constructing document-term matrices, for which each individual word is a separate row and vector space dimension, as documents will regularly lack a majority of the words that may be more frequent in other documents. Of course, text data preprocessing techniques, such as stopword removal or [stemming](https://www.ibm.com/topics/stemming) and [lemmatization](https://www.ibm.com/topics/stemming-lemmatization), can help reduce the size of the matrix. LSA offers a more targeted approach for [reducing sparsity and dimensionality](https://www.ibm.com/topics/dimensionality-reduction).

LSA begins with the document-term matrix, which displays the number of times each word appears in each document. From here, LSA produces a document-document matrix and term-term matrix. If the document-term matrix dimensions are defined as *d* documents times *w* words, then the document-document matrix is *d* times *d* and the term-term matrix *w* times *w*. Each value in the document-document matrix indicates the number of words each document has in common. Each value in the term-term matrix indicates the number of documents in which two term co-occur.<sup>9</sup>

Using these two additional matrices, the LSA algorithm conducts singular value decomposition on the initial document-term matrix, producing new special matrices of eigenvectors. These special matrices breakdown the original document-term relationships into linearly independent factors. Because many of these factors are near-zero, they are treated as zero and thrown out of the matrices. This reduces the model’s dimensions.<sup>10</sup>

Once model dimensions have been reduced through singular value decomposition, the LSA algorithm compares documents in the lower dimensional space using cosine similarity. Cosine similarity signifies the measurement of the angle between two vectors in vector space. It may be any value between -1 and 1. The higher the cosine score, the more alike two documents are considered. Cosine similarity is represented by this formula, where *x* and *y* signify two item-vectors in the vector space:<sup>11</sup>

![Illustration of the cosine similarity formula](https://assets.ibm.com/is/image/ibm/cosine-collaborative-filtering?ts=1763391986450&dpr=off)

### Latent Dirichlet allocation

Latent Dirichlet allocation (LDA) — not to be confused with [linear discriminant analysis](https://www.ibm.com/topics/linear-discriminant-analysis) — is a probabilistic topic modeling algorithm. This means it generates topics, classifying words and documents among these topics, according to probability distributions. Using the document-term matrix, the LDA algorithm generates topic distributions (that is, lists of keywords with respective probabilities) according to word frequency and co-occurrences. This assumption is that words that occur together are likely a part of similar topics. The algorithm assigns document-topic distributions based on the clusters of words that appear in the given document.<sup>12</sup>

For example, say we generate a LDA model for a collection of news articles that has the following partial output:

![Illustration representing an LDA model](https://assets.ibm.com/is/image/ibm/table-topic-modeling?ts=1763391986674&dpr=off)

Here, we have two topics that may likely be described as immigration (Topic 1) and astronomy (Topic 2). The scores attached to each word are the probability of that keyword appearing in its given topic. The probabilities attached to each document are that document’s respective probabilities of belonging to a mixture of topics given the distribution and co-occurrence of words from each topic within that document. For example, the table’s first row lists *border* under Topic 1 with a 40% probability and *space* in Topic 2 with a 60% probability. These percentages indicate the probability of their respective terms occurring in that topic across the whole corpus. The first document row reads *Document 1: Topic 1: .95, Topic 2: .05*. This means that, based the occurrence of words in Document 1, the model projects Document 1 as being 95% derived from Topic 1 and 5% derived from Topic 2. In other words, our hypothetical LDA model assumes these are the topics and proportions of those topics used to generate the model.

Of course, polysemous words in particular create problems for such discrete categorizations — for example, *alien* may refer to a human immigrant or an extra-terrestrial creature. If our algorithm encounters *alien* in a document, how does it determine to which topic the word (and by extension, the document) belongs?

When assigning topics to words, the LDA algorithm uses what is known as Gibbs sampling. The Gibbs sampling formula is:

![Illustration of the Gibbs formula](https://assets.ibm.com/is/image/ibm/gibbs-formula?ts=1763391986839&dpr=off)

Understanding this equation’s exact operations and hyperparameters requires foundational knowledge in statistics and Markov Chain [Monte Carlo](https://www.ibm.com/topics/monte-carlo-simulation) techniques (the latter often employed in reinforcement learning). Nevertheless, we can summarize the equation’s principal components:

- The first ratio expresses the probability of topic *t* in document *d*. The algorithm calculates this probability according to the number of words in document *d* that belong to topic *t*. This essentially asks: how prevalent is topic *t* in document *d*?
- The second ratio expresses the probability of word *w* belonging to topic *t*. The algorithm calculates this probability by enumerating the occurrences of *w* in *t* over all word-tokens in *t*. This asks: with what frequency does word *w* appear in topic *t* throughout the rest of the corpus?

Note that Gibbs sampling is an iterative process. That is, a word is not sampled once, assigned a topic, and tossed aside. Rather, Gibbs sampling passes each word through multiple iterations, updating topic-word probabilities in light of one another.<sup>13</sup>

## Recent research

There are many use cases for topic models, from literary criticism<sup>14</sup> to bioinformatics<sup>15</sup> to hate speech detection in social media.<sup>16</sup> As with many NLP tasks, a significant proportion of topic modeling research through the years concerns English and other Latin-script languages. More recently, however, research has explored topic modeling approaches for Arabic and other non-Latin languages.<sup>17</sup>

Ongoing research also addresses evaluation metrics for topic models. Indeed, there is no one metrics used to evaluate topic models. Past evaluation metrics have adopted qualitative and quantitative approaches. The former requires significant domain-specific knowledge to evaluate topic mode key terms for interpretability.<sup>18</sup> Quantitative measures consist of log-likelihood and coherence scores, which aim to measure the likelihood and cohesion of topics within a model.<sup>19</sup> A wide body of research argues, however, such quantitative metrics may be unreliable.<sup>20</sup>

In attempt to resolve issues related to topic model evaluation, one study investigates [artificial intelligence](https://www.ibm.com/topics/artificial-intelligence) applications, notably [large language models](https://www.ibm.com/topics/large-language-models) (LLMs), as a means of designing and evaluating LDA models for specific research objectives. LLMs, the study argues, can help resolve longstanding problems in topic modeling, namely, how to determine and evaluate the appropriate number of topics.<sup>21</sup> Other studies also turn to LLM applications as a means to address the evaluation gap in topic modeling.<sup>22</sup>

## Footnotes

<sup>1 </sup>Daniel Jurafsky and James Martin, Speech and Language Processing: An Introduction to Natural Language Processing, Computational Linguistics, and Speech Recognition, 3rd edition, 2023, [https://web.stanford.edu/~jurafsky/slp3/](https://web.stanford.edu/~jurafsky/slp3/)

<sup>2</sup> Jay Alammar and Maarten Grootendorst, Hands-On Large Language Models, O’Reilly, 2024.

<sup>3</sup> David Blei, “Probabilistic Topic Models,” Communications of the ACM, Vol. 55, No. 4, 2012, pp. 77-84.

<sup>4</sup> Matthew Jockers, Text Analysis with R for Students of Literature, Springer, 2014.

<sup>5</sup> Cole Howard, Hobson Lane, and Hannes Hapke, Natural Language Processing in Action, Manning Publications, 2019. Sowmya Vajjala, Bodhisattwa Majumder, Anuj Gupta, Harshit Surana Practical Natural Language Processing, O’Reilly, 2020.

<sup>6</sup> Chandler Camille May, “Topic Modeling in Theory and Practice,” Dissertation, John Hopkins University, 2022.

<sup>7</sup> Practical Natural Language Processing, O’Reilly. David Blei, “Probabilistic Topic Models,” Communications of the ACM, Vol. 55, No. 4, 2012, pp. 77-84.

<sup>8</sup> Cole Howard, Hobson Lane, and Hannes Hapke, Natural Language Processing in Action, Manning Publications, Deerwester, “Indexing by Latent Semantic Analysis,” David Blei, “Probabilistic Topic Models,” Communications of the ACM, Vol. 55, No. 4, 2012, pp. 77-84.

<sup>9</sup> Hana Nelson, Essential Math for AI, O’Reilly, 2023. Scott Deerwester, Susan Dumais, George Furnas, Thomas Landauer, and Richard Harshman, “Indexing by Latent Semantic Analysis,” Journal of the American Society for Information Science, Vol. 41, No. 6, 1990, pp. 391-407, [https://asistdl.onlinelibrary.wiley.com/doi/abs/10.1002/%28SICI%291097-4571%28199009%2941%3A6%3C391%3A%3AAID-ASI1%3E3.0.CO%3B2-9](https://asistdl.onlinelibrary.wiley.com/doi/abs/10.1002/%28SICI%291097-4571%28199009%2941%3A6%3C391%3A%3AAID-ASI1%3E3.0.CO%3B2-9)

<sup>10</sup> Scott Deerwester, Susan Dumais, George Furnas, Thomas Landauer, and Richard Harshman, “Indexing by Latent Semantic Analysis,” Journal of the American Society for Information Science, Vol. 41, No. 6, 1990, pp. 391-407, [https://asistdl.onlinelibrary.wiley.com/doi/abs/10.1002/%28SICI%291097-4571%28199009%2941%3A6%3C391%3A%3AAID-ASI1%3E3.0.CO%3B2-9](https://asistdl.onlinelibrary.wiley.com/doi/abs/10.1002/%28SICI%291097-4571%28199009%2941%3A6%3C391%3A%3AAID-ASI1%3E3.0.CO%3B2-9)

<sup>11</sup> Elsa Negre, Information and Recommender Systems, Vol. 4, Wiley-ISTE, 2015. Hana Nelson, Essential Math for AI, O’Reilly, 2023.

<sup>12</sup> Sowmya Vajjala, Bodhisattwa Majumder, Anuj Gupta, Harshit Surana Practical Natural Language Processing, O’Reilly, 2020. David Blei, Andrew Ng, and Michael Jordan, “Lantent Dirichlet Allocation,” Journal of Machine Learning Research, Vol. 3, 2003, pp. 993-1022.

<sup>13</sup> Zhiyuan Chen and Bing Liu, “Topic Models for NLP Applications,” Encyclopedia of Machine Learning and Data Science, Springer, 2020.

<sup>14</sup> Derek Greene, James O’Sullivan, and Daragh O’Reilly, “Topic modelling literary interviews from The Paris Review,” Digital Scholarship in the Humanities, 2024, [https://academic.oup.com/dsh/article/39/1/142/7515230?login=false](https://academic.oup.com/dsh/article/39/1/142/7515230?login=false)

<sup>15</sup> Yichen Zhang, Mohammadali (Sam) Khalilitousi, and Yongjin Park, “Unraveling dynamically encoded latent transcriptomic patterns in pancreatic cancer cells by topic modeling,” Cell Genomics, Vol. 3, No. 9, 2023, [https://www.ncbi.nlm.nih.gov/pmc/articles/PMC10504675/](https://pmc.ncbi.nlm.nih.gov/articles/PMC10504675/)

<sup>16</sup> Richard Shear, Nicholas Johnson Restrepo, Yonatan Lupu, and Neil F. Johnson, “Dynamic Topic Modeling Reveals Variations in Online Hate Narratives,” Intelligent Computing, 2022, [https://link.springer.com/chapter/10.1007/978-3-031-10464-0_38](https://pmc.ncbi.nlm.nih.gov/articles/PMC10504675/)

<sup>17</sup> Abeer Abuzayed and Hend Al-Khalifa, “BERT for Arabic Topic Modeling: An Experimental Study on BERTopic Technique,” Procedia Computer Science, 2021, pp. 191-194, [https://www.sciencedirect.com/science/article/pii/S1877050921012199](https://pmc.ncbi.nlm.nih.gov/articles/PMC10504675/) . Raghad Alshalan, Hend Al-Khalifa, Duaa Alsaeed, Heyam Al-Baity, and Shahad Alshalan, “Detection of Hate Speech in COVID-19--Related Tweets in the Arab Region: Deep Learning and Topic Modeling Approach,” Journal of Medical Internet Research, Vol. 22, No. 12, 2020, [https://www.jmir.org/2020/12/e22609](https://www.jmir.org/2020/12/e22609/)

<sup>18</sup> Matthew Gillings and Andrew Hardie, “The interpretation of topic models for scholarly analysis: An evaluation and critique of current practice,” Digital Scholarship in the Humanities, Vol. 38, No. 2, 2023, pp. 530–543, [https://academic.oup.com/dsh/article-abstract/38/2/530/6957052](https://www.jmir.org/2020/12/e22609/)

<sup>19</sup> Chandler Camille May, “Topic Modeling in Theory and Practice,” Dissertation, John Hopkins University, 2022.

<sup>20</sup> Zachary Lipton, “The Mythos of Model Interpretability: In machine learning, the concept of interpretability is both important and slippery,” Queue, Vol. 13, No. 3, 2018, pp. 31-57, [https://dl.acm.org/doi/10.1145/3236386.3241340](https://www.jmir.org/2020/12/e22609/) Caitlin Doogan and Wray Buntine, “Topic Model or Topic Twaddle? Re-evaluating Semantic Interpretability Measures,” Proceedings of the 2021 Conference of the North American Chapter of the Association for Computational Linguistics: Human Language Technologies” 2021, pp. 3824-3848, [https://aclanthology.org/2021.naacl-main.300.pdf](https://aclanthology.org/2021.naacl-main.300.pdf) . Alexander Hoyle, Pranav Goel, Andrew Hian-Cheong, Denis Peskov, Jordan Boyd-Graber, and Philip Resnik, “Is Automated Topic Model Evaluation Broken? The Incoherence of Coherence,” Advances in Neural Processing Systems, vol. 34, 2021, [https://proceedings.neurips.cc/paper_files/paper/2021/hash/0f83556a305d789b1d71815e8ea4f4b0-Abstract.html](https://proceedings.neurips.cc/paper_files/paper/2021/hash/0f83556a305d789b1d71815e8ea4f4b0-Abstract.html)

<sup>21</sup> Dominik Stammbach, Vilém Zouhar, Alexander Hoyle, Mrinmaya Sachan, and Elliott Ash, “Revisiting Automated Topic Model Evaluation with Large Language Models,” Proceedings of the 2023 Conference on Empirical Methods in Natural Language Processing, 2023, [https://aclanthology.org/2023.emnlp-main.581](https://aclanthology.org/2023.emnlp-main.581/)  

 <sup>22</sup> Eric Chagnon, Ronald Pandolfi, Jeffrey Donatelli, and Daniela Ushizima, “Benchmarking topic models on scientific articles using BERTeley,” Natural Language Processing Journal, Vol. 6, 2024, pp. 2949-7191, [https://www.sciencedirect.com/science/article/pii/S2949719123000419](https://www.sciencedirect.com/science/article/pii/S2949719123000419) . Han Wang, Nirmalendu Prakash, Nguyen Khoi Hoang, Ming Shan Hee, Usman Naseem, and Roy Ka-Wei Lee, “Prompting Large Language Models for Topic Modeling,” Proceedings of the 2023 IEEE International Conference on Big Data, 2023, pp. 1236-1241, [https://www.computer.org/csdl/proceedings-article/bigdata/2023/10386113/1TUOz14EiBy](https://www.computer.org/csdl/proceedings-article/bigdata/2023/10386113/1TUOz14EiBy)
