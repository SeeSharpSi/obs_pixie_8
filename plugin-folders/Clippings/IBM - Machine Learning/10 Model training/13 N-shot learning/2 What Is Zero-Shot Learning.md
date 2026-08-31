---
title: What is zero-shot learning?
source: https://www.ibm.com/think/topics/zero-shot-learning
author:
- '[[Dave Bergmann]]'
published: 2024-12-06
created: 2026-08-31
description: "Zero-shot learning is a machine learning problem in which an AI model is trained to recognize and categorize objects or concepts that it has never seen before."
---

## What is zero-shot learning?

Zero-shot learning (ZSL) is a [machine learning](https://www.ibm.com/topics/machine-learning) scenario in which an [AI model](https://www.ibm.com/topics/ai-model) is trained to recognize and categorize objects or concepts without having seen any examples of those categories or concepts beforehand.

Most state-of-the-art [deep learning](https://www.ibm.com/topics/deep-learning) models for [classification](https://www.ibm.com/think/topics/classification-machine-learning) or [regression](https://www.ibm.com/think/topics/logistic-regression) are trained through [supervised learning](https://www.ibm.com/topics/supervised-learning), which requires many labeled examples of relevant data classes. Models “learn” by making predictions on a labeled training dataset; data labels provide both the range of possible answers and the correct answers (or *ground truth*) for each training example. “Learning,” here, means adjusting model weights to minimize the difference between the model’s predictions and that ground truth. This process requires enough labeled samples for many rounds of training and updates.

While powerful, supervised learning is impractical in some real-world scenarios. Annotating large amounts of data samples is costly and time-consuming, and in cases like rare diseases and newly discovered species, examples may be scarce or non-existent. Consider image recognition tasks: according to one study, humans can recognize approximately 30,000 individually distinguishable object categories.<sup>1</sup> It’s not feasible, in terms of time, cost and computational resources, for artificial intelligence models to remotely approach human capabilities if they must be explicitly trained on labeled data for each class.

The need for machine learning models to be able to generalize quickly to a large number of semantic categories with minimal training overhead has given rise to *n-shot learning*: a subset of machine learning that also includes [*few-shot learning*](https://ibm.com/topics/few-shot-learning) (FSL) and *one-shot learning*. Few-shot learning typically uses *transfer learning* and *meta learning*-based methods to train models to quickly recognize new classes with only a few labeled training examples—or, in one-shot learning, a single labeled example.

**Zero-shot learning**, **like all n-shot learning, refers not to any specific algorithm or [neural network](https://www.ibm.com/topics/neural-networks) architecture, but to the nature of the learning problem itself**: in ZSL, the model is not trained on any labeled examples of the unseen classes it is asked to make predictions on post-training.

This problem setup doesn’t account for whether that class was present (albeit unlabeled) in training data. For example, some [large language models (LLMs)](https://www.ibm.com/topics/large-language-models) are well-suited for ZSL tasks, as they are pre-trained through [self-supervised learning](https://ibm.com/topics/self-supervised-learning) on a massive corpus of text that may contain incidental references to or knowledge about unseen data classes. Without labeled examples to draw upon, ZSL methods all rely on the use of such *auxiliary knowledge* to make predictions.

Given its versatility and wide range of use cases, zero-shot learning has become an increasingly notable area of research in data science, particularly in the fields of [computer vision](https://www.ibm.com/topics/computer-vision) and [natural language processing (NLP)](https://www.ibm.com/topics/natural-language-processing).

### Generalized zero-shot learning (GZSL)

In a conventional ZSL setting, the model is tested on a dataset containing samples from unseen classes of data. While useful for developing and validating zero-shot methodologies, it doesn’t reflect most common real-world conditions: *generalized zero-shot learning* (GZSL) refers to the specific zero-shot learning problem in which the data point(s) the model is tasked with classifying might belong to either unseen classes *or seen classes*: classes the model has already “learned” from labeled examples.

GZSL must overcome an additional challenge: the tendency for classifiers to bias predictions towards classes it has seen in training over unseen classes it has not yet been exposed to. As such, GZSL often requires additional techniques to mitigate that bias.

## How does zero-shot learning work?

In the absence of any labeled examples of the categories the model is being trained to learn, zero-shot learning problems make use of *auxiliary information*: textual descriptions, attributes, embedded representations or other semantic information relevant to the task at hand.

Rather than directly modeling the decision boundaries between classes, zero-shot learning techniques typically output a probability vector representing the likelihood that a given input belongs to certain classes. GZSL methods may add a preliminary discriminator that first determines whether the sample belongs to a seen class or a new class, then proceed accordingly.

### Understanding labels

In supervised learning—as well as in few-shot learning (FSL)—the model learns to recognize different classes by directly observing one or more labeled examples of each class. Without these explicit annotations to guide them, zero-shot learning requires a more fundamental *understanding of the label’s meaning*.

For a simple analogy, imagine a child wants to learn what a bird looks like. In a process resembling supervised learning or FSL, the child learns by looking at images labeled “bird” in a book of animal pictures. Moving forward, she’ll recognize a bird because it resembles the bird images she’s already seen. But in a ZSL scenario, no such labeled examples are available. Instead, the child might read an encyclopedia entry on birds and learn that they are small- or medium-sized animals with feathers, beaks and wings that can fly through the air. She’ll then be able to recognize a bird in the real world, even though she has never seen one before, because she has learned the *concept* of a bird.

As mentioned earlier, LLMs have demonstrated natural potential for ZSL, derived from their ability to fundamentally understand the meaning of the words used to name data classes.

### Transfer learning

To minimize the time and resources needed for training, as well the amount of auxiliary information needed to identify unseen classes, ZSL often leverages *transfer learning*—the repurposing of a trained model for a new task—instead of training models from scratch.

Transfer learning is used prominently in ZSL methods that represent classes and samples as [semantic embeddings](https://www.ibm.com/topics/embedding). For example, a model performing zero-shot text classification might use a transformer-based model like BERT, already pre-trained on a massive corpus of language data, to convert words into vector embeddings. Likewise, a zero-shot image classification model might repurpose a pre-trained [convolutional neural network (CNN)](https://www.ibm.com/topics/convolutional-neural-networks) like a ResNet or U-Net, as it will already have learned filter weights conducive to identifying important image features that could inform classification.

Transfer learning is particularly important for GSZL, in which the model’s knowledge of seen classes can be used as auxiliary information about unseen classes.For example, imagine an object detection model has already learned to recognize grizzly bears. Instead of training it to also recognize polar bears by providing it with labeled examples of polar bears, it can be trained to understand that polar bears look like *grizzly bears with white fur*.

This process of transferring learned knowledge to new tasks and different classes is also referred to as *domain adaptation*.

## Attribute-based methods

Attribute-based zero-shot learning methods use logic similar to that of conventional supervised learning. Rather than directly training a classifier on labeled examples of each data class, classifiers are trained on labeled features of certain data classes, like color, shape or other key characteristics.

Though the target classes are not directly seen in training, the label of an unseen class can be inferred if its attributes resemble attribute classes present in the training data.

Once the classifier has learned all relevant features, it can utilize semantic descriptions of different classes. This approach is particularly useful when labeled examples of a target class are unavailable, but labeled examples of its characteristic features are relatively abundant. For example, a model can learn “*stripes*” from images of tigers and zebras; it can learn “*yellow*” from images of canaries, and “*flying insect*” from images of flies. The model can now perform zero-shot classification of bees, despite the absence of bee images in the training set, because it can understand them as a combination of learned features: “*yellow, striped flying insects.*”

While versatile and useful in the right circumstances, attribute-based ZSL methods have important drawbacks:

- They rely on the key assumption that every class can be described with a single vector of attributes, which is not always the case. Mall, Hariharan and Bala cite the examples of the American Goldfinch—whose color and plumage patterns vary with gender, age and breeding status—and of outdoor badminton courts, which vary widely in terms of color, surface and presence (or absence) of formal lines.<sup>2  

 </sup>
- Annotating examples of individual attributes can potentially be as costly and time-consuming as annotating examples of a given class.
- Attribute-based methods cannot generalize to classes whose attributes are unknown or not present in available samples.

## Embedding-based methods

Many ZSL methods represent both classes and samples as [semantic embeddings](https://www.ibm.com/topics/embedding): vector representations that can be used to reflect the features or meaning of (and relationship between) different data points. Classification is then determined by measuring similarity between the semantic embedding of a given sample and the embeddings of the different classes it might be categorized into.

Once data points have been represented as embeddings, classification is determined using principles similar to those of [K-nearest neighbors](https://www.ibm.com/topics/knn) algorithms: some metric of distance, like [cosine similarity](https://community.ibm.com/community/user/ai-datascience/blogs/moloy-de1/2020/06/18/points-to-ponder), Euclidian distance or [Wasserstein distance](https://research.ibm.com/publications/on-efficient-multilevel-clustering-via-wasserstein-distances), is used to measure the proximity of the embedding of the input data to the embeddings for each potential class. The closer (or more similar) the embedding of that data sample is to the embedding for a given class, the more likely it belongs to that class.

These embeddings can be generated in a number of ways. For example:

- Pre-trained models and algorithms like BERT, word2vec or GloVe (Global Vectors) can readily output vector embeddings for words (like the names of class labels).
- Likewise, the encoder networks of pre-trained CNNs like ResNet (or transformer-based image encoders like ViT) can do the same for images.
- [Autoencoders](https://www.ibm.com/topics/autoencoder) can learn latent representations—compressed, lower-dimensional encodings that isolate the most distinguishing variables of a given data input—of samples or classes.
- In lieu of transfer learning, a variety of neural network architectures can be trained from scratch on relevant training data—like samples of relevant data classes for which labeled examples are available—to output effective embeddings.

### Joint embedding space

Because embedding-based methods typically process auxiliary information and vector space embeddings of different forms (or *modalities*) of data—like word embeddings that describe a class label and the image embedding of a photograph that might belong to that class—they require a way to facilitate comparison between embeddings of different data types.

To be compared, vector embeddings of different types and sizes must be normalized and projected to a shared high-dimensional semantic space, referred to as the *joint embedding space*, where they can be compared in an apples-to-apples setting. Abstractly speaking, this works similarly to the concept of finding the least common denominator to compare unlike fractions. A strong, correlative mapping between different embedding sources is essential to a model’s generalization performance.<sup>3</sup>

Some zero-shot learning models also use [*contrastive learning*](https://research.ibm.com/publications/which-features-are-learnt-by-contrastive-learning-on-the-role-of-simplicity-bias-in-class-collapse-and-feature-suppression) to better align semantic embeddings from different models or algorithms: using pairs of semantic embeddings, contrastive learning trains models to minimize the distance between “positive” pairs (like the embedding of an image of a dog and that of the word “dog”) and maximize the distance between “negative” (non-matching) pairs.

### Joint end-to-end training

One effective way to ensure alignment between embeddings from different models is to jointly train those models side by side. For example, OpenAI’s Contrastive Language-Image Pre-training (CLIP) model was trained on an enormous unlabeled dataset of over 400M image-caption pairs taken from the internet.<sup>4</sup>

These pairings were used to jointly train an image encoder and text encoder from scratch, using contrastive loss to maximize the cosine similarity between image embeddings and the embeddings for their corresponding captions. This yielded a natural ability for zero-shot classification: with no fine-tuning, CLIP demonstrated strong classification performance on 27 different image classification datasets.

## Generative-based methods

[Generative AI](https://www.ibm.com/think/insights/generative-ai-benefits) offers an alternate solution to the zero-shot learning problem: using auxiliary information to *generate* sample data, without requiring labeled examples to do so.

Generative-based methods can leverage the semantic representations of unseen classes to generate samples that, once labeled, can be used to convert the learning problem to standard supervised learning. Though unlabeled samples (or representations of closely related seen classes) can aid in the synthesis of samples, in a zero-shot setting this process often relies primarily on semantic descriptions.

LLMs can reduce the labor needed to produce high quality descriptions: in the release paper for its DALL-E 3 text-to-image generation model, OpenAI noted that synthetic captions even improved model performance relative to “ground truth” captions.<sup>5</sup>

### Variational autoencoders

[Variational autoencoders (VAEs)](https://www.ibm.com/topics/autoencoder#Variational+autoencoders) are [self-supervised](https://www.ibm.com/topics/self-supervised-learning) generative models that learn latent representations of training data as a parameterized distribution of latent variables. In other words, they learn to encode a data class not as a static semantic embedding, but as a probability distribution in latent space. The decoder can then be used to generate a random sample from that latent space. Conditional VAEs (CVAEs) can constrain the properties of synthesized samples by maximizing the probability of chosen variables.

### Generative adversarial networks (GANS)

[Generative adversarial networks (GANs](https://www.ibm.com/think/topics/generative-adversarial-networks)[)](https://www.ibm.com/think/topics/generative-adversarial-networks) consist of two neural networks, jointly trained in an adversarial zero-sum game: a generator that uses semantic attributes and Gaussian noise to synthesize samples and a discriminator that determines whether samples are real or “fake” (that is, synthesized by the generator). Feedback from the discriminator is used to train the generator until the discriminator can no longer distinguish between real and fake samples. Since the original GAN paper in 2014, a number of modifications have been developed to refine and stabilize this process.

### VAEGANs

Both VAEs and GANs suffer from drawbacks:

- VAEs are stable, but tend to generate blurry images due to the nature of how samples are reconstructed from latent space.
- GANs learn to generate high-quality images, but are prone to destabilization because they must converge two separate and distinct training processes.

Though a number of a number of modifications have been developed to refine and stabilize both processes, combining the two model architectures has yielded promising results in a zero-shot setting.<sup>6</sup>

### Large language models (LLMs)

LLMs can also be used to synthesize labeled samples: for example, using an autoregressive model like [Llama 2](https://www.ibm.com/topics/llama-2) to generate samples that can be used to train a bidirectional language model like Sentence-BERT for text classification tasks.

## Footnotes

<sup>1</sup> [“Recognition-by-components: A theory of human image understanding”.](https://typeset.io/papers/recognition-by-components-a-theory-of-human-image-2d038hmxno) *Psychological Review* vol. 94 (pp. 115–147). 1987.  
 <sup>2</sup> [“Zero-shot Learning Using Multimodal Descriptions”.](https://openaccess.thecvf.com/content/CVPR2022W/L3D-IVU/html/Mall_Zero-Shot_Learning_Using_Multimodal_Descriptions_CVPRW_2022_paper.html) Proceedings of the IEEE/CVF Conference on Computer Vision and Pattern Recognition (CVPR) Workshops. 2022.  
 <sup>3</sup> [“Data-Efficient Language-Supervised Zero-Shot Learning with Self-Distillation”. arXiv.](https://arxiv.org/abs/2104.08945) April 18, 2021.  
 <sup>4</sup> [“CLIP: Connecting text and images”.](https://openai.com/index/clip/) OpenAI. January 5, 2021.  
 <sup>5</sup> [“Improving Image Generation with Better Captions”.](https://cdn.openai.com/papers/dall-e-3.pdf) OpenAI. 2023.  
 <sup>6</sup> [“Zero-VAE-GAN: Generating Unseen Features for Generalized and Transductive Zero-Shot Learning”.](https://pubmed.ncbi.nlm.nih.gov/31940538/) PubMed. January 13, 2023.
