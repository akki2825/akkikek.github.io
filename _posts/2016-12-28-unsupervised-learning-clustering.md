---
title: "Unsupervised learning: Clustering"
categories: [machine-learning]
---

Unsupervised Learning is a type of Machine Learning algorithm used to predict from dataset consisting of input data without labeled responses.

Getting an algorithm to recognise clumps of data points without any help is called Clustering. 

**Types of Clustering**:

- Monothetic – Cluster members have some common property.
- Polythetic – Cluster members are similar to each other. There isn’t a single property which makes them all similar.
- Hard clustering – clusters do not overlap.  That is, each element belongs to a cluster or not.
- Soft Clustering – Clusters may overlap.
- Flat or Hierarchical Clustering.

Here are a few Algorithms used are:

**K-Means Algorithm**

It works like this: first we choose k, the number of clusters.

- Assign – We then find the center of each cluster, they are called Centroids. Choosing the initial location of the centroid affects the final clustering results.

- Optimize – We move the cluster centers to minimize total bands’ length. The web connects the centroids to the data points in that cluster. Thereby, we minimize the total length of the web for each centroid.

**Limitations of K-Means**

- k-means can only be applied when the data points lie in a Euclidean space, failing for more complex types of data.
- Even though we have fixed data points and clusters, we wont get the same result everytime.
- It is highly dependent on the initial location of the centroid, so, there are chances of us reaching the local minima. More the centroids, more the local minima there is. Hence, we are forced to run the algorithm multiple times.

**Single Linkage Clustering**

- We consider each object as a cluster (n objects).
- Define inter cluster distance between the closest two points in the two clusters.
- Merge two closest clusters.
- Repeat the same, for n-k times, to make k clusters.
- Its just connecting the dots to the nearest ones in a linear fashion.

Running time is O(n^3) or slightly lesser.

**Expectation Maximization**

- The overview of this is similar to K-means, but here, you are going to judge by probability, and you are never assigning one data point fully to one cluster or one cluster wholly to one data point.
- You instead assign each point partially to each cluster based on the probability that it would belong to the cluster if you fully knew the clusters, and then assign the mean of each cluster based on the assumption that your prior probabilities were correct, and repeat until there are no significant changes.

**Clustering Properties**


- Richness – For any assignment of object to clusters, there is some distance from matrix D such that Pd returns that clustering.

- Scale-invariance – Scaling distances by a positive value does not change the clustering.

- Consistency – Shrinking intra-cluster distances and expanding inter-cluster distances does not change the clustering.

**Impossibility Theorem**

It states that, no clustering scheme can achieve all three clustering properties.

You can find further information, [here](https://www.cs.cornell.edu/home/kleinber/nips15.pdf).
