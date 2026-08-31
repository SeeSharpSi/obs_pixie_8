---
title: What is text summarization?
source: https://www.ibm.com/think/topics/text-summarization
author:
- '[[Jacob  Murel Ph.D.]]'
- '[[Eda Kavlakoglu]]'
published: 2024-11-27
created: 2026-08-31
description: "Text summarization condenses one or more texts into shorter summaries for enhanced information extraction."
---

## Text summarization defined

Text summarization condenses one or more texts into shorter summaries for enhanced information extraction.

Automatic text summarization (or document summarization) is a [natural language processing](https://www.ibm.com/think/topics/natural-language-processing) (NLP) method that condenses information from one or more input text documents into an original output text. How much of the input text appears in the output is debated—some definitions state only 10%, others 50%.<sup>1</sup> Text summarization algorithms often use [deep learning](https://www.ibm.com/think/topics/deep-learning) architectures—specifically, [transformers](https://www.ibm.com/think/topics/transformer-model)—to parse documents and generate text summaries.

## Types of automatic text summarization

There are two principal types of summarization: extractive and abstractive.

**Extractive summarization** extracts unmodified sentences from the original text documents. A key difference between extractive algorithms is how they score sentence importance while reducing topical redundancy. Differences in sentence scoring determines which sentences to extract and which to retain.

**Abstractive summarization** generates original summaries using sentences not found in the original text documents. Such generation requires [neural networks](https://www.ibm.com/think/topics/neural-networks) and [large language models](https://www.ibm.com/think/topics/large-language-models) (LLMs) to produce semantically meaningful text sequences.

As one may guess, abstractive text summarization is more computationally expensive then extractive, requiring a more specialized understanding of [artificial intelligence](https://www.ibm.com/think/topics/artificial-intelligence) and [generative systems](https://research.ibm.com/blog/what-is-generative-AI). Of course, extractive text summarization may also utilize neural networks transformers—such as GPT, BERT, and BART—to create summaries. Nevertheless, extractive approaches do not require neural networks.<sup>2</sup>

### Extractive versus abstractive summarization

Comparative evaluations of extractive and abstractive techniques show mixed results. For instance, while some research suggests that abstractive summarization is more prone to hallucinations—that is, misleading or factually false information.<sup>3</sup> Additional research, however, suggests that abstractive hallucinations actually align with world knowledge, being derived from the summarization source material itself.<sup>4</sup> Other comparisons of extractive and abstractive techniques show that each have their comparative benefits. While human users view abstractive summaries as more coherent, they also consider extractive summaries more informative and relevant.<sup>5</sup> Research also suggests that the controversiality of text subject matter affects how users view respective summary types.<sup>6</sup> Thus, there may not be a direct one-to-one evaluative comparison between these summarization types.

## How extractive text summarization works

As with other NLP tasks, text summarization requires text data first undergo preprocessing. This includes tokenization, stopword removal, and [stemming](https://www.ibm.com/think/topics/stemming) or [lemmatization](https://www.ibm.com/think/topics/stemming-lemmatization) in order to make the dataset readable by a [machine learning](https://www.ibm.com/think/topics/machine-learning) model. After preprocessing, all extractive text summarization methods follow three general, independent steps: representation, sentence scoring, and sentence selection.

### Representation

In the representation stage, an algorithm segments and represents preprocessed text data for comparison. Many of these representations build from [bag of words](https://www.ibm.com/think/topics/bag-of-words) models, which represent text segments—such as words or sentences—as datapoints in a vector space. Large, multi-document datasets my use term frequency-inverse document frequency (TF-IDF), a variant of bag of words that weights each term to reflect its importance within a text set. [Topic modeling](https://www.ibm.com/think/topics/topic-modeling) tools such as latent semantic analysis (LSA) are another representation method that produce groups of summary keywords weighted across documents. Other algorithms, such as LexRank and TextRank, use graphs. These graph-based approaches represent sentences as nodes (or vertices) that are connected by lines according to semantic similarity scores. How do algorithms gauge semantic similarity?<sup>7</sup>

### Sentence scoring

Sentence scoring, per its name, scores each sentence in a text according to their importance to that text. Different representations implement different scoring methods. For example, topic representation approaches score each sentence according to the degree that they individually express or combine key topics. More specifically, this may involve weighting sentences according to the co-frequency of topic keywords. Graph-based approaches, compute sentence centrality. These algorithms determine centrality using TF-IDF to calculate how far a given sentence node may be from a document’s centroid in vector space.<sup>8</sup>

### Sentence selection

The final general step in extractive algorithms is sentence selection. Having weighted sentences by importance, algorithms select the *n* most important sentences for a document or collection thereof. These sentences comprise the generated summary. But what if there is semantic and thematic overlap in these sentences? The sentence selection step aims to reduce redundancy in the final summaries. Maximal marginal relevance methods employ an iterative approach. Specifically, they recompute sentence importance scores in accordance with that sentence’s similarity to already selected sentences. Global selection methods select a subset of the most importance sentences to maximize overall importance and reduce redundancy.<sup>9</sup>

As this overview illustrates, extractive text summarization is ultimately a text (and most often, sentence) ranking issue. Extractive text summarization techniques rank documents and their test strings (for sample, sentences) in order or produce a summary that best matches the central topics identified in the given texts. In this way, extractive summarization may be understood as a form of information retrieval.<sup>10</sup>

## How abstractive text summarization works

As covered, abstractive text summarization techniques employ neural networks to generate original text that summarizes one or more documents. While there are numerous types of abstractive text summarization methods, literature does not use any one overarching classification system for describing these methods.<sup>11</sup> Nevertheless, it is possible to overview the general aims of these various methods.

### Sentence compression

As with many artificial intelligence applications, abstractive text summarization ultimately aims to mimic human-generated summaries. One key feature of the latter is sentence compression—humans summarize longer texts and sentences by shortening them. There are two general approaches to sentence compression: rule-based and statistical methods.

The former leverage syntactical knowledge to parse grammatical segments. These use keywords, syntactic clues, or even part-of-speech labels to extract text snippets that are then merged, often according to a pre-defined template. This template can be lifted from additional automated text analysis or user-defined rules.<sup>2</sup>

In statistical approaches, a model (whether obtained from pretraining or finetuning) learns which sentence segments to remove. For example, a tree parser may identify similar sentences from an input text and populate comparable sentences across a tree structure. A dependency tree is one such structure that models sentences according to the perceived relation between words, aligning with subject-predicate arrangements. A sentence in this structure may have the verb as its central node, with subjects and objects (that is, nouns) and conjunctions branching off. Additional verbs will then branch off from the nouns to which they are attached. Once text is represented in a tree structure, the algorithm then selects common words or phrases for use by a generative network in creating a new summary.<sup>12</sup>

### Information fusion

As this brief overview of sentence compression hints, information fusion is another key aspect of abstractive summarization. People summarize documents by concatenating information from multiple passages into a single sentence or phrase.<sup>2</sup> One proposed approach to mimic this is sentence fusion across a multi-document set. This approach identifies commonly occurring phrases across a set of documents and fuses them through a technique called lattice computation to produce a grammatically coherent English summary.<sup>13</sup> Another proposed method uses neural topic models to generate key terms that in turn guide summary generation. In this approach, commonly occurring keywords covering main points across multiple documents are combined into a single sentence or group thereof.<sup>14</sup>

### Information order

A final concern in abstractive text summarization is the order of information. Summarized information does not necessarily follow the same order as that of the initial source document. When people write summaries, for instance, they may often organize information thematically. One method used for thematic organization is clusters. Specifically, extracted sentences are organized in clusters according to topical content (as determined by co-occurring keywords). Along these lines, neural topic models are another potential approach ordered information topically.<sup>2</sup>

## Evaluation metrics

Developers use a number of evaluation metrics for text summarization. Differences in metrics generally depend on the type of summary as well as which feature of the summary one wants to measure.

**BLEU** (bilingual evaluation understudy) is an evaluation metric commonly used in machine translation. It measures similarity between ground truth and model output for a sequence of *n* words, known as n-grams. In text summarization, BLEU measures how often, and to what extent, n-grams in an automatic summary overlap with those in a human-generated summary, accounting for erroneous word repetitions in the former. It then uses these precision scores for individual n-grams to calculate an overall text precision, known as the geometric mean precision. This final value is between 0 and 1, the latter indicating perfect alignment between the machine and human generated text summaries.<sup>15</sup>

**ROUGE** (recall-oriented understudy for gisting evaluation) is derived from BLEU specifically for evaluating summarization tasks. Like BLEU, it compares machine summaries to human-generated summaries using n-grams. But while BLEU measures machine precision, ROUGE measures machine recall. In other words, ROUGE computes the accuracy of an automatic summary according to the number of n-grams from the human-generated summarization found in the automatic summary. The ROUGE score, like BLEU, is any value between 0 and 1, the latter indicating perfect alignment between the machine and human generated text summaries.<sup>16</sup>

Note that these metrics evaluate the final summarized text output. They are distinct from the myriad sentence scoring methods used within text summarization algorithms that select suitable sentences and keywords from which to produce the final summarized output.

## Use cases

A number of libraries allow users to readily implement text summarization tools in Python. For instance, the HuggingFace Transformers Library comes loaded with BART, an encoder-decoder transformer architecture, for generating text summaries. OneAI’s Language Skills API also provides tools for readily generating text summaries.

Text summarization’s most obvious application is expedited research. This has potential uses for a variety of fields, such as legal, academic, and marketing. Researchers also show how text summarization transformers can advance additional tasks, however.

**News** News articles are a common dataset for testing and comparing text summarization techniques. Summarization is not always the end goal, however. A handful of studies investigates the role of transformer-derived text summaries as a mode of feature extraction for powering fake news detection models.<sup>17</sup> This research shows promising potential and illustrates how text summaries can be adopted for more wide-reaching uses than merely saving time in reading multiple texts.

**Translation** Cross-lingual summarization is a branch of text summarization that overlaps with machine translation. Admittedly, this is not as large a research field as summarization or translation themselves. Nevertheless, the aim of summarizing a source language text or text collection in a different target language poses an array of new challenges.<sup>18</sup> One published explores cross-lingual summarization with historical texts. In this task, historical language variants (for example, ancient Chinese versus modern Chinese, or Attic Greek to modern Greek) are treated as distinct languages. The specific experiment uses word embeddings alongside extractive and abstractive summarization and [transfer learning](https://www.ibm.com/think/topics/transfer-learning) methods to produce modern summarizations of ancient-language documents.<sup>19</sup>

## Footnotes

<sup>1</sup> Juan-Manuel Torres-Moreno, *Automatic Text Summarization*, Wiley, 2014.

<sup>2</sup> Aggarwal, *Machine Learning for Text*, Springer. Bettina Berendt, “Text Mining for News and Blogs Analysis,” *Encyclopedia of Machine Learning and Data Science*, Springer, 2020.

<sup>3</sup> Haopeng Zhang, Xiao Liu, and Jiawei Zhang, “Extractive Summarization via ChatGPT for Faithful Summary Generation,” Findings of the Association for Computational Linguistics: EMNLP 2023, [https://aclanthology.org/2023.findings-emnlp.214](https://aclanthology.org/2023.findings-emnlp.214/)

<sup>4</sup> Meng Cao, Yue Dong, and Jackie Cheung, “Hallucinated but Factual! Inspecting the Factuality of Hallucinations in Abstractive Summarization,” Proceedings of the 60th Annual Meeting of the Association for Computational Linguistics, 2022, [https://aclanthology.org/2022.acl-long.236](https://aclanthology.org/2022.acl-long.236/)

<sup>5</sup> Jonathan Pilault, Raymond Li, Sandeep Subramanian, and Chris Pal, “On Extractive and Abstractive Neural Document Summarization with Transformer Language Models,” Proceedings of the 2020 Conference on Empirical Methods in Natural Language Processing (EMNLP), 2020, [https://aclanthology.org/2020.emnlp-main.748](https://aclanthology.org/2020.emnlp-main.748/)

<sup>6</sup> Giuseppe Carenini and Jackie C. K. Cheung, “Extractive vs. NLG-based Abstractive Summarization of Evaluative Text: The Effect of Corpus Controversiality,” Proceedings of the Fifth International Natural Language Generation Conference, 2008, [https://aclanthology.org/W08-1106](https://aclanthology.org/W08-1106/)

<sup>7</sup> Ani Nenkova and Kathleen McKeown, “A Survey of Text Summarization Techniques,” *Text Mining Data*, Springer, 2012. Wafaa S. El-Kassas, Cherif R. Salama, Ahmed A. Rafea, and Hoda K. Mohamed, “Automatic text summarization: A comprehensive survey,” *Expert Systems with Applications*, 165, 2021, [https://www.sciencedirect.com/science/article/abs/pii/S0957417420305030](https://www.sciencedirect.com/science/article/abs/pii/S0957417420305030)

<sup>8</sup> Ani Nenkova and Kathleen McKeown, “A Survey of Text Summarization Techniques,” *Text Mining Data*, Springer, 2012. Steven Shearing, Abigail Gertner, Benjamin Wellner, and Liz Merkhofe, “Automated Text Summarization: A Review and Recommendations,” Technical Report, MITRE Corporation, 2020.

<sup>9</sup> Ani Nenkova and Kathleen McKeown, “A Survey of Text Summarization Techniques,” *Text Mining Data*, Springer, 2012.

<sup>10</sup> Jade Goldsteiny, Mark Kantrowitz, Vibhu Mittal, and Jaime Carbonell, “Summarizing Text Documents: Sentence Selection and Evaluation Metrics,” Proceedings of the 22nd annual international ACM SIGIR conference on Research and development in information retrieval, 1999, pp. 121-128, [https://www.cs.cmu.edu/~jgc/publication/Summarizing_Text_Documents_Sentence_SIGIR_1999.pdf](https://www.cs.cmu.edu/~jgc/publication/Summarizing_Text_Documents_Sentence_SIGIR_1999.pdf)

<sup>11</sup> Som Gupta and S.K. Gupta, “Abstractive summarization: An overview of the state of the art,” Expert Systems With Applications, 2019, [https://www.sciencedirect.com/science/article/abs/pii/S0957417418307735](https://www.sciencedirect.com/science/article/abs/pii/S0957417418307735) . Wafaa S. El-Kassas, Cherif R. Salama, Ahmed A. Rafea, and Hoda K. Mohamed, “Automatic text summarization: A comprehensive survey,” Expert Systems With Applications, 2021, [https://www.sciencedirect.com/science/article/abs/pii/S0957417420305030](https://www.sciencedirect.com/science/article/abs/pii/S0957417420305030) . Hui Lin and Vincent Ng, “Abstractive Summarization: A Survey of the State of the Art,” Proceedings of the AAAI Conference on Artificial Intelligence, Vol. 33, No. 1, 2019, pp. 9815-9822, [https://ojs.aaai.org/index.php/AAAI/article/view/5056](https://ojs.aaai.org/index.php/AAAI/article/view/5056)

<sup>12</sup> Som Gupta and S.K. Gupta, “Abstractive summarization: An overview of the state of the art,” Expert Systems With Applications, 2019, [https://www.sciencedirect.com/science/article/abs/pii/S0957417418307735](https://www.sciencedirect.com/science/article/abs/pii/S0957417418307735) . Regina Barzilay and Kathleen R. McKeown, “Sentence Fusion for Multidocument News Summarization,” Computational Linguistics, Vol. 31, No. 3, 2005, pp. 297-328, [https://aclanthology.org/J05-3002](https://aclanthology.org/J05-3002/)

<sup>13</sup> Regina Barzilay and Kathleen R. McKeown, “Sentence Fusion for Multidocument News Summarization,” Computational Linguistics, Vol. 31, No. 3, 2005, pp. 297-328, [https://aclanthology.org/J05-3002](https://aclanthology.org/J05-3002/)

<sup>14</sup> Peng Cui and Le Hu, “Topic-Guided Abstractive Multi-Document Summarization,” Findings of the Association for Computational Linguistics: EMNLP 2021, [https://aclanthology.org/2021.findings-emnlp.126](https://aclanthology.org/2021.findings-emnlp.126/)

<sup>15</sup> Kishore Papineni, Salim Roukos, Todd Ward, and Wei-Jing Zhu, “Bleu: a Method for Automatic Evaluation of Machine Translation,” Proceedings of the 40th Annual Meeting of the Association for Computational Linguistics, 2002, [https://aclanthology.org/P02-1040/](https://aclanthology.org/P02-1040/)

<sup>16</sup> Chin-Yew Lin, “ROUGE: A Package for Automatic Evaluation of Summaries,” Text Summarization Branches Out, [https://aclanthology.org/W04-1013](https://aclanthology.org/W04-1013/)

<sup>17</sup> Soheil Esmaeilzadeh, Gao Xian Peh, and Angela Xu, “Neural Abstractive Text Summarization and Fake News Detection,” 2019, [https://arxiv.org/abs/1904.00788](https://arxiv.org/abs/1904.00788) . Philipp Hartl and Udo Kruschwitz, “Applying Automatic Text Summarization for Fake News Detection,” Proceedings of the Thirteenth Language Resources and Evaluation Conference, 2022, [https://aclanthology.org/2022.lrec-1.289](https://arxiv.org/abs/1904.00788)

<sup>18</sup> Jiaan Wang, Fandong Meng, Duo Zheng, Yunlong Liang, Zhixu Li, Jianfeng Qu, and Jie Zhou, “A Survey on Cross-Lingual Summarization,” Transactions of the Association for Computational Linguistics, Vol. 10, 2022, [https://aclanthology.org/2022.tacl-1.75](https://aclanthology.org/2022.tacl-1.75/)

<sup>19</sup> Xutan Peng, Yi Zheng, Chenghua Lin, and Advaith Siddharthan, “Summarising Historical Text in Modern Languages,” Proceedings of the 16th Conference of the European Chapter of the Association for Computational Linguistics, 2021, [https://aclanthology.org/2021.eacl-main.273](https://aclanthology.org/2021.eacl-main.273/)
