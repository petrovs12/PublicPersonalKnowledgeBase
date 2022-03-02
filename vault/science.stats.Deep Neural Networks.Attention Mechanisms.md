---
id: 0eavyyB1FV31znYjoX6hE
title: Attention Mechanisms
desc: ''
updated: 1646179094183
created: 1644708670411
---


# Bahnadau Attention mechanism

Let's start with training inputs $x_1,x_2,...,x_n$ as input sequence and $y_1,y_2,...,y_n$ as target sequence.

Then we will have the following model:

1. Compute $h_i = concat(h_{i,forward},h_{i,backward})$, encoding of 2 LSTM's, one ran forward and one ran backward __only on $x$- the input sequence__.
2. Initialize $s_0$ randomly
3.  Define $a_{0,j} = softmax(s_0,h_j$  for $j=1..N$.
4. Define now $c_1 = \Sum_{j=1..N}h_j*a_{0,j}$
5. Postulate $s_1 = f(s_0,y_0,c_1)$
6. Postulate $y_1 = g(y_0,s_1,c_1)$

Unroll the above in a loop, so it becomes:
1.  Define $a_{t,j} = softmax(s_{t-1},h_j$  for $j=1..N$.
2. Define now $c_t = \sum_{j=1..N}h_j*a_{t,j}$
3. Postulate $s_t = f(s_{t-1},y_{t-1},c_t)$
4. Postulate $y_t = g(y_{t-1},s_t,c_t)$


Note now after training we only use $y$ in the last 2 equations, and $y_t$ appears only on the left-hand side of the last equation.
This gives a way to generate $y$.




Simulate 'time flow' with masking.
