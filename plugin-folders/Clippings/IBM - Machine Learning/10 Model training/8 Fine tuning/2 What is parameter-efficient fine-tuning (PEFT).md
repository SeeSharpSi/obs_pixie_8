---
title: What is parameter-efficient fine-tuning (PEFT)?
source: https://www.ibm.com/think/topics/parameter-efficient-fine-tuning
author:
- '[[Ivan Belcic]]'
- '[[Cole Stryker]]'
published: 2024-08-15
created: 2026-08-31
description: "Parameter-efficient fine-tuning (PEFT) is a method of improving the performance of pretrained large language models (LLMs) and neural networks for specific tasks or data sets."
---

## What is parameter-efficient fine-tuning (PEFT)?

Parameter-efficient fine-tuning (PEFT) is a method of improving the performance of pretrained [large language models (LLMs)](https://www.ibm.com/topics/large-language-models) and [neural networks](https://www.ibm.com/topics/neural-networks) for specific tasks or data sets. By training a small set of parameters and preserving most of the large [pretrained model’s](https://www.ibm.com/think/topics/pretrained-model) structure, PEFT saves time and computational resources.

[Neural networks](https://www.ibm.com/topics/neural-networks) trained for general tasks such as [natural language processing (NLP)](https://www.ibm.com/topics/natural-language-processing) or image classification can specialize in a related new task without being entirely retrained. PEFT is a resource-efficient way to build highly specialized models without starting from scratch each time.

## How does parameter-efficient fine-tuning work?

PEFT works by freezing most of the pretrained [model parameters](https://www.ibm.com/think/topics/model-parameters) and layers while adding a few trainable parameters, known as adapters, to the final layers for predetermined downstream tasks.

The fine-tuned models retain all the learning gained during training while specializing in their respective downstream tasks. Many PEFT methods further enhance efficiency with gradient checkpointing, a memory-saving technique that helps models learn without storing as much information at once.

## Why is parameter-efficient fine-tuning important?

Parameter-efficient fine-tuning balances efficiency and performance to help organizations maximize computational resources while minimizing storage costs. When tuned with PEFT methods, transformer-based models such as [GPT-3](https://www.ibm.com/think/topics/gpt), [LLaMA](https://www.ibm.com/think/topics/llama-2) and BERT can use all the knowledge contained in their pretraining parameters while performing better than they otherwise would without [fine-tuning](https://www.ibm.com/think/topics/fine-tuning).

PEFT is often used during transfer learning, where models trained in one task are applied to a second related task. For example, a model trained in image [classification](https://www.ibm.com/think/topics/classification-machine-learning) might be put to work on object detection. If a base model is too large to completely retrain or if the new task is different from the original, PEFT can be an ideal solution.

## PEFT versus fine-tuning

Traditional full [fine-tuning](https://www.ibm.com/topics/fine-tuning) methods involve slight adjustments to all the parameters in pretrained LLMs to adapt them for specific tasks. But as developments in [artificial intelligence (AI)](https://www.ibm.com/topics/artificial-intelligence) and [deep learning](https://www.ibm.com/topics/deep-learning) have led models to grow larger and more complex, the fine-tuning process has become too demanding on computational resources and energy.

Also, each fine-tuned model is the same size as the original. All these models take up significant amounts of storage space, further driving up costs for the organizations that use them. While fine-tuning does create more efficient [machine learning (ML)](https://www.ibm.com/topics/machine-learning), the process of fine-tuning LLMs has itself become inefficient.

PEFT adjusts the handful of parameters that are most relevant to the model’s intended use case to deliver specialized [model performance](https://www.ibm.com/think/topics/model-performance) while reducing model weights for significant computational cost and time savings.

## PEFT benefits

Parameter-efficient fine-tuning brings a wealth of benefits that have made it popular with organizations that use LLMs in their work:

- Increased efficiency
- Faster time-to-value
- No catastrophic forgetting
- Lower risk of overfitting
- Lower data demands
- More accessible AI
- More flexible AI

### Increased efficiency

Most large language models used in generative AI (gen AI) are powered by expensive graphics processing units (GPUs) made by manufacturers such as Nvidia. Each LLM uses large amounts of computational resources and energy. Adjusting only the most relevant parameters imparts large savings on energy and cloud computing costs.

### Faster time-to-value

Time-to-value is the amount of time that it takes to develop, train and deploy an LLM so it can begin generating value for the organization that uses it. Because PEFT tweaks only a few trainable parameters, it takes far less time to update a model for a new task. PEFT can deliver comparable performance to a full fine-tuning process at a fraction of the time and expense.

### No catastrophic forgetting

[Catastrophic forgetting](https://www.ibm.com/think/topics/catastrophic-forgetting) happens when LLMs lose or “forget” the knowledge gained during the initial training process as they are retrained or tuned for new use cases. Because PEFT preserves most of the initial parameters, it also safeguards against catastrophic forgetting.

### Lower risk of overfitting

[Overfitting](https://www.ibm.com/topics/overfitting) is when a model hews too closely to its training data during the training process, making it unable to generate accurate predictions in other contexts. Transformer models tuned with PEFT are much less prone to overfitting as most of their parameters remain static.

### Lower data demands

By focusing on a few parameters, PEFT lowers the training data requirements for the fine-tuning process. Full fine-tuning requires a much larger training data set because all the model’s parameters will be adjusted during the fine-tuning process.

### More accessible AI

Without PEFT, the costs of developing a specialized LLM are too high for many smaller or medium-sized organizations to bear. PEFT makes LLMs available to teams who might not otherwise have the time or resources to train and fine-tune models.

### More flexible AI

PEFT enables data scientists and other professionals to customize general LLMs to individual use cases. AI teams can experiment with model optimization without worrying as much about burning through computational, energy and storage resources.

## PEFT techniques

AI teams have various PEFT techniques and algorithms at their disposal, each with its relative advantages and specializations. Many of the most popular PEFT tools can be found on Hugging Face and numerous other GitHub communities.

- Adapters
- LoRA
- QLoRA
- Prefix-tuning
- Prompt-tuning
- P-tuning

### Adapters

Adapters are one of the first PEFT techniques to be applied to [natural language processing](https://www.ibm.com/think/topics/natural-language-processing) (NLP) models. Researchers strove to overcome the challenge of training a model for multiple downstream tasks while minimizing model weights. Adapter modules were the answer: small add-ons that insert a handful of trainable, task-specific parameters into each transformer layer of the model.

### LoRA

Introduced in 2021, low-rank adaption of large language models ([LoRA](https://www.ibm.com/think/topics/lora)) uses twin low-rank decomposition matrices to minimize model weights and reduce the subset of trainable parameters even further.

### QLoRA

QLoRA is an extended version of LoRA that quantizes or standardizes the weight of each pretrained parameter to just 4 bits from the typical 32-bit weight. As such, QLoRA offers significant memory savings and makes it possible to run an LLM on just one GPU.

### Prefix-tuning

Specifically created for [natural language generation](https://www.ibm.com/think/topics/natural-language-generation) (NLG) models, prefix-tuning appends a task-specific continuous vector, known as a prefix, to each transformer layer while keeping all parameters frozen. As a result, prefix-tuned models store over a thousandfold fewer parameters than fully fine-tuned models with comparable performance.

### Prompt-tuning

[Prompt-tuning](https://research.ibm.com/blog/what-is-ai-prompt-tuning) simplifies prefix-tuning and trains models by injecting tailored prompts into the input or training data. Hard prompts are manually created, while soft prompts are AI-generated strings of numbers that draw knowledge from the base model. Soft prompts have been found to outperform human-generated hard prompts during tuning.

### P-tuning

P-tuning is a variation of prompt-tuning designed for [natural language understanding](https://www.ibm.com/think/topics/natural-language-understanding) (NLU) tasks. Rather than use manually created prompts, P-tuning introduced automated prompt training and generation that leads to more impactful training prompts over time.
