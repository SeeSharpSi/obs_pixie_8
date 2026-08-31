---
title: What is a GNN (graph neural network)?
source: https://www.ibm.com/think/topics/graph-neural-network
author:
- '[[Joshua Noble]]'
published: 2025-02-19
created: 2026-08-31
description: "Graph neural networks are a deep neural network architecture that represents data about entities and their relationships. They’re useful for real-world data mining, understanding social networks, knowledge graphs, recommender systems and bioinformatics."
---

## Introducing GNNs

Graph neural networks (GNNs) are a deep neural network architecture that is popular both in practical applications and cutting-edge [machine learning](https://www.ibm.com/think/topics/machine-learning) research. They use a neural network model to represent data about entities and their relationships. They’re useful for real-world [data mining](https://www.ibm.com/think/topics/data-mining), understanding social networks, [knowledge graphs](https://www.ibm.com/think/topics/knowledge-graph), recommender systems and bioinformatics.

The development of GNNs drew inspiration from deep learning algorithms such as [convolutional neural networks](https://www.ibm.com/think/topics/convolutional-neural-networks) (CNNs) and [recurrent neural networks](https://www.ibm.com/think/topics/recurrent-neural-networks) (RNNs) but they have several key differences. CNNs are designed for data that has a grid-like structure like the pixels of an image. Any one pixel can be connected to, at most, eight other pixels. Conversely, RNNs are tailored to sequence structures where each element can be connected to two other elements at most, like a string of words in a text. In graph-structured data though, any element can have one or more connections and might have no consistency between the numbers of connections for a specific element.

Graph neural networks are an implementation of geometric deep learning<sup>[1](#F1)</sup>, which is classified into four fundamental categories:

**Graph-based learning**, which learns about graph-like data.

**Grid-based learning**, which learns about data-like images and other data types that can be described by grids.

**Group-based learning**, which learns about how information relates to a parent group. This is powerful when data is acquired from a group like a sphere, for instance, geological data from different sources across the Earth.

**Mesh-based learning**, which learns about how information is spread across an irregular mesh, such as analyzing and predicting elements of a 3D model of an object.

GNNs are an area of active [artificial intelligence](https://www.ibm.com/think/topics/artificial-intelligence) research but are well supported by libraries and toolkits that are built in languages such as Python and frameworks including TensorFlow and PyTorch.

## What is a graph?

A set of objects and the connections between them can be expressed as a graph. Computer science researchers developed neural networks to operate on graph data structures.

A graph represents the relations, which are called ‘edges’ between a collection of entities, which are called ‘nodes.’ Mathematically, a graph *G* is defined as a tuple of a set of nodes and vertices *V*, and a set of edges and links. *E:G = (V, E)*. Each edge is a pair of two vertices and represents a connection between them.

To further describe each node, edge or the entire graph, we can store information in each of these pieces of the graph.

![An illustration showing the vertices of a graph and how they are connected by edges](https://assets.ibm.com/is/image/ibm/vertices_edge?ts=1785949151158&dpr=off)   The vertices (sometimes called nodes) of a graph are connected by edges

Graphs can be further described by assigning directionality with each edge. A graph is described as being either directed or undirected. An undirected graph represents a relationship, which is bidirectional. If Rosa has a sibling Juan, then Juan also has a sibling, Rosa. The relationship between Rosa and her sibling doesn’t have any directionality, it just connects them two of them. A directed graph represents relationships that are directional. If Rosa has an older sibling Juan, then the relationship ‘older sibling’ only goes one direction: from Juan to Rosa, Juan doesn’t have an ‘older sibling’.

![An illustration of an undirected graph and a directed graph](https://assets.ibm.com/is/image/ibm/directed_undirected_graph?ts=1785949151406&dpr=off)   The type of graph is determined by whether the edges have directionality or not

A way of visualizing the connectivity of a graph is through its adjacency matrix. This is a matrix-based representation of the vertices of the graph that can represent both undirected and directed graphs.

![A directed graph and an adjacency matrix of numbers that represent it](https://assets.ibm.com/is/image/ibm/adjacency-matrix-for-directed-and-unweighted-graph?ts=1785949151655&dpr=off)   The edges of a directed graph can be represented by an adjacency matrix

The adjacency matrix of a directed graph shown indicates all the vertices and the direction of the edge creating them. For instance, node 0 in the directed graph connects to node 1, but the inverse is not true because of the directionality of the connection. In the adjacency matrix, *[row 0, column 1]* contains a value, whereas *[row 1, column 0]*, does not.

Representations of graphs should have permutation invariance, which means that representations of the graph should produce the same results if the graph structure is the same but the node order is different. This approach ensures that the representation of the graph has the same properties as the graph itself.

## Graph neural networks

GNNs typically adopt a “graph-in, graph-out” architecture. This means that these model types accept a graph as input, with information loaded into its nodes, edges and global context. The models progressively transform these embeddings without changing the connectivity of the input graph. Embeddings represent the nodes as node embeddings, and the vertices as vertex embeddings. These embeddings allow the model to learn what types of nodes occur and where in the graph as well as the types and locations of edges.

Typically, training a neural network is done by updating the network parameters with gradients that are calculated on a randomized subset of the training data. To train graph networks, graph neural networks to create subgraphs that preserve essential properties of the parent large graph.

GNNs use a message-passing mechanism to aggregate information from neighboring nodes, allowing them to capture the complex relationships in graphs. A challenge in modeling graph-structured data is capturing the interactions among the nodes. Neural message passing addresses this challenge by providing a framework for modeling dependencies and interactions in graph data. Nodes exchange information with their neighboring nodes and aggregate that information to update their own representations. This message passing process is similar to nodes in a graph exchanging messages or signals.

## Types of graph analysis

GNNs allow for several different types of analysis, each of which provides insights into different elements of graph data.

**Graph-level tasks**

In a graph-level task, the GNN predicts a property of an entire graph. For a molecule represented as a graph, you might want to predict whether it will bind to a receptor associated with a disease. For a social network, you might want to predict whether they’re likely to be associated with a particular institution such as a university or college. This type of pattern recognition can be framed as a form of graph classification because it classifies the entire graph.

**Node-level tasks**

Node-level tasks are concerned with predicting the identity or role of each node within a graph. For instance, a node classification problem in a social network dataset might be to predict whether a user is likely to have a specific interest based on their friend network is connected. Having friends who only share an interest in golf but no other interests in common is a good indication that a new friend might also be likely to enjoy golf. These kinds of node features can often be predicted with a GNN.

**Edge-level tasks**

The final type of prediction problem in graphs is edge prediction, sometimes called link-prediction.

One example of edge-level inference is in image scene understanding. After identifying objects in an image, deep learning models can also predict the relationship between them. This is an edge-level classification because the nodes represent the objects in the image and the prediction indicates which of these nodes share an edge or what the value of that edge is. If you want to discover connections between entities, you might consider the graph as being ‘fully connected’ and based on their predicted value, prune edges to arrive at a sparse graph.

## Variants and extensions

Graph convolutional networks<sup>[4](#F4)</sup> (GCNs): This approach is for semisupervised learning based on a variant of convolutional neural networks that can learn and predict from graph-based data. These models scale linearly in the number of graph edges, making it suitable for large datasets. The models also learn local graph structure and the features of nodes.

Graph autoencoders<sup>[2](#F2)</sup>: These variants are end-to-end trainable neural network models for unsupervised learning, clustering and link prediction on graphs. They typically use a GCN as an encoder to create embeddings and have a decoder that reconstructs the graph from the learned latent representation.

Graph attention networks<sup>[3](#F3)</sup> (GAT): A neural network architecture that operates on graph-structured data. GATs leverage an attention mechanism in the form of self-attention layers to address the shortcomings of prior methods based on graph convolutions or their approximations. By stacking layers in which nodes can attend over their neighborhoods’ features, a GAT enables (implicitly) specifying different weights to different nodes in a neighborhood. This is possible without requiring costly matrix operations such as inversion or depending on knowing the graph structure upfront.

Graph representation: Learning is an area of research that extends graph neural networks as a way to find a meaningful, potentially low-dimensional representation of nodes from the complex relations present in a graph. An example of this extension is GraphSage<sup>[6](#F6)</sup>, a project from Stanford University, which creates low-dimensional vector representations for nodes, making it suitable for working with data where nodes represent high-dimensional data.

## GNN architectures

As a sample of how a GNN can be structured, consider a simple graph convolutional network (GCN) for classifying an entire graph. The simplest GCN has three layers:

**Convolutional layer**—this layer performs the convolution on each node to learn its connections.

**Nonlinear activation layer**—this layer applies an activation function such as ReLU to the output of the convolution.

**Output linear layer**—this final layer sums the outputs to generate a final prediction.

First, a convolution is performed by using each node in the convolution layer graph. This convolutional layer uses feature information from the neighbors of each node and aggregates it, updating the weights associated with each node. Then, a nonlinear activation function, such as ReLU, is applied to the output of the convolution layer. To get to the best accuracy, a network can use multiple convolutions and nonlinear activation layers stacked together. Finally, an output linear layer is used to predict which class a graph is most likely to belong to.

GCNs are conceptually simple, suitable for large-scale graphs and easy to program but have several key drawbacks as well. For one, GCNs do not support edge features. They can only learn and predict node features or overall graph features. The notion of message passing doesn’t exist with GCNs. This issue restricts its usage to only those cases where all required information is present in the nodes rather than existing in the edges.

A message passing neural network (MPNN) however, allows for representations of edges.<sup>[5](#F5)</sup> The process of messaging passing is, roughly, as follows. Each node in the graph receives an initial embedding that acts as the node’s initial input features. At each iteration of message passing, the node aggregates information from its neighboring nodes. That aggregated information is then combined with the node’s current embedding by using an update function. The updated embeddings are passed to the next iteration of message passing. After several iterations suitable to represent the complexity of the graph, the final embeddings are used to represent each node in the graph. Finally, aggregation, update and iteration steps are performed by neural networks to learn complex patterns in the graph overall.

Using message passing allows for more sophisticated node classification, classification of edges or even prediction of where edges might appear in the graph (called link prediction).

## Applications of GNNs

GNNs have many applications in natural language processing (NLP). For example, in document classification GNNs can be used to model the relationships between words or sentences in documents. This ability enables improved document classification and information retrieval. GNNs can help in question-answering tasks by representing the relationships between words in a question and candidate answers within a knowledge graph. GNNs can capture contextual information and sentiment dependencies in text, improving sentiment analysis in situations with high ambiguity or highly specific entity relationships.

They also have many applications in computer vision. In image segmentation tasks, GNNs can be employed for pixel-level image segmentation tasks by modeling the relationships between adjacent pixels as a graph. GNNs can assist in object detection by capturing contextual information and relationships between objects in images. In scene understanding tasks, GNNs are used for understanding complex scenes and scene graph generation that represents the spatial relationships between objects in an image.

GNNs are powerful tools in bioinformatics as well. In genomic sequence analysis, GNNs can model relationships between genes or genetic sequences, helping in gene expression prediction and sequence classification tasks. In drug discovery, GNNs can be used for drug-target interaction prediction and molecular property prediction, which is vital in pharmaceutical research.

## Footnotes

1. Inductive representation learning on large graphs, Will Hamilton, Zhitao Ying, Jure Leskovec, [https://papers.nips.cc/paper_files/paper/2017/hash/5dd9db5e033da9c6fb5ba83c7a7ebea9-Abstract.html](https://papers.nips.cc/paper_files/paper/2017/hash/5dd9db5e033da9c6fb5ba83c7a7ebea9-Abstract.html)

2. Variational Graph Auto-Encoders, Thomas N. Kipf, Max Welling [https://arxiv.org/abs/1611.07308](https://arxiv.org/abs/1611.07308)

3. Graph Attention Networks; Petar Veličković, et al, [https://arxiv.org/abs/1710.10903](https://arxiv.org/abs/1710.10903)

4. Semi-Supervised Classification with Graph Convolutional Networks, Thomas N. Kipf, Max Welling [https://arxiv.org/abs/1609.02907](https://arxiv.org/abs/1609.02907)

5. Hierarchical Graph Representation Learning with Differentiable Pooling, NeurIPS 2018 · Rex Ying, et al [https://arxiv.org/abs/1806.08804](https://arxiv.org/abs/1806.08804)

6. GraphSage [https://snap.stanford.edu/graphsage/](https://snap.stanford.edu/graphsage/)
