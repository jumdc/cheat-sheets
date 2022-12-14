# Basic ML

## Summary 
1. [DB-Scan](#db-scan)
2. [RandomForest](#rf)


## db-scan <a name="db-scan"></a>

**DBSCAN** is a clustering method that is used in machine learning to separate clusters of high density from clusters of low density region. Its a very efficient clustering algorithm as it used to segregate the data points with high density observations vs data points of low density observations in form of various clusters.

hyperparameters : 
- `eps` :  The maximum distance between two samples for one to be considered as in the neighborhood of the other. This is not a maximum bound on the distances of points within a cluster. This is the most important DBSCAN parameter to choose appropriately for your data set and distance function.
default=0.5
- `min_samples` : The number of samples (or total weight) in a neighborhood for a point to be considered as a core point. This includes the point itself.
default=5

## random forest <a name="rf"></a>

Hyperparemeters : 
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
