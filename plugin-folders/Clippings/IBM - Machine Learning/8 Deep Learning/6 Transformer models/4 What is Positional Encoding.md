---
title: What is positional encoding?
source: https://www.ibm.com/think/topics/positional-encoding
author:
- '[[Fangfang Lee]]'
published: 2025-05-14
created: 2026-08-31
description: "Positional encoding is an important part of constructing the transformer architecture, which underlies all the modern LLMs we use today. Learning positional encoding will enable users to better tune, customize, and implement their models."
---

## What is positional encoding?

Positional encoding is a technique that injects information about the position of the words in a sequence to [transformer](https://www.ibm.com/think/topics/transformer-model) architectures.

The order of words plays a fundamental part in understanding the semantic meaning of a sentence. For example, “Allen walks dog” and “dog walks Allen” have entirely different meanings despite having the same words, or tokens. When implementing [natural language processing (NLP)](https://www.ibm.com/think/topics/natural-language-processing) applications by using [deep learning](https://www.ibm.com/think/topics/deep-learning) and [neural networks](https://www.ibm.com/think/topics/neural-networks), we need to create a mechanism by which machines can retain the orders of words in a sentence to produce logical output.

Traditionally, models such as [recurrent neural networks (RNNs)](https://www.ibm.com/think/topics/recurrent-neural-networks), or long short-term memories (LSTM), have a built-in mechanism that handles the order of words. RNNs and LSTMs process inputs sequentially, one token at a time, memorizing all positions of words in a sequence. In other words, the n-dimension vector, also called “input vector” is processed one after the other, inherently learning orders. In contrast, other architectures that take advantage of [convolutional neural networks (CNNs)](https://www.ibm.com/think/topics/convolutional-neural-networks) or transformers (Vaswani et al. 2017) do not retain word order and process tokens in parallel. Therefore, we need to implement a mechanism that can explicitly represent the order of words in a sequence—a technique known as positional encoding. Positional encoding allows the transformer to retain information of the word order, enabling parallelization and efficient model training. You can often find implementations of positional encoding on [GitHub](https://github.com/wzlxjtu/PositionalEncoding2D).

## Why does positional encoding matter?

The ordering of words in a sentence or a sequence dictates the inherent meaning of the sentence in natural languages. In addition, for machine learning, encoding the order of the word gives us a “dictionary” on where each word should be. This information is retained and can generalize throughout the training of transformer models, enabling parallelization and beating RNNs and LSTMs for its training efficiency.

Let's revisit the example:

- "Allen walks dog"
- "dog walks Allen"

These two sentences with the same three tokens have entirely different meanings based on the word orders. Transformers, which rely on [self-attention](https://www.ibm.com/think/topics/self-attention) and [multi-head attention mechanism](https://www.ibm.com/think/topics/attention-mechanism), do not have inherent representation of word orders, and would treat the individual word in a sequence identically if we did not provide explicit positional information. We want the model to understand who is doing the walking and who is being walked, which depends entirely on positions.

We achieve this objective by first processing each word as a vector that represents its meaning—for example, “dog” will be encoded in a high dimensional array that encodes its concept. In technical terms, each word or sub word is mapped to an input embedding of varying lengths. However, on its own, the meaning vector does not tell us where in the sentence dog appears. Positional encoding adds a second vector—one that encodes the position index, such as “first word”, or “second word”, and so on. The two vectors are then added to represent what the word is and where the word is. This resulting vector is often referred to as the positional encoding vector.

There are several ways of creating positional encoding. In this article, we explore the most well-known example of using a sinusoidal function introduced by authors in [Attention is all you need](https://proceedings.neurips.cc/paper_files/paper/2017/file/3f5ee243547dee91fbd053c1c4a845aa-Paper.pdf)<sup>[1](#f01)</sup> to create positional encoding.

## Positional encoding in transformers

In the original paper introduced by Vaswani *et al*. 2017, the key idea is to generate a fixed and deterministic encoding for each position in a sequence by using a *sinusoidal* function—particularly, the sine function $sin(x)$ and cosine function $cos(x)$ .

### What are sinusoidal functions?

The sine functions are a fundamental mathematical concept that produces a smooth, wavelength pattern. In particular, the cosine and sine functions are used by the authors in the original transformer functions to aid positional encoding.

If we plot $sin(x)$ and $cos(x)$ , we will see a curve that rises and falls between -1 and 1 in a repeating, periodic pattern.

A few properties of sine that make it powerful for positional encoding:

- It is **periodic**: It repeats regularly over intervals, which is useful for representing repeated patterns.
- It is **smooth** and **continuous**: Small changes in input result in small changes in output, which gives us a way to represent positions in a differentiable space.
- By varying the **frequency** of the wavelengths across dimensions, we can create a rich, multiscale representation of position.

Let us plot the sine and cosine waves to visualize what they look like:

The sine function

![Graph of the sine function, a repeating curve with a positive and negative range.](https://assets.ibm.com/is/image/ibm/sine-function?ts=1763388355422&dpr=off)

And now let's look at how we can plot the cosine function:

![A graph of the cosine function, illustrating its periodic nature and key characteristics.](https://assets.ibm.com/is/image/ibm/cosine-function?ts=1763388355652&dpr=off)

The sinusoidal position encoding formulae, defined by the authors of the original transformers paper (Vaswani et al. 2017), are shown as follows:

For even positions:

$$ PE_{pos,2i} = \sin\left( \frac{pos}{10000^{2i/d_{model}}} \right)
 $$

For odd positions:

$$ PE_{pos,2i+1} = \cos\left( \frac{pos}{10000^{2i/d_{model}}} \right)
 $$

- $k$ : The position of the word in the sentence (for example, 0 for the first word, 1 for the second, and so on.)

- $i$ : The dimension index of the embedding vector. maps to column index. 2i will indicate an even position and 2i+1 will indicate an odd position

- $d_{model}$ : The predefined dimensionality of the token embeddings (for example, 512)

- $n$ : user-defined scaler value (for example, 10000)

- $PE$ : position function for mapping position k in the input sequence to get the positional mapping

Using this formula, each word, at position k, will have an embedding value based on the position of the word. Take the example that we used, “Allen walks dog”, we can calculate the positional embedding for each word:

- $k_{1}$ = "Allen"

- $k_{2}$ = "walks"

- $k_{3}$ ="dog"

Let’s write a simple Python function to calculate the value of $PE(k)$ :

Once we called the function and input the corresponding value in our example, where the sequence length is 3, with a simplified dimension of $d = 4$ , and $n = 10000$

We get the following encoding matrix (also referred to as a tensor):

[[ 0. 1. 0. 1. ]

[ 0.84147098 0.54030231 0.09983342 0.99500417]

[ 0.90929743 -0.41614684 0.19866933 0.98006658]]

To represent this result more concretely, we get

Here we can see the concrete value of each word and their corresponding positional embedding value. However, we cannot use these word embeddings directly to interpret the order of words. The value calculated here is used to inject information about the position in an input vector of the transformer. Because the input of $sin(x)$ and $cos(x)$ are different, each position $k$ will respond to a different sinusoidal function. The corresponding position of the different sinusoidal function gives us information on the absolute position and relative position of the word in “Allen walks dog”. In other words, this information can be used by the model in such a way that the model can learn to associate these patterns with order, spacing and structure.

Now let's implement a python function to visualize the positional matrix

![Sinusoidal heatmap](https://assets.ibm.com/is/image/ibm/sinusoidal?ts=1763388356510&dpr=off)

## Final thoughts

As we can see with the different frequencies based on values of x, each corresponding position from the input word k will differ on a scale of $[-1.1]$ —the range of the $sin(x)$ function. From there our [encoder and decoder based](https://www.ibm.com/think/topics/encoder-decoder-model) transformer model will learn and preserve the different position encoding of each word, allowing the model to retain the information for training. The encoded position vector stays static through training, allowing for parallel computation.

## Footnotes

1. “[Attention Is All You Need](https://arxiv.org/abs/1706.03762v7)”, Ashish Vaswani et al., Proceedings of the 31st International Conference on Neural Information Processing Systems, arXiv:1706.03762v7, revised on 2 August 2023.

2. “[Long Short-Term Memories](https://dl.acm.org/doi/10.1162/neco.1997.9.8.1735)”, Sepp Hochreiter and Jürgen Schmidhuber. 1997. Long Short-Term Memory. Neural Comput. 9, 8 (November 15, 1997), 1735–1780.,

3. “[Foundations of Recurrent Neural Networks (RNNs) and Long Short-Term Memories](https://arxiv.org/abs/1808.03314)” Alex Sherstinsky et al., Elsevier “Physica D: Nonlinear Phenomena” journal, Volume 404, March 2020: Special Issue on Machine Learning and Dynamical Systems
