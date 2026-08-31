---
title: What is a Mamba model?
source: https://www.ibm.com/think/topics/mamba-model
author:
- '[[Dave Bergmann]]'
published: 2025-07-08
created: 2026-08-31
description: "Mamba is a neural network architecture derived from state space models (SSMs), used for language modeling and other sequence modeling tasks. Mamba-based LLMs rival the performance of transformers at greater efficiency."
---

## What is a Mamba model?

Mamba is a [neural network](https://www.ibm.com/think/topics/neural-networks) architecture, derived from [state space models (SSMs)](https://www.ibm.com/think/topics/state-space-model), used for language modeling and other sequence modeling tasks. The Mamba architecture’s fast inference speed and computational efficiency, particularly for long sequences, make it the first competitive alternative to the [transformer architecture](https://www.ibm.com/think/topics/transformer-model) for autoregressive [large language models (LLMs)](https://www.ibm.com/think/topics/large-language-models).

Mamba models are perhaps the first [deep learning](https://www.ibm.com/think/topics/deep-learning) architecture to rival the efficacy of transformer models on the task for which transformers originally won their fame: [language modeling](https://www.ibm.com/think/topics/natural-language-processing). Most notably, the Mamba architecture has demonstrated the capacity to match equivalently sized transformers on prominent [LLM benchmark evaluations](https://www.ibm.com/think/topics/llm-benchmarks) while often being significantly more efficient in terms of latency and memory requirements.

The Mamba architecture was first introduced by Tri Dao and Albert Gu in the 2023 paper, “Mamba: Linear-Time Sequence Modeling with Selective State Spaces.” A year later, they followed up the original Mamba paper with another paper that both explored the connections between SSMs and transformers and presented a refined, significantly faster version of the Mamba architecture, which they dubbed Mamba-2.

Though transformers have remained the dominant mode of LLM in the 2 years following the release of the original Mamba paper, the architecture has been incorporated into a growing number of open source models. Some, such as Mistral AI’s Codestral Mamba, are pure Mamba models. Many more, including AI2I’s Jamba series and [IBM Granite 4.0](https://www.ibm.com/new/announcements/ibm-granite-4-0-tiny-preview-sneak-peek), are hybrid models incorporating both [attention](https://www.ibm.com/think/topics/attention-mechanism) (transformer) layers and SSM (Mamba) layers. In addition to their performance-based benefits, the proliferation of Mamba-based models promises to democratize AI access by virtue of running smoothly on comparatively inexpensive hardware.

## What are state space models?

SSMs were originally designed to predict the next *state* of a continuous sequence, like an electrical signal, a weather pattern or the trajectory of a moving object, based on some input. Conceptually and mathematically, they’re related to the [recurrent neural networks (RNNs)](https://www.ibm.com/think/topics/recurrent-neural-networks) that dominated natural language processing (NLP) prior to the introduction of transformers in 2017, as well as to other machine learning algorithms including [convolutional neural networks (CNNs)](https://www.ibm.com/think/topics/convolutional-neural-networks) and hidden Markov models (HMMs).

As their name suggests, SSMs make predictions about the next state in a dynamic system by modeling the *[state space](https://www.ibm.com/think/topics/state-space-model#What+is+a+state+space)*: a [mathematical representation](https://www.ibm.com/think/topics/vector-embedding) of all the *state variables* that describe the state of a system and the range of possibilities for each of those variables in tandem with one another.

An SSM takes an input sequence *x*(*t*) and maps it to a [latent](https://www.ibm.com/think/topics/latent-space) state representation *h*(*t*)—analogous to the *hidden state* of an RNN—in order to predict an output sequence *y*(*t*). At the core of any SSM are 2 equations:

- **The state equation, $h'(t)=A*h(t)+B*x(t)$**
- **The output equation, $y(t)=C*h(t)+D*x(t)$**

The key parameters of the model are the A, B, C and D, which typically take the form of a matrix of weights. In the fields where SSMs are conventionally used, such as [control theory](https://en.wikipedia.org/wiki/Control_theory), these matrices are often assumed to be fixed: they represent the dynamics of an established system, and the SSM is used to find the inputs *x* that lead to desirable outputs *y.* In more modern conceptions of SSMs, those matrices are themselves parameters to be optimized through [machine learning](https://www.ibm.com/think/topics/machine-learning). In deep learning models, those matrices are represented by the learnable weights of a neural network.

#### The state equation

The *state equation* describes how the state changes. The values in matrix A determine how each state variable evolves over time if left to itself. The values in matrix B determine how the input—such as the next token in a text sequence—influences each state variable.

![Diagram of an SSM's state space equation](https://assets.ibm.com/is/image/ibm/mamba_state-space-equation_2_1ratio?ts=1763387608820&dpr=off)  The state equation. Illustration derived from Maarten Grootendorst's "A Visual Guide to Mamba and State Space Models"

In language modeling, the current state represents the context of a text sequence, updated after each token. Its role is equivalent to that of the KV cache in a transformer model.

#### The output equation

The *output equation* describes how the current state influences the output (as mediated by matrix C), as well as how the input influences the output directly (as mediated by matrix D). Because matrix D is essentially external to the modeling of *h*(t*)* itself, it’s often omitted from diagrams and discussions of SSMs in favor of focusing on the core matrices A, B and C.

![Diagram of SSM's output equation](https://assets.ibm.com/is/image/ibm/mamba_output-equation_2_1ratio?ts=1763387609234&dpr=off)  The output equation. The state equation. Illustration derived from Maarten Grootendorst's "A Visual Guide to Mamba and State Space Models."

In a Mamba LLM, the output equation is used to generate the next [token](https://www.ibm.com/docs/en/watsonx/saas?topic=solutions-tokens).

### Discrete SSMs

Traditional SSMs are designed to model *continuous* inputs, but text sequences (and most other data modalities processed by modern deep learning models) are *discrete* inputs. Using SSMs to model a discrete sequence requires a means to represent its distinct, specific timesteps as part of a continuous signal.

Conceptually, discretization amounts to sampling the value of a continuous function at specific moments. This entails the introduction of a new parameter—the *step size*, written as *∆*—that determines how long that value is sampled or “held” at each discrete time step *t*. Adjustments to *∆* are akin to changes to qualities such as the data’s resolution (for [time series](https://www.ibm.com/think/topics/time-series-model) data) or frame rate (for video data). There exist multiple “discretization” methods, but most modern SSM variants (including Mamba) use the simple [zero order hold (ZOH)](https://en.wikipedia.org/wiki/Zero-order_hold) method.

Discretizing an SSM enables it to be used like an RNN for sequence-to-sequence tasks. The parameters and equations of a discretized SSM are usually rewritten to distinguish them from their continuous-time equivalents, using the subscript notation typically employed for RNNs. In this notation, *h<sub>t</sub>* represents the updated state space the model will generate and *h*<sub>t-1</sub> represents the state before it—that is, the current state space.

**$$ h_t=\bar{A}h_{t-1}+\bar{B}x_t $$   
 $$ y_t=\bar{C}h_t $$**

### Structured SSMs

Modeling text data using standard discrete SSMs is impractical due to a number of shortcomings that they share with RNNs. Two of those shortcoming were addressed by the introduction of *structured state space sequence models* (or “S4 models”) by Albert Gu *et al* in 2021: the inefficiency of their training and their inability to model long sequences.

Though success of S4 models—and their many derivatives, such as diagonal SSMs (DSS), diagonal S4 (S4D) and H3 models—directly paved the way for what became Mamba.

##### Efficient training through convolutions

The benefit of discretized SSMs being the equivalent of a specific instance of an RNN is that RNNs are extremely fast at inference. The downside, however, is that RNNs are extremely slow to train.

Fortunately, discretized SSMs have one important property distinguishing them from other RNNs: they exclusively model *linear* dependencies. In other words, they use only simple, straightforward multiplication and addition operations. As [the S4 paper demonstrates](https://arxiv.org/pdf/2111.00396#subsection.2.4), these simple, repeated and interdependent linear recurrences can be unrolled into a 1-dimensional [convolution](https://developer.ibm.com/articles/introduction-to-convolutional-neural-networks/#convolution1) kernel, , that directly maps input *x* to output *y* in a single step: . This can be computed very efficiently using the [fast Fourier transform](https://research.ibm.com/publications/what-is-the-fast-fourier-transform--1).

The only “catch” is that this is only possible when every step of the entire input sequence is known. This isn’t possible during inference, but it *is* the case during training. A structured SSM therefore enjoys the best of both worlds: during training, it can be operated very efficiently as a CNN; during inference, it can be operated very efficiently as an RNN.

##### Modeling long sequences through structured matrices

Like most RNNs, standard SSMs are inherently weak at modeling long-distance dependencies. In other words, they aren’t good at understanding the relationship between steps in a sequence that are far apart, such as words at the beginning and end of a paragraph—which makes them weak at modeling long sequences altogether.

To solve for this, Gu and his co-authors (one of whom was Tri Dao) used a technique called *HiPPO—*short for High-order Polynomial Projection Operators—to define the way the A and B matrices behave by [*structuring* their intial values using a formula derived from orthogonal polynomials](https://www.ibm.com/think/topics/state-space-model#Structured+state+space+models). This is in contrast to standard machine learning practice, in which model weights are randomly initialized at the onset of [model training](https://www.ibm.com/think/topics/model-training). For S4, Dao and Gu proposed initialization schemes derived from [Legendre polynomials](https://mathworld.wolfram.com/LegendrePolynomial.html). They explored additional formulae in a follow-up paper, titled “How to Train Your HiPPO."<sup>1</sup>[](#_ftn1)

The S4 paper notes that “simply modifying an SSM from a random matrix *A* to [the HiPPO Matrix] improved its performance on the sequential MNIST benchmark from 60% to 98%,” effectively solving SSMs’ long-term memory problem. Later variations of structured SSMs, such as DSS, S5 and Mamba, use different (often simpler) initialization schemes for A and B that nevertheless retain the core HiPPO principals: implementing a diagonal structure that imposes stable updates and some degree of independence between each value in the matrix.

## How do Mamba models work?

At the core of the Mamba architecture are two innovations. The first is the *selective state space model,* which provides Mamba with a crucial capability previously possessed only by transformer models: the ability to selectively focus on or ignore specific parts of past input history based on their present relevance. The other is the hardware-aware *parallel scan*, an algorithm that optimizes the way a [graphics processing unit (GPU)](https://www.ibm.com/think/topics/gpu) handles the model’s computations in its memory hierarchy to maximize speed and computational efficiency.

In transformers, this ability is provided by the [attention mechanism](https://www.ibm.com/think/topics/attention-mechanism) that adjusts the *attention weights* that emphasize or deemphasize the influence of each previous token based on its relevance to the current input token. Ordinary SSMs are explicitly designed to map input to output using *the entire input history.* This is acceptable or even desirable for some sequence modeling tasks, but a significant handicap for most advanced language modeling tasks.

To remedy this inability to dynamically omit or emphasize specific parts of their input history, Dao and Gu proposed a new class of state space models with a “selective scan.” In the Mamba paper, the authors remark that they “sometimes abbreviate selective SSMs as *S6 models,* because they are *S4 models* with a *selection* mechanism *and computed with a* scan.” They nicknamed their S6-based architecture “Mamba” because, among other reasons, [all of those S’s sound like a snake’s hiss](https://xcancel.com/_albertgu/status/1731727694809723364#m).

Mamba can best be understood as a neural network architecture that contains the selective state space model at its core. For a simple analogy, Mamba is to selective SSMs as the transformer model is to the attention mechanism.

### How selective state space models (S6) work

A traditional SSM has fixed dynamics: the rules governing how the hidden state evolves from one step to the next—the [model parameters](https://www.ibm.com/think/topics/model-parameters)—are the same for every input and at every step in the sequence. This property is known as linear time invariance (LTI). To provide SSMs with the ability to selectively prioritize or deprioritize specific past information based on present context, Dao and Gu reconfigured their SSM such that *the values of key model parameters will be different for different inputs*.

More specifically, selective SSMs make the step size *∆<sub>t</sub>* and matrices *B<sub>t</sub>*<sub> </sub>and *C<sub>t</sub>*<sub> </sub>direct functions of the current input token *x<sub>t</sub>*. This is achieved by first passing the [vector embedding](https://www.ibm.com/think/topics/vector-embedding) of *x*<sub>t</sub> through three parallel linear projection layers—in other words, standard feedforward neural network layers (or *MLP layers*). This is equivalent to how the parallel [query, key and value](https://www.ibm.com/think/topics/attention-mechanism#How+do+attention+mechanisms+work%3F) heads generate an input’s respective *Q*, *K* and *V* vectors in a transformer model.

![Diagram of a selective state space model](https://assets.ibm.com/is/image/ibm/mamba-s6-diagram?ts=1763387610630&dpr=off)  The selective SSM and RAM allocation on a GPU. Taken from the original paper, "Mamba: Linear Time-Sequence Modeling with Selective State Spaces"

Multiplying *x*<sub>t</sub>’s vector embedding by the weight and bias terms in that linear projection network yields the resulting values of ∆<sub>t</sub>, B<sub>t</sub> and C<sub>t</sub>. The weight and bias terms of the linear projection layers themselves are learned during model [pretraining on massive datasets](https://www.ibm.com/think/topics/self-supervised-learning) of text samples, then (optionally) refined through subsequent fine-tuning.

- The value of ***∆<sub>t</sub>*** determines the magnitude of the influence of *x*<sub>t</sub> on the model’s memory of the context it has seen thus far: in other words, on *how much* of an update there will be from hidden state *h<sub>t-1</sub>* to *h<sub>t</sub>.* A larger step size *∆<sub>t</sub>* results in greater changes and speeds up the decay—in other words, the “forgetting”—of older information contained within the state. Conversely, a smaller step size results in a smaller update. At a small enough step size, the current input will have no impact on the hidden state at all.
- Changes to the matrix ***B*<sub>k</sub>** determine *how* the current input token updates the hidden state. For instance, if *x*<sub>t</sub> is a token for the word “yesterday,” *B*<sub>t</sub> might be adjusted in a way that updates the state to reflect that the ensuing context probably pertains to the past.
- Changes to the matrix ***C<sub>t</sub>*** determine how this contextual information translates to influence on the model’s output *y*<sub>t</sub>. Continuing the example in which *x*<sub>k</sub> is a token for “yesterday,” *C*<sub>k</sub> might be influenced in a way that causes any verbs that are subsequently output by the model to be conjugated in the past tense.

Notably, no such input-based adjustments are made to the *A* matrix. Its role remains the same as in S4 models: to efficiently memorize the entire history of past inputs. The role of determining *which parts* of that history to utilize at a given moment is handled by the *B* and *C* matrices.

### Parallel scan

But once the model is no longer time-invariant, it can no longer use the convolution shortcut during training because the transition kernel is no longer constant: the crux of the selectivity mechanism is that the transition from *h*<sub>t-1 </sub>to *h<sub>t</sub>* is now dependent on context.

Instead, Mamba uses a clever workaround to achieve similar parallelization benefits. Because the SSM uses only multiplication and addition, its computations are subject to the familiar associative property of math: they can be grouped in different ways without changing the final outcome. This allows the many sequential calculations to be broken down into small, independent chunks that can be processed in parallel by a GPU through a [*parallel prefix sum scan*](https://developer.nvidia.com/gpugems/gpugems3/part-vi-gpu-computing/chapter-39-parallel-prefix-sum-scan-cuda).

Furthermore, the results are combined in a specific hierarchical manner that makes optimally efficient use of the different kinds of hardware memory on a GPU, using principles similar to the [FlashAttention](https://arxiv.org/abs/2205.14135) techniques—which were also developed by Tri Dao—that are now ubiquitous in modern LLMs.

### The Mamba block

Within the Mamba architecture, the S6 model serves as a module of the larger “Mamba block,” similarly to how the attention mechanism serves as a module within the larger “attention block.” It combines the S6 module with a [gated neural network](https://arxiv.org/pdf/2105.08050) architecture. Mamba models typically comprise multiple Mamba blocks—that is, a series of consecutive Mamba layers in a neural network—prior to the output layer that makes the model’s final output prediction.

![Diagram of Mamba-2 block](https://assets.ibm.com/is/image/ibm/mamba-block-1?ts=1763387611245&dpr=off)  The Mamba block. The "x" following the selective SSM refers to element-wise multiplication, rather than standard dot product.

Before entering the Mamba block, a copy of the input is sent directly to the end as a *residual connection.* The purpose of the Mamba block’s inner workings is to not only determine which parts of the greater context are relevant to that input, but to determine *how much* that contextual information should modify the input’s original meaning.

Within the Mamba block, the original input vector is processed as follows:

- First, the input is passed through a linear layer that’s twice as wide as the input vector itself, projecting it to a higher-dimensional space. For instance, if the model originally represents each input token *x* as 512-dimension vector embedding, multiplying *x* by the weights of the linear projection layer expands it into a 1024-dimension vector.
- Next, the expanded vector is split in two. One half (which we’ll call *x<sub>proj</sub>*) is fed into the path that runs through the SSM, and the other half (which we’ll call *z*<sub>proj</sub>) is fed into a separate path that runs through a gating mechanism. For clarity, the previous expansion step is usually depicted as being performed by 2 parallel linear layers.
- Before x<sub>proj</sub> reaches the SSM, it’s fed into a 1-dimensional [convolution](https://developer.ibm.com/articles/introduction-to-convolutional-neural-networks/) layer. This convolution layer extracts local patterns (like dependencies between neighboring tokens, such as simple verb-subject pairings). This enables the SSM to “focus” on contextual understanding of long-range, global dependencies.
- The output of the convolution layer serves as the input to a nonlinear [activation function](https://www.ibm.com/think/topics/backpropagation#How+neural+networks+work). Introducing nonlinearity is a hallmark of all neural networks, allowing them to capture more complex patterns. The Mamba paper uses [Sigmoid Linear Unit (SiLU)](https://github.com/paperswithcode). We’ll call the resulting vector *x*<sub>act</sub>.
- Meanwhile, in the separate gating mechanism path, *z*<sub>proj</sub> is also input to a nonlinear activation function, yielding *z*<sub>act</sub>.
- In the SSM path, *x*<sub>act</sub> is fed into three parallel linear projection layers that generate the respective values for ∆<sub>x</sub>, B<sub>x</sub> and C<sub>x</sub>, respectively.
- The SSM uses these input-dependent parameters (and the *A* and *D* matrices) to compute the state space update and the SSM’s output *y.*
- The SSM’s output vector *y* is now [multiplied element-wise](https://en.wikipedia.org/wiki/Hadamard_product_(matrices)) by the gating path’s output vector *z*<sub>act</sub>. Essentially, each element in z<sub>act</sub> acts like a volume knob on an [audio mixing console](https://upload.wikimedia.org/wikipedia/commons/thumb/e/e4/SSL_SL9000J_%2872ch%29_%40_The_Cutting_Room_Recording_Studios%2C_NYC.jpg/1920px-SSL_SL9000J_%2872ch%29_%40_The_Cutting_Room_Recording_Studios%2C_NYC.jpg): if a given element of *z*<sub>act</sub> is close to zero, multiplication with the corresponding part of *y* will yield a value closer to zero and its influence will be diminished. Conversely, if a given element of *z*act is large, multiplication with *y* will amplify the influence of its contextual information.
- The resulting vector is projected back down to its original size. It can be understood as a vector of weighted contextual updates (or non-updates) to each of the elements of the original input vector.
- Finally, that vector of updates is added to the copy of the original input vector that was sent straight to the end of the block as a residual connection.
- The original input vector has now been updated to reflect the contextual understanding provided by the selective SSM. It can now be sent to the next Mamba layer or, at the model’s final layers, serve as the input to a softmax function that outputs the respective probability that the fully updated vector corresponds to each word in the model’s vocabulary.

## Mamba-2

A year after the original Mamba paper, Dao and Gu followed it up with “Transformers are SSMs: Generalized Models and Efficient Algorithms Through Structured State Space Duality.” This follow-up paper offered three major contributions:

- An exploration of the theoretical connections between Mamba and transformers and a shared vocabulary between the two architectures
- A series of clarifications and explorations of different design choices for Mamba models
- A modified architecture, *Mamba-2*, informed and improved by those design explorations

The Mamba-2 algorithm is significantly faster and easier to implement than the original Mamba: the authors provided a “minimal SSD” code base that implements the selective SSM in about 25 lines of code.<sup>2</sup>[](#_ftn1) This efficiency enables Mamba-2 to use much larger hidden state dimensions without slowing the model down, allowing for larger, more powerful, more expressive models built with the architecture. In testing, Mamba-2 models definitively matched or outperformed correspondingly-sized Mamba and transformer models on a series of downstream tasks.

### Connections to transformers

As the paper’s introductions states, Dao and Gu’s “main goal [was] to develop a rich body of theoretical connections between structured SSMs and variants of attention.” This yielded a new conceptual framework uniting the two, which they called “state space duality” (SSD).<sup>3</sup>[](#_ftn1) In doing so, they opened the door for Mamba to benefit from several years’ worth of exploration and optimization of the transformer architecture.

One notable benefit was the development of a Mamba equivalent of [multi-head attention (MHA)](https://www.ibm.com/think/topics/grouped-query-attention#Standard+multi-head+attention), in which a Mamba block can be split into multiple “Mamba heads” akin the to the multiple “attention heads” in transformers. One variant of this approach, which they deemed analogous to [grouped query attention](https://www.ibm.com/think/topics/grouped-query-attention), enables even more efficiency through tensor parallelism in GPUs.

### Mamba-2 architecture

In the Mamba-2 block—which they call the *parallel Mamba block* (as opposed to the original “sequential” Mamba block”)—the input-dependent parameters ∆, B and C are generated in parallel at the initial projection layer. B and C, specifically, are derived by simply copying portions of *x<sub>proj</sub>,* rather than by multiplying x<sub>proj </sub>through dedicated linear layers. In addition to simplifying and reducing total model parameters, this parallelism enables significantly more efficient large-scale training.<sup>4</sup>[](#_ftn1)

![Diagram of Mamba-2 block](https://assets.ibm.com/is/image/ibm/mamba-block-2?ts=1763387612141&dpr=off)  The Mamba-2 block. The "x" following the selective SSM refers to element-wise multiplication, rather than standard dot product.

## Mamba vs. transformers

Both Mamba and transformers have their own respective strengths, but Mamba-based models are generally superior in all matters related to memory usage and speed: per the Mamba paper, Mamba offers 5 times greater throughput than equivalent transformers.

Transformers are incredibly precise and versatile, but also incredibly demanding on computational resources. During pre-training (and [fine-tuning](https://www.ibm.com/think/topics/fine-tuning)), the memory requirements of self-attention scale quadratically with sequence length: if you double the [context length](https://www.ibm.com/think/topics/context-window) of a sequence, the attention mechanism uses quadruple the resources. This “quadratic bottleneck” increasingly throttles speed and memory availability as the context window grows. During inference, their memory needs scale linearly.

During training, the memory usage of a Mamba model scales only linearly during training. More importantly, it’s memory usage during inference is *constant*: regardless of how many tokens the model has seen, the SSM maintains a fixed-size representation of its input history. This allows theoretically unlimited context length, constrained only by hardware limitations.

That being said, transformers’ more memory-intensive and computationally redundant method has its own advantages. For instance, [research has shown](https://arxiv.org/pdf/2406.07887) that transformers still outpace both Mamba and Mamba-2 on tasks requiring in-context learning (such as [few-shot prompting](https://www.ibm.com/think/topics/few-shot-prompting)), copying, or long-context reasoning.

### Hybrid mamba models

Fortunately, the respective strengths of transformers and Mamba are not mutually exclusive. The Mamba-2 paper suggests that a hybrid model could outperform both pure transformers or SSMs—a notion formally validated by NVIDIA research later in 2024.<sup>5</sup>[](#_ftn1) Broadly speaking, hybrid models seem to combine the efficiency benefits of Mamba with the nuance and in-context learning performance provided by transformers’ more resource-intensive attention mechanism.

To explore this further, [IBM Research collaborated with Dao and Gu](https://research.ibm.com/blog/bamba-ssm-transformer-model), along with the University of Illinois at Urbana-Champaign (UIUC)’s Minjia Zhang, on [Bamba](https://huggingface.co/ibm-ai-platform/Bamba-9B-v1) and [Bamba V2](https://huggingface.co/ibm-ai-platform/Bamba-9B-v2). Bamba, in turn, has informed many of the architectural elements of [IBM Granite 4.0](https://www.ibm.com/new/announcements/ibm-granite-4-0-tiny-preview-sneak-peek).

Research into hybrid models remains an area of active research, particularly within the open source community.

## Footnotes

1. [“How to Train Your HiPPO: State Space Models with Generalized Orthogonal Basis Projections,”](https://arxiv.org/pdf/2206.12037) arXiv, 5 August 2022  
 2. [“State Space Duality (Mamba-2) Part III – The Algorithm,”](https://goombalab.github.io/blog/2024/mamba2-part3-algorithm/#the-code) Goomba Lab, 31 May 2024  
 3. [“Transformers are SSMs: Generalized Models and Efficient Algorithms Through Structured State Space Duality,”](https://arxiv.org/pdf/2405.21060) arXiv, 31 May 2024  
 4. *ibid*  
 5. [“An Empirical Study of Mamba-based Language Models,”](https://arxiv.org/pdf/2406.07887) arXiv, 12 June 2024
