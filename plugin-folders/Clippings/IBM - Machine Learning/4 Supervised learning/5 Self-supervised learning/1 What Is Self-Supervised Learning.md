---
title: What is self-supervised learning?
source: https://www.ibm.com/think/topics/self-supervised-learning
author:
- '[[Dave Bergmann]]'
published: 2024-12-03
created: 2026-08-31
description: "Self-supervised learning is a machine learning technique that uses unsupervised learning for tasks typical to supervised learning, without labeled data."
---

## What is self-supervised learning?

Self-supervised learning is a [machine learning technique](https://www.ibm.com/topics/machine-learning) that uses [unsupervised learning](https://www.ibm.com/topics/unsupervised-learning) for tasks that conventionally require [supervised learning](https://www.ibm.com/topics/supervised-learning). Rather than relying on labeled datasets for supervisory signals, self-supervised models generate implicit labels from unstructured data.

Self-supervised learning (SSL) is particularly useful in fields like [computer vision](https://www.ibm.com/topics/computer-vision) and [natural language processing (NLP)](https://www.ibm.com/topics/natural-language-processing) that require large amounts of labeled data to train state-of-the-art [artificial intelligence (AI) models](https://www.ibm.com/topics/ai-model). Because these labeled datasets require time-consuming annotation by human experts, gathering sufficient data can be prohibitively difficult. Self-supervised approaches can be more time- and cost-effective, as they replace some or all need to manually label training data.

To train a deep learning model for tasks that require accuracy, like classification or regression, one must be able to compare the model’s output predictions for a given input to the “correct” predictions for that input—usually called the *ground truth*. Customarily, manually labeled training data serves as that ground truth: because this method requires direct human intervention, it’s called “supervised” learning. In *self-*supervised learning, tasks are designed such that “ground truth” can be *inferred* from *unlabeled* data.

In SSL, tasks fall into two categories: *pretext tasks* and *downstream tasks.* In a *pretext task*, SSL is used to train an AI system to learn meaningful representations of unstructured data. Those learned representations can be subsequently used as input to a *downstream task*, like a supervised learning task or reinforcement learning task. The reuse of a pre-trained model on a new task is referred to as “transfer learning.”

Self-supervised learning is used in the training of a diverse array of sophisticated deep learning architectures for a variety of tasks, from transformer-based large language models (LLMs) like BERT and GPT to image synthesis models like variational [autoencoders](https://www.ibm.com/topics/autoencoder) (VAEs) and generative adversarial networks (GANs) to computer vision models like SimCLR and Momentum Contrast (MoCo).

## Self-supervised learning vs. supervised learning vs. unsupervised learning

Though self-supervised learning is a technically a subset of *unsupervised learning* (as it doesn’t require labeled datasets), it’s closely related to *supervised learning* in that it optimizes performance against a ground truth.

This imperfect fit with both conventional machine learning paradigms led to the various techniques now collectively considered “self-supervised learning” receiving their own categorization.

Coining of the term is often attributed to Yann LeCun, Turing Award-winning computer scientist and key figure in the advent of deep learning,<sup>1</sup>[](#_ftn1) who declared it necessary to disambiguate SSL from truly *unsupervised* learning (which he called “both a loaded and confusing term”).<sup>2</sup> [](#_ftn2)The name (and formal concept) may have its origins in a 2007 paper by Raina, et al, titled “Self-taught learning: Transfer learning from unlabeled data."<sup>3</sup>[](#_ftn3) Some machine learning frameworks now considered SSL, like autoencoders, predate the existence of the term itself by a number of years.

### Self-supervised learning vs. unsupervised learning

Self-supervised learning is a subset of unsupervised learning: all self-supervised learning techniques are unsupervised learning, but most unsupervised learning does not entail self-supervision.

Neither unsupervised nor self-supervised learning use labels in the training process: both methods learn *intrinsic* correlations and patterns in unlabeled data, rather than *externally imposed* correlations from annotated datasets. Apart from this shared focus on unlabeled data, the differences between self-supervised and unsupervised learning largely mirror the [differences between unsupervised and supervised learning](https://www.ibm.com/think/topics/supervised-vs-unsupervised-learning).

Problems using conventional unsupervised learning do not measure results against any pre-known ground truth. For example, an unsupervised [association model](https://dataplatform.cloud.ibm.com/docs/content/wsd/nodes/associationrules.html?context=cpdaas) could power an e-commerce recommendation engine by learning which products are frequently purchased together. The utility of the model is not derived from replicating human predictions, but from discovering correlations not apparent to human observers.

Self-supervised learning *does* measure results against a ground truth, albeit one implicitly derived from unlabeled training data. Like supervised models, self-supervised models are optimized using a *loss function:* an algorithm measuring the divergence (“loss”) between ground truth and model predictions. During training, self-supervised models use [gradient descent](https://www.ibm.com/topics/gradient-descent) during backpropagation to adjust model weights in a way that minimizes loss (and thereby improves accuracy).

Driven by this key difference, the two methods focus on different use cases: unsupervised models are used for tasks like clustering, anomaly detection and dimensionality reduction that do not require a loss function, whereas self-supervised models are used for classification and regression tasks typical to supervised learning.

### Self-supervised learning vs. supervised learning

While supervised and self-supervised learning are largely used for the same kinds of tasks and both require a ground truth to optimize performance via a loss function, self-supervised models are trained on unlabeled data whereas supervised learning requires labeled datasets for training.

Labeled datasets are highly effective in model training: annotating training data allows a model to directly learn the key features and correlations those annotations reflect. By minimizing the divergence between model predictions and the hand-annotated “predictions” of human experts during training, supervised models learn to make correct inferences about new (unlabeled) input data.

Though state-of-the-art supervised approaches can yield high accuracy, annotating large amounts of training is often a bottleneck in the research process. For example, in computer vision tasks like [instance segmentation](https://www.ibm.com/topics/instance-segmentation) that require pixel-specific predictions, annotation of training data must be done at the pixel level. This is costly and time-consuming, limiting both the amount of training data available and the ability of most enterprises and researchers to obtain it.

In contrast, self-supervised models use various techniques to obtain supervisory signals from the structure of the input data itself, eschewing labels altogether. For example, by randomly hiding (or “masking”) parts of a sentence and tasking a self-supervised model with predicting the hidden words, using the original (unlabeled) sentence as ground truth.

### Self-supervised vs. semi-supervised learning

Unlike self-supervised learning, which does not involve human-labeled data, *semi*-supervised learning uses both labeled and unlabeled data to train models. For example, a semi-supervised model might use a small amount of labeled data points to infer labels for the rest of an otherwise unlabeled set of training data, then proceed to use the entire dataset for supervised learning. Though their motivations are similar, as both approaches circumvent the need for large labeled datasets in supervised learning, their respective methodologies are different.

## How does self-supervised learning work?

Self-supervised learning tasks are designed such that a loss function can use unlabeled input data as ground truth. This allows the model to learn accurate, meaningful representations of the input data without labels or annotations.

The goal of self-supervised learning is to minimize or altogether replace the need for labeled data. While labeled data is relatively scarce and expensive, unlabeled data is abundant and relatively cheap. Essentially, *pretext tasks* yield “pseudo-labels” from unlabeled data. The term “pretext” implies that the training task is not (necessarily) useful unto itself: it is useful only because it teaches models data representations that are useful for the purposes of subsequent downstream tasks. Pretext tasks are thus also often referred to as *representation learning.*

Models pre-trained with SSL are often fine-tuned for their specific downstream tasks: this fine-tuning often involves true supervised learning (albeit with a fraction of the labeled data needed to train a model with supervised learning alone).

Though the discipline of SSL is diverse in both methodology and use cases, models trained with SSL use one (or both) of two machine learning techniques: *self-predictive learning* and *contrastive learning.*

### Self-predictive learning

Also known as *autoassociative self-supervised learning,* self-prediction methods train a model to predict part of an individual data sample, given information about its other parts. Models trained with these methods are typically generative models, rather than discriminative.

Yann LeCun has characterized self-supervised methods as a structured practice of “filling in the blanks.” Broadly speaking, he described the process of learning meaningful representations from the underlying structure of unlabeled data in simple terms: “pretend there is a part of the input you don’t know and predict that.”[](#_ftn1)<sup> 4</sup> For example:

- Predict *any part of the input* from *any other part*
- Predict the *future* from the *past*
- Predict the *masked* from the *visible*
- Predict any *occluded part* from all *available parts*

Self-supervised systems built upon these philosophies often employ certain model architectures and training techniques.

#### Autoencoders

An [autoencoder](https://www.ibm.com/topics/autoencoder) is a neural network trained to compress (or *encode*) input data, then reconstruct (or *decode*) the original input using that compressed representation. They are trained to minimize *reconstruction error*, using the original input itself as ground truth.

Though autoencoder architectures vary, they typically introduce some form of *bottleneck*: as data traverses the encoder network, each layer’s data capacity is progressive reduced. This forces the network to learn only the most important patterns hidden within the input data—called *latent variables*, or the *latent space—*so that the decoder network can accurately reconstruct the original input despite now having less information.

Modifications to this basic framework enable autoencoders to learn useful features and functions.

- *Denoising autoencoders* are given partially corrupted input data and trained to restore the original input by removing useless information (“noise”). This reduces [overfitting](https://www.ibm.com/topics/overfitting) and makes such models useful for tasks like restoring corrupted input images and audio data.
- Whereas most autoencoders encode *discrete* models of latent space, *Variational autoencoders* (VAEs) learn *continuous* models of latent space: by encoding latent representations of input data as a probability distribution, the decoder can generate new data by sampling a random vector from that distribution.

#### Autoregression

Autoregressive models use past behavior to predict future behavior. They work under the logic that any data with an innate sequential order—like language, audio or video—can be modeled with regression.

Autoregression algorithms model time-series data, using the value(s) of the previous time step(s) to predict the value of the following time step. Whereas in conventional regression algorithms, like those used for [linear regression](https://www.ibm.com/topics/linear-regression), independent variables are used to predict a target value (or dependent variable), in autoregression the independent and dependent variable are essentially one and the same: it’s called *auto*regression because regression is performed on the variable itself.

Autoregression is used prominently in causal language models like the GPT, LLaMa and Claude families of LLMs that excel at tasks like text generation and question answering. In pre-training, language models are provided the beginning of sample sentences drawn from unlabeled training data and tasked with predicting the next word, with the “actual” next word of the sample sentence serving as ground truth.

#### Masking

Another self-supervised learning method involves masking certain parts of an unlabeled data sample and tasking models with predicting or reconstructing the missing information. Loss functions use the original (pre-masking) input as ground truth. For example, *masked autoencoders* are like an inversion of denoising audioencoders: they learn to predict and restore missing information, rather than remove extraneous information.

Masking is also used in the training of masked language models: random words are omitted from sample sentences and models are trained to fill them in. Though masked language models like BERT (and the many models built off its architecture, like BART and RoBERTa) are often less adept at text generation than autoregressive models, they have the advantage of being *bidirectional*: they can predict not only the next word, but also previous words or words found later on in a sequence. This makes them well suited to tasks requiring strong contextual understanding, like translation, summarization and search.

#### Innate relationship prediction

*Innate relationship prediction* trains a model to maintain its understanding of a data sample after it is transformed in some way. For example, rotating an input image and tasking a model with predicting the change degree and direction of rotation relative to the original input.<sup>5</sup>

### Contrastive learning

Contrastive self-supervised learning methods provide models with multiple data samples and task them to predict the relationship between them. Models trained with these methods are typically discriminative models, rather than generative.

Contrastive models generally operate on *data-data* pairs for training, whereas autoassociative models operate on *data-label* pairs (in which the label is self-generated from the data). Using these data-data pairs, contrastive methods train models to distinguish between similar and dissimilar things.

These pairs are often created via *data augmentation*: applying different kinds of transformations or perturbations to unlabeled data to create new instances or augmented views. For example, common augmentation techniques for image data include rotation, random cropping, flipping, noising, filtering and colorizations. Data augmentation increases data variability and exposes the model to different perspectives, which helps ensure that the model learns to capture meaningful, dynamic semantic representations.

#### Instance discrimination

Instance discrimination-based models frame training as a series of binary classification tasks: using one data sample as the target (or “anchor”), other data samples are determined to be “positive” (matching) or “negative” (not matching).

In computer vision, such methods—like SimCLR or MoCo—typically begin with a batch of unlabeled raw images and apply a random combination of transformations to generate pairs (or sets) of augmented image samples. Each of these augmented images are then encoded into a vector representation, and a contrastive loss function is used to minimize the difference in vector representations between positive matches—pairs of augmented images derived from the same original image—and maximize the difference between negative matches.

Instance discrimination methods thus train models to learn representations of different categories that, thanks to random data augmentations, are robust to trivial variations (like the color, perspective or visible parts in a specific image). These representations thus generalize very well to downstream tasks.

#### Non-contrastive learning

Somewhat counterintuitively, “non-contrastive learning” refers to a method closely related to contrastive learning (rather than, as one might guess, a general catch-all for methods that are not contrastive learning). Models are trained using only positive pairs, learning to minimize the difference between their representations–hence, *non­–*contrastive.

Compared to contrastive learning, non-contrastive approaches are relatively simple: because they operate only on positive samples, they utilize smaller batch sizes for training epochs and don’t need a memory bank to store negative samples. This saves memory and computational cost during pre-training.

Non-contrastive models like Bootstrap Your Own Latent (BYOL)<sup>6</sup>[](https://www.ibm.com/topics/self-supervised-learning#_ftn1) and Barlow Twins<sup>7</sup>[](https://www.ibm.com/topics/self-supervised-learning#_ftn2) have achieved results competitive with those of contrastive and purely supervised results.

#### Multi-modal learning

Given data points of different types—modalities—contrastive methods can learn mapping between those modalities. For example, Contrastive Language-Image Pre-training (CLIP) jointly trains an image encoder and text encoder to predict which caption goes with which image, using millions of readily available unlabeled (*image, text*) pairings collected from the internet. After pre-training, natural language processing (NLP) is used to reference visual concepts learning in training (or even to describe new visual concepts), making CLIP-trained models highly useful for a wide array of transfer learning applications.

Contrastive learning has also been used to learn alignments between video and text,<sup>8</sup>[](https://www.ibm.com/topics/self-supervised-learning#_ftn3)[](https://www.ibm.com/topics/self-supervised-learning#_ftn3) video and audio,<sup>9</sup>[](https://www.ibm.com/topics/self-supervised-learning#_ftn4) and speech and text.<sup>10</sup>

## Self-supervised learning use cases

Self-supervised learning has been used to pre-train artificial intelligence models for a wide array of tasks and disciplines.

### Self-supervised learning for NLP

- [](#_ftn2)Within a year of its introduction in 2018, Google implemented the BERT masked language model as the NLP engine for ranked and featured snippets in Search.<sup>11</sup>[](#_ftn1) As of 2023, Google continues to use BERT architecture to power its real-world search applications.<sup>12</sup>[](#_ftn2)

- The LLaMa, GPT and Claude families of LLMs are autoregressive language models. GPT3 was trained primarily with self-supervised learning; InstructGPT, and the subsequent GPT-3.5 models used to launch ChatGPT, fine-tuned the pre-trained models using [reinforcement learning with human feedback (RLHF)](https://www.ibm.com/topics/rlhf).

- Autoregressive models are also used for audio-based NLP tasks like speech-to-text, as well as text-to-speech models like WaveNet.<sup>13</sup>[](#_ftn3) Facebook (Meta) uses *wav2vec* for speech recognition, using two deep convolutional neural networks stacked on top of each other to map raw audio input to a vector representation. In self-supervised pre-training, these vectors are used as inputs to self-prediction tasks.<sup>14</sup>[](#_ftn4)

### Self-supervised learning for computer vision

- Self-supervised learning is a rapidly growing subset of deep learning techniques used for medical imaging, for which expertly annotated images are relatively scarce. Across PubMed, Scopus and ArXiv, publications reference the use of SSL for medical image classification rose by over 1,000 percent from 2019 to 2021.<sup>15</sup>[](#_ftn1)

- SSL-based methods can often match or exceed the accuracy of models trained using fully supervised methods. For example, the original MoCo outperformed supervised models across seven object detection and [image segmentation](https://www.ibm.com/topics/image-segmentation) tasks on the PASCAL, VOC and COCO datasets.<sup>16</sup>[](#_ftn2) When fine-tuned using labeled data for only one percent of all training data, models pre-trained with SSL have achieved over 80 percent accuracy on the ImageNet dataset. This rivals the performance of benchmark supervised learning models like ResNet50.

- The ability to maintain successful object detection and image segmentation despite changes to an object’s orientation is essential to many robotics tasks. Self-supervised learning has been proposed as an effective way to train computer vision models to understand rotation without time-intensive collection of labeled data.<sup>17 18</sup>

- Masking has been used to train models to understand motion trajectory in video.<sup>19</sup>

### Self-supervised learning for image processing and image synthesis

- Denoising autoencoders are an essential component in the training of some state-of-the-art image synthesis models, like Stable Diffusion.<sup>20</sup>[](#_ftn1)

- Autoregressive modeling has been used for image synthesis in models like PixelRNN and PixelCNN. The success of PixelCNN led to it becoming the basis for WaveNet.

- Convolutional autoencoders are used for a variety of image processing tasks, like inpainting and the colorization of grayscale images.

- Variational autoencoders (VAEs) are an important tool in image synthesis. OpenAI’s original DALL-E model used a VAE to generate images. Both DALL-E 1 and DALL-E 2 use CLIP in the process of translating natural language prompts into visual information.<sup>21</sup>

## Footnotes

<sup>1</sup> ["Fathers of the Deep Learning Revolution Receive ACM A.M. Turing Award".](https://www.acm.org/media-center/2019/march/turing-award-2018) Association for Computing Machinery. March 27, 2019  
 <sup>2</sup> [Facebook](https://www.facebook.com/722677142/posts/10155934004262143/). Yann LeCun. April 30, 2019  
 <sup>3</sup> ["Self-taught learning: transfer learning from unlabeled data".](https://www.researchgate.net/publication/200038912_Self-taught_learning_Transfer_learning_from_unlabeled_data) Proceedings of the 24th International Conference on Machine Learning. June 20, 2007  
 <sup>4</sup> [Lecture: Energy based models and self-supervised learning.](https://www.youtube.com/watch?v=tVwV14YkbYs&t=2758s) YouTube. Uploaded in 2020  
 <sup>5</sup> ["Learning to see by moving".](https://arxiv.org/abs/1505.01596) arXiv. September 14, 2015  
 <sup>6</sup> ["Bootstrap Your Own Latent: A New Approach to Self-Supervised Learning".](https://arxiv.org/pdf/2006.07733.pdf) arXiv. September 10, 2020  
 <sup>7</sup> ["Barlow Twins: Self-Supervised Learning via Redundancy Reduction".](https://arxiv.org/pdf/2103.03230.pdf) arXiv. June 14, 2021  
 <sup>8</sup> ["VideoCLIP: Contrastive Pre-Training for Zero-shot Video-Text Understanding".](https://arxiv.org/abs/2109.14084) arXiv. October 1, 2021  
 <sup>9</sup> ["Active Contrasting Learning of Audio-Visual Video Representations".](https://openreview.net/pdf?id=OMizHuea_HB) Proceedings of the International Conference on Learning Representations. 2021  
 <sup>10</sup> ["Cross-modal Contrastive Learning for Speech Translation".](https://arxiv.org/abs/2205.02444) arXiv. May 5, 2022  
 <sup>11</sup> [**"Understanding searches better than ever before".**](https://blog.google/products/search/search-language-understanding-bert/) Google. October 25, 2019  
 <sup>12</sup> [******"End-to-End Query Term Weighting".******](https://research.google/pubs/end-to-end-query-term-weighting/) Google. 2023  
 <sup>13</sup> [********"WaveNet: A Generative Model for Raw Audio".********](https://arxiv.org/abs/1609.03499) arXiv. September 19, 2016  
 <sup>14</sup> [**********"Wave2vec: State-of-the-art speech recognition through self-supervision".**********](https://ai.meta.com/blog/wav2vec-state-of-the-art-speech-recognition-through-self-supervision/) Meta. September 19, 2019  
 <sup>15</sup> [**************"Self-supervised learning for medical image classification: a systematic review and implementation guidelines".**************](https://www.nature.com/articles/s41746-023-00811-0) Nature. April 26, 2023  
 <sup>16</sup> [******************"Momentum Contrast for Unsupervised Visual Representation Learning".******************](https://arxiv.org/abs/1911.05722) arXiv. November 13, 2019 (last revised March 23, 2020)  
 <sup>17</sup> [********************"Deep Projective Rotation Estimation through Relative Supervision".********************](https://arxiv.org/abs/2211.11182) arXiv. November 21, 2022  
 <sup>18</sup> [**********************"Orienting Novel 3D Objects Using Self-Supervised Learning of Rotation Transforms".**********************](https://arxiv.org/abs/2105.14246) arXiv. May 29, 2021  
 <sup>19</sup> [**************************"Masked Motion Encoding for Self-Supervised Video Representation Learning".**************************](https://openaccess.thecvf.com/content/CVPR2023/papers/Sun_Masked_Motion_Encoding_for_Self-Supervised_Video_Representation_Learning_CVPR_2023_paper.pdf) The Computer Vision Foundation. October 2022  
 <sup>20</sup> [******************************"High-Resolution Image Synthesis with Latent Diffusion Models".******************************](https://arxiv.org/abs/2112.10752) arXiv. December 20, 2021 (last revised April 13, 2022)  
 <sup>21</sup> [**********************************"DALL-E: Creating images from text".**********************************](https://openai.com/index/dall-e/) OpenAI. January 5, 2021
