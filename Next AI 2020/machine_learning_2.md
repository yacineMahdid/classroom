# Machine Learning #2
This was the second remote course for NextAI 2020, it was a class only for the CTOs and it delved into more technical details than the previous overview. This course was once again thought by [Dr. Laurent Charlin](https://www.hec.ca/en/profs/laurent.charlin.html)
Here are my raw notes:

Neural Networks Basics:
- They are highly non-linear and super flexible
- Decision rule is added to linear regression in order to make linear classification
- If something is not solvable by a linear classifier, joint decision of several linear classifier make the problem linearly separable. This is akin to having a third function taking the two other function output as input (which is the basic idea of what a neural network is)

Feed Forward Neural Network:
- Each node do a simple weighted sum and pass the result through an activation function
- At test time we simply do a forward pass through all the node and layers
- At training we do a gradient based optimization (stochastic gradient descent)
- Heaviside step function is not differentiable so we need to have a smoother activation function
- We can use sigmoid, relu, leaky-relu (+ a billion more)
- To train we do a backward pass (backpropagation if we have multiple layers)
- We simply substract the gradient (gained by SGD) to the weight as follow `w = w - a*gradient_w` where a is the learning rate.
- Gradient Descent is central algorithm in neural network (the stochastic version of it).
- Deeper network is better than wider network (even with the same proportion of parameters)
- A deep neural network doesn't need feature engineering as it learn the representational encoding

Activation Functions:
- It's a type of function that take the weighted sum of input and run it through a non-linearity. This improves the representational power but also augment the optimization difficulties
- Logit: saturate on both sides
- Relu is doing f(x) = max{0,z}, its a very good activation function that is highly used. However, it is not differentiable at 0.000000000000000000000000000 (which almost never happen when we use computers)
- This will also shut off units when its activation is below 0
- for the output neuron there are differnt function that can be used like softmax which depends on what the output needs to be.

Regularization:
- DNN will overfit if not careful
- we can do weight decay (i.e. L2 regularization)
- early stopping by monitoring the loss on the test set
- Size of the neural nets can also be penalized
- rule of thumbs: start small and then go deeper
- we can also use dropout, wihch ends up training multiple neural nets implicitly.

Neural Networks in practice:
- Interpretability of neural network is difficult
- Need to setup the architecture, we can play with architecture over here with [tensorflow playground](http://playground.tensorflow.org)
- Scikit learn, Pytorch, Tensorflow, Keras, Theano, Caffee, PySpark, NLTK are all tools that I should be familiar with 
- FFNN is not at all suited for some task other architectures makes more sense

Recurrent Neural Network (RNN):
- This is good for text, speech, stock price, **sensor through time**, videos, dna
- The length here is not fixed for the input or potentially the output
- The intuition behind this is similar to reading a book, the word are not all at once in your brain they come one behind each other.
- The middle units is recurrent meaning it feedbs back into itself (could also use LSTM cells for better performance or GRU units)
- Parameters are shared over time, otherwise it will be a mess to optimize
- To train that thing we need to use gradient descent through time.
- RNN can get exploding or vanishing gradient, gradient clipping help or use LSTM/GRU (gives memory without gradient)
- There are different architecture for the RNN depending on the task, like deep RNNs or bi-directional RNN.
- There are also decoder/encoder called transformer architecture that rivalized with RNN (ELMO ET BERT)

Convolutional Neural Network (CNN)
- FFNN doesn't scale well to high dimensional data. There is a lot of connection we don't need al of them necessarly.
- Image is scale and translational invariant
- to mimick that we can make a object detector over all regions of image
- convolution involve a kernel which will do a dot product with a single pixel
- detector is usually bigger than single pixel, kernels are also something to learn
- For instance having a kernel of [1,-1] will be a edge detector as it makes the difference between two neighboring pixels
- CNN have sparse connection and the weights are shared (this reduce the complexity)
- There are different type of architecture possible (like anything goes) here are a few: inception, U-nets and ResNets.
- Pretrained models are available to use, just watch out though that the training that they gained is useful for you
- We can also mix and matches different architecture together depending on the problem (like image captioning use RNN and CNN)

