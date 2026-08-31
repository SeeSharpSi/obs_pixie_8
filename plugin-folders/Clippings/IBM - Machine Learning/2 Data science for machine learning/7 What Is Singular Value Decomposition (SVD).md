---
title: What is singular value decomposition (SVD)?
source: https://www.ibm.com/think/topics/singular-value-decomposition
author:
- '[[Fangfang Lee]]'
published: 2026-02-19
created: 2026-05-21
description: "SVD is a fundamental concept in linear algebra, and it underlies some of the most popular modern AI applications such as IBM Granite."
---

Singular value decomposition (SVD) is a way to break any matrix into three simpler matrices that reveal its underlying structure. It’s one of the most important tools in machine learning and data science.

## SVD explained

Nearly all forms of information—whether numerical tables, images or text embeddings—can be expressed as a matrix. In [machine learning](https://www.ibm.com/think/topics/machine-learning) and [data science](https://www.ibm.com/think/topics/data-science), models are built by using data transformed from various structured and unstructured inputs. For example, a grayscale image becomes a grid of pixel intensities; a text corpus becomes a term-document matrix. Even the massive weight tensors that drive today’s [large language models](https://www.ibm.com/think/topics/large-language-models) (LLMs) are matrices performing linear transformations in high-dimensional spaces.

In the field of [artificial intelligence](https://www.ibm.com/think/topics/artificial-intelligence) (AI), matrices are the building blocks and language of structure. Each number in a matrix captures how one variable influences another, and matrix multiplication describes how entire systems interact. This ability to represent, manipulate and transform relationships algebraically makes matrices the backbone of [linear algebra](https://www.ibm.com/think/topics/linear-algebra-for-machine-learning).

In practice, building an AI application by using raw data can be extremely complicated. Singular value decomposition (SVD) is a general-purpose matrix factorization technique that simplifies these large matrices into smaller, more structured components. By doing so, it improves storage efficiency, accelerates model training and enhances interpretability—making SVD one of the most powerful tools for managing complexity in modern AI systems.

Because data is represented in matrix format, we can manipulate the matrix to train high-performing models. Conceptually, a matrix acts like a machine that transforms, rotates, scales, reflects or projects data in geometric spaces.

For example, when a vector is multiplied by a matrix, the vector gets transformed into a new coordinate system. These transformations allow algorithms to find patterns, correlations and symmetries that aren’t immediately visible in raw data. The transformation of the matrix helps identify patterns that exist in a massive dataset.

The algebraic and geometric nature explains why matrices are so powerful: they bridge data representation and transformation. In a deep [neural network](https://www.ibm.com/think/topics/neural-networks), for example, every layer is a series of matrix multiplications that learn how to map inputs to outputs through successive calculation of linear combinations of features.

### Linear algebra in machine learning

In the field of AI, data is manipulated and transformed by using the principles of linear algebra, and the discipline defines how data types are transformed and used. Therefore, matrices encode everything from weights and embeddings to covariance structures and similarity graphs. Linear algebra allows us to:

- Represent tables of data as matrices, in which rows of observations are denoted as n, and columns of features are denoted as P.
- Perform **factorization** and **decomposition** to simplify complex objects. An example of factorization is that 16 can be factorized, or decomposed into 2^4—therefore storing only the lower, simpler value instead of the large value. The principle applies to matrix and aids computation, interpretation and model training.
- Build **low-rank approximations** to compress or denoise high-dimensional data. In many datasets, not every feature contributes equally—most of the information lies in a few dominant patterns or directions. By keeping only the top singular values and their corresponding vectors (in SVD), we can approximate the original matrix with a smaller one that captures most of the signals. This “low-rank” form preserves what matters while discarding noise, enabling faster training, less memory usage and often better generalization. It’s the principle behind dimensionality reduction, latent factor models and recommender systems.
- Compute **pseudo-inverses** for least squares regression problems. When a matrix isn’t square or invertible (as is often the case with real-world data), the Moore–Penrose pseudo-inverse provides a way to find the best approximate solution.
- Identify **principal components** in principal component analysis ([PCA](https://www.ibm.com/think/topics/principal-component-analysis#1793360183)) through the eigenvalues and eigenvectors of the covariance matrix. PCA finds directions (also called eigenvectors) where the data varies the most, and each eigenvalue represents how much variance is captured along that direction. By projecting data onto these few principal axes, we uncover the underlying structure—useful for visualization, compression and noise reduction. Computationally, this is achieved by using SVD, where the right singular vectors correspond to principal directions, and the squared singular values correspond to variances.

## SVD in-depth

The singular value decomposition (SVD) is a way of breaking down a complex matrix into simpler, more interpretable components. SVD, similar to PCA, enables large matrices to be broken done into smaller pieces that capture underlying patterns, directions and strengths of the relationship it encodes without capturing the additional noise.

In mathematical form, any matrix A can be written as:

$$ A=U \Sigma V^T $$

SVD allows every matrix (A) to be expressed as a combination of rotations and scalings in space, despite its shape. Other popular matrix decomposition methods often suffer from limitations such as matrix shape requirement, but SVD allows decomposition of matrix A into three smaller matrices: U, V and $\Sigma$. U and V are orthogonal matrices, where $\Sigma$ contains the singular values.

![Diagram made for the Think blog](https://assets.ibm.com/is/image/ibm/svd?ts=1771521495663&dpr=off)

To use a concrete example, a table of movie ranking by various users is shown here:

![Data table made for the Think blog](https://assets.ibm.com/is/image/ibm/movies-x-users?ts=1771521495855&dpr=off)

In the movie dataset, each row represents a user and each column represents a movie. The fields represent users’ rating regarding a specific movie, on a scale of 1–5. Data in the real world, when expressed this way, can quickly become unmanageably large. Instead of storing the large dataset as a single matrix, we can use SVD to not only break it down into simpler pieces, but also identify patterns in it.

SVD can identify features such as:

- What group of users like action movies?
- Which type of movies attract certain groups of users?
- Which movies fall under a distinct category?
- Are there distinct groups of users who prefer a certain type of movies?

SVD factorizes this matrix into three parts:

$$ A=U \Sigma V^{\top} $$

### Step 1. The left singular vector U

U is an orthogonal matrix, meaning its columns are perpendicular and have a unit length. Each column of U represents a fundamental “preference direction” across users. When columns in a matrix are perpendicular, there is linear independence between each column, meaning no correlations will exist in the matrix. Therefore, each column will represent a distinct genre for the movies dataset.

For example:

- The first column of U might represent the “action versus romance” axis among users.
- The second column might represent “comedy versus drama.”

Orthogonality ensures that these preference directions are independent—each captures a distinct type of variation in the data. In vector spaces, when a vector is orthogonal to another, it means that there are no correlations between them, therefore representing independent features. These independent columns form a matrix U that tells us **how each user aligns with hidden preference patterns** found in the data.

### Step 2. Singular values (Σ)

$\Sigma$ is a **diagonal matrix**—a square matrix where all the entries outside the main diagonal axis are zero. Along the diagonal line, values shown (usually represented as $\sigma_1$ , $\sigma_2$ , $\sigma_n$ and so on, are called singular values, and they measure how strong each pattern is).

These singular values are non-negative and arranged in descending order

- A large singular value means that the corresponding pattern explains a lot of variance in the data
- A small one means that the pattern barely contributes—often noise.

In practice, only the top few singular values are retained because they capture most of the variance with much fewer dimensions. The singular matrix sigma indicates the importance of each hidden feature, and helps identify features that are negligible.

### Step 3. The right singular vector (Vᵀ)

V is also an orthogonal matrix where the columns are perpendicular and linearly independent. The matrix Vᵀ represents the movie space: it captures relationships among movies rather than users. In the SVD framework, V contains the right singular vectors, and its columns define new axes or directions along which the movies vary the most in user preference.

Each column of V corresponds to a distinct latent theme direction in the dataset.

For example:

- One direction might represent a contrast between action-oriented and romantic movies.
- Another direction might capture the difference between drama and comedy.

Each row of Vᵀ or equivalently, each column of V can be viewed as the “coordinates of a movie” in this newly discovered “theme space.”

A movie that scores highly along a particular direction is strongly associated with that theme, one that has small or negative values along the same axis diverges from it.

For instance, if the first column of V corresponds to an action-romance spectrum, a movie with a high positive value might be an action blockbuster, while a movie with a large negative value might be a romantic drama.

Through this lens, Vᵀ defines how movies relate to one another in terms of shared underlying factors that shape user ratings.

It converts raw numeric data—individual ratings—into a structured representation of thematic relationships among items.

These relationships form the basis for many modern algorithms: in recommender systems, for instance, they allow unseen movies to be recommended by proximity in this latent semantic space.

## Eigenvalue and eigenvectors

When a matrix transforms data, it rarely acts in a simple way. Most of the time, it rotates points, stretches them in some directions, compresses them in others and mixes features together all at once. In this tangled coordinate system, it is hard to see what the matrix is really doing.

However, hidden inside every transformation are special directions where the behavior becomes clean and predictable. These directions are called **eigenvectors**. When the matrix acts on an eigenvector, it does not twist or redirect it. The vector keeps pointing in the same direction—it only changes in length. The amount of stretching or shrinking along that direction is described by the **eigenvalue**.

Large eigenvalues correspond to directions where the matrix strongly amplifies data, while small or near-zero eigenvalues correspond to directions that are barely affected or flattened entirely.

This idea is powerful because it turns a complicated transformation into something far simpler: independent stretching along a few meaningful axes. Instead of thinking about a matrix as a messy mix of rotations and distortions, eigenvectors reveal its natural directions of action, and eigenvalues measure how important each of those directions is.

SVD is built directly on this same intuition. Rather than letting the matrix operate in its original coordinate system, SVD rotates the data into special directions where the transformation becomes simple and separable.

The matrix **V** contains the key input directions—the fundamental patterns in the original feature space. The matrix **U** contains the corresponding output directions—how those patterns appear after the transformation. The diagonal matrix **Σ** tells us how strongly the matrix acts along each of these directions. In this sense, the singular values in Σ play the same conceptual role as eigenvalues: they quantify the importance of each pattern.

Large singular values indicate directions where the data carries significant structure and variation. Small singular values indicate directions dominated by noise or redundancy. By keeping only the strongest directions and discarding the rest, SVD isolates the essential geometry of the data.

In essence, eigenvectors introduced the idea that complex linear transformations can be understood as simple stretching along special directions. SVD generalizes this idea to any matrix, making it possible to uncover the dominant patterns in real-world datasets, compress information, remove noise and reduce dimensionality. All by focusing on the directions where the matrix truly does meaningful work.
