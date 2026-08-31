---
title: What is LLM customization?
source: https://www.ibm.com/think/topics/llm-customization
author:
- '[[Ivan Belcic]]'
- '[[Cole Stryker]]'
published: 2025-07-02
created: 2026-08-31
description: "LLM customization, or large language model customization, is the process of adapting a pre-trained LLM to specific tasks."
---

## What is LLM customization?

LLM customization, or [large language model](https://www.ibm.com/think/topics/large-language-models) customization, is the process of adapting a pre-trained LLM to specific tasks. The LLM customization process involves selecting a pre-trained model, also known as a foundation model, then tailoring the model to its intended use case.

## The LLM customization workflow

The process of creating a custom LLM is designed to apply generalized models to more specific contexts. Though various LLM customization methods are available, the general process tends to follow a similar series of steps.

1. **Data preparation:** Optimal model performance hinges on strong training data. Model creators and data scientists must collect and assemble a domain-specific training [dataset](https://www.ibm.com/think/topics/dataset) that is relevant to the model’s intended purpose. With a knowledge base of high-quality data, the model’s responses are more likely to be accurate and useful.
2. **Model selection:** The [list of LLMs](https://www.ibm.com/think/topics/large-language-models-list) is as numerous as it is varied. [AI models](https://www.ibm.com/think/topics/ai-model) range in size, effectiveness, computational resource use and architecture, all of which affect performance. Choosing the right model requires an understanding both the goals and limitations of the [machine learning](https://www.ibm.com/think/topics/machine-learning) project.
3. **Model customization:** Here, machine learning specialists transform the foundation model into a specialized tool. The model’s output will be tailored to specific downstream tasks. Developers must understand the workings of the foundation model and the chosen customization method to successfully optimize the model’s behavior.
4. **Iteration:** ML algorithms perform best when trained with step-by-step processes, rather than by making huge adjustments. Developers can measure the effect of the customization technique at each step and use those findings to inform the next iteration.
5. **Testing:** After training is complete, but before real-world use, the model is tested for reliable performance. Developers make sure their adaptations are effective and that the model applies its newly obtained specific knowledge without suffering [catastrophic forgetting](https://www.ibm.com/think/topics/catastrophic-forgetting).
6. **Model deployment:** The custom model is deployed into its production environment, such as an AI-powered software application or an [API](https://www.ibm.com/think/topics/api), and made available for specific use cases in the real world.

## LLM customization techniques

Depending on the use case and desired output, developers and machine learning specialists choose from a range of LLM customization methods. All types of LLM customization can shape a [generative AI](https://www.ibm.com/think/topics/generative-ai) (genAI) model’s performance to specific downstream tasks.

LLM customization techniques include:

- [Retrieval-augmented generation (RAG)](https://www.ibm.com/think/topics/retrieval-augmented-generation)
- [Fine-tuning](https://www.ibm.com/think/topics/fine-tuning)
- [Prompt engineering](https://www.ibm.com/think/topics/prompt-engineering)

### Retrieval-augmented generation (RAG)

Retrieval-augmented generation (RAG) connects an LLM with an external source of data to expand its knowledge base. When a user submits a query, the RAG system searches the paired database for relevant information, then combines that with the query to give the LLM more context when generating a response.

RAG uses [embeddings](https://www.ibm.com/think/topics/embedding) to transform a database, source code or other information in a searchable [vector database](https://www.ibm.com/think/topics/vector-database). Embeddings mathematically plot each data point in a three-dimensional vector space. To find relevant data, the information retrieval model in a RAG system converts user queries into embeddings and locates similar embeddings in the vector database.

RAG systems typically follow the same standard sequence:

1. **Prompting:** The user submits a prompt into the user interface, such as an AI-powered [chatbot](https://www.ibm.com/think/topics/chatbots).
2. **Querying:** An information retrieval model converts the prompt into an embedding and queries the database for similar data.
3. **Retrieval:** The retrieval model retrieves the relevant data from the database.
4. **Generation:** The RAG system combines the retrieved data with the user’s query and submits it to the LLM, which generates a response.
5. **Delivery:** The RAG system returns the generated response to the user.

RAG gets its name because of the way RAG systems *retrieve* relevant data and use it to *augment* the LLM’s *generated* response. More complex RAG systems introduce additional components to refine the process and further enhance response quality.

#### RAG benefits

Granting the LLM access to domain-specific knowledge allows it to incorporate that data into its response generation process. This increases the accuracy and reliability of AI solutions without too significant a cost investment, especially if the external data is already available and ready for machine learning use.

For example, a RAG model designed for [question-answering](https://www.ibm.com/think/topics/question-answering) can give better answers when it is able to find the correct answers in its linked knowledge base.

Using RAG with smaller models can help them perform at a higher level. [Small language models (SLMs)](https://www.ibm.com/think/topics/small-language-models) offer lower computational requirements, faster training times and less latency in inference. Building a RAG system around an SLM preserves these benefits while tapping into the greater context-specific accuracy RAG offers.

### Fine-tuning

Fine-tuning an LLM involves making iterative adjustments to the internal settings that guide its behavior. These settings are known as [model parameters](https://www.ibm.com/think/topics/model-parameters) or weights, and they control how the model processes and evaluates data.

During training, a model’s learning algorithm adjusts the parameters until optimal performance is reached. At that point, the training process is judged to have been successfully concluded.

Advanced LLMs, especially [transformers](https://www.ibm.com/think/topics/transformer-model) such as OpenAI’s [GPT](https://www.ibm.com/think/topics/gpt) and Meta’s [Llama 2](https://www.ibm.com/think/topics/llama-2), can have billions of parameters. Because these models are so large, full fine-tuning is often prohibitively expensive and time-consuming.

More nuanced fine-tuning methods adjust some of the model’s parameters or add new ones with the goal of both preserving its training performance while increasing proficiency with specific tasks.

Notable fine-tuning methods include:

- [Parameter-efficient fine-tuning (PEFT)](https://www.ibm.com/think/topics/parameter-efficient-fine-tuning)
- [Reinforcement learning with human feedback (RLHF)](https://www.ibm.com/think/topics/rlhf)
- Continual fine-tuning (CFT)

#### Parameter-efficient fine-tuning (PEFT)

PEFT freezes most of a pre-trained model’s parameters and focuses on adjusting those that are most relevant to the new task. In doing so, it consumes far fewer computational resources than a full fine-tune. PEFT is a wide-ranging field with many implementations.

##### Transfer learning

[Transfer learning](https://www.ibm.com/think/topics/transfer-learning) leverages a pre-trained model’s knowledge for new tasks, applying what it already knows in a new context. It works best when the new task is related to the original task, such as when using a [classifier](https://www.ibm.com/think/topics/classification-machine-learning) to recognize and classify new categories or types of objects.

In this example, the type of transfer learning being applied is known as multitask learning: where a model is fine-tuned with several tasks at once. Here, those new tasks are object recognition and classification.

##### Low-rank adaptation (LoRA)

Low-rank adaptation (LoRA) is a modular approach to fine-tuning that adds supplemental parameters to a pre-trained model. LoRA freezes the pre-trained model’s parameters and adds a supplement known as a low-rank matrix that adapts the model’s responses to match the requirements of a specific use case or task.

Imagine LoRA as a set of magical hats that enable the wearer to perform an associated skill. Put on the magical chef’s hat and cook a five-star meal. Don the magical hard hat and build a house. Wear the magical motorcycle helmet and win the Isle of Man TT. Grab a magical baseball cap and bring in the game-winning run.

#### Reinforcement learning with human feedback (RLHF)

Reinforcement learning with human feedback (RLHF) uses a partnered reward model to fine-tune a pre-trained model for complex, subjective tasks. An ML model cannot judge whether a piece of writing is evocative, but humans can, and those humans can teach a model to mimic their preferences.

With RLHF, humans train a reward model for the new task. The reward model’s job is to successfully predict how a human would react to a given input. Whereas standard model training penalizes errors, reward training incentivizes good performance.

Then, the reward model in turn teaches the foundation model how to behave, based on the preferences of the human trainers. Once the reward model is trained, it can train the foundation model without a human in the loop (HITL).

As with all types of machine learning, the model is not thinking critically, or even thinking at all. Rather, it is mathematically choosing the outcome that is most likely to match the preferences of its human trainers.

#### Continual fine-tuning (CFT)

Continual fine-tuning (CFT) is a type of [continual learning](https://www.ibm.com/think/topics/continual-learning) that sequentially adapts a model to new tasks. Using [instruction tuning](https://www.ibm.com/think/topics/instruction-tuning)—training a model using labeled pairs of instructional inputs and related outputs—the model is adapted to a wider data set for downstream tasks. CFT often teaches models to perform the same task on different data distributions.

One risk with all types of continual learning is [catastrophic forgetting](https://www.ibm.com/think/topics/catastrophic-forgetting): when a model loses the ability to perform older tasks after being adapted for new ones. Fortunately, ML researchers have developed several mitigation techniques to help developers avoid catastrophic forgetting in the pursuit of continual learning.

#### Fine-tuning benefits

Fine-tuning adapts models to new use cases while sidestepping the costs of developing new models. Many types of fine-tuning further increase efficiency by only adjusting a small number of parameters. Fine-tuning also shines in situations where there isn’t enough data to train a model from scratch.

### Prompt engineering

Also known as in-context learning or prompt-based learning, prompt engineering includes relevant information in the prompt to help the LLM generate better responses. During inference—when the model fields a user prompt—the user typically provides explicit instructions and examples to follow.

For example, a model being asked to perform [text summarization](https://www.ibm.com/think/topics/text-summarization) can benefit from a prompt that shows it how to format its summary—as a bulleted list, perhaps. More comprehensive prompts help the model return the type of response that the user expects to receive.

[Deep learning](https://www.ibm.com/think/topics/deep-learning) researchers have developed numerous types of [prompt engineering techniques](https://www.ibm.com/think/topics/prompt-engineering-techniques). Some landmark developments include:

- [**Few-shot prompting**](https://www.ibm.com/think/topics/few-shot-learning)**:** The model is given a handful of example outputs (known as *shots*) after which to model its responses. The model can follow the examples and base its response on the shots that the user provides in the prompt.
- **Chain-of-thought (CoT) prompting:** The prompt includes a step-by-step reasoning method for the model to follow. The model structures its response generation according to the CoT provided by the user. CoT prompting is an advanced technique requiring a practiced understanding of how LLMs generate responses.

#### Prompt engineering benefits

Unlike many other LLM customization techniques, prompt engineering requires no additional coding or development. Instead, prompt engineers must be well-versed in the context in which the LLM is to be deployed so that they can craft effective and informed prompts.

When implemented correctly, prompt engineering is a valuable [natural language processing (NLP)](https://www.ibm.com/think/topics/natural-language-processing) technique that allows anyone—especially [artificial intelligence](https://www.ibm.com/think/topics/artificial-intelligence) (AI) beginners—to customize LLMs. Alongside the widespread availability of [open source LLMs](https://www.ibm.com/think/topics/open-source-llms) and [open source AI tools](https://www.ibm.com/think/insights/open-source-ai-tools), prompt engineering is an accessible gateway to machine learning that rewards experimentation, curiosity and persistence.
