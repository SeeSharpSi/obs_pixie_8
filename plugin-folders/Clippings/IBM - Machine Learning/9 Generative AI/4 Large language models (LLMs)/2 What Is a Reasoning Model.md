---
title: What is a reasoning model?
source: https://www.ibm.com/think/topics/reasoning-model
author:
- '[[Dave Bergmann]]'
published: 2025-08-07
created: 2026-08-31
description: "A reasoning model is a large language model (LLM) fine-tuned to break complex problems into smaller chain-of-thought (CoT) steps, often called “reasoning traces,” prior to generating a final output."
---

## What is a reasoning model?

A reasoning model, also called a *thinking model* or *large reasoning mode*l (LRM), is a [large language model (LLM)](https://www.ibm.com/think/topics/large-language-models) that has been [fine-tuned](https://www.ibm.com/think/topics/fine-tuning) to perform multi-step problem-solving by generating intermediate steps, often called “reasoning traces,” through which it iteratively refines its output prior to generating its final response.

[Trained](https://www.ibm.com/think/topics/model-training) to employ sophisticated chain-of-thought reasoning and other multi-step decision-making strategies, reasoning models represent the cutting edge of LLM performance, particularly in mathematics, coding and other domains driven by logical reasoning. Originally introduced as a distinct, specialized model category, these “thinking models” have steadily grown more ubiquitous: today, *most* modern LLMs offer a “thinking mode” or similarly-named reasoning capabilities.

The concept of a “reasoning model” was first introduced by [OpenAI’s o1-preview](https://openai.com/index/introducing-openai-o1-preview/) (and o1-mini) in September 2024, followed by Alibaba’s “Qwen with Questions” (QwQ-32B-preview) in November and Google’s Gemini 2.0 Flash Experiment in December. A milestone in the development of reasoning LLMs was the January 2025 release of the open source [DeepSeek-R1](https://www.ibm.com/think/topics/deepseek) model. Whereas the training processes used to fine-tune prior reasoning models had been closely guarded secrets, DeepSeek released a detailed technical paper that provided a blueprint for other model developers. [IBM Granite](https://www.ibm.com/granite), Anthropic and Mistral AI, among others, have since released their own reasoning LLMs.

Simply put, reasoning LLMs are trained to spend more time “thinking” before they respond. The addition of this “reasoning process” has been empirically shown to yield major advancements in LLM performance on complex reasoning tasks. This success has expanded the real-world use cases and domains to which AI models can be applied, marking an important inflection point in the ongoing development of generative AI and AI agents.

It’s worth noting, however, that anthropomorphic terms like a model’s “thought process” are more convenient than literal. Like all [machine learning](https://www.ibm.com/think/topics/machine-learning) models, reasoning models are ultimately just applying sophisticated algorithms to make predictions—like what word should come next—that reflect patterns learned from [training data](https://www.ibm.com/think/topics/training-data). Reasoning LLMs have *not* demonstrated consciousness or other signs of [artificial general intelligence (AGI)](https://www.ibm.com/think/topics/artificial-general-intelligence). A widely cited Apple research paper presented at NeurIPS 2025 [casts doubt](https://proceedings.neurips.cc/paper_files/paper/2025/hash/9b26ad15462c81548c0689188d2e8018-Abstract-Conference.html) on whether current model reasoning abilities can scale to truly “generalizable” reasoning.

It’s perhaps most accurate to say that reasoning LLMs are trained to “show their work” by generating a sequence of tokens (words) that resembles a human thought process—and that this act of “verbalizing” thoughts seems to unlock latent reasoning capabilities that LLMs implicitly learn from their massive corpus of training data (which contains examples of individuals directly and indirectly articulating their own processes).

## Why do reasoning models work?

Adding a “thought process” to model outputs mitigates many of the inherent flaws of standard LLM inference by helping the model avoid harmful cognitive shortcuts and surface more potentially relevant knowledge it learned from training data.

In the context of reasoning LLMs, AI research literature often references [“*System 1*” and “*System 2*” thinking](https://thedecisionlab.com/reference-guide/philosophy/system-1-and-system-2-thinking), terms coined by the Nobel Prize-winning behavioral economist Daniel Kahneman’s in his seminal *Thinking, Fast and Slow.* System 1 thinking is fast, unconscious and intuitive, relying on heuristics and entailing little to no effort. System 2 thinking is slow, deliberate and logical, requiring concerted effort. Research has consistently demonstrated that autoregressive LLMs are, by default, [inclined to System 1 thinking](https://doi.org/10.48550/arXiv.2502.17419).

For some tasks, System 1 thinking is effective and computationally efficient. But for many others, impulsive System 1 thinking falls short. For instance, a [2023 paper](https://doi.org/10.48550/arXiv.2311.11829) from Meta researchers Jason Weston and Sainbayar Sukhbaatar noted how LLMs are easily swayed by the presence of irrelevant context or subjective details in the input prompt.

![LLM examples](https://assets.ibm.com/is/image/ibm/s2a_irrelevant-details?ts=1783460832680&dpr=off)  Example of how non-reasoning LLMs are often "distracted" by irrelevant information. Taken from the paper "System 2 Attention (is something you might need too)."

They proposed a class of techniques they dubbed “System 2 Attention” (S2A), in which the model is instructed to first generate a rewritten version of the input prompt stripped of irrelevant context, then answer that rewritten prompt. In experiments, S2A outperformed standard inference on a variety of tasks, increasing accuracy and decreasing sycophancy.

![LLM examples](https://assets.ibm.com/is/image/ibm/s2a_before-after?ts=1783460833146&dpr=off)  S2A, an early inference scaling method. By adding steps between input and response—in this case, to rewrite the original prompt—the model improves its final output. Taken from the paper "System 2 Attention (is something you might need too)."

Conceptually speaking, the implicit goal of reasoning approaches could be understood as implementing System 2-like model behavior that explores, evaluates and refines its potential outputs.

The foundation for modern “thinking models” was established by early LLM research papers: [one authored by Google Research](https://doi.org/10.48550/arXiv.2112.00114) in 2021 and [another written by University of Tokyo researchers](https://doi.org/10.48550/arXiv.2205.11916) in 2022. Both demonstrated that simply adding the phrase “think step by step”—a technique called [chain of thought prompting](https://www.ibm.com/think/topics/chain-of-thoughts)—significantly improves model outputs. A 2024 paper from Google DeepMind made an even broader assertion by proposing [a new scaling law](https://doi.org/10.48550/arXiv.2408.03314): scaling up *test-time compute* (the resources used to generate an output) increases model performance as much as scaling up *train-time compute* (the resources used to train a model). CoT prompting is merely 1 of many such [inference scaling](https://research.ibm.com/blog/inference-scaling-reasoning-ai-model) (also called *test-time scaling*) techniques, as is S2A.

Modern reasoning LLMs go further: rather than relying on [prompt engineering](https://www.ibm.com/think/prompt-engineering), they use novel fine-tuning techniques and sophisticated workflows to *intrinsicall*y increase the amount of compute the model uses at inference time. The optimization of a reasoning model entails both the technical challenge of developing algorithms and training data and the philosophical challenge of designing an ideal “thought process.”

## How do reasoning models work?

The initial stages of training reasoning LLMs mirror those of conventional LLMs. Like standard LLMs, reasoning models gain their general linguistic facility and world knowledge from large-scale [self-supervised](https://www.ibm.com/think/topics/self-supervised-learning) pretraining, followed by some amount of [supervised](https://www.ibm.com/think/topics/supervised-learning) fine-tuning (SFT) to adapt it to downstream tasks (like conversational chatbot usage). The central innovation is the application of novel *reinforcement learning* (RL) techniques that incentivize the model to generate intermediate “reasoning steps” at inference time before producing a final output.

Years of research and experimentation have yielded an exponentially expanding array of reasoning approaches, but they all share the fundamental goal of *increasing test-time compute.* Other than the base (or [instruction-tuned](https://www.ibm.com/think/topics/instruction-tuning)) LLM serving as their foundation, reasoning models are differentiated by the specific decision-making strategies they’re trained to employ and the specific algorithms used to incentivize that behavior.

Broadly speaking, there are 2 primary methods to increase the compute used at inference time. The aim of fine-tuning a reasoning model is to train it to employ one (or both) of these broad approaches through various learning algorithms.

- **Generate longer outputs:** The model learns to generate longer output sequences through strategies including long chain-of-thought, backtracking and self-refinement.
- **Generate multiple outputs:** Instead of generating a single output in response to a prompt, the model generates multiple iterations of its output and arrives at its final answer through a process of searching, rejecting and aggregating potential outputs.

The nature of the learning paradigms that produce reasoning models typically entails training and evaluation on problems whose solutions are *verifiable* in nature, such as coding tasks or math problems. Benchmark metrics used to evaluate reasoning model performance therefore typically focus on those domains. Considerably less research has been conducted on the impact of reasoning in more subjective domains, such as creative writing.

### Reinforcement fine-tuning

Central to the rise of reasoning LLMs has been the advancement of RL-based fine-tuning, comprising both rules-based RL and deep learning-driven RL (“deep RL”) in LLM contexts. Whereas supervised and self-supervised learning require well-defined, static training tasks, RL is well-suited to the kind of dynamic, open-ended and complex tasks for which multi-step reasoning is most useful.

The use of RL to fine-tune LLMs in a way that imparts abstract qualities is not unique to reasoning models. For instance, the standard training pipeline for an LLM to be used in chatbot settings is as follows:

1. *Self-supervised pretraining*, in which the model learns the linguistic patterns and base knowledge to be applied to downstream tasks.
2. *Supervised fine-tuning (SFT)*, in which the model learns how to properly format its responses to user inputs.
3. *Instruction tuning*, in which the model learns how to follow instructions and perform specific tasks.
4. [*Reinforcement learning from human feedback* (RLHF)](https://www.ibm.com/think/topics/rlhf), in which the model is fine-tuned on human preference data to impart subjective qualities like helpfulness, harmlessness, truthfulness and ideal tone.

Reasoning LLMs typically undergo those same training stages, with the addition (at some point) of a reinforcement learning stage that instills a productive CoT-based reasoning process. This is achieved by defining the goals of this reasoning process—the specific model behaviors to be “rewarded,” such as generating CoT reasoning traces before a final output—and then optimizing model weights in a way that maximizes reward.

Because it’s difficult or even impossible to design an explicit reward *function* for a task as abstract and complex as a reasoning process that will be effective for all complex problem solving, this reward signal often comes from a separate *reward model* used during training*.* In RLHF, this reward model is itself trained on human feedback and learns to predict a numerical score for how much a human would prefer a given response.

In the context of RL for reasoning models, reward signals can be divided into 3 broad categories: *outcome reward models* (ORMs), *process reward models* (PRMs), and rules-based reward systems.

#### Outcome reward models (ORMs)

Outcome reward models (ORMs), as their name suggests, verify the accuracy of the reasoning model’s final output and provide reward signals that are used to optimize model weights accordingly. This is superficially similar to the role of a [loss function](https://www.ibm.com/think/topics/loss-function) in supervised learning, though the mechanics are often more complex.

Whereas a loss function typically measures the token-by-token divergence between a model output and ground truth, an effective ORM must be able to recognize a correct answer to a math problem even when presented very differently from the available ground truth answer, which is often the case given the high variability of long CoT outputs. Likewise, most real-world coding problems have multiple solutions: holistically evaluating code output typically requires a data pipeline that efficiently executes and verifies the efficacy of code snippets. Other output qualities, such as whether it follows prescribed formatting or instructions, can use a standard LLM as a verifier.

While ORMs are a relatively straightforward and computationally efficient solution, they can potentially reward situations wherein flawed reasoning steps nevertheless lead to a correct final answer, resulting in the model learning sub-optimal reasoning processes.

#### Process reward models (PRMs)

Process reward models (PRMs) score and reward (or penalize) each individual reasoning step in isolation, rather than focusing solely on the accuracy of the final answer. This provides more fine-grained reward signals and subsequent model adjustments, yielding models with a more robust and interpretable reasoning process.

PRMs are, however, more costly and time-consuming to train and implement. Influential early approaches to PRMs, such as [OpenAI’s PRM800K dataset](https://doi.org/10.48550/arXiv.2305.20050), relied almost entirely on laborious data labeling from human annotators. Many subsequent approaches, such as the influential [Math-Shepherd](https://doi.org/10.48550/arXiv.2312.08935), have automated this process by inferring the validity of a reasoning step based on how often it results in a correct answer.

#### Rule-based reward systems

To avoid the costs and complications of reward models, some RL-based fine-tuning approaches design training tasks in a way that simplifies the act of evaluating model outputs.

For instance, the DeepSeek-R1 and R1-Zero techniques prompt models to format their final answers within a separate box, allowing accuracy to be verified without a specialized reward model that must parse the entire response. Other rule-based reward systems incentivize specific micro-actions, such as periodically [adding “*wait*”](https://doi.org/10.48550/arXiv.2501.19393) to the model’s response to encourage more exploration and self-correction. The usage of such micro-actions has been proven to improve final outputs and, equally importantly, is easy and cheap to verify.

### DeepSeek-R1-Zero: Pure RL

A simple, illustrative and highly influential reinforcement fine-tuning technique was pioneered by DeepSeek in the training of their open source R1-Zero experimental reasoning model.

Using DeepSeek-V3 as a base, DeepSeek went directly from pretraining to an extremely simple rules-based reinforcement learning scheme:

- *Model query*: Ask the model a question. Prompt it to output a *thought process* between “`<think>` ” and “`</think>` ” tokens, and output its final *answer* between “`<answer>` ” and “`</answer>` ” tokens.
- *Accuracy rewards:* Reward the model for the quality of its final answer*,* such as how well its generated code runs.
- *Format rewards:* Reward the model for correctly using the “`<think> </think>` ” and “`<answer> </answer>` ” format in responses.

Surprisingly, *without any explicit instruction to do so*, DeepSeek-R1-Zero learned to generate complex chains of thought and employ reasoning strategies that yielded impressive performance on math and reasoning tasks. In other words, given only the mandate to “think” before outputting a final answer and maximize the accuracy of final answers, the model naturally explored and “discovered” optimal reasoning patterns.

Practically speaking, this stripped down approach had important flaws: as the technical paper explains, “DeepSeek-R1-Zero encounters challenges such as endless repetition, poor readability and language mixing.” Nevertheless, this pure RL approach served as the basis of the more refined methodology that yielded the massively popular [DeepSeek-R1 model](https://www.ibm.com/think/topics/deepseek).

### Search and sample-based approaches

Whereas most CoT-based RL paradigms aim to optimize the efficacy of a single model output, other methods generate *multiple* final or intermediate outputs with the goal of identifying and incentivizing the best reasoning steps.

Many such approaches rely on *search*-based optimization algorithms, such as beam search, tree-of-thoughts or a Monte Carlo tree search (MCTS), to generate and explore multiple reasoning paths. A process reward model (PRM) evaluates the quality and success of each individual reasoning step, and a reward is then iteratively [backpropagated](https://www.ibm.com/think/topics/backpropagation) through the reasoning paths that led to desirable outcomes. Optimizing model weights to maximize expected reward increases the likelihood of the model pursuing the most productive reasoning paths. This is particularly useful for reasoning tasks with a very large range of potential decisions or those that require extensive long-term planning to have a chance to reach an accurate final answer.

Whereas search-based algorithms inherently focus on intermediate steps, *sampling* approaches prioritize final outcomes. The most basic implementation of sampling-based inference scaling is a simple *best-of-N* algorithm: provide the same input prompt to a model *N* times, use an outcome reward model (ORM) to score each result and select the result that the ORM gives the highest score as the model’s final answer.  

 One classic sampling-based algorithm, *[self-consistency](https://doi.org/10.48550/arXiv.2203.11171)* (also called *majority voting*), doesn’t require an ORM*.* Each task begins with chain-of-thought prompting. Multiple responses, each with their own reasoning paths, are sampled from the model’s decoder. The final answer that appears most consistently among the sampled outputs is determined to be the optimal answer. This can be used either as test-time scaling strategy to minimize randomness and hallucination or as a means of generating high-quality reasoning data for SFT-based methods.

The main downside of search- and sampling-based methods for thinking models is the increased latency—that is, longer response times—and computational overhead they introduce. However, [research from Carnegie Mellon University](https://doi.org/10.48550/arXiv.2408.00724) posits that smaller models employing search- or sample-based inference algorithms can offer a superior performance-efficiency tradeoff to larger models used conventionally.

### SFT, knowledge distillation and self-improvement approaches

Among the most conceptually straightforward way to fine-tune models for reasoning is to simply use supervised learning on a dataset comprising challenging input prompts and corresponding CoT-based outputs.

While using conventional methods to assemble a training dataset “by hand” through human-written examples is prohibitively time- and labor-intensive, the proliferation of reasoning models and inference scaling techniques has made it significantly easier to generate suitable [synthetic training data](https://research.ibm.com/blog/what-is-synthetic-data). Research conducted by Stanford University and the Allen Institute for AI found that after fine-tuning the Qwen2.5-32B-Instruct mode on a curated dataset of only 1,000 pairings of questions and reasoning traces, their “s1” model [beat OpenAI’s o1-preview](https://www.clearscope.io/ibm1/drafts/546d06d8224b86e5/editor?p=e09eddbf) on competition math problems.

[Knowledge distillation](https://www.ibm.com/think/topics/knowledge-distillation) can also be used to teach smaller models to emulate the thought processes of larger reasoning models by fine-tuning them through SFT directly on outputs generated by the larger “teacher” model. DeepSeek used knowledge distillation, with DeepSeek-R1 as teacher, to create reasoning-tuned versions of multiple sizes of Qwen and Llama models.

Other methods aim to bootstrap a dataset of prompts and corresponding long CoT outputs through a process of model “self-improvement.” [Self-Taught Reasoner (STaR)](https://doi.org/10.48550/arXiv.2203.14465) provides [few-shot](https://www.ibm.com/think/topics/few-shot-learning) examples of effective reasoning traces, then prompts a model to generate answers and rationales to a larger number of sample questions. The model is then fine-tuned on rationales that ultimately yielded correct answers, after which the process is iteratively repeated. [Reinforced Self-Training (ReST)](https://doi.org/10.48550/arXiv.2308.08998) applies a similar conceptual approach to fine-tune the reward signal (or “policy”) used for reinforcement fine-tuning. Both have yielded a number of derivative methodologies.

## Challenges of reasoning models

Despite their many strengths and benefits, reasoning LLMs are not without downsides.

### Overthinking

Reasoning models—particularly those with relatively few parameters—are prone to overthinking. [One study from Tencent](https://doi.org/10.48550/arXiv.2308.08998) found that reasoning models consume an average of 1,953% more tokens than conventional models to reach the same answer. [Another study](https://doi.org/10.48550/arXiv.2502.08235)[x], conducted by researches across multiple universities, found that in agentic environments, reasoning models have a tendency to engage in extended circular reasoning instead of interacting with external tools and information sources.

### Limitations of inference scaling

Research published by Anthropic in July 2025 asserted that such overthinking is not solely an efficiency concern: their paper, [“Inverse Scaling in Test-Time Compute,”](https://doi.org/10.48550/arXiv.2507.14417) explored “cases where longer reasoning *deteriorates* performance, exhibiting *an inverse relationship between test-time compute and accuracy.*” While it has been empirically demonstrated that increasing test-time compute can often enhance model performance, their research demonstrated multiple scenarios in generating more reasoning tokens before the final output amplified model weaknesses and alignment issues. This challenges “the assumption that more reasoning universally improves model outputs.”

Related research from Apple, mentioned earlier in this article, demonstrated a series of low-complexity tasks where standard models outperformed reasoning models, as well as high-complexity tasks where both model types failed outright. In Apple’s explorations, reasoning models “fail to develop generalizable problem-solving capabilities for planning tasks, with performance collapsing to zero beyond a certain complexity threshold.”

### Degradation in non-reasoning domains

While reasoning fine-tuning generally yields major improvement on complex tasks in logical domains like math and coding, it can also lead to performance dropoffs elsewhere. For instance, compared to their original counterparts, the versions of Llama 3.1 and Qwen2.5 that were fine-tuned through knowledge distillation on DeepSeek-R1 demonstrated [significant regression](https://assets.ibm.com/is/image/ibm/granite-annonuncement-bar-chart-4?fmt=png-alpha&dpr=on%2C1.3333333333333333&wid=1152&hei=648) on both [ArenaHard](https://lmsys.org/blog/2024-04-19-arena-hard/) and [Alpaca-Eval-2](https://github.com/tatsu-lab/alpaca_eval?tab=readme-ov-file#overview), popular benchmarks that measure a model’s ability to think their way through difficult instructions. Having said that, more broadly-targeted reasoning techniques, such as the [thought preference optimization (TPO)](https://arxiv.org/abs/2410.10630) used to fine-tune IBM Granite 3.2, significantly *improve* instruction following (albeit without a meaningful impact on math or coding performance).

### Increased cost and latency

Users must pay (and wait) for all the tokens the model generates while “thinking,” and those thinking tokens eat into the available [context window](https://www.ibm.com/think/topics/context-window). Some use cases justify that extra time and compute, but for others it’s a waste of resources. However, constantly switching from a reasoning model to a “standard” model on a task-by-task, prompt-by-prompt basis is usually impractical.

#### Reasoning effort and hybrid reasoning models

In the time since the earliest reasoning models were released, the AI industry has largely embraced “hybrid reasoning models” whose reasoning or thinking “effort”—in other words, the amount of reasoning tokens they generate before a final output—can be adjusted.

In February 2025, [IBM Granite 3.2](https://www.ibm.com/new/announcements/ibm-granite-3-2-open-source-reasoning-and-vision) became the first LLM to offer a toggleable “thinking” mode, allowing users to leverage reasoning when they need it and prioritize efficiency when they don’t.16 Anthropic’s Claude 3.7 Sonnet followed suit later that month, adding the ability for [API](https://www.ibm.com/think/topics/api) users to have fine-grained control over *how long* the model “thinks.” Google subsequently introduced a similar ability to adjust the “thinking budget” of Gemini models, and OpenAI soon allowed the “reasoning effort” of its o1 and o3 reasoning models to be set to “low,” “medium” or “high.”

In the time since, this approach has essentially become standard. Though some important language model families continue to be released with distinct reasoning and non-reasoning variants, most providers simply release reasoning-capable models whose reasoning effort can be disabled by the user.

### Interpretability

Ostensibly, revealing the model’s chain of thoughts to the user helps provide an understanding of exactly how an LLM arrives at its final answers, providing greater interpretability than usually possible with a standard model. But research from Anthropic suggests that [reasoning models don’t always say what they actually think](https://www.anthropic.com/research/reasoning-models-dont-say-think). Across a series of specially designed tasks, researchers discovered that both Claude 3.7 Sonnet and DeepSeek-R1 did not faithfully explain their reasoning: for instance, when provided hints of the correct answer, their responses rarely mentioned those hints when describing their alleged rationale.
