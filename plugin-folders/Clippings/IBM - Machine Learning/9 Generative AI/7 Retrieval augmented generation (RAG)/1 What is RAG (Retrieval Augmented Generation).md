---
title: What is retrieval augmented generation (RAG)?
source: https://www.ibm.com/think/topics/retrieval-augmented-generation
author:
- '[[Ivan Belcic]]'
published: 2024-10-31
created: 2026-08-31
description: "Retrieval augmented generation (RAG) is an architecture for optimizing the performance of an artificial intelligence (AI) model by connecting it with external knowledge bases."
---

## What is retrieval augmented generation (RAG)?

Retrieval augmented generation, or RAG, is an architecture for optimizing the performance of an [artificial intelligence (AI)](https://www.ibm.com/think/topics/artificial-intelligence) model by connecting it with external knowledge bases. RAG helps [large language models (LLMs)](https://www.ibm.com/think/topics/large-language-models) deliver more relevant responses at a higher quality.

[Generative AI](https://www.ibm.com/think/topics/generative-ai) (gen AI) models are trained on large datasets and refer to this information to generate outputs. However, training datasets are finite and limited to the information the AI developer can access—public domain works, internet articles, social media content and other publicly accessible data.

RAG allows generative AI models to access additional external knowledge bases, such as internal organizational data, scholarly journals and specialized datasets. By integrating relevant information into the generation process, [chatbots](https://www.ibm.com/think/topics/chatbots) and other [natural language processing (NLP)](https://www.ibm.com/think/topics/natural-language-processing) tools can create more accurate domain-specific content without needing further training.

## What are the benefits of RAG?

RAG empowers organizations to avoid high retraining costs when adapting generative AI models to domain-specific use cases. Enterprises can use RAG to complete gaps in a [machine learning](https://www.ibm.com/think/topics/machine-learning) model’s knowledge base so it can provide better answers.

The primary benefits of RAG include:

- Cost-efficient AI implementation and [AI scaling](https://www.ibm.com/think/topics/ai-scaling)

- Access to current domain-specific data

- Lower risk of [AI hallucinations](https://www.ibm.com/think/topics/ai-hallucinations)

- Increased user trust

- Expanded use cases

- Enhanced developer control and model maintenance

- Greater data security

### Cost-efficient AI implementation and AI scaling

When implementing AI, most organizations first select a foundation model: the [deep-learning](https://www.ibm.com/think/topics/deep-learning) models that serve as the basis for the development of more advanced versions. Foundation models typically have generalized knowledge bases populated with publicly available training data, such as internet content available at the time of training.

Retraining a foundation model or [fine-tuning](https://www.ibm.com/think/topics/fine-tuning) it—where a foundation model is further trained on new data in a smaller, domain-specific dataset—is computationally expensive and resource-intensive. The model adjusts some or all of its parameters to adjust its performance to the new specialized data.

With RAG, enterprises can use internal, authoritative data sources and gain similar model performance increases without retraining. Enterprises can scale their implementation of AI applications as needed while mitigating cost and resource requirement increases.

### Access to current and domain-specific data

Generative AI models have a *knowledge cutoff,* the point at which their training data was last updated. As a model ages further past its knowledge cutoff, it loses relevance over time. RAG systems connect models with supplemental external data in real-time and incorporate up-to-date information into generated responses.

Enterprises use RAG to equip models with specific information such as proprietary customer data, authoritative research and other relevant documents.

RAG models can also connect to the internet with [application programming interfaces (APIs)](https://www.ibm.com/think/topics/api) and gain access to real-time social media feeds and consumer reviews for a better understanding of market sentiment. Meanwhile, access to breaking news and search engines can lead to more accurate responses as models incorporate the retrieved information into the text-generation process.

### Lower risk of AI hallucinations

Generative AI models such as OpenAI’s [GPT](https://www.ibm.com/think/topics/gpt#:~:text=GPT%20models%20work%20by%20analyzing,based%20on%20all%20previous%20words.) work by detecting patterns in their data, then using those patterns to predict the most likely outcomes to user inputs. Sometimes models detect patterns that don’t exist. A hallucination or confabulation happens when models present incorrect or made-up information as though it is factual.

RAG anchors LLMs in specific knowledge backed by factual, authoritative and current data. Compared to a generative model operating only on its training data, RAG models tend to provide more accurate answers within the contexts of their external data. While RAG can reduce the risk of hallucinations, it cannot make a model error-proof.

### Increased user trust

[Chatbots](https://www.ibm.com/think/topics/chatbots), a common generative AI implementation, answer questions posed by human users. For a chatbot such as ChatGPT to be successful, users need to view its output as trustworthy. RAG models can include citations to the knowledge sources in their external data as part of their responses.

When RAG models cite their sources, human users can verify those outputs to confirm accuracy while consulting the cited works for follow-up clarification and additional information. Corporate data storage is often a complex and siloed maze. RAG responses with citations point users directly toward the materials they need.

### Expanded use cases

Access to more data means that one model can handle a wider range of prompts. Enterprises can optimize models and gain more value from them by broadening their knowledge bases, in turn expanding the contexts in which those models generate reliable results.

By combining generative AI with retrieval systems, RAG models can retrieve and integrate information from multiple data sources in response to complex queries.

### Enhanced developer control and model maintenance

Modern organizations constantly process massive quantities of data, from order inputs to market projections to employee turnover and more. Effective [data pipeline](https://www.ibm.com/think/topics/data-pipeline) construction and data storage is paramount for strong RAG implementation.

At the same time, developers and [data scientists](https://www.ibm.com/think/topics/data-science) can tweak the data sources to which models have access at any time. Repositioning a model from one task to another becomes a task of adjusting its external knowledge sources as opposed to fine-tuning or retraining. If fine-tuning is needed, developers can prioritize that work instead of managing the model’s data sources.

### Greater data security

Because RAG connects a model to external knowledge sources rather than incorporating that knowledge into the model’s training data, it maintains a divide between the model and that external knowledge. Enterprises can use RAG to preserve first-party data while simultaneously granting models access to it—access that can be revoked at any time.

However, enterprises must be vigilant to maintain the security of the external databases themselves. RAG uses [vector databases](https://www.ibm.com/think/topics/vector-database), which use [embeddings](https://www.ibm.com/think/topics/embedding) to convert data points to numerical representations. If these databases are breached, attackers can reverse the [vector embedding](https://www.ibm.com/think/topics/vector-embedding) process and access the original data, especially if the vector database is unencrypted.

## RAG use cases

RAG systems essentially enable users to query databases with conversational language. The data-powered [question-answering](https://research.ibm.com/blog/retrieval-augmented-generation-RAG?mhsrc=ibmsearch_a&mhq=question-answering%20abilities%20of%20RAG) abilities of RAG systems have been applied across a range of use cases, including:

- Specialized chatbots and virtual assistants
- Research
- Content generation
- Market analysis and product development
- Knowledge engines
- Recommendation services

### Specialized chatbots and virtual assistants

Enterprises wanting to [automate](https://www.ibm.com/think/topics/automation) customer support might find that their AI models lack the specialized knowledge needed to adequately assist customers. RAG AI systems plug models into internal data to equip customer support chatbots with the latest knowledge about a company’s products, services and policies.

The same principle applies to AI avatars and personal assistants. Connecting the underlying model with the user’s personal data and referring to previous interactions provides a more customized user experience.

### Research

Able to read internal documents and interface with search engines, RAG models excel at research. Financial analysts can generate client-specific reports with up-to-date market information and prior investment activity, while medical professionals can engage with patient and institutional records.

### Content generation

The ability of RAG models to cite authoritative sources can lead to more reliable content generation. While all generative AI models can hallucinate, RAG makes it easier for users to verify outputs for accuracy.

### Market analysis and product development

Business leaders can consult social media trends, competitor activity, sector-relevant breaking news and other online sources to better inform business decisions. Meanwhile, product managers can reference customer feedback and user behaviors when considering future development choices.

### Knowledge engines

RAG systems can empower employees with internal company information. Streamlined onboarding processes, faster HR support and on-demand guidance for employees in the field are just a few ways businesses can use RAG to enhance job performance.

### Recommendation services

By analyzing previous user behavior and comparing that with current offerings, RAG systems power more accurate recommendation services. An e-commerce platform and content delivery service can both use RAG to keep customers engaged and spending.

## How does RAG work?

RAG works by combining information retrieval models with generative AI models to produce more authoritative content. RAG systems query a knowledge base and add more context to a user prompt before generating a response.

Standard LLMs source information from their training datasets. RAG adds an information retrieval component to the AI workflow, gathering relevant information and feeding that to the generative AI model to enhance response quality and utility.

RAG systems follow a five-stage process:

![Diagram of connected nodes with arrows, showing blue and black circles linked by directional paths on a white background.](https://assets.ibm.com/is/image/ibm/retrieval-augmented-generation?ts=1784923847001&dpr=off)

1. The user submits a prompt.
2. The information **retrieval** model queries the knowledge base for relevant data.
3. Relevant information is returned from the knowledge base to the integration layer.
4. The RAG system engineers an **augmented** prompt to the LLM with enhanced context from the retrieved data.
5. The LLM **generates** an output and returns an output to the user.

This process showcases how RAG gets its name. The RAG system *retrieves* data from the knowledge base, *augments* the prompt with added context and *generates* a response.

## Components of a RAG system

RAG systems contain four primary components:

- The **knowledge base**: The external data repository for the system.

- The **retriever**: An AI model that searches the knowledge base for relevant data.

- The **integration layer**: The portion of the RAG architecture that coordinates its overall functioning.

- The **generator**: A generative AI model that creates an output based on the user query and retrieved data.

Other components might include a *ranker*, which ranks retrieved data based on relevance, and an *output handler*, which formats the generated response for the user.

### The knowledge base

The first stage in constructing a RAG system is creating a queryable knowledge base. The external data repository can contain data from countless sources: PDFs, documents, guides, websites, audio files and more. Much of this will be [unstructured](https://www.ibm.com/think/topics/structured-vs-unstructured-data) data, which means that it hasn’t yet been labeled.

RAG systems use a process called embedding to transform data into numerical representations called vectors. The embedding model vectorizes the data in a multidimensional mathematical space, arranging the data points by similarity. Data points judged to be closer in relevance to each other are placed closely together.

Knowledge bases must be continually updated to maintain the RAG system’s quality and relevance.

LLM inputs are limited to the context window of the model: the amount of data it can process without losing context. *Chunking* a document into smaller sizes helps ensure that the resulting embeddings will not overwhelm the context window of the LLM in the RAG system.

Chunk size is an important hyperparameter for the RAG system. When chunks are too large, the data points can become too general and fail to correspond directly to potential user queries. But if chunks are too small, the data points can lose semantic coherency.

### The retriever

Vectorizing the data prepares the knowledge base for semantic [vector search](https://www.ibm.com/think/topics/vector-search), a technique that identifies points in the database that are similar to the user’s query. Semantic search [machine learning algorithms](https://www.ibm.com/think/topics/machine-learning-algorithms) can query massive databases and quickly identify relevant information, reducing latency as compared to traditional keyword searches.

The information retrieval model transforms the user’s query into an embedding and then searches the knowledge base for similar embeddings. Then, its findings are returned from the knowledge base.

### The integration layer

The integration layer is the center of the RAG architecture, coordinating the processes and passing data around the network. With the added data from the knowledge base, the RAG system creates a new prompt for the LLM component. This prompt consists of the original user query plus the enhanced context returned by the retrieval model.

RAG systems employ various [prompt engineering](https://www.ibm.com/think/topics/prompt-engineering) techniques to automate effective prompt creation and help the LLM return the best possible response. Meanwhile, LLM orchestration frameworks such as the open source [LangChain](https://www.ibm.com/think/topics/langchain) and [LlamaIndex](https://www.ibm.com/think/topics/llamaindex) or [IBM® watsonx Orchestrate™](https://www.ibm.com/products/watsonx-orchestrate) govern the overall functioning of an AI system.

### The generator

The generator creates an output based on the augmented prompt fed to it by the integration layer. The prompt synthesizes the user input with the retrieved data and instructs the generator to consider this data in its response. Generators are typically pretrained language models, such as GPT, [Claude](https://www.ibm.com/think/topics/claude-ai) or [Llama](https://www.ibm.com/think/topics/llama-2).

## What is the difference between RAG and fine-tuning?

The [difference between RAG and fine-tuning](https://www.ibm.com/think/topics/rag-vs-fine-tuning) is that RAG lets an LLM query an external data source while fine-tuning trains an LLM on domain-specific data. Both have the same general goal: to make an LLM perform better in a specified domain.

RAG and fine-tuning are often contrasted but can be used in tandem. Fine-tuning increases a model’s familiarity with the intended domain and output requirements, while RAG assists the model in generating relevant, high-quality outputs.
