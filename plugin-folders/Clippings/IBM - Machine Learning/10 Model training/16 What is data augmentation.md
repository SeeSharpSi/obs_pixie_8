---
title: What is data augmentation?
source: https://www.ibm.com/think/topics/data-augmentation
author:
- '[[Jacob  Murel Ph.D.]]'
- '[[Eda Kavlakoglu]]'
published: 2024-12-05
created: 2026-08-31
description: "Data augmentation uses pre-existing data to create new data samples that can improve model optimization and generalizability."
---

## What is data augmentation?

Data augmentation uses pre-existing data to create new data samples that can improve model optimization and generalizability.

In its most general sense, data augmentation denotes methods for supplementing so-called incomplete [datasets](https://www.ibm.com/think/topics/dataset) by providing missing data points in order to increase the dataset’s analyzability.<sup>1</sup> This manifests in [machine learning](https://www.ibm.com/topics/machine-learning) by generating modified copies of pre-existing data to increase the size and diversity of a dataset. Thus, with respect to machine learning, augmented data may be understood as artificially supplying potentially absent real-world data.

Data augmentation improves machine learning model optimization and generalization. In other words, data augmentation can reduce [overfitting](https://www.ibm.com/topics/overfitting) and improve model robustness.<sup>2</sup> That large, diverse datasets equal improved model performance is an axiom of machine learning. Nevertheless, for a number of reasons—from [ethics](https://www.ibm.com/impact/ai-ethics) and [privacy](https://research.ibm.com/blog/ai-privacy-toolkit) concerns to simply the time-consuming effort of manually compiling necessary data—acquiring sufficient data can be difficult. Data augmentation provides one effective means of increasing dataset size and variability. In fact, researchers widely use data augmentation to correct imbalanced datasets.<sup>3</sup>

Many deep learning frameworks, such as [PyTorch](https://www.ibm.com/think/topics/pytorch), Keras, and Tensorflow provide functions for augmenting data, principally image datasets. The Python package [Ablumentations](https://albumentations.ai/) (available on Github) is also adopted in many open source projects. Albumentations allows for augmenting image and text data.

### Augmented data vs. synthetic data

Note that data augmentation is distinct from synthetic data. Admittedly, both are [generative algorithms](https://research.ibm.com/blog/what-is-generative-AI) that add new data into a data collection in order to improve the performance of machine learning models. [Synthetic data](https://www.ibm.com/think/topics/synthetic-data), however, refers to the automatic generation of entirely artificial data. An example is using computer-generated images—as opposed to real-world data—to train an object detection model. By contrast, data augmentation copies existing data and transforms those copies to increase the diversity and amount of data in a given set.

## Data augmentation techniques

There are a variety of data augmentation methods. The specific techniques used for augmenting data depend upon the nature of data with which a user is working. Note that data augmentation is typically implemented during preprocessing on the training dataset. Some studies investigate the effect of augmentation on the validation or test set, but augmentation applications outside of training sets are rarer.<sup>4</sup>

### Image augmentation

Data augmentation has been widely implemented in research for a range of [computer vision](https://www.ibm.com/topics/computer-vision) tasks, from image classification to [object detection](https://www.ibm.com/topics/object-detection). As such, there is a wealth of research on how augmented images improve the performance of state-of-the-art [convolutional neural networks](https://www.ibm.com/topics/convolutional-neural-networks) (CNNs) in image processing.

Many tutorials and non-academic resources classify image data augmentation into two categories: geometric transformations and photometric (or, color space) transformations. Both consist of relatively simple image file manipulation. The first category denotes techniques that alter the space and layout of the original image, such as resizing, zooming, or changes in orientation (for example, horizontal flip). Photometric transformations alter an image’s RGB (red-green-blue) channels. Examples of photometric transformation include saturation adjustment and grayscaling an image.<sup>5</sup>

![Example of basic image augmentation for cat image](https://assets.ibm.com/is/image/ibm/data-augmentation-image-augment?ts=1763387103642&dpr=off)

Some sources categorize noise injection with geometric transformations,<sup>6</sup> while others classify it with photometric transformations.<sup>7</sup> Noise injection inserts random black, white, or color pixels into an image according to a Gaussian distribution.

![Example of noise injection for image augmentation](https://assets.ibm.com/is/image/ibm/data-augmentation-noise?ts=1763387103808&dpr=off)

As noise injection illustrates, the binary classification of image augmentation techniques into geometric and photometric fails to cover the whole range of possible augmentation strategies. Excluded image augmentation techniques are kernel filtering (sharpening or blurring an image) and image mixing. An example of the latter is random cropping and patching. This technique randomly samples sections from several images to create a new image. This new image is a composite made from the sampled sections of the input images. A related technique is random erasing, which deletes a random portion of an image.<sup>8</sup> Such tasks are useful in image recognition tasks, as real-world use cases may require machines to identify partially obscured objects.

![Visualization for random cropping for golden retriever image](https://assets.ibm.com/is/image/ibm/data-augmentation-random?ts=1763387103979&dpr=off)

Instance-level augmentation is another augmentation. Instance-level augmentation essentially copies labeled regions (for example, bounding boxes) from one image and inserts them onto another image. Such an approach trains the image to identify objects against different backgrounds as well as objects obscured by other objects. Instance-level augmentation is a particularly salient approach for region-specific recognition tasks, such as object detection and image segmentation tasks.<sup>9</sup>

### Text augmentation

Like image augmentation, text data augmentation consists of many techniques and methods that are used across a range of [natural language processing](https://www.ibm.com/topics/natural-language-processing) (NLP) tasks. A few resources divide text augmentation into rule-based (or “easy”) and neural methods. Of course, as with the binary division of image augmentation techniques, this categorization is not all-encompassing.

Rule-based approaches include relatively simple find-and-replace techniques, such as random deletion or insertion. Rule-based approaches also encompass synonym replacement. In this strategy, one or more words in a string are replaced with their respective synonyms as recorded in predefined thesaurus, such as WordNet or the Paraphrase Database. Sentence inversion and passivation, in which the object and subject are swapped, are also examples of rule-based approaches.<sup>10</sup>

![Chart visualization of rule-based text augmentations](https://assets.ibm.com/is/image/ibm/data-augmentation-text-augment?ts=1763387104303&dpr=off)

Per their classification, neural methods utilize neural networks to generate new text samples from the input data. One notable neural method is back-translation. This uses machine translation to translate input data into a target language and then back into the original input language. In this way, back-translation leverages linguistic variances that result in automated translations to generate semantic variances in single-language dataset for the purpose of augmentation. Research suggests this is effective for improving machine translation model performance.<sup>11</sup>

![Visualization of translation augmentation with phrase I am dancing in the club](https://assets.ibm.com/is/image/ibm/data-augmentation-translate-augment?ts=1763387104474&dpr=off)

Mix-up text augmentations is another strategy. This approach deploys rule-based deletion and insertion methods using neural network embeddings. Specifically, pre-trained transformers (for example, BERT) generate word or sentence-level embeddings of text, transforming text into vector points, as in a [bag of words](https://www.ibm.com/topics/bag-of-words) model. The transformation of text into vector points generally aims to capture linguistic similitude, that is, words or sentences nearer one another in vector space are believed to share similar meanings or frequency. Mix-up augmentations interpolates text strings within a specified distance of one another to produce new data that is an aggregate of the input data.<sup>12</sup>

## Recent research

Many users struggle with identifying which data augmentation strategies to implement. Do data augmentation techniques vary in efficacy between datasets and tasks? Comparative research on data augmentation techniques suggests that multiple forms of augmentation have a greater positive impact than one, but determining the optimal combination of techniques is dataset and task dependent.<sup>13</sup> But how does one go about selecting the optimal techniques?

### Automated augmentation

To address this issue, research has turned to automated data augmentation. One automated augmentation approach uses [reinforcement learning](https://www.ibm.com/topics/reinforcement-learning) to identify augmentation techniques that return the highest validation accuracy on a given dataset.<sup>14</sup> This approach has shown to implement strategies that improve performance on both in and out of sample data.<sup>15</sup> Another promising approach to automated augmentation identifies and augments false positives from classifier outputs. In this way, automatic augmentation identifies the best strategies to correct for frequently misclassified items.<sup>16</sup>

### Generative networks

More recently, research has turned to generative networks and models to identify task-dependent<sup>17</sup> and class-dependent<sup>18</sup> optimal augmentation strategies. This includes work with generative adversarial networks (GANs). GANs are [deep learning](https://www.ibm.com/topics/deep-learning) networks typically used to generate synthetic data, and recent research investigates their use for data augmentation. A few experiments, for instance, suggest that synthetic data augmentations of medical image sets improve classification<sup>19</sup> and segmentation<sup>20</sup> model performance more than classic augmentations. Relatedly, research in text augmentation leverages [large language models](https://www.ibm.com/topics/large-language-models) (LLMs) and [chatbots](https://www.ibm.com/topics/chatbots) to generate augmented data. These experiments use LLMs to generate augmented samples of input data with mix-up and synonymizing techniques, showing a greater positive impact for text classification models than classic augmentation.<sup>21</sup>

Researchers and developers widely adopt data augmentation techniques when training models for various machine learning tasks. By contrast, synthetic data is a comparatively newer area of research. Comparative experiments on synthetic versus real data show mixed results, with models trained entirely on synthetic data sometimes outperforming, sometimes underperforming models trained on real-world data. Perhaps unsurprisingly, this research suggests synthetic data is most useful when it reflects characteristics of real-world data.<sup>22</sup>

## Footnotes

All links reside outside IBM.com.

<sup>f</sup> Martin Tanner and Wing Hung Wong, “The Calculation of Posterior Distributions by Data Augmentation,” *Journal of the American Statistical Association*, Vol. 82, No. 398 (1987), pp. 528-540.

<sup>2</sup> Sylvestre-Alvise Rebuffi, Sven Gowal, Dan Andrei Calian, Florian Stimberg, Olivia Wiles, and Timothy A Mann, “[Data Augmentation Can Improve Robustness](https://proceedings.neurips.cc/paper_files/paper/2021/hash/fb4c48608ce8825b558ccf07169a3421-Abstract.html),” Advances in Neural Information Processing Systems, Vol. 34, 2021.

<sup>3</sup> Manisha Saini and Seba Susan, “[Tackling class imbalance in computer vision: A contemporary review,” Artificial Intelligence Review](https://link.springer.com/article/10.1007/s10462-023-10557-6), Vol. 54, 2023.

<sup>4</sup> Fabio Perez, Cristina Vasconcelos, Sandra Avila, and Eduardo Valle, “[Data Augmentation for Skin Lesion Analysis](https://link.springer.com/chapter/10.1007/978-3-030-01201-4_33),” OR 2.0 Context-Aware Operating Theaters, Computer Assisted Robotic Endoscopy, Clinical Image-Based Procedures, and Skin Image Analysis, 2018.

<sup>5</sup> Connor Shorten and Taghi M. Khoshgoftaa, “[A survey on Image Data Augmentation for Deep Learning](https://journalofbigdata.springeropen.com/articles/10.1186/s40537-019-0197-0),” *Journal of Big Data*, 2019.

<sup>6</sup> Duc Haba, *Data Augmentation with Python*, Packt Publishing, 2023.

<sup>7</sup> Mingle Xu, Sook Yoon, Alvaro Fuentes, and Dong Sun Park, “[A Comprehensive Survey of Image Augmentation Techniques for Deep Learning](https://www.sciencedirect.com/science/article/pii/S0031320323000481),” *Patter Recognition*, Vol. 137.

<sup>8</sup> Connor Shorten and Taghi M. Khoshgoftaa, “[A survey on Image Data Augmentation for Deep Learning](https://journalofbigdata.springeropen.com/articles/10.1186/s40537-019-0197-0),” *Journal of Big Data*, 2019, . Terrance DeVries and Graham W. Taylor, “[Improved Regularization of Convolutional Neural Networks with Cutout](https://arxiv.org/abs/1708.04552),” 2017.

<sup>9</sup> Zhiqiang Shen, Mingyang Huang, Jianping Shi, Xiangyang Xue, and Thomas S. Huang, “[Towards Instance-Level Image-To-Image Translation](https://openaccess.thecvf.com/content_CVPR_2019/html/Shen_Towards_Instance-Level_Image-To-Image_Translation_CVPR_2019_paper.html),” Proceedings of the IEEE/CVF Conference on Computer Vision and Pattern Recognition (CVPR), 2019, pp. 3683-3692, . Golnaz Ghiasi, Yin Cui, Aravind Srinivas, Rui Qian, Tsung-Yi Lin, Ekin D. Cubuk, Quoc V. Le, and Barret Zoph, “[Simple Copy-Paste Is a Strong Data Augmentation Method for Instance Segmentation](https://openaccess.thecvf.com/content/CVPR2021/html/Ghiasi_Simple_Copy-Paste_Is_a_Strong_Data_Augmentation_Method_for_Instance_CVPR_2021_paper.html),” Proceedings of the IEEE/CVF Conference on Computer Vision and Pattern Recognition (CVPR), 2021, pp. 2918-2928.

<sup>10</sup> Connor Shorten, Taghi M. Khoshgoftaar and Borko Furht, “[Text Data Augmentation for Deep Learning](https://journalofbigdata.springeropen.com/articles/10.1186/s40537-021-00492-0),” *Journal of Big Data*, 2021, . Junghyun Min, R. Thomas McCoy, Dipanjan Das, Emily Pitler, and Tal Linzen, “[Syntactic Data Augmentation Increases Robustness to Inference Heuristics](https://aclanthology.org/2020.acl-main.212/),” Proceedings of the 58th Annual Meeting of the Association for Computational Linguistics, 2020, pp. 2339-2352.

<sup>11</sup> Connor Shorten, Taghi M. Khoshgoftaar, and Borko Furht, “[Text Data Augmentation for Deep Learning](https://journalofbigdata.springeropen.com/articles/10.1186/s40537-021-00492-0),” *Journal of Big Data*, 2021, . Rico Sennrich, Barry Haddow, and Alexandra Birch, “[Improving Neural Machine Translation Models with Monolingual Data](https://aclanthology.org/P16-1009/),” Proceedings of the 54th Annual Meeting of the Association for Computational Linguistics, 2016, pp. 86-96.

<sup>12</sup> Connor Shorten, Taghi M. Khoshgoftaar, and Borko Furht, “[Text Data Augmentation for Deep Learning](https://journalofbigdata.springeropen.com/articles/10.1186/s40537-021-00492-0),” *Journal of Big Data*, 2021. Lichao Sun, Congying Xia, Wenpeng Yin, Tingting Liang, Philip Yu, and Lifang He, “[Mixup-Transformer: Dynamic Data Augmentation for NLP Tasks](https://aclanthology.org/2020.coling-main.305/),” Proceedings of the 28th International Conference on Computational Linguistics, 2020. Hongyu Guo, Yongyi Mao, and Richong Zhang, “[Augmenting Data with Mixup for Sentence Classification: An Empirical Study](https://arxiv.org/abs/1905.08941),” 2019.

<sup>13</sup> Suorong Yang, Weikang Xiao, Mengchen Zhang, Suhan Guo, Jian Zhao, and Furao Shen, “[Image Data Augmentation for Deep Learning: A Survey](https://arxiv.org/pdf/2204.08610.pdf),” 2023. Alhassan Mumuni and Fuseini Mumuni, “[Data augmentation: A comprehensive survey of modern approaches](https://www.sciencedirect.com/science/article/pii/S2590005622000911),” Array, Vol. 16, 2022. Evgin Goveri, “[Medical image data augmentation: techniques, comparisons and interpretations](https://link.springer.com/article/10.1007/s10462-023-10453-z),” Artificial Intelligence Review, Vol. 56, 2023, pp. 12561-12605.

<sup>14</sup> Ekin D. Cubuk, Barret Zoph, Dandelion Mane, Vijay Vasudevan, and Quoc V. Le, “[AutoAugment: Learning Augmentation Strategies From Data](https://openaccess.thecvf.com/content_CVPR_2019/papers/Cubuk_AutoAugment_Learning_Augmentation_Strategies_From_Data_CVPR_2019_paper.pdf),” Proceedings of the IEEE/CVF Conference on Computer Vision and Pattern Recognition (CVPR), 2019, pp. 113-123.

<sup>15</sup> Barret Zoph, Ekin D. Cubuk, Golnaz Ghiasi, Tsung-Yi Lin, Jonathon Shlens, and Quoc V. Le, “[Learning Data Augmentation Strategies for Object Detection](https://link.springer.com/chapter/10.1007/978-3-030-58583-9_34),” Proceedings of the 16<sup>th</sup> European Conference on Computer Vision, 2020.

<sup>16</sup> Sandareka Wickramanayake, Wynne Hsu, and Mong Li Lee, “[Explanation-based Data Augmentation for Image Classification](https://proceedings.neurips.cc/paper_files/paper/2021/hash/af3b6a54e9e9338abc54258e3406e485-Abstract.html),” Advances in Neural Information Processing Systems, Vol. 34, 2021.

<sup>17</sup> rishna Chaitanya, Neerav Karani, Christian F. Baumgartner, Anton Becker, Olivio Donati, and Ender Konukoglu, “[Semi-supervised and Task-Driven Data Augmentation](https://link.springer.com/chapter/10.1007/978-3-030-20351-1_3),” Proceedings of the 26<sup>th</sup> International Conference on Information Processing in Medical Imaging, 2019.

<sup>18</sup> Cédric Rommel, Thomas Moreau, Joseph Paillard, and Alexandre Gramfort, “[ADDA: Class-wise Automatic Differentiable Data Augmentation for EEG Signals](https://iclr.cc/virtual/2022/poster/7154),” International Conference on Learning Representations, 2022.

<sup>19</sup> Maayan Frid-Adar, Idit Diamant, Eyal Klang, Michal Amitai, Jacob Goldberger, and Hayit Greenspan, “[GAN-based synthetic medical image augmentation for increased CNN performance in liver lesion classification](https://www.sciencedirect.com/science/article/abs/pii/S0925231218310749),” Neurocomputing, 2018, pp. 321-331.

<sup>20</sup> Veit Sandfort, Ke Yan, Perry Pickhardt, and Ronald Summers, “[Data augmentation using generative adversarial networks (CycleGAN) to improve generalizability in CT segmentation tasks](https://www.nature.com/articles/s41598-019-52737-x),” Scientific Reports, 2019.

<sup>21</sup> Kang Min Yoo, Dongju Park, Jaewook Kang, Sang-Woo Lee, and Woomyoung Park, “[GPT3Mix: Leveraging Large-scale Language Models for Text Augmentation](https://aclanthology.org/2021.findings-emnlp.192/),” Findings of the Association for Computational Linguistics: EMNLP 2021, pp. 2225-2239. Haixing Dai, Zhengliang Liu, Wenxiong Liao, Xiaoke Huang, Yihan Cao, Zihao Wu, Lin Zhao, Shaochen Xu, Wei Liu, Ninghao Liu, Sheng Li, Dajiang Zhu, Hongmin Cai, Lichao Sun, Quanzheng Li, Dinggang Shen, Tianming Liu, and Xiang Li, “[AugGPT: Leveraging ChatGPT for Text Data Augmentation](https://arxiv.org/abs/2302.13007),” 2023.

<sup>22</sup> Bram Vanherle, Steven Moonen, Frank Van Reeth, and Nick Michiels, “[Analysis of Training Object Detection Models with Synthetic Data](https://bmvc2022.mpi-inf.mpg.de/0833.pdf),” *33<sup>rd</sup> British Machine Vision Conference*, 2022. Martin Georg Ljungqvist, Otto Nordander, Markus Skans, Arvid Mildner, Tony Liu, and Pierre Nugues, “[Object Detector Differences When Using Synthetic and Real Training Data](https://link.springer.com/article/10.1007/s42979-023-01704-5),” *SN Computer Science*, Vol. 4, 2023. Lei Kang, Marcal Rusinol, Alicia Fornes, Pau Riba, and Mauricio Villegas, “[Unsupervised Writer Adaptation for Synthetic-to-Real Handwritten Word Recognition](https://openaccess.thecvf.com/content_WACV_2020/html/Kang_Unsupervised_Writer_Adaptation_for_Synthetic-to-Real_Handwritten_Word_Recognition_WACV_2020_paper.html),” *Proceedings of the IEEE/CVF Winter Conference on Applications of Computer Vision* (WACV), 2020, pp. 3502-3511.
