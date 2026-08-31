---
title: What is named entity recognition?
source: https://www.ibm.com/think/topics/named-entity-recognition
author: null
published: 2024-12-03
created: 2026-08-31
description: "Named entity recognition (NER) is a component of natural language processing (NLP) that identifies predefined categories of objects in a body of text."
---

## What is named entity recognition?

Named entity recognition (NER)—also called entity chunking or entity extraction—is a component of [natural language processing (NLP)](https://www.ibm.com/think/topics/natural-language-processing) that identifies predefined categories of objects in a body of text.

These categories can include, but are not limited to, names of individuals, organizations, locations, expressions of times, quantities, medical codes, monetary values and percentages, among others. Essentially, NER is the process of taking a string of text (i.e., a sentence, paragraph or entire document), and identifying and classifying the entities that refer to each category.

When the term “NER” was coined at the Sixth Message Understanding Conference (MUC-6), the goal was to streamline information extraction tasks, which involved processing large amounts of unstructured text and identifying key information. Since then, NER has expanded and evolved, owing much of its evolution to advancements in [machine learning](https://www.ibm.com/think/topics/machine-learning) and [deep learning](https://www.ibm.com/think/topics/deep-learning) techniques.

## NER techniques

According to a 2019 survey, about 64 percent of companies rely on structured data from internal resources, but fewer than 18 percent are leveraging unstructured data and social media comments to inform business decisions<sup>1</sup>.

The organizations that do utilize NER for unstructured data extraction rely on a range of approaches, but most fall into three broad categories: rule-based approaches, machine learning approaches and hybrid approaches.

- **Rule-based approaches** involve creating a set of rules for the grammar of a language. The rules are then used to identify entities in the text based on their structural and grammatical features. These methods can be time-consuming and may not generalize well to unseen data.

- **Machine learning approaches** involve training an [AI](https://www.ibm.com/think/topics/artificial-intelligence)-driven machine learning model on a labeled dataset using algorithms like conditional random fields and maximum entropy (two types of complex statistical language models). Techniques can range from traditional machine learning methods (e.g., decision trees and support vector machines) to more complex deep learning approaches, like recurrent neural networks (RNNs) and transformers. These methods generalize better to unseen data, but they require a large amount of labeled training data and can be computationally expensive.

- **Hybrid approaches** combine rule-based and machine learning methods to leverage the strengths of both. They can use a rule-based system to quickly identify easy-to-recognize entities and a machine learning system to identify more complex entities.

## NER methodologies

Since the inception of NER, there have been some significant methodological advancements, especially those that rely on deep learning-based techniques. Newer iterations include:

- **Recurrent neural networks (RNNs)** and **long short-term memory (LSTM)**. RNNs are a type of neural network designed for sequence prediction problems. LSTMs, a special kind of RNN, can learn to recognize patterns over time and maintain information in “memory” over long sequences, making them particularly useful for understanding context and identifying entities.

- **Conditional random fields (CRFs)**. CRFs are often used in combination with LSTMs for NER tasks. They can model the conditional probability of an entire sequence of labels, rather than just individual labels, making them useful for tasks where the label of a word depends on the labels of surrounding words.

- **Transformers and BERT**. Transformer networks, particularly the BERT (Bidirectional Encoder Representations from Transformers) model, have had a significant impact on NER. Using a self-attention mechanism that weighs the importance of different words, BERT accounts for the full context of a word by looking at the words that come before and after it.

## The NER process

### Step 1. Data collection

The first step of NER is to aggregate a dataset of annotated text. The dataset should contain examples of text where named entities are labeled or marked, indicating their types. The annotations can be done manually or using automated methods.

### Step 2. Data preprocessing

Once the dataset is collected, the text should be cleaned and formatted. You may need to remove unnecessary characters, normalize the text and/or split text into sentences or tokens.

### Step 3. Feature extraction

During this stage, relevant features are extracted from the preprocessed text. These features can include part-of-speech tagging (POS tagging), word embeddings and contextual information, among others. The choice of features will depend on the specific NER model the organization uses.

### Step 4. Model training

The next step is to train a machine learning or deep learning model using the annotated dataset and the extracted features. The model learns to identify patterns and relationships between words in the text, as well as their corresponding named entity labels.

### Step 5. Model evaluation

After you have trained the NER model, it should be evaluated to assess its performance. You can measure metrics like precision, recall and F1 score, which indicate how well the model correctly identifies and classifies named entities.

### Step 6. Model fine-tuning

Based on the evaluation results, you will refine the model to improve its performance. This can include adjusting hyperparameters, modifying the training data and/or using more advanced techniques (e.g., ensembling or domain adaptation).

### Step 7. Inference

At this stage, you can start using the model for inference on new, unseen text. The model will take the input text, apply the preprocessing steps, extract relevant features and ultimately predict the named entity labels for each token or span of text.

### Step 8. Post-processing

The output of the NER model may need to undergo post-processing steps to refine results and/or add contextual information. You may need to complete tasks like entity linking, wherein the named entities are linked to knowledge bases or databases for further enrichment.

## Implementing the NER process

The easiest way to implement a named entity recognition system is to rely on an [application programming interface](https://www.ibm.com/think/topics/api) (API). NER APIs are web-based or local interfaces that provide access to NER functionalities. Some popular examples of NER APIs are:

### Natural Language Toolkit (NLTK)

NLTK is a leading [open-source](https://www.ibm.com/think/topics/open-source) platform for building [Python](https://www.ibm.com/think/topics/python-vs-r) programs to work with human language data. It provides easy-to-use interfaces for more than 100 trained extraction models<sup>2</sup>. It also includes text processing libraries for classification, tokenization, stemming, tagging, parsing and semantic reasoning. NLKT has its own classifier to recognize named entities, called ne_chunk, but also provides a wrapper to use the Stanford NER tagger in Python.

### Stanford Named Entity Recognizer

Developed by Stanford University, the Stanford NER is a Java implementation widely considered the standard entity extraction library. It relies on CRF and provides pre-trained models for extracting named entities.

### SpaCy

Written in Python and known for its speed and user-friendliness, SpaCy is an open-source software library for advanced NLP. It's built on the very latest research and was designed for use with real products. It also has an advanced statistical system that allows users to build customized NER extractors.

## Applications of NER

As technologies continue to evolve, NER systems will only become more ubiquitous, helping organizations make sense of the data they encounter every day. So far, it’s proven instrumental to multiple sectors, from healthcare and finance to customer service and cybersecurity.

Some of the most impactful use cases are:

NER is a crucial first step in extracting useful, structured information from large, unstructured databases. Search engines use NER to improve the relevance and preciseness of their search results.

News aggregators use NER to categorize articles and stories based on the named entities they contain, enabling a more organized, efficient way of presenting news to audiences. For instance, NER for news apps automates the classification process, grouping similar news stories together and providing a more comprehensive view of particular news events.

With the proliferation of social media platforms, the amount of textual data available for analysis is overwhelming. NER plays a significant role in social media analysis, identifying key entities in posts and comments to understand trends and public opinions about different topics (especially opinions around brands and products). This information can help companies conduct sentiment analyses, develop marketing strategies, craft customer service responses and accelerate product development efforts.

Virtual assistants and generative artificial intelligence chatbots and use NER to understand user requests and customer support queries accurately. By identifying critical entities in user queries, these AI-powered tools can provide precise, context-specific responses. For example, in the query "Find Soul Food restaurants near Piedmont Park," NER helps the assistant understand "Soul Food" as the cuisine, "restaurants" as the type of establishment and "Piedmont Park" as the location.

In cybersecurity, NER helps companies identify potential threats and anomalies in network logs and other security-related data. For example, it can identify suspicious IP addresses, URLs, usernames and filenames in network security logs. As such, NER can facilitate more thorough security incident investigations and improve overall network security.

## Challenges of using NER

NER has come a long way since its inception, integrating innovative technologies and expanding prolifically in its usefulness along the way. However, there are a few noteworthy challenges to consider when assessing NER technologies.

While NER has made a lot of progress for languages like English, it doesn’t have the same level of accuracy for many others. This is often due to a lack of labeled data in these languages. Cross-lingual NER, which involves transferring knowledge from one language to another, is an active area of research that may help bridge the NET language gap.

Sometimes entities can also be nested within other entities, and recognizing these nested entities can be challenging. For example, in the sentence "The Pennsylvania State University, University Park was established in 1855," both "Pennsylvania State University" and "The Pennsylvania State University, University Park" are valid entities.

Furthermore, while general NER models can identify common entities like names and locations, they may struggle with entities that are specific to a certain domain. For example, in the medical field, identifying complex terms like disease names or drug names can be challenging. Domain-specific NER models can be trained on specialized, domain-specific data, but procuring that information can itself prove challenging.

NER models can also encounter broader issues with ambiguity (for instance, "Apple" could refer to a fruit or the tech company); entity name variation (e.g., "USA," "U.S.A.," "United States" and "United States of America" all refer to the same country); and limited contextual information (wherein texts and/or sentences don’t contain enough context to accurately identify and categorize entities).

Though NER has its challenges, ongoing advancements are constantly improving its accuracy and applicability, and therefore helping minimize the impact of existing technology gaps.

## The future of NER

While NER is a well-established field, there is still much work to be done.

Taking a look at the future, one promising area is unsupervised learning techniques for NER. While supervised learning techniques have performed well, they require lots of labeled data, which can be challenging to obtain. Unsupervised learning techniques don’t require labeled data and can help organizations overcome data availability challenges.

Another interesting direction is the integration of NER with other NLP tasks. For example, joint models for NER and entity linking (which involves linking entities to their corresponding entries in a knowledge base) or NER and coreference resolution (which involves determining when two or more expressions in a text refer to the same entity) could allow for systems that better understand and process text.

Few-shot learning and multimodal NER also expand the capabilities of NER technologies. With few-shot learning, models are trained to perform tasks with only a few examples, which can be particularly helpful when labeled data is scarce. Multimodal NER, on the other hand, involves integrating text with other entity types. An image or piece of audio, for example, could provide additional context that helps in recognizing entities.

## Footnotes

<sup>1</sup> [Analytics and AI-driven enterprises thrive in the Age of With](https://www2.deloitte.com/us/en/insights/topics/analytics/insight-driven-organization.html). Deloitte Insights. July 25, 2019

<sup>2</sup> [3 open source NLP tools for data extraction](https://www.infoworld.com/article/2338710/3-open-source-nlp-tools-for-data-extraction.html). InfoWorld. July 10, 2023
