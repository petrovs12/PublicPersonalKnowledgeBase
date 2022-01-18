---
id: 7N29gmizh7Ks2JbsvDOdF
title: Ads Evaluation Framework
desc: ''
updated: 1642541960968
created: 1642536498536
---



Design evaluation framework for ads ranking

Source ads: given query; queries are grouped for scalability.

- Sourcing ads is like 'search' a list of ads.
- Then you have several steps of rankings.
- They all go trough same code. 
- $E[CTR]$ , other metrics -> bidding  formula.
- Positioning on page hapens in the end.

Cause you have many steps and need to return ad very fast, every step needs to be fast.

Revenue
OPS - what they make from the sale using the ad.

RoAS = OPS/Revenue

------------

LTV - lifetime value

Use short-term surrogates. Number of top purchases is correlated with LTV (Accuracy@1).

3 stakeholders:
Advertiser
Ad provider
Shopper.

For each model you have treatment, do statistical testing on the business metrics.

When you're online you know the metrics.
You need offline metrics (counterfactuals) that it correlates a lot with the online evaluation.
