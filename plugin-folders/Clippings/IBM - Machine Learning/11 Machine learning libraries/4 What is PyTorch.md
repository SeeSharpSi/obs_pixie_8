---
title: What is PyTorch?
source: https://www.ibm.com/think/topics/pytorch
author:
- '[[Dave Bergmann]]'
- '[[Cole Stryker]]'
published: 2024-11-21
created: 2026-08-31
description: "PyTorch is a software-based open source deep learning framework to build neural networks, pairing the Torch machine learning library with a Python-based API."
---

## What is PyTorch?

PyTorch is a software-based open source [deep learning](https://www.ibm.com/think/topics/deep-learning) framework used to build [neural networks](https://www.ibm.com/think/topics/neural-networks), combining the [machine learning](https://www.ibm.com/think/topics/machine-learning) (ML) library of Torch with a [Python](https://www.ibm.com/think/topics/python-vs-r)-based high-level API. Its flexibility and ease of use, among other benefits, have made it the leading ML framework for academic and research communities.

PyTorch supports a wide variety of neural network architectures, from simple linear regression algorithms to complex convolutional neural networks and generative transformer models used for tasks like [computer vision](https://www.ibm.com/think/topics/computer-vision) and [natural language processing (NLP)](https://www.ibm.com/think/topics/natural-language-processing). Built on the widely understood Python programming language and offering extensive libraries of pre-configured (and even pre-trained) models, PyTorch allows data scientists to build and run sophisticated deep learning networks while minimizing the time and labor spent on code and mathematical structure.

PyTorch also allows data scientists to run and test portions of code in real time, rather than wait for the entire code to be implemented—which, for large deep learning models, can take a very long time. This makes PyTorch an excellent platform for rapid prototyping, and also greatly expedites the debugging process.

Originally developed by Facebook AI Research (now Meta), PyTorch was made open source in 2017 and has been under the stewardship of the PyTorch Foundation (which is part of the larger Linux Foundation) since 2022. The foundation serves a neutral space for the deep learning community to collaborate on further development of the PyTorch ecosystem.

[In 2023, IBM became a premier member of the PyTorch Foundation](https://research.ibm.com/blog/ibm-pytorch-foundation), having already collaborated on two major projects: enabling more efficient training of [flexible AI foundation models with billions of parameters](https://research.ibm.com/blog/what-are-foundation-models) and [making checkpointing for AI training considerably more cost effective](https://research.ibm.com/blog/ibm-pytorch-ai-training). The IBM [watsonx](https://www.ibm.com/watsonx) portfolio uses PyTorch to provide an enterprise-grade software stack for artificial intelligence [foundation models](https://www.ibm.com/products/watsonx-ai/foundation-models), from end-to-end training to fine-tuning of models.

## How does PyTorch work?

PyTorch’s mathematical and programming structure simplifies and streamlines machine learning workflows, without limiting the complexity or performance of deep neural networks.

### Python

Python is a general purpose, high-level programming language widely used in data science, making it an intuitive choice for data scientists extending their work into actively modeling deep learning networks. Python’s simple syntax is easy to read, takes relatively little time to learn and can run on any operating system, including Windows, macOS, Linux or Unix. Python has been the second most used programming language on GitHub for over three years, having overtaken Java in 2019. It continues to grow in popularity, with a 22.5 percent increase in 2022.<sup>1</sup>

This flexibility and simplicity has helped foster a robust online community of Python developers, collaborating on a [wide array of Python libraries and APIs](https://community.ibm.com/community/user/ai-datascience/blogs/samira-gholizadeh/2022/02/22/top-popular-python-libraries)—like Numerical Python (NumPy) for mathematical operations, [Pandas](https://developer.ibm.com/learningpaths/get-started-data-science/data-analysis-in-python-using-pandas/) for data manipulation or [matplotlib](https://dataplatform.cloud.ibm.com/exchange/public/entry/view/55f7f605960d9a4d578aeeaa2b62bdea) for data visualization—and [educational resources](https://developer.ibm.com/languages/python/). This community has also produced a great volume of Pytorch libraries that reduce the monotony and guesswork of coding for machine learning, freeing up developers and data scientists to focus on innovation rather than rote task writing.

### Tensors

In any machine learning algorithm, even those applied to ostensibly non-numerical information like sounds or images, data must be represented numerically. In PyTorch, this is achieved through tensors, which serve as the fundamental units of data used for computation on the platform.

In the context of machine learning, a tensor is a multi-dimensional array of numbers that functions like a mathematical bookkeeping device. Linguistically, “tensor” functions as a generic term inclusive of some more familiar mathematical entities:

- A *scalar* is a zero-dimensional tensor, containing a single number.
- A *vector* is a one-dimensional tensor, containing multiple scalars of the same type. A *tuple* is a one-dimensional tensor containing different data types.
- A *matrix* is a two-dimensional tensor, containing multiple vectors of the same type.
- Tensors with three or more dimensions, like the [three-dimensional tensors used to represent RGB images](https://developer.ibm.com/articles/introduction-to-convolutional-neural-networks/) in computer vision algorithms, are collectively referred to as *N-dimensional tensors*.

PyTorch tensors function similarly to the *ndarrays* used in NumPy—but unlike ndarrays, which can only run on central processing units (CPUs), tensors can also run on [graphics processing units (GPUs)](https://www.ibm.com/cloud/gpu). GPUs enable dramatically faster computation than CPUs, which is a major advantage given the massive volumes of data and parallel processing typical to deep learning.

In addition to encoding a model’s inputs and outputs, PyTorch tensors also encode model parameters: the weights, biases and gradients that are “learned” in machine learning. This property of tensors enables automatic differentiation, which is one of PyTorch’s most important features.

### Modules

PyTorch uses modules as the building blocks of deep learning models, which allows for the quick and straightforward construction of neural networks without the tedious work of manually coding each algorithm.

Modules can—and often do—contain other nested modules. In addition to enabling the creation of more elaborate multi-layer neural networks, this also allows these complex deep learning models to be easily saved as a single named module and transferred between different machines, CPUs or GPUs. PyTorch models can even be run in non-Python environments, like C++, using [Torchscript](https://pytorch.org/tutorials/beginner/Intro_to_TorchScript_tutorial.html), helping bridge the gap between research prototypes and production deployment.

Broadly speaking, there are three primary classes of modules used to build and optimize deep learning models in PyTorch:

- **nn modules** are deployed as the layers of a neural network. The *torch.nn* package contains a large library of modules that perform common operations like [convolutions](https://developer.ibm.com/articles/introduction-to-convolutional-neural-networks/), pooling and regression. For example, *torch.nn.Linear(n,m)* calls a [linear regression](https://www.ibm.com/think/topics/linear-regression) algorithm with n inputs and m outputs (whose initial inputs and parameters are then established in subsequent lines of code).
- The **autograd module** provides a simple way to automatically compute gradients, used to optimize model parameters via [gradient descent](https://www.ibm.com/think/topics/gradient-descent), for any function operated within a neural network. Appending any tensor with *requires_grad=True* signals to autograd that every operation on that tensor should be tracked, which enables automatic differentiation.
- **Optim modules** apply optimization algorithms to those gradients. *Torch.optim* provides modules for various optimization methods, like stochastic gradient descent (SGD) or root mean square propagation (RMSprop), to suit specific optimization needs.

### Dynamic computation graphs

Dynamic computation graphs (DCGs) are how deep learning models are represented in PyTorch. Abstractly speaking, computation graphs map the flow of data between the different operations in a mathematical system: in the context of deep learning, they essentially translate a neural network’s code into a flowchart indicating the operations performed at each node and the dependencies between different layers in the network—the arrangement of steps and sequences that transform input data into output data.

What differentiates dynamic computation graphs (like those used in PyTorch) from static computation graphs (like those used in TensorFlow) is that DCGs defer the exact specification of computations and relationships between them until run time. In other words, whereas a static computation graph requires the architecture of the entire neural network to be fully determined and compiled in order to run, DCGs can be iterated and modified on the fly.

This makes DCGs particularly useful for debugging and prototyping, as specific portions of a model’s code can be altered or run in isolation without having to reset the entire model—which, for the very large deep learning models used for sophisticated computer vision and NLP tasks, can be a waste of both time and computational resources. The benefits of this flexibility extend to model training, as dynamic computation graphs are easily generated in reverse during backpropagation.

While their fixed structure can empower greater computational efficiency, static computational graphs have limited flexibility: for example, building a model that uses a varying number of layers depending on the input data—like a [convolutional neural network (CNN)](https://www.ibm.com/think/topics/convolutional-neural-networks) that can process images of different sizes—is prohibitively difficult with static graphs.

### Automatic differentiation

One extensively used method for training neural networks, particularly in [supervised learning](https://www.ibm.com/think/topics/supervised-learning), is *backpropagation*. First, in a forward pass, a model is fed some inputs (*x*) and predicts some outputs (*y*); working backwards from that output, a loss function is used to measure the error of the model’s predictions at different values of *x*. By differentiating that loss function to find its derivative, [gradient descent](https://www.ibm.com/think/topics/gradient-descent) can be used to adjust weights in the neural network, one layer at a time.

PyTorch’s autograd module powers its automatic differentiation technique using a calculus formula called *the chain rule*, calculating complex derivatives by splitting them into simpler derivates and combining them later. Autograd automatically calculates and records gradients for all operations executed in a computational graph, greatly reducing the legwork of backpropagation.

When running a model that has already been trained, autograd becomes an unnecessary use of computational resources. Appending any tensor operation with *requires_grad=False* will signal PyTorch to stop tracking gradients.

### Datasets and dataloaders

Working with the large datasets required to train deep learning models can be complex and computationally demanding. PyTorch provides two data primitives, datasets and dataloaders, to facilitate data loading and make code more easily readable.

- *torch.utils.data.Dataset* stores data samples and their corresponding labels
- *torch.utils.data.Dataloader* wraps an iterable—an object that can be operated upon—around the dataset to enable easy access to samples

## PyTorch ecosystem

PyTorch’s core features are supplemented by [a robust ecosystem of tools, libraries and extensions](https://pytorch.org/ecosystem/) developed by members of the PyTorch community. Many additional open source libraries, containing purpose-specific modules, pre-configured neural networks and even pre-trained models, are available to supplement the pre-installed torch library.

Torchvision is a toolkit containing modules, network architectures and datasets for various image classification, object detection and image segmentation tasks.

TorchText provides resources like datasets, basic text-processing transformations and pre-trained models for use in NLP.

The Open Neural Network Exchange (ONNX) ensures interoperability between AI frameworks, allowing users to easily transition their PyTorch models onto other platforms.

Many helpful tutorials are available at PyTorch.org. For example, this [intermediate tutorial](https://pytorch.org/tutorials/intermediate/mario_rl_tutorial.html) teaches the fundamentals of deep reinforcement learning by training an AI to play a video game.

## Installing and running PyTorch

PyTorch can be installed and run in different configurations on both local systems and cloud platforms.

Running PyTorch locally requires installing Python, using either the Anaconda package manager, [Homebrew](https://brew.sh/) or the [Python website](https://www.python.org/downloads/macos/).

PyTorch can be locally installed via [Anaconda](https://www.anaconda.com/download/#macos) using the command conda install pytorch torchvision -c pytorch, or via [pip](https://pypi.org/project/pip/) using the command pip3 install torch torchvision. Anaconda is recommended, as it provides all PyTorch dependencies (including Python) in one sandboxed install.<sup>2</sup>

PyTorch can also be run on cloud platforms, including Amazon Web Services, Google Cloud and Microsoft Azure.

It is recommended (but not required) to work with NVIDIA GPUs in order to take advantage of PyTorch’s support for CUDA (Compute Unified Device Architecture), which offers dramatically faster training and performance than can be delivered by CPUs.

## Footnotes

<sup>1</sup> [Octoverse 2022: The top programming languages](https://octoverse.github.com/2022/top-programming-languages), Github, 17 November 2022  
 <sup>2 </sup>[PyTorch: Get Started – Start Locally](https://pytorch.org/get-started/locally/)
