# The Deep Learning Book
This is the one by Ian Goodfellow, Yoshua Bengion and Aaron Courville

It can be found over [here](http://www.deeplearningbook.org/)

This was the required book for the [NextAI](https://www.nextcanada.com/next-ai/) accelerator program.

Note: Keep the [notation page](http://www.deeplearningbook.org/contents/notation.html) next to you when reading the book.

## Chapter 1: Introduction
- Knowledge base approach to learning is when we hard-code knowledge about the world in formal languages. Cyc is an example of such system.
- machine learning is when the AI system acquire their own knowledge from pattern in raw data. Representation of the data matters a lot to the AI system using machine learning with feature engineered.
- Representation Learning is to use machine learning to discover the representation for the learning task. Muchh better performance than hand-designed representations (Autoencoder are representational leearning algorithm).
- Deep Learning enable to make representation learning out of simpler representation. This leads to a hierarchy of representation.

`Cybernetics -> Connectionism -> Deep Learning`

Deep Learning Algorithm Training Rule of Thumbs:
- 5000 labeled examples per category == acceptable
- 10 million labeled example == human performance (or exceeded)

2016 size of neural network architecture is similar to a frog.

## Chapter 2: Linear Algebra
- The Matrix Cookbook might be a good reference on linear algebra to get.
- Cartesian product of set A and B is all ordered pair (a,b)
- Element-wise product in a matrix is called the Hadamard product
- A matrix multiplication is basically a bunch of dot product between row of one matrix with column of another.
- To solve a linear equation we can use matrix inversion with the concept of a identity matrix. The problem switch from finding the weight to finding an inverse for our matrix of feature. It's a nice theoretical tool, but has limited practical useage.
- For the inverse of the feature to exist we need to have exactly one solution for every value of the output. We could have none or an infinite amount though.
- Having redundant column is a problem in the feature matrix as it reduce the dimentionality.
- Linear dependance means that there is already a linear combination of the vectors that can generate it.
- Matrix needs to be square to have an inverse.
- L^n norm is defined as `(Sum(xi)^p)^(1/p)`
- L^2 is euclidean norm
- L^1 is mostly used when it is important to discrimintate between elements that are exactly zero and elements that are small but non-zero.
- L^inf norm (max norm) = absolute value of elment with largest magnitude.
- Frobenius norm (measure size of a matrix)
- Diagonal matrix offers cheap computation which is great.
- two vector are orthogonal to each other if x^T*y = 0. They are at 90 degree of each other. Orthonormal = orthogonal + unit norm.
- Orthogonal Matrix are square matrix where row are mutually orthonormal and columns are mutually orthonormal.
- **Eigendecomposition**: decompose matrix into functional properties (i.e. egeinvector and eigenvalues). Eigenvector of square matrix A is a non-zero vector such that mulitplication by A alter only it's scale. The scalar multiplier is the Eigeinvalue. We only look at unit eigenvalue. The eigendecomposition of A is then given by `A = V*diag(lambda)*V^-1` where V is a matrix of the eigenvectors of a and lambda is a diagonal matrix of the eigenvalue.
- having specific eigenvalues and eigenvector allow us to stretch space in a desired directions if we want to construct a matrix.
- for the decomposition of real symmetric matrix can be decomposed into using only real-valued eigenvector and eigenvalues.
- Singular Value Decomposition : more generally applicable than the eigendecomposition. Every real matrix has a singular value decomposition (even non-square matrix). A = UDV^T where each matrix has a special structure. U, V are orthogonal matrices and D is diagonal. Element in D are singular values, columns of U are left-singular vector and columns of V are right-singular vectors.
- Moore-Penrose Pseudoinverse is a way to get somewhat of an inverse even when not possible. Using a pseudo-inverse for solving a linear equation give use the solution with minimal euclidean norm.
- The Trace Operator : this concept gives us the sum of all the diagonal entries of a matrix. It's useful to play some identities tricks.
- The Determinant: equal to the product of all eigenvalues of matrix. Absolute value of determinant is a measure of how much multiplication by the matrix expands or contracts space.
- PCA: Lossy compression of these points. PCA is defined by our choice of decoding function. PCA constraint the decoding matrix D to be orthogonal in g(c) = Dc and D to have column with unit norm. We can spin this as an optimization problem where we want to have c and x have a small L2 norm (squared). For the matrix D we can do the same but instead of the L2 norm we use the Frobenius norm. **(Should definetely spend a good deal of time going through the derivation)**

This chapter was nice, it was concise but it was really well tied together at the end with PCA!
## Chapter 3: Probability and Information Theory

## Chapter 4: Numerical Computation

## Chapter 5: Machine Learning Basics
Most deep learning algorithms are based on SGD.
Deep probabilistic model seems nice for medical diagnosis task.
Also Classification with missing inputs is something worth looking at right now especially in EEG where we can have missing channels (Goodfellow et al. ( 2013b )_).

For an [anomaly detection](http://cucis.ece.northwestern.edu/projects/DMS/publications/AnomalyDetection.pdf) review.

>A computer program is said to learn from experience E with respect to some class of tasks T and performance measure P , if its performance at tasks in T , as measured by P , improves with experience E.

Design matrix == dataframe in this book.

Affine Functions means that plot of the model looks like a line, but doesn't need to pass through the origin.

**Stopped at 5.2**
