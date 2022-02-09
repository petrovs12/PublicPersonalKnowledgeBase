---
id: R5xbIPGBS1xzJ5zvAHq2F
title: Graph Analysis
desc: ''
updated: 1644282117246
created: 1644279580217
---

# Similarity Graphs and Laplacians

Let $G= (V,E)$ be a graph and $w:E->R^{+0}$ be a weight function. Then let the degree matrix D be the diagonal matrix with $D_{i,i}=\sum_{j\in E} w(i,j)$. Let the corresponding adjacency matrix be $A_{i,j} = w_{i,j}$
Then the unnormalized Graph Laplacian is given by:

$L = D-A$

In the unweighted case, all edges have a weight of 1, and non-edges have a weight of 0.

We can show that $L$ is positive semidefinite:

# Normalized Laplacians

$I-D^{-1}W$ - random walk matrix.


# Spectral Clustering:
Let us have $n$ datapoints and some dissimilarity function on them. We would like to compute a [[science.stats.Unsupervised Learning.Clustering]] on them.
we can use __graph cuts__ on a weighted undirected similarity graph $G = ({1,2,...,n},W)$.

$cut(C_1,C_2) = \sum_{i,j\in E, i \in C_1,j\in C_2} w_{i,j}$ where $C_1,C_2$ are arbitrary (disjoint) sets of nodes.

$cut(C_1,C_2,...,C_k) = \sum_{i = 1..k} cut(C_i,\bar{C_i})$ where $\bar{C_i}$ is the complement of $C_1$.

We would like to minimize a normalized version of this cut:

$ratio-cut(C_1,C_2,...,C_k) = \sum_{i = 1..k} cut(C_i,\bar{C_i})/|C_i|$

The reason of doing this is that otherwise we might get too many splits in practice (maybe there's some theoretical reason as well)

## Approximation Via Laplacian Eigenvectors 

If we define the clusterings as normalized indicator vectors $h$ on the graph, they are orthonormal.  
They also minimize the expression $ratio-cut (C_1,...C_k) = \Sigma_{i=1..K} h_k^TLh_k$.

Were they __not__ to identity, it would correspond to computing the eigenvectors.

Which eigenvectors do we take? If the graph was disconnected, there would be multiple eigenvectors, corresponding to the eigenvalue 0.
So we take instead the $k$ eigenvectors,corresponding to the $k$ smallest eigenvalues.

This would gives us a new data representation of the graph, to which we can apply say [[science.stats.Unsupervised Learning.Clustering#^kmeans]] k-means.
