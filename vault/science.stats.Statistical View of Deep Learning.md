---
id: 0bbr30u9q0dqbx45iqxedui
title: Statistical View of Deep Learning
desc: ''
updated: 1646297391146
created: 1646297244003
---



From [S. Mohamed's review paper](http://www.cs.columbia.edu/~blei/seminar/2020-representation/readings/Mohamed2015a.pdf) we know that if we have a glm model:


$\hat{y} = \beta^T x+\alpha$
$Var(\hat{y}) = \sigma^2$
$E(y) = Link^{-1}(\hat(y))$

Where $\bf{\beta},\alpha,\sigma$ are parameters to esimate.
Link functions are listed here:[[science.stats.Regression.Loss Functions.Activation Functions]]