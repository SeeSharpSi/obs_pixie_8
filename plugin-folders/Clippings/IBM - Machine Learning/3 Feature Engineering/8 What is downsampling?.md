## Authors

Jacob Murel Ph.D.

Senior Technical Content Creator

## What is downsampling?

Downsampling decreases the number of data samples in a dataset. In doing so, it aims to correct imbalanced data and thereby improve model performance.

Downsampling is a common data processing technique that addresses imbalances in a dataset by removing data from the majority class such that it matches the size of the minority class. This is opposed to upsampling, which involves resampling minority class points. Both Python scikit-learn and Matlab contain built-in functions for implementing downsampling techniques.

Downsampling for data science is often mistaken for downsampling in digital signal processing (DSP). The two are similar in spirit. Downsampling for digital signal processing (also known as decimation) is the process of decrementing the bandwidth and sampling rate of the sampler, thus removing some of the original data from the original signal. The process of decreasing the sampling frequency is often done by reducing the sampling rate by some integer factor, keeping only one of every *nth* sample. This is done by using a lowpass filter, otherwise known as an anti-aliasing filter, to reduce the high frequency/noise components of a discrete-time signal by the previously mentioned integer factor.

Downsampling for data balancing can also be confused with downsampling for image processing. When data contains lots of features, like in high resolution MRI images, calculations can become expensive. Downsampling in image processing thus reduces the dimensionality of each data point through convolution. This is not the same as balancing the dataset: it is an optimization technique that will later require interpolation to get back the original data.

## The latest AI trends, brought to you by experts

