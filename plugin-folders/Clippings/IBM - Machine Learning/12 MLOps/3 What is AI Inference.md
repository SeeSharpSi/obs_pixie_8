---
title: What is AI inference?
source: https://www.ibm.com/think/topics/ai-inference
author:
- '[[Dave Bergmann]]'
published: 2024-12-18
created: 2026-08-31
description: "AI inference is the act of using a trained artificial intelligence model to make predictions on new data. A trained AI model applies patterns learned from training data to infer the correct output for a given input."
---

## AI inference, simplified and explained

In [machine learning](https://www.ibm.com/think/topics/machine-learning), AI inference is the act of using a trained [AI model](https://www.ibm.com/think/topics/ai-model) to make predictions on new data. Essentially, any instance of an [artificial intelligence](https://www.ibm.com/think/topics/artificial-intelligence) model actually generating outputs or making decisions in a real-world AI application constitutes AI inference. In simple terms, AI inference entails a trained model applying the patterns it learned from its [training data](https://www.ibm.com/think/topics/training-data) to *infer* the correct output for a given input.

All [machine learning](https://www.ibm.com/think/topics/machine-learning), from email spam detection models to the navigation systems powering self-driving cars to [generative AI](https://www.ibm.com/think/topics/generative-ai), boils down to pattern recognition. Models are “trained” to perform well on a [dataset](https://www.ibm.com/think/topics/dataset) of sample tasks or data points. During [model training](https://www.ibm.com/think/topics/model-training), the [model’s parameters](https://www.ibm.com/think/topics/model-parameters) (and [hyperparameters](https://www.ibm.com/think/topics/hyperparameter-tuning)) are adjusted until the model’s decision-making “fits” the patterns of the training data. The core assumption of machine learning is that if the training data is relevant enough to what the model will see in real-world scenarios, it will make accurate predictions in those real-world use cases.

Whereas a lot of AI jargon is highly technical, “AI inference” is actually a literal, intuitive term.

- A stock market [forecasting model](https://www.ibm.com/think/topics/forecasting) doesn’t *know* how a given stock’s price will change; it *infers*, based on how that stock’s history compares to past trends in stock price movement, what will happen next.

- A spam detection model doesn’t *know* if a given email is spam; it *infers*, based on how much that email resembles the spam examples it saw in training, whether it’s spam or not.

- A [large language model (LLM)](https://www.ibm.com/think/topics/large-language-models) iteratively *infers* what the next word—or rather, [token](https://www.ibm.com/docs/en/watsonx/saas?topic=solutions-tokens)—will be based on the linguistic patterns of the millions of text samples it was trained on.

- Social media networks *infer* what content you’re most likely to engage with based on the content that you and people similar to you have engaged with before.

Whereas the goal of AI training is achieving model accuracy and alignment, the goal of AI inference is deploying that trained model in a maximally efficient, cost-effective way. The same AI model might perform differently in different inference frameworks.

There is no one, single “optimal” AI inference setup. There are many different ways to split workloads, different types of hardware (and computational algorithms with which to use them), and different environments in which to access that hardware. The ideal setup for a given scenario will depend on the nature of your use case and workload. For enterprises, the challenge is usually to identify an inference approach that balances the desire for low latency with the need to be scalable and cost-efficient.

### AI inference vs. AI training

Both AI inference and AI training involve a model making predictions about input data. The difference lies in their respective purposes and, in the case of AI training, in the extra steps taken toward that purpose.

Training is where the “learning” in machine learning occurs. In [model training](https://www.ibm.com/think/topics/model-training), a machine learning model makes predictions on a batch of training data examples. In [supervised learning](https://www.ibm.com/think/topics/supervised-learning), a [loss function](https://www.ibm.com/think/topics/loss-function#1580786328) calculates the average error (or “loss”) of each prediction, and an optimization algorithm is used to update [model parameters](https://www.ibm.com/think/topics/model-parameters) in a way that reduces loss. This process is iteratively repeated until loss has been minimized to an acceptable level. [Reinforcement learning](https://www.ibm.com/think/topics/reinforcement-learning) works similarly, albeit with the goal of maximizing a reward function instead of minimizing a loss function.

In short, AI training typically entails both a *forward pass* in which the model generates an output in response to each input and a [*backward pass*](https://www.ibm.com/think/topics/backpropagation) in which potential improvements to the model’s parameters are calculated. These parameter updates comprise a machine learning model’s “knowledge.”

In AI inference, the trained model then makes predictions on real-world input data. AI inference works by using what it has “learned”—that is, the model parameter updates that were made in order to improve its performance on the training data—to *infer* the correct output for the new input data. Unlike in model training, inference entails only a forward pass.

While training and inference are usually separate, distinct stages, its worth noting that they’re not quite mutually exclusive. For instance, a social media platform’s recommendation algorithm has already been trained on large data sets of user behavior before you join the platform, and is performing inference each time it provides content suggestions to you. But that trained model is also continually [fine-tuned](https://www.ibm.com/think/topics/fine-tuning) on your individual behaviors, refining its suggestions based on how you personally engage with content.

## Types of AI inference

“Type” is a nebulous word: there are many ways to execute AI inference, and therefore many ways to delineate its variants. But the two most fundamental categories of AI inference strategies are *batch inference* and *online inference*.

### Online inference

In online inference, a trained model processes input data immediately, one input at a time. Online inference is appropriate for any AI system whose outputs are time sensitive (such as autonomous vehicles, digital ad bidding or dynamic pricing) or that require live interactions with users (such as chatbots or machine translation).

Online inference generally entails greater costs and complexity—especially for heavy workloads and the large [neural networks](https://www.ibm.com/think/topics/neural-networks) that power [deep learning](https://www.ibm.com/think/topics/deep-learning) models—but it’s often necessary for any real-world use case that requires real-time decision making. A [chatbot](https://www.ibm.com/think/topics/chatbots) or self-driving car must process data in real time to avoid degrading the user experience. The utility of an AI system that predicts whether a given applicant should receive a loan isn’t really affected by a slight delay between input and output, but in an autonomous vehicle a few extra milliseconds of lag might endanger passengers.

### Batch inference

In batch inference, a trained model processes a large volume of inputs asynchronously in groups (or “batches”). Each batch is typically scheduled for a certain time: for instance, a business might use batch inference to run nightly reports on all of that day’s activity. This allows for greater flexibility and efficiency, making batch inference the more cost-effective option. However, it’s only practical in situations where timeliness isn’t important.

Batch inference also allows for more efficient usage of hardware. For instance, GPUs contain many thousands of processing units (or “cores”), each of which can perform calculations simultaneously in parallel. Running inference for a single input that doesn’t enlist all those cores is like leaving seats empty on a bus: it might be necessary in time-sensitive situations, but it’s a sub-optimal use of resources. Batch inference enables you to run inference only once your hardware is “full,” so to speak.

Furthermore, model parameters—which, for deep learning models, often comprise literal billions of model weights—must be loaded into system memory each time inference is performed. This entails energy usage and costs. Batch inference reduces the number of times weights must be loaded into RAM, spreading the cost across the entire batch.

#### Micro-batching

Micro-batching is a middle-ground approach between online inference and batch inference: as its name suggests, it entails running inference in small batches.

There’s no clear, quantifiable batch size that differentiates “micro-batching” from “batching.” Instead, the two approaches are differentiated primarily by their goals: micro-batching aims to increase model throughput while (mostly) preserving model speed, whereas conventional batch inference aims to maximize efficiency and generally doesn’t take latency into consideration. In batch inference, an input might be processed minutes or even hours after it’s received—but micro-batching usually aims for no more milliseconds to a few seconds of lag.

Perhaps the most prominent application of micro-batching is in cloud-based LLM inference through major platforms such as Anthropic’s Claude or OpenAI’s ChatGPT. When thousands of users are prompting a chatbot simultaneously, these services typically process multiple prompts in parallel, increasing efficiency without noticeable lag for individual end users.

## AI inference environments

One of the most important considerations in designing an AI ecosystem is deciding where the inference workload will actually run. In other words, where the hardware is located and how you’ll access that hardware.

[Deployment](https://www.ibm.com/think/topics/model-deployment) environments generally fall into one of four categories, each of which has its own strengths and tradeoffs.

- **On-premise**

- **Cloud**

- **Edge deployment**

- **On-device**

### On-premise deployment

In on-premise (or “on-prem”) deployment, AI models are run on physical hardware that you (or your organization) own and maintain yourself.

On-prem deployment offers the greatest possible control over AI workloads, as you yourself have autonomy over how and when data is processed and computational resources are allocated. This is especially beneficial in highly regulated industries such as healthcare, finance, government and law, wherein strict adherence to requirements for data privacy and security are mandatory.

That control comes with a trade-off in the cost and labor involved. On-prem deployment, particularly with the hardware needed for enterprise-scale workloads and the massive models typically associated with generative AI, entails major upfront investment. It also entails a need for dedicated IT professionals to manage those servers.

### Cloud deployment

In cloud deployment, models are run on remote servers managed by third party vendors (such as IBM) in large data center. This enables an organization to utilize high-powered AI hardware without the massive upfront investment required to purchase it or ongoing labor to maintain it. As such, cloud deployment typically represents the quickest route to scalability—especially in circumstances when you must quickly scale up your computational resources to meet some spike in demand.

That flexibility and scalability comes with a trade-off in data sovereignty and, in some cases, latency and long-term costs. Data might travel back and forth to and from the cloud servers, which might have an adverse effect on inference speed (though that’s often negated by the more powerful hardware usually available through major cloud providers). That also introduces theoretical complications with regard to data provenance, as data is exposed to more entities than it would be in on-prem scenarios.

### Edge deployment

Edge deployment refers to the utilization of computational resources that are physically close to the data source, such as through internet of things (IoT) devices and local area networks.

Broadly speaking, edge deployment can be understood as something akin to an “on-premise cloud.” It’s most beneficial when data needs to be aggregated from or distributed to a number of devices—such as sensors across a factory assembly line or monitoring devices in a hospital—and processed in near real-time. In such scenarios, running inferences through devices at the “edges” of a local network allows for faster processing and greater privacy than would be possible through cloud deployment.

Those benefits are, to some extent, mitigated by the fact that edge computing usually enlists hardware that’s relatively limited compared to what’s available through cloud providers. And as local networks grow larger, managing updates across hundreds or thousands of “edge nodes” becomes increasingly complex.

### On-device deployment

On-device deployment is the most straightforward: AI inference runs directly on the end user’s device, such as a laptop or a smartphone.

On-device deployment is simple and secure, and theoretically provides the greatest possible user privacy. It is, of course, limited by the compute capacity of the device itself: the compute available in a smartphone, or even in a high-performance consumer computer, generally pales in comparison to that of specialized hardware. Particularly on smartphones, on-device inference is typically limited to specific tasks, such as camera filters, facial recognition or speech-to-text.

## Hardware for AI inference

AI inference is a complex process that involves training an AI model on appropriate datasets until it can infer accurate responses. This is a highly compute-intensive process, requiring specialized hardware and software. Before looking at the process of training AI models for AI inference, let’s explore some of the specialized hardware that enables it:

### Graphics processing unit (GPU)

[GPUs](https://www.ibm.com/think/topics/gpu) were, as their name suggests, originally designed for rendering graphics (such as in video games). Rendering 3D graphics, like running inference for deep neural networks, requires massive matrix multiplications—for instance, to calculate effects of light and texture on thousands of pixels simultaneously.

The ability to use that parallelism for math (instead of graphics) took a huge leap forward when NVIDIA introduced Compute Unified Device Architecture (CUDA), a software platform, [API](https://www.ibm.com/think/topics/api) and programming model enabling developers to write code that runs directly on the thousands of parallel cores of GPU. Today, GPUs remain the industry standard hardware for training and running deep learning models.

### Tensor processing units (TPUs)

TPUs are Google’s proprietary custom chips, built specifically for neural networks. Whereas GPUs are flexible, general purpose parallel processors, TPUs are designed exclusively for high-speed matrix math. Though they’re less versatile than GPUs, TPUs offer greater speed and energy efficiency when processing huge amounts of neural network data.

### Neural processing units (NPUs)

[Neural processing units (NPUs)](https://www.ibm.com/think/topics/neural-processing-unit), like TPUs, were explicitly designed to process the computations of neural networks. They’re typically used on smartphones and other mobile devices, as their more narrowly focused capabilities reduce power consumption relative to that of GPUs.

### Field-programmable gate arrays

[Field-programmable gate arrays (FPGAs)](https://www.ibm.com/think/topics/field-programmable-gate-arrays) are a type of configurable integrated circuit that can be programmed (and reprogrammed) to suit the demands of specific applications, including artificial intelligence operations. Though they generally offer less processing power than top flight GPUs, FPGAs are advantageous when extreme customization is needed.

### Application-specific integrated circuits

ASICS, unlike FPGAs, cannot be customized or reconfigured. They’re explicitly designed to perform a single task at maximum efficiency. Google’s TPUs, for example, are ASICs designed to exclusively perform neural network operations through TensorFlow, PyTorch and JAX.

## Distributed AI inference

The training or inference workloads of a large generative AI model will often exceed the capacity of even the largest accelerator hardware. When your workload is too big for a single GPU, it can be spread across multiple processors using one or more *parallelism* techniques to divide and spread out the work. There are many parallelism paradigms, but the most prominent are *data parallelism*, *tensor parallelism* and *pipeline parallelism*.

Developers can often make use of open source frameworks such as [vLLM](https://github.com/vllm-project/vllm) to optimize and simplify the process of distributing inference across multiple devices.

In data parallelism, a replica of the full model is copied across each processor. The input dataset itself is then split into multiple batches (or “shards”) and each copy of the model—that is, each processor—handles a single batch. While this is perhaps the most straightforward means of parallelism, it requires each processor to be large enough to fit all of the model’s parameters in memory. When dealing with larger LLMs and [vision-language models (VLMs)](https://www.ibm.com/think/topics/vision-language-models) with dozens or hundreds of billions of parameters, this is rarely possible. In such cases, other parallelism paradigms must be used.

In pipeline parallelism, different layers of a neural network are assigned to different GPUs. For example, a 12-layer neural network might be divided across 3 GPUs, with the first GPU being assigned the first 4 layers, the second GPU handling the middle 4 layers and the third GPU handling the final 4 GPU layers. The data is then processed sequentially: the output of the first GPU is passed to the second GPU, the output of the second GPU is passed to the third and the third GPU computes the model’s final output.

Efficient pipeline parallelism typically calls for mini-batching, so that each GPUs is always processing data simultaneously rather than sitting idly until it receives data from the previous GPU in the sequence. In our basic example from the previous paragraph, the first GPU might begin processing a new mini-batch of input data immediately after passing the output from the first mini-batch to the second GPU.

Naturally, a system using pipeline parallelism takes some “ramp-up” time to reach full device utilization. In our example, the second GPU can’t begin working until it receives data from the first; the third GPU can’t begin working until the first 2 GPUs have processed the full mini-batch; the fourth GPU can’t begin until the third is finished.

For very large models, even a single layer might be too large to fit on a single processor. In tensor parallelism, the layers themselves are subdivided, with each processor receiving a portion of the tensor of model weights. The [vector embedding](https://www.ibm.com/think/topics/vector-embedding)—that is, the tensor representation—of the input data is likewise subdivided, with each processor receiving a corresponding subset of the input data.

Tensor parallelism significantly reduces the memory demands on each device, as each processor needs to load smaller tensors in memory than they would in other parallelism paradigms. This comes with some tradeoff in complexity, as a greater amount of intra-device communication and mathematical steps are needed to weave together the outputs of each GPU.

## Footnotes

1 [“Why Companies Are Vastly Underprepared For The Risks Posed By AI”](https://www.forbes.com/sites/bernardmarr/2023/06/15/why-companies-are-vastly-underprepared-for-the-risks-posed-by-ai/), Forbes, June 15, 2023

2 [“Onshoring Semiconductor Production: National Security Versus Economic Efficiency”](https://www.cfr.org/article/onshoring-semiconductor-production-national-security-versus-economic-efficiency#:~:text=But%20even%20that%20understates%20Taiwan%27s,chips%20are%20manufactured%20in%20Taiwan.), Council on Foreign Relations, April 2024
