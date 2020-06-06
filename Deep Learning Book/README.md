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
- probability theory is used both to make ai agent or to analyze ai agent. information theory allow to quantify amount of uncertainty in a probability distribution.
- in practice it is better to use a simple but uncertain rule than a complex but certain one.
- there are two kind of probability framework (frequentist and Bayesian), I am very familiar with the first one and not so much with the second one. The second has to do with the degree of belief.
- nice definition: "Probability theory provides a set of formal rules for determining the
likelihood of a proposition being true given the likelihood of other propositions."
- Probability mass function (discrete variables) have three propoerties:
  - domain need to map all possible states of x
  - impossible P(x) = 0, always P(x) = 1
  - if we sum all P(x) we get 1
- Probability Density function (continous) have three properties:
  - domain map to all possible states of x
  - p(x) >= 0 but not necessarly smaller than 1
  - integral should equal to 1
- Chain rule of probability = joint probability distribution can be decomposed into conditional distribution over only one variable.
- We have expected values and vairance for probability distributions

Useful common probability distributions:
- Bernoulli
- Multinoulli
- Gaussian (good default when not knowing distribution)
- Multivariate normal distribution (for the two above we can have a precision parameter B to more efficiently parametrize the distribution)
- Exponential Distribution
- Laplace distribution
- Dirac Delta function (for empirical distribution)
- Can do mixtures of distribution by sampling with a multinoulli which distribution to generate the sample. Gaussian mixture model are a type of mixtures of distribution (important).

Useful Properties of common functions:
- Logistic sigmoid
- softplus

Jacobian matrix seems to be an important concept in machine learning
learning that an unlikely event has occured is more informative than learning that a likely event has occured.

Shannon Entropy is the amount of uncertainty in an entire probability distribution.
The Kullback-Leibler divergence can measure how different two distribution are for a single variable x. Related to KL is cross entropy.

Factorization of a probability distribution with a graph we call that a structured probabilistic model or a graphical model.
## Chapter 4: Numerical Computation
In a computer there are approximation of real number because we have a physical computer.\
- Directional derivative in dircetion u (unit vector) is the slope of the function f in direction u.
- The gradient points directly uphill and the negative gradient point directly downhill.
- Jacobian matrix is a matrix of all partial derivatives.
- second derivative are derivative of derivative, it measures curvature. It's like more info on the function environment around a point.
- Hessian matrix is like the Jacobian but for second derivatives. It's the Jacobian for the gradient lol. eigeinvector of H can be used to improve the gradient descent.
- We can do a second derivative test for the local minima/maxima
- optimization algorithm that use only the gradient are called first-order optimization algorithms. Those that are using the information in the Hessian matrix (like the Newton method) are called second-order optimization algorithms.
- Lipschitz continous is used to gain guarantees when using deep learning model.
- importance of convex optimization is not that great in deep learning.
- Karush-Kuhn-Tucker approach for contrasined optimization generate a new function called the generalized Langrangian.
- Condition for a point to be optimal (Karush-Kuhn-Tucker conditions):
  - gradient of the generalized Lagrangian is zero
  - all contraints on both x and KKT multipliers are satisfied
  - inequality constraints exhibit complementary slackness.

## Chapter 5: Machine Learning Basics
Most deep learning algorithms are based on SGD.
Deep probabilistic model seems nice for medical diagnosis task.
Also Classification with missing inputs is something worth looking at right now especially in EEG where we can have missing channels (Goodfellow et al. ( 2013b )_).

For an [anomaly detection](http://cucis.ece.northwestern.edu/projects/DMS/publications/AnomalyDetection.pdf) review.

>A computer program is said to learn from experience E with respect to some class of tasks T and performance measure P , if its performance at tasks in T , as measured by P , improves with experience E.

Design matrix == dataframe in this book.

Affine Functions means that plot of the model looks like a line, but doesn't need to pass through the origin.

What separates machine learning from optimization is that we want the generalization error.
Training and test data generated by a data-generating process. For statistical learning we make the i.i.d. (independent, identically distributed) assumptions: examples from training and test set are independent and identically distributed.

Test error will always be bigger than the training error. The goal of a machine learning algorithm is to:
- Make the training error small (Overfitting)
- Make the gap between training and test error small (Underfitting)

Capacity is what control if we underfit or overfit. Increasing the amount of parameters the classifier can use. Models with high capacity can solve complex tasks, but when their capacity is higher than needed to solve the present task, they may overﬁt.

Representational capacity is the family of functions a learning algorithm can choose from. Model doesn't find the best function within that family, but one that reduce the the training error significantly.

Occam's razor: s equally well, we should choose the “simplest” one.

Vapnik-Chervonenkis dimension (VC dimension) measure capacity of a binary classifier.

The discrepancy between training error and generalization error is bounded from above by a quantity that grows as the model capacity grows but shrinks as the number of training examples 
increases.

There exist non-parametric model doesn't define the parameters before the data is observed. For instance the nearest neighbor regression.

Bayes error is the error incured by an oracle making predictins from the true distribution (because there is noise in the process)

No Free Lunch Theorem, no machine learning algorithm is universally any better than any other. But this only holds for trying to learn all distribution. The goal of machine learning research is not to seek a universal learning algorithm. We need to design our machine learning algorithms to perform well on a specific task.

Hypothesis space is the space of all functions that the classifier can choose from. We can give preference for one solution over another in that hypothesis space by using regularization. Regularization is any modfiication we make to a learning algorithm that is intended to reduce its generalization error but not its training error. This is why we need a validation set. This validation set is constructed from the training data (this will allow us to update the parameter without overfitting).

In machine
learning experiments, it is common to say that algorithm A is better than algorithm B if the upper bound of the 95 percent conﬁdence interval for the error of algorithm A is less than the lower bound of the 95 percent conﬁdence interval for the error of algorithm B.

Bias and variance measure two different source of error in an estimator. Bias measures the expected deviation from the true value of the function or parameter. Variance provides a measure of the deviation from the expected estimator value that any particular sampling of the data is likely to cause.

Cross validation is highly successful on many real-world tasks.

Bias and variance tradeoff is tightly linked to capacity, underfitting and overffiting. Increase capacity tends to increase variance and decrease bias.

Maximum Likelihood Estimation: minimizing the dissimilarity between the empirical distribution that is generating the data defined by the training set and the model distribution. The degree of dissimilarity between the two is measured by the KL divergence.

Cross entropy is any loss consisting of a negative log-likelihood between empirical distribution defined by the model. Mean squared error is the cross entropy between the empirical distribution and a gausian model.

Maximum likelihood is often considered the preferred estimator to use for machine learning.

Bayesian statistics: we have a prior probability distribution of the parameter we want to fit. We have a distribution of likely value for a parameter. We can then use the value along with their probability density to output a number. We integrate over the probability in order to have a value. Bayesian methods typically generalize much better when limited training data is available but typically suffer from high computational cost.

We can go from distribution to point estimate by choosing the maximum a posteriori (MAP) point estimate.

Logistic Regression is a classification algorithm where we learn linear equation and we squash the output between 0 and 1.

in SVM, the kernel-based function is exactly equivalent to preprocessing the data by applying the kernel to all inputs, then learning a linear model in the new transformed space. Kernel trick render high dimensional feature space tractable.

Gaussian kernel is the one most commonly used (RBF; Radial Basis Function).
