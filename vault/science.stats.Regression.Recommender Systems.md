---
id: VG6JMpj1Lic8br5iTSvIL
title: Recommender Systems
desc: ''
updated: 1644859769394
created: 1641997907947
---


[Rec Systems Google Drive](https://drive.google.com/open?id=0B-C_0LZtyGcNR3RMTlFVVGRKWEE&resourcekey=0-zkpm-R4LmO8XCchjdcEMHA&authuser=stefanvpetrov%40gmail.com&usp=drive_fs).

[Netflix Prize Paper On Matrix Factorications]()
[[science.math.Linear Algebra]]

[Netflix Prize Paper](https://drive.google.com/open?id=1AqarZQOZgrcYehme3JzL4pCV_IAQhn_E&authuser=stefanvpetrov%40gmail.com&usp=drive_fs)

#TODO - read and write some notes here...

# History of Recsys


```mermaid
graph LR;
a["2003 Scalable models"];
b["2005-2009 Netflix Prize - Matrx Factorization"]
c["2010-Factorization Machines(Generalized Factorizations)"]
d["2014-Deep Content Systems"]
e["2017-Deep Learning RecSys"]

a-->b-->c-->d-->e



```


## Matrix Factorization

user ratings/other signals as user/rating matrix
can handle implicit data.

[Article](https://medium.com/radon-dev/als-implicit-collaborative-filtering-5ed653ba39fe)


# Basic Model:
We would like to find a matrix $X$ such that $X$ is a low-rank matrix and $X$ is close to the user-item matrix. That is, we project both the 'users' and the 'items' into a latent space of dimension $f$. Each item is associated with a vector $\vec{q_i}\in R^f$, and each user $u$ is associated with a vector $\vec{p_u}\in R^f$. 

Then the $\hat{r}_{ui}=p_u.q_i$ is the prediction.  ^basic-model-equation

We can add also overall intercept,  user-specific intercept, and item-specific intercept, denoting 
correspondingly avg ratings across the system, and average systematic deviations from the ratings of the user or item.
thus

$\hat{r}_{u,i} = p_u.q_i+\mu+\beta_u+\beta_i$ ^basic-model-equation-with-intercepts

We're going to try to find approximate fit of the data wrt parameters.

# Software 

[Case Recommender](https://github.com/caserec/CaseRecommender) [[science.cs.languages.python]]




# Combining implicit and explicit feedback - paper review ^implicit-explicit

[Glasgow paper](https://eprints.gla.ac.uk/189873/7/189873.pdf).

* Rating (explicit data) is often used to predict *rating* of an item by user. This can be measured by
<!-- RMSE -->
* Ranking (implicit data) is often used to predict *ranking* of an items by a user
the rating prediction. Can be measured by IR (information retrieval) measures
task is usually quantified in terms of the Root Mean Square
Error [20]; while the ranking task effectiveness is measured
using Information Retrieval (IR) metrics



Main difference between implicit and explicit feedback are:
1. Implicit is dense, explicit very sparse.
2. Implicit-based models are kind of preferred.
3. Reason is ratings are very sparse
4. Generative assumption: user behavior is a 'monotonous chain of actions (e.g. browsing, clicking, watching))'. This implicit chain has explicit feedback at the end of it. But if a user stops somewhere, they maybe don't ever get the explicit feedback. So the 'tail' of the action chain might be missing, but the 'head' is there. This is why implicit feedback is preferred (I think).
5. A problem for this might be that the 'head' of the implicit feedback might be biased towards popular items, it might lack serendipity, surprise, discovery, fairness etc. ^popularity-bias-implicit


2.3 Unifying Approaches
For recommendation scenarios with both implicit and explicit interaction data, it is desirable to unify both forms of
users’ interactions in order to generate more accurate recommendations. A line of work has emerged that incorporates
both implicit feedback and explicit ratings for either ranking or rating prediction tasks. For example, ChainRec [23]
– a recent approach that we use as a baseline – represents
the sequence of implicit and explicit feedback as a monotonic behaviour chain; i.e. it is not possible to observe an explicit feedback without observing a chain of implicit feedback
beforehand. Liu et al. [9] proposed a collaborative filtering
model that can be simultaneously learned from both explicit
and implicit feedback. Zhang et al. [25] proposed a model
that learns the corresponding user and item embeddings individually for each type of feedback and integrates them to obtain a joint representation of users and items. SVD++ [5] is
another work proposed for the task of rating prediction that


considers all items for which a user made implicit feedback,
in order to learn a representation for the user. Also, previous
research [3, 7, 18] proposed training simultaneously a ranking
and a rating prediction algorithm with a shared representation for users and items in a multi-task learning framework.
Although the connection between explicit and implicit interactions has been well-studied in previous research [8, 9, 14,
15, 23], most approaches have focused on modifying the current recommendation models or have proposed a new model
that considers other feedback as auxiliary information.
The main barrier in unifying explicit and implicit feedback is that they are heterogeneous in terms of both representations and distributions. Therefore, the identification
of a single model to represent both of them simultaneously
at the level of recommendation is a challenging task. Instead, in this paper, we propose to tackle the problem of
unifying explicit and implicit feedback from a completely
different perspective. In particular, the most important aspect of our proposed approach compared to the most related
work [3, 8, 9, 23, 25] is that we tackle the problem at the level
of data pre-processing: instead of suggesting a new recommendation model/algorithm that learns from both explicit
and implicit feedback, we propose a weak supervision approach to augment the implicit feedback into the underlying
model at the lower level of data pre-processing


## Summary of model (as I understand it) ^glasgow-summary
Let $U = {u_1,u_2,...,u_m}$ iterates over users, and $I={i_1,i_2,...,i_n}$ iterates over items.

The explicit feedback dataset is $D_e=<U,I,R>$ (by obvious abuse of notation).

The ratings $R$ are numeric (or like/dislike, but quantified eventually).

The implicit feedback rating dataset is $D_i=<U,I>$, indicating that user $i$ has interacted with item $j$. 

The weakly annotated dataset $D_i^{*} =<U,I,\hat{R}>$ is something we learn from both $D_i$ and $D_e$.
Let us denote $\Phi$ a given model and $\Phi_{D_e}$ a model learned from $D_e$, while $\Phi_{D_i}^{*}$ is learned from the 'weakly annotated $\Phi_{D_{i}}^*$.

So how do we get to $D_i^{*}$ from $D_i$ and $D_e$?

Simple:

1. Input: $D_e$, $D_i$.
output: $D_i^{*}$
2. Train $\Phi_{D_e}$ in a standart way (stoch grad descent, Alternating Least Squares, etc).
3. Predict in the implicit feedback set $D_i$ using $\Phi_{D_e}$, using simple dot products, 
  getting $D_i^*$
4. Predict  on $D_i^*$, using the same model training $Phi$, getting $\Phi_{D_i}^{*}$. 
 We can think a bit how to modify these so they maybe have lower weight, maybe estimate variance etc.

 Can think of a bayesian interpretation of the above. E.g. if we know the estimated variance of the $\hat{r}$ parts of $D_{i}^*$, we could use their inverse square roots as weights. See also ![[#^basic-model-equation-weighted]] 

 This is shown by "Unifying Explicit and Implicit Feedback for Rating Prediction
and Ranking Recommendation Tasks" to improve performance on both ranking and rating prediction tasks.








# Note about Imputation ^imputation-useless

Previously imputation approaches were used for collaborative filtering (to fill ratings), but too slow.
Also, difficult problem, due to distortion, data [[science.stats.Imputation and Missing Data#^mnar]].
From "MATRIX FACTORIZATION TECHNIQUES FOR RECOMMENDER SYSTEMS" (Y)
```
Earlier systems relied on imputation to fill in missing
ratings and make the rating matrix dense. 2 However, im-
putation can be very expensive as it significantly increases
the amount of data. In addition, inaccurate imputation
might distort the data considerably. Hence, more recent
works 3-6 suggested modeling directly the observed rat-
ings only, while avoiding overfitting through a regularized
model
```
...


# SVD++ ^svdpp

[SVD++ Quora](https://www.quora.com/Whats-the-difference-between-SVD-and-SVD++?share=1)

The actual loss function to minimize includes a general bias term and two bias for both the user and the item. L2 regularization is also used to prevent overfitting. The formulation is the following:

![](/assets/images/2022-02-14-18-27-59.png)^svd-loss-image

$min_{p,q,b}\Sigma_{u,i} (r_{ui}-\mu-b_u-b_i-p_u . q_i)^2+\lambda(||p_u||^2+||q_i||^2+b_u^2+b_i^2)$ ^svd-loss2

Now, let $y_{u,i}$ are the implicit feedbacks of user $u$ and item $i$:


$min_{p,q,b}\Sigma_{u,i} (r_{ui}-\mu-b_u-b_i-p_u . q_i)^2+\lambda(||p_u||^2+||q_i||^2+b_u^2+b_i^2)$ ^svdpp-loss

[SVD++ paper by Koren](
https://github.com/gpfvic/IRR/blob/master/Factorization%20meets%20the%20neighborhood-%20a%20multifaceted%20collaborative%20filtering%20model.pdf
).

This is in the __Additional input sources_ part of the recommender-systems[netflix] paper. ^additional-input-sources

There we essentially have SVD++.

# Temporal Dynamics:

Can just make all parameters from the [[#^basic-model-equation-with-intercepts]] dynamic, and
impose some model on them, e.g. (V)AR(1):

^temporal-model-equation
$$
\hat{r}_{u,i}(t) = p_u(t).q_i(t)+\mu(t)+\beta_u(t)+\beta_i(t)\\
\vec{p(t)} = \alpha_P.\vec{p(t-1)}+\vec{\beta{p}(t)}
$$ 


Of course, can add neural nets and stuff here.

# Inputs with varying confidence levels:

Can also weight the observations somehow, as mentioned in 
$min_{q,p} c_{u,i}(\hat{r}_{ui}-p_u.q_i)^2$ ^basic-model-equation-weighted





