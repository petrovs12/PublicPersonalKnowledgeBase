---
id: pBIMmRuN5zKHlVDIWn2wt
title: Loss Functions
desc: ''
updated: 1643151887946
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
 ```
For each user and each relevant item, compute 
the mean precision of the list __trough__ that item

 ```
* Precision at K ("p@K").
* DCG/NDCG (Normalized Discounted Gain)

^ranking-end



# Huber Loss Functions

L_{\delta }(a)={\begin{cases}{\frac  {1}{2}}{a^{2}}&{\text{for }}|a|\leq \delta ,\\\delta (|a|-{\frac  {1}{2}}\delta ),&{\text{otherwise.}}\end{cases}}
This function is quadratic for small values of a, and linear for large values, with equal values and slopes of the different sections at the two points where {\displaystyle |a|=\delta }|a|=\delta . The variable a often refers to the residuals, that is to the difference between the observed and predicted values {\displaystyle a=y-f(x)}a=y-f(x), so the former can be expanded to[2]

{\displaystyle L_{\delta }(y,f(x))={\begin{cases}{\frac {1}{2}}(y-f(x))^{2}&{\textrm {for}}|y-f(x)|\leq \delta ,\\\delta \,(|y-f(x)|-{\frac {1}{2}}\delta ),&{\textrm {otherwise.}}\end{cases}}}{\displaystyle L_{\delta }(y,f(x))={\begin{cases}{\frac {1}{2}}(y-f(x))^{2}&{\textrm {for}}|y-f(x)|\leq \delta ,\\\delta \,(|y-f(x)|-{\frac {1}{2}}\delta ),&{\textrm {otherwise.}}\end{cases}}}