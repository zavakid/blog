---
title: Orthogonal 矩阵
date: 2025-01-12T18:29:00
tags:
  - 矩阵
  - 线性代数
categories:
  - 数学
draft: false
mathjax: true
---

### Orthonormal Bases

对于一个给定的空间 $R^n$，有无限多的基。 每组基都可以线性组合成该空间的向量。
在这么多组基中，最好的基，就叫做 **Orthonormal Bases**，常用 $q_1, q_2,... q_n$ 来表示。

Orthonormal Bases 有以下性质：
$$
q_i^Tq_j = 
\begin{cases}
0 & if & i \ne j & (orthogonality)  \\
1 & if &i = j    & (normalization)
\end{cases}
$$

由 Orthonormal Bases 组成的矩阵一般称为 $Q$ ，一般来说矩阵 $Q$ 都是比较高的，也就是 $Q_{m\times n}$ 中的 $m \geqslant n$  ，因为 Othonormal Bases 是互相垂直的，且是$m$ 维的向量组成的，所以 $m$ 一定要比 $n$ 大，否则就很难相互之间垂直了。

如果 $m = n$ ，则 Orthonormal Bases 形成一个方阵，这个方阵的名字叫做 **Orthogonal Matrix**。 注意 Bases 是 Orthonormal， 而 Matrix 是  Orthogonal 。



### Orthogonal Matrix 的特点

* 结合 Orthonormal Bases 的性质，**Orthogonal Matrix 的各列都是正交的，而且各列的长度为 1**
* $\bf Q^TQ = I$  ， **也就是 $\bf Q^T = Q^{-1}$** ， **同时 $\bf QQ^T = I$**
	* 这点特别重要，因为求 Orthogonal Matrix 的 $Q^{-1}$ 会变的特别简单，只要 $Q^T$ 就可以了。

第二点要证明也很简单，如下：

$$

Q^TQ = 
\begin{bmatrix}
q_1^T \\\\
q_2^T \\\\
q_3^T \\\\
\vdots
\end{bmatrix}

\begin{bmatrix}
q_1 & q_2 & q_3 & \dots
\end{bmatrix}

=

\begin{bmatrix}
1 & 0 & 0 & \dots \\\\
0 & 1 & 0 & \dots \\\\
0 & 0 & 1 & \dots \\\\
\end{bmatrix}

= I =  Q^{-1}Q

$$

$$

QQ^T =  (Q^TQ)^T = I^T = I

$$

### Orthogonal Matrix 对向量的操作

orthogonal Matrix 对向量的操作，主要就是用来 旋转、反射向量，或者是这两个操作的结合。

### Orthonormal Bases 好什么好处？

如果一个向量可以用 Orthonormal Bases  来表示，那么很容易就能找到他们的系数。 比如：
$$
b = x_1q_1 + x_2q_2 + \dots + x_nq_n
$$
只要 $q_1, q_2, \dots, q_n$ 是一组 Orthonormal Bases，那么找到 $x$ 会很简单。因为如果两边同时左乘 $q_1^T$,参考开头 $q_i^Tq_j$ 的定义， 就能进行推导：
$$\begin{align}
q_1^Tb &= x_1q_1^Tq_1 + x_2q_1^Tq_2 + \dots + x_nq_1^Tq_n \\\\
	   &= x1
\end{align}
$$

或者直接用用矩阵的方式来解决，让 $Q$ 为 Orthogonal Matrix：

$$
\begin{align}
Qx &= b \\\\
Q^{-1}Qx &= Q^{-1}b \\\\
x &= Q^{-1}b \\\\
x &= Q^Tb
\end{align}
$$

这里可以看出来，由于 $A^{-1} = A^{-T}$ ，所以求解线性方程组会变得非常简单，毕竟 $x^{-1}$ 还是有计算量的，而 $x^T$ 就很容易看出来了。

到这里可以看出来，在 Orthogonal Matrix 中，一个向量可以分别投影到各个 base 向量中，而各个 base 是垂直的。一个最简单的想象方式就是小时候经常训练的由 $(x, y)$ 组成的二维平面。 

[上一篇](https://www.foldright.com/post/relearn-matrix-3/)文章中提到的投影矩阵  $P = A(A^TA)^{-1}A^T$，如果 $A$ 为 $Q$，则 $P = Q(Q^TQ)^{-1}Q^T = QQ^T$。 注意这里的 $Q_{m\times n}$ 中的 $m$ 可能和 $n$ 不相等。如果 $m = n$，那么 $P = I$ 。

在 $Ax=b$ 的问题上，如果 $A$ 为 $Q$ ，则 $x = Q^Tb$。 


### 如何把普通的 A 转换为 Q

使用 Gram-Schmidt 方法，把相互独立的 bases，转换成相互垂直的 bases，同时使得保持所 span 成的空间不变。具体的方法这里就不展开了。









