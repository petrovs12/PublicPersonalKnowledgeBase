
Bootstrap Aggregation:

Generate many datasets that are statistically similar to your training data, train models on them, and aggregate them together somehow.

 Intuitively, this will reduce overfitting (variance) at the cost of some bias and computation. You're forcing your model to be able to robust to reasonable changes in datasets.

 Due to this, best to use with learners with $high variance and low bias$: e.g. Decision Trees, knn, Nets.


 # Random forests are a bagging method
