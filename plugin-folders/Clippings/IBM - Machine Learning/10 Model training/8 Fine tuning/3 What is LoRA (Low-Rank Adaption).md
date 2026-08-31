---
title: What is LoRA (low-rank adaption)?
source: https://www.ibm.com/think/topics/lora
author:
- '[[Joshua Noble]]'
published: 2025-01-28
created: 2026-08-31
description: "Low-rank adaptation (LoRA) is a technique used to adapt machine learning models to new contexts. It can adapt large models to specific uses by adding lightweight pieces to the original model rather than changing the entire model."
---

*This article was featured in the Think newsletter. [Get it in your inbox](https://www.ibm.com/forms/news-mkt-52954).[](https://www.ibm.com/forms/news-mkt-52954)*

## What is LoRA?

Low-rank adaptation (LoRA) is a technique used to adapt [machine learning](https://www.ibm.com/think/topics/machine-learning) models to new contexts. It can adapt large models to specific uses by adding lightweight pieces to the original model rather than changing the entire model. A [data scientist](https://www.ibm.com/think/topics/data-science) can quickly expand the ways that a model can be used rather than requiring them to build an entirely new model.

The technique was originally published by Edward Hu, Yelong Shen and collaborators in their paper LoRA: Low-Rank Adaptation Of Large Language Models <sup>[1](#F1)</sup>. In the paper, they showed that models reduced and retrained using LoRA outperformed base models on a variety of benchmark tasks. The model performance might be improved without requiring full fine-tuning and by using a significantly smaller number of trainable [model parameters](https://www.ibm.com/think/topics/model-parameters).

## What does LoRA do?

Large and complex machine learning models, such as those used for [large language models](https://www.ibm.com/think/topics/large-language-models) (LLMs) like [ChatGPT](https://www.ibm.com/think/topics/chatgpt), take a long time and numerous resources to set up. They might have trillions of parameters that are set to specific values. Once this process is complete, the model might be powerful and accurate in general, but it is not necessarily [fine-tuned](https://www.ibm.com/think/topics/fine-tuning) to carry out specific tasks.

Getting a model to work in specific contexts can require a great deal of retraining, changing all its parameters. With the number of parameters in such models, this retraining is expensive and time-consuming. LoRA provides a quick way to adapt the model without retraining it.

As an example, a full fine-tuning of the GPT-3 model requires training 175 billion parameters because of the size of its training dataset. Using LoRA, the trainable parameters for GPT-3 can be reduced to roughly 18 million parameters, which reduces [GPU](https://www.ibm.com/think/topics/gpu) memory requirements by roughly two thirds.

LoRA is not the only efficient fine-tuning method. A variant of LoRA is [quantization](https://www.ibm.com/think/topics/quantization) LoRA (QLoRA), a fine tuning technique that combines a high-precision computing technique with a low-precision storage method. This helps keep the model size small while still making sure the model is still highly performant and accurate.

## How LoRA works

Instead of retraining the whole model, LoRA freezes the original weights and parameters of the model as they are. Then, on top of this original model, it adds a lightweight addition called a low-rank matrix, which is then applied to new inputs to get results specific to the context. The low-rank matrix adjusts for the weights of the original model so that outputs match the desired use case.

LoRA leverages the concept of lower-rank matrices to make the model training process extremely efficient and fast. Traditionally fine-tuning LLMs requires adjusting the entire model. LoRA focuses on modifying a smaller subset of parameters (lower-rank matrices) to reduce computational and memory overhead.

The diagram shows how LoRA updates the matrices A and B to track changes in the pretrained weights by using smaller matrices of rank r. Once LoRA training is complete, smaller weights are merged into a new weight matrix, without needing to modify the original weights of the [pretrained model](https://www.ibm.com/think/topics/pretrained-model).

![An illustrated diagram showing how low rank adaptation reduces model size](https://assets.ibm.com/is/image/ibm/lora-2?ts=1785851533652&dpr=off)

LoRA is built on the understanding that large models inherently possess a low-dimensional structure. By leveraging smaller matrices, which are called low-rank matrices, LoRA adapts these models effectively. This method focuses on the core concept that significant model changes can be represented with fewer parameters, thus making the adaptation process more efficient.

Matrices are an important part of how machine learning models and neural networks work. Low-rank matrices are smaller and have many fewer values than larger or higher-rank matrices. They do not take up much memory and require fewer steps to add or multiply together and this makes them faster for computers to process.

A high-rank matrix can be decomposed into two low-rank matrices, a 4 x 4 matrix can be decomposed into a 4 x 1 and a 1 x 4 matrix.

![An illustrated diagram showing how a 4 by 4 matrix can be reduced to a 1 by 4 and 4 by 1 matrix](https://assets.ibm.com/is/image/ibm/lora-1?ts=1785851533921&dpr=off)

LoRA adds low-rank matrices to the frozen original machine learning model. The low-rank matrices are updated through gradient descent during fine-tuning, without modifying the weights of the base model. These matrices contain new weights to apply to the model when generating results. The multiplied change matrix is added to the base model weights to get the final fine-tuned model. This process alters the outputs that the model produces with minimal computing power and training time.

In essence, LoRA keeps the original model unchanged and adds small, changeable parts to each layer of the model. This significantly reduces the trainable parameters of the model and the GPU memory requirement for the training process, which is another significant challenge when it comes to fine-tuning or training large models.

To implement LoRA fine tuning with HuggingFace using Python and PyTorch, developers can use the [parameter-efficient fine-tuning](https://www.ibm.com/think/topics/parameter-efficient-fine-tuning) (PEFT) library to inject the LoRA adapters into the model and use them as the update matrices. This library is freely available through [HuggingFace](https://www.ibm.com/think/topics/hugging-face) or GitHub. This [library](https://www.ibm.com/think/insights/open-source-ai-tools) provides ways to configure LoRA parameters for your model. Some of the most commonly used parameters are:

**r**: the rank of the update matrices, expressed in int. Lower rank decomposition results in smaller update matrices with fewer trainable parameters.

**target_modules**: The modules (for example, attention blocks) to apply the LoRA update matrices.

**lora_alpha**: LoRA scaling factor.

## Advantages of LoRA

One of the key advantages of LoRA is that a base model can be shared and used to build many small LoRA modules for new tasks. The shared model is frozen, which allows users to switch tasks by replacing the LoRA weight matrices. Instead of needing two different models, a single model can be used in different tasks while still retaining the performance gains of fine-tuning.

LoRA makes training more efficient and lowers the hardware barrier to entry because users do not need to calculate the gradients or maintain the optimizer states for most parameters. Instead, the process requires optimizing only the much smaller low-rank matrices.

The linear design of LoRA allows data scientists to merge the trainable matrices with the frozen pretrained model weights when deployed, introducing no inference latency compared to a fully fine-tuned model by construction.

LoRA can be combined with other techniques to improve model performance such as prefix-tuning, making it flexible.

## Tradeoffs

While LoRA provides a significant reduction in the number of trainable parameters, there is a tradeoff as well. The process creates information loss during matrix decomposition. Because LoRA reduces the fullweight matrix into smaller components, some details can be lost in the process. This is comparable to model overfitting. In the case of LLMs though, the loss is often minimal because deep learning models are so highly overparameterized-—meaning that they contain more parameters than necessary for the task. “Over-parameterized” means that these models are often bigger than they need to be for the training data. Not all the parameters strictly matter. There is redundancy, robustness and resiliency within the parameters. Removing this resiliency can make models less accurate, so the rank of update matrices can be tuned as a part of the LoRA process.

## Footnotes

1. Hu, Edward, et al, LoRA: Low-Rank Adaptation of Large Language Models, 2021
