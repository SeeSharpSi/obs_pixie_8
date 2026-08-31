---
title: What is natural language generation (NLG)?
source: https://www.ibm.com/think/topics/natural-language-generation
author:
- '[[Ivan Belcic]]'
- '[[Cole Stryker]]'
published: 2025-03-06
created: 2026-08-31
description: "Natural language generation (NLG) is the use of artificial intelligence (AI) to create natural language outputs from structured and unstructured data."
---

## What is natural language generation (NLG)?

Natural language generation (NLG) is the use of [artificial intelligence (AI)](https://www.ibm.com/think/topics/artificial-intelligence) to create natural language outputs from structured and unstructured data. NLG makes it possible for computers and [generative AI (gen AI)](https://www.ibm.com/think/topics/generative-ai) software applications to interact with users in comprehensible human language. Along with [natural language understanding (NLU)](https://www.ibm.com/think/topics/natural-language-understanding), NLG is a subcategory of [natural language processing (NLP)](https://www.ibm.com/think/topics/natural-language-processing).

NLG systems are already in widespread use in both enterprise and consumer products, such as [business intelligence (BI)](https://www.ibm.com/think/topics/business-intelligence) tools and [chatbots](https://www.ibm.com/think/topics/chatbots). Voice assistants communicate with users through NLG.   

 Business leaders use NLG to transform complex data into generated text to distill key insights. Whenever an AI model generates output in human language, that’s NLG at work.

## Types of NLG

The 2 primary types of NLG are extractive and abstractive:

- **Extractive NLG** pulls exact words and phrases directly from the source text. It is used in cases where specific wording is critical, such as with legal documents. Compared to abstractive NLG, extractive NLG is simpler because it copies from source documents rather than output new content.

- **Abstractive NLG** creates novel outputs based on source documents, paraphrasing and generating new content. It is a more complex process that requires more advanced models, such as transformers. Where extractive NLG is preferred in technical settings, abstractive NLG shines in more creative applications.

## How NLG works

NLG works by progressing through a multistage process to refine structured and unstructured data inputs and generate natural language outputs. As described by computer scientist Ehud Reiter,<sup>[1](#footnotes1)</sup> the stages in the typical NLG process are:

- **Signal analysis:** The NLG system determines which input data is needed for the final output. In the signal or data analysis stage, pattern recognition identifies the subject matter of the content and the relationships between topics. Input data includes user prompts, database content and unstructured language content such as PDFs, documents and spoken language recordings. [Entity recognition](https://www.ibm.com/think/topics/named-entity-recognition) helps NLP systems understand what is being discussed.

- **Data interpretation:** NLP models generate insights from the results of the [data analytics](https://www.ibm.com/think/topics/big-data-analytics) stage. If the data is already preprocessed with the insights available, then this step is bypassed. NLP systems identify parts of speech and use NLU to assess syntax and semantics, creating an understanding of meaning.

- **Document planning:** This stage identifies which information to communicate and how to format it. The NLG system determines its approach for the final output, depending on the data available to it and the user prompt.

- **Microplanning:** After settling on the content and format for the communication, the NLG system plans the sentence and paragraph structure for the final output.

- **Surface realization:** The NLG system puts its plan into action and generates natural language outputs according to the results of the previous steps.

### NLG vs. NLP

NLG is part of the computer science discipline of natural language processing (NLP): the use of machine learning (ML) models to understand and work with human language.  

 NLG is the portion of NLP that is concerned with content generation, specifically with outputting novel written or spoken language. For example, [conversational AI](https://www.ibm.com/think/topics/conversational-ai) chatbots use NLG to respond to user inputs in real time.

NLP converts natural language inputs into data, and NLG uses data to generate natural language outputs.

NLP is part of the field of computational linguistics: the study of how computers analyze and understand human language. NLP is computational linguistics in practice.  

 The development of deep learning and [large language models (LLMs)](https://www.ibm.com/think/topics/large-language-models) made it possible for advancements in NLP to power the many generative AI applications that handle content creation.

### NLG vs. NLU

Natural language understanding (NLU) is another subset of NLP. Rather than focusing on grammatical and linguistic meaning, NLU attempts to grasp human language holistically. NLU uses semantic and syntactic analysis to fully and contextually comprehend natural language inputs, including emotion, sentiment and intent.

NLU enables computers to understand natural language inputs in a way that is closer to how humans do. When people talk to each other, they process more than the definitions of the words being used. They can naturally understand the deeper meaning behind a speaker’s literal words.

When a software application offers [predictive text](https://www.ibm.com/think/topics/predictive-ai) options, it uses NLU to understand the user’s intent, then applies NLG to finish the sentence. [NLP, NLU and NLG](https://www.ibm.com/think/topics/nlp-vs-nlu-vs-nlg) work together to help computers communicate with users.

## NLG models and methodologies

Many NLG systems use advanced AI models such as transformers to create novel texts from training data and user inputs.   

 However, before these models were developed, NLG was made possible by other means. NLG models and techniques include:

- Templates

- Rule-based systems

- Statistical [machine learning algorithms](https://www.ibm.com/think/topics/machine-learning-algorithms)

- [Deep learning](https://www.ibm.com/think/topics/deep-learning) models

- Transformers

### Templates

Template-based systems use predefined sentence templates with variables for input data. Templates are one of the earliest and simplest types of NLG, appropriate for contexts where sentence and document structures are consistent. However, template-based systems cannot adapt outside of their predefined use cases.

An example template might be: In [month],[year], our [location] store sold [amount] units of [item]*.*

While this template excels in reporting location-based sales, one could not apply it to generate a cooking recipe.

### Rule-based systems

Rule-based systems generate text according to a series of predefined rules and logic. Early rule-based systems were created to mirror the way domain experts spoke or wrote. Programmers would interview experts, then create corresponding rules for [text generation](https://www.ibm.com/think/topics/text-generation).

“If-then” systems are a common example of rule-based programming. For instance, NLG software for weather forecasts might be instructed to describe the weather as “below freezing” if the temperature is below 32 degrees Fahrenheit or 0 degrees Celsius.

### Statistical machine learning algorithms

Statistical [machine learning](https://www.ibm.com/think/topics/machine-learning) algorithms, such as hidden Markov chains, identify patterns in large [datasets](https://www.ibm.com/think/topics/dataset) to make predictions and decisions with new data.   

 They generate new instances based on the current instance. For NLG, Markov chains and other statistical models generate words that are likely to follow each other.

Statistical models are more flexible than templates and rule-based systems but require large quantities of training data.

### Deep learning models

Deep learning models are an advancement in AI technology over statistical algorithms and can generate more natural-seeming text. [Recurrent neural networks (RNNs)](https://www.ibm.com/think/topics/recurrent-neural-networks) are an example of deep learning models applied to NLG.   

 RNNs process sequential data, such as the words in a sentence, and can transfer knowledge, such as with machine translation.

### Transformers

Transformer model architecture powers some of the most effective NLG technology available. Transformer-based models such as [GPT](https://www.ibm.com/think/topics/gpt) and BERT use self-attention mechanisms to capture long-range dependencies in input sequences for greater contextual understanding.   

 ChatGPT, [Claude](https://www.ibm.com/think/topics/claude-ai) and other transformer-powered chatbots can generate realistic human language outputs.

## Natural language generation use cases

NLG is found across the generative AI landscape, wherever AI is used to communicate directly with humans in natural language. From Siri to [sentiment analysis](https://www.ibm.com/think/topics/sentiment-analysis), NLG use cases include:

- **Voice assistants:** Siri, Alexa and other voice assistants use NLG to respond to user requests with spoken language. They also use NLP and NLU for [speech recognition](https://www.ibm.com/think/topics/speech-recognition) to understand what users want.

- **Virtual assistants:** Chatbots and virtual assistants use NLG to [automate](https://www.ibm.com/think/topics/automation) customer interactions. Many organizations use virtual assistants to field initial customer service inquiries before escalating to human representatives when necessary. [Virtual agents](https://www.ibm.com/think/topics/virtual-agent) also communicate with users through NLG.

- **Machine translation:** [Machine translation](https://www.ibm.com/think/topics/machine-translation) is the use of machine learning models to automatically translate between languages. NLG systems handle the output generation and streamline the time-consuming translation process. Human translators and localization experts can then verify and edit the outputs as needed.

- **Data summaries and reporting:** NLG systems convert complex data into easily comprehensible summaries and outlines. Streamlining the aggregation and summarization of articles and reports makes forecasting more efficient. Business leaders use NLG-powered BI tools for [data-driven decision-making](https://www.ibm.com/think/topics/data-driven-decision-making). Other enterprises use AI and NLG to create this content for their customers.

- **Content generation:** Anytime a generative AI model outputs natural language content, that’s NLG at work. Businesses can choose to use NLG to automate product descriptions, email marketing campaigns, social media posts and other types of short-form content.

- **Sentiment analysis:** NLG systems create [text summaries](https://www.ibm.com/think/topics/text-summarization) and reports based on audience feedback and communications. Enterprises can pull user-generated content from product reviews, social media platforms, forum posts and other online locations, then use NLP and NLG to identify how users feel.

## Footnotes

<sup>1</sup> [Natural Language Generation](https://arxiv.org/html/2502.14437v1#Ch1.S1), Ehud Reiter, Springer, 2024.
