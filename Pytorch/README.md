# 60 minute blitz
- tensor == same thing as numpy array but can run on gpus
- we can do addition in many different ways
- in place stuff are post fixed with `_`
- numpy and pytorch are deeply linked in syntax
- resizing we can use torch.view()
- `.item()` will give you the number as a python number
- to use CUDA we can use `.to(device)`:
```python
    device = torch.device("cuda")          # a CUDA device object
    y = torch.ones_like(x, device=device)  # directly create a tensor on GPU
    x = x.to(device)   
```
- pytorch autograd can automatically track and calculate gradient
- autograd is super cool, should try to peek under the hood to see how it works
- when creating a network we just need to define the forward function and the backward is automatically defined for us.
- we can only input mini-batches to torch.nn. This means we need a 4D tensor: `nSamples x nChannels x Height x Width.`
- once we have the loss we can call backward on it and be able to differentiate the whole network w.r.t that loss. Don't forget to zero the gradient otherwise they will be accumulated.
- torch.optim is where all of the packages for doing gradient-descent / optimization of the weights are
- torchvision is used to load usual image dataset
- When making a model look at how the layer are initialized to find out what parameters go where. Otherwise it's difficult to know.
- Here is a simple convolutional neural net:
```python
import torch.nn as nn
import torch.nn.functional as F


class Net(nn.Module):
    def __init__(self):
        super(Net, self).__init__()
        self.conv1 = nn.Conv2d(3, 6, 5)
        self.pool = nn.MaxPool2d(2, 2)
        self.conv2 = nn.Conv2d(6, 16, 5)
        self.fc1 = nn.Linear(16 * 5 * 5, 120)
        self.fc2 = nn.Linear(120, 84)
        self.fc3 = nn.Linear(84, 10)

    def forward(self, x):
        x = self.pool(F.relu(self.conv1(x)))
        x = self.pool(F.relu(self.conv2(x)))
        x = x.view(-1, 16 * 5 * 5)
        x = F.relu(self.fc1(x))
        x = F.relu(self.fc2(x))
        x = self.fc3(x)
        return x


net = Net()
```
- Once the architecture is create we need to attach a loss to the network and choose an optimizer (like stochastic gradient descent) like so:
```python
import torch.optim as optim

criterion = nn.CrossEntropyLoss()
optimizer = optim.SGD(net.parameters(), lr=0.001, momentum=0.9)
```
- Try to keep the same terminology so that debugging is easier (criterion/optimizer)
- When training the neural network we often do more than one pass on the training data