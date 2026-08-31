---
title: What is grouped query attention (GQA)?
source: https://www.ibm.com/think/topics/grouped-query-attention
author:
- '[[Dave Bergmann]]'
- '[[Cole Stryker]]'
published: 2024-12-13
created: 2026-08-31
description: "Grouped query attention (GQA) is a method to increase the efficiency of attention mechanism in transformers, often used to enable faster inference from LLMs."
---

## What is grouped query attention (GQA)?

Grouped query attention (GQA) is a method to increase the efficiency of the [attention mechanism](https://www.ibm.com/think/topics/attention-mechanism) in transformer models, often used to enable faster inference from [large language models (LLMs)](https://www.ibm.com/topics/large-language-models).

Ainslie *et al* conceived grouped query attention as an optimization of multi-head attention (MHA), the innovative self-attention algorithm introduced in the seminal 2017 [“Attention is All You Need” paper](https://proceedings.neurips.cc/paper_files/paper/2017/file/3f5ee243547dee91fbd053c1c4a845aa-Paper.pdf) that established transformer [neural networks](https://www.ibm.com/topics/neural-networks). More specifically, it was proposed as a generalization and more restrained application of multi-query attention (MQA), an earlier optimization of MHA.

Though standard multi-head attention catalyzed an evolutionary leap forward in [machine learning](https://www.ibm.com/topics/machine-learning), [natural language processing (NLP)](https://www.ibm.com/topics/natural-language-processing) and [generative AI](https://www.ibm.com/topics/generative-ai), it’s extremely demanding on computational resources and memory bandwidth. As LLMs grew larger and more sophisticated, these memory usage requirements became a bottleneck on progress, especially for the [autoregressive](https://www.ibm.com/topics/autoregressive-model) decoder-only LLMs used for [text generation](https://www.ibm.com/topics/text-generation), [summarization](https://www.ibm.com/topics/text-summarization) and other generative AI tasks.

Subsequent research focused on techniques to enhance or streamline multi-head attention. Some, such as flash attention and ring attention, improve the ways that the [GPUs](https://www.ibm.com/topics/gpu) used to train and run models handle calculations and memory storage. Others, such as GQA and MQA, explored changes to the way that transformer architectures process [tokens](https://www.ibm.com/docs/en/watsonx/saas?topic=solutions-tokens).

Grouped query attention aims to balance the tradeoffs between standard multi-head attention and multi-query attention. The former maximizes accuracy at the cost of increased memory bandwidth overhead and decreased speed. The latter maximizes speed and efficiency at the expense of accuracy.

## Standard multi-head attention

To understand how grouped query attention optimizes transformer models, it’s important to first understand how multi-head attention works in general. Both GQA and MQA simply *refine*, rather than *replace*, the core methodology of MHA.

The driving force behind LLMs and other models that use the transformer architecture is *self-attention*, a mathematical framework for understanding the relationships between each of the different tokens in a sequence. Self-attention allows an LLM to interpret text data through not only static baseline definitions, but also the context provided by other words and phrases.

In autoregressive LLMs used for text generation, the attention mechanism helps the model predict the next token in a sequence by determining which previous tokens are most worth “paying attention to” at that moment. Information from tokens it deems most relevant is given greater *attention weights*, while information from tokens deemed irrelevant is given attention weights approaching 0.

The multi-head attention mechanism that animates transformer models generates rich contextual information through calculating self-attention many times in parallel by splitting attention layers into multiple *attention heads.*

![Diagram of multi-head attention](https://assets.ibm.com/is/image/ibm/multi-head-attention?ts=1763388075615&dpr=off)   The simplified multi-head attention diagram made famous in "Attention is All You Need"

### How standard multi-head attention works

The authors of “Attention is All You Need” articulated its attention mechanism using the terminology of a [relational database](https://www.ibm.com/topics/relational-databases): **queries**, **keys** and **values**. Relational databases are designed to simplify the storage and retrieval of relevant data: they assign a unique identifier (“key”) to each piece of data, and each *key* is associated with a corresponding *value*. The goal of a relational database is to match each *query* to the appropriate key.

For each token in a sequence, multi-head attention requires the creation of 3 vectors.

- A *query vector*, *Q*, representing the information that the token is “seeking.” For instance, the query vector for a noun might represent a search for adjectives that describe it.
- A *key vector, K*, representing the information that the token contains. Alignment scores, representing the relevance of each token’s key vector to the query vector of each of the other tokens, are used to compute attention weights.
- A *value vector*, *V,* representing the contextual information that will be updated by the attention-weighted contributions from the key vectors of other tokens.

The mathematical interactions between these 3 vectors, mediated by the attention mechanism, are how a model adjusts its context-specific understanding of each token.

##### **Generating query, key and value vectors**

To generate each of these 3 vectors for a given token, the model starts with that token’s original [vector embedding](https://www.ibm.com/think/topics/vector-embedding): a numerical encoding in which each *[dimension](https://www.ibm.com/think/topics/vector-embedding#How+does+vector+embedding+work%3F)* of the vector corresponds with some abstract element of the token’s semantic meaning. The number of dimensions in these vectors is a predetermined hyperparameter.

The *Q*, *K* and *V* vector for each token are generated by passing the original token embedding through a linear layer that precedes the first attention layer. This linear layer is partitioned into 3 unique matrices of model weights: W<sub>Q</sub>, W<sub>K</sub> and W<sub>V</sub>. The specific weight values therein are learned through [self-supervised pretraining](https://www.ibm.com/topics/self-supervised-learning) on a massive dataset of text examples.

Multiplying the token’s original vector embedding by W<sub>Q</sub>, W<sub>K</sub> and W<sub>V</sub> yields its corresponding query vector, key vector and value vector, respectively. The number of dimensions *d* each vector contains is determined by the size of each weight matrix. *Q* and *K* will have the same number of dimensions, *d<sub>k</sub>.*

These 3 vectors are then passed to the attention layer.

![A diagram of a transformer model's attention mechanism](https://assets.ibm.com/is/image/ibm/self-attention-matrix-calculation?ts=1763388076490&dpr=off)   A simplified diagram of the transformer's attention mechanism: the original vector embeddings for the tokens of an input sentence are multiplied by W, K and V weight matrices to yield their respective W, K and V vectors.

##### **Scaled dot product attention and softmax**

In the attention layer, the *Q, K* and *V* vectors are used to calculate an *alignment score* between each token at each position in a sequence. Those alignment scores are then normalized into *attention weights* using a softmax function.

For each token *x* in a sequence, alignment scores are calculated by computing the *dot product* of that token’s query vector *Q<sub>x</sub>* with the key vector *K* of each of the other tokens: in other words, by multiplying them together. If a meaningful relationship between 2 tokens is reflected in similarities between their respective vectors, multiplying them together will yield a large value. If the 2 vectors *aren’t* aligned, multiplying them together will yield a small or negative value. Most transformer models use a variant called *scaled dot product attention*, in which QK is *scaled*—that is, multiplied—by $\frac{1}{\sqrt{d_k}}$ to improve training stability.

These query-key alignment scores are then typed in to a *[softmax function](https://victorzhou.com/blog/softmax/).* Softmax normalizes all inputs to a value between 0 and 1 such that they all add up to 1. The outputs of the softmax function are the *attention weights*, each representing the share (out of 1) of token *x*’s attention to be paid to each of the other tokens. If a token’s attention weight is close to 0, it will be ignored. An attention weight of 1 would mean that a token receives *x*’s entire attention and all others will be ignored.

Finally, the *value vector* for each token is multiplied by its attention weight. These attention-weighted contributions from each previous token are averaged together and added to the original vector embedding for token *x*. With this, token *x*’s embedding is now updated to reflect the context provided by the other tokens in the sequence that are relevant to it.

The updated vector embedding is then sent to another linear layer, with its own weight matrix *W*<sub>Z</sub>, where the context-updated vector is normalized back to a consistent number of dimensions and then sent to the next attention layer. Each progressive attention layer captures greater contextual nuance.

##### **Multiple attention heads**

Using the *averages* of attention-weighted contributions from other tokens instead of accounting for each piece of attention-weighted context individually is mathematically efficient, but it results in a loss of detail.

To compensate, the transformer networks split the original input token’s embedding into *h* evenly sized pieces. They likewise split *W<sub>Q</sub>, W<sub>K</sub> and W<sub>V</sub>* into *h* subsets called *query heads*, *key head* and *value heads*, respectively. Each query head, key head and value head receives a piece of the original token embedding. The vectors produced by each of these parallel triplets of query heads, key heads and value heads are fed into a corresponding *attention head.* Eventually, the outputs of these *h* parallel circuits are concatenated back together to update the full token embedding.

![Concatenation in multi-head attention](https://assets.ibm.com/is/image/ibm/multi-head-attention-concatenation?ts=1763388077315&dpr=off)   The outputs "Z" of each attention head are concatenated together. In this example, h=8.

In training, each circuit learns distinct weights that capture a separate aspect of semantic meanings. This, in turn, helps the model process the different ways that a word’s implications can be influenced by the context of other words around it.

![Diagram of multi-head attention block](https://assets.ibm.com/is/image/ibm/transformer_multi-headed_self-attention-recap?ts=1763388077844&dpr=off)   Simplified diagram of all the matrix multiplication in a multi-head attention block (h=8). Derived from Jay Alammar's "The Illustrated Transformer." Note that "+" refers to concatenation, rather than addition.

### Disadvantages of standard multi-head attention

The downside of standard multi-head attention is not so much the presence of some crucial flaw, but rather the lack of any optimization. MHA was the first algorithm of its kind and represents the most complex execution of its general mechanism for attention computation.

Most of MHA’s inefficiency stems from the abundance of calculations and model parameters. In standard MHA, each query head, key head and value head in each attention block has its own matrix of weights. So, for instance, a model with 8 attention heads in each attention layer—far fewer than most modern LLMs—would require 24 unique weight matrices for the layer's Q, K and V heads alone. This entails a huge number of intermediate calculations at each layer.

One consequence of this configuration is that it’s computationally expensive. Compute requirements for MHA scale quadratically with respect to sequence length: doubling the number of tokens in an input sequence requires quadruple the complexity. This puts hard practical limits on the size of [context windows](https://www.ibm.com/think/topics/context-window).

MHA also puts a major strain on system memory. GPUs don’t have much on-board memory to store the outputs of the massive quantity of intermediate calculations that must be recalled at each subsequent processing step. These intermediate results are instead stored in *high-bandwidth memory* (HBM), which isn’t located on the GPU chip itself. This entails a small amount of latency each time keys and values must be read from memory. As transformer models began to scale to many billions of parameters, the time and compute required to train and run inference became a bottleneck on model performance.

Further progress required methods to reduce the number of computational steps without reducing the capacity of transformers to learn and reproduce intricately complex linguistic patterns. It was in this context that MQA, and subsequently GQA, were introduced.

## How multi-query attention (MQA) works

Multi-query attention (MQA) is a more computationally efficient attention mechanism that simplifies multi-head attention to reduce memory usage and intermediate calculations. Instead of training a unique key head and value head for each attention head, MQA uses a *single* key head and *single* value head at each layer. Therefore, key vectors and value vectors are calculated only once; this single set of key and value vectors is then shared across all *h* attention heads.

This simplification greatly reduces the number of linear projections that the model must calculate and store in high-bandwidth memory. According to [the 2019 paper that introduced MQA](https://arxiv.org/abs/1911.02150), MQA allows a 10–100 times smaller key-value pair storage (or *KV cache*) and 12 times faster decoder inference. MQA’s reduced memory usage also significantly speeds up training by enabling a larger batch size.

![Diagram of grouped query attention](https://assets.ibm.com/is/image/ibm/mqa-and-mha?ts=1763388078735&dpr=off)

### Disadvantages of multi-query attention (MQA)

Despite its benefits, MQA comes with several unavoidable downsides.

- *Performance degradation:* Unsurprisingly, reducing the number of unique, trainable model parameters reduces the model’s capacity for knowledge and nuance. MQA entails a meaningful drop in accuracy compared to standard MHA, making it unsuitable for certain situations and use cases.
- *Must be trained from scratch*: A model trained with standard MHA cannot be simply adapted to MQA, but must instead be trained with MQA from scratch. This means MQA cannot be used to optimize existing models and entails a considerable opportunity cost when experimenting with MQA for new models.
- *Redundancies in tensor parallelism*: One of the main benefits of training transformer models on GPUs is the ability to perform multiple complex tensor operations in parallel. K and V values must be present on each node of the GPU cluster performing these operations, which means that in practice they must be replicated for each node. This is not an optimal use of compute resources despite still being more efficient than standard MHA.

## How grouped query attention (GQA) works

Grouped query attention is a more general, flexible formulation of multi-query attention that partitions query heads into multiple *groups* that each share a set of keys and values, rather than sharing one set of keys and values across all query heads.[](https://www.ibm.com/new/ibm-granite-3-0-open-state-of-the-art-enterprise-models)

Following the publication of [“GQA: Training Generalized Multi-Query Transformer Models from Multi-Head Checkpoints”](https://arxiv.org/abs/2305.13245) in May 2023, many LLMs quickly adopted GQA. For instance, Meta first adopted GQA for its [Llama 2](https://www.ibm.com/topics/llama-2) models in July 2023 and retained GQA in the [Llama 3 models](https://www.ibm.com/blog/meta-releases-llama-3-1-models-405b-parameter-variant/) released in 2024. [Mistral AI](https://www.ibm.com/think/topics/mistral-ai) used GQA in the Mistral 7B model that it released in September 2023. Likewise, [IBM’s Granite 3.0](https://www.ibm.com/new/ibm-granite-3-0-open-state-of-the-art-enterprise-models) models employ GQA for fast inference.

### Grouped query attention versus multi-query attention versus multi-head attention

In theory, GQA can be thought of as a generalization of the spectrum between standard MHA and full MQA. GQA with the same number of key-value head groups as attention heads is the equivalent of standard MHA; GQA with 1 head group is the equivalent of MQA.

In practice, GQA almost always implies some intermediate approach, in which the number of groups is itself an important hyperparameter.

![Diagram of grouped query attention](https://assets.ibm.com/is/image/ibm/mha-mqa-and-gqa?ts=1763388079755&dpr=off)

## Benefits of grouped query attention

Grouped query attention offers several advantages that have led to its relatively widespread adoption for leading LLMs.

- *Efficient GPU usage:* GQA’s distribution of key-value pairs takes advantage of tensor parallelism, reducing the amount of compute that’s “wasted” by replicating redundant values.
- *Effective compromise:* GQA offers an ideal tradeoff between decoder inference speed and performance accuracy, in that it's nearly as accurate as MHA while being nearly as fast as MQA.
- *Reduced memory bandwidth overhead*: Like MQA, GQA significantly reduces the number of intermediate calculations that must be computed, stored and retrieved at inference time.
- *Flexible training:* Unlike MQA, group query attention doesn’t require models to be trained from scratch using the approach. Models pretrained using standard MHA can be adapted to use GQA through a fine-tuning process called “uptraining.”
