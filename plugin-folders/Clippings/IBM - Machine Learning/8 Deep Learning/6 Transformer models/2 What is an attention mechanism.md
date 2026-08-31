---
title: What is an attention mechanism?
source: https://www.ibm.com/think/topics/attention-mechanism
author:
- '[[Dave Bergmann]]'
- '[[Cole Stryker]]'
published: 2024-12-13
created: 2026-08-31
description: "An attention mechanism is a machine learning technique that directs deep learning models, like transformers, to focus on the most relevant parts of input data."
---

## What is an attention mechanism?

An attention mechanism is a [machine learning](https://www.ibm.com/think/topics/machine-learning) technique that directs [deep learning](https://www.ibm.com/think/topics/deep-learning) models to prioritize (or *attend to*) the most relevant parts of input data. Innovation in attention mechanisms enabled the transformer architecture that yielded the modern [large language models (LLMs)](https://www.ibm.com/think/topics/large-language-models) that power popular applications like ChatGPT.

As their name suggests, attention mechanisms are inspired by the ability of humans (and other animals) to selectively pay more attention to salient details and ignore details that are less important in the moment. Having access to *all* information but focusing on only the *most relevant* information helps to ensure that no meaningful details are lost while enabling efficient use of limited memory and time.

Mathematically speaking, an attention mechanism computes *attention weights* that reflect the relative importance of each part of an input sequence to the task at hand. It then applies those attention weights to increase (or decrease) the influence of each part of the input, in accordance with its respective importance. An attention model—that is, an [artificial intelligence model](https://www.ibm.com/topics/ai-model) that employs an attention mechanism—is trained to assign accurate attention weights through [supervised learning](https://www.ibm.com/topics/supervised-learning) or [self-supervised learning](https://www.ibm.com/topics/self-supervised-learning) on a large dataset of examples.

Attention mechanisms were originally introduced by Bahdanau *et al* in 2014 as a technique to address the shortcomings of what were then state-of-the-art [recurrent neural network (RNN)](https://www.ibm.com/topics/recurrent-neural-networks) models used for machine translation. Subsequent research integrated attention mechanisms into the [convolutional neural networks (CNNs)](https://www.ibm.com/topics/convolutional-neural-networks) used for tasks such as image captioning and visual question answering.

In 2017, the seminal paper [“Attention is All You Need”](https://proceedings.neurips.cc/paper_files/paper/2017/file/3f5ee243547dee91fbd053c1c4a845aa-Paper.pdf) introduced the *transformer model*, which eschews recurrence and convolutions altogether in favor of only attention layers and standard feedforward layers. The transformer architecture has since become the backbone of the cutting-edge models powering the ongoing era of [generative AI](https://www.ibm.com/topics/generative-ai).

While attention mechanisms are primarily associated with LLMs used for [natural language processing (NLP)](https://www.ibm.com/think/topics/natural-language-processing) tasks, such as [summarization](https://www.ibm.com/think/topics/text-summarization), question answering, [text generation](https://www.ibm.com/think/topics/text-generation) and [sentiment analysis](https://www.ibm.com/think/topics/sentiment-analysis), attention-based models are also used widely in other domains. Leading [diffusion models](https://www.ibm.com/think/topics/diffusion-models) used for image generation often incorporate an attention mechanism. In the field of computer vision, vision transformers (ViTs) have achieved superior results on tasks including [object detection](https://www.ibm.com/think/topics/object-detection),<sup>1</sup> [image segmentation](https://www.ibm.com/think/topics/image-segmentation)<sup>2</sup> and visual question answering.<sup>3</sup>

## Why are attention mechanisms important?

Transformer models and the attention mechanisms that power them have achieved state-of-the-art results across nearly every subdomain of deep learning. The nature of attention mechanisms gives them significant advantages over the convolution mechanisms used in convolutional neural networks (CNNs) and recurrent loops used in recurrent neural networks (RNNs).

- *Flexibility over time:* The way RNNs process sequential data is inherently *serialized*, meaning that they process each timestep in a sequence individually in a specific order. This makes it difficult for an RNN to discern correlations—called *dependencies*, in the parlance of data science—that have many steps in between them. Attention mechanisms, conversely, can examine an entire sequence simultaneously and make decisions about the order in which to focus on specific steps.
- *Flexibility over space*: CNNs are inherently *local*, using [convolutions](https://developer.ibm.com/articles/introduction-to-convolutional-neural-networks/) to process smaller subsets of input data one piece at a time. This makes it difficult for a CNN to discern dependencies that are far apart, such as correlations between words (in text) or pixels (in images) that aren’t neighboring one another. Attention mechanisms don’t have this limitation, as they process data in an entirely different way.
- *Parallelization*: The nature of attention mechanisms entails many computational steps being done at once, rather than in a serialized manner. This, in turns, enables a high degree of parallel computing, taking advantage of the power and speed offered by [GPUs](https://www.ibm.com/think/topics/gpu).

To understand how attention mechanisms in deep learning work and why they helped spark a revolution in generative AI, it helps to first understand why attention was first introduced: to improve the RNN-based Seq2Seq models used for machine translation.

### How Seq2Seq works without attention mechanisms

RNNs are neural networks with *recurrent loops* that provide an equivalent of “memory,” enabling them to process sequential data. RNNs intake an ordered *sequence* of input vectors and process them in timesteps. After each timestep, the resulting network state—called the *hidden state*—is provided back to the loop, along with the next input vector.

RNNs quickly suffer from [vanishing or exploding gradients](https://www.ibm.com/think/topics/gradient-descent#Challenges+with+gradient+descent) in training. This made RNNs impractical for many NLP tasks, as it greatly limited the length of input sentences they could process.<sup>4</sup> These limitations were somewhat mitigated by an improved RNN architecture called [long short term memory networks (LSTMs)](https://video.ibm.com/recorded/131507960), which add gating mechanisms to preserve “long term” memory.

Before attention was introduced, the Seq2Seq model was the state-of-the-art model for machine translation. Seq2Seq uses two LSTMs in an [encoder-decoder architecture](https://www.ibm.com/think/topics/encoder-decoder-model).

- The first LSTM, the **encoder**, processes the source sentence step by step, then outputs the hidden state of the final timestep. This output, the *context vector*, encodes the whole sentence as one [vector embedding](https://www.ibm.com/think/topics/vector-embedding). To enable Seq2Seq to flexibly handle sentences with varying numbers of word, the context vector is always the same length.
- The second LSTM, the **decoder**, takes the vector embedding output by the encoder as its initial input and *decodes* it, word by word, into a second language.

Encoding input sequences in a fixed number of dimensions allowed Seq2Seq to process sequences of varying length, but also introduced important flaws:

- It represents long or complex sequences with the same level of detail as shorter, simpler sentences. This causes an information bottleneck for longer sequences and wastes resources for shorter sequences.
- This vector represents only the final hidden state of the encoder network. In theory, each subsequent hidden state should contain information provided by the previous hidden state, which in turn contains information from the prior time step, and so on, back to the first step. In practice, the context vector inevitably “forgets” information from early time steps, hindering model performance on lengthier sequences.

### How attention mechanisms improved Seq2Seq

Bahdanau *et al* proposed an attention mechanism in their 2014 paper, “Neural Machine Translation by Jointly Learning to Align and Translate,” to improve communication between the encoder and decoder and remove that information bottleneck.

Instead of passing along only the *final* hidden state of the encoder—the context vector—to the decoder, their model passed *every* encoder hidden state to the decoder. The attention mechanism itself was used to determine which hidden state—that is, which word in the original sentence—was most relevant at each translation step performed by the decoder.

“This frees the model from having to encode a whole source sentence into a fixed-length vector, and also lets the model focus only on information relevant to the generation of the next target word,” the paper explained. “This has a major positive impact on the ability of the neural machine translation system to yield good results on longer sentences."<sup>5</sup>[](#_ftn1)

Subsequent NLP research focused primarily on improving performance and expanding use cases for attention mechanisms in recurrent models. The 2017 invention of transformer models, powered solely by attention, eventually made RNNs all but obsolete for NLP.

## How do attention mechanisms work?

An attention mechanism’s primary purpose is to determine the relative importance of different parts of the input sequence, then influence the model to *attend to* important parts and disregard unimportant parts.

Though there are many variants and categories of attention mechanisms, each suited to different use cases and priorities, all attention mechanisms feature three core processes:

1. A process of “reading” raw data sequences and converting them into [vector embeddings](https://www.ibm.com/think/topics/vector-embedding), in which each element in the sequence is represented by its own feature vector(s).
2. A process of accurately determining similarities, correlations and other dependencies (or lack thereof) between each vector, quantified as *alignment scores* (or *attention scores*) that reflect how aligned (or not aligned) they are*.* Alignment scores are then used to compute *attention weights* by using a softmax function, which normalizes all values to a range between 0–1 such that they all add up to a total of 1. So for instance, assigning an attention weight of 0 to an element means it should be ignored. An attention weight of 1 means that element should receive 100% attention because all other elements would have attention weights of 0 (because all weights must sum up to 1). In essence, the output of a softmax function is a *probability distribution.*
3. A process of using those attention weights to emphasize or deemphasize the influence of specific input elements on how the model makes predictions. In other words, a means of using attention weights to help models focus on or ignore information.

#### **Queries, keys and values**

The seminal “Attention is All You Need” paper articulated its attention mechanism by using the terminology of a [relational database](https://www.ibm.com/think/topics/relational-databases): **queries**, **keys** and **values**. Relational databases are designed to simplify the storage and retrieval of relevant data: they assign a unique identifier (“key”) to each piece of data, and each *key* is associated with a corresponding *value.* In NLP, a model’s “database” is the vocabulary of tokens it has learned from its training dataset.

The massive influence of the “Attention is All You Need” paper has resulted in even previous attention mechanisms often being retroactively described in these terms. Generally speaking, this conception of attention entails interaction between three types of vector representations for each [token](https://www.ibm.com/docs/en/watsonx/saas?topic=solutions-tokens) in a sequence.

- The *query vector* represents the information a given token is seeking.
- The *key vectors* represent the information that each token contains. Alignment between query and key is used to compute attention weights.
- The *value* (or *value vector*) applies the attention-weighted information from the key vectors. Contributions from keys that are strongly aligned with a query are weighted more heavily; contributions from keys that are not relevant to a query will be weighted closer to zero.

Specific attention mechanism variants are differentiated primarily by how vectors are encoded, how alignment scores are calculated and attention weights are applied to provide the model with relevant information.

### Additive attention

Badhanau’s attention mechanism was designed specifically for machine translation. It uses a *bidirectional* RNN to encode each input token, processing the input sequence in both the forward direction and in reverse and concatenating the results together. This approach is particularly useful when, for example, the original and translated languages have different ordering conventions for nouns and adjectives.

Here, the decoder hidden state at each timestep of the translated sentence is the equivalent of a *query vector* and the encoder hidden state at each step in the source sentence is the equivalent of a *key vector.*

Alignment scores are then determined by a simple feedforward neural network, the *attention layer*, jointly trained with the rest of the model. This attention layer comprises up to three subsets of learnable model weights: query weights for the hidden decoder states (“*W*<sub>q</sub>”), key weights for hidden encoder states (“*W*<sub>k</sub>”) and value weights to scale the final output (“*w*<sub>v</sub>”). These weights are the model’s “knowledge”: by adjusting the specific values of those weights during training to minimize a [loss function](https://www.ibm.com/think/topics/loss-function), the model learns to make accurate translations.

At each step, additive attention works as follows:

- The query vector (multiplied by *W<sub>q</sub>*) is *added* to a key vector (multiplied by *W<sub>k</sub>*). If they are aligned, adding them together will yield a large value. If they’re irrelevant to one another, adding them together will yield a small value or negative value.
- The resulting number is input to a [*$tanh$* activation function](https://huggingface.co/papers/trending), which maps all inputs to a number between -1 and 1.
- The output of the $tanh$ function is then multiplied by the value weights *w*<sub>v</sub>*.* This yields the *alignment score* between the query vector and that key vector.
- The alignment score is then input to a softmax function, which yields an attention weight for that key vector.

The context vector that the decoder uses to generate the translated sentence is calculated as the attention-weighted sum of each key vector. One benefit of additive attention is that it does not require query and key vectors to be the same length.

### Dot product attention

In 2015, Luong *et al* introduced several novel methodologies to simplify and enhance Badhanau’s attention mechanism for machine translation. Perhaps their most notable contribution was a new alignment score function that used *multiplication* instead of addition. It also eschewed the *$tanh$* function, calculating the similarity between hidden state vectors by using their [dot product](https://en.wikipedia.org/wiki/Dot_product). For that reason, it’s often called *dot product attention* or *multiplicative attention.*

The intuition behind using dot product to compare query vectors is both mathematical and pragmatic:

- If the $Q$ and $K$ vectors are aligned—that is, if a query and key are similar in meaning to one another—multiplying them will yield a large value. After softmax, this large value results in a large attention weight for that key. If they are not well aligned, their dot product will be small or negative, and the subsequent softmax function will result in a small attention weight.
- In practice, multiplication is much faster and more computationally efficient for neural networks than additive operations, as it can implemented in fewer steps by using [matrix multiplication](https://www.redbooks.ibm.com/redpapers/pdfs/redp5612.pdf).<sup>6</sup>[](#_ftn1)

One consequence of using dot product attention is that dot product calculations require both vectors to have the same number of dimensions, $d_k$ .

Whereas additive attention proceeds to calculate the context vector as the weighted *sum* of key vectors, dot product attention computes the context vector as the weighted *average* of key vectors.

### Scaled dot product attention

The authors of “Attention is All You Need” noted that while dot product attention is faster and more computationally efficient than additive attention, additive attention outperforms traditional dot-product attention for longer vectors.

They theorized that when $d_k$ is very large, the resulting dot products are also very large. When the softmax function squishes all those very large values to fit between 0–1, [backpropagation](https://www.ibm.com/think/topics/backpropagation) yields extremely small gradients that are difficult to optimize. Experimentation revealed that scaling the dot product of two vectors of length $d_k$ by $\frac{1}{\sqrt{d_k}}$ before softmax normalization results larger gradients and therefore, smoother training.

The scaled dot-product attention function used in transformer models is written as $Attention(Q, K, V) = softmax(\frac{QK^T}{\sqrt{d_k}})V$ .

## Self-attention

The earliest types of attention mechanisms all performed what is now categorized as *cross-attention.* In cross-attention, queries and keys come from different data sources. For instance, in machine translation tasks the keys come from a text corpus in one language and the queries from another language; in speech recognition tasks, queries are audio data and keys are text data to transcribe that audio.

In *self-attention*, queries, keys and values are all drawn from the same source. Whereas both Bahdanau and Luong’s attention mechanisms were explicitly designed for machine translation, Cheng *at al* proposed *self-attention—*which they called “intra-attention”—as a method to improve machine reading in general. Their attention mechanism, outlined in [a 2016 paper](https://arxiv.org/abs/1601.06733), explored not how input elements contribute to an overall sequence, but how different input tokens relate *to each other.*

Consider a language model interpreting the English text  
 “on Friday, the judge issued a sentence.”

- The preceding word`the` suggests that`judge` is acting as a noun—as in, *person presiding over a legal trial*—rather than a verb meaning *to appraise or form an opinion*.
- That context for the word`judge` suggests that`sentence` probably refers to a legal penalty, rather than a grammatical “sentence.”
- The word`issued` further implies that sentence is referring to the legal concept, not the grammatical concept.
- Therefore, when interpreting the word`sentence` , the model should *pay close attention to* `judge` and`issued` . It should also pay some attention to the word`the` . It can more or less ignore the other words. A well-trained self-attention mechanism would compute attention weights accordingly.

Cheng *et al*’s paper focused solely on self-attention’s capacity to read and understand text, but it soon followed that modeling intrasequence relationships could also be a powerful tool for *writing* text. Further development of self-attention, along with the transformer models it enabled, led directly to the advent of modern generative AI and [autoregressive](https://www.ibm.com/think/topics/autoregressive-model) LLMs that can generate original text.

#### Self-attention and machine translation

Autoregressive LLMs can also perform machine translation by using self-attention, but must approach the task differently. Whereas cross-attention treats the original source sentence and the translated sentence as two distinct sequences, self-attention treats the original text and the translated text as one sequence.

For an autoregressive, self-attention-based LLM to be capable of translating text, all of the words the model encounters in training—across every language—are learned as part of one large multilingual token vocabulary. The model simply realizes that when a sequence contains instructions like “*translate [words in Language 1] into Language 2*,” the next words in the sequence should be tokens from Language 2.

In essence, an autoregressive LLM doesn’t necessarily understand that there are different languages by itself. Instead, it simply understands how certain groupings of tokens—in this case, tokens corresponding to words from the same language—*attend* to one another. This contextual understanding is further reinforced through techniques such as [instruction tuning](https://www.ibm.com/think/topics/instruction-tuning).

## Attention in transformer models

The “Attention is All You Need” paper, authored by Viswani *et al,* took inspiration from self-attention to introduce a new neural network architecture: **the transformer.** Their transformer model eschewed convolutions and recurrence altogether, and instead used only attention layers and standard linear feedforward layers.

The authors’ own model followed an encoder-decoder structure, similar to that of its RNN-based predecessors. Later transformer-based models departed from that encoder-decoder framework. One of the first landmark models released in the wake of the transformers paper, [BERT](https://www.ibm.com/think/insights/how-bert-and-gpt-models-change-the-game-for-nlp) (short for bidirectional encoder representations from transformers), is an encoder-only model. The autoregressive LLMs that have revolutionized text generation, such as GPT (Generative Pretrained Transformer) models, are decoder-only.

“Attention is All You Need” proposed several innovations to the attention mechanism—one of which was scaled dot product attention—to improve performance and adapt attention to an entirely new model structure.

### Positional encoding

The relative order and position of words can have an important influence on their meanings. Whereas RNNs inherently preserve information about the position of each token by computing hidden states serially, one word after the other, transformer models must explicitly encode positional information.

With *positional encoding,* the model adds a vector of values to each token’s embedding, derived from its relative position, before the input enters the attention mechanism. This positional vector typically has much fewer dimensions than the token embedding itself, so only a small subset of the token embedding will receive positional information. The math is somewhat complex, but the logic is simple:

- The nearer two tokens are, the more similar their positional vectors will be.
- The more similar their respective positional vectors are, the more the similarity between their respective token embeddings will increase after adding those positional vectors.
- The more similar their positionally updated embeddings are, the greater their alignment score will be, resulting in a larger attention weight between those two tokens. Thus the model learns to pay more self-attention to nearby tokens.

Viswani *et al* designed a simple algorithm that uses a sine function for tokens in even positions and cosine for tokens in odd positions. Later algorithms, such as rotary positional encoding (RoPE), improved the ability to effective encode positional information for very long sequences—which, in turn, has helped enable LLMs with larger [context windows](https://www.ibm.com/think/topics/context-window).

### Self-attention mechanism in transformer models

Once each token embedding has been updated with positional information, each is used to generate three new vectors by passing the original token embedding through each of three parallel linear (feedforward) neural network layers that precede the first attention layer. Each parallel layer has a unique matrix of weights whose specific values are learned through self-supervised pretraining on a massive dataset of text.

- The embedding is multiplied by the weight matrix $W_Q$ to yield the *query vector* ($Q$), which has $d_k$ dimensions
- The embedding is multiplied by the weight matrix $W_K$ to yield the key vector ($K$), also with dimensions $d_k$
- The embedding is multiplied by the weight matrix $W_V$ to yield the value vector ( $V$ ), with dimensions $d_v$

![A diagram of a transformer model's attention mechanism](https://assets.ibm.com/is/image/ibm/self-attention-matrix-calculation?ts=1785852352484&dpr=off)   A simplified diagram of the transformer's attention mechanism: the original vector embeddings for the tokens of an input sentence are multiplied by W, K and V weight matrices to yield their respective W, K and V vectors.

The attention mechanism’s primary function is to weight the importance of the query-key pairings between each token. For each token *x* in an input sequence, the transformer model computes (and then applies) attention weights as follows:

1. Token *x*’s query vector $Q_x$ is multiplied by each other token’s key vector $K$. The resulting dot product will be large for a token that’s highly relevant; its dot product with an irrelevant token will be small or negative.
2. Each dot product will be *scaled*—that is, multiplied—by $\frac{1}{\sqrt{d_k}}$. The result is the *alignment score* between token *x* and each other token.
3. These alignment scores are input to a softmax function, which normalizes each score to a value between 0–1, such that they all add up to 1. These are the *attention weights* between token *x* and each other token. You can think of each token as now having a corresponding vector of attention weights, in which each element of that vector represents the extent to which some other token should influence it.
4. Each other token’s *value vector* is now multiplied by its respective attention weight.
5. These attention-weighted value vectors are all averaged together. The resulting vector represents the average of all the attention-weighted contributions from each key vector.
6. Finally, the resulting vector of changes for each token is added to token *x’s* original vector embedding. In essence, token x’s vector embedding has been updated to better reflect the context provided by the other tokens in the sequence.

### Multihead attention

*Averaging* the attention-weighted contributions from other tokens instead of accounting for each attention-weighted contribution individually is mathematically efficient, but it results in a loss of detail. The transformer architecture addresses this by implementing *multihead attention.*

To enjoy the efficiency of averaging while still accounting for multifaceted relationships between tokens, transformer models compute self-attention operations multiple times in parallel at each attention layer in the network. Each original input token embedding is split into *h* evenly sized subsets. Each piece of the embedding is fed into one of *h* parallel matrices of *Q, K* and *V* weights, each of which are called a *query* head, *key head* or *value head*, respectively. The vectors output by each of these parallel triplets of query, key value heads are then fed into a corresponding *attention head.*

![Diagram of multi-head attention](https://assets.ibm.com/is/image/ibm/multi-head-attention?ts=1785852353479&dpr=off)   The simplified multi-head attention diagram made famous in "Attention is All You Need"

In the final layers of each *attention block*, the outputs of these *h* parallel circuits are eventually concatenated back together. In practice, model training results in each circuit learning different weights that capture a separate aspect of semantic meanings. This, in turn, lets the model process different ways that context from other words can influence a word’s meaning. For instance, one attention head might specialize in changes in tense, while another specializes in how nearby words influence tone.

![Concatenation in multi-head attention](https://assets.ibm.com/is/image/ibm/multi-head-attention-concatenation?ts=1785852354353&dpr=off)   The outputs "Z" of each attention head are concatenated together. In this example, h = 8.

The entire circuit of matrix multiplication in the attention block of a standard transformer is demonstrated here. It's worth noting that later evolutions of the transformer's attention mechanism, such as multiquery attention and grouped query attention, simplify or combine some elements of the process to reduce computational demands.

![Diagram of multi-head attention block](https://assets.ibm.com/is/image/ibm/transformer_multi-headed_self-attention-recap?ts=1785852355055&dpr=off)   Simplified diagram of all the matrix multiplication in a multi-head attention block (h = 8), derived from Jay Alammar's "The Illustrated Transformer." Note that here, "+" signifies concatenation, not addition.

### Generating outputs

In the final few layers of transformer models, attention heads are often trained to make specific predictions. For instance, one attention head in the final layer of an LLM might specialize in [named entity recognition](https://www.ibm.com/think/topics/named-entity-recognition), while another specializes in sentiment analysis, and so on.

In autoregressive LLMs, the penultimate layer is a linear layer that receives the fully transformed vector and projects it to a size matching that of the vector embeddings the model has learned for each token in its vocabulary. This allows for the computation of scores representing how closely the resulting vector matches each token in that vocabulary. The final layer is a softmax layer, which converts those scores into probabilities (out of 1) and uses those probabilities to output what it determines to be the most likely next word, based on the words that preceded it.

## Footnotes

1. [“Leaderboard: Object Detection on COCO test-dev,”](https://paperswithcode.com/sota/object-detection-on-coco) Papers With Code, accessed 18 November 2024  
 2. [“Leaderboards: Image Segmentation”](https://paperswithcode.com/task/image-segmentation) Papers With Code, accessed 18 November 2024  
 3. [“Leaderboard: Visual Question Answering (VQA) on VQA v2 test-dev,”](https://paperswithcode.com/sota/visual-question-answering-on-vqa-v2-test-dev) Papers With Code, accessed 18 November 2024  
 4. [“Learning long-term dependencies with gradient descent is difficult,”](https://www.researchgate.net/publication/5583935_Learning_long-term_dependencies_with_gradient_descent_is_difficult) IEE Transactions on Neural Networks 5(2): 157-66, February 1994  
 5. [“Neural Machine Translation by Jointly Learning to Align and Translate,”](https://arxiv.org/abs/1409.0473) arXiv, 1 September 2014  
 6. [“Multiplicative Attention,”](https://paperswithcode.com/method/multiplicative-attention) Papers With Code
