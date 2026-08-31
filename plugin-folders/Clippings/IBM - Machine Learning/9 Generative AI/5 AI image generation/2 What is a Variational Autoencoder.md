---
title: What is a variational autoencoder?
source: https://www.ibm.com/think/topics/variational-autoencoder
author:
- '[[Dave Bergmann]]'
- '[[Cole Stryker]]'
published: 2024-08-12
created: 2026-08-31
description: "Variational autoencoders (VAEs) are generative models used in machine learning to generate new data samples as variations of the input data they’re trained on."
---

## What is a variational autoencoder?

Variational autoencoders (VAEs) are [generative models](https://www.ibm.com/think/topics/generative-ai) used in [machine learning](https://www.ibm.com/think/topics/machine-learning) (ML) to generate new data in the form of variations of the input data they’re trained on. In addition to this capability, they also perform tasks common to other autoencoders, such as denoising.

As with all [autoencoders](https://www.ibm.com/think/topics/autoencoder), variational autoencoders are [deep learning](https://www.ibm.com/think/topics/deep-learning) models composed of an encoder that learns to isolate the important latent variables from training data. The decoder then uses those latent variables to reconstruct the input data.

However, whereas most autoencoder architectures encode a discrete, fixed representation of latent variables, VAEs encode a continuous, probabilistic representation of that latent space. This approach enables a VAE to not only accurately reconstruct the exact original input, but also use variational inference to generate new data samples that resemble the original input data.

The [neural network](https://www.ibm.com/think/topics/neural-networks) architecture for the variational autoencoder was originally proposed in a 2013 paper by Diederik P. Kingma and Max Welling, titled [Auto-Encoding Variational Bayes](https://arxiv.org/abs/1312.6114). This paper also popularized what they called the reparameterization trick, an important machine‑learning technique that enables the use of randomness as a model input without compromising the model’s differentiability. This method preserves the model’s ability to optimize its parameters.

While VAEs are frequently discussed in the context of image generation, including in this article, they can be used for a diverse array of AI applications. This versatility spans [anomaly detection](https://www.ibm.com/think/topics/anomaly-detection)<sup>1</sup> to generating new drug [molecules](https://www.nature.com/articles/s42004-023-01054-6)<sup>2</sup>.

![A demonstration of the output of a variational autoencoder, using handwritten digits](https://assets.ibm.com/is/image/ibm/variational-autoencoder-manifold-traversal?ts=1783429634218&dpr=off)   TOP: handwritten digits from the MNIST data set; BOTTOM: original samples output by a VAE trained on those MNIST digits. Source: Mak, Hugo and Han, Runze and Yin, Hoover. (2023)

## What is latent space?

Essential to understanding VAEs or any other type of autoencoders is the notion of latent space, the name given to the collective latent variables of a specific set of input data. In short, latent variables are underlying variables in data that inform the way the data is distributed but are often not directly observable.

For a useful visualization of the concept of latent variables, imagine a bridge with a sensor that measures the weight of each passing vehicle. Naturally, there are different kinds of vehicles that use the bridge, from small, lightweight convertibles to huge, heavy trucks.

Because there is no camera, we have no way to detect if a specific vehicle is a convertible, sedan, van or truck. However, we do know that the type of vehicle significantly influences that vehicle’s weight.

This example thus entails two random variables, **x** and **z**, in which **x** is the directly observable variable of vehicle weight and **z** is the latent variable of vehicle type. The primary training objective for any autoencoder is for it to learn how to efficiently model the latent space of a particular input.

### Latent space and dimensionality reduction

Autoencoders model latent space through [dimensionality reduction](https://www.ibm.com/think/topics/dimensionality-reduction): the compression of data into a lower-dimensional space that captures the meaningful information contained in the original input.

In a machine learning (ML) context, mathematical dimensions correspond not to the familiar spatial dimensions of the physical world, but to features of data. For example, a 28×28‑pixel black‑and‑white image of a handwritten digit from the [MNIST data set](https://dataplatform.cloud.ibm.com/exchange/public/entry/view/e5ec6df59cd736a6b6b091062e3715a2?context=cpdaas) can be represented as a 784‑dimensional vector. In this vector, each dimension corresponds to an individual pixel whose value ranges from 0 (for black) to 1 (for white).

That same image in color might be represented as a 2,352‑dimensional vector. In this vector, each of the 784 pixels is represented in three dimensions corresponding to its respective red, green and blue (RGB) values.

However, not all those dimensions contain useful information. The actual digit itself represents only a small fraction of the image, so most of the input space is background noise. Compressing data down to only the dimensions containing relevant information—the latent space—can improve the accuracy, efficiency and efficacy of many ML tasks and algorithms.

![Visual depiction of an autoencoder](https://assets.ibm.com/is/image/ibm/variational-autoencoder-neural-network?ts=1783429634771&dpr=off)   Visual depiction of the architecture of a standard autoencoder neural network.

## What is an autoencoder?

VAEs are a subset of the larger category of [autoencoders](https://www.ibm.com/think/topics/autoencoder), a [neural network](https://www.ibm.com/think/topics/neural-networks) architecture typically used in [deep learning](https://www.ibm.com/think/topics/deep-learning) for tasks such as data compression, image denoising, anomaly detection and facial recognition.

Autoencoders are [self-supervised](https://www.ibm.com/think/topics/self-supervised-learning) systems whose training goal is to compress (or encode) input data through dimensionality reduction and then accurately reconstruct (or decode) their original input by using that compressed representation.

On a fundamental level, the function of an autoencoder is to effectively extract the data’s most salient information—its latent variables—and discard irrelevant noise. What distinguishes different types of autoencoders from one another is the specific strategy they employ to extract that information and the use cases to which their respective strategy is best suited.

In training, the encoder network passes input data from the training data set through a “bottleneck” before it reaches the decoder. The decoder network, in turn, is then responsible for reconstructing the original input by using only the vector of latent variables.

After each training epoch, optimization algorithms such as [gradient descent](https://www.ibm.com/think/topics/gradient-descent) are used to adjust model weights to minimize the difference between the original data input and the decoder’s output. Eventually, the encoder learns to allow through the information most conducive to accurate reconstruction and the decoder learns to effectively reconstruct it.

While this approach most intuitively lends itself to straightforward data compression tasks, the ability to efficiently encode accurate latent representations of unlabeled data gives autoencoders a wide variety of applications. For example, autoencoders can be used to restore corrupted audio files, colorize grayscale images or detect anomalies (such as instances resulting from fraud) that would otherwise be invisible to the naked eye.

### Autoencoder structure

Though different types of autoencoders add or alter certain aspects of their architecture to better suit-specific goals and data types, all autoencoders share three key structural elements:

The **encoder** extracts latent variables of input data *x* and outputs them in the form of a vector representing latent space *z.* In a typical “vanilla” autoencoder, each subsequent layer of the encoder contains progressively fewer nodes than the previous layer. As data traverses each encoder layer, it’s compressed through the process of “squeezing” itself into fewer dimensions.

Other autoencoder variants instead use regularization terms, such as a function that enforces sparsity by penalizing the number of nodes that are activated at each layer to achieve this dimensionality reduction.

The **bottleneck** or **“code”** is both the output layer of the encoder network and the input layer of the decoder network. It contains the latent space: the fully compressed, lower-dimensional embedding of the input data. A sufficient bottleneck is necessary to help ensure that the decoder cannot simply copy or memorize the input data, which would nominally satisfy its training task but prevent the autoencoder from learning.

The **decoder** uses that latent representation to reconstruct the original input by essentially reversing the encoder: in a typical decoder architecture, each subsequent layer contains a progressively *larger* number of active nodes.

While the encoder and decoder networks of many autoencoders are built from standard multilayer perceptrons (MLPs), autoencoders are not confined to any specific type of neural network.

Autoencoders used for [computer vision](https://www.ibm.com/think/topics/computer-vision) tasks are often [convolutional neural networks (CNNs)](https://www.ibm.com/think/topics/convolutional-neural-networks) and are thus called convolutional autoencoders. Autoencoders built from [transformer architecture](https://www.ibm.com/think/topics/transformer-model) have been used in multiple fields, including computer vision<sup>3</sup> and music.<sup>4</sup>

A key benefit of autoencoders over other dimensionality reduction algorithms, such as [principal component analysis (PCA),](https://www.ibm.com/think/topics/principal-component-analysis) is that autoencoders can model nonlinear relationships between different variables. For that reason, the nodes of autoencoder neural networks typically use nonlinear activation functions.

In many autoencoder applications, the decoder serves only to aid in the optimization of the encoder and is thus discarded after training. In variational autoencoders, the decoder is retained and used to generate new data points.

## How do variational autoencoders work?

What distinguishes VAEs from other autoencoders is the unique way they encode latent space and the different use cases to which their probabilistic encoding can be applied.

Unlike most autoencoders, which are deterministic models that encode a single vector of discrete latent variables, VAES are probabilistic models. VAEs encode latent variables of training data not as a fixed discrete value **z**, but as a continuous range of possibilities expressed as a probability distribution **p(z)**.

In [Bayesian statistics](https://www.ibm.com/think/topics/naive-bayes#A+brief+review+of+Bayesian+statistics), this learned range of possibilities for the latent variable is called as the prior distribution. In variational inference, the generative process of synthesizing new data points, this prior distribution is used to calculate the posterior distribution, **p(z|x).** In other words, the value of observable variables **x,** given a value for latent variable **z**.

For each latent attribute of training data, VAEs encode two different latent vectors: a vector of means, “**μ**” and a vector of standard deviations, “**σ**”. In essence, these two vectors represent the range of possibilities for each latent variable and the expected variance within each range of possibilities.

By randomly sampling from within this range of encoded possibilities, VAEs can synthesize new data samples that, while unique and original unto themselves, resemble the original training data. Though relatively intuitive in principle, this methodology requires further adaptations to standard autoencoder methodology to be put into practice.

To explain this ability of VAEs, we’ll review the following concepts:

- Reconstruction loss
- Kullback-Leibler (KL) divergence
- Evidence lower bound (ELBO)
- The reparameterization trick

### Reconstruction loss

Similar to all autoencoders, VAEs use reconstruction loss, also called reconstruction error, as a primary loss function in training. Reconstruction error measures the difference (or “loss”) between the original input data and the reconstructed version of that data output by the decoder. Multiple algorithms, including cross-entropy loss or mean-squared error (MSE), can be used as the reconstruction loss function.

As explained earlier, the autoencoder architecture creates a bottleneck that allows only a subset of the original input data to pass through to the decoder. At the onset of training, which typically begins with a randomized initialization of model parameters, the encoder has not yet learned which parts of the data to weigh more heavily.

As a result, it will initially output a suboptimal latent representation and the decoder will output a fairly inaccurate or incomplete reconstruction of the original input.

By minimizing reconstruction error through gradient descent over the encoder and decoder parameters, the autoencoder’s weights are adjusted to yield a more useful encoding of latent space. This adjustment produces a more accurate reconstruction.

Mathematically, the goal of the reconstruction loss function is to optimize p<sub>θ</sub>(z|x), in which **θ** represents the model parameters that enforce accurate reconstruction of input **x** given latent variable **z**.

Reconstruction loss alone is sufficient to optimize most autoencoders, whose sole goal is a learning compressed representation of input data that’s conducive to accurate reconstruction.

However, the goal of a variational autoencoder is not to reconstruct the original input; it’s to generate new samples that resemble the original input. For that reason, an additional optimization term is needed.

### Kullback-Leibler divergence

For the purposes of variational inference, the generation of new samples by a trained model, reconstruction loss alone can result in an irregular encoding of latent space. This encoding [overfits](https://www.ibm.com/think/topics/overfitting) the training data and doesn’t generalize well to new samples. Therefore, VAEs incorporate another regularization term: Kullback-Leibler divergence or KL divergence.

To generate images, the decoder samples from the latent space. Sampling points in latent space that represent original training inputs would replicate those inputs. To generate new images, the VAE must be able to sample from anywhere in the latent space between the original data points. For this requirement to be possible, the latent space must exhibit two types of regularity:

- **Continuity:** Nearby points in latent space should yield similar content when decoded.
- **Completeness:** Any point sampled from the latent space should yield meaningful content when decoded.

A simple way to implement both continuity and completeness in latent space is to help ensure that it follows a standard normal distribution, called a Gaussian distribution. But minimizing only reconstruction loss doesn’t encourage the model to organize the latent space in any particular way. For this limitation, the “in‑between” space is not relevant to the accurate reconstruction of the original data points. This mechanism is where the KL divergence regularization term comes into play.

KL divergence is a metric used to compare two probability distributions. Minimizing the KL divergence between the learned distribution of latent variables and a Gaussian distribution whose values range from 0–1 forces the learned encoding of latent variables to follow a normal distribution. This property allows smooth interpolation of any point in latent space and enables the generation of new images.

![A comparison of latent space using only reconstruction loss, only KL divergence, and a combination of both](https://assets.ibm.com/is/image/ibm/variational-autoencoder-distribution?ts=1783429637497&dpr=off)   Examples of how reconstruction loss and KL divergence affect the modeling of latent space for handwritten digits of 0–9 from the MNIST dataset.

### Evidence lower bound (ELBO)

One obstacle to using KL divergence for variational inference is that the denominator of the equation is intractable, meaning it would take a theoretically infinite amount of time to compute directly. To work around that problem and integrate both key loss functions, VAEs approximate the minimization of KL divergence by instead maximizing the evidence lower bound (ELBO).

In statistical terminology, the “evidence” in “evidence lower bound” refers to p(x), the observable input data that the VAE is ostensibly responsible for reconstructing. Those observable variables in the input data are the “evidence” for the latent variables discovered by the autoencoder. The “lower bound” refers to the worst-case estimate for the log-likelihood of a specific distribution. The actual log-likelihood might be higher than the ELBO.

In the context of VAEs, the evidence lower bound refers to the worst‑case estimate of the likelihood that a specific posterior distribution fits the “evidence” of the training data. This estimate represents a specific output of the autoencoder, conditioned by both the KL divergence loss term and the reconstruction loss term. Hence, training a model for variational inference can be referred to in terms of maximizing the ELBO.

### The reparameterization trick

As has been discussed, the goal of variational inference is to output new data in the form of random variations of the training data **x**. At first glance, this approach is relatively straightforward: use a function ƒ that selects a random value for the latent variable z, which the decoder can then use to generate an approximate reconstruction of x.

However, an inherent property of randomness is that it can’t be optimized. There is no “best” random; a vector of random values, by definition, has no derivative—that is, no gradient expressing any pattern in the resultant model outputs. This limitation means it can’t be optimized through backpropagation by using any form of gradient descent.

This limitation would mean that a neural network that uses the preceding random sampling process cannot learn the optimal parameters to do its task.

To circumvent this obstacle, VAEs use the reparameterization trick. The reparameterization trick introduces a new parameter, **ε**, which is a random value selected from the normal distribution between 0–1.

It then reparameterizes the latent variable z as z = μx + εσx. In simpler terms, it chooses a value for the latent variable z by starting with the mean of that variable (represented by μ). It then shifts by a random multiple (represented by ε) of a standard deviation (σ). Conditioned by that specific value of z, the decoder outputs a new sample.

Because the random value ε is not derived from and has no relation to the autoencoder model’s parameters, it can be ignored during backpropagation. The model is updated through some form of gradient descent—most often through [Adam](https://arxiv.org/abs/1412.6980), a gradient-based optimization algorithm also developed by Kingma—to maximize the ELBO.

## Conditional VAEs (CVAEs)

One shortcoming of conventional “vanilla” VAEs is that the user has no control over the specific outputs generated by the autoencoder. For example, a conventional VAE trained on the previously mentioned MNIST data set will generate new samples of handwritten digits from 0–9. It cannot be constrained to output only 4 s and 7 s.

As their name suggests, conditional VAEs (CVAEs) enable outputs conditioned by specific inputs, rather than solely generating variations of training data at random. This approach is achieved by incorporating elements of [supervised learning](https://www.ibm.com/think/topics/supervised-learning) (or [semisupervised learning](https://www.ibm.com/think/topics/semi-supervised-learning)). It does so alongside the traditionally [unsupervised](https://www.ibm.com/think/topics/unsupervised-learning) training objectives of conventional autoencoders.

By further training the model on labeled examples of specific variables, those variables can be used to condition the output of the decoder. For example, a CVAE can be first trained on a large data set of facial images. It can then be trained by using supervised learning to learn a latent encoding for “beards” so that it can output new images of bearded faces.

## VAEs versus GANs

VAEs are often compared with generative adversarial networks (GANs), another model architecture used to generate samples that resemble training data, especially for images.

Similar to VAEs, GANs are a joint architecture combining two neural networks: a generator network responsible for outputting image samples that resemble images from the training data set. A discriminator network is then responsible for determining whether a specific image is a “real” image from the training data or a “fake” image from the generator network.

The two networks are trained adversarially in a zero-sum game: the feedback from the discriminator is used to improve the output of the generator until the discriminator is no longer able to discern between real and fake samples.

For image synthesis, both have upsides and downsides: GANs produce clearer images but due to the adversarial tradeoffs between the two composite models, are unstable in training. VAEs are easier to train but due to the nature of producing images from the “average” features of training data, tend to produce blurrier images.

### VAE-GANs

A VAE-GAN is, as its name suggests, a hybrid between a variational autoencoder (VAE) and a generative adversarial network (GAN). It reduces the blurriness of VAE-generated images by replacing the VAE model’s reconstruction loss term with a discriminator network.

## Footnotes

External links to ibm.com

1 [“Novel applications for VAE-based anomaly detection systems”](https://arxiv.org/abs/2204.12577). arXiv, 26 April 2022  
 2 [“Variational autoencoder-based chemical latent space for large molecular structures with 3D complexity”](https://www.nature.com/articles/s42004-023-01054-6). Nature*,* 16 November 2023  
 3 [“Masked autoencoders are scalable vision learners”](https://arxiv.org/abs/2111.06377). arXiv, 11 November 2021  
 4 [“Encoding musical style with transformer autoencoders”](https://arxiv.org/abs/1912.05537). arXiv, 10 December 2019
