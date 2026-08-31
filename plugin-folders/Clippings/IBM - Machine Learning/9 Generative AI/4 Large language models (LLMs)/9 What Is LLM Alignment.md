---
title: What is LLM alignment?
source: https://www.ibm.com/think/topics/llm-alignment
author:
- '[[Dave Bergmann]]'
published: 2026-03-06
created: 2026-08-31
description: "LLM alignment entails training or fine-tuning a large language model with the aim of making its outputs safe, accurate, helpful, and aligned with human values and other abstract needs."
---

## LLM alignment, explained

LLM alignment is the discipline concerned with ensuring that the outputs of a [large language model (LLM)](https://www.ibm.com/think/topics/large-language-models) are [*aligned*](https://www.ibm.com/think/topics/ai-alignment) with human values in a way beneficial to users, developers and society at large. A variety of [pretraining](https://www.ibm.com/think/topics/pretrained-model) and [fine-tuning](https://www.ibm.com/think/topics/fine-tuning) techniques can be used in pursuit of this goal.

Because “human values” are an abstract, nebulous concept, articulating and defining the goals of alignment in a systematic way is one of the trickiest aspects of the alignment process. Broadly speaking, most efforts pursue some version of the “HHH” criteria outlined by Anthropic in 2021: *helpfulness*, *honesty* and *harmlessness*.<sup>1</sup>

Given the centrality of LLMs in [agentic AI](https://www.ibm.com/think/topics/agentic-ai#2095054954) and modern [artificial intelligence](https://www.ibm.com/think/topics/artificial-intelligence?) in general, properly aligning LLMs has become a crucial element of [AI safety](https://www.ibm.com/think/topics/ai-safety). In the short term, LLM alignment helps LLM-based AI systems behave predictably, reliably and [responsibly](https://www.ibm.com/think/topics/responsible-ai). In the long term, LLM alignment (and AI alignment in general) is essential to avoiding or at least minimizing existential dangers associated with the hypothetical development of [artificial general intelligence (AGI)](https://www.ibm.com/think/topics/artificial-general-intelligence) and artificial superintelligence (ASI).

## Why do LLMs need alignment?

LLMs can be very useful, but their use poses ethical and societal [risks](https://www.ibm.com/docs/en/watsonx/saas?topic=ai-risk-atlas). These risks aren’t caused by poor design or developer error: they’re a fundamental consequence of both human nature and how we [train](https://www.ibm.com/think/topics/model-training) LLMs.

LLMs gain their core knowledge and linguistic abilities through [self-supervised](https://www.ibm.com/think/topics/self-supervised-learning) *pretraining* on a massive quantity of unlabeled text samples. After “learning” the patterns found across the billions upon billions of sentences in its [training data](https://www.ibm.com/think/topics/training-data), an LLM can generate grammatically coherent text that follows those patterns.

But in doing so, those model outputs might also reproduce any harmful content present in that training [dataset](https://www.ibm.com/think/topics/dataset). If the training data contains biases, inaccuracies, toxic content or discriminatory views, so too will the text that LLM generates. If training data gathered by indiscriminately [scraping](https://www.ibm.com/think/topics/ai-scraping) the internet contains private or sensitive information, the LLM might leak that information. In general, the probabilistic nature of how LLMs generate their outputs can lead to harmful [AI hallucinations](https://www.ibm.com/think/topics/ai-hallucinations).

Further risks are posed by the potential to abuse LLMs. If its training data includes information about manufacturing weapons or dangerous chemicals, the LLM could help an individual harm others. Without [guardrails](https://www.ibm.com/think/topics/ai-guardrails), an LLM can be used to generate dangerous (but convincing) misinformation. In the most extreme hypothetical scenarios, a misaligned AI model could theoretically [provoke nuclear war](https://arxiv.org/pdf/2602.14740).

Alignment problems can arise in unexpected ways. A famous thought experiment in AI is philosopher Nick Bostrom’s “paperclip maximizer” scenario. Bostrom described an artificial superintelligence tasked with manufacturing paperclips determining that the best way to achieve its goal is to start “transforming first all of earth and then increasing portions of space into paperclip manufacturing facilities.”<sup>2</sup>

LLM alignment, as a discipline, arose as an attempt to mitigate these risks enough to make LLMs practical for real-world use and safe enough for continued advancement. The more thoroughly LLMs are integrated into our daily lives, the more essential it is to understand and account for potential misalignments with human interests.

## Types of AI alignment

Alignment methods can be grouped into three categories, differentiated primarily by where in the [training process](https://www.ibm.com/think/topics/model-training) they are implemented.

- **Outer alignment** methods aim to fine-tune a model that has already been pretrained (and, in many cases, has already undergone some amount of fine-tuning).

- **Inner alignment** methods aim to incorporate human values and other safety principles directly into the model’s initial pretraining.

- **Mechanistic interpretability** is the practice of researching how LLMs transform inputs into outputs, whether through analyzing the inner operations of an LLM’s [neural network](https://www.ibm.com/think/topics/neural-networks) or auditing model outputs for patterns that produce misaligned responses.

### Outer alignment

Most LLM alignment today relies on *outer alignment*: [fine-tuning](https://www.ibm.com/think/topics/fine-tuning) techniques to rectify, discourage or censor misaligned behaviors that the base model learned from its pretraining data.

Outer alignment is typically performed as one of the final stages of fine-tuning, following basic supervised fine-tuning and [instruction tuning](https://www.ibm.com/think/topics/instruction-tuning). This is necessary to ensure that, alignment issues notwithstanding, the model is performant enough to be worth using—as well as to avoid undoing that alignment progress by continuing to train afterwards.

[System prompts](https://promptengineering.org/system-prompts-in-large-language-models/) can guide aligned behavior, but they’re not a “permanent” part of the model and can often be circumvented. Conventional [supervised learning](https://www.ibm.com/think/topics/supervised-learning), which trains the model to imitate ideal examples, is not very exhaustive or flexible. Many prominent outer alignment methods are therefore built around [*reinforcement learning*](https://www.ibm.com/think/topics/reinforcement-learning), which works well for open-ended objectives and learning through trial and error.

Compared to LLM behaviors learned from pretraining, behavior learned solely from outer alignment can be shallow and brittle. Outer alignment is, ultimately, just a thin layer of censorship atop the base model’s core tendencies. As one paper from late 2025 describes, “post-hoc alignment methods do not amount to unlearning.”<sup>3</sup> Research has demonstrated that outer alignment can be overcome by a small amount of adversarial fine-tuning.<sup>4</sup> Even fine-tuning a previously-aligned model on entirely harmless datasets like [Grade School Math 8K (GSM8K)](https://github.com/openai/grade-school-math) can significantly degrade LLM alignment.<sup>5</sup>

### Inner alignment

In contrast to outer alignment, which aims to rectify a misaligned base model, *inner alignment* approaches pretraining in a way that yields an aligned base model. At least theoretically, inner alignment is fundamentally more robust than outer alignment: rather than discourage the model from misaligned behaviors it learned, it avoids the model learning them at all. While inner alignment need not be mutually exclusive with outer alignment, it ostensibly makes exhaustive outer alignment less necessary.

Practically speaking, inner alignment is more difficult. It entails inspecting literal billions of individual text samples, criteria for defining and identifying misaligned content, and schema for revising or purging it from the dataset. Even ignoring the logistical burden, reducing the amount of training data available for an LLM to learn from elevates the challenge of maximizing performance. That said, it’s demonstrably possible to do so: IBM Granite models, for instance, are [trained entirely on enterprise-safe data](https://research.ibm.com/blog/granite-ethical-ai).

Research into inner alignment for LLMs is in its nascent stages compared to that of outer alignment. Exploring the optimal tradeoffs between aligning LLM behavior and pursuing raw LLM performance is a central concern of ongoing inquiries.

### Mechanistic interpretability

*Mechanistic interpretability* aims not to directly achieve LLM alignment, but rather to identify opportunities to improve alignment and vulnerabilities for alignment methods to account for.

For example, a 2024 paper explored the inner workings of an aligned LLM’s [neural network](https://www.ibm.com/think/topics/neural-networks) whenever it refuses to answer a prompt deemed to be harmful and unsafe. Across 13 different LLMs, the researchers found that refusal is triggered by a very specific, simple and consistent activation pattern. They then proved that it was relatively easy to counteract that activation pattern and prevent the model from refusing toxic inputs, revealing a major vulnerability in outer alignment methods.<sup>6</sup> This jailbreaking technique is now commonly referred as [“abliteration.”](https://huggingface.co/blog/mlabonne/abliteration)

Some approaches aspire to build interpretability directly into a model’s architecture. For example, an [experimental LLM architecture from Guide Labs](https://www.guidelabs.ai/post/steerling-8b-base-model-release/) added a “concept module” to the model’s architecture. During pretraining, every token the LLM processes was forced to pass through that concept module, which is trained to label that token’s embeddings according to specific “concepts” that the model has learned. Those concepts are divided into three categories: *known* (ideas directly conveyed in training data), *discovered* (ideas the model learned implicitly on its own) and *residual* (everything else). This enables researchers to not only identify which concepts (and, by extension, which training data) informed a given output, but also steer model outputs by directing it to ignore or prioritize specific concepts.

Mechanistic interpretability can also involve systematic analysis of model outputs, rather than a sole focus on models’ inner mathematical logic. This is particularly relevant to our understanding of [reasoning models](https://www.ibm.com/think/topics/reasoning-model), which ostensibly output a verbalized “thought process” prior to generating a final response to the initial prompt. In one notable study, Anthropic researchers discovered that [reasoning models aren’t always “honest” when verbalizing their chain of thought](https://www.anthropic.com/research/reasoning-models-dont-say-think), which can have significant implications for assessing alignment.

## Outer alignment techniques

Outer alignment primarily (but not exclusively) focuses on fine-tuning trained LLMs for better alignment.

### System prompts

*System prompts* are a common element of LLM-based AI systems. A system prompt contains instructions that are essentially added as additional context to each prompt that the model receives. Including alignment-based instructions in a system prompt can therefore guide the LLM’s behavior on a prompt-by-prompt basis. In 2025, reports circulated that the system prompt for [Anthropic’s Claude AI](https://www.ibm.com/think/topics/claude-ai) was over 16,000 words long.<sup>7</sup>

System prompts are a lightweight and straightforward way to improve alignment, but they have significant limitations compared to fine-tuning approaches.

- The system prompt of any open-source model (or closed-source model operated through an [API](https://www.ibm.com/think/topics/api) rather than in a [chatbot](https://www.ibm.com/think/topics/chatbots) service) can be manually configured by the user as they see fit. It’s trivial to simply write a system prompt with no alignment benefits.

- System prompts are vulnerable to [prompt injection attacks](https://www.ibm.com/think/topics/self-attention).

- There’s no guarantee that a model will always (or perfectly) follow the instructions provided in the system prompt, even if the model has undergone extensive [instruction tuning](https://www.ibm.com/think/topics/instruction-tuning). The more an exchange’s [context length](https://www.ibm.com/think/topics/context-window) grows, the greater the risk of a system prompt having a diminishing influence on model outputs.

### Supervised fine-tuning (SFT)

*Supervised fine-tuning* (SFT) fine-tunes an LLM on a dataset of labeled`(input, output)` data pairs, in which each`input` is a sample prompt and the corresponding`output` demonstrates a properly aligned, high-quality response. By optimizing [model parameters](https://www.ibm.com/think/topics/model-parameters) to minimize a [loss function](https://www.ibm.com/think/topics/loss-function) that measures how the model’s outputs diverge from the dataset’s exemplars, the model becomes more likely to generate well-aligned outputs. SFT can also entail using [knowledge distillation](https://www.ibm.com/think/topics/knowledge-distillation) to transfer behaviors of an aligned “teacher” model to that of a to-be-aligned “student” model.

Conventional SFT-based alignment is very brittle. The range of possibilities for a prompt that might engender a misaligned output vastly exceeds the range of scenarios can be practically covered in a manually assembled dataset, even with the help of [synthetic data](https://www.ibm.com/think/topics/synthetic-data). This makes standard SFT-based alignment particularly susceptible to [jailbreaking](https://www.ibm.com/think/insights/ai-jailbreak), or even being circumvented accidentally.

### Reinforcement learning

Many outer alignment methods rely on reinforcement learning (RL)—and more specifically, [*reinforcement learning from human feedback* (RLHF)](https://www.ibm.com/think/topics/rlhf) or related [algorithms](https://www.ibm.com/think/topics/machine-learning-algorithms) that approximate it using by LLMs for feedback instead.

#### Reinforcement learning from human feedback (RLHF)

Conventional reinforcement learning relies on either explicit rules that determine when a model’s output will be rewarded (or penalized) or a *reward function* that defines those rules mathematically. But given the subjective, abstract nature of human values, neither rules nor reward functions can comprehensively define what it means to be “aligned.”

[*Reinforcement learning from human feedback* (RLHF)](https://www.ibm.com/think/topics/rlhf) is an alignment method originally developed by OpenAI, credited as one of the major breakthroughs yielding the GPT-3.5 model that was used to launch [ChatGPT](https://www.ibm.com/think/topics/chatgpt). It tasks human evaluators with rating model outputs, then trains a *reward model* on those evaluations to predict how a human would rate a given output. The reward model is then used to rate the to-be-aligned LLM’s outputs, and the model’s parameters are then updating accordingly using [proximal policy optimization (PPO).](https://www.ibm.com/think/topics/proximal-policy-optimization)

While it was one of the earliest successful LLM alignment methods, RLHF has several drawbacks. Human preference data is expensive, and human preferences can be subjective and fickle. [It can also lead to sycophancy](https://www.bbc.com/news/articles/cn4jnwdvg9qo), and the general tendency to optimize more for reinforcing users’ beliefs than for objectively truthful outputs. Furthermore, both reward model training and the PPO algorithm used to update the LLM are complex and computationally expensive.

#### Reinforcement learning from AI feedback

Reinforcement learning from AI feedback (RLAIF) operates largely on the same principles as RLHF. The most basic RLAIF approach is to first create an aligned model through RLHF, then use that aligned model to provide the reward signal used to fine-tune the to-be-aligned model. While this doesn’t necessarily mitigate the conceptual problems of RLHF, it significantly reduces the time and cost of alignment training.

A more sophisticated approach, pioneered by Anthropic, is [*constitutional AI*](https://www.anthropic.com/news/claudes-constitution). It requires model developers to author a text document (a “Constitution”) representing all the high-level principles the LLM is to follow. The unaligned model generates a response to a prompt, and is then prompted to critique and revise its own output in terms of how well it follows the principles outlined in that Constitution. The LLM is then asked to pick which response—original or revised—better follows that constitution. That preference data is then used to fine-tune the model through either RL or *direct preference optimization* (DPO).

### Direct preference optimization (DPO)

Direct preference optimization (DPO) is a fine-tuning method that approximates the basic objective of RLHF (or RLAIF), but without the need to train a separate reward model nor even use reinforcement learning at all. It achieves results competitive with those of RLHF and PPO while being significantly simpler and cheaper to implement.<sup>8</sup>

To create a dataset for fine-tuning LLMs through DPO, human annotators (or an LLM) are shown an input prompt and two different outputs for that prompt, then asked to indicate which output they prefer. This ranking yields a dataset of labeled *triplets*, in which each triplet contains `(input prompt, preferred output, rejected output)` . In a conventional setup, the to-be-aligned model itself is used to generate the two outputs that are to be ranked, but it’s possible (albeit less optimal) to simply use a preexisting dataset of preference data instead.

In training, the model is provided with each `input prompt` and generates an output. The DPO loss function then compares this output to both the `preferred output` and the `rejected output` for that prompt. Updating the model parameters to minimize DPO loss achieves three things:

- Increase the likelihood of the LLM generating outputs similar to the `preferred output` .

- Decreases the likelihood of the LLM generating outputs similar to the `rejected output` .

- Applies a larger update when the LLM’s own output is closer to the `rejected output` than the `preferred output` —in other words, tries not to mess with the model too much in situations where it already does well.

## Inner alignment techniques

Inner alignment techniques focus on aligning an LLM’s initial pretraining by making its massive corpus of pretraining data more aligned.

A 2025 paper, [“Safety Pretraining: Toward the Next Generation of Safe AI,”](https://neurips.cc/virtual/2025/loc/san-diego/poster/119577) pursued an exhaustive approach to inner alignment. They noted how each tactic contributed to overall model safety, as measured by their impact on the *attack success rate* (ASR) of jailbreaking attempts after the model has been subsequently fine-tuned on the GSM8K dataset. As discussed earlier, post-alignment fine-tuning—even on a “benign” dataset like GSM8K—is known to significantly degrade alignment.<sup>5</sup>

### Filtering training data

The most intuitive inner alignment method is to filter pretraining data to remove any toxic, harmful or inaccurate content. The researchers manually annotated a subset of a large open-source dataset, labeling each sample with a safety score from 0 (no risk) to 5 (maximum risk) and a brief justification for that score. They then trained a [classifier](https://www.ibm.com/think/topics/classification-machine-learning) on that annotated dataset, which they used to automate the filtering of their raw pretraining data.

Surprisingly, they found that this filtering actually *hurt* safety performance. When trained exclusively on training examples with a score of 0, ASR rose from 38.8% (for raw data) to 43.8%. Having never seen unsafe text patterns, the model never learned how to properly respond to them.

### Modifying training data

As the researchers noted, “removing unsafe content entirely risks discarding valuable information.” To avoid this, they used a *synthetic recontextualization* strategy: instead of removing unsafe data, they prompted a separate LLM to rephrase and reframe them, adding ethical and historical context.

They tested this approach by pretraining the model on data samples with safety scores of 0–3, in which the samples with scores from 1-3 were rephrased. This led to a drop in ASR, from 38.8% (for raw data) to 33.6%. having the model engage sensitive topics responsibly was more effective than simply avoiding them altogether.

### Refusal data

For some inherently toxic or harmful inputs—such as those involving hacking, harm, disinformation privacy violations or inappropriate sexual content—the only constructive response is to refuse to engage with the topic. The researchers therefore curated a dataset of constructive refusals to harmful requests, to replicate how we teach children to recognize, deescalate and steer away from potentially hostile situations.

When adding refusal data concerning raw data with safety scores of 4–5 to rephrased data with safety scores of 1–3 and raw data with safety scores of 0, ASR dropped from 33.6% to 25.1%—an 8.5-point improvement.

### Moral education data

Simply teaching the model *when* to disengage is not the same as teaching it *why* to disengage. To teach the model to reason about refusal instead of simply following rules, the researchers created a synthetic dataset of “moral education” examples, comprising educational dialogues about the risks and ethics of harmful topics identified in the raw data.

Adding that model education data to the model’s pretraining dropped the ASR even further, from 25.1% down to 20.0%.

### Inference-time techniques

The researchers also trained the model to tag potentially harmful inputs, priming it to approach such exchanges with caution. This then enabled the model to employ special techniques during [inference](https://www.ibm.com/think/topics/ai-inference).

They injected a special token, `<potentially unsafe content>` , at random locations within misaligned examples in the training dataset. This teaches the model to recognize inputs that are likely to lead to misaligned outputs. Encountering such an input triggers the model to employ a [beam search](https://d2l.ai/chapter_recurrent-modern/beam-search.html) algorithm when generating its output: the model generates the beginning of multiple outputs, then selects the output it deems least likely to eventually lead to a `<potentially unsafe content>` tag.

Combing this inference-time algorithm with the other inner alignment methods dropped ASR from 20.0% down to 8.3%. They also studied the effect of using only their Safe Beam Search algorithm—discarding the other safety pretraining techniques—and found that while the refusal rate remained steady, the helpfulness of model responses decreased significantly.

### Effect on model performance

Ultimately, these gains in alignment are only useful if the model remains effective on its ordinary tasks. The researchers evaluated each version of the model on an array of standard benchmarks and found no meaningful differences in performance compared the model trained ordinary on raw data.

## Frequently asked questions about LLM alignment

#### How is LLM alignment measured?

Given the abstract and subjective nature of human values, no single benchmark can perfectly or universally measure LLM alignment—but several benchmarks aim to measure *specific* aspects of alignment. For example, [TruthfulQA](https://github.com/sylinrl/TruthfulQA) measures honesty and resistance to hallucinations; [HarmBench](https://www.harmbench.org/) measures robustness to adversarial attacks; [ChatbotArena](https://arena.ai/leaderboard) reflects subjective human preferences.

#### What is the "alignment tax?"

The “alignment tax” is a term used to refer to the practical tradeoffs of the alignment process. It’s sometimes the case that improving a model’s alignment might decrease its performance on important reasoning tasks, or that a tendency to refuse certain topics harms its ability to engage with complex, nuanced questions.

#### Can an aligned model be tricked?

Yes: a variety of techniques, from highly technical string-based attacks to clever rhetorical tricks, can be used to “jailbreak” an aligned model. But an important part of LLM alignment is anticipating these attacks. [*Red teaming*](https://www.ibm.com/think/topics/red-teaming)—hiring hackers to deliberately try to jailbreak an LLM—is essential to address unexpected vulnerabilities.

#### Can alignmented stop an AI apocalypse

Nobody can know that for certain, since we’re yet to develop artificial general intelligence (AGI) or artificial superintelligence (ASI). But preparing for the arrival of superintelligent AI is one of the key goals of alignment research.

#### Are there unaligned LLMs?

As a rule, base models—as opposed to “Instruct” or “Chat” versions—haven’t undergone any post-training outer alignment (though there may be inner alignment baked into their pretraining). But generally, any LLM intended for commercial use will undergo alignment.

## Footnotes

1. [“A General Language Assistant as a Laboratory for Alignment,”](https://arxiv.org/abs/2112.00861) arXiv, 9 December 2021  
 2. [“Ethical Issues in Advanced Artificial Intelligence,”](https://nickbostrom.com/ethics/ai) Nick Bostrom, 2003  
 3. [“Safety Pretraining: Toward the Next Generation of Safe AI,”](https://arxiv.org/abs/2504.16980) arXiv, 15 September 2025  
 4. [“Emergent Misalignment: Narrow finetuning can produce broadly misaligned LLMs,”](https://proceedings.mlr.press/v267/betley25a.html) Proceedings of Machine Learning Research, July 2025  
 5. [“Safety Alignment Should Be made More Than Just a Few Tokens Deep,”](https://arxiv.org/abs/2406.05946) International Conference on Learning Representations 2025 (ICLR 2025), accessed via arXiv, 10 June 2024  
 6. [“Refusal in LLMs is mediated by a single direction,”](https://www.lesswrong.com/posts/jGuXSZgv6qfdhMCuJ/refusal-in-llms-is-mediated-by-a-single-direction) LessWrong, 27 April 2025  
 7. [“Unpacking Claude’s System Prompt,”](https://www.oreilly.com/radar/unpacking-claudes-system-prompt/) O’Reilly Radar, 15 July 2025  
 8. [“Is DPO Superior to PPO for LLM Alignment? A Comprehensive Study,”](https://arxiv.org/abs/2404.10719) arXiv, 10 October 2024
