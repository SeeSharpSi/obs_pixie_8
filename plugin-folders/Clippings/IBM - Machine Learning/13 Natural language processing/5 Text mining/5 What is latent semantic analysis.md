---
title: What is latent semantic analysis?
source: https://www.ibm.com/think/topics/latent-semantic-analysis
author:
- '[[Jacob Murel Ph.D.]]'
- '[[Joshua Noble]]'
published: 2024-12-05
created: 2026-08-31
description: "Learn about this topic modeling technique for generating core semantic groups from a collection of documents."
---

## What is latent semantic analysis?

In [machine learning](https://www.ibm.com/topics/machine-learning), latent semantic analysis (LSA) is a [topic modeling](https://www.ibm.com/topics/topic-modeling) technique that analyzes word co-occurence to uncover latent topics in documents. LSA uses [dimensionality reduction](https://www.ibm.com/topics/dimensionality-reduction) to create structured data from unstructured text in order to aid text classification and retrieval.

LSA is is one of two principal topic modeling techniques, the other being [latent Dirichlet allocation](https://www.ibm.com/topics/latent-dirichlet-allocation) (LDA). Topic modeling is a [natural language processing](https://www.ibm.com/topics/natural-language-processing) (NLP) technique that applies [unsupervised learning](https://www.ibm.com/topics/unsupervised-learning) on large text datasets in order to produce a summary set of terms derived from those documents. These terms are meant to represent the collection’s overall primary set of topics. Topic models aim to uncover the latent topics or themes characterizing a number of documents.<sup>[1](#f01)</sup>

Users can generate LSA topic models using scikit-learn’s (commonly referred to as *sklearn*) [natural language toolkit](https://www.nltk.org/) (NLTK) and [gensim](https://pypi.org/project/gensim/) in Python. The [topic models](https://cran.r-project.org/web/packages/topicmodels/) and [lsa](https://cran.r-project.org/web/packages/lsa/lsa.pdf) packages in R also contain functions for generating LSA topic models.

### Information retrieval

Latent semantic analysis is associated with latent semantic indexing (LSI) which is an [information retrieval](https://www.ibm.com/think/topics/information-retrieval) technique. In information retrieval systems, LSI uses the same mathematical procedure underlying LSA to map user queries to documents based on word co-occurrence. If a user queries a system for *waltz* and *foxtrot*, they might be interested in documents that don't contain either of those terms but do contain terms that often co-occur with their query terms. For instance *tango* and *bolero* may frequently co-occur with the query terms and should indicate documents about the same topic. LSI indexes documents according to latent semantic word groups consisting of commonly co-occurring words. In this way, it can improve search engine results. LSA applies the same mathematical procedure as LSI in order to capture the hidden semantic structure underlaying large collections of documents.<sup>[2](#f02)</sup>

## How latent semantic analysis works

### Document-term matrix

LSA begins with the document-term matrix or sometimes a term-document matrix. This displays the number of occurrences for each word across all documents. In Python (to offer one example), users can construct these matrices using a pandas dataframe. Here is an example document-term matrix using the three text strings as individual documents:

**d1**: My love is like red, red roses

**d2**: Roses are red, violets are blue

**d3**: Moses supposes his toes-es are roses

![example document-term matrix with three documents](https://assets.ibm.com/is/image/ibm/term-matrix-diagram?ts=1763388266668&dpr=off)

This matrix shows the word frequency of each word across all three documents following tokenization and stopword removal. Each column corresponds to a document, while each row corresponds to a specific word found across the whole text corpus. The values in the matrix signify the number of times a given term appears in a given document. If term w occurs n times within document d, then [w,d] = n. So, for example, document 1 uses 'red' twice, and so [*red*, *d1*] = 2.

From the document-term matrix, LSA produces a document-document matrix and term-term matrix. If the document-term matrix dimensions are defined as *d* documents times *w* words, then the document-document matrix is *d* times *d* and the term-term matrix *w* times *w*. Each value in the document-document matrix indicates the number of words each document has in common. Each value in the term-term matrix indicates the number of documents in which two terms co-occur.<sup>[3](#f03)</sup>

Data sparsity, which leads to model [overfitting](https://www.ibm.com/topics/overfitting), is when a majority of data values in a given dataset are null (that is, empty). This happens regularly when constructing document-term matrices, for which each individual word is a separate row and vector space dimension, as one document will regularly lack a majority of the words that are more frequent in other documents. Indeed, the example document-term matrix here used contains numerous uses for words such as *Moses*, *violets* and *blue* that appear in only one document. Of course, text preprocessing techniques, such as stopword removal, [stemming](https://www.ibm.com/topics/stemming) and [lemmatization](https://www.ibm.com/topics/stemming-lemmatization), can help reduce sparsity. LSA offers a more targeted approach however.

### Dimensionality reduction

LSA deploys a dimensionality reduction technique known as singular value decomposition (SVD) to reduce sparsity in the document-term matrix. SVD powers many other dimension reduction approaches such as [principal component analysis](https://www.ibm.com/topics/principal-component-analysis). SVD helps alleviate problems resulting from polysemy, single words that have multiple meanings, and synonymy, different words with similar meaning.

Using the matrices calculated from the terms across document-document and term-term matrices, the LSA algorithm performs SVD on the initial term-document matrix. This produces new special matrices of eigenvectors that break down the original term-document relationships into linearly independent factors. Most important of these is the diagonal matrix of singular values produced from the square roots of the document-document matrix’s eigenvalues. In this diagonal matrix, often represented as Σ, values are always positive and arranged in decreasing order down the matrix diagonal:

![Example of a sparse sigma matrix](https://assets.ibm.com/is/image/ibm/sigma-matrix-diagram?ts=1763388267039&dpr=off)

As shown in this example Σ matrix, many of the lower values are near zero. The developer determines a cut-off value appropriate for their situation and reduces all singular values in Σ below that threshold to zero. This effectively means removing all of the rows and columns entirely occupied by zeros. In turn, we remove rows and columns from our other original matrices until they have the same number of rows and columns as Σ. This reduces the model’s dimensions.<sup>[4](#f04)</sup>

### Document comparison

Once model dimensions have been reduced through SVD, the LSA algorithm compares documents in a lower dimensional semantic space using cosine similarity. The first step in this comparison stage involves mapping documents in vector space. Here, LSA treats texts as a [bag of words](https://www.ibm.com/topics/bag-of-words) model. The algorithm plots each text from the corpus or corpora as document vector, with individual words from the reduced matrix as the dimensions of that vector. Plotting ignores word order and context, focusing instead on how often words occur and how often they co-occur across documents.<sup>[5](#f05)</sup>

With standard bag of words models, semantically irrelevant words (for example, words such as *the* and *some,* and other similar words) can have the highest term frequency, and so greatest weight in a model. Term frequency-inverse document frequency (TF-IDF) is one technique to correct for this. It does this by accounting for a word’s prevalence throughout every document in a text set and weighting words in each document according to the word’s prevalence throughout the corpus.<sup>[6](#f06)</sup>

Once documents are plotted in vector space, the LSA algorithm uses the cosine similarity metric to compare them. Cosine similarity signifies the measurement of the angle between two vectors in vector space. It can be any value between -1 and 1. The higher the cosine score, the more alike the two documents are considered. Cosine similarity is represented by this formula, where *a* and *b* signify two document vectors:<sup>[7](#f07)</sup>

![cosine similarity score equation](https://assets.ibm.com/is/image/ibm/content-based-filtering-cosine-similarity?ts=1763388267400&dpr=off)

## Recent research

There are many use cases for topic models, from literary criticism<sup>[8](#f08) </sup>to bioinformatics<sup>[9](#f09) </sup>to hate speech detection in social media.<sup>[10](#f10) </sup>As with many NLP tasks, a significant proportion of topic modeling research through the years concerns English and other Latin-script languages. More recently, however, research has explored topic modeling approaches for Arabic and other non-Latin languages.<sup>[11](#f11) </sup>Research has also turned to how [large language models](https://www.ibm.com/topics/large-language-models) (LLMs) might advance and improve topic models. For instance, one study argues that LLMs provide an automated method for resolving longstanding problems in topic modeling, namely how to determine the appropriate number of topics and how to evaluate generated topics.<sup>[12](#f12)</sup>

## Footnotes

1 Daniel Jurafsky and James Martin, *Speech and Language Processing: An Introduction to Natural Language Processing, Computational Linguistics, and Speech Recognition*, 3<sup>rd</sup> edition, 2023, [https://web.stanford.edu/~jurafsky/slp3/](https://web.stanford.edu/~jurafsky/slp3/) (link resides outside ibm.com). Jay Alammar and Maarten Grootendorst, *Hands-On Large Language Models*, O’Reilly, 2024.

2 Christopher Manning and Hinrich Schütze, *Foundations of Statistical Natural Language Processing*, MIT Press, 2000.

3 Scott Deerwester, Susan Dumais, George Furnas, Thomas Landauer, and Richard Harshman, “Indexing by Latent Semantic Analysis,” *Journal of the American Society for Information Science*, Vol. 41, No. 6, 1990, pp. 391-407, [https://asistdl.onlinelibrary.wiley.com/doi/abs/10.1002/%28SICI%291097-4571%28199009%2941%3A6%3C391%3A%3AAID-ASI1%3E3.0.CO%3B2-9](https://asistdl.onlinelibrary.wiley.com/doi/abs/10.1002/%28SICI%291097-4571%28199009%2941%3A6%3C391%3A%3AAID-ASI1%3E3.0.CO%3B2-9) (link resides outside of ibm.com). Alex Thomo, “Latent Semantic Analysis,” [https://www.engr.uvic.ca/~seng474/svd.pdf](https://www.engr.uvic.ca/~seng474/svd.pdf) (link resides outside of ibm.com).

4 Hana Nelson, *Essential Math for AI*, O’Reilly, 2023. Scott Deerwester, Susan Dumais, George Furnas, Thomas Landauer, and Richard Harshman, “Indexing by Latent Semantic Analysis,” *Journal of the American Society for Information Science*, Vol. 41, No. 6, 1990, pp. 391-407, [https://asistdl.onlinelibrary.wiley.com/doi/abs/10.1002/%28SICI%291097-4571%28199009%2941%3A6%3C391%3A%3AAID-ASI1%3E3.0.CO%3B2-9](https://asistdl.onlinelibrary.wiley.com/doi/abs/10.1002/%28SICI%291097-4571%28199009%2941%3A6%3C391%3A%3AAID-ASI1%3E3.0.CO%3B2-9) (link resides outside of ibm.com).

5 Matthew Jockers, *Text Analysis with R for Students of Literature*, Springer, 2014.

6 Alice Zheng and Amanda Casari, *Feature Engineering for Machine Learning*, O’Reilly, 2018.

7 Elsa Negre, *Information and Recommender Systems*, Vol. 4, Wiley-ISTE, 2015. Hana Nelson, *Essential Math for AI*, O’Reilly, 2023.

8 Derek Greene, James O'Sullivan, and Daragh O'Reilly, “Topic modelling literary interviews from The Paris Review,” Digital Scholarship in the Humanities, 2024,[https://academic.oup.com/dsh/article/39/1/142/7515230?login=false](https://academic.oup.com/dsh/article/39/1/142/7515230?login=false)(link resides outside ibm.com).

9 Yichen Zhang, Mohammadali (Sam) Khalilitousi, and Yongjin Park, “Unraveling dynamically encoded latent transcriptomic patterns in pancreatic cancer cells by topic modeling,” Cell Genomics, Vol. 3, No. 9, 2023, [https://www.ncbi.nlm.nih.gov/pmc/articles/PMC10504675/](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC10504675/) (link resides outside ibm.com).

10 Richard Shear, Nicholas Johnson Restrepo, Yonatan Lupu, and Neil F. Johnson, “Dynamic Topic Modeling Reveals Variations in Online Hate Narratives,” Intelligent Computing, 2022, [https://link.springer.com/chapter/10.1007/978-3-031-10464-0_38](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC10504675/) (link resides outside ibm.com).

11 Abeer Abuzayed and Hend Al-Khalifa, “BERT for Arabic Topic Modeling: An Experimental Study on BERTopic Technique,” Procedia Computer Science, 2021, pp. 191-194, [https://www.sciencedirect.com/science/article/pii/S1877050921012199](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC10504675/) (link resides outside ibm.com). Raghad Alshalan, Hend Al-Khalifa, Duaa Alsaeed, Heyam Al-Baity, and Shahad Alshalan, “Detection of Hate Speech in COVID-19--Related Tweets in the Arab Region: Deep Learning and Topic Modeling Approach,” Journal of Medical Internet Research, Vol. 22, No. 12, 2020, [https://www.jmir.org/2020/12/e22609/](https://www.jmir.org/2020/12/e22609/) (link resides outside ibm.com).

12 Dominik Stammbach, Vilém Zouhar, Alexander Hoyle, Mrinmaya Sachan, and Elliott Ash, “Revisiting Automated Topic Model Evaluation with Large Language Models,” Proceedings of the 2023 Conference on Empirical Methods in Natural Language Processing, 2023, [https://aclanthology.org/2023.emnlp-main.581/](https://aclanthology.org/2023.emnlp-main.581/) (link resides outside ibm.com).
