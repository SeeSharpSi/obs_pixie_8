---
title: What are diffusion models?
source: https://www.ibm.com/think/topics/diffusion-models
author:
- '[[Dave Bergmann]]'
- '[[Cole Stryker]]'
published: 2024-09-12
created: 2026-08-31
description: "Diffusion models are generative models that “diffuse” training data with random noise, then learn to reverse the diffusion process to output new images."
---

## What are diffusion models?

Diffusion models are generative models used primarily for image generation and other computer vision tasks. Diffusion-based [neural networks](https://www.ibm.com/topics/neural-networks) are trained through [deep learning](https://www.ibm.com/topics/deep-learning) to progressively “diffuse” samples with random noise, then reverse that diffusion process to generate high-quality images.

Diffusion models are among the neural network architectures at the forefront of [generative AI](https://www.ibm.com/topics/generative-ai), most notably represented by popular text-to-image models including Stability AI’s Stable Diffusion, OpenAI’s DALL-E (beginning with DALL-E-2), Midjourney and Google’s Imagen. They improve upon the performance and stability of other [machine learning](https://www.ibm.com/topics/machine-learning) architectures used for image synthesis such as [variational autoencoders (VAEs),](https://www.ibm.com/think/topics/variational-autoencoder) generative adversarial networks (GANs) and autoregressive models such as PixelCNN.

The intuition behind diffusion models is inspired by physics, treating pixels like the molecules of a drop of ink spreading out in a glass of water over time. Much like how the random movement of the ink molecules will eventually lead to their even dispersal in the glass, the random introduction of noise into an image will eventually result in what looks like TV static. By modeling that diffusion process, then somehow learning to *reverse* it, an [artificial intelligence model](https://www.ibm.com/topics/ai-model) can generate new images by simply “denoising” samples of random noise.

Diffusion models are most prominently associated with image generation and other image processing tasks such as inpainting and super-resolution, but their applications extend to other domains including audio generation, drug design and molecule generation. For simplicity, this article will focus on image generation.

## History and theory of diffusion models

To explain and understand diffusion models, it’s important to first note that the generative process now called “diffusion” was independently discovered on two separate occasions through two distinct mathematical approaches. In short, there are *multiple* ways that diffusion models, which are conceptually simple but mathematically complex, can “work.”

Subsequent developments have borrowed ideas from both approaches, blending the advantages of each to eventually yield the modern diffusion models that currently dominate the field of image generation. A brief review of the history and theory of diffusion models thus facilitates an understanding of not only *how* diffusion models work, but *why* they work.

### Deep learning models inspired by thermodynamics

Physics-inspired diffusion models were first introduced by Sohl-Dickstein *et al* in their 2015 paper, “Deep Unsupervised Learning using Nonequilibrium Thermodynamics.” Their algorithm applied [*Langevin dynamics*](https://en.wikipedia.org/wiki/Langevin_dynamics)*,* a method for modeling the movement of molecular systems, to underwrite the basic premise of diffusion models: turn data into noise, so you can then turn noise into data.

#### A note on probability density functions

Like most generative models, such as variational autoencoders (VAEs), Sohl-Dickstein’s algorithm modeled *probability density:* the relative likelihood of a randomly sampled variable, *x*, falling within a particular range of values. Essentially, modeling a probability density function for a training data set allows an algorithm to then generate samples that are highly likely to fit the training data distribution. When generating a new image, the model is assuming a *high probability* of pixel values being distributed in that specific way, based on the probability distribution it learned from patterns in training data.

Logically speaking, probability density functions require the likelihood of all possibilities to sum up to 1. Put another way, the percentage chance of all possibilities must sum up to exactly 100%. In practice, this often requires a *normalizing constant:* a value incorporated into a probability function that reduces total probability to 1.

Calculating a normalization constant that works for all possible variable values is often *intractable:* technically solvable, but requiring infinite time to compute. In such cases, likelihood-based models must either be restricted to specific model architectures or develop clever workarounds that approximate the normalization constant in a tractable way.

### Score-based generative models

Independently of Sohl-Dickstein’s work, Yang Song and Stefano Ermon developed a type of [energy-based model](https://arxiv.org/abs/2101.03288) called a *noise conditional score network* in their 2019 paper, “Generative Modeling by Estimating Gradients of the Data Distribution.” Their algorithm modeled the [*gradient*](https://www.ibm.com/think/topics/backpropagation#Key+mathematical+concepts) (∇<sub>x</sub>) of the logarithm ($log$) of the probability density function $p(x)$. The gradient of the log probability density function, written as $∇_x\log{p(x)}$, is called the *Stein score* or simply the “score function."

Unlike conventional probability density functions, *score functions* don’t require a normalizing constant because they don’t directly model probability density (and therefore don’t have to normalize total probability to 1). Instead, they’re trained through *score matching*: learning model parameters, *θ, that yields* a model *p*<sub>θ</sub>(*x*) whose score—in other words, its gradient—matches that of the data distribution *q*(*x*) of the training data.

Another benefit of such score-based generative models (SGMs) is that, unlike likelihood-based models, they don’t impose many restrictions on the model architecture of *p*<sub>θ</sub>(*x*).

Exploring ways to improve their model’s performance, Song and Ermon coincidentally arrived at the same techniques employed by Sohl-Dickstein *et al.* Their paper noted that “perturbing data with random [Gaussian](https://www.ibm.com/docs/en/cognos-analytics/12.0.0?topic=terms-normal-distribution) noise makes the data distribution more amenable to score-based generative modeling.” Their model, built using [the U-Net](https://www.ibm.com/topics/image-segmentation#Deep+learning+image+segmentation+models) architecture originally developed for [image segmentation](https://www.ibm.com/topics/image-segmentation), likewise applied Langevin dynamics to generate samples.

### Denoising diffusion probabilistic models (DDPMs)

In 2020, Ho *et al* proposed using Sohl-Dickstein’s approach to generate high-quality images by using variational inference in their seminal paper, “Denoising diffusion probabilistic models” (DDPMs). Their paper showed that maximizing the [evidence lower bound (ELBO)](https://www.ibm.com/think/topics/variational-autoencoder#How+variational+autoencoders+work)—a way to rewrite probability-based optimization problems to be tractable—to train diffusion models is essentially equivalent to the combination of score matching objectives used to train SGMs.

Implementing Sohl-Dickstein’s approach using score matching, Ho *et al* demonstrated that diffusion probabilistic models can achieve image quality competitive with GANs, which at the time were state-of-the-art. These connections were further explored by Song, Ermon, Sohl-Dickstein and others—including Diederik P. Kingma, creator of the VAE—in their 2021 paper, “Score-Based Generative Modeling through Stochastic Differential Equations.”

Later that year, Dhariwal and Nichol, leveraging insights from the previously mentioned paper, published “Diffusion Models Beat GANs on Image Synthesis,” firmly establishing diffusion models as the new state-of-the-art.

DDPMs, rather than SGMs, generally remain the dominant mode of diffusion models, albeit with improvements pioneered through subsequent research. For example, the influential 2022 paper “High-Resolution Image Synthesis with Latent Diffusion Models” marked important advancements in efficiency and cost-effectiveness.

## How do diffusion models work?

In training, diffusion models gradually *diffuse* a data point with random noise, step-by-step, until it’s destroyed, then learn to reverse that diffusion process and reconstruct the original data distribution.

A trained diffusion model can then generate new data points that resemble the training data by simply *denoising* a random initial sample of pure noise. Conceptually, this is similar to a [denoising autoencoder](https://www.ibm.com/topics/autoencoder#Regularized+autoencoders) in which the noisy images act as latent variables.

Directly transforming random noise into a coherent image is extremely difficult and complex, but transforming a noisy image into *a slightly less noisy* image is relatively easy and straightforward. Diffusion models therefore formulate the reverse diffusion process as an incremental, step-by-step transformation of a simple distribution (like [Gaussian](https://www.ibm.com/docs/en/cognos-analytics/12.0.0?topic=terms-normal-distribution) noise) to a more complex distribution (like a coherent image).

The process of training and then deploying a diffusion can be broken down into three key stages:

- **The forward diffusion process,** wherein an image from the training data set is transformed into pure noise—usually a gaussian distribution.
- **The reverse diffusion process,** wherein the model learns the inverse of each previous step in the original forward diffusion process.
- **Image generation,** wherein the trained model samples a random noise distribution and transforms it into a high-quality output by using the reverse diffusion process it has learned to denoise a random sample of gaussian noise.

## Forward diffusion process

The purpose of the forward diffusion process is to transform clean data from the training dataset, such as an image or audio sample, into pure noise. The most common method entails iteratively injecting gaussian noise until the entire data distribution is gaussian.

Mathematically, this step-by-step process is formulated as a [*Markov chain*](https://community.ibm.com/community/user/ai-datascience/blogs/moloy-de1/2020/03/26/points-to-ponder): a type of stochastic process—a random process that follows certain probabilistic rules—for modeling sequential time-series data. In a Markov chain, the outcome at each timestep is influenced only by the timestep immediately preceding it. Put simply: *x*<sub>t</sub>*,* the state of the Markov chain *x* at timestep *t,* is directly influenced only by *x*<sub>t-1</sub>. The mathematical function defining the transition from any *x*<sub>t</sub> to *x*<sub>t+1</sub> is called a *transition kernel.*

At each timestep *t,* a small amount of Gaussian noise is added to *x*<sub>t-1</sub> and the image is then rescaled to maintain a constant image size despite the continual injection of random pixels. In this formulation, *x*<sub>0</sub> is the original clean data point; *x*<sub>1</sub> is the data point after the first timestep, with a small amount of gaussian noise added to it; *x*<sub>T</sub> is the final state of forward diffusion process. If T is large enough—that is, after enough steps—*x*<sub>T</sub> will converge to pure gaussian noise.

We define each forward step as *$q(x_t|x_{t-1}): $*predict the state of the data distribution *q*(x<sub>t</sub>), given *q*(x<sub>t-1</sub>). In a standard DDPM, this forward process does not involve any machine learning: the end result of the Markov chain will always be a gaussian distribution, and thus does not require optimization.

### Adding noise

In a DDPM, the Gaussian noise added at each step in the Markov chain is neither constant nor arbitrary. Instead, the noise is derived from the structure of the original image and the rate at which it’s added steadily increases with each consecutive step.

Varying the amount of noise both improves the stability of model training and enhances overall performance by balancing two competing priorities. As noted by Yang Song in [his blog post about score-based generative models](https://yang-song.net/blog/2021/score/#score-based-generative-modeling-with-multiple-noise-perturbations):

- *Larger noise* improves the model’s ability to accurately learn in “low density” regions of training data—visual categories and concepts that have less representation in training data—by populating those regions with noisy data. But it can also over-corrupt data, reducing overall accuracy.
- *Smaller noise* causes less corruption of the original data distribution but yields poor performance on low density regions.
- Therefore, to achieve the best of both worlds, *diffusion models use multiple scales of noise* in training.

Recall that any gaussian (normal) distribution has both a mean, $ \mu$ , and a variance, $\mathrm{\Sigma}$ . Another parameter, *β,* serves as a scaling factor for the mean and variance of the gaussian noise in the transition kernel that defines each step in the forward Markov chain. Changing the value of *β* in a given step results in changing the gaussian noise added at that step. *β<sub>1</sub>*<sub> </sub>is the variance at timestep 1; *β*<sub>t</sub> is the variance at timestep *t*, and so on, until *β*<sub>T</sub>.

The rate value of *β* at each step is, in turn, determined by the *variance schedule.*

### Variance schedule

At each step *t,* the image is slightly shifted from its iteration in the previous step (per the mean) and noise is added to this shifted version of the image (per the variance). The magnitude of each shift and addition of noise is driven by the value of βt: as βt increases in accordance with the variance schedule, the rate of diffusion steadily increases as a result. *β* is always a value between 0 and 1: so, 0 < *β<sub>1</sub> < β<sub>2 </sub>< … < β<sub>T</sub> <* 1.

Choosing a specific variance schedule for *β* is an important consideration. It’s usually set by hand as a hyperparameter, either fixed to a constant value or proceeding according to some formula with a predetermined starting value and end value for *β*. In the DDPM paper, Ho *et al* used a linear schedule with 1,000 steps wherein *β*<sub>1</sub> = 10<sup>-4</sup> and *β*<sub>T</sub> = 0.02. Later research found improvements in performance and efficiency with other types of schedules, such as a cosine schedule,<sup>[1]</sup> or making the schedule itself another learned parameter.<sup>[2]</sup>

The value of *β<sub>t</sub>* determines both the mean and variance of the Gaussian noise added at step *t.*

- The **mean** $\mu$ of the gaussian noise added at timestep *t,* $\mu_t$, is calculated as $\mu_t=\left(1-\beta_t\right)x_{t-1}$. In plain language, the average of the noise added at each step *t* is simply a scaled version of the image from the previous step, *x*<sub>t-1</sub>. The size of *β<sub>t</sub>* determines how far this mean deviates from the previous step: when *β<sub>t</sub>* is very small, this shift is very minor—because $\left(1-\beta_t\right)\approx(1-0)\approx1$—and the added noise will thus closely resemble the original image. As the value of *β<sub>t </sub>*increases, this shift becomes more significant.
- The **variance** of the gaussian noise added at timestep *t* is calculated as $\mathrm{\Sigma}_t= \beta_tI$, where $I$ is the [*identity matrix*](https://deepai.org/machine-learning-glossary-and-terms/identity-matrix). A larger *β<sub>t</sub>* results in more noise. A very small *β<sub>t</sub>* results in negligible noise.

In summary, at each step *t,* the image is slightly shifted from its iteration in the previous step (per the mean) and noise is added to this shifted version of the image (per the variance). The magnitude of each shift and addition of noise is driven by the value of *β<sub>t</sub>*: as *β<sub>t</sub>* increases in accordance with the variance schedule, the rate of diffusion steadily increases as a result.

Because the addition of gaussian noise begins gradually and the noise itself is always derived from the essential structure of the original image in the previous step, the essential qualities of the original image are retained for many steps. This enables the model to meaningfully learn the patterns and structure of the original data distribution during the reverse diffusion process.

### The reparameterization trick

One shortcoming of that step-by-step process is that it’s cumbersome and computationally expensive: for each image in a training data set that might contain thousands or millions of images, the forward process would require dozens or hundreds of individual steps.

Instead of repeatedly adding noise, the formula for the forward process can be rewritten in a clever way by *reparameterizing* the expression of $1–\beta_t$ as a new parameter, $\alpha_t$. Through a “nice property” of Markov chains, this new parameter can be further extended to an additional parameter, ${\bar{\alpha}}_t$, derived from the iterative multiplication of $\alpha_t$ at each progressive step in the chain up to that point. This additional parameter essentially reflects the signal-to-noise ratio (SNR) of *x<sub>t</sub>*: in other words, how much of the original image remains at timestep *t*.

For instance, at *x*<sub>1</sub>*,* a small amount of noise has been added one time. The value of ${\bar{\alpha}}_t$ is close to 1, meaning the image still retains most of its original "signal." At a later step, like *x*<sub>50</sub>, noise has been added many times. Because $\alpha_t=1–\beta_t$, the value of $\alpha_t$ is always less than 1. Since ${\bar{\alpha}}_50=\alpha_1∙\alpha_2∙...∙\alpha_49∙\alpha_50
$, the value of ${\bar{\alpha}}_t$ at step 50 will be much closer to 0, meaning more of the original image has been replaced by noise. At timestep *T*, *x<sub>T</sub>* is entirely noise and the value of ${\bar{\alpha}}_t$ approaches 0.

While the complex derivation of the equation is beyond the scope of this article, there are two important takeaways to understand the importance of this reparameterization trick:

- The state of *x* at any timestep *t* can now be defined as $x_t=\sqrt{{\bar{\alpha}}_t}\bullet x_0+\sqrt{1-{\bar{\alpha}}_t}\bullet\varepsilon_0$, where $ε_0$ is the noise added in the first step. As the value of ${\bar{\alpha}}_t$ decreases with each step, the influence of *x*<sub>0</sub> decreases and the influence of *ε*<sub>0</sub> increases.
- Because $ {\bar{\alpha}}_t$ is derived from $1–\beta_t$ and the value of $\beta_t$ is determined by the variance schedule, rewriting the formula this way allows for the direct calculation of *x<sub>t</sub>* at any timestep *t* without having to go through the entire step-by-step forward process.

## Reverse diffusion process

In diffusion models, the reverse diffusion process is where the actual machine learning takes place. In learning to perform the reverse of the noising steps of the forward process, the model is essentially learning to denoise pure gaussian noise into a clean image. Once the neural network has been trained, this ability can be used to generate new images out of gaussian noise through step-by-step reverse diffusion.

In theory, the model’s task can be thought of as the simple reverse of forward diffusion. The forward process, starting with data point x<sub>0</sub> sampled from the real data distribution *q*(*x*) of the training data set, is defined as $q(x_t|x_{t-1})$: that is, given $q\left(x_{t-1}\right)$, calculate $q(x_t)$. Its opposite, reverse diffusion, would be defined as $q(x_{t-1}|x_t)$. But in practice, computing $q(x_{t-1}|x_t)$ is intractable.

Instead, the training task is formulated through two workarounds:

- As described earlier, *q*(x) is approximated with a neural network *p*<sub>θ</sub>(*x*) that constitutes the actual diffusion model itself. The goal of training is to learn the model parameters *θ* that make the output of *p*<sub>θ</sub>( $x_{t-1}|x_t$ ), match the output of *q*( $x_{t-1}|x_t$ ).
- This model, *p*<sub>θ</sub>(*x*), does not directly predict $x_{t-1}$, nor even the specific noise added between *x*<sub>t-1</sub> and *x*<sub>t</sub>. Instead, it predicts the *entire noise* present in *x*<sub>t</sub>, then removes a fraction of that noise (based on the state of the variance schedule at that step) to get to *x*<sub>t-1</sub>. The original DDPM paper further simplified this process by only estimating the *mean* of the gaussian noise, though later models often also predict the variance.

Recall again that the mean of the gaussian noise added in forward diffusion is not arbitrary: though it's indeed *random*, the structure of the noise is initially derived from the structure of the original image *x*<sub>0</sub>. Therefore, by learning to accurately predict the noise through reverse diffusion, the model not only learns to denoise the image, but also implicitly learns the structure of *x*<sub>0</sub>.

### Loss function for diffusion model training

The specific training objective used for diffusion models is closely related to the reconstruction loss term used to optimize [variational autoencoders (VAEs).](https://www.ibm.com/think/topics/variational-autoencoder) Like VAEs, diffusion models are optimized by maximizing the *variational lower bound* (VLB), also called the *evidence lower bound* (ELBO), of a combination of multiple loss terms.

Maximizing the VLB is used in variational inference to approximate the intractable score function $∇_x\log(p(x))$: instead of directly minimizing error, it reformulates the equation as maximizing the minimum estimation (or *lower bound*) of the accuracy of model predictions.

The loss terms used each reflect the [*Kullback-Leibler divergence*](https://research.ibm.com/publications/variational-kullback-leibler-divergence-for-hidden-markov-models) (or “KL divergence,” usually denoted as *D*<sub>KL</sub>) between the outcomes of forward diffusion steps of *q* and the reverse steps predicted by *p*<sub>θ</sub>. KL divergence is used to measure the difference between two probability distributions—for instance, between the distribution of pixel values in one image and the distribution of pixel values in another.

Specifically, the [loss function](https://www.ibm.com/think/topics/loss-function) for diffusion models combines three loss terms: ***L<sub>T</sub>**,* ***L*<sub>t</sub>**<sub> </sub>and ***L<sub>0</sub>**.*

- ***L<sub>T</sub>*** reflects the KL divergence between *q*$(x_T|x_0)$ and *p*<sub>θ</sub>(*x*<sub>T</sub>). In other words, the difference between the fully noised end result of the forward process *q* and the starting point of the reverse process. This term can generally be ignored, because *x*<sub>T</sub> is gaussian and *q* has no learnable parameters.
- ***L*<sub>t</sub>** reflects the KL divergence between $q(x_{t-1}|x_t,x_0)$ and $p_θ(x_{t-1}|x_t)$ at each step. In other words, the accuracy of each of *p*<sub>θ</sub>’s denoising predictions during reverse diffusion as compared to each corresponding noising step of during the forward diffusion process for the original image, x<sub>0</sub>.
- ***L<sub>0</sub>*** measures $-\log{p_θ(x_0|x_1)}$. In other words, *L<sub>0 </sub>*reflects the negative log likelihood of the model’s prediction of the fully denoised image *x*<sub>0</sub>. The gradient of *L*<sub>0</sub> is the *score matching* term described earlier in the article. The loss term is negative so that minimizing the loss function becomes the equivalent of maximizing the likelihood of the model's predictions.

Though its complex mathematical derivation is beyond the scope of this article, the VLB can ultimately be simplified down to the [*mean-squared error (MSE*)](https://www.ibm.com/think/topics/loss-function#Regression+loss+functions) *between the noise predicted by the model*, *$\varepsilon_\theta$ and the true noise added in the forward process*, *$\varepsilon$,* at each timestep. This explains why the model’s output is a prediction of noise at each step, rather than the denoised image itself.

By calculating the gradient of the [loss function](https://www.ibm.com/think/topics/loss-function) during [backpropagation](https://www.ibm.com/think/topics/backpropagation) and then adjusting model weights to minimize the loss function through [gradient descent](https://www.ibm.com/topics/gradient-descent), the model’s predictions across the entire training data set will become more accurate.

## Image generation with diffusion models

Once the diffusion model has learned to accurately estimate the noise to be subtracted at each step, it can be used to generate new images by sampling from a random noisy image *x*<sub>T</sub> from the data distribution it has learned and denoising it for T steps. Similar to VAEs, introducing a slight element of randomness into the sampling process enables diffusion models to produce *new* images that *resemble* the training data, rather than directly reproduce training images.

Unlike in the reverse diffusion training process, the amount of steps in the generation process does not have to match the amount of steps used in the forward process. This is possible because the model is trained to predict *the entire noise* at each image step, rather than the specific amount of noise to be removed in that step.

Fewer steps entail greater speed and lower computational demands, with a potential tradeoff in fine detail; more steps typically improve accuracy, albeit at the cost of decreased speed and increased computational costs.

### Guided diffusion models

While a standard diffusion model can produce high-quality variations of training images at random, most practical uses of an image generation model require some control over the model’s output. *Guided diffusion models* allow a user to condition the generated images with specific *guidance*.

The most common form of guided diffusion model is a text-to-image diffusion model that lets users condition the output with a text prompt, like “a giraffe wearing a top hat.” This entails pairing a diffusion model with a separate large language model (LLM) to interpret the text prompt, first introduced by Google in the paper “Photorealistic Text-to-Image Diffusion Models with Deep Language Understanding.”

Standard diffusion models aim to predict the unconditional score function ∇xlogp(x): in other words, the gradient of the logarithm of the likelihood that the image *x* generated by the model *p* fits the training data *x*. Guided diffusion models introduce a specific visual category, *y*—for example, “giraffe”—and predict the *conditional* score function ∇xlogp(x|y): in other words, the likelihood of image *x,* given that it must fit category *y.*

Methods for guided diffusion can be separated into two categories:

- *Classifier-guided diffusion* requires a separate classifier model to learn [vector embeddings](https://www.ibm.com/think/topics/vector-embedding) for each category *y* that the diffusion model will be trained to produce visuals for. This vector embedding is then used to condition the output at each step *t*. The diffusion model doesn’t require extra training, but will only be able to condition outputs on the specific categories learned by the classifier.
- *Classifier-free guidance* doesn’t require a separate model, but does require a two-stage diffusion model to be trained specifically for conditional guidance. This typically entails a two-stage model: in the first stage, an embedding algorithm like [CLIP](https://openai.com/index/clip/) generates an embedding *y* for the prompt. In the second stage, a diffusion model uses that embedding to condition its output. Despite the extra training overhead, this has the benefit of enabling [zero-shot](https://www.ibm.com/topics/zero-shot-learning) guidance for unseen image categories.

## Latent diffusion models

Despite their state-of-the-art ability to generate high-quality images, conventional diffusion models have two important disadvantages: they’re slow and computationally expensive. These drawbacks were greatly reduced by the advent of *latent diffusion models,* beginning with Stable Diffusion.

The premise behind latent diffusion models is simple, drawing once again on the connection to variational autoencoders (VAEs). Rather than applying the diffusion process in high-dimensional *pixel space*—that is, directly to input images—the model could first project input to lower-dimensional [*latent space*](https://www.ibm.com/think/topics/variational-autoencoder)*,* then apply the diffusion process there.

In essence, latent diffusion models employ a VAE-like autoencoder architecture to train an encoder to output latent representations *z* of input data *x*. Those latent representations are then used as the input to a standard diffusion model, typically using the U-Net architecture. Because the diffusion model is working with lower-dimensional data, its output is then fed into a decoder network for upsampling into the desired final image size.

## Footnotes

*NOTE: All links reside outside ibm.com.*

[1] [“Improved Denoising Diffusion Probabilistic Models,”](https://arxiv.org/abs/2102.09672) arXiv, 18 February 2021  
 [2] [“Variational Diffusion Models,”](https://arxiv.org/abs/2107.00630) arXiv, last revised 14 April 2023
