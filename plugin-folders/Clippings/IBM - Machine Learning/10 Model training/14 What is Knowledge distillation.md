---
title: What is knowledge distillation?
source: https://www.ibm.com/think/topics/knowledge-distillation
author:
- '[[Dave Bergmann]]'
published: 2024-12-06
created: 2026-08-31
description: "Knowledge distillation is a machine learning technique used to transfer the learning of a large pre-trained “teacher model” to a smaller “student model.”"
---

## What is knowledge distillation?

Knowledge distillation is a [machine learning](https://www.ibm.com/topics/machine-learning) technique that aims to transfer the learnings of a large pre-trained model, the “teacher model,” to a smaller “student model.” It’s used in [deep learning](https://www.ibm.com/topics/deep-learning) as a form of model compression and knowledge transfer, particularly for massive deep neural networks.

The goal of knowledge distillation is to train a more compact model to mimic a larger, more complex model. Whereas the objective in conventional deep learning is to train an [artificial neural network](https://www.ibm.com/topics/neural-networks) to bring its predictions closer to the output examples provided in a training data set, the primary objective in distilling knowledge is to train the student network to match the predictions made by the teacher network.

Knowledge distillation (KD) is most often applied to large deep neural networks with many layers and learnable [model parameters](https://www.ibm.com/think/topics/model-parameters). This process makes it particularly relevant to the ongoing proliferation of massive [generative AI](https://www.ibm.com/think/topics/generative-ai) models with billions of parameters.

The concept has its origins in a 2006 paper titled “Model Compression.” Caruana *et al* used what was a state-of-the-art classification model at the time, a huge [ensemble model](https://www.ibm.com/topics/ensemble-learning) comprising of hundreds of base-level classifiers, to label a large [dataset](https://www.ibm.com/think/topics/dataset), and then trained a single neural network on that newly labeled data set through conventional [supervised learning](https://www.ibm.com/topics/supervised-learning). This compact model, “a thousand times smaller and faster,” matched the ensemble’s performance.<sup>1</sup>[](#_ftn1)

[](#_ftn1)Knowledge distillation techniques have since been successfully employed across diverse fields, including [natural language processing (NLP)](https://www.ibm.com/topics/natural-language-processing), [speech recognition](https://www.ibm.com/topics/speech-recognition), image recognition and [object detection](https://www.ibm.com/think/topics/object-detection). In recent years, the study of knowledge distillation has been of particular importance to [large language models (LLMs)](https://www.ibm.com/topics/large-language-models). For LLMs, KD has emerged as an effective means of transferring advanced capabilities from leading proprietary models to smaller, more accessible [open source models](https://www.ibm.com/think/topics/open-source-llms).

## Why is knowledge distillation important?

In many real-world settings, an [artificial intelligence model](https://www.ibm.com/think/topics/ai-model)’s accuracy and capacity are not, unto themselves, enough to make the model useful: it must also fit within the available budget of time, memory, money and computational resources.

The top performing models for a given task are often too large, slow or expensive for most practical use cases—but often have unique qualities that emerge from a combination of their size and their capacity for pre-training on a massive quantity of [training data](https://www.ibm.com/think/topics/training-data). These emergent abilities are especially evident in autoregressive language models, like [GPT](https://www.ibm.com/think/topics/gpt) or [Llama](https://www.ibm.com/think/topics/llama-2), that exhibit capabilities beyond their explicit training objective of simply predicting the next word in a sequence. Conversely, small models are faster and less computationally demanding, but lack the accuracy, refinement and knowledge capacity of a large model with far more parameters.

In the seminal 2015 paper, “Distilling the Knowledge in a Neural Network,” Hinton *et al* proposed to circumvent these limitations by dividing training into two distinct stages with distinct purposes. The authors presented an analogy: whereas many insects have a larval form optimized for extracting energy and nutrients from the environment and a totally different adult form optimized for traveling and reproduction, conventional deep learning uses the same models for both the training and deployment stages, despite their different requirements.

Taking inspiration from both nature and the work of Caruana *et al*, Hinton *et al* suggested that training large, cumbersome models is worthwhile if doing so is the best way to extract structure from data—but introduced a different kind of training, *distillation,* to transfer that knowledge to a small model more suitable for real-time deployment.<sup>2</sup>[](#_ftn1)

Knowledge distillation techniques aim to not only replicate the outputs of teacher models, but to emulate their “thought processes.” In the era of LLMs, KD has enabled the transfer of abstract qualities like style, reasoning abilities and [alignment to human preferences and values](https://www.ibm.com/think/topics/rlhf).<sup>3</sup>[](#_ftn2)

Furthermore, smaller models are fundamentally more [explainable](https://www.ibm.com/think/topics/explainable-ai): in a model with hundreds of billions of parameters, it’s difficult to interpret the contributions of different parts of the neural network. Transferring representations learned by large “black-box” models to simpler models can help elucidate transformative insights in fields like medical diagnostics and molecular discovery.<sup>4</sup>

## How does knowledge distillation work?

Knowledge distillation (KD) doesn’t rely on any specific neural network architecture, nor does it even require the teacher network and student network to have the same architectures: it can be applied to any deep learning model.

KD takes advantage of the fact that artificial neural networks are “universal approximators”: given enough training data, and a large enough hidden layer, a neural network can approximate any function to arbitrary precision.<sup>5</sup>[](#_ftn1)

In conventional machine learning, the “knowledge” of a trained model is identified with its learned parameters: the variable weights (and biases), applied to the different mathematical operations occurring across the neural network, that amplify or diminish the influence a certain part of the network’s output has on another part. This view of knowledge makes it hard to see how one model can absorb the knowledge of another model of a different size and structure.

Instead, Hinton *et al* applied a more abstract, flexible view of knowledge as simply “a learned mapping from input vectors to output vectors.” In other words, KD interprets a model’s knowledge not as the strictly mathematical parameters it learns in training, but as *how it* *generalizes to new data* after that training.

Through this alternate understanding of knowledge, knowledge distillation methods aim to train student models to mimic not just the teacher model’s final output for a given input, but also the reasoning steps the teacher model takes to arrive at that final output. Conceptually, this works similarly to [*instruction tuning*](https://www.ibm.com/think/topics/instruction-tuning) through [chain-of-thought (CoT) prompts](https://www.ibm.com/think/topics/instruction-tuning), which improves the quality of LLM responses by teaching them to articulate their “step by step” rationale.

In conventional [supervised](https://www.ibm.com/think/topics/supervised-learning) or [self-supervised](https://www.ibm.com/think/topics/self-supervised-learning) learning, a *loss function* produces a vector representing the divergence (or *loss*) between the model’s outputs and the “correct” outputs (or *ground truth*) across different inputs. By adjusting model parameters to minimize the slope (or *gradient*) of this vector through an optimization algorithm like [gradient descent](https://www.ibm.com/think/topics/gradient-descent), the model’s outputs come closer to those correct outputs. While the model’s reasoning steps are “important” in that they influence its final output, they are not typically measured by a conventional loss function.

Knowledge distillation, conversely, also trains the student model to mimic the teacher model’s reasoning process through the addition of a specialized type of loss function, *distillation loss*, that uses discrete reasoning steps as *soft targets* for optimization.

### Soft targets

The output of any AI model can be understood as *predictions*: an autoregressive LLM *predicts* the next word(s) in a specified sequence; a computer vision model used for image classification *predicts* the category of a certain image. To arrive at these final predictions, called “hard targets” in this context, deep learning models typically make multiple preliminary predictions and use a [*softmax function*](https://research.ibm.com/publications/convex-bounds-on-the-softmax-function-with-applications-to-robustness-verification) to output the prediction with the highest probability. During training, a cross-entropy loss function is used to maximize the probability assigned to the correct output and minimize the probability assigned to incorrect outputs.

For example, an image classification model predicts the probability of an input image belonging to each known class the model is trained to recognize, then outputs the class with the highest probability value. In the mathematical parlance of machine learning, these individual classwise predictions are called *logits.* Similarly, an autoregressive LLM predicts multiple possibilities for each next word and (depending on its [*temperature*](https://dataplatform.cloud.ibm.com/docs/content/wsj/wscommon/glossary-wx.html?context=wx#x9661382) setting) samples one of those possibilities for its output.

In knowledge distillation, these intermediate predictions—the “*soft targets*”—generated by the teacher model often provide the principal training data for the student model. The relative probabilities assigned to these preliminary predictions provide valuable insight into how the teacher model tends to generalize. For example, an image classification model is many times more likely to misclassify an image of a fox as “dog” than as “sandwich.” Soft targets thus provide far more information per training case than hard targets alone.

Soft targets also provide more consistency than hard targets: a model’s final prediction might ultimately hinge on a minuscule difference between two logit values, but the logit values themselves have much less variance in the gradient between each training example.

Because of the richness and stability of the information provided by soft targets, the student model can be trained on fewer training examples, using a higher learning rate, than were used to train the original teacher model.

### Distillation loss

To bring the student network’s generalization tendencies closer to those of the teacher network, knowledge distillation typically uses two loss functions. The first is a standard loss function that operates on “hard loss,” measuring the student model’s final outputs against the ground truth labels (in supervised learning) or against the original data sample (in self-supervised learning). The second is *distillation loss*, a “soft loss” measuring the student model’s soft targets against those of the teacher.

Because there can be multiple soft targets for each training example, distillation loss measures the difference between the *probability distribution* of the teacher network’s soft targets and the probability distribution of the student’s. Kullback-Leibler divergence (or “KL divergence”) is commonly used for this purpose.

## Types of knowledge in knowledge distillation

While logits are the typical focus of teacher-student knowledge transfer, there are various ways that “knowledge” can manifest in a deep neural network. Other knowledge distillation methods focus on weights and activations in the network’s hidden layers, or on the relationships between different parts of the network.

These different forms of knowledge generally fall into one of three categories: *response-based knowledge*, *feature-based knowledge* or *relation-based knowledge.*

### Response-based knowledge

Response-based knowledge, the most common genre of knowledge distillation, focuses on transferring information from the final output layer of the teacher model. In a typical response-based KD method, the student model is trained to output logits that match the teacher model’s predictions.

When the teacher model’s soft targets have low entropy—in other words, when the predictions are extremely “confident,” like if a classification model outputs a logit very close to 1 (representing certainty) for one class and logits approaching 0 for all others—they do not provide as much information. Response-based methods thus often use a high *temperature* setting for model outputs, which increases the entropy of model predictions. This ensures a more variable probability distribution and thus a greater quantity of information from each training example.

### Feature-based knowledge

Feature-based knowledge focuses on information that is conveyed in the intermediate layers, or “hidden layers,” of a neural network. This is where neural networks tend to perform *feature extraction*, the identification of distinct characteristics and patterns of the input data that are relevant to the task at hand.

For example, in the convolutional neural networks used predominantly for computer vision tasks like [image segmentation](https://www.ibm.com/think/topics/image-segmentation), each successive hidden layer captures progressively richer detail as data is transmitted across the network. In a model used to classify images of animals by species, the earliest hidden layers might simply discern the presence of an animal shape in one part of the photo; the middle hidden layers might discern that the animal is a bird; the final hidden layers, just before the output layer, would discern the nuanced details differentiating one species of bird from another closely related species.

The goal of feature-based knowledge distillation methods is thus to train the student model to learn the same features as the teacher network. Feature-based distillation loss functions are used to measure and then minimize the difference between the two networks’ feature activations.

### Relation-based knowledge

Whereas both response-based and feature-based knowledge focus on the outputs of specific model layers, *relation-based* knowledge distillation focuses on the relationships between different layers or between feature maps representing the activations at different layers or locations.

In essence, relation-based knowledge represents perhaps the comprehensive approach to training the student network to emulate the teacher model’s “thought process.” These relationships and correlations can be modeled in various ways, including correlations between feature maps, matrices representing the similarity between different layers, feature embeddings or probabilistic distributions of feature representations.

## Knowledge distillation schemes

Knowledge distillation methods can also be categorized by their impact on the teacher network. While the distillation process originally proposed by Hinton *et al* and the many subsequent evolutions of that methodology aim solely to train the student network, other distillation schemes also entail the simultaneous updating of the *teacher* network weights.

### Offline distillation

In offline distillation, the teacher network is already pre-trained and its model weights are frozen to prevent further changes. Offline distillation is typical of many KD approaches for LLMs, in which the teacher is often a larger proprietary model for which model weights cannot be changed.

### Online distillation

In some circumstances, a suitably pre-trained and adequately performing teacher model might not be available, or a data scientist might want to tailor the teacher network to their specific use case. Online distillation schemes aim to simultaneously train both the teacher and student networks.

For example, Cioppa *et al* proposed an online distillation scheme for [semantic segmentation](https://www.ibm.com/think/topics/image-segmentation?_gl=1*doiemm*_ga*MTMwODI3MzcwLjE3NDA0MTE1Njg.*_ga_FYECCCS21D*MTc0MDc4MDQ4OS4xLjEuMTc0MDc4MjU3My4wLjAuMA..#Semantic+segmentation) models used in live sporting events, where visual circumstances might change throughout a match. It aimed to circumvent the tradeoff between a smaller network’s speed and a larger network’s accuracy by continuously training a slow, well-performing model on live match data while simultaneously distilling that larger model’s knowledge into a smaller, faster model deployed to generate outputs in real time.<sup>6</sup>[](#_ftn1)

### Self-distillation

In self-distillation, one network acts as both teacher and student. Whereas conventional knowledge distillation entails the transfer of knowledge from one model to another, self-distillation can be understood as the transfer of knowledge from a network’s deeper layers to the same network’s shallow layers.<sup>7</sup>[](#_ftn1)

In self-distillation, multiple attention-based “shallow classifiers” are added to the model’s intermediate layers at varying depths. During training, the deeper-lying classifiers act as the teacher models and guide the training of the other attention-based modules through two kinds of distillation losses: a KL divergence metric loss on the outputs and an [L2 regularization loss](https://www.ibm.com/think/topics/ridge-regression) on the feature maps.

After the model is trained and ready for inference, all these shallow classifiers are dropped from the model. Essentially, this allows for the model to be larger and have greater capacity for pattern recognition during training, but then be smaller and consequently faster and more efficient when deployed.

## Knowledge distillation and LLMs

With the advent of LLMs, knowledge distillation has emerged as an important means of transferring the advanced capabilities of large, often proprietary models to smaller, often open-source models. As such, it has become an important tool in the democratization of generative AI.

The LLMs with the highest capabilities are, in most cases, too costly and computationally demanding to be accessible to many would-be users like hobbyists, startups or research institutions. Furthermore, despite their advanced performance and unique abilities, proprietary LLMs by their nature cannot be tailored to niche applications and specific use cases.

Furthermore, most commercially viable LLMs are too large and computationally demanding to be used locally on mobile phones or other edge devices. This presents various logistical, computational and privacy complications that would otherwise be circumvented with a smaller model that could be run directly on mobile devices. KD’s model compression thus presents a promising means to transfer the emergent qualities of large models to models small enough to be run on-device.

Other common uses of knowledge distillation for LLMs include:

- **Making LLMs multilingual**, such as by using multiple teacher models—each of which specializes in a separate language—to transfer linguistic knowledge to a single student model<sup>8</sup>[](/content/adobe-cms/us/en/think/topics/knowledge-distillation.html#_ftn1)[](/content/adobe-cms/us/en/think/topics/knowledge-distillation.html#_ftn1) or by co-training models in separate languages to generate similar embeddings for the same sentence.<sup>9</sup>
- **Using larger, proprietary LLMs to generate data sets for the instruction tuning of smaller models**. For example, Microsoft’s Orca model “learn(ed) from rich signals from GPT-4 including explanation traces, step-by-step thought processes and other complex instructions.” [](#_ftn1)<sup>10</sup>
- **Using a teacher model to rank student outputs**, distilling its preferences and alignment settings through a variation of [reinforcement learning from human feedback (RLHF)](https://www.ibm.com/think/topics/rlhf) dubbed *reinforcement learning from AI feedback (RLAIF).*<sup>11</sup>

## Footnotes

<sup>1</sup> [“Model compression”](https://www.researchgate.net/publication/221653840_Model_compression), *Proceedings of the Twelfth ACM SIGKDD International Conference on Knowledge Discovery and Data Mining*, 23 August 2006

<sup>2</sup> [“Distilling the Knowledge in a Neural Network”](https://arxiv.org/abs/1503.02531), arXiv, 9 March 2015  
 <sup>3</sup> [“A Survey on Knowledge Distillation of Large Language Models”](https://arxiv.org/abs/2402.13116), arXiv, 8 March 2024  
 <sup>4</sup> [“Improving drug-target affinity prediction via feature fusion and knowledge distillation”](https://academic.oup.com/bib/article/24/3/bbad145/7142721), *Briefings in Bioinformatics*, May 2023  
 <sup>5</sup> [“A three layer neural network can represent any multivariate function”](https://arxiv.org/abs/2012.03016), arXiv, 16 January 2022  
 <sup>6</sup> [“ARTHuS: Adaptive Real-Time Human Segmentation in Sports Through Online Distillation”](https://openaccess.thecvf.com/content_CVPRW_2019/papers/CVSports/Cioppa_ARTHuS_Adaptive_Real-Time_Human_Segmentation_in_Sports_Through_Online_Distillation_CVPRW_2019_paper.pdf), *2019 IEEE/CVF Conference on Computer Vision and Pattern Recognition Workshops (CVPRW)*, 2019  
 <sup>7</sup> [“Self-Distillation: Towards Efficient and Compact Neural Networks”](https://ieeexplore.ieee.org/document/9381661), *IEEE Transactions on Pattern Analysis and Machine Intelligence*, vol. 44, no. 8, pp. 4388-4403, 1 August 2022  
 <sup>8</sup> [“Multilingual Neural Machine Translation with Knowledge Distillation”](https://arxiv.org/abs/1902.10461), arXiv, 30 April 2019  
 <sup>9</sup> [“Making Monolingual Sentence Embeddings Multilingual using Knowledge Distillation”](https://arxiv.org/abs/2004.09813), arXiv, 21 April 2020  
 <sup>10</sup> [“Orca: Progressive Learning from Complex Explanation Traces of GPT-4”](https://huggingface.co/papers/2306.02707), Hugging Face, 5 June 2023  
 <sup>11</sup> [“RLAIF: Scaling Reinforcement Learning from Human Feedback with AI Feedback”](https://arxiv.org/abs/2309.00267), arXiv, 1 September 2023
