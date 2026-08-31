---
title: What is an encoder-decoder model?
source: https://www.ibm.com/think/topics/encoder-decoder-model
author:
- '[[Jacob Murel Ph.D.]]'
- '[[Joshua Noble]]'
published: 2024-12-02
created: 2026-08-31
description: "Learn about the encoder-decoder model architecture and its various use cases."
---

Encoder-decoder is a type of neural network architecture used for sequential data processing and generation.

In [deep learning](https://www.ibm.com/think/topics/deep-learning), the encoder-decoder architecture is a type of [neural network](https://www.ibm.com/think/topics/neural-networks) most widely associated with the [transformer architecture](https://www.ibm.com/think/topics/transformer-model) and used in sequence-to-sequence learning. Literature thus refers to encoder-decoders at times as a form of sequence-to-sequence model ([seq2seq model](https://arxiv.org/abs/1409.3215)). Much [machine learning](https://www.ibm.com/think/topics/machine-learning) research focuses on encoder-decoder models for [natural language processing (NLP)](https://www.ibm.com/think/topics/natural-language-processing) tasks involving [large language models (LLMs).](https://www.ibm.com/think/topics/large-language-models)

Encoder-decoder models are used to handle sequential data, specifically mapping input sequences to output sequences of different lengths, such as neural machine translation, [text summarization](https://www.ibm.com/think/topics/text-summarization), image captioning and [speech recognition](https://www.ibm.com/think/topics/speech-recognition). In such tasks, mapping a token in the input to one in the output is often indirect. For example, take machine translation: in some languages, the verb appears near the beginning of the sentence (as in English), in others at the end (such as German) and in some, the location of the verb may be more variable (for example, Latin). An encoder-decoder network generates variable length yet contextually appropriate output sequences to correspond to a given input sequence.<sup>[1](#F1)</sup>

## The encoder-decoder architecture

As may be inferred from their respective names, the encoder encodes a given input into a vector representation, and the decoder decodes this vector into the same data type as the original input dataset.

Both the encoder and decoder are separate, fully connected neural networks. They may be [recurrent neural networks (RNNs)](https://www.ibm.com/think/topics/recurrent-neural-networks)—plus its variants long-short term memory (LSTM), gated recurrent units (GRUs)—and [convolutional neural networks (CNNs)](https://www.ibm.com/think/topics/convolutional-neural-networks), as well as transformer models. An encoder-decoder model typically contains several encoders and several decoders.

![Diagram of encoder-decoder architecture ](https://assets.ibm.com/is/image/ibm/trans-architecture-image?ts=1763387626965&dpr=off)

Each encoder consists of two layers: the self-attention layer (or self-attention mechanism) and the feed-forward neural network. The first layer guides the encoder in surveying and focusing on other related words in a given input as it encodes one specific word therein. The feed-forward neural network further processes encodings so they are acceptable for subsequent encoder or decoder layers.

The decoder part also consists of a self-attention layer and feed-forward neural network, as well as an additional third layer: the encoder-decoder attention layer. This layer focuses network attention on specific parts of the output of the encoder. The multi-head attention layer thereby maps tokens from two different sequences.<sup>[2](#F2)</sup>[<sup></sup>](#_edn1)

![Diagram of parts of encoder and decoder stacks](https://assets.ibm.com/is/image/ibm/encoder-decoder-image?ts=1763387627154&dpr=off)

## How encoder-decoder models work

Literature widely presents encoder-decoder models as consisting of three components: the encoder, the context vector, and the decoder.<sup>[3](#F3)</sup>[](#_edn1)

### Encoder

The principal component of the encoder is the self-attention mechanism. The self-attention mechanism determines token weights in a text input to reflect inter-token relationships. In contrast to a traditional word embedding that ignores word order, self-attention processes the whole input text sequence to compute each token’s weighted average embedding that takes into account that token’s distance from all of the other tokens in the text sequence. It computes this average embedding as a linear combination of all embeddings for the input sequence according to following formula:

![Encoder input mathematical sequence formula despicting x prime sub i equals the sum from j equals 1 to n of w sub j i times x sub j](https://assets.ibm.com/is/image/ibm/input-sequence-linear-combination-formula?ts=1763387627569&dpr=off)

Here, *x<sub>j</sub>* is a given input token at the j-th position in the input text string and *x<sub>i</sub>* is the corresponding output token at the i-th position in the input text string. The coefficient *w<sub>ij</sub>* is the attention weight, which is computed using what is called the softmax function and represents how important is that token in the output text to the corresponding source sequence. In other words, this coefficient signals how much attention the encoder should give to each token in the output text with respect to original token’s importance in the source text.<sup>[4](#F4)</sup>[](#_edn1)

![Diagram showing word embeddings combined with positional encoding to create embeddings with time signal for three words: Alas, poor, Yorick](https://assets.ibm.com/is/image/ibm/tokenization-diagram-image?ts=1763387627759&dpr=off)

The encoder passes this token embedding to the feed-forward layer which adds a positional encoding (or, positional embedding) to the token embedding. This positional encoding accounts for the order of tokens in a text, specifically the distance between tokens. Together, this token embedding and positional embedding comprise the hidden state passed on to the decoder.<sup>[5](#F5)</sup>[](#_edn1)

### Context vector

Literature widely calls the encoder’s final hidden state the *context vector*. It is a condensed, numerical representation of the encoder’s initial input text. More simply, it is the embedding and positional encoding produced by the encoder for every word in the input sequence.

Literature often defines the context vector using the following function, in which the context vector X is defined as each token (*x*) at the *i*-th position in the input sequence:<sup>[6](#F6)</sup>[](#_edn1)

![Context vector function formula showing C equals a sequence of x values from 1 to n sub x](https://assets.ibm.com/is/image/ibm/context-vector-function?ts=1763387628101&dpr=off)

### Decoder

Much like the encoder, the decoder is comprised of a self-attention layer and feed-forward network. Between these, the decoder contains a multi-head attention masking layer. This marks the difference between the encoder and decoder. Whereas the encoder generates contextualized token embeddings simultaneously, the decoder’s multi-head attention layer utilizes autoregressive masking.

First, the decoder receives the context vector from the encoder. The decoder uses these positional embeddings to calculate attention scores for each token. These attention scores determine to what degree each token from the input sequence will affect later tokens therein; in other words, the scores determine how much weight each token has in other tokens’ determinations when generating output sequences.

One important feature of this, however, is that the decoder will not use future tokens to determine preceding tokens in that same sequence. Each token’s generated output depends only on the preceding tokens; in other words, when generating a token’s output, the decoder does not consider the next words or tokens after the current one. As is the case with many [artificial intelligence](https://www.ibm.com/think/topics/artificial-intelligence) techniques, this aims to mimic conventional understandings of how humans process information, specifically language. This approach to information processing is called autoregressive.<sup>[7](#F7)</sup>[](#_edn1)

![Diagram of autoregressive masking of Hamlet quotation](https://assets.ibm.com/is/image/ibm/autoregressive-image?ts=1763387628357&dpr=off)

## Why use encoder-decoder models in NLP?

One of the foremost advantages of encoder-decoder models for downstream NLP tasks like [sentiment analysis](https://www.ibm.com/think/topics/sentiment-analysis) or masked language modeling is its production of contextualized embeddings. These embeddings are distinct from fixed word embeddings used in [bag of words](https://www.ibm.com/think/topics/bag-of-words) models.

First, fixed embeddings do not account for word order. They thereby ignore relationships between tokens in a text sequence. Contextualized embeddings, however, account for word order via positional encodings. Moreover, contextualized embeddings attempt to capture the relationship between tokens through the attention mechanism that considers the distance between tokens in a given sequence when producing the embeddings.

Fixed embeddings generate one embedding for a given token, conflating all instances of that token. Encoder-decoder models produce contextualized embeddings for each token instance of a token. As a result, contextualized embeddings more adeptly handle polysemous words—that is, words with multiple meanings. For example, *flies* may signify an action or an insect. A fixed word embedding collapses this word’s multiple significations by creating a single embedding for the token or word. But an encoder-decoder model generates individual contextualized embeddings for every occurrence of the word *flies*, and so captures is myriad significations through multiple distinct embeddings.<sup>[8](#F8)</sup>[](#_edn1)

## Types of encoder-decoder variants

As may be expected, the encoder-decoder architecture has many variants, each with their own primary use cases in [data science](https://www.ibm.com/think/topics/data-science) and machine learning.

**Encoder-only.** These models (also described as auto-encoders) use only the encoder stack, eschewing decoders. Such models thus lack autoregressive masked modeling and have access to all the tokens in the initial input text. As such, these models are described as bi-directional, as they use all the surrounding tokens–both preceding and succeeding—to make predictions for a given token. Well-known encoder models are the BERT family of models, such as BERT,<sup>[9](#F9)</sup>[](#_edn1) RoBERTa,<sup>[10](#F10)</sup>[](#_edn2) and ELECTRA,<sup>[11](#F11)</sup>[](#_edn3) as well as the [IBM Slate models.](https://www.ibm.com/products/watsonx-ai/foundation-models) Encoder-only models are often utilized for tasks that necessitate understanding a whole text input, such as text classification or [named entity recognition](https://www.ibm.com/think/topics/named-entity-recognition).

**Decoder-only.** These models (also called autoregressive models) use only the decoder stack, foregoing any encoders. Thus, when making token predictions, the model’s attention layers can only access those tokens preceding the token under consideration. Decoder-only models are often used for text generation tasks like question answering, code writing, or chatbots such as ChatGPT. An example of a decoder-only model is the [IBM granite family](https://huggingface.co/ibm-granite) of foundational models.<sup>[12](#F12)</sup>[](#_edn4)

## Footnotes

<sup>1 </sup>Jurafsky, D. and Martin, J., [“Speech and Language Processing: An Introduction to Natural Language Processing, Computational Linguistics, and Speech Recognition”](https://web.stanford.edu/~jurafsky/slp3/), Third edition, 2023.

<sup>2 </sup>Telmo, P., Lopes, A. V., Assogba, Y. and Setiawan, H. [“One Wide Feedforward Is All You Need”](https://aclanthology.org/2023.wmt-1.98/) , 2023.  
 Vaswani, A., Shazeer, N., Parmar, N., Uszkoreit, J., Jones, L., Gomez, A. N., Kaiser, L. and Polosukhin I. [“Attention Is All You Need”](https://proceedings.neurips.cc/paper_files/paper/2017/hash/3f5ee243547dee91fbd053c1c4a845aa-Abstract.html), 2017.  
 Tunstall, L., Werra, L. and Wolf and T. “Natural Language Processing with Transformers”, Revised Edition, O’Reilly, 2022

<sup>3</sup> Goodfellow, I., Bengio, Y. and Courville, A. “Deep Learning”, MIT Press, 2016.  
 Jurafsky, D. and Martin, J. [“Speech and Language Processing”](https://web.stanford.edu/~jurafsky/slp3), Third Edition, 2023.  
 Tunstall, L., Werra, L. and Wolf and T. “Natural Language Processing with Transformers”, Revised Edition, O’Reilly, 2022.

<sup>4</sup> Tunstall, L., Werra, L. and Wolf and T. “Natural Language Processing with Transformers”, Revised Edition, O’Reilly, 2022.  
 Goldberg, Y. “Neural network methods for Natural Language Processing”, Springer, 2022.

<sup>5</sup> Alammar, J. and Grootendorst, M. “Hands-on Large Language Models”, O’Reilly, 2024.  
 <sup>  
 6</sup> Goodfellow, I., Bengio, Y. and Courville, A. “Deep Learning”, MIT Press, 2016.  
 Jurafsky, D. and Martin, J. [“Speech and Language Processing”](https://web.stanford.edu/~jurafsky/slp3), Third Edition, 2023.

<sup>7</sup> Foster, D. “Generative Deep Learning”, Second Edition, O’Reilly, 2023.  
 Rothman, D. “Transformers for Natural Language Processing”, Second Edition, 2022.   
 Jurafsky, D. and Martin, J. [“Speech and Language Processing”](https://web.stanford.edu/~jurafsky/slp3), Third Edition, 2023.

<sup>8</sup> Tunstall, L., Werra, L. and Wolf and T. “Natural Language Processing with Transformers”, Revised Edition, O’Reilly, 2022.

<sup>9</sup> Devlin, J. et all. [“BERT: Pre-training of Deep Bidirectional Transformers for Language Understanding”](https://aclanthology.org/N19-1423), 2019.

<sup>10</sup> Liu, Y., Ott, M., Goyal, N., Du, J., Joshi, M., Chen, D., Levy, O., Lewis, M. , Zettlemoyer, L. and Stoyanov, V. [“RoBERTa: A Robustly Optimized BERT Pretraining Approach”](https://arxiv.org/abs/1907.11692), 2019.

<sup>11</sup> Clark, K. et all. [“ELECTRA: Pre-training Text Encoders as Discriminators Rather Than Generators”](https://arxiv.org/abs/2003.10555), 2020.

<sup>12</sup> Mayank, M. et all. [“Granite Code Models: A Family of Open Foundation Models for Code Intelligence”](https://arxiv.org/abs/2405.04324) 2024.  
 Ruiz, A. [“IBM Granite Large Language Models Whitepaper”](https://community.ibm.com/community/user/watsonx/blogs/armand-ruiz-gabernet/2024/06/24/ibm-granite-large-language-models-whitepaper) 2024.
