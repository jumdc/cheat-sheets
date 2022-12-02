# Basic ML

## Summary 
1. [DB-Scan](#db-scan)


## db-scan <a name="db-scan"></a>

**DBSCAN** is a clustering method that is used in machine learning to separate clusters of high density from clusters of low density region. Its a very efficient clustering algorithm as it used to segregate the data points with high density observations vs data points of low density observations in form of various clusters.

hyperparameters : 
- eps :  The maximum distance between two samples for one to be considered as in the neighborhood of the other. This is not a maximum bound on the distances of points within a cluster. This is the most important DBSCAN parameter to choose appropriately for your data set and distance function.
default=0.5
- min_samples : The number of samples (or total weight) in a neighborhood for a point to be considered as a core point. This includes the point itself.
default=5
