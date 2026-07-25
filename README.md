# hierarchical-clustring
# Hierarchical Clustering in Machine Learning

Hierarchical clustering is an **unsupervised learning** technique used to group similar data points into clusters. Unlike some other clustering methods, it does not always require the number of clusters to be decided in advance. Instead, it creates a **tree-like structure** of clusters known as a **dendrogram**.

## What is Hierarchical Clustering?

Hierarchical clustering organizes data into a hierarchy of clusters. It helps us understand how data points are related to each other based on similarity or distance.

There are two main approaches:

### 1. Agglomerative Hierarchical Clustering

This is a **bottom-up** approach.

* Start with each data point as a separate cluster.
* Merge the closest clusters step by step.
* Continue until all points are merged into one cluster or the desired number of clusters is reached.

This is the most commonly used method.

### 2. Divisive Hierarchical Clustering

This is a **top-down** approach.

* Start with all data points in one cluster.
* Split the cluster into smaller groups step by step.
* Continue until each data point becomes its own cluster.

This method is less common because it is more computationally expensive.

## Dendrogram

A dendrogram is a tree diagram that shows the merging or splitting process in hierarchical clustering.

* The **horizontal axis** represents the data points.
* The **vertical axis** represents the distance or dissimilarity between clusters.

The height at which two clusters are joined indicates how similar or different they are.
A lower merge height means the clusters are more similar.

## How Hierarchical Clustering Works

For agglomerative clustering, the process is as follows:

1. Treat each data point as an individual cluster.
2. Calculate the distance between all clusters.
3. Merge the two closest clusters.
4. Recalculate distances after the merge.
5. Repeat the process until the final clustering structure is formed.

## Distance Measures

To measure similarity between data points, different distance metrics can be used:

* Euclidean distance
* Manhattan distance
* Cosine distance
* Minkowski distance

Among these, **Euclidean distance** is one of the most commonly used.

## Linkage Methods

Linkage defines how the distance between two clusters is calculated.

### 1. Single Linkage

Uses the minimum distance between points of two clusters.

* Simple and fast
* May create long, chain-like clusters

### 2. Complete Linkage

Uses the maximum distance between points of two clusters.

* Produces compact clusters
* More sensitive to outliers

### 3. Average Linkage

Uses the average distance between all pairs of points from two clusters.

* More balanced than single or complete linkage
* Often a practical choice

### 4. Ward’s Linkage

Merges clusters in a way that minimizes the increase in variance.

* Very popular
* Produces well-separated and compact clusters

## Advantages of Hierarchical Clustering

* Does not always require the number of clusters in advance
* Easy to visualize using a dendrogram
* Useful for small to medium-sized datasets
* Provides a clear understanding of cluster relationships
* Highly interpretable

## Disadvantages of Hierarchical Clustering

* Not suitable for very large datasets
* Computationally expensive
* Once clusters are merged or split, the decision cannot be reversed
* Sensitive to the choice of distance metric and linkage method
* Outliers can affect the clustering result

## Applications

Hierarchical clustering is commonly used in:

* Customer segmentation
* Document grouping
* Image analysis
* Gene expression analysis
* Market research
* Social network analysis

## Hierarchical Clustering vs K-Means

| Feature                          | Hierarchical Clustering  | K-Means        |
| -------------------------------- | ------------------------ | -------------- |
| Approach                         | Tree-based               | Centroid-based |
| Number of clusters needed first? | Not always               | Yes            |
| Output                           | Dendrogram               | Cluster labels |
| Best for                         | Small to medium datasets | Large datasets |
| Interpretability                 | High                     | Moderate       |
| Reassignment of clusters         | No                       | Yes            |

## Python Example

```python
import numpy as np
import matplotlib.pyplot as plt
from scipy.cluster.hierarchy import dendrogram, linkage
from sklearn.cluster import AgglomerativeClustering

# Sample data
X = np.array([
    [1, 2],
    [1, 4],
    [1, 0],
    [10, 2],
    [10, 4],
    [10, 0]
])

# Create dendrogram
linked = linkage(X, method='ward')

plt.figure(figsize=(8, 5))
dendrogram(linked)
plt.title("Dendrogram")
plt.xlabel("Data Points")
plt.ylabel("Distance")
plt.show()

# Apply hierarchical clustering
model = AgglomerativeClustering(n_clusters=2, metric='euclidean', linkage='ward')
labels = model.fit_predict(X)

print(labels)
```

## Interview Definition

**Hierarchical clustering is an unsupervised learning algorithm that groups data points into a tree-like structure based on similarity. It can be performed using either a bottom-up or top-down approach, and the result is often visualized using a dendrogram.**

## Short Summary

Hierarchical clustering is a clustering technique that builds a hierarchy of groups based on similarity. It is useful for understanding data structure and relationships, especially in smaller datasets.
