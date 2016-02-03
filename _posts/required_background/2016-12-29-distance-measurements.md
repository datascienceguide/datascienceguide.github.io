---
layout: post
title:  "Distance Measurements"
categories: introduction 
date:   2015-02-19 21:46:04
---

Distance measurements are very important since they are used in clustering and nearest neibour algorithms.  The Scipy library has an implemention of common [distance computations](http://docs.scipy.org/doc/scipy/reference/spatial.distance.html).  The common ones are outlined below:

Better figures, formulas and examples coming soon!

## 1. Numeric Attributes

[Euclidean Distance](https://en.wikipedia.org/wiki/Euclidean_distance): ordinary straight line distance between two points.

Given two points p and q:

$$d(p,q) = d(q,p) = \sqrt{(q_1-p_1)^2+(q_2-p_2)^2 + ... + (q_n-p_n^2)}$$

Manhatten Distance: Distance a cab would drive (on a city grid)

## 2. Discrete

1 if the same, 0 if different 


## 3. Itemsets (binary attributes)
Jaccard similarity

## 4. Text data/vector angles

Cosine similarity

[Three](http://blog.christianperone.com/2011/09/machine-learning-text-feature-extraction-tf-idf-part-i/) [part](blog.christianperone.com/2011/10/machine-learning-text-feature-extraction-tf-idf-part-ii/) [tutorial](http://blog.christianperone.com/2013/09/machine-learning-cosine-similarity-for-vector-space-models-part-iii/) on the tf-idf and 
cosine similarity
