---
title: What are foundation models?
source: https://www.ibm.com/think/topics/foundation-models
author:
- '[[Rina Diane Caballar]]'
- '[[Cole Stryker]]'
published: 2024-10-15
created: 2026-08-31
description: "Foundation models are artificial intelligence (AI) models trained on vast, immense datasets and are capable of fulfilling a broad range of general tasks. They serve as the base or building blocks for crafting more specialized applications."
---

## What are foundation models?

Foundation models are [artificial intelligence (AI) models](https://www.ibm.com/think/topics/ai-model?) trained on vast, immense datasets and can fulfill a broad range of general tasks. They serve as the base or building blocks for crafting more specialized applications.

Their flexibility and massive size set them apart from traditional [machine learning](https://www.ibm.com/think/topics/machine-learning?) models, which are trained on smaller datasets to accomplish specific tasks, such as [object detection](https://www.ibm.com/think/topics/object-detection?) or trend [forecasting](https://www.ibm.com/think/topics/forecasting?). Foundation models, meanwhile, employ [transfer learning](https://www.ibm.com/think/topics/transfer-learning?) to apply the knowledge learned from one task to another. This makes them fit for more expansive domains, including [computer vision](https://www.ibm.com/think/topics/computer-vision?), [natural language processing (NLP)](https://www.ibm.com/think/topics/natural-language-processing?) and [speech recognition](https://www.ibm.com/think/topics/speech-recognition?).

Researchers at Stanford University’s Center for Research on Foundation Models and Institute for Human-Centered Artificial Intelligence coined the term “foundation models” in a 2021 paper. They characterize these models as a “paradigm shift” and describe the reasoning behind their naming: “[A] foundation model is itself incomplete but serves as the common basis from which many task-specific models are built via adaptation. We also chose the term ‘foundation’ to connote the significance of architectural stability, safety and security: poorly constructed foundations are a recipe for disaster and well-executed foundations are a reliable bedrock for future applications.”<sup>1</sup>

## How do foundation models work?

Building a foundation model often involves a series of steps akin to developing a conventional machine learning model:

1. Data gathering
2. Choosing the modality
3. Defining the model architecture
4. Training
5. Evaluation

### 1. Data gathering

The first step is to collate a huge corpus of data from diverse sources. This sweeping spectrum of unlabeled, unstructured data allows foundation models to infer patterns, recognize relationships, discern context and generalize their knowledge.

### 2. Choosing the modality

Modality refers to the type of data that a model can process, including audio, images, software code, text and video. Foundation models can be either unimodal or [multimodal](https://www.ibm.com/think/topics/multimodal-ai). Unimodal models are designed to handle a single type of data, such as receiving text inputs and generating text outputs. Multimodal models can combine information from multiple modalities, such as taking a text prompt and creating an image or producing written transcripts from a voice recording.

### 3. Defining the model architecture

Many foundation models employ a [deep learning](https://www.ibm.com/think/topics/deep-learning?) architecture, which uses multilayered [neural networks](https://www.ibm.com/think/topics/neural-networks?) to mimic the human brain’s decision-making process.

A type of deep learning model known as the [transformer model](https://www.ibm.com/think/topics/transformer-model?) has been an architecture of choice for foundation models, particularly those for NLP like the [generative pre-trained transformer (GPT)](https://www.ibm.com/think/topics/gpt) line of models. Here’s a brief overview of the transformer architecture:

- Encoders transform input sequences into numerical representations called embeddings that capture the semantics and position of tokens in the input sequence.

- A self-attention mechanism allows transformers to “focus their attention” on the most important tokens in the input sequence, regardless of their position.

- Decoders use this self-attention mechanism and the encoders’ embeddings to generate the most statistically probable output sequence.

[Diffusion models](https://www.ibm.com/think/topics/diffusion-models) are another architecture implemented in foundation models. Diffusion-based neural networks gradually “diffuse” training data with random noise, then learn to reverse that diffusion process to reconstruct the original data. Diffusion models are primarily used in text-to-image foundation models like Google’s Imagen, OpenAI’s DALL-E (starting with DALL-E 2) and Stability AI’s Stable Diffusion.

### 4. Training

Training typically entails [self-supervised learning](https://www.ibm.com/think/topics/self-supervised-learning?), where foundation models learn inherent correlations in unlabeled data. So, training happens over multiple iterations, with model weights adjusted to minimize prediction errors and [hyperparameters tuned](https://www.ibm.com/think/topics/hyperparameter-tuning) to find the optimal configuration variables for training. [Regularization](https://www.ibm.com/think/topics/regularization?) methods can also be applied to correct for [overfitting](https://www.ibm.com/think/topics/overfitting?) (when a model fits too closely or even exactly to its training data) and to improve a foundation model’s ability to generalize.

### 5. Evaluation

A foundation model’s performance can be validated by using standardized [benchmarks](https://www.ibm.com/think/topics/llm-benchmarks). The results from these assessments can inform further improvements or performance optimizations.

## Adapting foundation models

Developing a foundation model from scratch can be a costly, computationally intensive and time-consuming process. That’s why enterprises might consider adapting existing foundation models for their particular needs. These models can be accessed through an [application programming interface (API)](https://www.ibm.com/think/topics/api?) or by using a local copy of the model.

Here are two common approaches to adaptation:

### Fine-tuning

During [fine-tuning](https://www.ibm.com/think/topics/fine-tuning?), a pretrained foundation model adapts its general knowledge to a particular task. This involves further training by using [supervised learning](https://www.ibm.com/think/topics/supervised-learning?) on a smaller, domain-specific or task-specific dataset that includes labeled examples. The model’s parameters are updated to optimize its performance on the task.

Because fine-tuning alters a model’s parameters, it might affect how the model performs on other tasks. Creating a labeled dataset is also a tedious process.

### Prompting

This method entails providing a prompt to tailor a foundation model to a certain task. The prompt comes in the form of task-related instructions or task-relevant examples that guide a model, allowing it to gain context and generate a plausible output, an ability known as [in-context learning](https://research.ibm.com/blog/demystifying-in-context-learning-in-large-language-model).

While prompting doesn’t require training a model or changing its parameters, it can take several tries to get the right prompt that conditions a model to understand context and make fitting predictions.

## Foundation model use cases

The adaptability and general-purpose nature of foundation models means they can be implemented for various real-world applications:

- Computer vision

- Natural language processing

- Healthcare

- Robotics

- Software code generation

### Computer vision

Foundation models can be used to generate and classify images and to detect, identify and describe objects. DALL-E, Imagen and Stable Diffusion are examples of text-to-image foundation models.

### Natural language processing

[Large language models (LLMs)](https://www.ibm.com/think/topics/large-language-models?) are a class of foundation models that excel in NLP and natural language understanding (NLU). Their capabilities encompass question answering, text summarization, transcription, translation and video captioning, among others.

Here are a few popular foundation models in the NLP space:

- BERT (Bidirectional Encoder Representations from Transformers) was one of the first foundation models. Released by Google in 2018, this open source AI system was trained on only a plain-text corpus.<sup>2</sup>

- BLOOM is an open-access multilingual language model trained on 46 languages. It’s the result of a collaborative effort between Hugging Face and BigScience, a community of AI researchers.<sup>3</sup>

- Claude is Anthropic’s family of foundation models with advanced reasoning and multilingual processing capabilities.

- GPT, OpenAI’s foundation model, is the backbone of ChatGPT, the company’s [generative AI](https://www.ibm.com/think/topics/generative-ai?) chatbot. GPT-3.5 powers the free version of ChatGPT, while GPT-4 is behind the premium version. The GPT-4 series is also the generative AI model that supports Microsoft’s Copilot AI assistant.

- [Granite](https://www.ibm.com/granite) is the IBM® flagship series of LLM [foundation models](https://www.ibm.com/products/watsonx-ai/foundation-models) based on decoder-only transformer architecture. The Granite 13b chat model is optimized for dialogue use cases and works well with [virtual agent](https://www.ibm.com/think/topics/virtual-agent?) and chat apps. While the Granite multilingual model is trained to understand and generate text in English, German, Spanish, French and Portuguese.

- PaLM 2 is Google’s next-generation language model with enhanced multilingual and reasoning capabilities.

### Healthcare

Within the healthcare field, foundation models can aid in a range of tasks. From creating summaries of patient visits and searching medical literature to answering patient questions, matching patients with clinical trials and facilitating drug discovery. The Med-PaLM 2 language model, for instance, can answer medical questions, and Google is designing a multimodal version that can synthesize information from medical images.<sup>4</sup>

### Robotics

In the realm of robotics, foundation models can help robots rapidly adapt to new environments and generalize across various tasks, scenarios and machine embodiments. For example, the PaLM-E embodied multimodal language model transfers knowledge from PaLM’s language and visual domains to robotics systems and is trained on robot sensor data.<sup>5</sup>

### Software code generation

Foundation models can assist with completing, debugging, explaining and generating code in different programming languages. These text-to-code foundation models include Anthropic’s Claude, Google’s Codey and PaLM 2 and IBM’s Granite Code model family trained on 116 programming languages.

With so many options, how can organizations choose the right foundation model for AI development? Here’s a six-step AI model selection framework that can help:

## Benefits of foundation models

Building upon foundation models can lead to automation and innovation for enterprises. Here are other advantages businesses can gain from foundation models:

**Accelerated time to value and time to scale:** Adopting existing models eliminates the development and pretraining phases, allowing companies to swiftly customize and deploy fine-tuned models.

**Access to data:** Organizations don’t need to compile large amounts of data for pretraining that they might not have the means to acquire.

**Baseline accuracy and performance:** Foundation models have already been evaluated for accuracy and performance, offering a high-quality starting point.

**Reduced cost:** Enterprises won’t need to spend on the resources needed to create a foundation model from the ground up.

## Challenges of foundation models

Like other AI models, foundation models are still contending with [the risks of AI](https://www.ibm.com/think/insights/10-ai-dangers-and-risks-and-how-to-manage-them). This is a factor to keep in mind for enterprises considering foundation models as the technology underpinning their internal workflows or commercial AI applications.

**[Bias](https://www.ibm.com/think/topics/ai-bias?):** A model can learn from the human bias present in the training data, and that bias can trickle down to the outputs of fine-tuned models.

**Computational costs:** Using existing foundation models still requires significant memory, advanced hardware such as [GPUs (graphics processing units)](https://www.ibm.com/think/topics/gpu?) and other computational resources to fine-tune, deploy and maintain.

**Data privacy and intellectual property:** Foundation models might be trained on data obtained without the consent or knowledge of its owners. Exercise caution when feeding data into [algorithms](https://www.ibm.com/think/topics/machine-learning-algorithms?) to avoid infringing on the copyright of others or exposing personally identifiable or proprietary business information.

**Environmental toll:** Training and running large-scale foundation models involves energy-intensive computations that contribute to increased carbon emissions and water consumption.

**[Hallucinations](https://www.ibm.com/think/topics/ai-hallucinations?):** Verifying the results of AI foundation models is essential to make sure they’re producing factually correct outputs.

## Footnotes

<sup>1</sup> [On the Opportunities and Risks of Foundation Models](https://crfm.stanford.edu/assets/report.pdf), Stanford Center for Research on Foundation Models and Stanford Institute for Human-Centered Artificial Intelligence, 2021

<sup>2</sup> [Open Sourcing BERT: State-of-the-Art Pre-training for Natural Language Processing](https://research.google/blog/open-sourcing-bert-state-of-the-art-pre-training-for-natural-language-processing/), Google Research, 2 November 2018

<sup>3</sup> [BigScience Large Open-science Open-access Multilingual Language Model](https://huggingface.co/bigscience/bloom), Hugging Face, 6 July 2022

<sup>4</sup> [Med-PaLM](https://sites.research.google/med-palm/), Google Research, Accessed 8 October 2024

<sup>5</sup> [PaLM-E: An embodied multimodal language model](https://research.google/blog/palm-e-an-embodied-multimodal-language-model/), Google Research, 10 March 2023
