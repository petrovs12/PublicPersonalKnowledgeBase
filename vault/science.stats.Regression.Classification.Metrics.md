---
id: C0xQGR2tHaA6spLh3IAiw
title: Metrics
desc: ''
updated: 1642433474198
created: 1641861967307
---
#FalsePositiveRate
#AUC
#ROC
#accuracy
#precision
#recall
#FPR
#TPR


# Accuracy, prediction, recall, ...


[Note From Google](https://developers.google.com/machine-learning/crash-course/classification/precision-and-recall)
true\predicted | PositivePred | NegativePredicted
---------|----------|---------
 PositiveTrue | TP | FN
 NegativeTrue | FP | TN

 $Accuracy = (TP+FP)/(FN+TN+TP+FP)$ Is simply the proportion of correct predictions.

 $Precision = TP/ (TP + FP)$ Is the proportion of correct positive predictions out of all positive __cases__.

 $TPR=Recall = (TP)/(TP+FN)$ Is the propotion of correct positive predictions out of all positive __cases__.
 TPR- true positive rate.

$FPR= FP/(FP+TN)$ Is the proportion of false positive out of all  negative __predictions__.
ROC - Receiver Operating Characteristic curve plots TPR against FPR for different thresholds.

At 0:
all predictions are negative, TP = FP = 0, hence TPR=0,FPR = 0.

At 1: all predictions are positive, TN = FN  = 0, hence TPR =1, FPR = 1.
![](/assets/images/2022-01-11-01-56-55.png)



# Likelihood/log-likelihood
## Cross-Entropy


# Multivariate


 

