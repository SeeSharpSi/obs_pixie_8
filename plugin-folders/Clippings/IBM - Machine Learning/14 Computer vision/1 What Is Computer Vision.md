---
title: What is computer vision?
source: https://www.ibm.com/think/topics/computer-vision
author:
- '[[Rina Diane Caballar]]'
- '[[Cole Stryker]]'
published: 2024-11-21
created: 2026-08-31
description: "Computer vision is a subfield of artificial intelligence (AI) that equips machines with the ability to process, analyze and interpret visual inputs such as images and videos. It uses machine learning to help computers and other systems derive meaningful information from visual data."
---

## What is computer vision?

Computer vision is a subfield of [artificial intelligence (AI)](https://www.ibm.com/think/topics/artificial-intelligence) that equips machines with the ability to process, analyze and interpret visual inputs such as images and videos. It uses [machine learning](https://www.ibm.com/think/topics/machine-learning) to help computers and other systems derive meaningful information from visual data.

[Computer vision](https://research.ibm.com/topics/computer-vision) can be pictured as the interaction between three broad processes, each working together and informing one another: recognition, reconstruction and reorganization. [Image recognition](https://www.ibm.com/think/topics/image-recognition) is all about identifying actions, objects, people, places and writing in digital images or videos. Reconstruction derives the three-dimensional characteristics of those entities, while reorganization infers the relationships between the entities.<sup>1</sup>

## How computer vision works

Radiology imaging in pneumonia diagnosis is a common use case in computer vision. Radiologists have to carefully interpret chest X-rays, a process which can be error-prone and time-consuming due to the subtlety of pneumonia symptoms and their similarities with other lung conditions.<sup>2</sup> A computer vision system can help.

There are multiple types of models and approaches for computer vision tasks, but the following hypothetical example illustrates a common workflow:

1. Data gathering
2. Preprocessing
3. Model selection
4. Model training

### Data gathering

The first step is to collect the necessary visual data. Hospitals generate huge volumes of chest X-rays, which they can use to train a computer vision [algorithm](https://www.ibm.com/think/topics/machine-learning-algorithms). Since the goal is for the algorithm to classify whether an X-ray image depicts pneumonia or not, hospitals will need to compile a [dataset](https://www.ibm.com/think/topics/dataset) of chest X-ray scans and correctly [label](https://www.ibm.com/think/topics/data-labeling) or annotate each scan as either normal or signifying pneumonia.

For other use cases, images and videos can come from sources such as cameras and sensors. [Datasets](https://www.ibm.com/think/topics/dataset) like COCO, ImageNet and Open Images provide large collections of annotated images.

### Preprocessing

An [AI model](https://www.ibm.com/think/topics/ai-model) is only as good as the data used to train it, which makes high-quality data crucial for computer vision. Preprocessing can help improve [data quality](https://www.ibm.com/think/topics/data-quality) through [data cleaning](https://www.ibm.com/think/topics/data-cleaning) and enhancements like adjusting brightness or contrast to sharpen images, as well as resizing and smoothing.

Datasets must also be sufficiently large and diverse enough for computer vision [algorithms](https://www.ibm.com/think/topics/machine-learning-algorithms) to produce accurate results. [Synthetic data generation](https://www.ibm.com/think/insights/synthetic-data-generation) and [data augmentation](https://www.ibm.com/think/topics/data-augmentation) can help expand the size and diversity of datasets. For instance, hospitals can use geometric transformations such as rotating chest X-ray images to the left or right or flipping images upside down to augment their data.

### Model selection

[Selecting the right machine learning model](https://www.ibm.com/think/topics/model-selection) is crucial for optimizing efficiency and performance. [Convolutional neural networks (CNNs)](https://www.ibm.com/think/topics/convolutional-neural-networks) continue to be the primary [deep learning](https://www.ibm.com/think/topics/deep-learning) model for image processing tasks, while [recurrent neural networks (RNNs)](https://www.ibm.com/think/topics/recurrent-neural-networks) are particularly suited for processing sequential data such as video frames.

However, advances in AI are powering a shift toward [transformer models](https://www.ibm.com/think/topics/transformer-model). For instance, a vision transformer (ViT) applies elements of a transformer-based [language model](https://www.ibm.com/think/topics/large-language-models) to computer vision. ViTs process an image into patches and treat them as sequences, similar to tokens in a language transformer. The vision transformer then implements a [self-attention](https://www.ibm.com/think/topics/self-attention) mechanism across these patches to create a transformer-based representation of the input image. ViTs often match or exceed the performance of CNNs on computer vision tasks like image classification.<sup>3</sup>

### Model training

Once a model has been chosen, [model training](https://www.ibm.com/think/topics/model-training) follows. The training stage involves running the model on [training data](https://www.ibm.com/think/topics/training-data) specific to a computer vision task, measuring performance against [ground truth](https://www.ibm.com/think/topics/ground-truth) and optimizing [parameters](https://www.ibm.com/think/topics/model-parameters) to improve performance over time.

CNNs consist of three types of layers: a convolutional layer, a pooling layer and a fully connected layer. The convolutional layer is where [feature extraction](https://www.ibm.com/think/topics/feature-extraction) happens. Feature extraction entails determining and capturing key visual attributes from raw image data, such as colors, edges, shapes and textures. In the case of X-ray images with pneumonia, features to be extracted include asymmetric lung contours, bright regions that indicate inflammation or the presence of fluid (as opposed to dark, air-filled regions), clouded or opaque lung areas, and coarse or patchy textures.<sup>4</sup> Feature extraction allows algorithms to distinguish significant relationships and patterns in visual data.

An X-ray image is treated as a matrix of pixel values. Another matrix of weights (parameters that control how much influence a given input feature has on the model’s output) known as a filter or kernel is applied to an area of the X-ray image, with a dot product calculated between the input pixel values. The filter moves, or “convolves,” across the image to extract features, and the entire process is known as a convolution. The final output from the series of dot products is called an activation map or a feature map. Each filter is tuned to respond to specific patterns, such as edges, shapes or textures, allowing the CNN to learn multiple visual features simultaneously.

The feature map is fed into a pooling layer to further reduce the map’s size and compress its dimensions. Another filter sweeps through the entire input, taking the maximum or average values within a group of cells in the feature map. This retains the most essential features, allowing the model to focus its attention on them.

The act of moving across an image to extract features, reduce dimensions and produce a classification is known as a forward pass. After this forward pass, the model applies a [loss function](https://www.ibm.com/think/topics/loss-function) to calculate its error or the difference between its predicted classification and the true classification.

To minimize the loss function, [backpropagation](https://www.ibm.com/think/topics/backpropagation) is employed. Backpropagation is a backward pass to compute the gradient of the loss function with respect to each weight. Then, the [gradient descent](https://www.ibm.com/think/topics/gradient-descent) technique is implemented to update model weights and optimize the model.

Finally, the fully connected layer conducts the task of classification based on the features extracted through the previous layers and their different filters. The CNN then generates its outputs, which are probabilities for each class (in this case, normal vs. pneumonia). For the chest X-ray image classification task, this output will indicate either a normal scan or, if the likelihood passes a predetermined threshold, a scan positive for pneumonia.

## Computer vision tasks

[Computer vision](https://developer.ibm.com/articles/introduction-computer-vision/) algorithms can be trained on a wide range of tasks, some of which include:

- Image recognition
- Image classification
- Object detection
- Image segmentation
- Object tracking
- Scene understanding
- Facial recognition
- Pose estimation
- Optical character recognition
- Image generation
- Visual inspection

### Image recognition

Image recognition is the broadest form of computer vision. It encompasses the identification of people, places, objects and other entities in digital images and serves as the foundation for tasks like image classification, object detection and image segmentation.

### Image classification

Image [classification](https://www.ibm.com/think/topics/classification-machine-learning) is a core computer vision task that categorizes images into predefined groups or classes. It predicts the most fitting label for an image or objects within an image. The previously illustrated scenario of pneumonia diagnosis using chest X-rays is an example of image classification.

### Object detection

[Object detection](https://www.ibm.com/think/topics/object-detection) aims to pinpoint where objects are in digital images. It melds two learning techniques: object localization and image classification.

Object localization identifies the location of specific objects in an image by drawing bounding boxes around them. Then, image classification distinguishes the category to which objects belong. In footage of road traffic, for example, computer vision apps can use object detection to not only classify vehicles but also locate them on the road.

Common CNN architectures for object detection include R-CNN (region-based convolutional neural network) and YOLO (you only look once). R-CNN implements two-stage detection by first determining regions bearing objects then running those regions through separate networks for classification and more exact localization. Meanwhile, YOLO conducts single-stage detection by blending localization and classification in a single network pass, making it swift enough for real-time object detection.

Object detection for videos usually applies transformer-based models and RNNs, particularly the long short-term memory architecture.

### Image segmentation

[Image segmentation](https://www.ibm.com/think/topics/image-segmentation) is a more precise, pixel-level version of object detection. It partitions a digital image into discrete groups of pixels known as image segments, then labels pixels according to their class or instance.

While object detection can classify multiple elements within an image and approximate each element’s width and height, image segmentation discerns exact boundaries or shapes. This makes image segmentation valuable for delineating closely bunched objects with overlapping bounding boxes.

Image segmentation can be further subdivided into three task types:

- [Semantic segmentation](https://www.ibm.com/think/topics/semantic-segmentation) is the simplest type, assigning a semantic class—the specific category to which a given pixel might belong—to each pixel.
- [Instance segmentation](https://www.ibm.com/think/topics/instance-segmentation) predicts the exact pixel-wise boundaries of each individual object instance in an image.
- Panoptic segmentation combines semantic and instance segmentation by determining the semantic classification of all pixels and differentiating each object instance in an image.

For instance, in an image of a city street, semantic segmentation might treat cars parked one in front of the other as one long car segment, while instance segmentation separates and determines the shape of each car.

![A graphic comparing source images with semantic, instance, and panoptic segmentation.](https://assets.ibm.com/is/image/ibm/image-segmentation-diagram-all-4x?ts=1778777960104&dpr=off)

### Object tracking

Object tracking follows and traces an object as it moves across a sequence of video or image frames. It pinpoints and distinguishes the object in each frame and preserves the object’s continuity during traversal.

### Scene understanding

Scene understanding extends a step beyond object recognition, capturing a higher level of visual information. Upon identifying objects in an image, deep learning models predict connections between them, such as actions, events and interactions.

[Graph neural networks (GNNs)](https://www.ibm.com/think/topics/graph-neural-network) can be used to represent the spatial relationships between objects in an image. In the traffic footage example, computer vision systems can infer that a taxi is moving in front of a car, a car is parked to the left of a taxi or a car is turning right.

[Vision language models (VLMs)](https://www.ibm.com/think/topics/vision-language-models) can also help with scene understanding. This pairing of [large language models (LLMs)](https://www.ibm.com/think/topics/large-language-models) with vision transformers can recognize and classify objects within an image and provide contextual descriptions such as an object’s position relative to other visual elements.

### Facial recognition

Facial recognition applies image recognition to facial features. It captures the geometry of a face and spots key patterns like the distance between the eyes, the distance from forehead to chin, the contour of the nose and the shape of the lips.

Facial recognition can identify individuals in real time or in photos or videos. A popular example is [biometric authentication](https://www.ibm.com/think/topics/biometric-authentication) through face recognition to unlock smartphones.

![Person with face obscured, next to a digital facial recognition mesh displayed on a transparent interface.](https://assets.ibm.com/is/image/ibm/facial-recognition-v4?ts=1778777961313&dpr=off)

### Pose estimation

Pose estimation gauges the spatial position of different body parts to recognize gestures and track body movements. For instance, pose estimation can aid in marking the orientation of a gamer’s arms and hands during virtual reality gameplay. A more real-world example is NASA’s computer vision software that provides robotic arm operators aboard the International Space Station with real-time pose estimation for precise grappling of targets.<sup>5</sup>

### Optical character recognition

[Optical character recognition (OCR)](https://www.ibm.com/think/topics/optical-character-recognition), also referred to as text recognition, extracts and converts text from images, scanned documents and other sources into a machine-readable format. As such, it helps automate the digitalization of handwritten text and paper records.

The OCR workflow follows these steps:

1. Image acquisition converts the image or digital document into a black-and-white version, with light areas marked as background and dark areas marked as characters for recognition.
2. Preprocessing removes extraneous pixels and can include deskewing to correct for the image being improperly aligned during scanning.
3. Text recognition finds alphabetic letters, numeric digits or symbols, targeting one character at a time. It then identifies characters through pattern recognition, matching a character’s font, scale and shape to a template.

CNNs and transformer-based models are capable of more intelligent character recognition, extracting features such as curves, line intersections, loops and the number of angled lines in a character. These algorithms are also capable of intelligent word recognition, distinguishing words instead of characters for faster processing.

### Image generation

Image generation employs [generative AI](https://www.ibm.com/think/topics/generative-ai) models to produce images. Here are some common [generative models](https://www.ibm.com/think/topics/generative-model) used for image generation:

- [Diffusion models](https://www.ibm.com/think/topics/diffusion-models) are trained to create novel images by learning how to denoise or reconstruct samples in their training data that have been gradually diffused with random noise and scrambled beyond recognition.
- [Generative adversarial networks (GANs)](https://www.ibm.com/think/topics/generative-adversarial-networks) consist of two [neural networks](https://www.ibm.com/think/topics/neural-networks): a generator that creates images and a discriminator that acts as an adversary, discriminating between artificial and real images. Both networks are trained iteratively, with the discriminator’s feedback improving the generator’s output until the discriminator is no longer able to distinguish artificial from real images.
- [Variational autoencoders (VAEs)](https://www.ibm.com/think/topics/variational-autoencoder) are deep learning models that generate variations of the images they’re trained on. An encoder compresses input images into a lower-dimensional space, capturing the meaningful information contained in the images. A decoder then reconstructs new images from this compressed representation.

VLMs are also capable of generating images given a text description.

### Visual inspection

[Visual inspection](https://www.ibm.com/think/topics/visual-inspection) automates the identification of defects. Through object detection, computer vision systems inspect images or videos to spot faults and flaws. Image segmentation can also be implemented to more precisely locate defects.

Computer vision-powered visual inspection machines can help companies carry out swifter and safer inspections with increased consistency and accuracy, be it pointing out corrosion on hard-to-reach areas of bridges or finding faulty connectors in assembled electronic products.

## Computer vision applications

As a mature field of AI, computer vision has gone through many advancements, leading to a broad array of use cases. Here are some real-world applications of computer vision:

### Agriculture

Cameras, drones and satellites capture high-resolution images of crops and farm areas. Computer vision technologies then analyze these images to aid in evaluating plant health and pinpoint pests and weeds for more targeted herbicide application.

### Autonomous vehicles

In the automotive industry, self-driving cars compose a 3D model of their environment using a mix of cameras, lidar, radar and sensors. Then, they apply object detection, image segmentation and scene understanding for safe navigation, avoiding obstacles such as pedestrians and other vehicles and precisely detecting road features like lanes, traffic lights and traffic signs.

### Healthcare

Medical imaging is a key area of application for computer vision. For instance, object detection can automate image analysis, locating and identifying potential markers of disease in X-rays and CT, MRI and ultrasound scans. Additionally, instance segmentation can delineate the specific boundaries of organs, tissues and tumors, aiding in a more accurate diagnosis that can better inform decision-making for treatments and patient care.

### Manufacturing

Computer vision systems help with [inventory management](https://www.ibm.com/think/topics/inventory-management), scanning items to determine stock levels. They can also power quality control, recognizing defects in real time. These systems analyze product images and can rapidly and more accurately flag faults or inconsistencies compared to inspectors using their own human vision.

### Retail and e-commerce

Amazon’s Just Walk Out technology, for example, uses computer vision in small retail and food service stores to track customer selections and automate the checkout experience. Customers can just take their items and leave without lining up at payment counters.<sup>6</sup>

Online stores can also use augmented reality coupled with face recognition and pose estimation for their virtual try-on experiences, allowing customers to visualize how clothes, eyewear or makeup will look on them before purchasing.

### Robotics

Like autonomous vehicles, robots use cameras, lidar and sensors to map their surroundings. They then apply computer vision algorithms to complete their tasks, such as assisting surgeons with complex procedures, navigating through warehouses to transport goods, picking only ripe produce and putting objects in assembly lines.

### Space exploration

Object detection can help spacecraft locate and avoid hazards during landing, while rovers can implement the same capability for navigating terrain.<sup>7</sup> Image classification can be employed for categorizing asteroids, meteors and even space debris, while object tracking monitors the trajectories of these astronomical objects.

## Computer vision tools

Many tools exist for building computer vision apps, helping streamline the development process. A few popular tools include:

- Keras
- OpenCV
- Scikit-image
- TensorFlow
- Torchvision

### Keras

[Keras](https://keras.io/) is a deep learning [application programming interface (API)](https://www.ibm.com/think/topics/api) that can run on top of other [AI frameworks](https://www.ibm.com/think/topics/ai-frameworks) like PyTorch and TensorFlow. It provides dozens of tutorials and examples for various computer vision tasks, including image and video classification, image segmentation, object detection and OCR.

### OpenCV

[OpenCV](https://opencv.org/) is one of the most widely used computer vision libraries. This [open-source](https://www.ibm.com/think/topics/open-source) library is home to more than 2,500 computer vision algorithms and contains modules for image processing, object detection, video analysis and more. It’s written in C++ but also has wrappers for programming languages like Java and [Python](https://developer.ibm.com/languages/python/).

### Scikit-image

[Scikit-image](https://scikit-image.org/) is an open-source collection of algorithms for image processing in Python. It supports preprocessing, feature extraction, object detection and image segmentation, among other tasks. Its simplicity makes it accessible for beginners.

### TensorFlow

[TensorFlow](https://www.tensorflow.org/) is an open-source machine learning platform from Google. While it serves more general-purpose deep learning applications, TensorFlow also provides computer vision-specific datasets, tools for preprocessing and functions for image and video classification, image segmentation and object detection.

### Torchvision

The [torchvision](https://github.com/pytorch/vision) library forms part of the [PyTorch](https://www.ibm.com/think/topics/pytorch) ecosystem. It encompasses common image transformations, datasets and other utility functions. The package also offers models for image and video classification, object detection and semantic and instance segmentation.

## A brief history of computer vision

Computer vision is one of the earliest disciplines of AI. For decades, computer science researchers have been developing ways for machines to understand visual data.

Experimentation began in the 1950s to the 1960s when neurophysiologists showed cats an array of images while recording neural activity. They discovered that the animals responded first to lines, concluding that image processing starts with simple shapes like straight edges.<sup>8</sup>

At around the same time, the first computer image scanning technology was developed, equipping computers with the ability to digitize and acquire images.<sup>9</sup> Another milestone was reached when computers developed the ability to transform two-dimensional images into three-dimensional forms.<sup>10</sup>

In 1982, neuroscientist David Marr established that vision works hierarchically and introduced algorithms for machines to detect corners, curves, edges and similar basic shapes.<sup>11</sup> During the same decade, computer scientist Kunihiko Fukushima developed a network of cells that could recognize patterns and named it “neocognitron,” which included convolutional layers in a neural network.<sup>12</sup>

By 2000, the focus of study was on image classification and object recognition.<sup>13</sup> In 2009, the ImageNet dataset was introduced, containing millions of labeled images for training computer vision algorithms.<sup>14</sup> In 2012, a team from the University of Toronto created the AlexNet CNN, which was trained on the ImageNet dataset and significantly reduced the error rate for image recognition, paving the way for today’s computer vision models.<sup>15</sup>

## Footnotes

1. [The three R’s of computer vision: Recognition, reconstruction and reorganization](https://saurabhg.web.illinois.edu/pdfs/malik2016three.pdf), Pattern Recognition Letters, 8 February 2016  
 2. [Efficient pneumonia detection using Vision Transformers on chest X-rays](https://www.nature.com/articles/s41598-024-52703-2), Scientific Reports, 30 January 2024  
 3. [An Image is Worth 16x16 Words: Transformers for Image Recognition at Scale](https://arxiv.org/abs/2010.11929), arXiv, 3 June 2021  
 4. [NGBoost Classifier Using Deep Features for Pneumonia Chest X-Ray Classification](https://www.mdpi.com/2076-3417/15/17/9821), Applied Sciences, 8 September 2025  
 5. [Computer Vision Lends Precision to Robotic Grappling](https://technology.nasa.gov/patent/MSC-TOPS-114), NASA Technology Transfer Program, Accessed 11 September 2025  
 6. [Amazon Just Walk Out](https://aws.amazon.com/just-walk-out/), AWS, Accessed 11 September 2025  
 7. [The Computer Vision Laboratory](https://www-robotics.jpl.nasa.gov/how-we-do-it/facilities/the-computer-vision-laboratory/), NASA JPL Robotics, Accessed 11 September 2025  
 8. [From Cats to the Cortex: Unravelling the Hierarchical Processing System of Vision and Brain Plasticity](https://www.cureus.com/articles/289965-from-cats-to-the-cortex-unravelling-the-hierarchical-processing-system-of-vision-and-brain-plasticity%22%20/l%20%22!/), Cureus, 2 September 2024  
 9. [Your Engineering Heritage: Scanners and Computer Image Processing](https://insight.ieeeusa.org/articles/your-engineering-heritage-scanners-and-computer-image-processing/), IEEE-USA InSight, 8 February 2016  
 10. [A Simple World: The Blocks World](https://visionbook.mit.edu/simplesystem.html#a-simple-world-the-blocks-world), Foundations of Computer Vision, 2024  
 11. [Marr’s Computational Theory of Vision](https://visionbook.mit.edu/taxonomy.html#marrs-computational-theory-of-vision), Foundations of Computer Vision, 2024  
 12. [Neocognitron: A Self-organizing Neural Network Model for a Mechanism of Pattern Recognition Unaffected by Shift in Position](https://www.rctn.org/bruno/public/papers/Fukushima1980.pdf), Biological Cybernetics, 1980  
 13. [Computer Vision](https://visionbook.mit.edu/taxonomy.html#computer-vision), Foundations of Computer Vision, 2024  
 14. [ImageNet: A large-scale hierarchical image database](https://ieeexplore.ieee.org/document/5206848), IEEE Conference on Computer Vision and Pattern Recognition, 2009  
 15. [CHM Releases AlexNet Source Code](https://computerhistory.org/blog/chm-releases-alexnet-source-code/), Computer History Museum, 20 March 2025
