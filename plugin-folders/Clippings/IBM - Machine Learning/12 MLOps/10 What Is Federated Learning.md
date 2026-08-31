---
title: What is federated learning?
source: https://www.ibm.com/think/topics/federated-learning
author:
- '[[Rina Diane Caballar]]'
- '[[Cole Stryker]]'
published: 2025-04-02
created: 2026-08-31
description: "Federated learning is a decentralized approach to training machine learning (ML) models. Each node across a distributed network trains a global model using its local data, with a central server aggregating node updates to improve the global model."
---

## What is federated learning?

Federated learning is a decentralized approach to training [machine learning (ML)](https://www.ibm.com/think/topics/machine-learning) models. Each node across a distributed network trains a global model using its local data, with a central server aggregating node updates to improve the global model.

[Artificial intelligence (AI)](https://www.ibm.com/think/topics/artificial-intelligence) models require massive volumes of data. These [datasets](https://www.ibm.com/think/topics/dataset) are typically centralized in a single location for [model training](https://www.ibm.com/think/topics/model-training), opening up opportunities for any [personally identifiable information (PII)](https://www.ibm.com/think/topics/pii) contained in the datasets to be exposed during transmission or storage.

[Federated learning](https://research.ibm.com/blog/what-is-federated-learning) helps address these concerns as sensitive information remains on the node, preserving [data privacy](https://www.ibm.com/think/topics/data-privacy). It also allows for collaborative learning, with varied devices or servers contributing to the refinement of [AI models](https://www.ibm.com/think/topics/ai-model).

## How federated learning works

Federated learning involves 4 main stages:

- Initialization
- Local training
- Global aggregation
- Iteration

### Initialization

Federated learning starts with initializing a global machine learning model on a central server. This model is the basis from which the federated learning process begins.

The central server distributes the global model to connected client nodes, which can be other servers or [edge](https://www.ibm.com/think/topics/edge-computing) devices such as smartphones and [Internet of Things (IoT)](https://www.ibm.com/think/topics/internet-of-things) devices. It also relays relevant information, including configuration variables such as [hyperparameters](https://www.ibm.com/think/topics/hyperparameter-tuning) and the number of epochs or complete passes through the training data.

### Local training

Upon receiving the global model and all the necessary details, each client node proceeds with training. The training process is akin to any [neural network](https://www.ibm.com/think/topics/neural-networks), with client nodes training the model using only their on-device or local data.

When they’ve completed the number of epochs, client nodes transmit the updated model parameters or [gradients](https://www.ibm.com/think/topics/gradient-descent) to the central server—no fully trained local models or raw data are sent back.

### Global aggregation

The central server aggregates all the client node updates. There are different forms of aggregation, but a common method is federated averaging, which calculates the weighted average of all updates. These combined updates are then incorporated into the global model.

### Iteration

The central server again distributes the new global model to connected client nodes, and the federated learning process repeats until the model reaches full convergence or is fully trained.

## Types of federated learning

Federated learning can vary based on the structure of datasets or the nature of client nodes. It’s typically classified into these categories:

- Cross-device
- Cross-silo
- Horizontal
- Vertical

### Cross-device

Cross-device federated learning uses devices with volatile connectivity and limited computing resources, such as mobile phones and IoT devices. This type of federated learning needs to account for unreliable network connections, and because client nodes can only handle small datasets, many devices will usually be required for local training.<sup>1</sup>

E-commerce companies, for example, can train a [recommendation engine](https://www.ibm.com/think/topics/recommendation-engine) on user data across multiple devices to deliver more personalized product recommendations.<sup>1</sup>

### Cross-silo

Unlike the cross-device federated learning approach, cross-silo entails a limited number of servers or [data centers](https://www.ibm.com/think/topics/data-centers) with stable connectivity and computational resources powerful enough to store and process huge volumes of data. Client nodes are treated as silos holding personal data, and this data must not leave the system or be shared externally due to privacy concerns.<sup>1</sup>

Cross-silo federated learning can be valuable in industries such as finance and healthcare. For instance, a consortium of hospitals can train a shared model on their own patient data to enhance the diagnosis or prediction of certain diseases. Similarly, a coalition of banks can train a common [machine learning algorithm](https://www.ibm.com/think/topics/machine-learning-algorithms) using their own transaction records to improve fraud detection.<sup>1</sup>

### Horizontal

In horizontal federated learning, client node datasets share the same features or structure but have different samples. For instance, clinics can train a shared analytical model because each one has the same variables for their clinical trial data but distinct values for the patients involved in the trials.

### Vertical

Conversely, vertical federated learning involves client node datasets that share the same samples but have a different structure or features. For example, a retailer and a bank might enter into a partnership for more personalized customer offers, and they can train a common recommendation engine because they might have the same customer data but varied purchasing and financial information.

## Benefits of federated learning

The decentralized nature of federated learning offers these key advantages:

- Efficiency
- Enhanced data privacy
- Improved compliance

### Efficiency

Federated learning eliminates the need to access or transfer large datasets. This leads to decreased latency and a reduction in the required bandwidth for training machine learning models.

### Enhanced data privacy

The privacy-preserving architecture of federated learning systems means that sensitive data never leaves a device. This helps minimize the risk of [cyberattacks](https://www.ibm.com/think/topics/cyber-attack) or data breaches.

Most federated learning systems also implement cryptographic techniques including differential privacy and secure multiparty computation (SMPC) to boost data privacy.  

 Differential privacy adds noise to model updates before transmitting them to the central server, while SMPC allows the central server to carry out secure aggregation computations on encrypted model updates. These methods make it difficult to reverse engineer or distinguish which client node contributed an update, strengthening [data security](https://www.ibm.com/think/topics/data-security).

### Improved compliance

Because data is kept and processed locally, federated learning can help enterprises comply with [data protection](https://www.ibm.com/think/topics/data-protection) regulations. Compliance is crucial for sectors such as finance and healthcare, which handle private data.

## Challenges of federated learning

Federated learning signifies a transformative shift in training AI models, but it also comes with limitations. Here are some challenges associated with federated learning:

- Adversarial attacks
- Communication overhead
- Heterogeneity

### Adversarial attacks

Federated learning is vulnerable to [data poisoning](https://www.ibm.com/think/topics/data-poisoning) attacks, where [threat actors](https://www.ibm.com/topics/threat-actor) inject malicious data during local training or alter model updates for transmission to compromise or corrupt the central model.  

 Anomaly detection, adversarial training, strict access controls and other security measures can help safeguard against these attacks.

### Communication overhead

Regular exchanges between client nodes and the central server can result in substantial bottlenecks. For better communication efficiency, consider strategies such as compressing model updates before transmission, [quantization](https://www.ibm.com/think/topics/quantization) and sparsification to relay a subset of the updates or only essential updates. These strategies must be balanced with any accompanying decrease in accuracy.

### Heterogeneity

Federated learning’s decentralized design can bolster data diversity that can help mitigate [bias](https://www.ibm.com/think/topics/ai-bias). However, this also means that data is not identically distributed and can be imbalanced. Some devices might have more data than others, skewing the global model toward these data-heavy nodes.

A few ways to address this statistical heterogeneity include sampling methodologies or techniques that factor in variation in distribution, clustering nodes with similar data distributions during model training and optimization algorithms such as [FedProx](https://github.com/litian96/FedProx), which is targeted for heterogeneous networks.

Systems heterogeneity is also an issue, with devices having different computing capabilities. Adaptive local training can be applied to tailor model training according to what a node can handle.

## Federated learning use cases

Federated learning holds the promise of helping solve real-world problems, with organizations joining forces even across borders and geographical regions. Here are some industries that can benefit from federated learning:

- Finance
- Healthcare
- Retail and manufacturing
- Urban management

### Finance

Financial institutions can work together to diversify data for credit risk assessment models, allowing better credit access for underserved groups. They can also use federated learning to provide more personalized banking and investment advice, thereby improving the [user experience](https://www.ibm.com/think/topics/user-experience).

### Healthcare

Hospitals and research institutions can train shared [deep learning](https://www.ibm.com/think/topics/deep-learning) models that aid in drug discovery for rare diseases. Federated learning systems can also assist in finding better treatment strategies and enhancing patient outcomes for underrepresented communities.

### Retail and manufacturing

Retailers can use federated learning to track sales and inventory across multiple locations without revealing any customer data, allowing them to maximize stock levels and lessen waste. Meanwhile, manufacturers can aggregate data from different parts of the supply chain to optimize logistics.

### Urban management

Smart cities can take advantage of federated learning to glean insights from the myriad devices and sensors scattered around urban areas while keeping resident data private. These insights can be used to better direct traffic, for instance, or to monitor environmental conditions such as air and water pollution.

## Federated learning frameworks

Implementing federated learning for real-world applications can be complex, but several frameworks exist to train models on decentralized data and streamline server and client workflows. Here are some popular federated learning frameworks:

- Flower
- IBM Federated Learning
- NVIDIA FLARE
- OpenFL
- TensorFlow Federated

### Flower

[Flower](https://flower.ai/) is an [open source](https://www.ibm.com/think/topics/open-source) framework for collaborative AI and [data science](https://www.ibm.com/think/topics/data-science). It can be used to craft federated AI systems with numerous connected clients. It’s compatible with most machine learning frameworks and interoperable with various hardware platforms and operating systems.

### IBM Federated Learning

[IBM Federated Learning](https://www.ibm.com/docs/en/watsonx/saas?topic=models-federated-learning) is a framework for federated learning in enterprise environments. It works with various machine learning algorithms, including [decision trees](https://www.ibm.com/think/topics/decision-trees), [Naïve Bayes classifiers](https://www.ibm.com/think/topics/naive-bayes), neural networks and [reinforcement learning](https://www.ibm.com/think/topics/reinforcement-learning).  

 [IBM Federated Learning](https://github.com/IBM/federated-learning-lib) also comes with a rich library of fusion methods for combining model updates and supports various fairness techniques to help combat AI bias.

### NVIDIA FLARE

[NVIDIA FLARE](https://developer.nvidia.com/flare) (Federated Learning Application Runtime Environment) is an open source and domain-agnostic software development kit for federated learning.  

 It has built-in training and evaluation workflows, privacy-preserving algorithms and learning algorithms for federated averaging and FedProx. NVIDIA FLARE also has management tools for orchestration and monitoring.

### OpenFL

[OpenFL](https://openfl.io/) is a Python-based open source federated learning framework originally created by Intel and now under The Linux® Foundation. OpenFL works with deep learning frameworks such as [PyTorch](https://www.ibm.com/think/topics/pytorch) and machine learning libraries including TensorFlow. Its security features include differential privacy and support for hardware-based trusted execution environments.

### TensorFlow Federated

[TensorFlow Federated (TFF)](https://www.tensorflow.org/federated) is an open source framework developed by Google for machine learning on decentralized data. TFF’s [application programming interfaces (APIs)](https://www.ibm.com/think/topics/api) are divided into 2 layers:

- Federated Learning API is the high-level layer that facilitates implementing federated learning tasks such as training or evaluation using existing machine learning models.
- Federated Core API is the low-level layer for building new federated learning algorithms.

## Footnotes

*All links reside outside ibm.com*

<sup>1</sup> [Cross-silo and cross-device federated learning on Google Cloud](https://cloud.google.com/architecture/cross-silo-cross-device-federated-learning-google-cloud), Google Cloud, 3 June 2024.
