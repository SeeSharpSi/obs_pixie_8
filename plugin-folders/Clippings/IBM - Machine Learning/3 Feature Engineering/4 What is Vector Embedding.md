---
title: "What is Vector Embedding?"
source: "https://www.ibm.com/think/topics/vector-embedding#1003835712"
author:
  - "[[Dave Bergmann]]"
  - "[[Cole Stryker]]"
published: 2021-03-10
created: 2026-05-21
description: "Vector embeddings are numerical representations of data points, such as words or images, as an array of numbers that ML models can process."
tags:
  - "clippings"
---
## Authors

Senior Staff Writer, AI Models

IBM Think

Staff Editor, AI Models

IBM Think

Vector embeddings are numerical representations of data points that express different types of data, including nonmathematical data such as words or images, as an array of numbers that [machine learning](https://www.ibm.com/topics/machine-learning) (ML) models can process.

[Artificial intelligence (AI) models](https://www.ibm.com/topics/ai-model), from simple [linear regression](https://www.ibm.com/topics/linear-regression) algorithms to the intricate [neural networks](https://www.ibm.com/topics/neural-networks) used in [deep learning](https://www.ibm.com/topics/deep-learning), operate through mathematical logic. Any data that an AI model operates on, including unstructured data such as text, audio or images, must be expressed numerically. Vector embedding is a way to convert an unstructured data point into an array of numbers that still expresses that data’s original meaning.

[Training models](https://www.ibm.com/think/topics/model-training) to output vector representations of data points that correspond meaningfully to their real-world features enable us to make useful assumptions about how vector embeddings relate to one another. Intuitively, the more similar two real-world data points, the more similar their respective vector embeddings should be. Features or qualities shared by two data points should be reflected in both of their vector embeddings. Dissimilar data points should have dissimilar vector embeddings.

Armed with such logical assumptions, vector embeddings can be used as inputs to models that perform useful real-world tasks through mathematical operations that compare, transform, combine, sort or otherwise manipulate those numerical representations.

Expressing data points as vectors also enables the interoperability of different types of data, acting as a *lingua franca* of sorts between different data formats by representing them in the same embedding space. For example, smartphone voice assistants “translate” the user’s audio inputs into vector embeddings, and in turn use those vector embeddings for [natural language processing (NLP)](https://www.ibm.com/topics/natural-language-processing) of that input.

Vector embeddings thus underpin nearly all modern machine learning, powering models used in the fields of NLP and computer vision, and serving as the fundamental building blocks of generative AI.

## What is a vector?

Vectors belong to the larger category of *tensors*. In machine learning (ML), “tensor” is used as a generic term for an array of numbers (or an array of arrays of numbers) in *n* -dimensional space, functioning like a mathematical bookkeeping device for data.

It’s useful to note that certain words are used differently in an ML context than in everyday language or other mathematical settings. “Vector” itself, for example, has a more specific connotation in physics—where it usually refers to a quantity with both magnitude and direction—than it does in ML.

Likewise, the word “dimension” has different implications in ML, depending on its context. When describing a tensor, it refers to how many arrays that tensor contains. When describing a vector, it refers to how many components—individual numbers—that vector contains. Analogous terms such as “order” or “degree” can help reduce ambiguity.

- A *scalar* is a zero-dimensional tensor, containing a single number. For example, a system modeling weather data might represent a single day’s high temperature (in Celsius) in scalar form as*
	33
	*.
- *A vector* is a one-dimensional (or *first-degree* or *first-order*) tensor, containing multiple scalars of the same type of data. For example, the weather model might represent the low, mean and high temperatures of that single day in vector form as
	(*25, 30, 33*)
	. Each scalar component is a *feature* —that is, a dimension—of the vector, corresponding to a feature of that day’s weather.
- A *tuple* is a first-order tensor containing scalars of more than one type of data. For example, a person’s name, age and height (in inches) might be represented in tuple form as
	(*Jane, Smith, 31, 65*)
	.
- A *matrix* is a two-dimensional (or *second rank* or *second-order*) tensor, containing multiple vectors of the same type of data. It can be intuitively visualized as a two-dimensional grid of scalars in which each row or column is a vector. For example, that weather model might represent the entire month of June as a 3x30 matrix, in which each row is a feature vector describing an individual day’s low, mean and high temperatures.
- Tensors with three or more dimensions, like the [3-dimensional tensors used to represent color images](https://developer.ibm.com/articles/introduction-to-convolutional-neural-networks/) in computer vision algorithms, are referred to as *multidimensional arrays* or *N* -dimensional tensors.

Various straightforward transformations can also be applied to matrices or other *n* -dimensional tensors to represent the data they contain in vector form. For example, a 4x4 matrix can be flattened into a 16-dimensional vector; a 3-dimensional tensor of a 4x4 pixel image can be flattened into a 48-dimensional vector. embeddings predominately take the form of vectors in modern ML.

### Vectors versus embeddings:

Though the terms are often used interchangeably in ML, “vectors” and “embeddings” are not necessarily the same thing.

An *embedding* is any numerical representation of data that captures its relevant qualities in a way that ML algorithms can process. The data is *embedded* in *n* -dimensional space.

In theory, data doesn’t *have* to be embedded as a vector, specifically. For example, some types of data can be embedded in tuple form.<sup>1</sup> But in practice, embeddings predominately take the form of vectors in modern ML.

Conversely, vectors in other contexts, such as physics, aren’t necessarily embeddings. But in ML, vectors are usually embeddings and embeddings are usually vectors.

Think Keynotes

### Win the enterprise AI race

Join Arvind Krishna to see how IBM is enabling AI-first enterprises through hybrid cloud and emerging quantum capabilities.

## How does vector embedding work?

A vector embedding transforms a data point, such as a word, sentence or image, into an *n* -dimensional array of numbers representing that data point’s characteristics—its *features*. This is achieved by training an *embedding model* on a large data set relevant to the task at hand or by using a pretrained model.

To understand vector embeddings requires the explanation of a few key concepts:

- **How vector embeddings represent data.  
	  
	**
- **How vector embeddings can be compared.  
	  
	**
- **How models can be used to generate vector embeddings.  
	**

### How vector embeddings represent data

**In machine learning, the “dimensions” of data do not refer to the familiar and intuitive dimensions of physical space. In the vector space, each dimension corresponds to an individual *feature* of data**, in the same way that length, width and depth are each *features* of an object in physical space.

Vector embeddings typically deal with *high-dimensional data* because, in practice, most nonnumerical information is high-dimensional. For example, even a small, simple 28x28-pixel black-and-white image of a handwritten digit from the [MNIST data set](https://dataplatform.cloud.ibm.com/exchange/public/entry/view/e5ec6df59cd736a6b6b091062e3715a2?context=cpdaas) can be represented as a 784-dimensional vector in which each dimension corresponds to an individual pixel whose grayscale value ranges from 0 (for black) to 1 (for white).

However, not all of those dimensions of the data will contain useful information**.** In our MNIST example, the actual digit itself represents only a small fraction of the image: the rest is a blank background, or “noise.” It would thus be more accurate to say that we’re “embedding a representation of the image in 784-dimension space” than to say we’re representing 784 different features of the image.

Efficient vector embeddings of high-dimensional data thus often entail some degree of [*dimensionality reduction*](https://www.ibm.com/topics/dimensionality-reduction): the compression of high-dimensional data down to a [lower-dimensional space that omits irrelevant or redundant information](https://www.ibm.com/think/topics/latent-space).

Dimensionality reduction increases model speed and efficiency, albeit with a potential tradeoff in accuracy or precision, because smaller vectors require less computational resources for mathematical operations. It can also help decrease the risk of [overfitting](https://www.ibm.com/topics/overfitting) the training data. Different dimensionality reduction methods, such as [autoencoders](https://www.ibm.com/topics/autoencoder), [convolutions](https://developer.ibm.com/articles/introduction-to-convolutional-neural-networks/), [principal component analysis](https://www.ibm.com/topics/principal-component-analysis) and T-distributed stochastic neighbor embedding (t-SNE), are best suited to different data types and tasks.

Whereas the dimensions of image vector data are relatively objective and intuitive, determining the relevant features of certain data modalities—such as the semantic meanings and contextual relationships of language—is more abstract or subjective. In such cases, the specific features represented by the dimensions of vector embeddings can be established through manual [feature engineering](https://www.ibm.com/topics/feature-engineering) or, more commonly in the era of deep learning, determined implicitly through the process of training a model to make accurate predictions.

### How to compare vector embeddings

The core logic of vector embeddings is that *n* -dimensional embeddings of similar data points should be grouped closely together in *n* -dimensional space. However, embeddings can have dozens, hundreds or even thousands of dimensions. This goes well beyond the 2- or 3-dimensional spaces in which our minds can intuitively visualize things being "close" to one another.

Instead, one of multiple mathematical measures can be used to infer the relative similarity or proximity of different vector embeddings. The best measure of similarity for a specific situation depends largely on the nature of the data and what the comparisons are being used for.

- **Euclidian distance** measures the average straight-line distance between the corresponding points of different vectors. The difference between two *n* -dimensional vectors ***a*** and ***b*** is calculated by first adding the squares of the differences between each of their corresponding components—so,
	(*a <sub>1</sub> –b <sub>1</sub>) <sup>2</sup>* \+ (*a <sub>2</sub> –b <sub>2</sub>*) <sup>2</sup> +... (*a <sub>n</sub> –b <sub>n</sub>) <sup>2</sup>*
	—and then taking the square root of that sum. Because Euclidian distance is sensitive to magnitude, it’s useful for data that reflects things like size or counts. Values range from 0 (for identical vectors) to ∞.
- **Cosine distance**, also called *cosine similarity*, is a normalized measure of the cosine of the angle between two vectors. Cosine distance ranges from -1 to 1, in which 1 represents identical vectors, 0 represents *orthogonal* (or unrelated) vectors, and -1 represents fully opposite vectors. Cosine similarity is used widely in NLP tasks because it naturally normalizes vector magnitudes, which makes it less sensitive to the relative frequency of words in training data than Euclidian distance.
- **Dot product** is, algebraically speaking, the sum of the product of the corresponding components of each vector. Geometrically speaking, it’s a nonnormalized version of cosine distance that also reflects frequency or magnitude.

 ![Similarity metrics for vector embeddings](https://assets.ibm.com/is/image/ibm/similarity-metrics-for-vector-search-i-zilliz:16x9?fmt=png-alpha&dpr=on%2C2.2222222222222223&wid=1584&hei=891)Mathematical formulas and visualization of common vector similarity metrics.

### Embedding models

Stand-alone embedding models might be pretrained offerings or trained from scratch on specific tasks or training data. Each form of data typically benefits from a specific neural network architecture, but the use of a specific algorithm for a specific task is often a "best practice" rather than an explicit rule.

In some scenarios, the embedding process is an integrated part of a larger neural network. For example, in the encoder-decoder [convolutional neural networks (CNNs)](https://www.ibm.com/topics/convolutional-neural-networks) used for tasks such as [image segmentation](https://www.ibm.com/topics/image-segmentation), the act of optimizing the entire network to make accurate predictions entails training the encoder layers to output effective vector embeddings of input images.

**Pretrained models  
**For many use cases and fields of study, pretrained models can provide useful embeddings that can serve as inputs to custom models or vector databases. Such open source models are typically trained on a massive and broad set of training data to learn embeddings useful to many downstream tasks such as [few-shot learning](https://www.ibm.com/topics/few-shot-learning) or [zero-shot learning](https://www.ibm.com/topics/zero-shot-learning).

For text data, basic open source [word embedding](https://www.ibm.com/topics/word-embeddings) models such as Google’s Word2Vec or Stanford University’s Global Vectors (GloVe) can be trained from scratch, but are also offered in variants pretrained on public text data such as Wikipedia and Common Crawl. Likewise, encoder-decoder large language models (LLMs) often used for embeddings, such as BERT and its many variants, are pretrained on a huge amount of text data.

For computer vision tasks, pretrained image classification models such as ImageNet, ResNet or VGG can be adapted to output embeddings by simply removing their final, fully connected prediction layer.

**Custom embedding models**  
Some use cases, particularly those involving esoteric concepts or novel classes of data, benefit from the [fine-tuning](https://www.ibm.com/topics/fine-tuning) of pretrained models or the training of fully custom embedding models.

The legal and medical domains are prominent examples of fields that often rely on esoteric and highly specialized vocabulary, knowledge bases or imagery unlikely to have been included in the training data of more generalist models. Supplementing the base knowledge of pretrained models through further training on domain-specific examples can help the model output more effective embeddings.

While this can also be achieved through designing a bespoke neural network architecture or training a known architecture from scratch, doing so requires resources and institutional knowledge that might be out of reach to most organizations or hobbyists.

## Vector embedding for images

Image embeddings convert visual information into numerical vectors by using an image’s pixel values to correspond to vector components. They usually rely on CNNs, though recent years have increasingly seen computer vision models utilizing transformer-based neural networks.<sup>2</sup>

Images with a typical RGB color scheme are numerically represented as a three-dimensional matrix, in which those three matrices correspond to the respective red, green and blue values of each pixel. RGB images are usually 8-bit, meaning each color value for a pixel can range from 0 to 256 (or 2 <sup>8</sup>). As described earlier, black-and-white images are numerically represented as a two-dimensional matrix of pixels wherein each pixel has a value between 0 and 1.

 ![Diagram of an image being represented as a matrix of pixels](https://assets.ibm.com/is/image/ibm/vector-embedding:16x9?fmt=png-alpha&dpr=on%2C2.2222222222222223&wid=1584&hei=891)An image being represented as a three-dimensional matrix of pixels

[Convolutions](https://developer.ibm.com/articles/introduction-to-convolutional-neural-networks/) use 2-dimensional numerical filters, called *kernels*, to extract features from the image. The weights of the kernels most conducive to extracting relevant features are themselves a learnable parameter during model training. These convolutions yield a feature map of the image.

When necessary, *padding* is used to maintain the original size of the input by adding extra layers of zeros to the outer rows and columns of the array. Conversely, *pooling*, which essentially summarizes visual features by taking only their minimum, maximum or average values, can be used for further dimensionality reduction.

Finally, the compressed representation is then *flattened* into a vector.

### Image search

One intuitive application of image embedding is *image search:* a system taking image data as input and returning other images with similar vector embeddings, such as a smartphone app that identifies a plant species from a photograph.

A more complex execution is *multimodal* image search, taking text as input and returning images related to that text. This cannot be accomplished by taking a text embedding from a language model and using it as input to a separate computer vision model. Instead, the two embedding models must be explicitly trained to correlate with one another.

One prominent algorithm used for both image and text embeddings is *contrastive language-image pretraining* (CLIP), originally developed by OpenAI. CLIP was trained on an enormous unlabeled data set of over 400 million image-caption pairs taken from the internet. These pairings were used to jointly train an image encoder and text encoder from scratch by using *contrastive loss* to maximize the cosine similarity between image embeddings and the embeddings for their corresponding captions.

### Image generation

Another important application for image embedding is *image generation*: the creation of new images.

One method to generate new images from image embeddings uses [variational autoencoders (VAEs)](https://www.ibm.com/think/topics/variational-autoencoder). VAEs encode two different vector embeddings of input data: a vector of *means* and a vector of *standard deviations*. By randomly sampling from the probability distribution these vector embeddings represent, VAEs can use their decoder network to generate variations of that input data.

A more prominent embedding-based image generation method, especially in recent years, uses the previously mentioned CLIP algorithm. Image synthesis models such as DALL-E, Midjourney and Stable Diffusion take text prompts as input, using CLIP to embed a vector representation of the text; that same vector embedding, in turn, is used by a [diffusion model](https://www.ibm.com/think/topics/diffusion-models) to essentially reconstruct a new image.

## Vector embedding for NLP

Text embeddings are less straightforward. They must numerically represent abstract concepts such as semantic meaning, variable connotations and contextual relationships between words and phrases. Simply representing words in terms of their letters, the way image embeddings represent visuals in terms of their pixel values, would not yield meaningful embeddings.

Whereas most computer vision models are trained using conventional [supervised learning](https://www.ibm.com/topics/supervised-learning), embedding models for NLP require [*self* -supervised learning](https://www.ibm.com/topics/self-supervised-learning) on a truly massive amount of training data to adequately capture the many potential meanings of language in different contexts.

The resulting embeddings power many of the tasks commonly associated with generative AI, from language translation to conversational chatbots to document summarization to question-answering services.

### Text embedding models

The models used to generate vector embeddings for text data are often not the same as those used for generating actual text.

The popular LLMs commonly used for text generation and other generative AI tasks, such as OpenAI's GPT models or Meta's [Llama](https://newsroom.ibm.com/Blog-IBM-Offers-Metas-Llama-3-Open-Models-on-Watsonx,-Expands-Portfolio-of-Next-Generation-Enterprise-Ready-Models) models, are decoder-only *autoregressive* models, also called *causal language models*. In training, they’re presented with the first word of a text sample and tasked with continuously predicting the next word until the end of the sequence. While this lends itself well to learning to generate coherent text, it’s not optimal for learning useful standalone vector embeddings.

Instead, text embeddings typically rely on *masked language models* such as bidirectional encoder representations from transformers (BERT), first released in 2018. In training, these encoder-decoder models are provided text sequences with certain words *masked* —hidden—and tasked with completing the blanks. This exercise rewards embeddings that better capture information about a specific word or sentence and how it relates to the context around it. Word2vec pursues a similar training task, albeit with a simpler 2-layer neural network architecture.

As of June 2024, BERT remains the most popular language model on Hugging Face, having been downloaded over 60 million times in the month prior.<sup>3</sup> Several prominent [BERT](https://huggingface.co/google-bert/bert-base-uncased) variants have been adapted to specific types of language embeddings and scenarios:

- **SBERT:** Also known as sentence BERT and sentence transformers, SBERT is a variant of BERT with an adapted [Siamese neural network](https://www.cs.cmu.edu/~rsalakhu/papers/oneshot1.pdf) structure, [fine-tuned](https://www.ibm.com/topics/fine-tuning) on pairs of sentences to improve its ability to encode sentence embeddings.
- **DistilBERT:** A lightweight BERT variant, created through [knowledge distillation](https://www.ibm.com/topics/knowledge-distillation) of the BERT base model into a smaller model that runs 60% faster while preserving over 95% of BERT’s performance by some metrics.<sup>4</sup>
- **RoBERTa:** Short for robustly optimized BERT pretraining approach, RoBERTa refined the BERT training procedure to optimize its performance.

### Types of text embeddings

Vector embeddings can be used to represent various natural language data.

**Word embeddings**  
[Word embeddings](https://www.ibm.com/topics/word-embeddings) aim to capture not only the semantic meaning of individual words but also their contextual relationship to other words with which they often cooccur. In doing so, word embeddings can generalize well to new contexts and even rare or previously unseen words.

GloVe, a popular word embedding model, was trained on a “global word-word cooccurrence matrix,” inferring semantic meaning and semantic relationships from how often specific words are used close to one another. For example, meaning can be derived from how “ice” and “steam” coincide with “water” at roughly the same frequency, but coincide with “solid” and “gas” at very different rates.<sup>5</sup>

The way the dimensions of a word embedding vector implicitly capture these relationships enables us to mathematically manipulate them in useful and intuitive ways. In a well-configured word embedding scheme, subtracting the vector for “man” from the vector for “king” and adding the vector for “woman” should essentially yield the vector for “queen.”

**Sentence embeddings**  
Sentence embeddings embed the semantic meaning of entire phrases or sentences, rather than individual words. They’re typically generated with SBERT or other variants of sentence transformers.

- Sentence embeddings can embed representations of user queries, for use in search engines or question-answering applications.
- In machine translation, the vector embedding of a sentence in one language can be used to output a sentence in a different language with a similar vector embedding.
- Sentence embeddings are often used in sentiment analysis. Classifiers can be either trained on labeled examples of each category of sentiment or by using supervised learning, then classify new samples by matching their vector embedding to the learned embedding for each class. Sentiment analysis is also possible through zero-shot learning, in which the embedding for a specific sentence is compared to the word embedding of a particular categorization.

**Document embeddings**  
Document embeddingsare often used to classify documents or web pages for indexing in search engines or vector databases. Typical models for document embedding include BERT variants, Doc2vec (which is an expansion of the Word2vec model) or other open source embedding models such as Instructor (link resides outside ibm.com).

## Other types of vector embeddings

Though image and text data tend to receive the most attention, particularly for generative AI use cases, a wide variety of data modalities can benefit from vector embedding.

- **Audio embeddings** are used for various applications, from voice assistants to song recommendation systems to music recognition systems such as Shazam. They represent sound through the numerical properties of its waveform data. Audio can be embedded by using [recurrent neural networks (RNNs)](https://www.ibm.com/topics/recurrent-neural-networks), CNNs or [transformer-based architectures](https://www.ibm.com/think/topics/attention-mechanism).
- **Product embeddings** are often used to power recommendation systems for e-commerce platforms. They’re typically generated with [unsupervised learning](https://www.ibm.com/topics/unsupervised-learning) algorithms.
- **Graph embeddings** can be used to model and represent complex relationship structures such as social networks or biological systems. The dimensions of a graph embedding vector represent the way various nodes and edges of a system are connected.

## Vector databases

Traditional databases are rarely optimized to work the high-dimensional data common to vector embeddings. [Vector databases](https://www.ibm.com/topics/vector-database) such as [IBM® watsonx.data™](https://www.ibm.com/products/watsonx-data) are advanced solutions designed for organizing and retrieving data objects in high-dimensional vector space.

### Vector search

A primary benefit of an effective vector database solution is to optimize the efficiency and accuracy of *vector search* operations: finding, sorting and retrieving relevant data and documents by way of the semantic similarity of their respective vector embeddings to those of your search terms.

This type of similarity search is typically through straightforward [nearest-neighbor](https://www.ibm.com/topics/knn) algorithms that infer connections between data points based on their proximity in high-dimensional vector space.

**Semantic search  
**Semantic search uses vector embeddings to power searches that transcend simple keyword matching. For example, returning results for “apples” and “oranges” even though the original query was “fruit.” 

### Retrieval augmented generation (RAG)

This type of semantic search is also used to enable [retrieval augmented generation (RAG),](https://research.ibm.com/blog/retrieval-augmented-generation-RAG) a framework used to supplement the knowledge base of LLMs without having to undergo more fine-tuning.

In RAG, vector search is used to survey external data sources, as in, data sources that were not part of a foundation model’s training data and whose information could thus not be otherwise reflected in the LLM's output, to *retrieve* relevant information, then use that information to *augment* the responses *generated* by the LLM.

Link copied

[Data science and MLOps for data leaders](https://www.ibm.com/forms/mkt-51585)

[

Join forces with other leaders to drive the three essential pillars of MLOps and trustworthy AI: trust in data, trust in models and trust in processes.

](https://www.ibm.com/forms/mkt-51585)

## Resources

[Level up your ML expertise](https://developer.ibm.com/technologies/machine-learning/courses/)

[

Learn fundamental concepts and build your skills with hands-on labs, courses, guided projects, trials and more.

](https://developer.ibm.com/technologies/machine-learning/courses/)

Take the next step

Whether you choose to customize pre-built apps and skills or build and deploy custom agentic services using an AI studio, the IBM watsonx platform has you covered.

1. [Explore watsonx Orchestrate](https://www.ibm.com/products/watsonx-orchestrate)
2. [Explore watsonx.ai](https://www.ibm.com/products/watsonx-ai)

##### Footnotes

External links to ibm.com

1 ["Stable Tuple Embeddings for Dynamic Databases" \[Stable tuple embeddings for dynamic databases\]](https://arxiv.org/abs/2103.06766). arXiv. March 11, 2021.  
2 ["Leaderboard: Image Classification on ImageNet" \[Image classification on ImageNet\]](https://paperswithcode.com/sota/image-classification-on-imagenet). Papers With Code. Accessed June 5, 2024.  
3 ["Models" \[Models\] (sorted by "Most downloads")](https://huggingface.co/models?sort=downloads). Hugging Face. Accessed June 5, 2024.  
4 ["DistilBERT, a distilled version of BERT: smaller, faster, cheaper and lighter" \[DistilBERT, a distilled version of BERT: smaller, faster, cheaper, and lighter\]](https://arxiv.org/abs/1910.01108). arXiv. October 2, 2019.  
5 ["GloVe: Global Vectors for Word Representation" \[GloVe: global vectors for word representation\]](https://nlp.stanford.edu/projects/glove/). Stanford University. August 2014.