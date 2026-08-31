---
title: What is semantic segmentation?
source: https://www.ibm.com/think/topics/semantic-segmentation
author:
- '[[Mesh Flinders]]'
published: 2024-12-03
created: 2026-08-31
description: "Semantic segmentation is one of three sub-tasks in the overall process of image segmentation that helps computers understand visual information."
---

## What is semantic segmentation?

Semantic segmentation is a [computer vision](https://www.ibm.com/think/topics/computer-vision) task that assigns a class label to pixels using a [deep learning](https://www.ibm.com/think/topics/deep-learning) (DL) algorithm. It is one of three sub-categories in the overall process of image segmentation that helps computers understand visual information.

Semantic segmentation identifies collections of pixels and classifies them according to various characteristics. The other two sub-categories of image segmentation are [instance segmentation](https://www.ibm.com/think/topics/instance-segmentation) and panoptic segmentation.

## Image segmentation

Image segmentation is an end-to-end image analysis process that divides a digital image into multiple segments and classifies the information contained in each region.

The three kinds of image segmentation tasks—semantic, instance and panoptic segmentation—assign labels to individual pixels in the image to mark the specific boundaries and shapes of different objects and regions in the image, classifying them by using information like color, contrast, placement within the image and other attributes.

Whereas semantic segmentation labels every single pixel contained in an image by its semantic class, instance segmentation and panoptic segmentation are used for different classification tasks.

*Instance segmentation* models focus only on the semantic classes contained in an image that can be counted: entities and objects like people, animals, trees, cars or fire hydrants. It detects any individual object, or *instance*, and then outputs a segmentation mask and specific identifier tag for each.

*Panoptic segmentation* models entail both kinds of information: they perform semantic segmentation *and* detect and segment individual object instances, delivering a more complete analysis of the image by assigning each pixel both a semantic label and (where appropriate) a unique instance identifier.

## Why is semantic image segmentation important?

Semantic segmentation tasks help machines distinguish the different object classes and background regions in an image. With the rise of [artificial intelligence (AI)](https://www.ibm.com/think/topics/artificial-intelligence) and [machine learning (ML)](https://www.ibm.com/think/topics/machine-learning), image segmentation and the creation of segmentation maps play an important role in training computers to recognize important context in digital images such as landscapes, photos of people, medical images and much more.

Image segmentation learning models enable machines to interpret visual information similarly to the human brain. While image segmentation models do share certain uses with object detection models, they differ in a critical aspect: They identify different entities contained in an image at the pixel level, rather than approximate that information with a bounding box. Essentially, while an image classification model can determine *what* is contained in an image (but not perform any localization), and an object detection model can determine *where* in an image the object is located, to determine the specific shapes and boundaries of entities in the image requires an image segmentation model.<sup>1</sup>

With the increasing success of deep learning algorithms at helping machines interpret images as data, machines are getting better and better at identifying objects. While the task of image classification helps the machine understand what information is contained in an image, semantic segmentation lets the machine identify the precise locations of different kinds of visual information, as well as where each begins and ends.

## How does semantic segmentation work?

Semantic segmenation models create a segmentation map of an input image. A segmentation map is, essentially, a reconstruction of the original image in which each pixel has been color coded by its semantic class to create segmentation masks. A segmentation mask is simply a portion of the image that has been differentiated from other regions of the image. For example, a segmentation map a tree in an empty field would likely contain three segmentation masks: one for the tree, one for the ground and one for the sky in the background.

To do so, semantic segmentation models use complex [neural networks](https://www.ibm.com/think/topics/neural-networks) to both accurately group related pixels together into segmentation masks and correctly recognize the real-world semantic class for each group of pixels (or segment). These deep learning (DL) methods require a model to be trained on large pre-labeled datasets annotated by human experts, adjusting its weights and biases through machine learning techniques like backpropagation and [gradient descent](https://www.ibm.com/think/topics/gradient-descent).

DL methods have come to replace other "traditional" machine learning algorithms, like Support Vector Machines (SVM) and [Random Forest](https://www.ibm.com/think/topics/random-forest). Though deep neural networks require more time, data and computational resources to train, they outperform other methods and quickly became the chosen approach after early innovations proved successful.

## Datasets for training

The task of classifying image data accurately requires datasets consisting of pixel values that represent masks for different objects or class labels contained in an image. Typically, because of the complexity of the training data involved in image segmentation, these kinds of datasets are larger and more complex than other machine learning datasets.

Many open source image segmentation datasets are available, spanning a wide variety of semantic classes with thousands of examples and detailed annotations for each. For example, imagine a segmentation problem where computer vision in a driverless car is being taught to recognize all the various objects it will need to brake for, like pedestrians, bicycles, and other cars. The car's computer vision must be trained to consistently recognize all of them or else it might not always tell the car to brake; its training must also be extremely accurate and precise, or else it might *constantly* brake after mistakenly classifying innocuous visuals as objects of concern.

Here are some of the more popular open source datasets used in image and semantic segmentation:

**Pascal Visual Object Classes (Pascal VOC):** The Pascal VOC dataset consists of many different object classes, bounding boxes and robust segmentation maps.

**MS COCO:** MS COCO contains around 330,000 images and annotations for many tasks including detection, segmentation and image captioning.

**Cityscapes:** The popular cityscapes dataset interprets data from urban environments and is made up of 5,000 images with 20,000 annotations and 30 class labels.

## Semantic segmentation models

Trained models demand a robust architecture to function properly. Here are some widely used semantic segmentation models.

### Fully convolutional networks (FCNs)

A fully convolutional network (FCN) is a state-of-the-art neural network architecture used for semantic segmentation that depends on several connected, convolutional layers. Whereas traditional [convolutional neural network (CNN)](https://www.ibm.com/think/topics/convolutional-neural-networks) architecture is made up of convolutional layers and flat layers that output single labels, FCN models replace some of those flat layers with 1:1 convolutional blocks that can further extract more information about the image. Avoiding the use of flat, denser layers in favor of convolution, pooling or upsampling layers makes FCN networks easier to train.

- **Upsampling and downsampling:** As the network gathers more convolutional layers, the image size is reduced, resulting in less spatial information as well as pixel-level information, a necessary process known as downsampling. At the very end of this process, data engineers perform image optimization by expanding, or upsampling, the feature map that’s been created back to the shape of the input image.
- **Max-pooling:** Max-pooling is another critical tool in the process of extracting information from regions of an image and analyzing them. Max-pooling chooses the greatest element in a region being analyzed so its output can result in a feature map containing the most prominent features from the previous feature map.

### U-Nets

The U-Net architecture is a modification of the original FCN architecture that was introduced in 2015 and consistently achieves better results. It consists of two parts, an encoder and a decoder. While the encoder stacks convolutional layers that are consistently downsampling the image to extract information from it, the decoder rebuilds the image features using the process of deconvolution. U-net architecture is primarily used in the medical field to identify cancerous and non-cancerous tumors in the lungs and brain.

- **Skip-connections:** An important innovation introduced to FCNs by U-Net is known as skip-connections, used to connect the output of one convolutional layer to another that is non-adjacent. This skip-connections process reduces data loss during downsampling, enable higher-resolution output. Each convolutional layer is independently upsampled and combined with features from other layers until the final output accurately represents the image being analyzed.

### DeepLab

The DeepLab semantic segmentation model was developed by Google in 2015 to further improve on the architecture of the original FCN and deliver even more precise results. While the stacks of layers in an FCN model reduce image resolution significantly, DeepLab’s architecture uses a process called atrous convolution to upsample the data. With the atrous convolution process, convolution kernels can remove information from an image and leave gaps between the kernel parameters.

DeepLab’s approach to dilated convolution pulls data out of the larger field of view while still maintaining the same resolution. The feature space is then pulled through a fully connected conditional random field algorithm (CRF) so more detail can be captured and utilized for pixel-wise loss function, resulting in a clearer, more accurate segmentation mask.

### Pyramid Scene Parsing Network (PSPNet)

In 2017, a new segmentation algorithm for image segmentation was introduced. PSPNet deploys a pyramid parsing module that gathers contextual image datasets at a higher accuracy rate than its predecessors. Like its predecessors, the PSPNet architecture employs the encoder-decoder approach, but where DeepLab applied upscaling to make its pixel-level calculations, PSPNet adds a new pyramid pooling layer to achieve its results. PSPNet’s multi-scale pooling allows it to analyze a wider window of image information than other models.

## Semantic segmentation use cases

Self-driving cars use semantic segmentation to see the world around them and react to it in real-time. Semantic segmentation separates what the car sees into categorized visual regions like lanes on a road, other cars and intersections. The knowledge provided to the car by semantic segmentation enables it to navigate safely and reach its destination as well as take important actions in response to unexpected events like a pedestrian crossing the road or another car braking suddenly.

Lots of common medical procedures such as CT scans, X-rays and MRIs rely on image analysis. While this task has typically fallen to a medical professional in the past, today, medical image segmentation models are achieving similar results. By analyzing the image and drawing exact boundaries around the various objects in it, AI equipped with semantic segmentation can help detect anomalies and even suggest potential diagnoses.

Farmers are using AI, automation and semantic segmentation to help detect infestations in their crops and even automate the spraying of pesticides. Computer-vision can tell the farmer which parts of a field are potentially infected or at risk and an automated system can take action to eliminate a pest.

Semantic segmentation is frequently used to enable cameras to shift between portrait and landscape mode, add or remove a filter or create an affect. All the popular filters and features on apps like Instagram and TikTok use semantic segmentation to identify cars, buildings, animals and other objects so the chosen filters or effects can be applied.

## Footnotes

<sup>1</sup>[“Practical Machine Learning for Computer Vision”](https://learning.oreilly.com/library/view/practical-machine-learning/9781098102357/), Lakshmanan, Valliappa, Gorner, Martin and Gillard, Ryan, O’Reilly Media, July, 2021
