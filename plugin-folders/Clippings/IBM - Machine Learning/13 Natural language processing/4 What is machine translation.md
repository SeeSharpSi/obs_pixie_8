---
title: What is machine translation?
source: https://www.ibm.com/think/topics/machine-translation
author:
- '[[Jacob Murel Ph.D.]]'
- '[[Joshua Noble]]'
published: 2024-12-04
created: 2026-08-31
description: "Learn about different forms of machine translation methods and the critical considerations involved in their implementation."
---

## Machine translation defined

Machine translation is a [natural language processing](https://www.ibm.com/think/topics/natural-language-processing) (NLP) task for mapping text across languages. Translation methods range from simple heuristics to [large language models](https://www.ibm.com/think/topics/large-language-models) (LLMs).

Machine learning research often approaches machine translation as a stochastic process.<sup>[1](#f01)</sup> From their [inception in the mid-twentieth century](https://www.ibm.com/history/machine-aided-translation), machine translation systems have progressed from simple heuristic algorithms to [deep learning](https://www.ibm.com/topics/deep-learning) approaches powered by [neural networks](https://www.ibm.com/topics/neural-networks).

### Computer-assisted translation

Machine translation is distinct from computer-assisted translation (CAT). The latter refers to the use of machine translation software or other digital translation tools to assist human translators. Such tools may be a digital dictionary, grammar checker, or translation memory tool, such as a database of language pairs for common words. The key difference between CAT and machine translation is that in the former, the actual task of translation is done by humans.

### Automated translation

The distinction between machine and automated translation is indefinite. Some sources use *machine translation* and *automated translation* interchangeably yet distinguish them from automated translation while others distinguish the first from the latter two. Generally, these distinctions treat machine translation as encompassing any translation methodology that incorporates [machine learning](https://www.ibm.com/topics/machine-learning) tools—specifically [artificial intelligence](https://www.ibm.com/topics/artificial-intelligence)—and so including CAT.

Automated translation, by contrast, is one form of machine translation that automates steps in a translation workflow, like pre-editing of source text or post-editing of output text. Content management systems can often include translation management tools to help automate common translation tasks. Sources that distinguish this way align automated translation alongside CAT.

## Issues in translation

Machine translation tools face many of the same issues as human translation. Developments in machine translation involve increasingly sophisticated methods for addressing these issues, an overview of some central problems is helpful for context.

One core issue is word ambiguity. A classic illustrative example is the sentence, *The chicken is ready to eat*. Here, *chicken* could refer to the live animal or its cooked meat. This is one example of how polysemous and synonymous words affect translation. Another notable example of such ambiguity is idiomatic expressions. "Beat around the bush", for example, has nothing to do with bushes. Pronouns also can remain ambiguous in many sentences, particularly when treated in isolation.<sup>[2](#f02)</sup>

Changes in linguistic rules, such as syntax and grammar, between different languages also affect translation. For example, German verbs can often appear at the end of sentence, while they often appear in the middle in English, while word order is irrelevant in Latin. This accounts for differences in translation methods between professional translators. In some instances, language translation is word-for-word while other approaches aim to capture the sense and cultural import of text through loose translations.<sup>[3](#f03)</sup>

Poetic texts pose a unique challenge to creating accurate translations. Meter, rhyme, and alliteration are all concerns that uniquely affect poetical translation quality.<sup>[4](#f04)</sup> Machine translation research typically focuses on prose text. This overview introduces some of the concerns in the human translation process that also exist in machine translation technology.

## Types of machine translation

No single process exists for all types of machine translation. How a system translates text depends on the machine translation type. While researchers examine a wide variety of systems, the following three are among the most popular

### Rule-based machine translation

Per its name, rule-based machine translation (RBMT) provides a set of rules that specify how to leverage stored linguistic information for translation. For example, this may involve a list of word-level language pairs and part of speech tags that help the computer combine words into grammatically coherent structures. The user may then create a set of rules that instruct the computer how words and other textual groups from one language map onto those of another.<sup>[5](#f05)</sup>

The complexity of RBMT systems depends on the level of linguistic analysis implemented. Literature often illustrates these levels of linguistic analysis with a diagram called Vauquois’ triangle:

![diagram of different approaches to machine translation](https://assets.ibm.com/is/image/ibm/machine-translation-triangle?ts=1763387565695&dpr=off)

This diagram illustrates three approaches to RBMT:

- **Direct translation.** This approach generally uses a pre-defined dictionary to generate word-for-word translations of the source text. After this step a series of rules attempt to re-order the output text into the word order of the target language. These rules do not involve any syntactic analysis of the source or target texts.
- **Transfer.** This approach adopts a limited degree of syntactic analysis. Common methods of such analysis include part-of-speech tagging, word sense disambiguation, and morphological analysis (as used in [lemmatization](https://www.ibm.com/topics/stemming-lemmatization)). Through these, the system can utilize linguistic knowledge of the source and target languages to generate more idiomatic and less literal translations than direct approaches.
- **Interlingua.** This approach uses a formalized and artificial intermediary representation between the source and translated texts. This intermediary is, essentially, an even more abstracted version than that produced in transfer systems through morphological analysis. The system code the source text into this abstract artificial language which it then decodes into the target language.<sup>[6](#f06)</sup>

In order to effectively accommodate real-world cases, RBMT approaches require large dictionaries. Moreover, natural languages do not follow an unchanging set of rules—one is allowed in one culture, time period, or dialect does not linguistically apply to another. Given the ever-growing and mercurial nature of natural languages, RBMT does not offer a comprehensive solution to machine translation. Statistical-based methods to translation are one attempt to accommodate language’s ever-changing nature.

### Statistical machine translation

Statistical Machine Translation (SMT) is an approach that builds statistical models from training data of language pairs. An SMT training dataset consists of words or n-grams in one language paired with corresponding words and n-grams in one or more language. From this data, SMT approaches construct two machine learning models that divide the translation process into two stages.

The first model is a translation model. It uses the training data to learns linguistic pairs with probability distributions. When provided an n-gram in the source language, the model outputs potential target language n-grams with probability values. These values indicate the likelihood, based on what the model learned from the training data, that the target n-gram is an appropriate translation of the source n-gram. For example, a Latin-English translation model might produce this output for the source tri-gram *mihi canes placent*:

![table comparing translation of Latin mihi canes placent](https://assets.ibm.com/is/image/ibm/machine-translation-table?ts=1763387566032&dpr=off)

In this hypothetical output, the model predicts potential English translations for the Latin phrase *mihi canes placent*. The English *I like dogs* has the highest probability value of .8. This means that based on what the model learned from the Latin-English pairings, it is 80% likely that this is the best English translation.

The second model is a monolingual model for the target language. This model essentially predicts the likelihood of the translation model’s n-gram outputs appearing in target language. For instance, take the hypothetical output *I like dogs* from our translation model. The monolingual model predicts the probability of *dogs* appearing after *I like* according to the provided English-language training data. In this way, the monolingual model may be thought of as a stochastic approach to post-editing that aims to confirm the sense and appropriateness of a translation.<sup>[7](#f07)</sup>

While SMT improves on rule-based methods, it has many problems common to machine learning models. For instance, [overfitting](https://www.ibm.com/topics/overfitting) or [underfitting](https://www.ibm.com/topics/underfitting) training data. The former can particularly hamper a SMT system’s ability to address out of vocabulary terms, idiomatic expressions, and different word orders. SMT systems preprocesses text sequences in fixed lengths of n words.

### Neural machine translation

Neural networks translation (NMT) provides a more flexible translation that accommodates inputs and outputs of variable lengths. Much like SMT systems, NMT approaches can be divided into two general steps. First, a model reads the input text and contextualizes it within a data structure that summarizes the input. This contextual representation is often a vector model—as in [bag of words](https://www.ibm.com/topics/bag-of-words) models—but can also take others forms, such as tensors. A [recurrent](https://www.ibm.com/topics/recurrent-neural-networks) or [convolutional neural network](https://www.ibm.com/topics/convolutional-neural-networks) reads this representation and generates a sentence in the target language.<sup>[8](#f08)</sup> More recently, researchers have turned to [transformer architectures](https://www.ibm.com/topics/transformer-model) for NMT. One key example is mBART, a transformer trained on multilingual data for recovering artificial lacunas then fine-tuned for translation.<sup>[9](#f09)</sup>

NMT approaches have also adopted [large language models](https://www.ibm.com/topics/large-language-models) (LLMs). Specifically, rather than fine-tune a neural network or transformer for translation, researchers have explored prompting generative large language models for translation. One such study examines GPT models for machine translation. NMT systems consist of the previously described encoder-decoder architecture trained on large amounts of multilingual data. GPT models, by contrast, consist of only decoder setups trained on primarily English data. Testing across multiple languages—including English, French, Spanish, German, Chinese, and Russian—the study suggests that hybrid approaches of NMT and GPT models produce high-quality, state-of-the-art translations.<sup>[10](#f10)</sup>

This suggests that NMT systems, particularly when combined with LLMs and generative models, are able to better handle idiomatic expressions and out-of-vocabulary terms than SMT methods. Moreover, while SMTs process n-grams, NMTs process the full source sentence. It therefore better handles linguistic features such as discontinuity that require approaching sentences as units. Ambiguity in pronouns, however, can remain a problem for NMTs.<sup>[11](#f11)</sup>

## Use cases

Machine translation services are widely available, and one neural-based machine translation engine is IBM’s [Watson Language Translator](https://www.ibm.com/docs/en/openpages/9.0.0?topic=enhancements-watson-language-translator).

A key area in which machine translation can help traverse language barriers is speech-to-speech translation, potentially in real-time. Recent studies have explored joint applications of automatic speech recognition and transformer-based NMTs for speech-to-speech translation with positive results.<sup>[12](#f12)</sup> Because speech translation systems generally require transcribing speech then translating the resultant text. A recent study examines concatenating speech and text during preprocessing for multimodal translation with promising results.<sup>[13](#f13)</sup>

## Footnotes

1 Miles Osborne, “Statistical Machine Translation,” *Encyclopedia of Machine Learning and Data Mining*, Springer, 2017.

2 Philipp Koehn, *Neural Machine Translation*, Cambridge University Press, 2020.

3 Thierry Poibeau, *Machine Translation*, MIT Press, 2017.

4 Translating poetry essay

5 Dorothy Kenny, “Human and machine translation,” *Machine translation for everyone: Empowering users in the age of artificial intelligence*, Language Science Press, 2022.

6 Thierry Poibeau, *Machine Translation*, MIT Press, 2017.

7 Dorothy Kenny, “Human and machine translation,” *Machine translation for everyone: Empowering users in the age of artificial intelligence*, Language Science Press, 2022.

8 Ian Goodfellow, Yoshua Bengio, and Aaron Courville, *Deep Learning*, MIT Press, 2016.

9 Yinhan Liu, Jiatao Gu, Naman Goyal, Xian Li, Sergey Edunov, Marjan Ghazvininejad, Mike Lewis, and Luke Zettlemoyer, “Multilingual Denoising Pre-training for Neural Machine Translation,” *Transactions of the Association for Computational Linguistics*, Vol. 8, 2020, [https://aclanthology.org/2020.tacl-1.47/](https://aclanthology.org/2020.tacl-1.47/) (link resides outside of ibm.com).

10 Amr Hendy, Mohamed Abdelrehim, Amr Sharaf, Vikas Raunak, Mohamed Gabr, Hitokazu Matsushita, Young Jin Kim, Mohamed Afify, and Hany Hassan Awadalla, “How Good Are GPT Models at Machine Translation? A Comprehensive Evaluation,” [https://arxiv.org/abs/2302.09210](https://arxiv.org/abs/2302.09210) (link resides outside of ibm.com).

11 Dorothy Kenny, “Human and machine translation,” *Machine translation for everyone: Empowering users in the age of artificial intelligence*, Language Science Press, 2022.

12 Yi Ren, Jinglin Liu, Xu Tan, Chen Zhang, Tao Qin, Zhou Zhao, and Tie-Yan Liu, “SimulSpeech: End-to-End Simultaneous Speech to Text Translation,” *Proceedings of the 58th Annual Meeting of the Association for Computational Linguistics*, 2020, [https://aclanthology.org/2020.acl-main.350/](https://aclanthology.org/2020.acl-main.350/) (link resides outside of ibm.com). Parnia Bahar, Patrick Wilken, Tamer Alkhouli, Andreas Guta, Pavel Golik, Evgeny Matusov, and Christian Herold, “Start-Before-End and End-to-End: Neural Speech Translation by AppTek and RWTH Aachen University,” *Proceedings of the 17th International Conference on Spoken Language Translation*, 2020, [https://aclanthology.org/2020.iwslt-1.3/](https://aclanthology.org/2020.iwslt-1.3/) (link resides outside of ibm.com).

13 Linlin Zhang, Kai Fan, Boxing Chen, and Luo Si, “A Simple Concatenation can Effectively Improve Speech Translation,” *Proceedings of the 61st Annual Meeting of the Association for Computational Linguistics*, 2023, [https://aclanthology.org/2023.acl-short.153/](https://aclanthology.org/2023.acl-short.153/) (link resides outside of ibm.com).
