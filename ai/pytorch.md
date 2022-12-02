# Pytorch & lightning cheatsheet 


## Summary 
1. [Dataset preparation](#datasaet)
	2. [Dataset](#classDataset)
	3. [ImageDataModule](#datamodule)
2. [optimizers](#optim)
3. [Loss](#loss)


# 1. Dataset <a name="datset"></a>
## 1. `Dataset`, PyTorch class <a name="classDataset"></a>
Three functions must be implemented : `__init__, __len__, and __getitem__`.

- `__len__`
The `__len__` function returns the number of samples in our dataset.

- `__getitem__`
The `__getitem__` function loads and returns a sample from the dataset at the given index `idx`.

## 2. `DataModule`,  Lightning <a name="datamodule"></a>

# 2. Optimizers
To construct an [`Optimizer`](https://pytorch.org/docs/stable/optim.html#torch.optim.Optimizer "torch.optim.Optimizer") you have to give it an iterable containing the parameters (all should be `Variable`' s) to optimize. Then, you can specify optimizer-specific options such as the learning rate, weight decay, etc

`optimizer = optim.SGD(model.parameters(), lr=0.01, momentum=0.9)`

# 3. Losses <a name="loss"></a>
## BCEWithLogitsLoss
This loss combines a Sigmoid layer and the BCELoss in one single class. This version is more numerically stable than using a plain Sigmoid followed by a BCELoss as, by combining the operations into one layer, we take advantage of the log-sum-exp trick for numerical stability.
