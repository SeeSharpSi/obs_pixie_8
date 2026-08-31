---
title: What are generative adversarial networks (GANs)?
source: https://www.ibm.com/think/topics/generative-adversarial-networks
author:
- '[[Jobit Varughese]]'
published: 2025-04-29
created: 2026-08-31
description: "A generative adversarial network (GAN) is a machine learning model designed to generate realistic data by learning patterns from existing training datasets. It operates within an unsupervised learning framework by using deep learning techniques, where two neural networks work in opposition—one generates data, while the other evaluates whether the data is real or generated."
---

## What is a GAN?

A generative adversarial network, or GAN, is a [machine learning](https://www.ibm.com/think/topics/machine-learning) model designed to generate realistic data by learning patterns from existing training datasets. It operates within an [unsupervised learning](https://www.ibm.com/think/topics/unsupervised-learning) framework by using [deep learning](https://www.ibm.com/think/topics/deep-learning) techniques, where two [neural networks](https://www.ibm.com/think/topics/neural-network) work in opposition—one generates data, while the other evaluates whether the data is real or generated.

While deep learning has excelled in tasks such as image classification and speech recognition, generating new data, including realistic images or text, has been more challenging due to the complexity of computations in generative models.  

 GANs, introduced by Ian Goodfellow in his 2014 paper Generative Adversarial Nets, offer a groundbreaking solution to this challenge.<sup>[1](#f01)</sup> This innovative framework has transformed generative modeling, making it easier to develop models and algorithms capable of creating high-quality, realistic data.

## How do GANs work?

A GAN architecture consists of two deep neural networks: the generator network and the discriminator network. The GAN training process involves the generator starting with random input (noise) and creating synthetic data such as images, text or sound that mimics the real data from the given training set. The discriminator evaluates both the generated samples and the data from the training set and decides whether it’s real or fake. It assigns a score between 0 and 1: a score of 1 means that the data looks real, and a score of 0 means it’s fake. [Backpropagation](https://www.ibm.com/think/topics/backpropagation) is then used to optimize both the networks. This means that the gradient of the [loss function](https://www.ibm.com/think/topics/loss-function) is calculated according to the network's parameters, and these parameters are adjusted to minimize the loss. The generator then uses feedback from the discriminator to improve, trying to create more realistic data.

![The structure of a GAN](https://assets.ibm.com/is/image/ibm/the-structure-of-a-gan?ts=1763387791182&dpr=off)

The training of a GAN architecture involves an adversarial process. The generator model tries to trick the discriminative model into classifying fake data as real, while the discriminator continuously improves its ability to distinguish between real and fake data. This process is guided by loss functions that measure each network's performance. A generator loss measures how well the generator can deceive the discriminator into believing its data is real. A low generator loss means that the generator is successfully creating realistic data. A discriminator loss measures how well the discriminator can distinguish between fake data and real data. A low discriminator loss indicates the discriminator successfully identifying fake data.   

 For example, in a GAN trained to generate images of dogs, the generator transforms random noise into images that resemble dogs, while the discriminator evaluates these images against actual dog photos from the training set.  

 Over time, this adversarial process drives both networks to improve. It enables the generator to create convincing, realistic data that closely resembles the original training dataset while the discriminator sharpens its ability to identify subtle differences between real and fake data.

## Types of GANs

### Vanilla GANs

Vanilla GANs are the basic form of generative adversarial networks that include a generator, and a discriminator engaged in a typical adversarial game. The generator creates fake samples, and the discriminator aims to distinguish between the real and fake data samples. Vanilla GANs use simple multilayer perceptrons (MLPs) or layers of neurons for both the generator and the discriminator, making them easy to implement. These MLPs process data and classify inputs to distinguish known objects in a dataset. However, they are known for being unstable during training and often require careful tuning of hyperparameters to achieve good results.

### Conditional GANs (cGAN)

A cGAN is a type of generative adversarial network that includes additional information, called "labels" or "conditions," for both the generator and the discriminator.<sup>[2](#f02)</sup> These labels provide context, enabling the generator to produce data with specific characteristics based on the given input, rather than relying solely on random noise as in vanilla GANs. This controlled generation makes cGANs useful for tasks requiring precise control over the output. cGANs are widely used for generating images, text and synthetic data tailored to specific objects, topics or styles. For example, a cGAN can convert a black-and-white image to a color image by conditioning the generator to transform grayscale into the red, green, blue color model (RGB). Similarly, it can generate an image from text inputs, such as "create an image of a white furry cat," producing outputs that align with the provided description.

### Deep convolutional GAN (DCGAN)

Deep convolutional GAN (DCGAN) uses convolutional neural networks (CNNs) for both the generator and the discriminator. The generator takes random noise as input and transforms it into structured data, such as images. It uses transposed convolutions (or deconvolutions) to upscale the input noise into a larger, more detailed output by "zooming in" on the noise to create a meaningful image. The discriminator uses standard convolutional layers to analyze the input data. These layers help the discriminator "zoom out" and look at the overall structure and details of the data to make a decision. This approach makes DCGANs effective for generating high-quality images and other structured data.

### StyleGAN

Style GAN is a type of generative adversarial network that produces high-resolution images even to 1024 x 1024 resolution. StyleGANs are trained by using a dataset of images of the same object. The generator network is composed of multiple layers, each responsible for adding different levels of detail to the image, from basic features to intricate textures. The discriminator network also has multiple layers, evaluating the level of detail and assessing the overall quality.

### CycleGAN

In a CycleGAN, the generator and discriminator are trained in a cyclic manner. It is designed for image-to-image translation by using unpaired datasets. It works by translating an image into another style like a painting by using a generator and then translating it back to the original style by using a reverse generator. This method helps ensure that the reconstructed image closely resembles the original through a process called cycle consistency. These results are specifically useful for tasks such as image style transfer and image enhancement.

### Laplacian pyramid GAN (LAPGAN)

A Laplacian pyramid GAN (LAPGAN) is designed to generate high-quality images by refining them at multiple scales. It begins by generating a low-resolution image and then progressively adds more details at higher resolution by using a series of GANs. This multiscale approach known as Laplacian pyramid, allows LAPGAN to handle the complexity of generating high-resolution images more effectively.

### DiscoGAN

DiscoGAN is used to learn cross-domain relationships without requiring paired training data. It uses two generators and two discriminators to translate images from one domain to another and back, helping ensure that the reconstructed image closely resembles the original through cycle consistency. This makes DiscoGAN effective for tasks like image-to-image translation, style transfer and image enhancement, even with unpaired datasets.

## Applications of GANs

GANs can be used for various applications of computer vision, image generation, object detection, image-to-image translation, text to image generation, prediction of next frame in the video and more.

### Image generation

GANs are used for generating photorealistic images of samples that never existed and for creating visuals from textual descriptions, allowing for the creation of images based on specified attributes or scenes. BigGAN, trained on large datasets, generates data based on specific classes or conditions and achieves state-of-the-art results in image generation.<sup>[3](#f03)</sup> It is used for various applications, including image synthesis, colorization and reconstruction. For example, GAN-BVRM, a novel GAN-based Bayesian visual reconstruction method, utilizes a classifier to decode functional magnetic resonance imaging (fMRI) data. A pretrained BigGAN generator produces category-specific images and encoding models select images aligning with brain activity, achieving improved naturalness and fidelity in reconstructing image stimuli. GANs are making significant strides in healthcare by generating realistic medical data, such as MRIs, CT scans and X-rays, for training and analysis, and by creating new molecular structures for drug discovery.

### Image super resolution

GANs can enhance low-resolution images by generating high-resolution variations, improving the quality and detail of images. For instance, StyleGAN2 by NVIDIA generates high-resolution, highly realistic images with fine-grained control over attributes including content, identity, expression and pose, enabling users to create and manipulate images for artistic and practical applications.<sup>[4](#f04)</sup>

### Image to image translation

GANs accomplish style transfer and image editing by transforming images from one domain to another, such as turning a sketch into a painted version. For example, CycleGANs are employed for converting photos to paintings. This process involves one generator converting images from the source domain (photographs) to the target domain (paintings) and vice versa through a cyclic constraint, helping ensure the mapping retains semantic coherence.

### Video retargeting

GANs are used for unsupervised video retargeting, adapting video content to fit different aspect ratios and formats while preserving important visual information. Recycle-GANs utilize a similar cyclical strategy that is commonly found in CycleGANs, applying it specifically to video data. For example, Recycle-GANs can convert a widescreen video to a square format for social media platforms, helping ensure that the key elements and movements in the video remain intact.<sup>[5](#f05)</sup>

### Facial attribute manipulation

GANs enable the alteration of facial features in images, such as changing expressions or aging effects, showcasing their potential in entertainment and social media applications. StyleGAN operates by applying a layer-wise modification to the generated samples based on ‘styles’ extracted from the latent space. This process allows for intuitive control over various attributes including hair color and facial expression, enabling users to manipulate faces according to specific features without needing manual adjustment. For instance, StyleGAN can be used to change a person's hair color from brown to blonde or to add a smile to a neutral facial expression.

### Object detection

GANs are used in object detection to enhance the quality and diversity of training data, which can significantly improve the performance of object detection models. By generating synthetic images that closely resemble real data, GANs augment the training dataset, helping the model generalize better and perform more accurately. For example, research has shown that the performance of deep learning models for object detection significantly deteriorates when applied to images with reduced quality, such as those affected by noise, blur or other distortions.<sup>[6](#f06)</sup> The paper presents the GAN-DO framework, which utilizes GANs to enhance the robustness of object detection models against varying image quality without adding complexity to the model architecture or inference speed. Experimental results demonstrate that GAN-DO outperforms traditional fine-tuning methods, leading to improved accuracy in object detection.

## Other generative models for synthetic data generation

Apart from GANs, variational autoencoders (VAEs) are another deep learning model that can create new data samples that mimic real-world data. VAEs are probabilistic models, meaning they represent data in terms of probability distributions, which describe the likelihood of different outcomes or values occurring in the data. These models are designed to learn patterns from a training dataset and create new data that are variations of the original dataset, rather than exact replicas. A variational autoencoder (VAE) contains two components. The encoder (recognition model) compresses complex input data such as images into simpler low-dimensional data, and the decoder (generative model) re-creates the original input from the compressed representation. VAEs can also generate completely new samples of data learning from the patterns of the training dataset. VAEs typically produce blurrier and less sharp outputs but are more stable to train, whereas GANs generate sharper and more realistic outputs but are harder to train due to instability.

Ultimately, the choice between VAEs and GANs depends on the specific requirements of the task, such as the desired output quality, training stability and the need for interpretable latent representations, making each model uniquely valuable in different applications.

## Benefits and challenges of GANs

Generative adversarial networks (GANs) can generate highly realistic and diverse data, such as images, text and audio. They are used in applications including [natural language processing (NLP)](https://www.ibm.com/think/topics/natural-language-processing) to generate text data and improve language models and in music generation to create new compositions and realistic instrument sounds. Simulation and gaming use GANs to generate realistic environments and characters and anomaly detection by identifying patterns that deviate from the norm. GANs also aid scientific research by simulating complex data for experiments that are costly or impractical to perform. They enhance [machine learning](https://www.ibm.com/think/topics/machine-learning) (ML) processes through data augmentation, increasing the quantity and diversity of training sets to address the challenge of limited big data. GANs are expected to integrate further with technologies like reinforcement learning, robotics and NLP to advance artificial intelligence (AI) systems.   

 Despite the rise of transformers, GANs remain relevant due to their lightweight architecture and computational efficiency, making them ideal for edge deployment. With fewer parameters compared to transformers, GANs offer-controlled generation for fine-grained manipulation of features (for example, facial attributes), which simplifies fine-tuning for specific tasks. GANs provide faster inference speeds as it requires a single forward pass (or one-time flow of input through a neural network to generate output). This makes them ideal for real-time applications on resource-constrained edge devices such as mobile phones and IoT systems. These advantages make GANs a practical choice for tasks like image translation, super-resolution and real-time video synthesis in edge environments.   

 However, GANs face significant challenges. One of the primary issues is training instability, where the generator and discriminator might not converge properly, leading to poor-quality outputs. Mode collapse is another challenge where the generator produces limited variety, failing to capture the full diversity of the training data. GANs also require large amounts of data and substantial computational resources, which can be a barrier to their widespread use. Evaluating the quality of GAN-generated outputs is a challenge, as traditional metrics might not fully capture the nuances of the generated data. Helping ensure the ethical use of generated sample is a growing concern, as GANs can be used to create deep fakes and other potentially harmful content.

## How to implement a GAN model

A GAN can be implemented by using Tensorflow and Keras. It requires a training dataset, a generator script and a discriminator script to create a GAN model in Python. The following is a step-by-step guide to help you get started:

Step 1: Import the required libraries, including TensorFlow and other essential libraries like numpy and matplotlib for building and training the GAN model.

Step 2: Load and preprocess the dataset, helping ensure it represents the target data distribution (for example, images, text and more).

Step 3: Build the generator model by using TensorFlow or Keras layers that take random noise and produce data samples matching the target distribution.

Step 4: Build the discriminator model to classify real vs. fake data samples generated by the generator.

Step 5: Use suitable optimizers for both generator and discriminator and define loss functions.

Step 6: Combine the generator and discriminator into a single GAN model for training the generator to deceive the discriminator.

Step 7: Implement a loop to alternate between training the discriminator and the generator with real and fake data.

Step 8: Analyze the generator's output and discriminator accuracy over epochs to help ensure convergence.

Step 9: Use the trained generator to produce new samples that mimic the target data distribution.

Step 10: Plot or analyze the generated data to validate how well the GAN has learned the target distribution.

By following these steps, a basic GAN model can be implemented by using TensorFlow.

The future of GANs is promising, with advancements expected in realism, stability, efficiency and ethical considerations. As GANs become more integrated with other technologies and find new applications, they will continue to revolutionize various industries and fields.

## Footnotes

<sup>1</sup> Goodfellow, I. J., Pouget-Abadie, J., Mirza, M., Xu, B., Warde-Farley, D., Ozair, S., ... & Bengio, Y. (2014). Generative adversarial nets. *Advances in neural information processing systems*, *27*.

<sup>2</sup> Alqahtani, Hamed & Kavakli, Manolya & Kumar, Gulshan. (2019). Applications of Generative Adversarial Networks (GANs): An Updated Review. Archives of Computational Methods in Engineering. 28. 10.1007/s11831-019-09388-y.

<sup>3</sup> Qiao, K., Chen, J., Wang, L., Zhang, C., Tong, L., & Yan, B. (2020). BigGAN-based Bayesian reconstruction of natural images from human brain activity. *Neuroscience, 444,* 92–105. [https://doi.org/10.1016/j.neuroscience.2020.07.040](https://doi.org/10.1016/j.neuroscience.2020.07.040).

<sup>4</sup> Alarcon, N. (2020). Synthesizing High-Resolution Images with StyleGAN2. NVIDIA Technical Blog. [https://developer.nvidia.com/blog/synthesizing-high-resolution-images-with-stylegan2](https://developer.nvidia.com/blog/synthesizing-high-resolution-images-with-stylegan2).

<sup>5</sup> Bansal, A., Ma, S., Ramanan, D., & Sheikh, Y. (2018). Recycle-GAN: Unsupervised Video Retargeting. arXiv. [https://doi.org/10.48550/arXiv.1808.05174](https://doi.org/10.48550/arXiv.1808.05174).

<sup>6</sup> Prakash, C. D., Shrivastava, A., & Torresani, L. (2019). It GAN DO Better: GAN-based Detection of Objects on Images with Varying Quality. arXiv. [https://arxiv.org/abs/1912.01707](https://arxiv.org/abs/1912.01707).
