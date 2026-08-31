---
title: What are small language models?
source: https://www.ibm.com/think/topics/small-language-models
author:
- '[[Rina Diane Caballar]]'
- '[[Cole Stryker]]'
published: 2024-11-05
created: 2026-08-31
description: "Small language models (SLMs) are artificial intelligence (AI) models capable of processing, understanding and generating natural language content. As their name implies, SLMs are smaller in scale and scope than large language models (LLMs)."
---

## What are small language models?

Small language models (SLMs) are [artificial intelligence (AI)](https://www.ibm.com/think/topics/artificial-intelligence?) models capable of processing, understanding and generating natural language content. As their name implies, SLMs are smaller in scale and scope than [large language models (LLMs)](https://www.ibm.com/think/topics/large-language-models?).

In terms of size, SLM parameters range from a few million to a few billion, as opposed to LLMs with hundreds of billions or even trillions of parameters. Parameters are internal variables, such as weights and biases, that a model learns during training. These parameters influence how a [machine learning](https://www.ibm.com/think/topics/machine-learning?) model behaves and performs.

Small language models are more compact and efficient than their large model counterparts. As such, SLMs require less memory and computational power, making them ideal for resource-constrained environments such as [edge devices](https://www.ibm.com/think/topics/edge-computing?) and mobile apps, or even for scenarios where [AI inferencing](https://research.ibm.com/blog/AI-inference-explained)—when a model generates a response to a user’s query—must be done offline without a data network.

## How small language models work

LLMs serve as the base for SLMs. Like large language models, small language models employ a [neural network](https://www.ibm.com/think/topics/neural-networks?)-based architecture known as the [transformer model](https://www.ibm.com/think/topics/transformer-model?). Transformers have become fundamental in [natural language processing (NLP)](https://www.ibm.com/think/topics/natural-language-processing?) and act as the building blocks of models like the [generative pre-trained transformer (GPT)](https://www.ibm.com/think/topics/gpt?).

Here’s a brief overview of the transformer architecture:

- Encoders transform input sequences into numerical representations called [embeddings](https://www.ibm.com/think/topics/embedding?) that capture the semantics and position of tokens in the input sequence.
- A self-attention mechanism allows transformers to “focus their attention” on the most important tokens in the input sequence, regardless of their position.
- Decoders use this self-attention mechanism and the encoders’ embeddings to generate the most statistically probable output sequence.

### Model compression

Model compression techniques are applied to build a leaner model from a larger one. Compressing a model entails reducing its size while still retaining as much of its accuracy as possible. Here are some common model compression methods:

- Pruning
- Quantization
- Low-rank factorization
- Knowledge distillation

### Pruning

Pruning removes less crucial, redundant or unnecessary parameters from a neural network. Parameters that are usually pruned include the numerical weights corresponding to the connections between neurons (in this case, the weights will be set to 0), the neurons themselves or the layers in a neural network.

Pruned models will often need to be [fine-tuned](https://www.ibm.com/think/topics/fine-tuning?) after pruning to make up for any loss in accuracy. And it’s vital to know when enough parameters have been pruned, as overpruning can degrade a model’s performance.

### Quantization

[Quantization](https://www.ibm.com/think/topics/quantization?) converts high-precision data to lower-precision data. For instance, model weights and activation values (a number between 0 and 1 assigned to the neurons in a neural network) can be represented as 8-bit integers instead of 32-bit floating point numbers. Quantization can lighten the computational load and speed up inferencing.

Quantization can be incorporated into model training (known as quantization-aware training or QAT) or done after training (called post-training quantization or PTQ). PTQ doesn’t require as much computational power and training data as QAT, but QAT can produce a more accurate model.

### Low-rank factorization

Low-rank factorization decomposes a large matrix of weights into a smaller, lower-rank matrix. This more compact approximation can result in fewer parameters, decrease the number of computations and simplify complex matrix operations.

However, low-rank factorization can be computationally intensive and more difficult to implement. Like pruning, the factorized network will require fine-tuning to recover any accuracy loss.

### Knowledge distillation

[Knowledge distillation](https://www.ibm.com/think/topics/knowledge-distillation?) involves transferring the learnings of a pretrained “teacher model” to a “student model.” The student model is trained to not only match the teacher model’s predictions but also mimic its underlying process of reasoning. As such, a larger model’s knowledge is essentially “distilled” into a smaller one.

Knowledge distillation is a popular approach for many SLMs. The offline distillation scheme is typically used, wherein the teacher model’s weights are frozen and cannot be changed during the distillation process.

## Examples of small language models

While larger models remain a technology of choice for many enterprises, smaller models are quickly gaining ground. Here are some examples of popular SLMs:

- DistilBERT
- Gemma
- GPT-4o mini
- Granite
- Llama
- Ministral
- Phi

### DistilBERT

DistilBERT is a lighter version of Google’s pioneering BERT [foundation model](https://www.ibm.com/think/topics/foundation-models?). It uses knowledge distillation to make it 40% smaller and 60% faster than its predecessor, while still retaining 97% of BERT’s natural language understanding capabilities.<sup>1</sup>

Other scaled-down versions of BERT include tiny at 4.4 million parameters, mini at 11.3 million parameters, small at 29.1 million parameters and medium at 41.7 million parameters.<sup>2</sup> Meanwhile, MobileBERT is tailored for mobile devices.<sup>3</sup>

### Gemma

Gemma is crafted and distilled from the same technology as [Google’s Gemini](https://www.ibm.com/think/topics/google-gemini?) LLM and is available in 2, 7 and 9 billion parameter sizes.<sup>4</sup> Gemma is available through Google AI Studio and the Kaggle and Hugging Face platforms.

Gemini also has more lightweight variants in the form of Gemini 1.5 Flash-8B and Gemini 1.0 Nano designed to operate on mobile devices.<sup>5</sup>

### GPT-4o mini

GPT-4o mini is part of OpenAI’s GPT-4 family of [AI models](https://www.ibm.com/think/topics/ai-model?), which powers the ChatGPT generative AI chatbot. GPT-4o mini is a smaller, cost-effective variant of [GPT-4o](https://www.ibm.com/think/topics/gpt-4o). It has [multimodal](https://www.ibm.com/think/topics/multimodal-ai) capabilities, accepting both text and image inputs and producing text outputs.

ChatGPT Free, Plus, Team and Enterprise users can access GPT-4o mini, which replaces GPT-3.5. Developers can access GPT-4o mini through various [application programming interfaces (APIs)](https://www.ibm.com/think/topics/api?).

### Granite

[Granite](https://www.ibm.com/granite)<sup>TM</sup> is the IBM® flagship series of LLM [foundation models](https://www.ibm.com/products/watsonx-ai/foundation-models). The Granite 3.0 collection includes base pretrained and [instruction-tuned](https://www.ibm.com/think/topics/instruction-tuning?) models with 2 and 8 billion parameters. Granite 3.0 also has [mixture of experts (MoE)](https://www.ibm.com/think/topics/mixture-of-experts?) SLMs for minimum latency and an optimized variant to accelerate model inference speed.

These [open-source](https://www.ibm.com/think/topics/open-source?) models excel not only in language-specific tasks but also in enterprise domains such as [cybersecurity](https://www.ibm.com/think/topics/cybersecurity?), as [AI agents](https://www.ibm.com/think/topics/ai-agents) using tool or function calling to autonomously perform tasks, and in [retrieval-augmented generation (RAG)](https://research.ibm.com/blog/retrieval-augmented-generation-RAG) tasks that involve retrieving facts from an external knowledge base to ground models on the most accurate, up-to-date information.

Granite 3.0 models are available for commercial use on products in the [IBM watsonx™ portfolio](https://www.ibm.com/products/watsonx) and through Google Vertex AI, Hugging Face, NVIDIA (as NIM microservices), Ollama and Replicate.

### Llama

Llama is Meta’s line of open source language models. Llama 3.2 comes in 1 and 3 billion parameter sizes,<sup>6</sup> even smaller than the earlier 7-billion-parameter version of [Llama 2](https://www.ibm.com/think/topics/llama-2?).<sup>7</sup>

The quantized versions of these multilingual text-only models have been cut down to more than half their size and are 2 to 3 times faster.<sup>6</sup> These SLMs can be accessed through Meta, Hugging Face and Kaggle.

### Ministral

Les Ministraux is a group of SLMs from [Mistral AI](https://www.ibm.com/think/topics/mistral-ai?). Ministral 3B is the company’s smallest model at 3 billion parameters, while Ministral 8B at 8 billion parameters is the successor to Mistral 7B, 1 of the first AI models that Mistral AI released. Both models can be accessed through Mistral.<sup>8</sup>

Ministral 8B outperforms Mistral 7B in benchmarks assessing knowledge, common sense, math and multilingual skills. For swift inference, Ministral 8B uses sliding window attention, a dynamic mechanism for focusing on certain fixed-size “windows” of input sequences, allowing models to concentrate on only a few words at a time.<sup>8</sup>

### Phi

Phi is a suite of small language models from Microsoft. Phi-2 has 2.7 billion parameters, while Phi-3-mini has 3.8 billion parameters.<sup>9</sup>

Phi-3-mini can analyze and reason over large text content due to its long context window, which is the maximum amount of text a model can consider. According to Microsoft, Phi-3-small, its 7-billion-parameter SLM, will be available in the future. Phi-3-mini can be accessed on Microsoft Azure AI Studio, Hugging Face and Ollama.<sup>9</sup>

## Combining LLMs and SLMs

Advances in AI development have led to optimization approaches that maximize the joint power of LLMs and SLMs:

**Hybrid AI pattern:** A [hybrid AI model](https://www.ibm.com/think/insights/bigger-isnt-always-better-how-hybrid-ai-pattern-enables-smaller-language-models) can have smaller models running on premises and accessing LLMs in the public cloud when a larger corpus of data is required to respond to a prompt.

**Intelligent routing:** Intelligent routing can be applied to more efficiently distribute AI workloads. A routing module can be created to accept queries, evaluate them and choose the most appropriate model to direct queries to. Small language models can handle basic requests, while large language models can tackle more complicated ones.

## Benefits of small language models

[Bigger isn’t always better](https://www.ibm.com/think/insights/are-bigger-language-models-better), and what SLMs lack in size, they make up for through these advantages:

**Accessibility:** Researchers, AI developers and other individuals can explore and experiment with language models without having to invest in multiple [GPUs (graphics processing units)](https://www.ibm.com/think/topics/gpu?) or other specialized equipment.

**Efficiency:** The leanness of SLMs makes them less resource-intensive, allowing for swift training and deployment.

**Effective performance:** This efficiency doesn’t come at the cost of performance. Small models can have comparable or even better performance than their large model equivalents. For instance, GPT-4o mini surpasses GPT-3.5 Turbo in language understanding, question answering, reasoning, mathematical reasoning and code generation [LLM benchmarks](https://www.ibm.com/think/topics/llm-benchmarks).<sup>10</sup> GPT-4o mini’s performance is also close to its bigger GPT-4o sibling.<sup>10</sup>

**Greater privacy and security control:** Because of their smaller size, SLMs can be deployed in private [cloud computing](https://www.ibm.com/think/topics/cloud-computing?) environments or on premises, allowing for improved data protection and better management and mitigation of cybersecurity threats. This can be especially valuable for sectors like finance or healthcare where both privacy and security are paramount.

**Lower latency:** Fewer parameters translate to decreased processing times, allowing SLMs to respond quickly. For instance, Granite 3.0 1B-A400M and Granite 3.0 3B-A800M have total parameter counts of 1 billion and 3 billion, respectively, while their active parameter counts at inference are 400 million for the 1B model and 800 million for the 3B model. This allows both SLMs to minimize latency while delivering high inference performance.

**More environmentally sustainable:** Because they require less computational resources, small language models consume less energy, thereby decreasing their carbon footprint.

**Reduced cost:** Organizations can save on development, infrastructure and operational expenses—such as acquiring huge amounts of high-quality training data and using advanced hardware—that would otherwise be needed to run massive models.

## Limitations of small language models

Like LLMs, SLMs still have to grapple with [the risks of AI](https://www.ibm.com/think/insights/10-ai-dangers-and-risks-and-how-to-manage-them). This is a consideration for businesses looking to integrate small language models into their internal workflows or implement them commercially for specific applications.

[**Bias**](https://www.ibm.com/think/topics/ai-bias?)**:** Smaller models can learn from the bias present in their larger counterparts, and this ripple effect can be manifested in their outputs.

**Decreased performance on complex tasks:** Because SLMs are typically fine-tuned on specific tasks, they might be less proficient on complex tasks that require knowledge across a comprehensive spectrum of topics. For example, Microsoft notes that its “Phi-3 models do not perform as well on factual knowledge benchmarks as the smaller model size results in less capacity to retain facts.”<sup>9</sup>

**Limited generalization:** Small language models lack the wide knowledge base of their expansive equivalents, so they might be better suited for targeted language tasks.

[**Hallucinations**](https://www.ibm.com/think/topics/ai-hallucinations?)**:** Validating the results of SLMs is vital to make sure what they produce is factually correct.

## Small language model use cases

Enterprises can fine-tune SLMs on domain-specific datasets to customize them for their specific needs. This adaptability means small language models can be employed for a variety of real-world applications:

[**Chatbots**](https://www.ibm.com/think/topics/chatbots?)**:** Because of their low latency and [conversational AI](https://www.ibm.com/think/topics/conversational-ai?) capabilities, SLMs can power customer service chatbots, responding rapidly to queries in real-time. They can also serve as the backbone for agentic AI chatbots that go beyond providing responses to completing tasks on behalf of a user.

**Content** [**summarization**](https://www.ibm.com/think/topics/text-summarization?)**:** Llama 3.2 1B and 3B models, for example, can be used to summarize discussions on a smartphone and create action items like calendar events.<sup>6</sup> Similarly, Gemini Nano can summarize audio recordings and transcripts of conversations.<sup>11</sup>

[**Generative AI**](https://www.ibm.com/think/topics/generative-ai?)**:** Compact models can be implemented for completing and generating text and software code. For instance, the granite-3b-code-instruct and granite-8b-code-instruct models can be used to generate, explain and translate code from a natural language prompt.

**Language translation:** Many small language models are multilingual and have been trained in languages other than English, so they can translate between languages quickly. Because of their ability to understand context, they can produce near-accurate translations that retain the original text’s nuance and meaning.

[**Predictive maintenance**](https://www.ibm.com/think/topics/predictive-maintenance?)**:** Lean models are small enough to deploy directly on local [edge](https://www.ibm.com/think/topics/edge-ai?) devices like sensors or [Internet of Things (IoT)](https://www.ibm.com/think/topics/internet-of-things?) devices. This means that manufacturers can treat SLMs as tools that gather data from sensors installed in machinery and equipment and analyze that data in real-time to predict maintenance needs.

[**Sentiment analysis**](https://www.ibm.com/think/topics/sentiment-analysis?)**:** In addition to processing and understanding language, SLMs are also skilled at sorting through and classifying huge volumes of text in an objective manner. This makes them suitable for analyzing text and gauging the sentiment behind it, aiding in understanding customer feedback.

**Vehicle navigation assistance:** A model as fast and compact as an SLM can run on a vehicle’s onboard computers. Because of their multimodal capabilities, small language models can combine voice commands with image classification, for example, to identify obstacles around a vehicle. They can even tap into their RAG capabilities, retrieving details from highway codes or road rules to help drivers make safer, more informed driving decisions.

## Footnotes

*All links reside outside ibm.com*

<sup>1</sup> [DistilBERT, a distilled version of BERT: smaller, faster, cheaper and lighter](https://arxiv.org/abs/1910.01108), arXiv, 1 March 2020

<sup>2</sup> [Well-Read Students Learn Better: On the Importance of Pre-training Compact Models](https://arxiv.org/abs/1908.08962), arXiv, 25 September 2019

<sup>3</sup> [MobileBERT: a Compact Task-Agnostic BERT for Resource-Limited Devices](https://arxiv.org/abs/2004.02984), arXiv, 14 Apr 2020

<sup>4</sup> [Gemma explained: An overview of Gemma model family architectures](https://developers.googleblog.com/en/gemma-explained-overview-gemma-model-family-architectures/), Google for Developers, 15 August 2024

<sup>5</sup> [Gemini Models](https://deepmind.google/technologies/gemini/), Google DeepMind, Accessed 17 October 2024

<sup>6</sup> [Introducing Llama 3.2](https://www.llama.com/), Meta, Accessed 17 October 2024

<sup>7</sup> [Meta and Microsoft Introduce the Next Generation of Llama](https://ai.meta.com/blog/llama-2/), Meta, 18 July 2023

<sup>8</sup> [Un Ministral, des Ministraux](https://mistral.ai/news/ministraux), Mistral AI, 16 October 2024

<sup>9</sup> [Introducing Phi-3: Redefining what’s possible with SLMs](https://azure.microsoft.com/blog/introducing-phi-3-redefining-whats-possible-with-slms/), Microsoft, 23 April 2024

<sup>10</sup> [GPT-4o mini: advancing cost-efficient intelligence](https://openai.com/index/gpt-4o-mini-advancing-cost-efficient-intelligence/), OpenAI, 18 July 2024

<sup>11</sup> [Gemini Nano](https://deepmind.google/technologies/gemini/nano/), Google DeepMind, Accessed 21 October 2024
