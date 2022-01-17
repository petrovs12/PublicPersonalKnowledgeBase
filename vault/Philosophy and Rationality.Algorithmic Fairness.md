---
id: 74afJvw5CEJWFWkDS8Ri0
title: Algorithmic Fairness
desc: ''
updated: 1642426730441
created: 1642360362865
---


## Error is same across groups
Can just train algo and then test if errors same (ANOVA, t-test variations, [[science.stats.Bayesian Framework]] bayesian models, etc).

[Independence,etc](https://en.wikipedia.org/wiki/Fairness_(machine_learning)#Fairness_criteria_in_classification_problems)

# Independence
We say the random variables ${\textstyle (R,A)}$ satisfy independence if the sensitive characteristics $A$ are statistically independent to the prediction $R$, and we write $R\bot A$.

We can also express this notion with the following formula:

${P(R=r|A=a)=P(R=r|A=b)\quad \forall r\in R\quad \forall a,b\in A}$ for $R$-result, $A$ -sensitive characteristic. ^independence-formula

This means that the probability of being classified by the algorithm in each of the groups is equal for two individuals with different sensitive characteristics.
 I think this is roughly equivalent of the 'same error for all groups'.