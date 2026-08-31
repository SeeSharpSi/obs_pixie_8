---
title: What is instruction tuning?
source: https://www.ibm.com/think/topics/instruction-tuning
author:
- '[[Dave Bergmann]]'
published: 2024-12-02
created: 2026-08-31
description: "Instruction tuning is a technique for fine-tuning large language models (LLMs) to improve model performance on natural language instruction following."
---

## What is instruction tuning?

*Instruction tuning* is a technique for [fine-tuning](https://www.ibm.com/topics/fine-tuning) large language models [(LLMs)](https://www.ibm.com/topics/large-language-models) on a labeled dataset of instructional prompts and corresponding outputs. It improves model performance not only on specific tasks, but on following instructions in general, thus helping adapt pre-trained models for practical use.

Instruction tuning is a subset of the broader category of fine-tuning techniques used to adapt pre-trained foundation models for downstream tasks. [Foundation models](https://research.ibm.com/blog/what-are-foundation-models) can be fine-tuned for a variety of purposes, from style customization to supplementing the core knowledge and vocabulary of the pre-trained model to optimizing performance for a specific use case. Though fine-tuning is not exclusive to any specific domain or [artificial intelligence model](https://www.ibm.com/topics/ai-model) architecture, it has become an integral part of the LLM lifecycle. For example, Meta’s [Llama 2 model family](https://www.ibm.com/topics/llama-2) is offered (in multiple sizes) as a base model, as a variant fine-tuned for dialogue (*Llama-2-chat*) and as a variant fine-tuned for coding (*Code Llama*).

Instruction tuning is not mutually exclusive with other fine-tuning techniques. For example, chat models often undergo both instruction tuning and [*reinforcement learning from human feedback* (RLHF)](https://www.ibm.com/topics/rlhf), a fine-tuning technique that aims to improve abstract qualities like helpfulness and honesty; models fine-tuned for coding often undergo both instruction tuning (to broadly optimize responses for instruction following) and additional fine-tuning on programming-specific data (to augment the model’s knowledge of coding syntax and vocabulary).

While the genesis of LLMs traces back to the 2017 “Attention is All You Need” paper that introduced large-scale [transformer models](https://www.ibm.com/topics/transformer-model) to [natural language processing (NLP)](https://www.ibm.com/topics/natural-language-processing) tasks, the incorporation of instruction tuning and RLHF*—*driven by influential papers from Google (in 2021)<sup>1</sup> and OpenAI (in 2022),<sup>2</sup> respectively—yielded the modern LLMs that initiated the current era of [generative AI](https://research.ibm.com/blog/what-is-generative-AI) with the launch of ChatGPT.

## Why instruction tune LLMs?

The utility of instruction tuning, like that of most fine-tuning techniques, lies in the fact that pre-trained LLMs are not optimized for conversations or instruction following. In a literal sense, LLMs do not *answer* a prompt: they only *append text to it.* Instruction tuning helps make that appended text more useful.

The pre-training process for *autoregressive* language models—LLMs used for generating text, like Meta’s [Llama 2](https://www.ibm.com/topics/llama-2), OpenAI’s GPT, Google’s Gemini or [IBM’s Granite](https://www.ibm.com/downloads/cas/X9W4O6BM)—optimizes these LLMs to simply predict the next word(s) in a given sequence until it’s complete.

LLMs are pre-trained using [*self-supervised learning*](https://www.ibm.com/topics/self-supervised-learning) on a massive corpus of written content. In pre-training, autoregressive models are provided the beginning of a text sample and repeatedly tasked with predicting the next word in the sequence until the end of the excerpt. For each prediction, the actual next word of the original sample sentence serves as “ground truth.” Through optimization algorithms like [gradient descent](https://www.ibm.com/topics/gradient-descent) that iteratively adjust model parameters—the varying weights and biases applied to the mathematical operations occurring at each node in a neural network—in a way that brings the model’s predictions closer to the original text, the model “learns” the linguistic patterns in its training data (and, by extension, the “knowledge” conveyed in those linguistic patterns).

Though this pre-training process imparts an impressive ability to generate linguistically coherent text, it doesn’t necessary align model performance with the practical needs of human users. Without fine-tuning, a base model might respond to a prompt of “*teach me how to bake bread*” with “*in a home oven.”* That’s a grammatically sound way to complete the sentence, but not what the user wanted.

Nevertheless, pre-training an LLM for any specific purpose (like following instructions) is impractical. The “large” in “large language models” refers to the fact that these models often have billions of parameters: training these huge models from scratch entails a tremendous amount of energy, time, computational resources and training data. Conversely, fine-tuning an already-trained LLM requires far less data and, especially when using *parameter efficient fine-tuning* (PEFT) methods like partial fine-tuning or *low rank adaptation* (LoRA)*,* only a fraction of the computational demands.

Though fine-tuning can be achieved through nearly any machine learning paradigm, including reinforcement learning, [semi-supervised learning](https://www.ibm.com/topics/semi-supervised-learning) or additional self-supervised learning, instruction tuning entails [supervised learning](https://www.ibm.com/topics/supervised-learning) on labeled (*input, output*) pairs. What distinguishes instruction tuning from other forms of supervised fine-tuning (SFT) is that the *input* samples in an instruction dataset consist entirely of tasks that resemble requests users might make in their prompts; the *outputs* demonstrate desirable responses to those requests. In adjusting model weights to make the LLM’s outputs resemble the examples in the instruction dataset, the LLM “learns” to respond to a prompt like “*teach me how to bake bread*” by appending text that contains actual advice for baking bread.

Instruction tuning thus helps to bridge the gap between the model’s fundamental objective—next-word prediction—and the user’s goal of having the model follow instructions and perform specific tasks. This makes model behavior more useful and predictable.

## How does instruction tuning work?

Fine-tuning LLMs on a labeled dataset of varied instruction-following tasks yields greater ability to follow instructions in general, reducing the amount of in-context information needed for effective prompts. Instruction datasets can be either manmade or generated by another LLM.

As articulated in Google Research’s influential 2022 paper, “Finetuned Language Models are [Zero-Shot Learners](https://www.ibm.com/topics/zero-shot-learning),” the goal of instruction tuning is to improve the ability of LLMs to respond to NLP instructions. To do so, instruction tuning “combines appealing aspects of both the pretrain–finetune and prompting paradigms.” In essence, by organically incorporating the principles of prompt engineering into supervised fine-tuning, instruction tuning reduces the amount of [prompt engineering](https://www.ibm.com/topics/prompt-engineering) and [few-shot](https://www.ibm.com/topics/few-shot-learning) exemplars required to elicit a useful, accurate response from the fine-tuned model.<sup>1</sup>

Each training sample in an instruction dataset comprises three elements:

- **An instruction:** A natural language text *input* that specifies a given task. For example, “*translate this sentence from English to Spanish.”*
- **Additional information:** Optional, supplementary information that provides context relevant to the task at hand. For example, an input for a reading comprehension task might include a brief passage (and then instruct the model to answer a given question about it).
- **Desired output:** The target *output*—response—for the given prompt, per the instructions and context provided. This will serve as a ground truth against which the model’s predictions are evaluated and optimized.

The Google paper noted that the resulting instruction-tuned variant of their LaMDA-PT model, dubbed FLAN (for *F*inetuned *La*nguage *N*et), experienced the greatest improvements on tasks that are naturally articulated as instructions, like translation, question-answering, reading comprehension and natural language inference (NLI)—the task of determining whether a given “hypothesis” follows logically from a given “premise.”

To explain this, the FLAN paper notes an observation made by Brown, et al in the research paper released for the original GPT-3 model in 2020: one explanation for why pre-trained LLMs (absent additional fine-tuning) struggle with tasks like NLI is that passages resembling a typical NLI task are unlikely to occur naturally in the corpus of unlabeled data used for self-supervised pre-training.<sup>3</sup> Conversely, for tasks that more closely resemble the straightforward language modeling objective of pre-training—like commonsense reasoning tasks that ultimately require the model to complete a sentence correctly—instructions are largely redundant (and thus instruction tuning imparts less benefit).

Perhaps most importantly, the paper demonstrated that adding additional tasks to the instruction tuning dataset improved the instruction-tuned model’s performance even on novel tasks that were not represented in the instruction dataset. Therein lies the fundamental benefit of instruction tuning: a holistic improvement in the model’s ability to follow instructions in general.

## Instruction tuning vs. multi-task fine-tuning

The FLAN paper also included an ablation study that explored whether the apparent benefits of instruction fine-tuning were due to the instruction themselves or simply attributable to fine-tuning the model on multiple NLP tasks.To examine the role of instructions in fine-tuning, the ablation study fine-tuned the base model on three different setups:

- **No template:** Only inputs are outputs were given to the model. For example, the input for a translation task would be “*the dog runs,*” and the target output would be “*le chien court.*”
- **Dataset name:** Each input was preceded by the name of the task and dataset. In our translation example, the input—drawn from the WMT 2014<sup>4</sup> dataset collection—would be   
 “*[Translation: WMT 14 to French] The dog runs.*”
- **FLAN Instructions:** Inputs followed instruction tuning principles. For this translation example, the input would be “*Please translate this sentence to French: ‘The dog runs.’*”

The ablation study then measured the results of each fine-tuned language model on a series of zero-shot instruction-following tasks. The instruction-tuned model achieved over 18% greater accuracy than the “no template” model and over 8% greater accuracy than the “dataset name” model. This indicates that training with the instructions themselves is crucial to enhancing zero-shot performance on unseen tasks.

## Chain-of-thought (CoT) fine-tuning

Chain-of-thought (CoT) prompting asks an LLM to not only answer a question but also generate a rationale for how it arrived at an answer. This can be achieved through few-shot prompting with examplars of sequential reasoning, or by simply appending “*think step by step*” to the end of a prompt. Research has demonstrated that CoT prompting significantly enhances the zero-shot capabilities of large models across diverse arithmetical, symbolic reasoning and other logical reasoning tasks.<sup>5</sup> Wei, et al found that instruction tuning that does not include CoT tasks in the instruction dataset significantly *degrades* model performance on CoT evaluations—but that adding CoT datasets improves performance on all evaluations.<sup>6</sup>

Furthermore, their research found that instruction finetuning on CoT tasks—both with and without few-shot exemplars—increases a model’s ability for CoT reasoning in a zero-shot setting. An intuitive understanding of this benefit would be that through being fine-tuned to work through a problem in logical steps rather than leap to an answer that simply seems linguistically coherent, models learn to better produce and apply their own reasoning skills.

## Instruction-tuning datasets

A number of datasets exist for the purpose of instruction tuning LLMs, many of which are open source. These datasets can comprise directly written (or collected) natural language (*instruction, output*) pairs, use templates to convert existing annotated datasets into instructions or even use other LLMs to generate examples.

### Human-created datasets

While directly authoring (*instruction, output*) pairs is straightforward, it’s a labor-intensive process that ultimately entails a significant amount of time and cost. Various methods have been proposed to transform natural language datasets into instructions, typically by applying templates. The release of multiple open source human-crafted datasets has helped defray to cost of fine-tuning on organic data.

Prominent open source human-created instruction datasets include:

- **Flan:** First used to fine-tune Google’s LaMDA-PT model, yielding the original FLAN model, the Flan dataset has since been refined and used to fine-tune a number of LLMs. Prominent models fine-tuned on Flan include FLAN-T5, Flan-UL2 and Flan-PaLM 540B (also referred to as FLAN-T5-XXL).
- **OpenAssistant:** OpenAssistant Conversations is a human-crafted, multilingual conversation corpus focusing on assistant-style dialogue exchanges. It consists of 91,829 user prompts and 69,614 assistant replies drawn from 66,497 conversation trees in 35 different languages.
- **Dolly:** Dolly is an English-language dataset of 15,000 human-generated conversation instances, designed to enable LLMs to interact with users in dialogue-driven patterns similar to ChatGPT. It spans a wide range of tasks and human behaviors, including summarization, information extraction, brainstorming, creative writing, classification and question answering.

### LLM-generated datasets

Motivated by the prohibitive amount of cost and labor required to manually generate instructions and target outputs, many instruction datasets use the responses of larger LLMs to generate prompts, outputs or both. The use of LLM-generated datasets often has the added effect of teaching smaller models to emulate the behavior of larger models, sometimes in a deliberate teacher/learner dynamic.

- **Self-Instruct:** Self-Instruct was constructed using InstructGPT, which itself is an instruction-tuned version of GPT-3. The authors supplied natural language “seed tasks” and prompted InstructGPT to generate additional examples, ultimately yielding 52,000 training instructions. A modified Self-Instruct method was used by Stanford University researchers to generate training data for *Alpaca*, the first instruction-tuned variant of LLaMA. Notably, Alpaca slightly outperformed InstructGPT’s benchmarks on the Self-Instruct dataset.<sup>7  

 </sup>
- **Evol-Instruct:** As its name suggests, Evol-Instruct proposes an evolution to the Self-Instruct methodology, rewriting instructions using *in-depth* and *in-breadth* strategies. The former evolves instructions to increase instruction complexity through measures like adding constraints, increasing reasoning steps and complicating input. The latter “mutates” prior instructions to increase the dataset’s diversity and topic coverage. Evol-Instruct was introduced in the research paper for *WizardLM*, which details how Evol-Instruct was used to fine-tune LLaMA.<sup>8  

 </sup>
- **ShareGPT:** ShareGPT.com contains a user-generated repository of their exchanges with ChatGPT. The researchers behind Vicuna, a notable fine-tune of LLaMA, used 70,000 conversational records from ShareGPT and tailored their selections for multi-turn conversations.<sup>9  

 </sup>
- **OpenOrca:** OpenOrca is a collection of augmented [Flan Collection](https://arxiv.org/abs/2301.13688) data. It aims to replicate the dataset used by Microsoft to train *Orca*, which explored methodology that explicitly focuses on optimizing the use of larger models to refine smaller LLMs through imitation learning.<sup>10</sup>

As the power of LLMs increases, the utility of LLM-generated instruction tuning datasets has similarly increased. A 2023 paper replicated the Alpaca fine-tuning paradigm—which fine-tuned LLaMA on InstructGPT-generated instructions—while repeating the process in parallel using *GPT-4* to generate instruction. The resultant model, which they dubbed LLaMA-GPT4, significantly outperformed the Alpaca equivalent’s “Helpfulness” scores and came close to matching GPT-4 itself in measures of “Helpfulness,” “Honesty” and “Harmlessness.”<sup>11</sup>

## Challenges and limitations of instruction tuning

Though instruction tuning techniques have yielded important advances in LLMs, work remains to diversify instruction tuning datasets and fully clarify its benefits.

Chief among the challenges of instruction tuning is the creation of high-quality instructions for use in fine-tuning. The resources required to craft a suitably large instruction dataset has centralized instruction to a handful of open source datasets, which can have the effect of decreasing model diversity. Though the use of larger, proprietary LLMs to generate instructions has helped reduce costs, this has the potential downside of reinforcing the biases and shortcomings of these proprietary LLMs across the spectrum of open source LLMs. This problem is compounded by the fact that proprietary models are often, in an effort to circumvent the intrinsic bias of human researchers, to *evaluate* the performance of smaller models.

On a technical level, some researchers have raised concerns that using larger models to improve smaller models may help smallest models imitate the larger models’ *style,* but not their actual *functionality*. A 2023 empirical study suggested that many of the impressive performance gains enjoyed through instruction tuning may come from picking up superficial patterns, rather than more genuine improvement in logical reasoning.<sup>12</sup>

Similarly, other researchers have posited that some reported improvements may depend somewhat on the reliance of evaluating instruction-tuned model performance on tasks too closely related to those of the instruction training dataset. Through more targeted testing of models instruction tuned in this fashion, Gudibande, et al concluded that “the highest leverage action for improving open-source models is to tackle the difficult challenge of developing better base [language models], rather than taking the shortcut of imitating proprietary systems.”<sup>13</sup>

## Footnotes

<sup>*NOTE: external links to ibm.com.*  
 1</sup> ["Finetuned Language Models Are Zero-Shot Learners".](https://arxiv.org/abs/2109.01652) Google (via arXiv). September 3, 2021 (last revision: February 8, 2022).  
 <sup>2</sup> ["Aligning language models to follow instructions".](https://openai.com/index/instruction-following/) OpenAI. January 27, 2022.  
 <sup>3</sup> ["Language Models are Few-Shot Learners".](https://arxiv.org/abs/2005.14165) arXiv. July 22, 2020.  
 <sup>4 </sup>["WMT 2014".](https://paperswithcode.com/dataset/wmt-2014) Papers With Code. June 27, 2014.  
 <sup>5</sup> ["Language Models are Zero-Shot Reasoners"](https://arxiv.org/abs/2205.11916). arXiv. May 24, 2022 (last revision January 29, 2023).  
 <sup>6</sup> ["Scaling Instruction-Finetuned Language Models"](https://arxiv.org/abs/2210.11416). Google (via arXiv). December 6, 2022.  
 <sup>7</sup> ["Alpaca: A Strong, Replicable Instruction-Following Model"](https://crfm.stanford.edu/2023/03/13/alpaca.html). Stanford Center for Research on Foundation Models. March 13, 2023.  
 <sup>8</sup> ["WizardLM: Empowering Large Language Models to Follow Complex Instructions"](https://arxiv.org/abs/2304.12244). arXiv. June 10, 2023.  
 <sup>9</sup> ["Vicuna: An Open-Source Chatbot Impressing GPT-4 with 90%* ChatGPT Quality"](https://lmsys.org/blog/2023-03-30-vicuna/). LMSYS Org. March 30, 2023.  
 <sup>10</sup> "Orca: Progressive Learning from Complex Explanation Traces of GPT-4". Microsoft. June 2023.  
 <sup>11</sup> ["Instruction Tuning with GPT-4"](https://arxiv.org/abs/2304.03277). arXiv. April 6, 2023.  
 <sup>12</sup> ["Do Models Really Learn to Follow Instructions? An Empirical Study of Instruction Tuning"](https://arxiv.org/abs/2305.11383). arXiv. May 19, 2023.  
 <sup>13</sup> ["The False Promise of Imitating Proprietary LLMs"](https://arxiv.org/abs/2305.15717). arXiv. May 25, 2023.
