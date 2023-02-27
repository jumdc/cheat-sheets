![téléchargement](https://user-images.githubusercontent.com/62952163/214655559-a65dd17b-cf6d-4a9f-bc23-95f1709e21fc.jpeg)

 
 Table of contents : 

- [Generalities](#generalities)
    - [Bias and variance in machine learning](#bias-and-variance-in-machine-learning)
    - [Ensemble models](#ensemble-models)
    - [Probability calculus](#probability-calculus)
- [Models](#models)
  - [db-scan](#db-scan)
    - [Hyperparameters](#hyperparameters)
  - [Random Forest](#random-forest)
    - [Hyperparemeters](#hyperparemeters)
  - [SVM](#svm)
    - [Hyperparameters](#hyperparameters-1)
    - [Kernels specifications](#kernels-specifications)
  - [AdaBoost](#adaboost)
    - [Definition](#definition)
    - [Hyperparameteres](#hyperparameteres)
  - [Logistic regression](#logistic-regression)
    - [Regularization](#regularization)
  - [ROC](#roc)
- [Feature Selection](#feature-selection)
  - [Filter methods](#filter-methods)
    - [Variance](#variance)
- [Cross-validation](#cross-validation)
    - [Stratified KFOLD](#stratified-kfold)


# Generalities 

### Bias and variance in machine learning 
   
$error = variance + bias + noise$

- Bias 
> Bias is considered a systematic error that occurs in the machine learning model itself due to incorrect assumptions in the ML process.

Technically, we can define bias as the error between average model prediction and the ground truth. Moreover, it describes how well the model matches the training data set:

A low bias model will closely match the training data set

- Variance
> Variance refers to the changes in the model when using different portions of the training data set. 

In other words, variance is the variability in the model prediction—how much the ML function can adjust depending on the given data set.

- Bias vs Variance 
Bias and variance are inversely connected. It is impossible to have an ML model with a low bias and a low variance.

### Ensemble models
> What Is Ensemble Learning?
Ensemble learning is a widely-used and preferred machine learning technique in which multiple individual models, often called base models, are combined to produce an effective optimal prediction model.

Several types of ensemble models exist : 
- Bagging (Bootstrap aggregating)

Bootstrapping is the method of randomly creating samples of data out of a population with replacement to estimate a population parameter.

Reduces the variance of a model. 
- Boosting 
> **Boosting** try to answer the question : "Can a set of weak learners create a single strong learner?". 
A weak classifier being a classifier that is only slightly better that a random classifier. 
Most boosting algorithms consist of iteratively learning weak classifier with respect to a distribution and adding them to a final strong classifier. 

Redues the bias of a  model (fits more closely to the data)
  
### Probability calculus
- Combinations  
Number of combination of k among n : $\binom{n}{k} = \frac{n!}{ k!( n-k)!}$

# Models
## db-scan 

**DBSCAN** is a clustering method that is used in machine learning to separate clusters of high density from clusters of low density region. Its a very efficient clustering algorithm as it used to segregate the data points with high density observations vs data points of low density observations in form of various clusters.

### Hyperparameters 
- `eps` :  The maximum distance between two samples for one to be considered as in the neighborhood of the other. This is not a maximum bound on the distances of points within a cluster. This is the most important DBSCAN parameter to choose appropriately for your data set and distance function.
default=0.5
- `min_samples` : The number of samples (or total weight) in a neighborhood for a point to be considered as a core point. This includes the point itself.
default=5

## Random Forest 

Bagging with as base estimator decision trees. 

### Hyperparemeters 
- `min_samples_split` : minimum requiered number of observations in order to split it. B
When the value is set to default (2) : the tree keeps on splitting until the nodes are completely pure which induce a tree prone to overfitting. Thus incresing this hyperparameter can tackle overfitting. 
- `max_depth` : maximum depth of the tree. It defines the longest possible path between the root node and the leaf node. 
- `max_terminal_nodes`: the maximum number of terminal nodes. If after splitting we have more than the value of `max_terminal_nodes` the tree will not grow further. 
- `min_samples_leaf`: specifies the minimum number of samples that should be present in the leaf node after splitting. 
The tree is prone to overfitting when it's set very low. 
- `n_estimators`: number of decision trees fitted
- `max_samples`: determines what fraction of the original dataset is given to an individual tree. 
When it's decreased : takes less time to train. (Works when bootstrap is set to true). 
- `max_features`

## SVM 
SVM creates a decision boundary which makes the distinction between two or more classes. 

To overcome overfitting (very precise decision boundary on the training data), the concept of 'soft boundary' was introduced. It allows some examples to be misclassified. It often results in a better generalized model. 

A soft margin SVM tries to solve two optimizations problems: 
- Increase the distance of decision boundary to classes
- Maximize the number of points that are correctly classified in the training set

There is a trade-off between those two goals. The decision boundary might be very close to one class to correctly label all points in the training set. However : might result in a low accuracy. 
However, a far decision boundary might result in misclassifications. 

### Hyperparameters 
-  `kernel` : which kernel ? relates to the kernel trick. The inputs are original features and the output is a similarity measure in the new feature space. Useful when the data are not linearly seperable. 
-  `C` : adds a penalty to each misclassified points. Thus if c is small, the penalty for a misclassification point is low and the boundary with large margin tend to be chosen. And if C is large, high penalty for misclassified points -> boundary wiht smaller margins. 
-  `gamma` : controls the distance of influence of a single point. Low values of gamma indicates a large similarity radius which results in more points being grouped together. For high values of gamma, the points need to be very close to each other in order to be considered in the same group. Large gamma are likely to end up in overfitting. 
  
With a linear kernel only  `C`  needs to be optimize. 
Otherwise both **C** and **gamma** need to be taken into account. 

Examples of values : 
$0.0001 < \gamma < 10$ and  $0.1 < C < 100$. 



**ATTENTION : features need to normalize**

### Kernels specifications
- **radial basis function** (RBF), highly popular due to its similar with a gaussian distribution 


## AdaBoost 

### Definition 


An AdaBoost classifier begins by fitting a classifier on the original dataset and then fits additional copies of the classifier on the same dataset but where the weights of incorrectly classified instances are adjusted such that subsequent classifiers focus more on difficult cases.

AKA : instances are attributed weights to give them more or less importance depending on wether they were correctly classified or not. The weights are update at each iteration accoriding to a learning rate. 

### Hyperparameteres
- `estimator`: estimator used
- `n_estimators`, number of subsequent estimators fitted. between : [1, inf)
- `learning_rate`: this parameter is provided to shrink the contribution of each classifier.



## Logistic regression 

### Regularization 
- elastic net : combination between $l1$ and $l2$ regularization. 

## ROC 

**ROC** curve shows the performance of a classification model at all classification thresholds.  
- $recall = \frac{TP}{TP + FN}$  
- $fpr = \frac{FP}{FP + TN}$

ROC curve : recall vs FRP at different classification threshold. 

**Examples** :  
- if the threshold is $0.5$, and the predicted proba is $0.49$ then the outcome is negative
- if the threshold is $0.3$, and the predicted proba is $0.49$ then the outcome is positive
- if the threshold is $0.3$, and the predicted proba is $0.49$ then the outcome is positive

<img width="917" alt="perfect ROC" src="https://user-images.githubusercontent.com/62952163/214248947-caf3af53-f5b4-41be-82f9-eb567b20bb19.png">

<img width="917" alt="good ROC" src="https://user-images.githubusercontent.com/62952163/214249078-472955c1-acf6-4552-a308-c670e249b381.png">

# Feature Selection 

## Filter methods 
> pick up the intrinsic properties of the features measured via univariate statistics instead of cross-validation performance

### Variance

The variance threshold is a simple baseline approach to feature selection.
It removes all features which variance doesn’t meet some threshold. By default, it removes all zero-variance features, i.e., features that have the same value in all samples. We assume that features with a higher variance may contain more useful information, but note that we are not taking the relationship between feature variables or feature and target variables into account, which is one of the drawbacks of filter methods.

# Cross-validation 

### Stratified KFOLD
[Implementation of n-fold which is designed to](https://scikit-learn.org/stable/modules/generated/sklearn.model_selection.StratifiedKFold.html#sklearn.model_selection.StratifiedKFold) : 
- Generate test sets such that all contain the same distribution of classes, or as close as possible.
- Be invariant to class label: relabelling y = ["Happy", "Sad"] to y = [1, 0] should not change the indices generated.
- Preserve order dependencies in the dataset ordering, when shuffle=False: all samples from class k in some test set were contiguous in y, or separated in y by samples from classes other than k.
- Generate test sets where the smallest and largest differ by at most one sample.
