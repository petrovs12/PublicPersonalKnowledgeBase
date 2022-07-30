---
id: j5ccfw6oz7ry5c5rc3gqtlf
title: Discrete Fourier Transform
desc: ''
updated: 1659207125216
created: 1659172713347
---
[Link from Cp algorithms](https://cp-algorithms.com/algebra/fft.html)

[[science.math.Functional Analysis.Functional Spaces.Bases]]


input:
Periodic function $f(x) \in R$, output: 
an infinite vector with the coefficients of $e^{i\pi(x/n)}f(x),\forall n\in N$ 

Discrete Fourier Transform:

```
Input:
set of values

then pretend there is a function:
A(i)=A[i]
and then we get the DFT of that function.
```

So effectively we get a representation of the array, pretending it's a function, by figuring out the set of coefficients in some functional space it belongs to.

Why would we do that?
:
Well, the fourier transform is an integral transform, and integral transforms often turn composition operations into pointwise multiplication operations.


That's kind of the point of the fourier transform, as if it's applied to the coefficients of 2 polynomicals, then it allows us to findthe DFT of their product as well as just a pointwise multiplication of the transforms of the 2 polynomials, and then invert...

Then the complexity of this obviously fundamental operation goes from $O(N^2$ to $O(nlog(n)))$.


# DFT

A DFT of an array is the evaluation of the polynomial w/ coefs the elements of the array:
$P(x)=a[0]+a[1]x+a[2]+a[3]x^2+...+a[n-1]x^{n-1}$

on the set of the n-th roots of unity:
$\{e^{2i\pi(x/n)}\}, x=0,1,2,...,n-1$

Obviously we can find this by solving a linear equation.


However, why DFT is quick?
Let $A$ be a polynomial, and we split it into $A_0,A_1$, such that $A_0$ is the polynomial w/ the evenly-numbered coefficients of A, and $A_!$ is the one with the oddly numbered coefficients of A.


Then:
$A(x)=x^2A_0(x)+xA_1(x)$
where $len(A_0)=len(A)/2$

then by the [[science.CS.algos.Master Theorem of Algorithmic Complexity]] the complexity of computing A would be $O(nlog(n))$

# [Inverse FFT](https://cp-algorithms.com/algebra/fft.html)
it's the same, also the Vandermonde matrix pops up here...s




