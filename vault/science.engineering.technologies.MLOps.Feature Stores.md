---
id: 3coCU94D3OUfqD6I8EWoX
title: Feature Stores
desc: ''
updated: 1644626069024
created: 1644588554746
---


Tl;dr
Several perspectives:
1. Implementational
Layer on top of a db, supporting many writes, key-based retrieval, last-before-timestamp retrieval.
Supports writing batch or streaming features [[plu]].
read: can ask for a feature x for item/customer/etc id y at time t easily and get back correct result.
Handles back-filling of these features.
Can use for embedding



2. Semantic
Have an 'easy and consistent' way to write something that generates features ppl or models can use.
Then create models that take data directly from the feature store and it's easily portable to production...




Many of the points are from the [FEASTS Docs](https://docs.feast.dev/).


Feature Stores are systems that support the following functionalities: 

1. Consistent Access to Data During Model Ideation, Training, Testing, and Deploymnet
Different roles in the organization have different objectives and data sources. It would be best if the path between 'prototype data source' and 'production data sources' is as short as possible.
2. Point-in-time correctness
When the 'predict' call is made, latest allowable value of the feature is needed. Look bellow for the [[^timeTravel]]
3. Deploying new features into prod is difficult
For example, if a data scientist has created some long feature calculation pipeline during the script, it's possible to shoehorn this in production.
But maybe it's computationally burdensome, especially if it's using a bunch of time/data to compute (e.g. rolling windows). 
Then the prod system would have to make additional queries to fetch data for a week back, then aggregate over it- very slow. 
Feature store can be 'db for kids' in this sense- a database ml ppl can experiment and put scripts/ ETL's for feature calculation withouth trouble.
4. Features aren't re-used across projects/ ppl
Clear what this means





They are usually built on top of existing data stores, e.g. dynamodb, redis, BigTable, etc.
Normally the underlying storage system should support fast key lookup + timestamp range queries, e.g. BigTable style
[[engineering.system_design.nosql databases.BigTable]]

[[engineering.system_design.nosql]]


Honestly, for features it does seem like something that is key-based, supports __appends__, range queries, and one can put secondary indices on, sounds perfect.






## Time Travel Problem and Information Sets ^timeTravel

Issue:
we would like to serve a model at time $T$ for lookahead period $h$, so we would like to use the data up to and including time $T-h$. So all features we use should be 'current' as of that timestamp. 

In other words, when we're making prediction at time $T$ with planning horizon $h$, the __information set__ we can use is the one available at time $T-h$.

Some [feature store solutions can help](https://www.tecton.ai/blog/time-travel-in-ml/) with this problem.



# FEATS Overview
![](https://www.tecton.ai/blog/time-travel-in-ml/)




