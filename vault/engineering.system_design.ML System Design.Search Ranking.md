---
id: v4bhymavtwv0dpnzw0klwwa
title: Search Ranking
desc: ''
updated: 1646305335732
created: 1646303114356
---


# Problem Statement

General Query, return results

## Scale 

## Personalization

## Internationalization


# Metrics


## Online Metrics

### End To End Metrics
 ### User engagement
 [[seed.Product Management.Product Metrics.User Based Metrics (Digital Products)]]
 [[seed.Product Management.Product Metrics.User Based Metrics (Digital Products)#^ctr]]
 ### Query Succcess
 Dwell time, not re-doing search after short time.

 [[seed.Product Management.Product Metrics.User Based Metrics (Digital Products)#^task_success]]


 # Offline Metrics
 Classification metrics
 [[science.stats.Regression.Classification.Metrics]]
 AUC, precision, recall, etc.
 Ranking Metrics: 
 ![[science.stats.Regression.Loss Functions#^ranking-NDCG]],
 ![[science.stats.Regression.Loss Functions#^ranking-map]],


 # Architectural Components

 Draw the usual Picture - think about multiple models etc.


# Document Selection Algorithm
 We can give multiple semi-independent scores of different aspects of the user-query-document match.
 1. Intent-document match
 2. Document Pagerank
 3. Keyword Match
 4. User-Document Topic Match
 5. Location Match 

 We will have independent models, estimating all these scores, and combine them w/ some function to estimate the best score.

# ML Architectural Parts

## Query Rewriting
### Spell Checking
### Query Expansion 
Add synonyms and nearby phrases.
#### Query Relaxation
Remove redundant words (e.g. __good italian restaurants__ --> __italian restaurant__).

### Query 
## Query Understanding 

### Intent Understanding
 Embed query?
Create an 'intent' embedding for the query- 'earthquake' is 'news-y', 'food' is 'local', etc.
Can see the intent dataset by manual labelling and then proceed.

## Inverted Index Lookup


##

 














