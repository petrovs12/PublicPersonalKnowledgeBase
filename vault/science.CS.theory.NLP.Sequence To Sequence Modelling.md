---
id: e19xez30674v61vgdmj2wyp
title: Sequence To Sequence Modelling
desc: ''
updated: 1646177085681
created: 1646176898221
---


# RNN- Driven

The standard first approach is to consider a recurrent model w/ state h:

$h_n=f(h_{n-1},x_n)$ as the encoding engine. k

Then the __key assumption__ is that the final encoding state $h_T$ contains enough information to carry out the decoding process:

$y_t=g(h_t,y_{t-1},y_{T-2},...,y_0)$

Where $y_0$ is randomly initialized!!!

We can see it's a lot of burden on $h_T$.

[[science.stats.Deep Neural Networks.Attention Mechanisms]]



