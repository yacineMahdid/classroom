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