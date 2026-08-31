---
title: What is instance segmentation?
source: https://www.ibm.com/think/topics/instance-segmentation
author:
- '[[Dave Bergmann]]'
- '[[Cole Stryker]]'
published: 2024-12-03
created: 2026-08-31
description: "Instance segmentation is a deep learning-driven computer vision task that predicts
exact pixel-wise boundaries for each individual object instance in an image."
---

## What is instance segmentation?

Instance segmentation is a [deep learning](https://www.ibm.com/think/topics/deep-learning)-driven [computer vision](https://www.ibm.com/think/topics/computer-vision) task that predicts the exact pixel-wise boundaries of each individual object instance in an image.

Instance segmentation, which is a subset of the larger field of image segmentation, provides more detailed and sophisticated output than conventional object detection algorithms. Other image segmentation tasks include [semantic segmentation](https://www.ibm.com/think/topics/semantic-segmentation), which categorizes each pixel in an image by semantic class–the category of “thing” or “stuff” it represents—and panoptic segmentation, which combines the objectives of both instance segmentation and semantic segmentation.

Instance segmentation has a wide variety of [image processing](https://developer.ibm.com/articles/learn-the-basics-of-computer-vision-and-object-detection/) use cases across many industries, from analysis of medical images to detecting objects of interest in satellite imagery to enabling navigation in self-driving cars.

## Instance segmentation vs. object detection

The primary difference between instance segmentation tasks and conventional object detection is that instance segmentation predicts pixel-level boundaries of each object while object detection predicts only an object’s approximate location.

Conventional object detection methods are an evolved combination of image classification and object localization. Trained with various [machine learning](https://www.ibm.com/think/topics/machine-learning) algorithms to recognize the visual patterns of relevant categories of objects—for example, an autonomous driving model might be trained to recognize things like “car” or “pedestrian”—an object detection model analyzes the visual data of an input image to annotate any relevant object instances and generate rectangular regions, called “bounding boxes,” in which each instance is located.

Instance segmentation systems likewise detect objects in an image, but in much greater detail: rather than a bounding box that approximates the location of an object instance, instance segmentation algorithms generate a pixel-by-pixel “segmentation mask” of the precise shape and area of each instance.

Many leading instance segmentation model architectures, like Mask R-CNN, perform conventional objection detection as a preliminary step in the process of generating segmentation masks. Such “two-stage” models typically provide state-of-the-art accuracy, albeit with a tradeoff in speed.

## Instance segmentation vs. semantic segmentation

Semantic segmentation is a less complex task than instance segmentation. Unlike instance segmentation, semantic segmentation is not concerned with counting or distinguishing between different instances: the sole aim of semantic segmentation is to annotate each pixel in an image with semantic class label.

Semantic segmentation models make no distinction between *things*—classes of countable entities with distinct shapes, like “car” or “person”—and *stuff* (i.e., classes of uncountable entities with variable shapes, like “sky” or “road”).

If multiple object instances of the same class of thing are closely adjacent or overlap one another, a semantic segmentation model will simply group them together within a single image segment. Consider, for example, how a semantic segmentation model treats the cars parked closely together on each side of the street in this image.

![A side-by-side comparison of a normal city street image vs. that same image with semantic segmentation](https://assets.ibm.com/is/image/ibm/image-segmentation-diagram-semantic-4x?ts=1763391665630&dpr=off)

Conversely, instance segmentation models focus exclusively on detecting and generating segmentation masks for individual things. An instance segmentation model must be able to delineate each different object instance—even for occluded instances of the same class of object.

![A side-by-side comparison of a normal city street image vs. that same image with semantic segmentation vs. that same image with instance segmentation](https://assets.ibm.com/is/image/ibm/image-segmentation-diagram-semantic-instance-4x?ts=1763391665787&dpr=off)

## Instance segmentation vs. panoptic segmentation

Panoptic segmentation entails both semantic classification of every pixel in an image and the delineation of each different object instance.

Panoptic segmentation models can theoretically perform instance segmentation, but do so at a much greater computational cost (as their output includes additional information not necessarily relevant to instance segmentation tasks).

![A side-by-side comparison of a normal city street image vs. that same image with semantic segmentation vs. that same image with instance segmentation vs. that same image with panoptic segmentation](https://assets.ibm.com/is/image/ibm/image-segmentation-diagram-all-4x?ts=1763391666085&dpr=off)

Initial attempts at panoptic segmentation simply performed both instance segmentation and semantic segmentation separately, then combined their outputs in a post-processing step. This method is computationally inefficient and struggles to resolve discrepancies between data outputs from the semantic model and data outputs from the instance model.

More recent approaches connect a semantic segmentation “head” and instance segmentation “head” to a shared “backbone”—often a feature pyramid network (FPN)—for feature extraction: the isolation of pertinent visual data. This adds efficiency and eliminates discrepancies.

## Instance segmentation use cases

Instance segmentation is essential to a variety of computer vision tasks.

- *Medical imaging*: Instance segmentation is used to detect the specific boundaries of tissues and pathologies, like tumors

- *Autonomous driving*: Instance segmentation allows self-driving cars to accurate detect and classify cars, objects, people and road features (like traffic lights).

- *Satellite imagery*: Instance segmentation can help identify and isolate objects of interest, like distinguishing between multiple buildings along a road for GPS purposes.

- *Robotics*: Instance segmentation allows for the sorting of items, detection of defects and, similar to self-driving cars, allows robots to discern and navigate around objects in their environment.

## How does instance segmentation work?

[Deep learning](https://www.ibm.com/think/topics/deep-learning) has become essential to instance segmentation: nearly all modern image segmentation methods utilize neural networks. Though recent years have seen transformer models emerge as a viable alternative, most image segmentation methods (including those used for instance segmentation) leverage some form of [convolutional neural networks (CNNs)](https://www.ibm.com/think/topics/convolutional-neural-networks).

CNN-based instance segmentation models fall into two categories:

- *Two-stage* models, like Mask R-CNN, first perform object detection, then generate object segmentation masks
- *One-shot* (or *single stage*) models, like YOLACT, perform both tasks in parallel.

Both CNN-based and transformer-based instance segmentation models use an encoder-decoder structure, in which an encoder network is used to extract relevant data from the input image and a decoder network uses that extracted feature data to reconstruct the image with a segmentation map.

To understand instance segmentation models, it helps to understand their constituent parts.

### Convolutional neural networks (CNNs)

Simple CNNs can perform image classification and (for images containing a single object) object classification.

For mathematical algorithms to be compatible with an image, they must represent the image in a numerical format. CNNs process an RGB input image as a three-dimensional (3D) array of pixels, in which the pixel’s three dimensions represent its R(ed), G(reen) and (B)lue values, respectively.

There are three types of layers in a conventional CNN:

- The *convolutional layer(s)* use two-dimensional filters, called kernels, to extract relevant features from the image by performing [convolutions](https://developer.ibm.com/articles/introduction-to-convolutional-neural-networks/). After each convolution, the kernel moves–strides–to an adjacent region, repeating this process until it has traversed the entire image. The output of this feature extraction is a feature map.
- *The pooling layer(s)* compress feature map data. This process, also called downsampling or dimensionality reduction, increases computational efficiency and reduces the risk of [overfitting](https://www.ibm.com/think/topics/overfitting) in model training.
- *The fully connected layer(s)* receive and collate visual data from every node in the neural network—hence “fully connected”—and predict whether the image matches any categories it has been trained to recognize.

While additional convolutional layers can enhance accuracy, adding too many layers leads to [vanishing gradients](https://www.ibm.com/think/topics/gradient-descent), preventing model optimization. ResNet architecture solved this problem, paving the way for CNNs with hundreds (or even thousands) of layers.

### Region-based CNN (R-CNN)

R-CNN was developed to solve complex multi-object detection tasks not achievable with standard CNNs. Its later evolution, *Faster R-CNN*, is an integral component of many instance segmentation models.

To make predictions at the object level (rather than image level), R-CNN introduced *region proposals*: R-CNN uses selective search to propose about 2,000 overlapping boxes that may contain an object, then feeds each “object proposal” into a CNN for feature extraction. [Support vector machine](https://www.ibm.com/docs/en/spss-modeler/18.4.0?topic=models-how-svm-works) (SVM) algorithms then classify objects and generate bounding boxes.

*Fast R-CNN* dramatically improved R-CNN’s speed by first feeding the entire image into a CNN for feature extraction, then using the resulting feature map to identify regions of interest (RoIs). Shortly thereafter, *Faster R-CNN* further improved speed and accuracy by introducing a trainable *region proposal network* (RPN) to replace the slower, non-trainable selective search algorithm.

### Fully convolutional networks

FCNs replace the fixed, fully connected layers of a simple CNN with additional convolutional and pooling layers—hence “fully convolutional.” The advent of FCNs ushered in the modern era of image segmentation.

Like conventional CNNs, FCNs use an encoder network, like ResNet or VGG, for feature extraction and downsampling. But rather than passing encoded data to a fully connected layer to classify the entire image, FCNs pass encoded data through layers of a “decoder” network that classifies and upsamples the compressed feature data to reconstruct the original image with pixel-by-pixel segmentation masks.

Naturally, some data is lost during the downsampling process. Later FCN variations, like U-Net, introduced *skip connections* that selectively bypass some convolutional layers to preserve greater detail.

### Mask R-CNN

Mask R-CNN architecture paired the object detection of a Faster R-CNN with the segmentation capabilities of an FCN to achieve a breakthrough in instance segmentation.

After the RPN generates bounding boxes for proposed objects, and the rest of the Faster R-CNN network confirms which region proposals contain objects (and performs regressions to improve the accuracy of object bounding boxes), an FCN creates a segmentation mask of the objects contained within each bounding box.

This process is effective even when objects are occluded, as the Faster R-CNN network can differentiate between each object instance to ensure that each is segmented individually.

### One-shot (single stage) models

Certain applications of instance segmentation, like detecting defective items in a manufacturing assembly line, require real-time results. Single stage models were developed for use cases in which speed is a top priority.

Two-stage models like Mask R-CNN are highly accurate, but their inherently sequential approach is difficult to accelerate. One-shot instance segmentation models like YOLACT (You Only Look At CoefficienTs) instead build upon single stage object detection models like YOLO (You Only Look Once).

In YOLACT, an FPN creates high-resolution feature maps, which are fed into two parallel branches: an FCN branch proposes *k* “prototype masks” of potential object instances; simultaneously, a branch of fully connected layers produces many “anchor boxes,” similar to region proposals, and also predicts *k* “mask coefficients”—one for each prototype mask—representing the likelihood that a proposed object aligns with a proposed segmentation mask. Non-maximum suppression (NMS) is used to filter for proposed instances with the highest mask coefficients.

### Transformer models

Recent innovations in instance and panoptic segmentation have explored transformer models, inspired by their success in fields like [natural language processing](https://www.ibm.com/think/topics/natural-language-processing). Models like [Vision Transformers (ViT)](https://research.ibm.com/publications/a-theoretical-understanding-of-shallow-vision-transformers-learning-generalization-and-sample-complexity) use self-attention in place of convolution, allowing for holistic analysis of an image’s visual context.

The primary challenge to overcome has been computational demands: the computational complexity of self-attention rises quadratically with image size. Swin transformers use *s*hifted *win*dows (instead of conventional *sliding* strides) to create non-overlapping self-attention layers, making computational complexity increase linearly, not quadratically, with image size. Swin-based models now rival the accuracy of leading CNN-based frameworks.

## Training instance segmentation models

Machine learning algorithms, including the deep learning algorithms used for instance segmentation, must be trained. Both CNN-based and transformer-based models are trained with *backpropagation*: models reverse engineer annotated training images to learn the appropriate weights and biases for the task at hand.

The annotation of training data must be very accurate to maximize proper machine learning and serve as a “ground truth” benchmark against which trained models can be evaluated and optimized. Because human capabilities greatly exceed even the most accurate computer vision models, this annotation is done by hand—an expensive, labor-intensive process.

To avoid the time and cost of custom datasets, most models make use of large, open source training datasets or fine-tune a pre-trained encoder network for more specific visual tasks. Common open source image datasets include:

- **COCO (Common Objects in Context)**: a massive dataset containing over 330,000 images with annotated segments across 80 *thing* categories and 91 *stuff* categories
- **ADE20K**: a scene segmentation dataset created by MIT containing over 20,000 images with over 150 semantic classes
- **Cityscapes**: a large-scale dataset focused on urban streets, with images from 50 cities across various daytimes, seasons and weather conditions.

## Evaluating instance segmentation models

The most commonly applied measures of instance segmentation and object detection performance are *Intersection over Union* (*IoU*) and *Average Precision* (*AP*). These metrics are typically expressed in terms of performance against a benchmark dataset, like “an AP of 54.4 on COCO dataset.”

### Intersection over Union (IoU)

IoU measures the pixel-wise overlap between a ground truth mask and a model’s prediction, expressed as a percentage or an integer between 0 and 1. For images with multiple instances, mean IoU (mIoU) is used.

While IoU is intuitive, it has important limitations:

- *It rewards overly broad predictions.* Even if a segmentation mask is far too large, it will score a perfect IoU of 1 if it contains the ground truth mask within it.
- *It cannot be used as a loss function.* For bad predictions with no overlap—whether slightly off or not even close—IoU=0. This means IoU is not differentiable, and thus cannot help an algorithm optimize a model. [*Generalized Intersection over Union* (or *GIoU*)](https://giou.stanford.edu/) amends IoU to make it differentiable.

### Average Precision (AP)

AP is calculated as the area under the precision-recall curve. It balances the tradeoffs between two metrics, precision and recall, calculated using discrete outcome values like true positives (TP), true negatives (TN), false positives (FP) and false negatives (FN).

- *Precision* measures how often positive predictions—in this case, pixels of a segmented instance—are correct: *TP/(TP+FP)*. It has the downside of rewarding false negatives.
- *Recall* measures how often positive predictions are captured: *TP/(TP+FN)*. It has the downside of rewarding false positives.

To maximize relevance, AP is often calculated within specific IoU thresholds. For example, “AP50” calculates AP only for predictions with an IoU greater than 50 percent. Mean average precision (mAP) is used situationally as the average AP value across all calculated thresholds.
