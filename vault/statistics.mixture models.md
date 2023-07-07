---
id: h8sh9ri0514bfy8mbl6cs8h
title: Mixture Models
desc: ''
updated: 1688725795854
created: 1688723749933
---

# Mean and Variance of a Limear Combination of Random Variables

Under independence assumptions, if we have $N$ random variables $X_i$ with means $\mu_i$ and variances $\sigma_i^2$, and non-negative weights $w_i$, then the mean and variance of a linear combination of these random variables is given by:

$Y = \sum_{i=1}^N w_i X_i$

$\mu_Y = \sum_{i=1}^N w_i \mu_i$

$\sigma_Y^2 = \sum_{i=1}^N w_i \sigma_i^2$

Let's call the function that takes a list of $mu$ and $sigma$ values and a list of $w$ values and returns the mean and variance of the linear combination `linear_combination_mean_variance`.

# Mean and Variance of a Mixture of Random Variables

Under the assumptions above,
the mean and variance of a mixture of random variables, where the weights sum to 1, is given by:

$\mu_Z = \sum_{i=1}^N w_i \mu_i$

$\sigma_Z^2 = \sum_{i=1}^N w_i \sigma_i^2 + \sum_{i=1}^N w_i(\mu_i)^2- (\sum_{i=1}^N(w_i\mu_i)^2)$ 

Let's call the function that takes a list of $mu$ and $sigma$ values and a list of $w$ values and returns the mean and variance of the mixture `mixture_mean_variance`.

# Splitting a distribution into a mixture with the same mean and variance

Let the distribution have mean $\mu$ and variance $\sigma^2$.
This can be done by using the equation for the mixture in the following way:
1. Take as parameters the number of mixtures to split into $L$
2. As another parameter the target variance of each component in the mixtures $\sigma_{comp}^2$.
2. Set the target mean of the means of the mixture be the original distribution mean $\mu$. That would make the mean of the mixture equal to the mean of the original distribution.
3. Then we need same for the variance. We will achieve it by taking the variance of the means in the mixture to be:
$\sigma^2 = \sigma_{comp}^2 + \sum{} - $

 