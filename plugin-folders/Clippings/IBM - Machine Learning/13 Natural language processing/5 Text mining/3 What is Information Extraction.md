---
title: What is information extraction?
source: https://www.ibm.com/think/topics/information-extraction
author:
- '[[Ivan Belcic]]'
- '[[Cole Stryker]]'
published: 2025-02-12
created: 2026-08-31
description: "Information extraction (IE) is the automated process of extracting structured information from semi-structured or unstructured text data, transforming it into organized, searchable and machine-readable data."
---

## What is information extraction?

Information extraction (IE) is the automated process of extracting structured information from semi-structured or unstructured text data, transforming human language text sources such as PDFs into a format that’s organized, searchable and machine-readable. [Natural language processing](https://www.ibm.com/think/topics/natural-language-processing) (NLP) relies on information extraction to identify important data within input text.

Information extraction algorithms can identify entities, including names, relationships, events, sentiment and more, then classify and store them in a database for further use. The resulting structured information has a standardized format and is typically stored in rows and columns that identify its attributes. The standardized storage is the primary differentiator between [structured data and unstructured data](https://www.ibm.com/think/topics/structured-vs-unstructured-data).

All the data values within the same database adhere to the same structured format with the same defined attributes. Relational attributes are also highlighted to connect databases together based on shared attributes.

## Why is information extraction important?

Information extraction allows enterprises to transform documents into actionable datasets and generate valuable insights from them. The intelligent document processing market—which IE facilitates—is projected to grow at a compound annual growth rate (CAGR) of 33.1% through 2030 from a value of USD 2.3 billion in 2024.<sup>[1](#footnotes1)</sup>

### Information retrieval

Information extraction systems set the stage for automated [information retrieval](https://www.ibm.com/think/topics/information-retrieval): the use of [artificial intelligence](https://www.ibm.com/think/topics/artificial-intelligence) (AI) algorithms to automatically find and retrieve relevant data from knowledge bases. Information retrieval is an essential component of [retrieval-augmented generation (RAG)](https://www.ibm.com/think/topics/retrieval-augmented-generation), a process by which [large language models](https://www.ibm.com/think/topics/large-language-models) (LLMs) gain access to more data for high accuracy in domain-specific use cases.

RAG can make LLM chatbots more accurate when applied to [question-answering](https://www.ibm.com/think/topics/question-answering) tasks because the LLM can draw on more knowledge outside of its training data to generate better answers.

### Data-driven decision-making

Business leaders can use extracted information to facilitate data-driven decision-making in real-time. IE is a preliminary stage in the larger information processing cycle in which information is acquired, organized, stored, manipulated and made available for use.

[Data pipelines](https://www.ibm.com/think/topics/data-pipeline) deliver information across an enterprise, connecting input points—for example, online orders—to databases. From there, data visualization tools draw on that data to create charts and graphs in real-time, revealing actionable insights that drive strategic decision-making.

The large datasets of structured data outputted by IE systems can be used to create reports and summaries. [Machine learning algorithms](https://www.ibm.com/think/topics/machine-learning-algorithms) for IE can also perform [text summarization](https://www.ibm.com/think/topics/text-summarization) to condense detailed documents into quickly digestible bullets with annotations for quick reference.

For example, IE in healthcare can automatically compile a patient report from multiple files, potentially making it easier for doctors to diagnose issues and prescribe treatments. Financial professionals can generate more accurate forecasts with information extracted from multiple reports, news articles and other sources.

## Types of information extraction

Information extraction tasks are categorized based on the type of information being identified and labeled. IE systems can handle tasks including:

- Named entity recognition (NER)
- Relation extraction
- Event extraction
- Sentiment analysis

### Named entity recognition (NER)

[Named entity recognition](https://www.ibm.com/think/topics/named-entity-recognition) is the IE task of identifying named entities in unstructured data. Named entities are real-world objects that can be uniquely identified. Essentially, they are the proper nouns of data. Named entities include people, dates, corporations, places and products and can be both physical or abstract.

In the sentence “As of January 2025, Arvind Krishna is the CEO of IBM,” the named entities include *January 2025*, *Arvind Krishna*, *CEO* and *IBM*.”

#### Entity linking

Entity linking is the process of figuring out whether multiple entities refer to the same real-world object. When conducting IE on an article mentioning “Arvind Krishna,” “Krishna” and “IBM’s CEO,” an entity linking subtask would identify all 3 as references to the same person. Entity linking is also referred to as *coreference resolution*.

### Relation extraction (RE)

Relation extraction is the information extraction task of identifying and categorizing the relationships between entities in a data source. Uncovering relationships between entities can open the door to insights that might otherwise go unnoticed.

In our example sentence from the beginning of this section, the RE process would draw a “works at” connection between “Arvind Krishna” and “IBM” with the title of “CEO.”

#### Relation extraction versus relationship extraction

The terms *relation extraction* and *relationship extraction* are often used interchangeably, but some data scientists argue for a subtle distinction. While *relationship extraction* covers any attempt to discern the relationships between entities, *relation extraction* is most often used regarding the application of machine learning models to accomplish this task.

### Event extraction

Event extraction is how IE systems recognize discrete events in a body of input text. Words, such as “appointment” or “meeting,” can trigger an event extraction sequence, as can dates. Event extraction covers the event itself, the time and date at which it occurred and any mentioned participants.

In the sample sentence, “Arvind Krishna attended the conference in January 2025,” an event extraction algorithm would identify that a conference took place in January 2025 and that 1 of the attendees was IBM CEO Arvind Krishna.

### Sentiment analysis

[Sentiment analysis](https://www.ibm.com/think/topics/sentiment-analysis) determines the feeling communicated by a piece of text. Sentiment analysis is a valuable tool for conducting market research and understanding customer behavior.

If given a dataset consisting of user reviews, an IE algorithm can provide semantic insights that reveal the percentages of consumers that feel positively, negatively or neutrally about a product. Product managers could then take those insights and tweak the product to make it more appealing to a greater portion of their current and potential users.

## How does information extraction work?

Information extraction works by parsing unstructured data sources with [machine learning](https://www.ibm.com/think/topics/machine-learning) algorithms to identify meaningful data. IE systems label the discovered data entities and store them in an organized, queryable database for efficient retrieval.

Information extraction techniques include:

- Rule-based
- Classification (machine learning)
- Sequence labeling

These methods are not mutually exclusive—advancements in IE have led to hybrid models that combine methods for improved results.

### Rule-based information extraction

Rule-based information extraction parses documents to identify entities based on established “rules”—predefined patterns and definitions that are known about the entities in the text. Rule-based IE is most often applied to semi-structured data sources—data that isn’t fully structured but still has some identifying features such as tags or metadata.

Top-down rule-based IE works by progressing from general cases to specific cases, while the bottom-up method does the opposite.

### Classification-based information extraction

Classification-based IE is a 2-step process that approaches information extraction as a [supervised learning](https://www.ibm.com/think/topics/supervised-vs-unsupervised-learning) [classification](https://www.ibm.com/think/topics/classification-machine-learning) task. First, machine learning models are trained on labeled datasets to learn the connections between entities and their corresponding attributes. The models then predict labels for the entities they identify in new unstructured data.

### Sequence labeling

Sequence labeling is the cornerstone of NLP and uses [deep learning](https://www.ibm.com/think/topics/deep-learning) models to identify and label the components of an input sequence—for example, the words in a chatbot prompt. Sequence labeling is a critical NLP preprocessing step, helping ensure that [neural networks](https://www.ibm.com/think/topics/neural-networks) know exactly how to interpret the input data.

In addition to identifying entities in data, sequence labeling also captures dependencies between parts of an input sequence. Dependencies are a special type of relationship in which 1 part of an input sequence relies on another part to be correctly interpreted. [Transformer models](https://www.ibm.com/think/topics/transformer-model) such as general-purpose technologies ([GPTs](https://www.ibm.com/think/topics/gpt)) excel at capturing dependencies, which is why they can maintain contextual understanding across lengthy input sequences.

## Footnotes

1. [Intelligent Document Processing Market Size, Share & Trends Analysis Report By Component (Solution, Services), By Technology (ML, NLP), By Deployment, By Organization Size, By End-use (Manufacturing, Retail), By Region, And Segment Forecasts, 2025-2030](https://www.grandviewresearch.com/industry-analysis/intelligent-document-processing-market-report), Grand View Research
