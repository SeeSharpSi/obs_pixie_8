---
title: What is long short-term memory (LSTM)?
source: https://www.ibm.com/think/topics/lstm
author:
- '[[Joshua Noble]]'
published: 2025-12-16
created: 2026-08-31
description: "A long short-term memory architecture (LSTM) is a special type of recurrent neural network (RNN) designed to learn and remember information over long sequences of data."
---

## What is long short-term memory (LSTM)?

A long short-term memory architecture (LSTM) is a special type of [recurrent neural network](https://www.ibm.com/think/topics/recurrent-neural-networks) (RNN) designed to learn and remember information over long sequences of data.

Humans don’t restart their thoughts every second; those thoughts have persistence and build upon one another. That’s how people can read an explainer like this one and understand each word in sequence to create a longer coherent thought and build those into coherent knowledge. Neither traditional neural networks nor classic machine learning architectures do this; they can’t reason about previous events to inform later events. That makes working with linear data like a time series or text very difficult. RNNs address this issue by using a [deep learning](https://www.ibm.com/think/topics/deep-learning) network architecture that contains loops which allow information to persist from one inference to the next.

Some of the most common applications of LSTM networks have been in natural language processing (NLP) and time series analysis. Other applications include [speech recognition](https://www.ibm.com/think/topics/speech-recognition): many early voice assistants used LSTMs to transcribe spoken language into text, and in [machine translation](https://www.ibm.com/think/topics/machine-translation), where LSTM were once widely used for sentiment analysis and language modeling (now mostly replaced by transformer models). In [time-series forecasting](https://www.ibm.com/think/topics/time-series-model), LSTMs are still widely used for predicting future values in sequential data like stock prices and weather patterns. In healthcare, time series data can be analyzed to predict disease progression and treatment outcomes.

Since LSTMs are an extension of an RNN, it’s easiest to understand them through their predecessor.

## Recurrent neural networks

Recurrent neural networks are a model architecture that focuses on learning from and predicting sequential data. They are different from other types of deep learning networks because they take information from prior inputs to influence how the current input is interpreted and what they should output.  

 Most deep learning networks assume that inputs and outputs are independent of each other and that information only flows forward as the network learns. An RNN on the other hand passes information about the previous state and the current input to each new node in the network. This architecture allows the model capture the information from previous steps and utilize it in the current step, enabling model to learn temporal dependencies and handle input of variable length.

Simple RNNs have long-term memory in the form of weights. Those weights change slowly during training, encoding general knowledge about the data. They also have short-term memory in the form of ephemeral activations, which pass from each node to successive nodes.

![A recurrent neural network passes data backwards through hidden layers](https://assets.ibm.com/is/image/ibm/rnn?ts=1785938362506&dpr=off)   A recurrent neural network passes data backwards through hidden layers

There is a key issue with RNNs though. During the backpropagation process, the gradients being backpropogated can become too small, leading to the vanishing gradient problem, or too large, resulting in the exploding gradient problem. A vanishing gradient is when the gradient becomes too small to allow the network to calculate effecitvely. This stalls out the training process and makes it very slow. The opposite problem, called the exploding gradient problem, can lead to numerical instability during training which can cause the model to deviate from an optimal solution. Taken to the extreme, the values of weights can get so large as to overflow the bytes available for a number and result in non-numeric values and other unspecified behavior. The “explosion” occurs through exponential growth by repeatedly multiplying gradients through the network layers with values greater than 1.0.

These issue with RNNs and other architectures have been known since the early 1990s and they prompted researchers to develop LSTMs as a response to them.

## How LSTMs work

![Each LSTM cell contains multiple gates that modify the memory and cell output](https://assets.ibm.com/is/image/ibm/lstm_architecture?ts=1785938362877&dpr=off)   Each LSTM cell contains multiple gates that modify the memory and cell output

LSTMs are a special kind of RNN, capable of learning long-term dependencies. They were introduced by Hochreiter & Schmidhuber in 1997, and were refined and popularized in subsequent work. They work tremendously well on a large variety of problems and are now used widely in time series forecasting and in some kinds of sequential data prediction problems. LSTMs are explicitly designed to avoid the long-term dependency problem. Remembering information for long periods of time is their default behavior.

An LSTM looks at some input $X_t$ and outputs a value $H_t$ . A loop allows information to be passed from one step of the network to the next. In theory, traditional RNNs are capable of handling these kinds of long-term dependencies. A human could carefully pick parameters for them to solve toy problems of this form. RNNs unfortunately aren’t able to learn them.

LSTMs are similar to many other kinds of feed-forward neural networks but they have several crucial differences. The LSTM model introduces an intermediate type of storage with a structure that’s called a memory cell. A memory cell is a composite kind of unit built from simpler nodes, the most important of which is a multiplicative node.

The multiplicative nodes in an LSTM memory cell function like gates that control the flow of information through the network. They enable the network to decide how much of each signal from the input data should pass through. There are three main places where these multiplicative interactions occur. An LSTM cell contains three gates and one cell state.

The **forget gate** multiplies the previous cell state by another value between 0 and 1, deciding how much information from the previous time step to retain or discard.

$$ f_t = \sigma(W_f h_{t-1}, x_t + b_f) $$

The **input gate** multiplies the candidate cell state by a value produced by a sigmoid function as the activation function, between 0 and 1, determining how much new information from the current input to add to the memory.

$$ i_t = \sigma(W_i h_{t-1}, x_t + b_i) $$

The input gate then generates a new candidate cell state:

$$ \hat{C}*t = \tanh(W_C h*{t-1}, x_t + b_C) $$

The cell state update $C_t$ is updated by the long-term memory:

$$ C_t = f_t * C_{t-1} + i_t * \tilde{C}_t $$

Finally, the **output gate** multiplies the updated cell state (after passing through a tanh) by a gating value to determine what part of the internal state becomes visible as output $o_t$ and a new hidden state $h_t$ :

$$ o_t = \sigma(W_o h_{t-1}, x_t + b_o) $$

$$ h_t = o_t * \tanh(C_t) $$

The multiplicative operations at each gate enable the LSTM to regulate information dynamically. That protects long-term dependencies from being overwritten or vanishing.

LSTMs resemble standard recurrent neural networks but here each ordinary recurrent node is replaced by a memory cell. Each memory cell contains an internal state, i.e., a node with a self-connected recurrent edge of fixed weight 1, ensuring that the gradient can pass across many time steps without vanishing or exploding.

### How LSTMs learn patterns

Think of an LSTM that has is learning how to predict the air temperature tomorrow for a specific city or area. That network has already seen one month of data and now is adding a new reading in celsius of 30 (that’s 86 in Fahrenheit). The newest reading can be designated $C_t$ . The LSTM now has a cell state $C_{t-1}$ that carries long-term context (like the overall seasonal trend for this time of year) and a hidden state $h_{t-1}$ that carries short-term patterns (like daily fluctuation that happens between night temperatures and day temperatures).  

 The LSTM first computes a forget gate value $f_t = \sigma(Wf·[h_{t-1}, x_t] + bf)$ . While that result will depend on the values that were calculated and stored in the memory cell, let’s say that the result is $f_t = 0.8$ . That indicates that the cell will keep 80% of the previous memory and forget 20%. For example if $c_{t-1} = 10$ (representing a learned “warm trend”), the contribution becomes 0.8 × 10 = 8.  

 Next the LSTM uses the input gate. The network computes $i_t = \sigma (Wi·[h_{t-1}, x_t] + bi)$ . Suppose $i_t$ = 0.3. This controls how much of the new information gets added to the memory unit. The LSTM also computes a candidate value $\hat{c}_t = tanh(Wc·[h_{t-1}, x_t] + bc)$ . Suppose $\hat{c}_t$ = 5. The input gate then multiplies these: $i_t * \hat{c}_t = 0.3 × 5 = 1.5$ . So 1.5 units of new information are allowed into the memory.  

 Next, the LSTM updates the cell state. The new cell state combines the remembered old state and the gated new input:  
 $c_t = (f_t × c_{t-1}) + (i_t × \hat{c}_t) = 8 + 1.5 = 9.5$ . The LSTM now “remembers” a slightly stronger warm trend.  

 Finally the LSTM uses the output gate. The LSTM decides what part of that memory to expose as output.

$o_t = \sigma(Wo·[h_{t-1}, x_t] + bo)$ . Suppose $o_t$ = 0.6. The hidden state becomes $h_t = o_t × tanh(c_t) = 0.6 × tanh(9.5) = 0.6$ .

This value (0.6) is what the LSTM passes on to the next time step or to the prediction layer.  

 In processing one new temperature reading, the forget gate preserved most of the prior warm trend. The input gate modestly incorporated new data (today’s 30 degrees celsius). Then the output gate controlled how much of this updated trend affects the prediction.  

 By repeating this process with each reading, the LSTM can gradually learn patterns like daily and weekly cycles as well as seasonal changes without losing earlier context that provides context for both the daily trends and the larger seasonal trends.

## LSTMs and transformers

LSTMs are similar to [transformer models,](https://www.ibm.com/think/topics/transformer-model) although transformers have largely replaced LSTMs in many modern applications. Both of these but grew out of the same problem space: how to model long-term dependencies in sequential data. Transformers are much more common in NLP applications like machine translation, [automated summarization](https://www.ibm.com/think/topics/text-summarization), or text generation.   

 LSTMs compute an output recursively via hidden states:

$$ h_t = \textbf{LSTM}(x_t, h_{t-1}) $$

Transformers compute an output via [attention](https://www.ibm.com/think/topics/attention-mechanism) over all positions:

$$ \textbf{Attention}(Q,K,V) = \textbf{softmax}\left(\frac{QK^T}{\sqrt{d_k}}\right)V $$

Transformers typically perform better in long-range modeling and parallelization of tasks than an LSTM architecture. However, that doesn’t mean that LSTMs are obsolete. They are often times more data-efficient, require lower memory, and able to create predictions or inferences in real-time. LSTMs also often perform better with smaller datasets and noisy data than transformers as well.  

 Because an LSTM processes data sequentially, one time step at a time, LSTMs have an explicit notion of time and order. The downside of this is that computations can’t be parallelized across time steps.  

 A transformer processes all tokens in parallel using self-attention, rather than recurrence. Contextual relationships are determined by how each token “attends” to every other token. Position information is added via positional encodings, since the model itself doesn’t process inputs sequentially. That means Transformers can use massive parallelism and have direct modeling of long-range dependencies but also that they may not have proper sequential information of data like times, dates, or strict sequencing.  

 You may think of an LSTM like carefully reading a book word by word, remembering what came before, and piecing together more meaning with each word that you read. A transformer on the other hand, is like looking at the whole page at once and understanding how all words relate to one another simultaneously, ignoring some words and giving a lot of weight to others.
