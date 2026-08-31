---
title: What is transfer learning?
source: https://www.ibm.com/think/topics/transfer-learning
author:
- '[[Jacob  Murel Ph.D.]]'
- '[[Eda Kavlakoglu]]'
published: 2024-12-06
created: 2026-08-31
description: "What is transfer learning? Learn how this machine learning technique fixes improves model generalizability and performance."
---

## What is transfer learning?

Transfer learning is a [machine learning](https://www.ibm.com/think/topics/machine-learning) technique in which knowledge gained through one task or dataset is used to improve model performance on another related task or different dataset.<sup>1</sup> In other words, transfer learning uses what has been learned in one setting to improve generalization in another setting.<sup>2</sup>

Transfer learning has many applications, from solving regression problems in [data science](https://www.ibm.com/think/topics/data-science) to training [deep learning](https://www.ibm.com/think/topics/deep-learning) models. Indeed, it is particularly appealing for the latter given the large amount of data needed to create deep [neural networks](https://www.ibm.com/think/topics/neural-networks).

Traditional learning processes build a new model for each new task, based on the available labeled data. This is because traditional machine learning algorithms assume training and test data come from the same feature space, and so if the data distribution changes, or the trained model is applied to a new dataset, users must retrain a newer model from scratch, even if attempting a similar task as the first model (e.g. sentiment analysis classifier of movie reviews versus song reviews). Transfer learning algorithms, however, takes already-trained models or networks as a starting point. It then applies that model’s knowledge gained in an initial source task or data (e.g. classifying movie reviews) towards a new, yet related, target task or data (e.g. classifying song reviews).<sup>3</sup>

## Advantages and disadvantages of transfer learning

### Advantages

- **Computational costs.** Transfer learning reduces the requisite computational costs to build models for new problems. By repurposing pretrained models or pretrained networks to tackle a different task, users can reduce the amount of model training time, training data, processor units, and other computational resources. For instance, a fewer number of epochs—i.e. passes through a dataset—may be needed to achieve a desired learning rate. In this way, transfer learning can accelerate and simplify model training processes.
- **Dataset size.** Transfer learning particularly helps alleviate difficulties involved in acquiring large datasets. For instance, [large language models](https://www.ibm.com/think/topics/large-language-models) (LLMs) require large amounts of training data to obtain optimal performance. Quality publicly available datasets can be limited, and producing sufficient manually labelled data can be time-consuming and expensive.
- **Generalizability.** While transfer learning aids model optimization, it can further increase a model’s generalizability. Because transfer learning involves retraining an existing model with a new dataset, the retrained model will consist of knowledge gained from multiple datasets. It will potentially display better performance on a wider variety of data than the initial base model trained on only one type of dataset. Transfer learning can thus inhibit [overfitting](https://www.ibm.com/think/topics/overfitting).<sup>4</sup>

Of course, the transfer of knowledge from one domain to another cannot offset the negative impact of poor-quality data. Preprocessing techniques and feature engineering, such as data augmentation and feature extraction, are still necessary when using transfer learning.

### Disadvantages

It is less the case that there are disadvantages inherent to transfer learning than that there are potential negative consequences that result from its misapplication. Transfer learning works best when three conditions are met:

- both learning tasks are similar
- source and target datasets data distributions do not vary too greatly
- a comparable model can be applied to both tasks

When these conditions are not met, transfer learning can negatively affect model performance. Literature refers to this as *negative transfer*. Ongoing research proposes a variety of tests for determining whether datasets and tasks meet the above conditions, and so will not result in negative transfer.<sup>5</sup> Distant transfer is one method developed to correct for negative transfer that results from too great a dissimilarity in the data distributions of source and target datasets.<sup>6</sup>

Note that there is no widespread, standard metric to determine similarity between tasks for transfer learning. A handful of studies, however, propose different evaluation methods to predict similarities between datasets and machine learning tasks, and so viability for transfer learning.<sup>7</sup>

## Types of transfer learning

There are three adjacent practices or sub-settings of transfer learning. Their distinction from one another—as well as transfer learning more broadly—largely result from changes in the relationship between the source domain, target domain, and tasks to be completed.<sup>8</sup>

- **Inductive transfer.** This is when the source and target tasks are different, regardless of any difference or similitude between the target and source domains (i.e. datasets). This can manifest in computer vision models when architectures pretrained for feature extraction on large datasets are then are adopted for further training on a specific task, such as [object detection.](https://www.ibm.com/think/topics/object-detection) Multitask learning, which consists of simultaneously learning two different tasks (such as image classification and object detection) on the same dataset, can be considered a form of inductive transfer.<sup>9  

 </sup>
- **Unsupervised learning.** This is similar to inductive transfer, as the target and source tasks are different. But in inductive transfer, source and/or target data is often labeled. Per its name, unsupervised transfer learning is [unsupervised](https://www.ibm.com/think/topics/unsupervised-learning), meaning there is no manually labeled data.<sup>10</sup> By comparison, inductive transfer can be considered [supervised learning](https://www.ibm.com/think/topics/supervised-learning). One common application of unsupervised learning is fraud detection. By identify common patterns across an unlabeled dataset of transactions, a model can further learn to identify deviating behaviors as possible fraud.
- **Transductive transfer.** This occurs when the source and target tasks are the same, but the datasets (or domains) are different. More specifically, the source data is typically labelled while the target data is unlabeled. Domain adaptation is a form of transductive learning, as it applies knowledge gained from performing a task on one data distribution towards the same task on another data distribution.<sup>11</sup> An example of transductive transfer learning is the application of a text classification model trained and tested on restaurant reviews to classify movie reviews.

### Transfer learning versus finetuning

Transfer learning is distinct from finetuning. Both, admittedly, reuse preexisting machine learning models as opposed to training new models. But the similarities largely end there. Finetuning refers to the process of further training a model on a task-specific dataset to improve performance on the initial, specific task for which the model was built. For instance, one may create a general purpose object detection model using massive imagesets such as COCO or ImageNet and then further train the resulting model on a smaller, labeled dataset specific for car detection. In this way, a user finetunes an object detection model for car detection. By contrast, transfer learning signifies when users adapt a model to a new, related problem as opposed to the same problem.

## Transfer learning use cases

There are many applications of transfer learning in real-world machine learning and [artificial intelligence](https://www.ibm.com/think/topics/artificial-intelligence) settings. Developers and data scientists can use transfer learning to aid in a myriad of tasks and combine it with other learning approaches, such as reinforcement learning.

One salient issue affecting transfer learning in NLP is feature mismatch. Features in different domains can have different meanings, and so connotations (e.g. *light* signifying weight and optics). This disparity in feature representations affects sentiment classification tasks, language models, and more. Deep learning-based models—in particular, word embeddings—show promise in correcting for this, as they can adequately capture semantic relations and orientations for domain adaptation tasks.<sup>12</sup>

Because of difficulties in acquiring sufficient manually labeled data for diverse computer vision tasks, a wealth of research examines transfer learning applications with [convolutional neural networks](https://www.ibm.com/think/topics/convolutional-neural-networks) (CNNs). One notable example is ResNet, a pretrained model architecture that demonstrates improved performance in image classification and object detection tasks.<sup>13</sup> Recent research investigates the renowned ImageNet dataset for transfer learning, arguing that (contra computer vision folk wisdom) only small subsets of this dataset are needed to train reliably generalizable models.<sup>14</sup> Many transfer learning tutorials for computer vision use both or either ResNet and ImageNet with TensorFlow’s keras library.

## Footnotes

<sup>1</sup> Emilio Soria Olivas, Jose David Martin Guerrero, Marcelino Martinez Sober, Jose Rafael Magdalena Benedito, Antonio Jose Serrano Lopez. *Handbook of Research on Machine Learning Applications and Trends: Algorithms, Methods, and Techniques*. Information Science Reference. 2009.

<sup>2</sup> Ian Goodfellow, Yoshua Bengio, and Aaron Courville. *Deep Learning*. MIT Press. 2016.

<sup>3</sup> Jiawei Han, Micheline Kamber, Jian Pei. *Data Mining: Concepts and Techniques*. 3rd edition. Elsevier. 2012.

<sup>4</sup> Jindong Wang and Yiqiang Chen. *Introduction to Transfer Learning: Applications and Methods*. Springer. 2023.

<sup>5</sup> Wen Zhang, Lingfei Deng, Lei Zhang, Dongrui Wu. “A Survey on Negative Transfer.” *IEEE/CAA Journal of Automatica Sinica*. Vol. 10, No. 2, 2023, pp. 305–329.  [https://arxiv.org/abs/2009.00909](https://arxiv.org/abs/2009.00909) .

<sup>6</sup> Ben Tan, Yangqiu Song, Erheng Zhong, Qiang Yang. “Transitive Transfer Learning.” *Proceedings of the 21st ACM SIGKDD International Conference on Knowledge Discovery and Data Mining*. 2015, pp. 1155–1164.  [https://dl.acm.org/doi/10.1145/2783258.2783295](https://dl.acm.org/doi/10.1145/2783258.2783295) . Ben Tan, Yu Zhang, Sinno Jialin Pan, Qiang Yang. “Domain Distant Transfer.” *Proceedings of the Thirty-First AAAI Conference on Artificial Intelligence*. 2017, pp. 2604–2610.  [https://dl.acm.org/doi/10.5555/3298483.3298614](https://dl.acm.org/doi/10.5555/3298483.3298614) .

<sup>7</sup> Changjian Shui, Mahdieh Abbasi, Louis-Émile Robitaille, Boyu Wang, Christian Gagné. “A Principled Approach for Learning Task Similarity in Multitask Learning.” *Proceedings of the Twenty-Eighth International Joint Conference on Artificial Intelligence*. 2019, pp. 3446–3452.  [https://www.ijcai.org/proceedings/2019/0478.pdf](https://www.ijcai.org/proceedings/2019/0478.pdf) . Kshitij Dwivedi and Gemma Roig. “Representation Similarity Analysis for Efficient Task Taxonomy & Transfer Learning.” *Proceedings of the Conference on Computer Vision and Pattern Recognition*. 2019, pp. 12387–12396.  [https://openaccess.thecvf.com/.../CVPR_2019_paper.pdf](https://openaccess.thecvf.com/content_CVPR_2019/papers/Dwivedi_Representation_Similarity_Analysis_for_Efficient_Task_Taxonomy__Transfer_Learning_CVPR_2019_paper.pdf) . Javier García, Álvaro Visús, Fernando Fernández. “A taxonomy for similarity metrics between Markov decision processes.” *Machine Learning*, Vol. 111. 2022, pp. 4217–4247.  [https://link.springer.com/article/10.1007/s10994-022-06242-4](https://link.springer.com/article/10.1007/s10994-022-06242-4) .

<sup>8</sup> Asmaul Hosna, Ethel Merry, Jigmey Gyalmo, Zulfikar Alom, Zeyar Aung, Mohammad Abdul Azim. “Transfer learning: a friendly introduction.” *Journal of Big Data*, Vol. 9, 2022.  [https://journalofbigdata.springeropen.com/articles/10.1186/s40537-022-00652-w](https://journalofbigdata.springeropen.com/articles/10.1186/s40537-022-00652-w) . Sinno Jialin Pan, Qiang Yang. “A Survey on Transfer Learning.” *IEEE Transactions on Knowledge and Data Engineering*, Vol. 22, No. 10, 2010, pp. 1345–1359.  [https://ieeexplore.ieee.org/document/5288526](https://ieeexplore.ieee.org/document/5288526) .

<sup>9</sup> Sinno Jialin Pan, Qiang Yang. “A Survey on Transfer Learning.” *IEEE Transactions on Knowledge and Data Engineering*, Vol. 22, No. 10, 2010, pp. 1345–1359.  [https://ieeexplore.ieee.org/document/5288526](https://ieeexplore.ieee.org/document/5288526) . Ricardo Vilalta. “Inductive Transfer.” *Encyclopedia of Machine Learning and Data Mining*. Springer. 2017.

<sup>10</sup> Sinno Jialin Pan, Qiang Yang. “A Survey on Transfer Learning.” *IEEE Transactions on Knowledge and Data Engineering*, Vol. 22, No. 10, 2010, pp. 1345–1359.  [https://ieeexplore.ieee.org/document/5288526](https://ieeexplore.ieee.org/document/5288526) .

<sup>11</sup> Sinno Jialin Pan, Qiang Yang. “A Survey on Transfer Learning.” *IEEE Transactions on Knowledge and Data Engineering*, Vol. 22, No. 10, 2010, pp. 1345–1359.  [https://ieeexplore.ieee.org/document/5288526](https://ieeexplore.ieee.org/document/5288526) . Ian Goodfellow, Yoshua Bengio, Aaron Courville. *Deep Learning*. MIT Press. 2016.

<sup>12</sup> Qiang Yang. *Transfer Learning*. Cambridge University Press. 2020. Eyal Ben-David, Carmel Rabinovitz, Roi Reichart. “PERL: Pivot-based Domain Adaptation for Pre-trained Deep Contextualized Embedding Models.” *Transactions of the Association for Computational Linguistics*, Vol. 8, 2020, pp. 504–521.  [https://aclanthology.org/2020.tacl-1.33.pdf](https://aclanthology.org/2020.tacl-1.33.pdf) .

<sup>13</sup> Kaiming He, Xiangyu Zhang, Shaoqing Ren, Jian Sun. “Deep Residual Learning for Image Recognition.” *IEEE Conference on Computer Vision and Pattern Recognition (CVPR)*. 2016, pp. 770–778.  [https://ieeexplore.ieee.org/document/7780459](https://ieeexplore.ieee.org/document/7780459) .

<sup>14</sup> Minyoung Huh, Pulkit Agrawal, Alexei Efros. “What makes ImageNet good for transfer learning?” Berkeley Artificial Intelligence Research Laboratory (BAIR). 2017.  [https://people.csail.mit.edu/minhuh/papers/analysis/](https://people.csail.mit.edu/minhuh/papers/analysis/) .
