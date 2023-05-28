# Pytorch & lightning cheatsheet 

- [Pytorch \& lightning cheatsheet](#pytorch--lightning-cheatsheet)
- [Introduction](#introduction)
  - [PyTorch vs TensorFlow](#pytorch-vs-tensorflow)
  - [Tensors](#tensors)
    - [Standard operations](#standard-operations)
- [Interacting with data](#interacting-with-data)
  - [`dataset`, PyTorch class](#dataset-pytorch-class)
  - [`DataLoader`, PyTorch](#dataloader-pytorch)
    - [Understanding the `DataLoader` class](#understanding-the-dataloader-class)
  - [`DataModule`,  Lightning](#datamodule--lightning)
- [The network](#the-network)
  - [designing the network](#designing-the-network)
  - [`nn.sequential`](#nnsequential)
  - [The optimizers](#the-optimizers)
    - [**SGD**](#sgd)
      - [Problems :](#problems-)
      - [momentum](#momentum)
    - [**AdaGrad**](#adagrad)
    - [**Adam**](#adam)
- [Losses](#losses)
  - [BCEWithLogitsLoss : Binary Cross Entropy](#bcewithlogitsloss--binary-cross-entropy)
  - [Cross Entropy loss](#cross-entropy-loss)
- [Steps to follow to train a neural network](#steps-to-follow-to-train-a-neural-network)
  - [normalization](#normalization)
    - [why normalization ?](#why-normalization-)
    - [normalization with pretrained net](#normalization-with-pretrained-net)
- [Regularization techniques](#regularization-techniques)
    - [Dropout](#dropout)



# Introduction
## PyTorch vs TensorFlow
In TensorFlow, you use the library to build up a graph representation of the neural network architecture and then you execute operations on that graph. This causes issues for : 
- debugging
  dynamically altering the architecture during training or inference. 

## Tensors
`tensors` can be thaught of as multidimensionnal arrays. 
They can be created from `list`,  from special functions such as ` ones` and `zeros`,  from standard mathematical operations. 

### Standard operations 
- changing the type of a tensor with `to()`
- finding the max, the argmax : `max()`, `argmax()`
- most functions operating on tensors create a new one to store the result. 
To save memory, look to see if an in-place function is defined, which should be the same name as the original function but with an appended underscore `_` : `tensor2.log()` vs `tensor.log2_()`
- **reshaping** :  `reshape`  
`view`  operates as a view on the tensor: if the initial one changes so does this one
  ```python
  t = torch.rand(784)
  reshaped = t.reshape(1,28,28)
  print(reshaped.shape)
  > torch.Size([1,28,28])
  ```

# Interacting with data
- `dataset` : allows to get the data 
- `dataloader` : feeds the data to the network to be trained or infered

## `dataset`, PyTorch class 
Three functions must be implemented : `__init__, __len__, and __getitem__`.

- `__len__`
The `__len__` function returns the number of samples in our dataset.

- `__getitem__`
The `__getitem__` function loads and returns a sample from the dataset at the given index `idx`.

## `DataLoader`, PyTorch 
The `DataLoader` class is used to create iterators over datasets. It makes the process of iterating over the dataset easier and more efficient.
It allows to : 
- define a dataset 
- batch the data
- shuffle the data
- support multiprocessing workers
- merge datasets together
- laod data directly to *CUDA*

### Understanding the `DataLoader` class
```python
from torch.utils.data import DataLoader

DataLoader(
    dataset, 
    batch_size=1, 
    shuffle=False, 
    sampler=None, 
    batch_sampler=None, 
    num_workers=0, 
    collate_fn=None, 
    pin_memory=False, 
    drop_last=False, 
    timeout=0, 
    *, 
    prefetch_factor=2, 
    persistent_workers=False
)
```
- `dataset`, `PyTorch Dataset` class expected
- `batch_size`, `int` how many samples per batch to load (default: `1`)
- `shuffle`, `bool` set to `True` to have the data reshuffled at every epoch (default: `False`) 
- `sampler`, `PyTorch Sampler` class expected, does not work when `shuffle=True`
- `pin_memory`, `bool` if `True`, the data loader will copy tensors into CUDA pinned memory before returning them. (default: `False`)

- `num_workers`, number of subprocesses to use when loading the dataset. 0 means that the data will be loaded in the main process.

Num_workers tells the data loader instance how many sub-processes to use for data loading, if num_workers=0  the GPU has to wait for the CPU to load the data.

- `persistent_workers`, if True the data loader will not shutdown the worker processes after a dataset has been consumed once. This allows to maintain the workers `Dataset` instances alive. (default: `False`)

- `prefetch_factor`, number of samples loaded in advance by each worker. (default: `2`)
- `drop_last`, set to `True` to drop the last incomplete batch, if the dataset size is not divisible by the batch size. If `False` and the size of dataset is not divisible by the batch size, then the last batch will be smaller. (default: `False`)

## `DataModule`,  Lightning 
Clean module to establish the datasets. 

⚠️ for images, prefer jpg ext to png ext. There are faster to load. 


# The network 

## designing the network 

Example : 
```python
class SimpleNet(nn.Module): 
    def __init__(self): 
        super(SimpleNet, self).__init__()
        self.fc1 = nn.Linear(12288, 84)
        self.fc2 = nn.Linear(84, 50)
        self.fc3 = nn.Linear(50,2)

    def forward(self):
        x = x.view(-1, 12288)
        x = F.relu(self.fc1(x))
        x = F.relu(self.fc2(x))
        # x = F.softmax(self.fc3(x)) 
        # If we use CrossEntropyLoss incorporates a softmax direclty in its calculation. 
        return x
```
In the `__init__` we define the layers, and in the `forward` the way the data will flow into the network. The class inherites from `torch.nn.Module`. 

## `nn.sequential` 
Allows to create a sequence of layers. 


```python
  self.features = nn.Sequential(
            nn.Conv2d(3, 64, kernel_size=11, stride=4, padding=2),
            nn.ReLU(),
            nn.MaxPool2d(kernel_size=3, stride=2),
            nn.Conv2d(64, 192, kernel_size=5, padding=2),
            nn.ReLU(),
            nn.MaxPool2d(kernel_size=3, stride=2),
            nn.Conv2d(192, 384, kernel_size=3, padding=1),
            nn.ReLU(),
            nn.Conv2d(384, 256, kernel_size=3, padding=1),
            nn.ReLU(),
            nn.Conv2d(256, 256, kernel_size=3, padding=1),
            nn.ReLU(),
            nn.MaxPool2d(kernel_size=3, stride=2),
        )
```
It can be use to create nore logical arrangements in the code. 
## The optimizers

To construct an [`Optimizer`](https://pytorch.org/docs/stable/optim.html#torch.optim.Optimizer "torch.optim.Optimizer") you have to give it an iterable containing the parameters (all should be `Variable`' s) to optimize. Then, you can specify optimizer-specific options such as the learning rate, weight decay, etc




### **SGD**  
`optimizer = optim.SGD(model.parameters(), lr=0.01, momentum=0.9)`

Why **stochastic** ? Think of loss as an expectation over the full data distribution and we approximate the expectation via sampling.

#### Problems : 
- what if loss changes quickly in one direction and slowly in another (loss function has high condition number) ? The gradient has slow progression and jitter.
- Saddle point & local miminum, in both case gradient can get stuck
- Stochastic aspect : the gradients can be noisy 

#### momentum  
Momemtum can be an anwser the issues mention above  
$W_{t+1} = W_t - V_t$  
$V_t = \beta*V_{t-1} + \nu*\Delta(W_t)$

Based on the *Exponential Weighted Average* which applies weighting factors which decrease exponetionaly. $s_t = \alpha*x_t + (1 - \alpha)*s_{t-1}$. The highest alpha the more we try to get an average of past data. 


What learning rate to use ? $e-3$

### **AdaGrad**
Added element-wise scaling of the gradient absed on the historical sum of squares in each dimension, but why ? 
Progress along 'steep' directions is damped and progress along 'flat' directions is accelerated. 

$G += g_t * g_t$  
$w_{t+1} = w_t - \eta \,\text{diag}(G)^{-1/2} g_t$

But G will grow and grow, and has the effect of decaying the learning rate. 

Variant : RMSProp "LeakAdagrad"

### **Adam**
Basicly : RMSProp + Momentum



# Losses 
## BCEWithLogitsLoss : Binary Cross Entropy
This loss combines a Sigmoid layer and the BCELoss in one single class. This version is more numerically stable than using a plain Sigmoid followed by a BCELoss as, by combining the operations into one layer, we take advantage of the log-sum-exp trick for numerical stability.

## Cross Entropy loss


# Steps to follow to train a neural network 
[A recipe for training neural networks](https://karpathy.github.io/2019/04/25/recipe/)

At each step, we make concrete hypothesis about what will happen and then either validate them or investigate further why it won't work. 

1. Become one with the data
2. Set-up an end-to-end training/eval skeleton \& and get dumb baselines 
	- fix a random seed `pytorch_lightning.seed_everything(1999)`
	- verify loss @init, example for a softmax : $-log(\frac{1}{n_{classes}})$  
  
    	Example of values : 
		- $n_{classes} = 2$, $0.30$
	- init well 
	- input-independant baseline (e.g all input equal to 0)
	- overfit one batches
	- visualize the dataset just before the network 
	- visualize pred dynamics on val set
  
## normalization 

### why normalization ? 

We want the data to be more amenable for efficient training. 
In the following example, we visualize the training data where each axis is a features of the data set. (In matrix notation $X \in \R^{n*d}$ and here $d=2$.)

![Screenshot from 2023-03-13 15-06-05](https://user-images.githubusercontent.com/62952163/224727614-e9f67059-7a01-487c-ae87-3cb21fd4edfb.png)

More precisely, it's linked with gradients. 
If all the data is positive or neg so are the gradients and thus taking more steps to converge following one direction at a time. 

Furthermore after normalization, the training set is less sensitive to small changes in weights and easier to optimize. 

### normalization with pretrained net

If a pre-train model is used, use the same normalization that was used for the pre-training. 

Example for the kinetics dataset : 
```python
transform=Compose([
  Normalize((0.45, 0.45, 0.45), (0.225, 0.225, 0.225))
])
```

# Regularization techniques    

### Dropout
**What is Dropout?**
> Dropout is a technique where randomly selected neurons are ignored during training. They are “dropped-out” randomly. This means that their contribution to the activation of downstream neurons is temporally removed on the forward pass and any weight updates are not applied to the neuron on the backward pass.
