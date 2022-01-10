---
id: DbTUa6UNUw7VCjBsiE1fb
title: StrassenAlgorithm
desc: ''
updated: 1641825086332
created: 1641824649872
---
Strassen's algorithm is a divide-and-conquer algorithm for matrix multiplication.
It works by noting that the product of two matrices of size $n\times n$ can be expressed as follows:

$$ 
XY = \begin{bmatrix}
A & B \\
C & D
\end{bmatrix}*\begin{bmatrix}
E & F \\
G & H\\
\end{bmatrix}=\begin{bmatrix}
AE+BG & AF+BH \\
CE+DG & CF+DH \\
\end{bmatrix}
$$

![](/assets/images/2022-01-10-15-29-26.png)

The running time will be then:
$T(N ) = 7T(\frac{n}{2})+O(N^2)$ 
where the $O(N^2)$ part comes from the fact that we have a bunch of $N/2*N/2$ matrices to sum (in order to combine).



