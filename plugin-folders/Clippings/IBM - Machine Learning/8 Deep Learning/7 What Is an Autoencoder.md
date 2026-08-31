---
title: What is an autoencoder?
source: https://www.ibm.com/think/topics/autoencoder
author:
- '[[Dave Bergmann]]'
- '[[Cole Stryker]]'
published: 2024-12-02
created: 2026-08-31
description: "An autoencoder is a neural network trained to efficiently compress input data down to essential features and reconstruct it from the compressed representation."
---

## What is an autoencoder?

An autoencoder is a type of [neural network](https://www.ibm.com/topics/neural-networks) architecture designed to efficiently compress (encode) input data down to its essential features, then reconstruct (decode) the original input from this compressed representation.

Using unsupervised [machine learning](https://www.ibm.com/topics/machine-learning), autoencoders are trained to discover *latent variables* of the input data: hidden or random variables that, despite not being directly observable, fundamentally inform the way data is distributed. Collectively, the latent variables of a given set of input data are referred to as *latent space*. During training, the autoencoder learns which latent variables can be used to most accurately reconstruct the original data: this latent space representation thus represents only the most essential information contained within the original input.

Most types of autoencoders are used for artificial intelligence tasks related to feature extraction, like data compression, image denoising, anomaly detection and facial recognition. Certain types of autoencoders, like variational autoencoders (VAEs) and adversarial autoencoders (AAEs), adapt autoencoder architecture for use in generative tasks, like image generation or generating time series data.

## Autoencoders vs. encoder-decoders

Though all autoencoder models include both an encoder and a decoder, not all *encoder-decoder* models are *autoencoders.*

**Encoder-decoder** frameworks, in which an encoder network extracts key features of the input data and a decoder network takes that extracted feature data as its input, are used in a variety of deep learning models, like the [convolutional neural network](https://www.ibm.com/topics/convolutional-neural-networks) (CNN) architectures used in computer vision tasks like [image segmentation](https://www.ibm.com/topics/image-segmentation) or the [recurrent neural network](https://www.ibm.com/topics/recurrent-neural-networks) (RNN) architectures used in sequence-to-sequence (seq2seq) tasks.

In most applications of encoder-decoder models, *the output of the neural network is different from its input*. For example, in image segmentation models like U-Net, the encoder network extracts feature data from the input image to determine the semantic classification of different pixels; using that feature map and those pixel-wise classifications, the decoder network then constructs segmentation masks for each object or region in the image. The goal of these encoder-decoder models is to accurately label pixels by their semantic class: they are trained via [supervised learning](https://www.ibm.com/topics/supervised-learning), optimizing the model’s predictions against a “ground truth” dataset of images labeled by human experts.

**Autoencoders** refer to a specific subset of encoder-decoder architectures that are trained via [*un*supervised learning](https://www.ibm.com/topics/unsupervised-learning) to *reconstruct their own input data.*

Because they do not rely on labeled training data, autoencoders are not considered a supervised learning method. Like all unsupervised learning methods, autoencoders are trained to discover hidden patterns in unlabeled data, rather than to predict known patterns demonstrated in labeled training data; however, like supervised learning models—and unlike most examples of unsupervised learning—autoencoders have a ground truth to measure their output against: the original input itself (or some modified version of it). For that reason, they are considered *“self-supervised learning*”–hence, *auto*encoder.

## How do autoencoders work?

Autoencoders discover latent variables by passing input data through a “bottleneck” before it reaches the decoder. This forces the encoder to learn to extract and pass through only the information most conducive to accurately reconstructing the original input.

Though different variants of autoencoders alter certain elements of their artificial neural network to best suit specific goals and types of data, all autoencoders share key structural elements:

The **encoder** comprises layers that *encode* a compressed representation of the input data through *dimensionality reduction*. In a typical autoencoder, the hidden layers of the neural network contain a progressively smaller number of nodes than the input layer: as data traverses the encoder layers, it is compressed by the process of “squeezing” itself into fewer dimensions.

The **bottleneck** (or **“code”**) contains the most compressed representation of the input: it is both the output layer of the encoder network and the input layer of the *decoder* network. A fundamental goal of the design and training of an autoencoder is discovering the minimum number of important features (or *dimensions*) needed for effective reconstruction of the input data. The latent space representation–that is, the *code*–emerging from this layer is then fed into the decoder.

The **decoder** comprises hidden layers with a progressively larger number of nodes that decompress (or *decode*) the encoded representation of data, ultimately reconstructing the data back to its original, pre-encoding form. This reconstructed output is then compared to the “ground truth”–which in most cases is simply the original input—to gauge the efficacy of the autoencoder. The difference between the output and ground truth is called the *reconstruction error.*

In some applications of autoencoders, the decoder can be discarded after training: in such instances, the decoder’s sole purpose is to train the encoder—similar to role of the discriminator in a [generative adversarial network (GAN)](https://developer.ibm.com/articles/generative-adversarial-networks-explained/)—which is then used as a component of a different neural network. In many autoencoders, the decoder continues to serve a purpose post-training: for example, in VAEs, the decoder outputs new data samples.

One of the primary advantages of using autoencoders over other dimensionality techniques like [principal component analysis (PCA)](https://www.ibm.com/docs/en/db2-warehouse?topic=procedures-principal-component-analysis-pca) is that autoencoders can capture complex *non-linear* correlations. Accordingly, the activation functions used in autoencoders are typically non-linear functions like the sigmoid function.

Different types of autoencoders make adaptations to this structure to better suit different tasks and data types. In addition to selecting the appropriate type of neural network—for example, a CNN-based architecture, an RNN-based architecture like [long short-term memory](https://developer.ibm.com/tutorials/iot-deep-learning-anomaly-detection-1/), a transformer architecture or a simple vanilla feed-forward neural network—the design of an autoencoder entails multiple hyperparameters:

- **Code size:** The size of the bottleneck determines how much the data is to be compressed. The code size can also be used a regularization term: adjustments to code size are one way to counter [overfitting](https://www.ibm.com/topics/overfitting) or [underfitting](https://www.ibm.com/topics/underfitting).
- **Number of layers:** The depth of the autoencoder is measured by the number of layers in the encoder and decoder. More depth provides greater complexity, while less depth provides greater processing speed.
- **Number of nodes per layer:** Generally, the number of nodes (or “neurons”) decreases with each encoder layer, reaches a minimum at the bottleneck, and increases with each layer of the decoder layer—though in certain variants, like *sparse autoencoders,* this is not always the case. The number of neurons may also vary per the nature of input data: for example, an autoencoder dealing with large images would require more neurons than one dealing with smaller images.
- **Loss function:** When training an autoencoder, the loss function—which measures reconstruction loss between the output and input—is used to optimize model weights through [gradient descent](https://www.ibm.com/topics/gradient-descent) during backpropagation. The ideal algorithm(s) for the loss function depends on the task the autoencoder will be used for.

## Undercomplete autoencoders

Undercomplete autoencoders are a simple autoencoder structure used primarily for dimensionality reduction. Their hidden layers contain fewer nodes than their input and output layers, and the capacity of its bottleneck is fixed.

The goal of this bottleneck is to prevent the autoencoder from overfitting to its training data. Without sufficiently limiting the capacity of the bottleneck, the network tends toward learning the *identity function* between the input and output: in other words, it may learn to minimize reconstruction loss by simply copying the input directly. By forcing the data to be significantly compressed, the neural network must learn to retain only the features most essential to reconstruction.

But if the encoder and decoder have a high enough capacity—that is, if they’re processing large or complex data inputs—then the autoencoder (even with a bottleneck) may still learn the identity function anyway, making it useless. This makes undercomplete autoencoders inflexible and limits their capacity.

## Regularized autoencoders

Regularized autoencoders address the shortcomings of undercomplete autoencoders by introducing *regularization:* techniques that constrain or modify the way the model calculates reconstruction error. These regularization terms not only reduce overfitting, but also enable the autoencoder to learn useful features or functions.

### Sparse autoencoders

Sparse autoencoders (SAEs) impose a *sparsity* constraint: rather than creating an information bottleneck by reducing the number of nodes in each hidden layer, SAEs create a bottleneck by reducing the number of nodes that can be activated at the same time.

Whereas a standard undercomplete autoencoder will use the entire neural network for each observation, autoencoders with a *sparsity function* are penalized for each neuron that has been activated beyond a certain threshold. This enables the encoder and decoder to have a higher capacity without a corresponding risk of overfitting to training data (because not all neurons will be activated). It also allows hidden layers to contain nodes dedicated to discovering specific features: the sparsity function ensures that it’s only “worth the penalty” to activate those nodes if said features are present.

Though the calculation of reconstruction error and subsequent optimization of parameter weights through backpropagation occurs separately, this optimization is *regularized* by this sparsity function. The autoencoder is thus forced to learn the most effective latent space representation within the given sparsity constraints.

The functions used to impose a sparsity constraint are typically [L1 regularization](https://community.ibm.com/community/user/ai-datascience/blogs/moloy-de1/2020/06/12/points-to-ponder) or KL divergence.

#### KL divergence

Kullback-Leibler (KL) divergence measures the difference between two probability distributions. When used in the context of SAEs, the penalty given to the network after each training batch is proportionate to the KL divergence between the target distribution of activation values—the desired sparsity—and the actual distribution of activation values. As will be discussed later in this article, KL divergence is also used to optimize the accuracy of probability distributions learned by variational autoencoders (VAEs).

### Contractive autoencoders

First introduced in 2011 by researchers from the Université de Montréal,<sup>1</sup>[<sup></sup>](#_ftn1) contractive autoencoders are designed to be insensitive to minor variations (or “noise”) in input data in order to reduce overfitting and more effectively capture essential information.

This is achieved by adding a regularization term in training, penalizing the network for changing the output in response to insufficiently large changes in the input. This penalty term is calculated using two mathematical concepts:

- The *Jacobian matrix* contains all first-order derivates of a function that can be used for backpropagation. It represents how the gradients of the network change as the input is changed.
- The *Frobenius norm* is calculated as “the square root of the sum of the absolute squares of its elements.<sup>2</sup>"It measures the average gain of the matrix along each [orthogonal](https://www.ibm.com/docs/en/informix-servers/14.10?topic=interoperability-orthogonality) direction in space.<sup>3</sup>[](#_ftn3)

Specifically, the penalty term is *the Frobenius norm of the Jacobian matrix of* *neuron activations in the encoder network with respect to the input.* This penalty term and the loss function algorithm used to reduce reconstruction error are adversarial: the reconstruction loss function tends toward observing variations in input data while the penalty term tends toward ignoring them. By combining both terms, the network is forced to learn a compressed representation of the input that contains only the most consequential variables.

### Denoising autoencoders

Denoising autoencoders are given partially corrupted input data and trained to restore the original input by removing useless information through dimensionality reduction.

Unlike most autoencoders, denoising autoencoders do not have the ground truth data as its input. Instead, Gaussian noise is added to the original data—for example, adding random static to an image—and the denoising autoencoder (DAE) learns to filter it out. During model training, the reconstruction error of the denoised output is not measured against the corrupted input data, but against the original image.

In addition to preventing overfitting, this training technique also makes denoising autoencoders very useful for cleaning up noisy or corrupted image and audio files. Denoising autoencoders have also served as foundational training paradigms for state-of-the-art image generation models like Stable Diffusion.<sup>4</sup>

## Variational autoencoders

Variational autoencoders (VAEs) are generative models that learn compressed representations of their training data as *probability distributions,* which are used to generate new sample data by creating *variations* of those learned representations.

The fundamental difference between VAEs and other types of autoencoders is that while most autoencoders learn *discrete* latent space models, VAEs learn *continuous* latent variable models. Rather than a single encoding vector for latent space, VAEs model two different vectors: a vector of means, “*μ*,” and a vector of standard deviations, “*σ*.” Because these vectors capture latent attributes as a *probability distribution*—that is, they learn a *stochastic* encoding rather than a *deterministic* encoding—VAEs allow for interpolation and random sampling, greatly expanding their capabilities and use cases. This means that VAEs are generative AI models.

In simpler terms, VAEs learn to encode important feature learnings from the inputs in the datasets they’re trained on in a flexible, approximate way that allows them to generate new samples that resemble the original training data. The loss function used to minimize reconstruction error is regularized by the KL divergence between the probability distribution of training data (the *prior distribution*) and the distribution of latent variables learned by the VAE (the *posterior distribution*). This regularized loss function enables VAEs to generate new samples that resemble the data it was trained on while avoiding overfitting, which in this case would mean generating new samples too identical to the original data.

To generate a new sample, the VAE samples a random latent vector (*ε*) from within the unit Gaussian—in other words, selects a random starting point from within the normal distribution—shifts it by the *mean* of the latent distribution (*μ*) and scales it by the *variance* of the latent distribution (*σ*). This process, called *the reparameterization trick*,<sup>5</sup>[](#_ftn1) avoids direct sampling of the variational distribution: because the process in random, it has no derivative—which eliminates the need for backpropagation over the sampling process.

When a VAE is being used for generative tasks, the encoder can often be discarded after training. More advanced evolutions of VAEs, like conditional VAEs, give a user more control over generated samples by providing *conditional* inputs that modify the output of the encoder.

## Autoencoder use cases

Both generative and deterministic autoencoders have a wide variety of use cases across different fields and data types.

- **Data compression:** Autoencoders naturally learn a compressed representation of input data.
- **Dimensionality reduction:** The encodings learned by autoencoders can be used as input to larger, composite neural networks. Dimensionality reduction of complex data can extract features relevant to other tasks, as well as increase computational speed and efficiency.
- **Anomaly detection and facial recognition:** Autoencoders can detect anomalies, fraud or other defects—and, conversely, confirm a genuine match—by determining the reconstruction loss of examined data relative to the “normal” or “genuine” example it’s compared against.
- **Image denoising and audio denoising:** Denoising autoencoders can remove extraneous artifacts or corruption that does not match the latent space representation learned by the network.
- **Image reconstruction:** Inverting techniques learned for denoising, autoencoders can fill in missing elements of an image. They can be similarly used to colorize images.
- **Generative tasks:** VAEs and adversarial autoencoders (AAEs), which learn probabilistic distributions akin to those learned by VAEs but use an adversarial discriminator network (similar to [generative adversarial networks](https://developer.ibm.com/articles/generative-adversarial-networks-explained/)) in place of KL divergence, have been used with great success for generative tasks. Prominent generative applications of autoencoders include OpenAI’s original Dall-E model for image generation<sup>6</sup>[](#_ftn1) and even the generation of molecular structures used for medications.<sup>7</sup>[](#_ftn2)

## Footnotes

*All links are located outside ibm.com*

<sup>1</sup> ["Contractive Auto-Encoders: Explicit Invariance During Feature Extraction".](https://icml.cc/2011/papers/455_icmlpaper.pdf) *Proceedings of the 28<sup>th</sup> International Conference on Machine Learning*. July 2011  
 <sup>2</sup> ["Frobenius Norm".](https://mathworld.wolfram.com/FrobeniusNorm.html) Wolfram Mathworld  
 <sup>3</sup> ["Matrix Norms".](https://mathworld.wolfram.com/FrobeniusNorm.html) UC Berkeley. February 2021  
 <sup>4</sup> ["High-Resolution Image Synthesis With Latent Diffusion Models".](https://www.computer.org/csdl/proceedings-article/cvpr/2022/694600k0674/1H1iFsO7Zuw) *Proceedings of the IEEE/CVF Conference on Computer Vision and Pattern Recognition (CVPR)*. June 2022  
 <sup>5 </sup>["Auto-Encoding Variational Bayes".](https://arxiv.org/abs/1312.6114) arXiv. December 2013 (last updated December 10, 2022)  
 <sup>6 </sup>["DALL-E: Creating Images from Text".](https://openai.com/index/dall-e/) OpenAI. January 5, 2021  
 <sup>7 </sup>["Junction Tree Variational Autoencoder for Molecular Graph Generation".](https://proceedings.mlr.press/v80/jin18a/jin18a.pdf) *Proceedings of the 35<sup>th</sup> International Conference on Machine Learning*. July 2018
