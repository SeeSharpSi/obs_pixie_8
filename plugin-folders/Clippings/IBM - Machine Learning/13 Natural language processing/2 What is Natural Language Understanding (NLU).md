---
title: What is natural language understanding (NLU)?
source: https://www.ibm.com/think/topics/natural-language-understanding
author:
- '[[Ivan Belcic]]'
- '[[Cole Stryker]]'
published: 2025-02-25
created: 2026-08-31
description: "Natural language understanding (NLU) is a subset of artificial intelligence (AI) that uses semantic and syntactic analysis to enable computers to understand human-language inputs."
---

## What is natural language understanding (NLU)?

Natural language understanding (NLU) is a subset of [artificial intelligence](https://www.ibm.com/think/topics/artificial-intelligence) (AI) that uses semantic and syntactic analysis to enable computers to understand human-language inputs. NLU aims to holistically comprehend intent, meaning and context, rather than focusing on the meaning of individual words.

NLU enables organizations to distill insights from unstructured data, such as spoken language or written inputs in natural language. Through NLU, computers can also communicate with untrained users without the use of programming languages.

Because human language is so nuanced, complex and full of ambiguities, NLU is a demanding [machine learning](https://www.ibm.com/think/topics/machine-learning) challenge for computer scientists and engineers working with [large language models](https://www.ibm.com/think/topics/large-language-models) (LLMs). NLU systems make it possible for computers to grasp the intricacies of written and spoken language—subtle nuances, complex sentence structures, potentially confusing word usages, slang and dialects and others.

Due to the rise of [generative AI](https://www.ibm.com/think/topics/generative-ai) and its use in consumer [chatbots](https://www.ibm.com/think/topics/chatbots), [question-answering](https://www.ibm.com/think/topics/question-answering), machine translation and other applications, NLU receives considerable commercial investment. Without NLU, interactive chatbots such as ChatGPT might not exist—NLU is why generative AI chatbots can hold a conversation with users that feels realistic and natural.

### Natural language understanding versus natural language processing (NLP)

NLU is a type of [natural language processing](https://www.ibm.com/think/topics/natural-language-processing) (NLP), the broader field of enabling computers to understand and communicate in human language. In addition to NLU’s focus on understanding meaning, NLP tasks cover the mapping of linguistic elements such as syntax, word definitions and parts of speech.

Before the development of NLP, users would communicate with computers through programming languages such as Python and C++. While coding still uses programming languages, no-code software applications allow users to directly instruct computers with natural language.

NLP emerged from the computer science field of computational linguistics, which uses computers to analyze language. The introduction of machine learning algorithms and deep learning models allowed computers to fulfill language-related tasks, such as [speech recognition](https://www.ibm.com/think/topics/speech-recognition) and content generation.

### NLU versus natural language generation (NLG)

Natural language generation (NLG) is how computers automatically generate content in human language—such as when a chatbot delivers a text summary or holds a conversation with a user. NLG is typically paired with NLU. A [deep learning](https://www.ibm.com/think/topics/deep-learning) model receives a natural language input, converts it to usable data with NLP, including NLU, then generates a response with NLG that the user can understand.

[NLP, NLG and NLU](https://www.ibm.com/think/topics/nlp-vs-nlu-vs-nlg) are all related, with NLP as the overarching discipline containing the latter two. NLG is what allows chatbots such as ChatGPT, contemporary customer support bots and voice assistants such as Amazon’s Alexa to appear humanlike when interacting with users.

## How does natural language understanding work?

Natural language understanding works by using [machine learning algorithms](https://www.ibm.com/think/topics/machine-learning-algorithms) to transform unstructured speech or written language into a structured data model representing its content and meaning. NLU systems apply syntactic analysis to understand the words in a sentence and semantic analysis to process the meaning of what is being said.

[Supervised learning](https://www.ibm.com/think/topics/supervised-learning) techniques for NLU algorithms involve feeding the algorithm labeled training data. This method explicitly guides the algorithm to understand linguistic nuances—for example, if using the homonym *mean* in a statistical context as opposed to a personality assessment.

[Unsupervised learning](https://www.ibm.com/think/topics/unsupervised-learning) techniques show algorithms to massive unlabeled datasets with the goal of having the algorithm discover the underlying relationships and patterns. Contemporary NLU models are typically trained with a combination of supervised and unsupervised methods.

The primary mechanisms that make NLU possible include:

- Tokenization and embedding

- Named entity recognition (NER)

- Intent recognition

### Tokenization and embedding

[Tokenization](https://www.ibm.com/think/topics/tokenization) in NLU is the use of machine learning algorithms to segment unstructured text into smaller parts that can then be further analyzed. Each resulting segment is known as a token. [Embedding](https://www.ibm.com/think/topics/embedding) algorithms convert each token into a numerical representation that is then plotted onto a three-dimensional vector space to map out the relationships between tokens.

Contemporary NLU typically uses transformer-based models, such as [GPT](https://www.ibm.com/think/topics/gpt), because they excel at capturing dependencies between tokens. Dependencies are long-range relationships between distant tokens in a sequence. Correctly capturing dependencies makes it possible for computers to maintain contextual understanding across lengthy input sequences.

### Named entity recognition (NER)

[Named entity recognition](https://www.ibm.com/think/topics/named-entity-recognition) (NER) is an [information extraction](https://www.ibm.com/think/topics/information-extraction) technique that identifies and classifies named entities, or real-world objects, in text data. Named entities can be physical, such as people, places and items, or abstract, such as a date or a person’s age and phone number.

### Intent recognition

Intent recognition tells an NLU algorithm what a user wants to do. Search engines use intent recognition to deliver results that are relevant to the corresponding query not only in factual terms, but that give the user the information they want.

For example, a search for “chicken tikka masala” likely yields a list of recipes. But what if the user instead types “chicken tikka masala near me?” Intent recognition tells the search engine that the user doesn’t want to cook chicken tikka masala themselves, but to instead enjoy the dish at a local restaurant.

## Natural language understanding use cases

NLU applications span a wide range of use cases in which it is necessary for computers to either communicate directly with humans or process human-language data. Natural language understanding use cases include:

- Sentiment analysis

- User intent

- Machine translation

- Customer support

- Speech recognition

- Text classification

- Virtual agents

### Sentiment analysis

[Sentiment analysis](https://www.ibm.com/think/topics/sentiment-analysis) is the application of machine learning models to identify mood and emotion in a piece of content. For example, researchers can use sentiment analysis on social media posts and user reviews to identify how users feel about a brand. The information they learn can be applied toward future product development, pricing adjustments and other changes.

### User intent

Search engines use NLU to provide more relevant answers. The same principle applies to websites with search functions—for example, an e-commerce website can potentially increase sales by showing the most relevant items in response to user searches. The optimization of search results is likely to result in more users continuing to use the search engine or making a purchase.

### Machine translation

[Machine translation](https://www.ibm.com/think/topics/machine-translation) is the use of computers to perform [automated](https://www.ibm.com/think/topics/automation) language translation. For example, imagine a mobile application that translates between spoken English and Spanish in real time. A Spanish-speaking user might use such an app to both converse with English speakers while also understanding anything being said in English around them.

### Customer support

Customer support chatbots have grown more sophisticated as generative AI improves. NLU enables chatbots to engage in humanlike conversations with users, and organizations have increasingly deployed them to field customer service queries and answer common questions. Meanwhile, human personnel round out the [customer experience](https://www.ibm.com/think/topics/customer-experience) interface by fielding issues too complex for AI to handle.

The use of customer support chatbots is one example of how advancements in AI, including NLU, have streamlined [workflows](https://www.ibm.com/think/topics/workflow) and led to more [workflow automation](https://www.ibm.com/think/topics/workflow-automation).

### Speech recognition

NLU systems help users communicate verbally with software, such as the automated routing systems one encounters when calling large corporations. Rather than repeatedly press *0* until the system passes the call to a human, callers can instead say, “speak to a human.” With NLU at work, the software can convert the user’s spoken request to structured data in real time and transfer the call.

### Virtual agents

Organizations have begun deploying [virtual agents](https://www.ibm.com/think/topics/virtual-agent) as part of the greater customer experience. These models can interface directly with users—using NLU and NLG to facilitate the interaction—and act on behalf of users and organizations. Virtual assistants such as Alexa and Siri also use NLU to fulfill user requests.
