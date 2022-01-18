---
id: pBIMmRuN5zKHlVDIWn2wt
title: Loss Functions
desc: ''
updated: 1642521255441
created: 1642432837032
---




# Likelyhoods and GLM


# Classification

![[science.stats.Regression.Classification.Metrics]]

# Ranking ^ranking-start

## Types ^ranking-metrics
* __Point-wise models__: which try to predict a (matching) score for each query-document pair in the dataset, and use it for ranking the items.
* __Pair-wise models__: which try to learn a __binary classifier__ that can tell which document is more relevant to a query, given pair of documents.
* __List-wise models__: which try to directly optimize the value of one of the above evaluation measures, averaged over all queries in the training data.


[Some Medium Article](https://towardsdatascience.com/20-popular-machine-learning-metrics-part-2-ranking-statistical-metrics-22c3e5a937b6) ^ranking-metrics



#TODO- learn some of these
* Mean Reciprocal Rank (MRR)
* Precision at K ("p@K").
* DCG/NDCG (Normalized Discounted Gain)
^ranking-end


