---
type: digest
title: K Nearest Neighbor (kNN)
source_link: "[[D-DL4CV-Lec02-Image_Classification]]"
tags:
---
# Nearest Neighbor Classifier
## Introduction
### Training

In the training part we just memorize all data and labels

The time complexity is $O(1)$

### Predict

The algorithm find the most similar distance with the input image by computing their distance

The time complexity is $O(N)$, since we compare the input with $N$ images

> [!info] This is bad in complexity: We can afford slow training, but we need fast testing

## **Distance Metric** to compare images
### L1 (Manhattan) Distance
$$
d_{1}\left( I_{1}, I_{2} \right) = \sum_{p}\left| I_{1}^{p}-I_{2}^{p} \right| 
$$
where $p$ refers to each pixels, and $I_{1}$, $I_{2}$ refer to RGB value of the two images

### L2 (Euclidean) Distance
$$
d_{1}\left( I_{1},I_{2} \right) =\left( \sum_{p}\left( I_{1}^{p}-I_{2}^{p} \right) ^{2} \right) ^{1/2}
$$

> [!important] Right choice of distance metric can not only improve your accuracy, but also allow you to apply $K$-nearest neighbors learning algorithm to other types of data besides images

## Classification Regions

When the value of pixels in the image are in certain range, the nearest neighbor will be a particular category. We call this range the **classification region**

## Decision Boundaries

There will be boundaries between different classification regions. We called these boundaries the **decision neighbors**

![[D-DL4CV-Lec02a-kNN-decision-boundaries.png]]

---
# $K$-Nearest Neighbors
## Problem

Sometimes the outliers in the training data will make inappropriate classification regions which will cause error in classification, we need a way to get rid of outliers

## Solution

Instead of copying label from the nearest neighbor, we take the **majority vote** from $K$ closest points

However, sometimes we'll have the same vote for more than one label. In this situation, we'll use other ways to determine the label for this input

![[D-DL4CV-Lec02a-kNN-k-nearest-neighbors.png]]

---
# Universal Approximation
## Introduction

As training samples approach infinity, the data becomes arbitrarily dense in the input space. This means for any query point $x$, we can find training points arbitrarily close to it. Since the nearest neighbor simply returns function value of the closest training point, and that the closest point can be made arbitrarily close to $x$, the prediction approaches the true function value $f(x)$
## Problem: Curse of Dimensionality

As we increase the dimensions in a space, the number of data points required to maintain the same density of coverage grows exponentially

![[D-DL4CV-Lec02a-kNN-curse-of-dimensionality.png]]