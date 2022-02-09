---
id: WPtQ6p4KjbTwf5lGKgfJN
title: Convex Optimization
desc: ''
updated: 1644236555491
created: 1641835000693
---

The  [[math.Optimization.Lagrangian]] dual yields a __lower bound__ of the objective value of the optimization problem.


[[science.math.Optimization.Linear Programming]]
[[science.math.Optimization.Semidefinite Optimzation]]





Not sure what this is and why it's interesting...
[SOS tools](http://www.mit.edu/~parrilo/sostools/)


# Duality Gap

If the gap is 0, then the solution is optimal.


# A saddlepoint/ game characterization 

__The primal and dual objective values can be characterized as a game where the 'minimizing' and 'maximizing' 'players' switch their order:__

$p^* = inf_{x\in D} sup_{\lambda,\mu} L(x,(\lambda,\mu))$ : first choose x, maximize result wrt the lagrangian multipliers

$d^* = sup_{\lambda,\mu} inf_{x\in D} L(x,(\lambda,\mu))$ : first choose lagrangian multipliers, then minimize result  x

NOTE - in the notation above, the OUTSIDE optimization happens FIRST, and the INSIDE optimization happens SECOND.

Therefore weak duality corresponds to the max-min inequality:



$ sup_{\lambda,\mu} inf_{x\in D} L(x,(\lambda,\mu)) <=inf_{x\in D} sup_{\lambda,\mu} L(x,(\lambda,\mu))$, which holds for general functions, not just 
the [[math.Optimization.Lagrangian]].
That is, the 2nd player has the advantage.



# Optimiality conditions
[[science.math.Optimization.Convex Optimization.KKT Slater Complimentary Slackness]]





