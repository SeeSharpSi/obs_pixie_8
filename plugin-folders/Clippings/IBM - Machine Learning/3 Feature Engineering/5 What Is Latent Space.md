---
title: What is latent space?
source: https://www.ibm.com/think/topics/latent-space
author:
- '[[Dave Bergmann]]'
published: 2025-01-28
created: 2026-05-21
description: "A latent space in machine learning is a compressed representation of data points that preserves only essential features informing the data’s underlying structure."
---

## What is latent space?

A latent space in [machine learning](https://www.ibm.com/think/topics/machine-learning) (ML) is a compressed representation of data points that preserves only essential features that inform the input data’s underlying structure. Effectively modeling latent space is an integral part of [deep learning](https://www.ibm.com/think/topics/deep-learning), including most [generative AI](https://www.ibm.com/think/topics/generative-ai) (gen AI) algorithms.

Mapping data points to latent space can express complex data in an efficient and meaningful way, enhancing the ability of machine learning models to understand and manipulate it while reducing computational requirements. To that end, encoding latent space representations typically entails some degree of [dimensionality reduction](https://www.ibm.com/think/topics/dimensionality-reduction): the compression of high-dimensional data down to a lower-dimensional space that omits irrelevant or redundant information.

Latent spaces play an important role in many fields of [data science](https://www.ibm.com/think/topics/data-science), and encoding latent space is an essential step in many modern artificial intelligence (AI) algorithms. For instance, any generative models, such as [variational autoencoders (VAEs)](https://www.ibm.com/think/topics/variational-autoencoder) and [generative adversarial networks (GANs)](https://www.ibm.com/think/insights/generative-adversarial-network-technology-ai-goes-mainstream), compute the latent space of training data to then interpolate from it to generate new data samples. Computer vision models trained for classification tasks such as [object detection](https://www.ibm.com/think/topics/object-detection) or [image segmentation](https://www.ibm.com/think/topics/image-segmentation) map input data to latent space to isolate its qualities that are relevant to making accurate predictions.

[Large language models (LLMs](https://www.ibm.com/think/topics/large-language-modelsd)), from embedding models that enable semantic search to [autoregressive](https://www.ibm.com/think/topics/autoregressive-model) models such as [IBM® Granite](https://www.ibm.com/granite)™ or those powering OpenAI’s ChatGPT, manipulate latent space to explore complex connections between different words in specific contexts.

## What does "latent space" mean?

The word *space* takes on a more varied meaning in the context of machine learning than it does in general language. Broadly speaking, a "space" in ML refers to a specific mode of mapping, comparing or sampling data points. For instance:

- The "input space*"* is the range of possibilities included in the input data.
- The "output space*"* is the range of possibilities for the model's output.
- In image data, the "pixel space*"* is the range of possibilities for numerical pixel values.
- In reinforcement learning, the "action space" is the range of possible actions that could be taken next, such as the legal moves available at a specific moment in a board game.

Mathematically speaking, a *space* is primarily defined by what its dimensions correspond to: that is, which *features*—variables—are being used to describe data points in that space. When data points are mapped to a specific space, data points with similar values for the variables that define the space will be *similar to* or *near each other* by some metric such as cosine similarity, Euclidian distance or dot product.

In machine learning, data points must be represented numerically. Most often, data points are represented (or “embedded”) as *vectors*. We thus refer to the space in which data points are compared by their vector representations as the "vector embedding space" (or *"*embedding space*"*). The numerical representations, in which each element in the vector corresponds to an individual dimension of the embedding space, are called [vector embeddings](https://www.ibm.com/think/topics/vector-embedding). Machine learning algorithms typically either take vector embeddings as input or begin by converting input data to vector embeddings.

### Feature space vs. latent space

The *feature space* is the vector space associated with the range of possibilities not for data points but for the values of meaningful features that might characterize a specific set of data points. For example, in models processing image data, each dimension of the feature space might correspond to specific shapes, textures or color patterns present in the model’s training data.

The feature space typically omits information from dimensions of the embedding space that don’t contain any features. Continuing the example of image data, the feature space would exclude backgrounds or empty space. The process of isolating meaningful features from the greater embedding space is called *feature extraction*.

“Feature space” and “latent space” are often used interchangeably but aren’t always synonymous. Given that feature extraction usually entails a compressed representation of data that omits information that isn’t useful, the concepts are closely related. However, some features might not necessarily be relevant to the data’s underlying structure. Therefore, the latent space is usually a *lower-dimensional* representation of the feature space containing only the subset of features that, through machine learning, are identified as most relevant to the task at hand.

### What does "latent" mean in machine learning?

In a latent space, each dimension corresponds to a *latent variable* of the original data. Latent variables are underlying characteristics that inform the way data is distributed but are often not directly observable.

For an intuitive example, imagine a bridge with a sensor that measures the weight of each passing vehicle. Many different vehicles, from lightweight convertibles to heavy trucks, use the bridge—but there’s no camera to detect a vehicle’s type. Nevertheless, we know that the type of vehicle significantly influences its weight. In this example, *vehicle weight* is an observable variable and *vehicle type* is a latent variable: we can infer what types of vehicles use the bridge by exploring patterns in vehicle weight.

Not every “hidden” variable is important, and thus not every hidden variable will be represented in the latent space encoded by a machine learning model. In practice, the model *learns* to encode the latent space most conducive to accurately performing the task it is being trained to do.

## Latent space and dimensionality reduction

Encoding a latent space representation usually entails the compression of high-dimensional data into a lower-dimensional space through a process called *dimensionality reduction*.

Consider the images in [MNIST](https://dataplatform.cloud.ibm.com/exchange/public/entry/view/e5ec6df59cd736a6b6b091062e3715a2?context=cpdaas), an open source dataset containing tens of thousands of 28x28 grayscale images of handwritten digits. Each small 28x28 image could be represented as a 784-dimensional vector embedding wherein each dimension corresponds to an individual pixel and has a value between 0 (for black) and 1 (for white). If they were color images, those vector embeddings would be *2,352*-dimensional: 3 dimensions for each of the 784 pixels, corresponding to its respective red, green and blue (RGB) values.

However, the actual digits comprise only a small fraction of the pixel space. Most of the image is empty background. Reducing images (and the vectors that represent them) down to only the dimensions containing actual information—the *latent space*—can greatly improve the ability of a machine learning model to accurately and efficiently process the images.

### Autoencoders (and other encoder-decoder frameworks)

One type of neural network architecture designed explicitly for dimensionality reduction and compressing input data into latent space is the [autoencoder](https://www.ibm.com/think/topics/autoencoder).

Autoencoders are self-supervised systems whose training goal is to compress (or *encode*) input data through dimensionality reduction and then accurately reconstruct (or *decode*) their original input from that compressed representation. In a standard autoencoder, each layer of the encoder contains progressively fewer nodes than the previous layer. As the vector embedding of the input data is passed to the next encoder layer, it’s compressed through the process of “squeezing” itself into fewer dimensions. The decoder network then reconstructs the original input by using only the latent vector produced by the encoder.

Autoencoders are trained to minimize reconstruction loss, which measures how much the decoder’s reconstruction differs from the original input. Because the encoder can pass only a limited amount of information to the decoder, it’s forced to extract only the data’s most salient features. In other words, an autoencoder naturally learns an effective mapping of the input data’s latent space.

![Diagram of an autoencoder neural networks](https://assets.ibm.com/is/image/ibm/variational-autoencoder-neural-network?ts=1763387713006&dpr=off)

This ability gives autoencoders many interesting use cases in addition to data compression. For instance, autoencoders can be used for [anomaly detection](https://www.ibm.com/think/topics/anomaly-detection) because they can register abnormalities not apparent to a human observer. Imagine a counterfeit watch: to even the trained eye, it might perfectly resemble the real item. Only by taking it apart and attempting to reconstruct the underlying gears and mechanics inside—its latent space—can you identify elements that don’t match those of the genuine watch it’s copying.

A key benefit of autoencoders over other dimensionality reduction algorithms, such as linear discriminant analysis or [principal component analysis (PCA),](https://www.ibm.com/think/topics/principal-component-analysis) is that autoencoders can model nonlinear relationships between different variables.

Many other neural networks implement a similar encoder-decoder architecture, in which the encoder network reduces the dimensionality of the input data and the decoder processes that latent encoding to make predictions. An autoencoder is any implementation of that structure in which the model is trained to reconstruct input data.

## Latent space in variational autoencoders (VAEs) and other generative models

[*Variational* autoencoders (VAEs)](https://www.ibm.com/think/topics/variational-autoencoder) use the autoencoder architecture to encode latent space in a way that can be used for generative tasks such as image generation.

Unlike most autoencoders, which are "deterministic" models that encode a single vector of discrete values for each latent variable of training data, VAES are "probabilistic" models that encode latent space as a range of possibilities. By interpolating from within this range of encoded possibilities, VAEs can synthesize new data samples that, while unique and original unto themselves, resemble the original training data.

To enable the generation of completely new data samples (rather than simply re-creating or combining samples from training data), the latent space must exhibit 2 types of regularity:

- **Continuity:** Nearby points in latent space should yield similar content when decoded.
- **Completeness:** Any point sampled from the latent space should yield meaningful content when decoded.

A simple way to enforce continuity and completeness in latent space is to force it to follow a normal (Gaussian) distribution. Therefore, VAEs encode 2 different vectors for each latent attribute of training data: a vector of means, “***μ***,” and a vector of standard deviations, “***σ***.” In essence, these 2 vectors represent the range of possibilities for each latent variable and the expected variance within each range of possibilities, respectively.

VAEs accomplish this by adding an additional [loss function](https://www.ibm.com/think/topics/loss-function) alongside reconstruction loss: Kullback-Leibler divergence (or *KL divergence*). More specifically, the VAE is trained to minimize the divergence between a standard Gaussian distribution and the latent space learned by minimizing reconstruction loss.

![Diagram demonstrating reconstruction loss and KL divergence in autoencoders](https://assets.ibm.com/is/image/ibm/variational-autoencoder-distribution?ts=1763387713517&dpr=off)

### Latent space in other image generation models

While other image generation model architectures use training objectives other than reconstruction loss, they all typically employ regularization terms to enforce the continuity and completeness of latent space. Most, but not all, fit the latent space to a normal distribution.

#### Generative adversarial networks (GANs)

Generative adversarial networks (GANs) train 2 neural networks—a "discriminator" network and a generator network—in an adversarial game. The discriminator is shown an image and trained to predict whether it’s an original image or an image drawn from the training dataset. The generator is trained to fool the discriminator by sampling from the latent space to generate original samples.

The generator is deemed trained when the discriminator is no longer able to differentiate between training images and generated images.

#### Latent diffusion models

Latent diffusion models, first introduced by the original Stable Diffusion model, essentially combine [diffusion models](https://www.ibm.com/think/topics/diffusion-models) with VAEs. Whereas standard diffusion models act directly on the pixel space, latent diffusion models first employ a VAE-style architecture to encode input data to a lower-dimensional latent representation, and then apply diffusion to the latent space. This innovation greatly increased the speed and efficiency of diffusion models.

## Visualizing latent space

The relationships between different data points in latent space are inherently difficult to imagine or visualize. Our senses and experience are confined to a 3-dimensional understanding of the world and our minds cannot conceive of a graph that plots points along dozens, hundreds or even thousands of dimensions.

To address this challenge, data scientists apply dimensionality reduction techniques such as [t-distributed stochastic neighbor embedding](https://en.wikipedia.org/wiki/T-distributed_stochastic_neighbor_embedding) (t-SNE) or [Uniform Manifold Approximation and Projection (UMAP)](https://arxiv.org/abs/1802.03426). Such techniques, used widely in data visualization, map high-dimensional data to a 2-dimensional (or 3-dimensional) graph, wherein similar objects are near each other and dissimilar objects are far apart. The visualization of a VAE's latent space featured earlier in this article, for example, was created using t-SNE.

Research in image models has also yielded interesting insights into the nature of latent space that have contributed to advancements in the manipulation of latent space for generative models. For instance, the widely cited paper [“Unsupervised Representation Learning with Deep Convolutional Generative Adversarial Networks”](https://arxiv.org/abs/1511.06434) explored techniques such as performing arithmetic with latent vectors to intuitively produce new images with specific qualities.

## Latent space in natural language processing (NLP)

In the same way that vector embeddings for images aim to represent the data provided by an image’s original distribution of pixel values, word embeddings aim to capture the semantic meaning of a particular word.

However, unlike an image, the semantic meaning of a word is not static: it’s dynamic, with connotations and relationships that can be changed by the words around it. Therefore, transformer models use a [self-attention mechanism](https://www.ibm.com/think/topics/attention-mechanism) to compute how a word’s meaning is impacted by its context and update its embedding accordingly. Between the input layer that intakes a prompt and the output layer where new text is generated, the original word embeddings are transformed into a series of latent representations as the model continuously refines its contextual understanding.

Though the inner workings of large language models (LLMs) have thus far proven fairly difficult to interpret, ongoing research has explored the activation of latent space in in-context learning and other emergent abilities of LLMs.<sup>1, 2</sup>

## Footnotes

<sup>1</sup> ["Large Language Models Are Latent Variable Models: Explaining and Finding Good Demonstrations for In-Context Learning,"](https://proceedings.neurips.cc/paper_files/paper/2023/file/3255a7554605a88800f4e120b3a929e1-Paper-Conference.pdf) Proceedings of the 37th Conference on Neural Information Processing Systems (NeurIPS 2023), December 2023.

<sup>2</sup> ["A Latent Space Theory for Emergent Abilities in Large Language Models,"](https://arxiv.org/abs/2304.09960) arXiv, 13 September 2023.