Get curated insights on the most important—and intriguing—AI news. Subscribe to our weekly Think newsletter. See the [IBM Privacy Statement](https://www.ibm.com/privacy).

## Thank you! You are subscribed.

\*

First name\*

Field required

\*

Last name\*

Field required

\*

Business email\*

Field required. Must be valid email. example@yourdomain.com

Your subscription will be delivered in English. You will find an unsubscribe link in every newsletter. Refer to our [IBM Privacy Statement](https://www.ibm.com/us-en/privacy) for more information.

## Why use downsampling?

Downsampling is an effective way to address imbalances within a dataset. An imbalanced dataset is defined as a dataset in which one class is greatly underrepresented in the dataset relative to the true population, creating unintended bias. For instance, imagine a model is trained to classify images as showing a cat or a dog. The dataset used is composed of 90% cats and 10% dogs. Cats in this scenario are overrepresented, and if we have a classifier predicting cats every time, it will yield a 90% accuracy for classifying cats, but 0% accuracy for classifying dogs. The imbalanced dataset in this case will cause classifiers to favor accuracy for the majority class at the expense of the minority class. The same issue can arise with multi-class datasets.<sup>1</sup>

The process of downsampling counteracts the imbalanced dataset issue. It identifies majority class points to remove based on specified criteria. These criteria can change with the chosen downsampling technique. This balances the dataset by effectively decreasing the number of samples for an overrepresented majority class until the dataset contains an equal ratio of points across all classes.

While imbalances can be seen by simply plotting the counts of data points in each class, it doesn’t tell us whether it will greatly affect the model. Fortunately, we can use performance metrics to gauge how well a downsampling technique corrects for class imbalance. Most of these metrics will be for binary classification, where there are only two classes: a positive and a negative. Usually, the positive class is the minority class while the negative class is the majority class. Two popular metrics are Receiver Operating Characteristic (ROC) curves and precision-recall curves.<sup>1</sup>

Think Keynotes

### Win the enterprise AI race

Join Arvind Krishna to see how IBM is enabling AI-first enterprises through hybrid cloud and emerging quantum capabilities.

[Get Started with watsonx Orchestrate®](https://www.ibm.com/products/watsonx-orchestrate)

## Advantages and disadvantages of downsampling

### Advantages

- **Less storage requirement**: When storage costs money, say for cloud storage, downsampling would be preferred over upsampling to avoid raising costs.<sup>2</sup>
- **Faster training**: Downsampling shrinks datasets and makes training less intensive on the CPU or GPU, which is more economically and environmentally friendly.
- **Less prone to overfitting:** Upsampling generates new data from the old data, which can cause models to overfit to the given data. Downsampling, being the opposite (deletes data), doesn’t suffer from this issue.<sup>2</sup>

### Disadvantages

- **Loss of Information**: Deleting points from the majority class can cause important information loss. This can be an issue if the classification of the majority class needs to be accurate. Another issue is if the dataset becomes too small for the model to train on.<sup>2</sup>
- **Introduced Bias**: The remaining majority class sample points can be a biased set of the original data, which negatively affects the classifier’s performance.

## Downsampling techniques

### Random downsampling

Random downsampling is a deletion technique where random points in the majority class are chosen without replacement and deleted from the dataset until the majority class size is equal to the minority class size. This is an easy way to randomly delete a subset of data for balancing purposes. However, this technique can cause important patterns or distributions in the majority class to disappear, negatively affecting classifier performance.<sup>2</sup>

### Near Miss downsampling

Near Miss downsampling is a technique that aims to balance class distribution by randomly eliminating certain majority class examples.

Conceptually, Near Miss operates on the principle that data should be kept in places where the majority and minority classes are very close, as these places give us key information in distinguishing the two classes.<sup>3</sup> These points are generally known as ‘hard’ to learn data points. Near Miss downsampling generally operates in two steps:

- Step 1: Calculate the pairwise distance between all majority-minority class instances.
- Step 2: Based on the calculated distances, remove instances of the majority class that are further away from minority points.

There are three variations of the Near Miss algorithm that provide a more definitive way of selecting majority class instances to remove.

- Version 1: This version keeps the majority class instances with the smallest average distance to their N *closest* minority class instances. The resulting data can potentially be unevenly distributed, with some majority class points being close to many minority class points and others being close to very few, causing both low precision and recall.<sup>4</sup>

     ![A diagram of downsampling - Near Miss 1](https://assets.ibm.com/is/image/ibm/downsampling-near-miss-v1:1x1?fmt=png-alpha&dpr=on%2C2.5&wid=320&hei=320)

- Version 2: This version of Near Miss downsampling keeps the majority class instances with the smallest average distance to their N *furthest* minority class instances. Unlike the first version, this version creates a more even distribution of the majority class, yielding better results from the classifier.<sup>4</sup>

     ![A diagram of downsampling - Near Miss 2](https://assets.ibm.com/is/image/ibm/downsampling-near-miss-v2:1x1?fmt=png-alpha&dpr=on%2C2.5&wid=320&hei=320)

- Version 3: This version keeps the closest majority class samples for the minority class instances closest to the majority class. It operates in two steps. First, the M nearest majority class neighbors of each minority class instance are kept. Then, from the remaining majority class instances, those with the largest average distance are identified and kept. Because this version keeps majority class instances that are close with many minority class instances, it can have high precision but low recall.<sup>4</sup>

     ![A diagram of downsampling - Near Miss 3](https://assets.ibm.com/is/image/ibm/downsampling-near-miss-v3:1x1?fmt=png-alpha&dpr=on%2C2.5&wid=320&hei=320)

### Condensed Nearest Neighbor Rule downsampling

Condensed Nearest Neighbors (CNN for short, ***not*** to be confused with [Convolutional Neural Networks](https://www.ibm.com/topics/convolutional-neural-networks)) seeks to find a subset of a dataset that can be used for training without loss in model performance. This is achieved by identifying a subset of the data that can be used to train a model that correctly predicts the entire dataset.

CNN downsampling can be broken down into the following steps:<sup>5</sup>

1. Create a new dataset, S, that contains all instances of the minority class and a single randomly sampled instance of the majority class.
2. Train a 1-NN classifier on the new dataset S.
3. For all majority class datapoints **not** in S, use the 1-NN classifier to predict its label. If the 1-NN classifier correctly predicts the label, discard the point. Otherwise, add it to S.

Like Near Miss, this process essentially removes all majority class instances far away from the decision boundary, which, again, are points that are easy to classify. It also ensures that every data in our original dataset can be correctly predicted using just the data within S. This way, the dataset can be shrunk significantly while preserving the decision boundary reasonably well.

     ![A diagram with 3 graphics of majority class sample, minority class sample and majority class sample with minority class neighbors.](https://assets.ibm.com/is/image/ibm/downsampling-edited-nearest-neighbors:1x1?fmt=png-alpha&dpr=on%2C2.5&wid=320&hei=320)

This image shows an example of applying condensed nearest neighbors using 1 nearest-neighbors and 21 nearest neighbors to two datasets. The top two images are before applying condensed nearest neighbors while the bottom two are after. As one can see, the decision boundary is reasonably well preserved.

### Tomek Link

The premise of Tomek Link downsampling is to reduce noise in the data by removing points near the decision boundary and increase class separation. How it works is that it identifies “tomek links” — a grouping of two points from different classes with no existing third point that is closest to either.<sup>2</sup>

For all tomek links, the point within the majority class is deleted. By removing a majority class point that is close to a minority class point, class separation increases. One drawback of this method is the computational complexity of calculating all pairwise distances between majority and minority class points.<sup>2</sup> Tomek Link downsampling is most effective when combined with other techniques.

### Edited Nearest Neighbors

Edited Nearest Neighbors (ENN) downsampling is similar to Tomek Link downsampling, where the goal is to remove examples near the decision boundary in order to increase class separation. In general, this method removes data points that differ in class from a majority of its neighbors.<sup>2</sup> This means that the process removes majority class datapoints with a majority of its nearest neighbors belonging to the minority class, and vice versa. Majority in this context can be freely defined: it could mean that at least one neighbor is of a different class or that the proportion of neighbors in a different class exceeds a certain threshold.

ENN downsampling is usually done with 3 nearest neighbors, as illustrated below.

     ![A diagram of downsampling - Boundry Preservation](https://assets.ibm.com/is/image/ibm/downsampling-near-miss-boundary-preservation:1x1?fmt=png-alpha&dpr=on%2C2.5&wid=320&hei=320)

This is a coarser-grain strategy because it looks at the general neighborhood of points rather than at a single neighbor, but it is an efficient way to get rid of noise within the data. ENN downsampling is most effective when combined with other techniques.

## Recent research

Current developments in downsampling revolve around deep learning integrations. This has been used in fields like image processing and medical data, which involve using neural networks to downsample the data.<sup>6</sup> An example of this is SOM-US, which uses a two-layer neural network.<sup>7</sup> In recent years, active learning has also been applied to downsampling to try and mitigate effects of imbalanced data.<sup>8</sup> Experiments have shown that these models perform significantly better than traditional techniques.

Current research in downsampling also revolve around combining it with other techniques to create hybrid techniques. One combination is to both downsample and upsample the data to get the benefits of both: SMOTE+Tomek Link, Agglomerative Hierarchical Clustering (AHC), and SPIDER are a few examples of these.<sup>9</sup> Algorithm-level techniques can also incorporate ideas from traditional downsampling techniques, such as with Hard Example Mining where training only focuses on the ‘harder’ data points.<sup>2</sup> All show better performance than using each technique individually.

Link copied