# Basic ML

- [Basic ML](#basic-ml)
  - [db-scan](#db-scan)
    - [Hyperparameters](#hyperparameters)
  - [Random Forest](#random-forest)
    - [Bagging aka bootstrap aggregating](#bagging-aka-bootstrap-aggregating)
    - [Hyperparemeters](#hyperparemeters)
  - [SVM](#svm)
    - [Hyperparameters](#hyperparameters-1)
    - [Kernels specifications](#kernels-specifications)
  - [AdaBoost](#adaboost)
    - [Boosting](#boosting)
    - [Definition](#definition)
  - [Logistic regression](#logistic-regression)
    - [ROC](#roc)


## db-scan 

**DBSCAN** is a clustering method that is used in machine learning to separate clusters of high density from clusters of low density region. Its a very efficient clustering algorithm as it used to segregate the data points with high density observations vs data points of low density observations in form of various clusters.

### Hyperparameters 
- `eps` :  The maximum distance between two samples for one to be considered as in the neighborhood of the other. This is not a maximum bound on the distances of points within a cluster. This is the most important DBSCAN parameter to choose appropriately for your data set and distance function.
default=0.5
- `min_samples` : The number of samples (or total weight) in a neighborhood for a point to be considered as a core point. This includes the point itself.
default=5

## Random Forest 

### Bagging aka bootstrap aggregating


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
### Boosting

**Boosting** try to answer the question : "Can a set of weak learners create a single strong learner?". 
A weak classifier being a classifier that is only slightly better that a random classifier. 
Most boosting algorithms consist of iteratively learning weak classifier with respect to a distribution and adding them to a final strong classifier. 

### Definition 

AdaBoost is adaptive in the sense that subsequent weak learners are tweaked in favor of those instances misclassified by previous classifiers.
Although AdaBoost is typically used to combine weak base learners (such as decision stumps), it has been shown that it can also effectively combine strong base learners (such as deep decision trees), producing an even more accurate model

## Logistic regression 

### ROC 

**ROC** curve shows the performance of a classification model at all classification thresholds.  
- $recall = \frac{TP}{TP + FN}$  
- $fpr = \frac{FP}{FP + TN}$

ROC curve : recall vs FRP at different classification threshold. 

**Examples** :  
- if the threshold is $0.5$, and the predicted proba is $0.49$ then the outcome is negative
- if the threshold is $0.3$, and the predicted proba is $0.49$ then the outcome is positive