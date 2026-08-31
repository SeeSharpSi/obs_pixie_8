---
title: What is a recurrent neural network (RNN)?
source: https://www.ibm.com/think/topics/recurrent-neural-networks
author:
- '[[Cole Stryker]]'
published: 2024-12-02
created: 2026-08-31
description: "Recurrent neural networks (RNNs) use sequential data to solve common temporal problems seen in language translation and speech recognition."
---

## What is a recurrent neural network?

A recurrent neural network or RNN is a deep [neural network](https://www.ibm.com/topics/neural-networks) trained on sequential or time series data to create a [machine learning (ML)](https://www.ibm.com/topics/machine-learning) model that can make sequential predictions or conclusions based on sequential inputs.

An RNN might be used to predict daily flood levels based on past daily flood, tide and meteorological data. But RNNs can also be used to solve ordinal or temporal problems such as language translation, [natural language processing (NLP)](https://www.ibm.com/topics/natural-language-processing), [sentiment analysis](https://www.ibm.com/topics/sentiment-analysis), [speech recognition](https://www.ibm.com/topics/speech-recognition) and image captioning.

## How RNNs work

Like traditional neural networks, such as feedforward neural networks and [convolutional neural networks (CNNs)](https://www.ibm.com/topics/convolutional-neural-networks), recurrent neural networks use training data to learn. They are distinguished by their “memory” as they take information from prior inputs to influence the current input and output.

While traditional [deep learning](https://www.ibm.com/topics/deep-learning) networks assume that inputs and outputs are independent of each other, the output of recurrent neural networks depend on the prior elements within the sequence. While future events would also be helpful in determining the output of a given sequence, unidirectional recurrent neural networks cannot account for these events in their predictions.

Let’s take an idiom, such as “feeling under the weather,” which is commonly used when someone is ill to aid us in the explanation of RNNs. For the idiom to make sense, it needs to be expressed in that specific order. As a result, recurrent networks need to account for the position of each word in the idiom, and they use that information to predict the next word in the sequence.

Each word in the phrase "feeling under the weather" is part of a sequence, where the order matters. The RNN tracks the context by maintaining a hidden state at each time step. A feedback loop is created by passing the hidden state from one-time step to the next. The hidden state acts as a memory that stores information about previous inputs. At each time step, the RNN processes the current input (for example, a word in a sentence) along with the hidden state from the previous time step. This allows the RNN to "remember" previous data points and use that information to influence the current output.

Another distinguishing characteristic of recurrent networks is that they share parameters across each layer of the network. While feedforward networks have different weights across each node, recurrent neural networks share the same weight parameter within each layer of the network. That said, these weights are still adjusted through the processes of backpropagation and [gradient descent](https://www.ibm.com/topics/gradient-descent) to facilitate reinforcement learning.

Recurrent neural networks use forward propagation and backpropagation through time (BPTT) algorithms to determine the gradients (or derivatives), which is slightly different from traditional backpropagation as it is specific to sequence data. The principles of BPTT are the same as traditional [backpropagation](https://www.ibm.com/think/topics/backpropagation), where the model trains itself by calculating errors from its output layer to its input layer. These calculations allow us to adjust and fit the parameters of the model appropriately. BPTT differs from the traditional approach in that BPTT sums errors at each time step whereas feedforward networks do not need to sum errors as they do not share parameters across each layer.

![Three diagrams quickly explaining what Recurrent Neural Networks are](https://assets.ibm.com/is/image/ibm/what-are-recurrent-neural-networks-combined?ts=1763386631553&dpr=off)   Feedforward vs recurrent neural networks

## Common activation functions

An activation function is a mathematical function applied to the output of each layer of neurons in the network to introduce nonlinearity and allow the network to learn more complex patterns in the data. Without activation functions, the RNN would simply compute linear transformations of the input, making it incapable of handling nonlinear problems. Nonlinearity is crucial for learning and modeling complex patterns, particularly in tasks such as NLP, time-series analysis and sequential data prediction.

The activation function controls the magnitude of the neuron’s output, keeping values within a specified range (for example, between 0 and 1 or -1 and 1), which helps prevent values from growing too large or too small during the forward and backward passes. In RNNs, activation functions are applied at each time step to the hidden states, controlling how the network updates its internal memory (hidden state) based on current input and past hidden states.

Common activation functions (pictured after this) include:

**The Sigmoid Function** is to interpret the output as probabilities or to control gates that decide how much information to retain or forget. However, the sigmoid function is prone to the vanishing gradient problem (explained after this), which makes it less ideal for deeper networks.

**The Tanh (Hyperbolic Tangent) Function**, which is often used because it outputs values centered around zero, which helps with better gradient flow and easier learning of long-term dependencies.

**The ReLU (Rectified Linear Unit)** might cause issues with exploding gradients due to its unbounded nature. However, variants such as Leaky ReLU and Parametric ReLU have been used to mitigate some of these issues.

For a closer look at how RNNs work, view our [recurrent neural networks deep dive](https://developer.ibm.com/articles/cc-cognitive-recurrent-neural-networks).

![Diagram of different activation functions used in RNNs ](https://assets.ibm.com/is/image/ibm/two-dimensional-coordinate-system?ts=1763386631798&dpr=off)   Sigmoid, tanh and ReLU

## Types of RNNs

Feedforward networks map inputs and outputs one-to-one, and while we’ve visualized recurrent neural networks in this way in the diagrams before this, they do not have this constraint. Instead, their inputs and outputs can vary in length, and different types of RNNs are used for different use cases, such as music generation, sentiment classification and machine translation. Popular recurrent neural network architecture variants include:

- Standard RNNs
- Bidirectional recurrent neural networks (BRRNs)
- Long short-term memory (LSTM)
- Gated recurrent units (GNUs)
- Encoder-decoder RNN

![Y and X values in a graph](https://assets.ibm.com/is/image/ibm/recurrent-and-feedforward-neural-networks-one-many?ts=1763386632098&dpr=off)   Different types of RNNs

### Standard RNNs

The most basic version of an RNN, where the output at each time step depends on both the current input and the hidden state from the previous time step, suffers from problems such as vanishing gradients, making it difficult for them to learn long-term dependencies. They excel in simple tasks with short-term dependencies, such as predicting the next word in a sentence (for short, simple sentences) or the next value in a simple time series.

RNNs are good for tasks that process data sequentially in real time, such as processing sensor data to detect anomalies in short time frames, where inputs are received one at a time and predictions need to be made immediately based on the most recent inputs.

### Bidirectional recurrent neural networks (BRNNs)

While unidirectional RNNs can only be drawn from previous inputs to make predictions about the current state, bidirectional RNNs or BRNNs, pull in future data to improve the accuracy of it. Returning to the example of “feeling under the weather”, a model based on a BRNN can better predict that the second word in that phrase is “under” if it knows that the last word in the sequence is “weather.”

### Long short-term memory (LSTM)

LSTM is a popular RNN architecture, which was introduced by Sepp Hochreiter and Juergen Schmidhuber as a solution to the vanishing gradient problem. This work addressed the problem of long-term dependencies. That is, if the previous state that is influencing the current prediction is not in the recent past, the RNN model might not be able to accurately predict the current state.

As an example, let’s say we wanted to predict the italicized words in, “Alice is allergic to nuts. She can’t eat *peanut butter*.” The context of a nut allergy can help us anticipate that the food that cannot be eaten contains nuts. However, if that context was a few sentences prior, then it would make it difficult or even impossible for the RNN to connect the information.

To remedy this, LSTM networks have “cells” in the hidden layers of the artificial neural network, which have 3 gates: an input gate, an output gate and a forget gate. These gates control the flow of information that is needed to predict the output in the network. For example, if gender pronouns, such as “she”, was repeated multiple times in prior sentences, you might exclude that from the cell state.

### Gated recurrent units (GRUs)

A GRU is similar to an LSTM as it also works to address the short-term memory problem of RNN models. Instead of using a “cell state” to regulate information, it uses hidden states, and instead of 3 gates, it has 2: a reset gate and an update gate. Similar to the gates within LSTMs, the reset and update gates control how much and which information to retain.

Because of its simpler architecture, GRUs are computationally more efficient and require fewer parameters compared to LSTMs. This makes them faster to train and often more suitable for certain real-time or resource-constrained applications.

### Encoder-decoder RNNs

These are commonly used for sequence-to-sequence tasks, such as machine translation. The encoder processes the input sequence into a fixed-length vector (context), and the decoder uses that context to generate the output sequence. However, the fixed-length context vector can be a bottleneck, especially for long input sequences.

## Limitations of RNNs

RNN use has declined in artificial intelligence, especially in favor of architectures such as [transformer models](https://www.ibm.com/topics/transformer-model), but RNNs are not obsolete. RNNs were traditionally popular for sequential data processing (for example, time series and language modeling) because of their ability to handle temporal dependencies.

However, RNNs’ weakness to the vanishing and exploding gradient problems, along with the rise of transformer models such as BERT and GPT have resulted in this decline. Transformers can capture long-range dependencies much more effectively, are easier to parallelize and perform better on tasks such as NLP, speech recognition and time-series [forecasting](https://www.ibm.com/think/topics/forecasting).

That said, RNNs are still used in specific contexts where their sequential nature and memory mechanism can be useful, especially in smaller, resource-constrained environments or for tasks where data processing benefits from step-by-step recurrence.

For those who want to experiment with such use cases, Keras is a popular open source library, now integrated into the TensorFlow library, providing a Python interface for RNNs. The API is designed for ease of use and customization, enabling users to define their own RNN cell layer with custom behavior.
