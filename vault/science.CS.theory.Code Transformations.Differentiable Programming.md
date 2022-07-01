---
id: qnsew4i2mrvs1xsb4f2zktp
title: Differentiable Programming
desc: ''
updated: 1652089781023
created: 1652088752579
---


References: [Matlab site](https://www.mathworks.com/help/deeplearning/ug/deep-learning-with-automatic-differentiation-in-matlab.html).

# Automatic Differentiation


$x_1 exp(-\frac{1}{2}(x_1^2+x_2^2)).$
```mermaid
graph TB;
x1[x1] --> u1[u2=x1^2];
x2[x2] --> u2[u2=x2^2];
u2[u2] --> u3[u3=u2+u1];
u1[u1] --> u3[u3];
u3 --> u4[u4=-1/2u3];
```

# Forward Mode Differentiation

# Reverse Mode Differentiation
