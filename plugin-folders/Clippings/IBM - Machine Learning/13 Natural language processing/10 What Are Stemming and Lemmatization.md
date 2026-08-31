---
title: Stemming and lemmatization
source: https://www.ibm.com/think/topics/stemming-lemmatization
author:
- '[[Jacob  Murel Ph.D.]]'
- '[[Eda Kavlakoglu]]'
published: 2024-12-03
created: 2026-08-31
description: "Stemming and lemmatization are text preprocessing techniques in natural language processing (NLP)."
---

## What are stemming and lemmatization?

In [natural language processing (NLP)](https://www.ibm.com/think/topics/natural-language-processing), stemming and lemmatization are text preprocessing techniques that reduce the inflected forms of words across a text data set to one common root word or dictionary form, also known as a “lemma” in computational linguistics.<sup>1</sup>

[Stemming](https://www.ibm.com/think/topics/stemming) and lemmatization are particularly helpful in information retrieval systems like search engines where users may submit a query with one word (for example, meditate) but expect results that use any inflected form of the word (for example, *meditates*, *meditation*, etc.). Stemming and lemmatization further aim to improve text processing in [machine learning](https://www.ibm.com/think/topics/machine-learning) algorithms.

![Diagram exemplifying stemming of morphological variants for dance](https://assets.ibm.com/is/image/ibm/stemming-figure-one-graphic?ts=1763391864714&dpr=off)

## Why stemming and lemmatization?

Researchers debate whether [artificial intelligence](https://www.ibm.com/think/topics/artificial-intelligence) can reason, and this debate has extended to computational linguistics. Can [chatbots](https://www.ibm.com/think/topics/chatbots) and [deep learning](https://www.ibm.com/think/topics/deep-learning) models only process linguistic forms, or can they understand semantics?<sup>2</sup> Whatever one believes on this matter, it nevertheless remains that machine learning models must be trained to recognize different words as morphological variants of one base word. Even process words according to morphology, not semantics. By reducing derivational word forms to one stem word, stemming and lemmatization help information retrieval systems and deep learning models equate morphologically related words.

For many [text mining](https://www.ibm.com/think/topics/text-mining) tasks including text classification, clustering, indexing, and more, stemming and lemmatization help improve accuracy by shrinking the dimensionality of machine learning algorithms and group morphologically related words. Reduction in algorithm dimensionality can, in turn, improve the accuracy and precision of statistical models in NLP, such as topic models and word vector models.<sup>3</sup>

## Stemming versus lemmatization

Stemming and lemmatization function as one stage in text mining pipelines that convert raw text data into a structured format for machine processing. Both stemming and lemmatization strip affixes from inflected word forms, leaving only a root form.<sup>4</sup> These processes amount to removing characters from the beginning and end of word tokens. The resulting roots, or base words, are then passed along for further processing. Beyond this basic similarity, stemming and lemmatization have key differences in how they reduce different forms of a word to one common base form.

### How stemming works

Stemming algorithms differ widely, though they do share some general modes of operation. Stemmers eliminate word suffixes by running input word tokens against a pre-defined list of common suffixes. The stemmer then removes any found suffix character strings from the word, should the latter not defy any rules or conditions attached to that suffix. Some stemmers (for example, Lovins stemmer) run the resulting stemmed bits through an additional set of rules to correct for malformed roots.

The most widely used algorithm is the Porter stemming algorithm, and its updated version the Snowball stemmer. To better understand stemming, we can run the following passage from Shakespeare’s *Hamlet* through the Snowball stemmer: “There is nothing either good or bad but thinking makes it so.”

The Python natural language toolkit (NLTK) contains built-in functions for the Snowball and Porter stemmers. After tokenizing the *Hamlet* quotation using NLTK, we can pass the tokenized text through the Snowball stemmer using this code:

```

from nltk.stem.snowball import SnowballStemmer
from nltk.tokenize import word_tokenize

stemmer = SnowballStemmer("english", True)
text = "There is nothing either good or bad but thinking makes it so."
words = word_tokenize(text)
stemmed_words = [stemmer.stem(word) for word in words]

print("Original:", text)
print("Tokenized:", words)
print("Stemmed:", stemmed_words)
```

The code outputs:

```

Original: There is nothing either good or bad but thinking makes it so.
Tokenized: ['There', 'is', 'nothing', 'either', 'good', 'or', 'bad', 'but', 'thinking', 'makes', 'it', 'so', '.']
Stemmed: ['there', 'is', 'noth', 'either', 'good', 'or', 'bad', 'but', 'think', 'make', 'it', 'so', '.']
```

The Snowball and Porter stemmer algorithms have a more mathematical method of eliminating suffixes than other stemmers. Suffice it to say, the stemmer runs every word token against a list of rules specifying suffix strings to remove according to the number of vowel and consonant groups in a token.<sup>5</sup> Of course, because the English language follows general but not absolute lexical rules, the stemming algorithm’s systematic criterion returns errors, such as *noth*.

The stemmer removes *-ing*, being a common ending signifying the present progressive. In the *Hamlet* quote, however, removing *-ing* erroneously produces the stemmed *noth*. This can inhibit subsequent linguistic analysis from associating *nothing* to similar nouns, such as *anything* and *something*. Additionally, the stemmer leaves the irregular verb *is* unchanged. The Snowball stemmer similarly leaves other conjugations of *to be*, such as *was* and *are*, unstemmed. This can inhibit models from properly associating irregular conjugations of a given verb.

### How lemmatization works

Literature generally defines stemming as the process of stripping affixes from words to obtain stemmed word strings, and lemmatization as the larger enterprise of reducing morphological variants to one dictionary base form.<sup>6</sup> The practical distinction between stemming and lemmatization is that, where stemming merely removes common suffixes from the end of word tokens, lemmatization ensures the output word is an existing normalized form of the word (for example, lemma) that can be found in the dictionary.<sup>7</sup>

Because lemmatization aims to output dictionary base forms, it requires more robust morphological analysis than stemming. Part of speech (POS) tagging is a crucial step in lemmatization. POS essentially assigns each word tag signifying its syntactic function in the sentence. The Python NLTK provides a function for the Word Net Lemmatization algorithm, by which we can lemmatize the *Hamlet* passage:

```

from nltk.stem import WordNetLemmatizer
from nltk.corpus import wordnet
from nltk import word_tokenize, pos_tag

def get_wordnet_pos(tag):
    if tag.startswith('J'):
        return wordnet.ADJ
    elif tag.startswith('V'):
        return wordnet.VERB
    elif tag.startswith('N'):
        return wordnet.NOUN
    elif tag.startswith('R'):
        return wordnet.ADV
    else:         
        return wordnet.NOUN

def lemmatize_passage(text):
    words = word_tokenize(text)
    pos_tags = pos_tag(words)
    lemmatizer = WordNetLemmatizer()
    lemmatized_words = [lemmatizer.lemmatize(word, get_wordnet_pos(tag)) for word, tag in pos_tags]
    lemmatized_sentence = ' '.join(lemmatized_words)
    return lemmatized_sentence

text = "There is nothing either good or bad but thinking makes it so."
result = lemmatize_passage(text)

print("Original:", text)
print("Tokenized:", word_tokenize(text))
print("Lemmatized:", result)
```

The code returns:

```

Original: There is nothing either good or bad but thinking makes it so.
Tokenized: ['There', 'is', 'nothing', 'either', 'good', 'or', 'bad', 'but', 'thinking', 'makes', 'it', 'so', '.']
Lemmatized: There be nothing either good or bad but think make it so .
```

The WordNetLemmatizer, much like the Snowball stemmer, reduces verb conjugations to base forms—for example *thinking* to *think*, *makes* to *make*. Unlike the Snowball stemming algorithm, however, the lemmatizer identifies *nothing* as a noun, and appropriately leaves its *-ing* ending unaltered while further altering *is* to its base form *be*. In this way, the lemmatizer more appropriately conflates irregular verb forms.

## Limitations

Stemming and lemmatization primarily support normalization of English language text data. Both text normalization techniques also support several other Roman script languages, such as French, German, and Spanish. Other scripts, such as Russian, are further supported by the Snowball stemmer. Development of stemming and lemmatization algorithms for other languages, notably Arabic, is a recent and ongoing area of research. Arabic is particularly challenging due to its agglutinative morphology, orthographic variations, and lexical ambiguity, among other features.<sup>8</sup> In all, such elements problematize a systematic method for identifying base word forms among morphological variants, at least when compared to English words.

Beyond this general limitation, stemming and lemmatization have their respective disadvantages. As illustrated with the *Hamlet* example, stemming is a relatively heuristic, rule-based process of character string removal. Over-stemming and under-stemming are two common errors that arise. The former is when two semantically distinct words are reduced to the same root (for example, *news* to *new*); under-stemming is when two words semantically related are not reduced to the same root (for example, *knavish* and *knave* to *knavish* and *knave* respectively).<sup>9</sup> Additionally, stemming only strips suffixes from words and so cannot account for irregular verb forms or prefixes as lemmatization does. Of course, stemming is relatively simple and straightforward to implement while lemmatization can be more computationally expensive and time-consuming depending on the size of the data processed.

## Footnotes

<sup>1</sup> Nitin Indurkhya and Fred Damerau. *Handbook of Natural Language Processing*. 2<sup>nd</sup> edition. CRC Press. 2010.

<sup>2</sup> Zhaofeng Wu, Linlu Qiu, Alexis Ross, Ekin Akyürek, Boyuan Chen, Bailin Wang, Najoung Kim, Jacob Andreas, Yoon Kim. "Reasoning or Reciting? Exploring the Capabilities and Limitations of Language Models Through Counterfactual Tasks". 2023. [https://arxiv.org/abs/2307.02477](https://arxiv.org/abs/2307.02477). Gati Aher, Rosa Arriaga, Adam Kalai. "Using Large Language Models to Simulate Multiple Humans and Replicate Human Subject Studies". *Proceedings of the 40th International Conference on Machine Learning*. PMLR. Vol. 202. 2023. pp. 337-371. [https://proceedings.mlr.press/v202/aher23a.html](https://proceedings.mlr.press/v202/aher23a.html). Emily Bender and Alexander Koller. "Climbing towards NLU: On Meaning, Form and Understanding in the Age of Data". Proceedings of the 58th Annual Meeting of the Association for Computational Linguistics. 2020. pp. 5185-5198. [10.18653/v1/2020.acl-main.463](https://aclanthology.org/2020.acl-main.463/).

<sup>3</sup> Gary Miner, Dursun Delen, John Elder, Andrew Fast, Thomas Hill and Robert A. Nisbet. *Practical Text Mining and Statistical Analysis for Non-Structured Text Data Applications*. Academic Press. 2012.

<sup>4</sup> Christopher Manning and Hinrich Schütze. *Foundations of Statistical Natural Language Processing*. MIT Press. 1999.

<sup>5</sup> Martin Porter. "An algorithm for suffix stripping". *Program: electronic library and information systems*. Vol. 14. No. 3. 1980. pp. 130-137. [https://www.emerald.com/insight/content/doi/10.1108/eb046814/full/html](https://www.emerald.com/insight/content/doi/10.1108/eb046814/full/html). Martin Porter. "Snowball: A language for stemming algorithms". 2001. [https://snowballstem.org/texts/introduction.html](https://snowballstem.org/texts/introduction.html).

<sup>6</sup> Nitin Indurkhya and Fred Damerau. *Handbook of Natural Language Processing*. 2<sup>nd</sup> edition. CRC Press. 2010.  
 Christopher Manning and Hinrich Schütze, *Foundations of Statistical Natural Language Processing*. MIT Press. 1999.

<sup>7</sup> Janez Brank, Dunja Mladenic and Marko Grobelnik. "Feature Construction in Text Mining". *Encyclopedia of Machine Learning and Data Mining*. Springer. 2017.

<sup>8</sup> Abed Alhakim Freihat, Gábor Bella, Mourad Abbas, Hamdy Mubarak and Fausto Giunchiglia. "ALP: An Arabic Linguistic Pipeline". Analysis and Application of Natural Language and Speech Processing. 2022. pp. 67-99. [https://link.springer.com/chapter/10.1007/978-3-031-11035-1_4.](https://link.springer.com/chapter/10.1007/978-3-031-11035-1_4) Abdul Jabbar, Sajid Iqbal, Manzoor Ilahi Tamimy, Shafiq Hussain and Adnan Akhunzada. "Empirical evaluation and study of text stemming algorithms". *Artificial Intelligence Review*. Vol. 53. 2020. pp. 5559–5588. [https://link.springer.com/article/10.1007/s10462-020-09828-3](https://link.springer.com/article/10.1007/s10462-020-09828-3). Abed Alhakim Freihat, Mourad Abbas, Gábor Bella, Fausto Giunchiglia. "Towards an Optimal Solution to Lemmatization in Arabic". *Procedia Computer Science*. Vol. 142. 2018. pp. 132-140. [https://www.sciencedirect.com/science/article/pii/S1877050918321707?via%3Dihub](https://www.sciencedirect.com/science/article/pii/S1877050918321707?via%3Dihub).

<sup>9</sup> Chris Paice. "Stemming". *Encyclopedia of Database Systems*. Springer. 2020.
