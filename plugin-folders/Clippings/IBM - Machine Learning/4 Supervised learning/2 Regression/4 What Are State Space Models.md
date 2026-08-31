---
title: What is a state space model?
source: https://www.ibm.com/think/topics/state-space-model
author:
- '[[Dave Bergmann]]'
published: 2025-07-07
created: 2026-08-31
description: "State space models (SSMs) are a class of machine learning algorithms used to make predictions about dynamic systems, adaptable to most sequence modeling tasks."
---

## What is a state space model (SSM)?

State space models (SSMs) are a class of [machine learning](https://www.ibm.com/think/topics/machine-learning) algorithms used to make predictions about dynamic systems by modeling how their internal state evolves over time through differential equations. Historically used in control systems engineering, SSMs are a remarkably flexible mathematical platform adaptable to most sequence modeling tasks. [Mamba](https://www.ibm.com/think/topics/mamba-model), an SSM-based [neural network](https://www.ibm.com/think/topics/neural-networks) architecture, rivals [transformers](https://www.ibm.com/think/topics/transformer-model) on language modeling performance.

State space models have their origins in control systems engineering, where they played a pivotal role in navigational calculations for the Apollo program in the 1960s.<sup>1</sup>[](#_ftn1) SSMs are also used prominently in electrical engineering, where they’re fundamental to signal processing, control theory and robotics. But perhaps the most important quality of SSMs is their versatility, especially for multiple-input, multiple-output systems.

Underpinning SSMs are two simple equations: one describes the internal dynamics of a system that aren’t directly observable, and the other describes how those internal dynamics relate to observable results. That simple, flexible formulation is extremely adaptable for a wide variety of multivariate [time series](https://www.ibm.com/think/topics/time-series-model) data.

In economics, SSMs can model how trends and seasonality affect stock prices. In neuroscience, they can map relationships between measurable brain signals (like fMRIs) and underlying neural activity. In ecology, SSMs can help model population dynamics, animal movement and capture-recapture data.<sup>2</sup>[](#_ftn2) SSMs are likewise leveraged in weather forecasting and other types of time series analysis.

In recent years, research on state space models has focused on their uses in [deep learning](https://www.ibm.com/think/topics/deep-learning), integrating neural networks as the [parameters](https://www.ibm.com/think/topics/model-parameters) of SSM equations. Most recently and notably, this has yielded the Mamba model architecture for [large language models (LLMs)](https://www.ibm.com/think/topics/large-language-models), which has been proven to match the performance capacity of transformer-based models while offering superior speed and efficiency.

## What is a state space?

The conditions of a system at any given moment are determined by the specific values of any number of system variables*.* The goal in effectively modeling the state space is to identify the smallest subset of system variables that are necessary to fully describe the system. This subset of system variables is called the *state variables.* The state space is the *n-dimensional* space whose axes (dimensions) are the state variables, containing all possible values for each of those *n* state variables.

Each of these *state variables* should be linearly independent: in other words, no one state variable can constitute a combination (by addition or subtraction) of any other state variables.

The specific state of the system at any given time can be expressed as a *state vector*, in which each element of the [vector](https://www.ibm.com/think/topics/vector-embedding) represents the value of its corresponding state variable. The state vector has the same number of dimensions as the state space itself. A given state vector can be understood as a set of specific “coordinates” in state space.

### Intuitive state space examples

Imagine a toy car moving along a straight track at constant velocity. The state space can be modeled with 2 state variables: the car’s position (measured in distance from the starting line) and its velocity. The state of the system at any time t can therefore be expressed as a 2-dimensional state vector [*position<sub>t</sub>, velocity*<sub>t</sub>]. In this simple system, if you know the car’s precise position and velocity at a given moment—its current state—you can predict where it will be in the next moment.

Velocity itself combines 2 *system* variables: speed and direction. Because the car is moving along a straight track, it’s possible to simply represent backwards movement as negative velocity and forward movement as positive velocity. But it’s possible, albeit inefficient, to replace the single state variable of velocity with the 2 state variables of speed and direction.

If the toy car were moving through an open field instead of a straight track, the state space would now be 4-dimensional, because the car’s position and its movement each require at least 2 dimensions to be fully described.

In practice, the “dimensions” of a state space rarely correspond to the familiar, easy-to-visualize dimensions of the physical world. For instance, consider a tic tac toe board. We could treat each of its 9 individual squares as a state variable—whose value could be “0” for blank, “1” for X and “2” for O—in a 9-dimensional state space. Any configuration of the board could be expressed in state space form as a 9-dimensional state vector.

## How do state space models work?

State space models aim to predict both how inputs into a system are reflected in its outputs and how the state of the system itself evolves over time and in response to specific inputs.

At each time *t,* an SSM takes an input sequence *x*(t) and maps it to both the current state *h*(t) and an output sequence *y*(t). The state *h*(t) is often referred to as the *latent state* because, unlike the system’s output, it’s not directly observable—that is, it’s [latent](https://www.ibm.com/think/topics/latent-space) (hidden).

The state space representation of a system is computed using 2 [first-order differential equations](https://www.youtube.com/watch?v=N2PpRnFqnqY):

#### **The** ***state equation,*** *$h'(t)=A*h(t)+B*x(t)$*    
 **The *output equation,*** *$y(t)=C*h(t)+D*x(t)$*

The key parameters of an SSM are A, B, C and D, which typically take the form of matrices. Each element of each matrix represents the relationship—expressed as a [first order derivative](https://www.ibm.com/think/topics/backpropagation#Key+mathematical+concepts+for+backpropagation)—of a state variable with respect to some other variable (such an external input variable, another state variable or itself). Using matrices makes state space methods a powerful and scalable tool for representing complex multi-input, multi-output (MIMO) systems in a compact and standardized format.

In [control theory](https://en.wikipedia.org/wiki/Control_theory) and related disciplines, these matrices are often defined directly: they represent the dynamics of an established system, and the SSM is used to find the inputs *x* that lead to desirable outputs *y* or optimal state *h.* In more modern conceptions of SSMs, those matrices are themselves parameters to be optimized through machine learning to best reflect the patterns in a [training dataset](https://www.ibm.com/think/topics/training-data). In deep learning models, this “parameterization” is represented by the learnable weights of a neural network.

### The state space equation

The state space equation (or simply *state equation*), as its name suggests, describes the state of the system as mediated by the A matrix and B matrix. In this notation, *h*(0) can be understood as the system’s initial state, *h*(t) is the latent state at time *t*, and *h’*(t)—the first order differential equation for h(t)—is the way that the state is changing at time *t.*

![Diagram of an SSM's state space equation](https://assets.ibm.com/is/image/ibm/mamba_state-space-equation_2_1ratio?ts=1778699607338&dpr=off)  The state equation. Illustration derived from Maarten Grootendorst's "A Visual Guide to Mamba and State Space Models"

To contextualize the abstract notions of differential equations and matrices, we can explore them through the lens of a simplified, intuitive example of a dynamic system in which the parameters A, B, C and D are already known.

For our example, imagine a small ecosystem on an isolated island that houses a population of fish and a population of pelicans that eat those fish. We can represent this system using 2 state variables: *$F$* (the number of fish) and *$P$* (the number of pelicans). Our goal is to define a function *$h'(t)$* that describes how the state *$h(t)$,* expressed as state vector $[F(t),P(t)]$ , is changing at time *t*.

#### The A matrix

The A matrix, also called the *transition matrix*, describes how the island’s ecosystem—as represented by those 2 state variables—evolves over time if left to itself. More specifically, it describes how the current state *h* influences the future state.

Let’s assume that the dynamics of the fish and pelican populations are very simple and constant:

- Left on its own, the fish population  *$F$* increases at a rate of 50%.
- Left on its own, the pelican population  *$P$* declines by 5%.
- Each pelican will eat 4 fish over that same time frame.
- For every 10 additional fish, the ecosystem can support 1 additional pelican.

We can now express each of these dynamics with simple equations and represent those equations in a matrix of size *n x n,* where *$n$ =* the number of state variables. Each column of our 2x2 A matrix represents a state variable and each row represents its rate of change—its first order derivative—with respect to each state variable. Italic annotations have been added for clarity.

$$ \begin{matrix}&Fish\ \left(F\right)&Pelicans\ \left(P\right)\\Changes_{to}Fish&\underline{0.5}&\underline{-4}\\Changes_{to}Pelicans&\underline{0.1}&\underline{-0.05}\\\end{matrix} $$

Because the rates of population change are constant in our simplified scenario, the elements of our A matrix are simple constants. Real-world scenarios often entail more state variables and more mathematically complex relationships between them—but the way those relationships are represented in the grid of their corresponding transition matrix A would be the same.

Assuming a complete absence of external influences, *h’(t)=A*h(t)* is sufficient to describe how the state of the island’s ecosystem evolves over time.

**$$ h'(t)=A*h(t) $$**

**$$ h'(t)=\begin{bmatrix} 0.5 & -4 \\ 0.1 & -0.05 \end{bmatrix}*h(t) $$**

$$ h'(t)=\begin{bmatrix} 0.5 & -4 \\ 0.1 & -0.05 \end{bmatrix} * \begin{bmatrix} F(t) \\ P(t) \end{bmatrix} $$

Solving this equation analytically entails calculating the [eigenvalues and eigenvectors](https://www.youtube.com/watch?v=PFDu9oVAE-g) of Matrix A, which is beyond the scope of this article. But it turns out that, left on its own, this ecosystem isn’t sustainable: the fish and pelican populations will each experience an interrelated and increasingly extreme cycle of boom and bust, eventually culminating in a catastrophic collapse.

#### The B matrix

What if there are also external factors influencing the ecosystem? The B matrix, also called the *input matrix,* informs the other half of the state equation, describing how a given input affects each state variable. It’s a matrix of size *n x m,* in which *n =* the number of state variables and *m* = the number of external *input variables*. The essence of control theory is to determine system inputs *x*(t) that achieve a desirable state or outcome for the overall system.

To further our island ecosystem example, we’ll add a single input variable: an airdrop of fish food *x* (measured in tons) at time *t*. Assume that each airdropped ton of fish food enables a further 30% increase in the fish population and has no effect on the pelican population.  

 Since we have 2 state variables and 1 input variable, we’ll capture them in a 2x1 input matrix. The top row of the B matrix will represent *F*, to match the A matrix.

$$ \begin{matrix} Change_{to}F \\
Change_{to}P \end{matrix} $$ $$ \begin{bmatrix} 
0.3 \\
0
\end{bmatrix} $$

We can now model state of the island ecosystem at time *t* using the full state equation:

$$ h'(t)=A*h(t)+B*x(t) $$$$ h'(t)=\begin{bmatrix} 0.5 & -4 \\ 0.1 & -0.05 \end{bmatrix}*h(t) + \begin{bmatrix} 0.3 \\ 0 \end{bmatrix}*x(t) $$

$$ h'(t)=\begin{bmatrix} 0.5 & -4 \\ 0.1 & -0.05 \end{bmatrix}h(t) + \begin{bmatrix} 0.3 \\ 0 \end{bmatrix}x(t) $$

In this instance, the goal would be to identify the optimal rules—typically represented by yet another matrix whose elements are functions of the state variables—for adding inputs *x(t)* to the ecosystem whenever the fish population is crashing, in order to stabilize the ecosystem.

### The output equation

As mentioned earlier, the purpose of the state equation is to describe the “hidden state” *h* that can’t be directly observed. SSMs assume the existence of some reflection of the true state that *is* directly observable—albeit potentially noisy or incomplete—and model it using the *output equation* (also called the *observation equation*)*.*

![Diagram of SSM's output equation](https://assets.ibm.com/is/image/ibm/mamba_output-equation_2_1ratio?ts=1778699610932&dpr=off)  The output equation. The state equation. Illustration derived from Maarten Grootendorst's "A Visual Guide to Mamba and State Space Models."

The same holds true for our simple ecosystem example: in reality, it’s probably impossible to literally count each and every individual fish and bird on an island. Instead, an ecological study might use aerial drones and underwater cameras to objectively survey *some* of the fish and pelican population, then make assumptions about how those measurements relate to the true state of the ecosystem.

#### The C matrix

The **C** matrix (or *output matrix*) determines the relationship between the internal state variables and the output, *y.* The output itself is represented as a vector whose elements correspond to the observed values for each of the *output variables.* In our ecosystem example, let’s add 4 output variables: 2 underwater cameras to observe the fish population and 2 aerial drones to observe the pelican population.

- Camera 1 is in a good location with clear water. It can reliably record about 20% of the true fish population *F* (and none of the pelicans).
- Camera 2 is in murky water and can only see about 5% of the fish population.
- Drone 1 is a new, highly quality drone. It can spot about 25% of the true pelican population *P,* but flies too high to see fish.
- Drone 2 is an older drone. It can only spot about 10% of the pelican population.

We can represent these output variables in an *p x n* matrix C, in which *n* = the number of state variables and *p* = the number of output signals to be measured. To align with our previous matrices, the left column corresponds to each output variable's relation to $F$ and the right column corresponds to its relation to $P$ .

$$ \begin{matrix}
Camera \: 1 \: \\
Camera \: 2 \: \\
Drone \: 1 \: \\
Drone \: 2 \: \end{matrix}
\begin{bmatrix}
.2 & 0 \\
.05 & 0 \\
0 & .25 \\
0 & .10 \\ \end{bmatrix} $$

#### Correlating outputs with the system state

We can now model system outputs *y* at time *t* as

$$ y(t)=C*h(t)=\begin{bmatrix} .2 & 0 \\ .05 & 0 \\ 0 & .25 \\ 0 & .10 \\ \end{bmatrix}*\begin{bmatrix}F(t) \\ P(t)\end{bmatrix} $$

Theoretically, this would allow us to derive the true state *h* from the output measurements *y* by referencing the state and output equations.

In reality, the exact relationship between the output measurements and true state is rarely knowable, and output measurements themselves are often imperfect and subject to noisy variation. For instance, it’s unrealistic to assume that Drone 1 will ever spot *exactly* 25% of pelicans on the island. The [Kalman filter](https://thekalmanfilter.com/kalman-filter-explained-simply/) is a technique commonly used to produce the estimate of the true state with the maximum likelihood, using noisy system outputs.

#### The D matrix

The D matrix describes how the input directly influences the observed system output. It’s often omitted from diagrams and discussions of SSMs because it essentially bypasses the actual “model” altogether, having no direct relationship to the state itself.

For instance, in our ecosystem example, imagine if the currents of the island's bodies of water result in airdropped fish food tending to settle near camera 2. This might result camera 2 recording a larger percentage of the true fish population than usual (and in camera 1 capturing a lesser percentage of F than usual) whenever system inputs are increased. The *p* x *m* D matrix would account for such an effect on each of the output variables.

In some cases, there’s no such direct connection between input and output and D is outright dropped from the model.

## SSMs and machine learning

Using the Kalman filter to map system outputs to the system’s true state requires the A and B parameters to be known beforehand. But in many cases, the state space system’s dynamics—the parameters A, B and C—are initially unknown. The correct parameters must be determined in order to use the SSM framework to make meaningful predictions about the system.

A number of machine learning algorithms can be used to derive the values of A, B and C from the known inputs and the corresponding known outputs, using the 2 interrelated equations that describe their interactions. If the model is linear time-invariant (LTI)—if its dynamics are consistent over time and its output scales proportionately with the input—[expectation maximization algorithms](https://vannevar.ece.uw.edu/techsite/papers/documents/UWEETR-2010-0002.pdf) or subspace methods such as [N4SID](https://people.duke.edu/~hpgavin/SystemID/References/VanOverschee-Automatica-1994.pdf) can efficiently estimate model parameters.

### SSMs and deep learning

In recent years, deep learning has emerged as an increasingly common means of learning SSM parameters. Such approaches represent the A, B and C matrices as the weights of a neural network. In an iterative process:

- The model is provided inputs from training data and tasked with predicting the system’s outputs.
- The predicted outputs are measured against the actual “ground truth” outputs for that input, using a [loss function](https://www.ibm.com/think/topics/loss-function).
- [Backpropagation](https://www.ibm.com/think/topics/backpropagation) is used to determine how each model parameter—that is, each element of the A, B and C matrices—contributed to the measured error.
- [Gradient descent](https://www.ibm.com/think/topics/gradient-descent) is used to optimize model parameters in a way that decreases loss (inaccuracy).
- The process is repeated, updating the SSM matrices until the model’s predictions reach some acceptable threshold of accuracy.

Using this process of [supervised learning](https://www.ibm.com/think/topics/supervised-learning) (or [self-supervised learning](https://www.ibm.com/think/topics/self-supervised-learning)), the model *implicitly* learns the dynamics of the state space system. While this is a robust and versatile means of learning optimal SSM parameters, it requires a great deal of training data.

Unlike a conventional SSM, a neural network-based SSM is not interpretable: the values of its matrices no longer correspond to the relationships between state variables and other model parameters in an intuitive way, such as in our earlier example. This is not a unique flaw of deep SSMs, but rather a quality universal to deep learning models writ large.

## Discrete state space models

Traditional SSMs are continuous-time models designed to model continuous sequences, such as an electrical signal or the trajectory of a moving object. But many data modalities processed by modern deep learning models—such as text, molecular structures, user behaviors or time series data—are typically *discrete* sequences. Using SSMs to model a discrete sequence requires a means to represent its distinct, specific timesteps as part of a continuous signal.

Conceptually, *discretization* amounts to sampling “snapshots” of the value of a continuous function at specific moments. This entails the introduction of a new parameter—the *step size*, *∆*—that determines how long that snapshot “held” at each discrete time step *t*. Adjustments to *∆* are akin to changes to qualities such as the data’s resolution (for time series data) or frame rate (for video data). Common discretization methods include the bilinear method, Euler’s method, and the simple [zero order hold (ZOH)](https://en.wikipedia.org/wiki/Zero-order_hold) method used by many modern SSM variants (including Mamba).

### Connection between SSMs and RNNs

Whereas a continuous-time SSM maps a *function* x(t) to a f*unction* y(t), a discrete-time SSM is a *sequence-to-sequence* model. Mathematically speaking, a discretized SSM is the equivalent of a [recurrent neural network (RNN)](https://www.ibm.com/think/topics/recurrent-neural-networks), in which the system’s latent state is the equivalent of an RNN’s “hidden state.”

Though there’s variance in specific letters are used to denote the input and state in SSM equations—in some cases, the former is expressed as *u* and the latter as *x—*this connection to RNNs is what motivates the use of *h* to denote the state in most machine learning contexts. The relationship to RNNs is also what led to the development of modern SSM-based architectures such as Mamba.

The parameters and equations of discretized SSMs are usually rewritten to distinguish them from their continuous-time equivalents, using the subscript notation typically employed for RNNs. In this notation, *h<sub>t</sub>* represents the updated state space the model will generate and *h*<sub>t-1</sub> represents the state before it—that is, the current state space. The notation of A, B and C is also altered to reflect their discretized forms.

#### ***$h_t=\bar{A}h_{t-1}+\bar{B}x_t$   
 $y_t=\bar{C}h_t$***

In this discrete formulation, the system’s state is updated after each timestep *t* (using the state equation), which then allows the updated state to inform the output equation in the following timestep.

## Structured state space models

Despite their many advantages, standard discrete SSMs share some important shortcomings with RNNs. Two of the most important shortcomings were addressed by the introduction of *structured state space sequence models* (or “S4 models”) by Albert Gu *et al* in 2021: their inability to handle long sequences and their inherent inefficiency during [model training](https://www.ibm.com/think/topics/model-training).

The former was addressed through a unique strategy for the initialization of an SSM’s parameters prior to training. The later was addressed through the discovery of an important connection between SSMs and [convolutional neural networks (CNNs)](https://www.ibm.com/think/topics/convolutional-neural-networks).

### HiPPO initialization

Like standard RNNs, conventional discrete SSMs are inherently weak at modeling long-distance dependencies. In other words, they aren’t good at understanding the relationship between steps in a sequence that are far apart, such as words at the beginning and end of a paragraph—which makes them weak at modeling long sequences (such as text data) altogether.

To solve for this, Gu *et al* proposed the use of a technique called [*HiPPO*](https://arxiv.org/pdf/2008.07669) (short for High-order Polynomial Projection Operators) to define the way the A and B matrices behave.

Polynomial functions combine one or more *terms.* Each term comprises a *coefficient* and a *basis function* of some variable. For instance, 3x2 is a term whose coefficient is 3 and whose basis is x2. A polynomial’s “order” is determined by the highest power of any basis it contains: 3x2 + 5x is a “second order polynomial.” The higher a polynomial’s order, the more intricate detail can be captured in its curves.

*Orthogonal* polynomial functions are special “families” of polynomials, spanning multiple orders, in which each polynomial is mathematically independent from the others, ensuring there’s no redundant overlap or informational dependencies between them. They’re also very robust to minor rounding errors, making them useful for approximating more complex functions. Families of orthogonal polynomials are themselves generated by a rule called a *three-term recurrence formula*. The HiPPO method uses such recurrence formulae to construct the A and B matrices.

In essence, each time the state *h<sub>t</sub>*<sub> </sub>is updated by the state equation $\bar{A}h_{t-1}+\bar{B}x_t$ *,* the elements of the state vector *h*<sub>t</sub> act as the coefficients of polynomial expressions that approximate the original input. Older inputs are approximated through lower order polynomials that capture broad, low frequency (long-term) details and more recent inputs are approximated through higher order polynomials capture fine-grained, high-frequency (short term) details. Since the chosen polynomials are *orthogonal*, no information is repeated. In essence, this structure forces the state space to “memorize” the entire input history by efficiently “compressing” it into a fixed-size vector of coefficients.

The S4 paper notes that “simply modifying an SSM from a random matrix *A* to [the HiPPO Matrix] improved its performance on the [sequential MNIST benchmark](https://paperswithcode.com/sota/sequential-image-classification-on-sequential) from 60% to 98%,” effectively solving SSMs’ long-term memory problem. Later variations of structured SSMs, such as DSS, S5 and Mamba, use different (often simpler) initialization schemes for A and B, but retain the core HiPPO principals.

### Connection between SSMs and CNNs

Like conventional RNNs, their discrete SSM equivalents are extremely fast at [autoregressive](https://www.ibm.com/think/topics/autoregressive-model) inference. The downside of this equivalence is that RNNs are extremely slow to train.

Fortunately, discretized SSMs have one important property distinguishing them from other RNNs: they exclusively model *linear* dependencies. In other words, they use only simple, straightforward multiplication and addition operations. As [the S4 paper demonstrates](https://arxiv.org/pdf/2111.00396#subsection.2.4), these simple, repeated and interdependent linear recurrences can be unrolled into a 1-dimensional [convolution](https://developer.ibm.com/articles/introduction-to-convolutional-neural-networks/#convolution1) kernel, , that directly maps input *x* to output *y* in a single step: . This can computed very efficiently using the [fast Fourier transform](https://research.ibm.com/publications/what-is-the-fast-fourier-transform--1).

The only “catch” is that this is only possible when every step of the entire input sequence is known. This isn’t the case during inference: the point of inference is using the model to iteratively *predict* the next step in a sequence, because it’s unknown. But during training, when the model is being fed sample sequences and optimized to improve the accuracy of its predictions, the entire sequence *is* known.

This enables a structured SSM to enjoy the best of both worlds: during training, it can be operated very efficiently as a CNN; during inference, it can be operated very efficiently as an RNN.

## Mamba models

[Mamba](https://www.ibm.com/think/topics/mamba-model) is a neural network architecture built upon a special variant of structured SSMs: the *selective state space model.* In tasks such as autoregressive language modeling, Mamba models have proven themselves to match or exceed the performance of transformer models across most academic benchmarks while being significantly faster and more memory-efficient in both inference in training.

Ordinary SSMs are explicitly designed to map input to output using *the entire input history.* This is acceptable or even desirable for some sequence modeling tasks, but a significant handicap for most advanced language modeling tasks. The *selective state space model* provides Mamba with a crucial capability previously offered only by the self-attention mechanism of the transformer architecture: the ability to selectively focus on or ignore specific parts of past input history based on their present relevance.

In prior SSM designs, the A, B, C, D and ∆ parameters are fixed: once they have been optimized through model training, they’re the same for every input. In a *selective* SSM, the SSM parameters are *input-dependent:* they’re generated by multiplying ("projecting") the input vector by a layer of model weights, which itself is optimized in training.

However, because selective SSMs are not linear time-invariant (LTI), they cannot operate as a CNN during training. The Mamba authors addressed this tradeoff with a hardware-aware *parallel scan*, an algorithm that optimizes the way a graphics processing unit (GPU) handles the model’s computations in its memory hierarchy to maximize speed and computational efficiency.

![Diagram of a selective state space model](https://assets.ibm.com/is/image/ibm/mamba-s6-diagram?ts=1778699620236&dpr=off)  The selective SSM and RAM allocation on a GPU. Taken from the original paper, "Mamba: Linear Time-Sequence Modeling with Selective State Spaces"

## Footnotes

1. ["The Apollo 11 Moon Landing: Spacecraft Design Then and Now,"](https://www.mathworks.com/company/technical-articles/the-apollo-11-moon-landing-spacecraft-design-then-and-now.html) MathWorks, 2019  
 2. ["A guide to state–space modeling of ecological time series,"](https://esajournals.onlinelibrary.wiley.com/doi/10.1002/ecm.1470) Econological Society of America, 14 June 2021
