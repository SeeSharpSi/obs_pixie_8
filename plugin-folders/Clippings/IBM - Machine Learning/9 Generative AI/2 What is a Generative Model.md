---
title: What is a generative model?
source: https://www.ibm.com/think/topics/generative-model
author:
- '[[Ivan Belcic]]'
published: 2024-11-05
created: 2026-08-31
description: "A generative model is a machine learning model designed to create new data that is similar to its training data."
---

## What is a generative model?

A generative model is a [machine learning](https://www.ibm.com/topics/machine-learning) model designed to create new data that is similar to its training data. Generative [artificial intelligence (AI)](https://www.ibm.com/topics/artificial-intelligence) models learn the patterns and distributions of the training data, then apply those understandings to generate novel content in response to new input data.

The act of content generation is what separates generative AI models from other types of AI. Generative models are advanced [neural networks](https://www.ibm.com/topics/neural-networks) that mimic the structure of the human brain and apply complex [machine learning algorithms](https://www.ibm.com/topics/machine-learning-algorithms) to process training data and manufacture novel outputs.

Generative AI models and their developers have chiefly driven the AI zeitgeist of the past several years. Generative models continue to receive the majority of AI-related news coverage and capture significant attention and investment.

### What is generative AI?

[Generative AI](https://www.ibm.com/topics/generative-ai) is a type of AI that uses sophisticated models to generate new content according to an input prompt. The generative model is the computer program that employs data and algorithms to facilitate the practice of generative AI. Generative AI use cases include [text summarization](https://www.ibm.com/topics/text-summarization), [text generation](https://www.ibm.com/topics/text-generation) and image generation, as well as 3D modeling and audio creation.

## How do generative models work?

Generative models work by identifying patterns and distributions in their training data and then applying those findings to the generation of new data based on user inputs. The training process teaches the model to recognize the joint probability distributions of features in the training dataset. Then, the model draws on what it has learned to create new data samples that are similar to its training data.

Generative models are typically trained with [unsupervised learning](https://www.ibm.com/topics/unsupervised-learning) techniques: when they are fed a mass of unlabeled data and sort through it by themselves. The models figure out the distribution of the data, which is how they cultivate the internal logic they then use to create new data.

During training, the model applies a [loss function](https://www.ibm.com/think/topics/loss-function?mhsrc=ibmsearch_a&mhq=loss%20function) to measure the gap between real-world outcomes and the model’s predictions. The goal of training is to minimize the loss function, bringing generated outputs as close to reality as possible.

Content generation is a probabilistic process. Generative models do not *know* things in the same way that humans do. Rather, a generative model uses complicated mathematical equations to predict the *most likely* output based on the rules it learned during training.

### Generative models versus other model types

Generative models attempt to generate new data of a certain class. Discriminative models separate items into known groups, while clustering models figure out how to group items in a dataset. Predictive models make estimations about future occurrences or states based on historical data.

- **Discriminative models** are used in [supervised learning](https://www.ibm.com/topics/supervised-learning) tasks in which the labels or categories of the data are known. Many discriminative models are classifiers that attempt to identify the relationships between features and labels and then assign class labels to new data based on the conditional probability of those labels.

For example, a discriminative model trained to differentiate between images of fish and birds can guess whether images are more likely to be fish or birds. Image recognition, a type of [classification in machine learning](https://www.ibm.com/think/topics/classification-machine-learning), is a common application for discriminative models.

While generative models and discriminative models have distinct differences, they often work together, such as in a [generative adversarial network (GAN)](https://developer.ibm.com/articles/generative-adversarial-networks-explained/).

- **Clustering models** are used in unsupervised learning tasks to group records within a data set into clusters. They can identify similar items and also learn what separates those items from other groups in the dataset.

Clustering models lack prior knowledge of the items in the dataset, including knowledge of how many groups there might be. A market researcher might use a clustering model to identify buyer personas within their target demographics.

- **Predictive models** process historical data to make predictions about future events using machine learning and statistical analysis. They are often used to help business leaders make data-driven decisions. Predictive models also power predictive text services, facial recognition software, fraud detection and supply chain management solutions.

- **Generative models** are given unlabeled data during training. They reverse-engineer the categorization criteria. Given a specific label, what are the features that cause a data point to receive that label? Generative models want to predict the features of a label and then use those features to generate new examples of that data.

A generative model trained to generate images of animals can attempt to create an image of a fish based on what it thinks makes a fish different from other animals. Image generation is a frequent use case for generative models.

## Types of generative models

Many types of generative models exist, each with its own defining architecture: the structure of the model that governs how it works. Deep generative models are a subtype of generative models that use multilayered [deep learning](https://www.ibm.com/topics/deep-learning) neural network structures—deep neural networks—to understand complicated, multifaceted relationships between data points in a dataset.

- [**Autoregressive models**](https://www.ibm.com/topics/autoregressive-model) predict the next data point in a sequence based on previous data instances. [Transformers](https://www.ibm.com/topics/transformer-model) excel at [natural language processing (NLP)](https://www.ibm.com/topics/natural-language-processing) tasks due to their enhanced ability to process context.

- [**Diffusion models**](https://www.ibm.com/think/topics/diffusion-models) create new data by gradually adding noise to a dataset, then figuring out how to remove the noise and yield novel output.

- **Generative adversarial networks (GANs)** pair a discriminative and generative model together in a competition, with the goal being for the generator to create output that fools the discriminator.

- [**Variational autoencoders (VAEs)**](https://www.ibm.com/think/topics/variational-autoencoder) compress input data with an encoder, then reverse the process with a decoder to create new similar data.

- **Flow-based models** learn the relationships between simple and complex distributions of data through reversible mathematical operations.

### Autoregressive models

Autoregressive models predict the next item in a sequence based on prior items. They assess the components in the sequence to determine the probabilistic correlation between them, then use that information to identify a new component that would likely follow.

Autoregression is a type of [linear regression](https://www.ibm.com/topics/linear-regression), which is a statistical technique that predicts the value of a variable based on the values of 1 or more variables. Autoregression narrows the focus to the target variable but considers its values over time. Autoregression also differs from [logistic regression](https://www.ibm.com/topics/logistic-regression) in that it predicts defined values while the latter yields a percentage chance of a specified event occurring.

Autoregressive models take the form of [recurrent neural networks (RNNs)](https://www.ibm.com/topics/recurrent-neural-networks) or transformer architectures.

#### Transformer models

First emerging in 2017[<sup>1</sup>](#footnotes1), transformer models quickly outshined RNNs, which until then were the leading form of autoregressive model. The transformer addressed several glaring RNN weaknesses. RNNs struggled to capture long-range dependencies—relationships between distance items in a sequence—and were compute-inefficient because they processed items sequentially, 1 by 1.

Transformers introduced 2 innovations that leapfrogged the architecture past RNNs and made them the de facto standard for [large language models (LLMs)](https://www.ibm.com/topics/large-language-models) in generative AI:

- **Parallel processing:** Transformers process all items in a sequence simultaneously, improving efficiency over sequential RNNs. Transformers can be trained in much less time, especially with the large-scale datasets required for top LLM performance.

- **Self-attention mechanisms:** Transformers can consider the relative importance of all items in a sequence when processing items. Self-attention enables transformers to capture key relationships between distant items in a series, enabling a contextual understanding that RNNs lacked. The ability to process context across large input sequences leads transformers to excel at NLP tasks such as text generation and language translation.

Of the 3 types of transformer models—encoders, decoders and encoder-decoders—the latter 2 contain autoregressive components. Decoders are the generative component and use autoregression to generate tokens informed by previously generated tokens.

#### Autoregressive model use cases

Autoregressive models, especially transformers, are in widespread use today. Many of the leading generative AI models are transformers, including OpenAI’s [GPT](https://www.ibm.com/think/topics/gpt) and [GPT-4o](https://www.ibm.com/think/topics/gpt-4o), Anthropic’s [Claude](https://www.ibm.com/think/topics/claude-ai), Meta’s [Llama](https://www.ibm.com/topics/llama-2), Google’s [Gemini](https://www.ibm.com/think/topics/google-gemini) and IBM’s [Granite](https://www.ibm.com/granite).

Autoregressive model use cases include:

- **Natural language processing:** Transformers can process complex natural language queries and respond conversationally with automated text generation, making them ideal for use as chatbots. For example, ChatGPT is OpenAI’s chatbot implementation of their GPT generative model. Other NLP applications include sentiment analysis, speech recognition, text-to-speech (TTS) applications and document summarization.

- **Coding support:** The same autoregressive capabilities that enable transformers to excel at text generation also allow them to debug code and generate code snippets.

- **Time-series forecasting:** Autoregression can be easily applied to [time-series forecasting](https://www.ibm.com/blog/time-series-forecasting/), in which a model predicts future values based on previous trends. Time-series forecasting is frequently applied to financial modeling, market predictions and weather forecasting.

- **Reinforcement learning:** Transformers have begun to see use in [reinforcement learning](https://www.ibm.com/topics/reinforcement-learning), a machine learning training technique that teaches autonomous decision-making. Transformers are also being applied to [classification](https://www.ibm.com/think/topics/classification-machine-learning) tasks.

### Diffusion models

Diffusion models gradually obfuscate or *diffuse* input data by adding noise, then refine the mess they created into new, similar data. They generate new data by learning to refine noise into data that is similar to their training datasets. Diffusion models work through a 3-stage process:

- **Step 1: Diffusion:** During training, the model gradually introduces noise to its input data until the data is no longer recognizable. The model adds a small amount of Gaussian noise to the data at each step in a mathematical process known as a Markov chain.

Imagine the diffusion process as a guitarist slowly turning up the gain knob on their amplifier until the sound of their guitar becomes a wall of pure static. This is how rock guitarists get a distorted sound in their music, albeit not typically to this extent.

- **Step 2: Learning:** The model traces the evolution of the now-destroyed data to understand how it was altered through the noising process. Diffusion models repeat this process at each stage of noising.

- **Step 3: Reverse diffusion:** By understanding how noise alters data, the diffusion model learns to reverse the noising process and reconstruct the input data. The goal of reverse diffusion is to travel backward through the Markov chain, removing Gaussian noise until only the pure data is left. The guitarist from Step 1 has received a stern talking-to from their bandmates and is turning the gain back down to an acceptable level.

Steps 1 and 2 are applied to train diffusion models. After training, diffusion models generate data by reverse-diffusing random noise to “find” the data requested by the user’s prompt.

#### Diffusion model use cases

Often used for image generation, diffusion models have other prominent use cases as well. Diffusion model applications include:

- **Image generation:** Diffusion models power mainstream image generation and image synthesis tools such as Midjourney, Stable Diffusion and OpenAI’s DALL-E 2. These models generate images in response to user prompts. Diffusion models can generate high-quality realistic images, including those of human faces.

The US Copyright Office ruled in 2023 that AI-generated images are not entitled to copyright protections. Meanwhile, numerous ongoing lawsuits[<sup>2</sup>](#footnotes2) will eventually determine whether AI-generated images are considered copyright violations.

- **Inpainting and outpainting:** Inpainting is the process of adding or removing content within an image, while outpainting expands an image beyond its original borders.

- **3D modeling:** Google’s DreamFusion and NVIDIA’s Magic3D are diffusion models that create 3D models from text inputs.

- **Market research:** Diffusion models show how things evolve over time, making them useful for understanding how consumers react to a product.

- **Anomaly detection:** Because they can learn how data changes over time, diffusion models can identify when data points do not fit established trends. [Anomaly detection](https://www.ibm.com/topics/anomaly-detection) applications include cybersecurity, fraud prevention and disease detection.

### Generative adversarial networks (GANs)

Introduced in 2014, generative adversarial networks (GANs) are among the earliest generative AI model types that pair 2 models together in a contest. A generative model creates outputs that a discriminator model must deem authentic or fake. The objective of the competition is for the generator to generate content that passes for authenticity when judged by the discriminator.

If the generator is an art forger, the discriminator is an art authenticator. An art dealer might obtain a forged work and attempt to sell it to a museum, but not before the work passes authentication. As the forger becomes better at imitating the great masters, the authenticator might struggle to detect subsequent forgeries. Before long, the museum is hosting an exhibition full of forged works.

The same training process that leads to realistic outputs can also result in mode collapse: when the generator leaves out some of its training data and limits itself to a narrow range of sample types. GANs, as well as diffusion models and transformers, require massive training data sets for effective performance.

Both networks in a GAN are often [convolutional neural networks (CNNs)](https://www.ibm.com/topics/convolutional-neural-networks), an early type of neural network notable for its strong performance in [computer vision](https://www.ibm.com/topics/computer-vision) tasks.

#### GAN use cases

GANs are used primarily in the field of computer vision and other graphics-related tasks.

- **Computer vision:** Computer vision is the use of machine learning to process information from images. Common computer vision tasks include object detection and classification, facial recognition, sign language translation and object tracking.

- **Image generation:** GANs can outperform diffusion models in the generation of realistic images. They also require less training time and are more compute-efficient, though diffusion models offer finer control, greater versatility and more stability. The Diffusion-GAN framework<sup>[3](#footnotes3) </sup>trains a GAN with diffusion to maximize the benefits of both model types.

- **Anomaly detection:** When trained to generate normal datasets, GANs can be applied to anomaly detection tasks. The GAN creates a synthetic dataset modeled on the real-world data, and by comparing the two, anomalies in the latter stand out. The discriminator can also detect anomalies by declaring certain data points more likely to be fake.

- **Data augmentation:** [Data augmentation](https://www.ibm.com/topics/data-augmentation)—the use of preexisting data to create more data samples—can boost computer vision performance even further with CNNs. This process differs from [synthetic data](https://www.ibm.com/topics/synthetic-data) in that it expands on real data, as opposed to generating something from scratch.

![An example of data augmentation using a photograph of a cat](https://assets.ibm.com/is/image/ibm/data-augmentation-image-augment?ts=1763388120140&dpr=off)   An example of data augmentation

### Variational auto encoders (VAEs)

Variational autoencoders (VAEs) compress input data, then expand or decode that compression to generate new like data. VAEs learn the distribution of a training dataset and apply those expectations when generating new data from encoded samples. Like all [autoencoders](https://www.ibm.com/topics/autoencoder), VAEs comprise 2 components: an encoder and a decoder.

The encoder’s job is to learn the latent variables in a data set. Latent variables are not directly observable but play a significant role in data distribution. *Latent space* is the collective name for all the latent variables in a dataset. The encoder models the latent space in a way that captures the information needed to accurately reconstruct the data. All other variables are omitted.

The decoder takes the compressed representation of the data, known as a bottleneck, and extrapolates it back to the data’s original form. An effective decoder produces output similar to the original pre-compressed data.

#### VAE use cases

VAEs struggle in image generation tasks as compared to diffusion models and GANs, but excel in other areas.

- **Image generation:** VAEs see use in image generation, though with mainstream image generation applications, diffusion models have widely replaced them. Compared to other image generators, VAEs tend to produce blurrier images due to their “averaging” of the latent space.

- **Genomics:** VAEs aid geneticists in calculating breeding values—the projected value an animal will provide with its offspring—as well as assigning disease risk scores.

- **Anomaly detection:** VAEs are cheaper and easier to train than both GANs and diffusers, making them an attractive choice for anomaly detection tasks. The re-created data is compared to the original data to isolate instances that deviate from the projected distribution.

- **Data imputation:** VAEs can generate new data to replace missing data and restore corrupted files. Examples include clearing up audio files and denoising videos as well as medical imaging. While VAEs tend to generate blurry images from scratch, they can restore preexisting blurry images by denoising the image.

- **Semisupervised learning:** VAEs help train classifiers by capturing data distributions in datasets with incomplete labeling. VAEs can also perform data augmentation to generate extra training samples for the classifier.

### Flow-based models

Flow-based models learn data distribution through a series of invertible or reversible mathematical transformations. Data can losslessly progress through this pipeline, known as a *normalizing flow*, in either direction. While VAEs and GANs estimate data distributions, flow-based models explicitly learn the probability density function for the dataset.

In a given dataset, the probability density function describes how the data is distributed. Normalizing flows progress from simple distributions to complex ones until the target variable’s probability density function is identified.

Flow-based models can generate new data samples that maintain the same statistical properties of the initial dataset. Like all generative modeling, the process is based on the concept of drawing samples from training data and applying complex statistical mathematics to produce similar, novel outcomes.

#### Flow-based model use cases

Flow-based models shine in cases where having an accurate assessment of data distribution is paramount.

- **Image generation:** Flow-based models generate images by running randomly sampled noise through normalization flows to produce a clean image. PixelCNN is a notable 2016 image generation model that applies autoregression to the sequence of transformations, modeling images pixel by pixel.

- **Accurate density estimation:** Density estimation is the challenge of identifying the probability density function of a dataset based on observable data. While flow-based models can accurately represent complex data distributions, they struggle to capture long-range dependencies when compared to transformers.

- **Molecular graph generation:** Flow-based models have found use in molecular graph generation, in which new molecular structures are modeled as graphs by generative AI models. Molecular graph generation is an important tool in aiding scientists and engineers in the discovery of new drugs and materials.

## Generative models and hallucinations

The same processes that often lead to impressive results are also what cause generative models to [hallucinate](https://www.ibm.com/topics/ai-hallucinations): when they output incorrect or misleading information. Hallucinations or confabulations happen when models perceive patterns in their training data sets that do not exist in the real world.

For example, prompting [ChatGPT-4o](https://www.ibm.com/think/topics/gpt-4o) mini with the question “In which episode of *Seinfeld* does Kramer go to Bangladesh?” returned this answer:

*Kramer travels to Bangladesh in the episode titled “The Little Jerry,” which is the 145th episode of* Seinfeld*. It is the 145th* [sic] *episode of the show, and it originally aired during Season 8. In this episode, Kramer becomes involved in a scheme to import a toy from Bangladesh.*

While *The Little Jerry* is the 145th episode of *Seinfeld* and aired during Season 8, it features Kramer buying and training a rooster—the eponymous Little Jerry. Prompting the [chatbot](https://www.ibm.com/topics/chatbots) again with the same question returned a second, different hallucination:

*Kramer goes to Bangladesh in the episode titled "The Maldives," which is the 18th episode of Season 9. In this episode, he tries to start a new life after his trip, and the storyline revolves around the idea of him becoming a "Bangladeshi" fisherman.*

In reality, episode 18 of season 9 of *Seinfeld* is *The Frogger*, and in it, Kramer only goes so far as the police station. There is no episode of *Seinfeld* called *The Maldives*, and at no point during the show’s entire run does Kramer go to Bangladesh.

Just as autoregressive models such as [GPT](https://www.ibm.com/think/topics/gpt) are known to hallucinate with made-up facts, other types of models can hallucinate in their own respective ways. Diffusion models used for image generation sometimes depict real-world objects in ways that do not match reality.

### How to mitigate hallucinations

While it’s not yet possible to entirely remove the possibility for generative AI models to hallucinate, best practices for hallucination mitigation include:

- **Clear prompting:** The more explicit the user prompt, the more focused the AI’s answer can be. Give the AI space within the prompt to answer with detail.

- **Focused direction:** Giving an AI a clear role and instructing it to provide truthful, verifiable information can help ensure its answers better reflect reality.

- **High-quality data:** The more current and relevant an AI model’s training data, the lower the chance that its answers will be biased.

- **Human verification:** AI-generated results should not be used without being first verified by knowledgeable humans.

- **RAG and fine-tuning:** Using RAG to augment an AI with credible data and fine-tuning models to become more domain-specific are both effective in reducing hallucinations.

## Footnotes

1. [Attention Is All You Need](https://arxiv.org/abs/1706.03762), Vaswani et al, 2 Aug 2023

2. [Artists Score Major Win in Copyright Case Against AI Art Generators](https://www.hollywoodreporter.com/business/business-news/artists-score-major-win-copyright-case-against-ai-art-generators-1235973601/), Winston Cho, The Hollywood Reporter, 13 August 2024

3. [Diffusion-GAN: Training GANs with Diffusion](https://arxiv.org/abs/2206.02262), Wang et al, 25 Aug 2023
