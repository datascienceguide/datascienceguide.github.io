---
layout: post
title:  "Clustering"
categories: introduction 
date:   2015-02-19 21:46:04
---

Clustering

The goal of clustering is to segment the dataset into k parts (clusters) such that data points within the same cluster are similar to each other, but not similar to data points from other clusters.  The k-means algorithm is a simple and popular clustering algorithm.  As input, it requires k, the number of clusters, and a distance metric.

Say k=2, distance metric=Euclidean distance, and consider the following one-dimensional dataset: {2,4,10,12,3,20,30,11,25}.


Step 1: k-means randomly selects k records from the input dataset and assigns them to be the initial centres (means) of the clusters.  Let’s say the two randomly chosen records are 3 and 4.

Step 2: go through the dataset, and for each record, compute the distance (using the provided distance function) from the record to the two cluster means.  Assign the record to the cluster whose mean is closer to the record.  We get:

cluster 1. initial mean = 3.  Records: {2,3}
cluster 2. initial mean = 4.  Records: {4,10,12,20,30,11,25}

Step 3: recalculate the cluster means based on the records currently assigned to each cluster.  We get 2.5 for cluster 1 and 16 for cluster 2.  Go through the dataset again and repeat the above step (assign each record to the cluster whose mean is closer to the given record).  We get:

cluster 1. mean = 2.5.  Records: {2,4,3}
cluster 2. mean = 16.  Records: {10,12,20,30,11,25}

Step 4: repeat step 3.  New means: 3 for cluster 1, 18 for cluster 2.  Reassign the data points according to the new means:

cluster 1. mean = 3.  Records: {2,4,10,3}
cluster 2. mean = 18.  Records: {12,20,30,11,25}

Step 5: repeat step 4.  New means: 4.75 for cluster 1, 19.6 for cluster 2.  Reassign the data points according to the new means:

cluster 1. mean = 4.75.  Records: {2,4,10,12,3,11}
cluster 2. mean = 19.6.  Records: {20,30,25}

Step 6: repeat step 5.  New means: 7 for cluster 1, 25 for cluster 2.  Reassign the data points according to the new means:

cluster 1.  mean = 7.  Records: {2,4,10,12,3,11}
cluster 2.  mean = 25.  Records: {20,30,25}

Since the clusters have not changed, stop.  

Observations about the k-means algorithm:
- Its goal is to minimize the sum of the squares of the distances between each data point and the corresponding cluster centre.  In other words, it ensures that records placed in the same cluster are close together.
- Different choices for the initial k means can lead to a different final answer.

