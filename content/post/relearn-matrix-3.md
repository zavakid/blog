---
title: 投影矩阵
date: 2025-01-06T22:22:02
tags:
  - 矩阵
  - 线性代数
categories:
  - 数学
draft: false
mathjax: true
---
两个向量的夹角为： 
$$
\cos\theta = \frac{a^Tb}{\parallel{a}\parallel\parallel{b}\parallel}
$$   

两个向量正交，则内积 $a^Tb = 0$。

向量 $b$ 投影到向量 $a$，可以形象的理解成 $b$ 会按照与 $a$ 垂直的方向投射到 $a$ 上。所以 $b$ 投影到 $a$ 的结果是一个与 $a$ 方向一样的向量，我们称为 $p = \hat{x}a$，其中 $\hat{x}$ 为标量。 因此有 $(b-p) \perp a$，也就是他们的内积为 0： $a^T(b - \hat{x}a) = 0$ 。可以进一步推导出 $a^Tb - \hat{x}a^Ta = 0$ ，因此：
$$
\hat{x} = \frac{a^Tb}{a^Ta}
$$
投影结果 $p$ 就为：
$$
p = \hat{x}a = \frac{a^Tb}{a^Ta} a = a \frac{a^Tb}{a^Ta} = \frac{aa^T}{a^Ta}b
$$

换个视角，如果把投影的过程当成一个线性系统，也就是输入为 $b$，输出结果为 $p$，投影过程所代表的转换矩阵为 $P$，则： $Pb = p$ 。通过代入计算可得：

$$
P = \frac{aa^T}{a^Ta}
$$

**$P$ 就称为投影矩阵**。

如果向量的维度为 $n$， 则 $P$ 为 $n\times{n}$ 矩阵。$P$ 投影矩阵的 rank 为 1，因为上面式子揭露了矩阵是由向量 $a$ 和 $a^T$ 相乘决定的。并且 nullspace 的 basis 为 $n-1$ 个，row space 和 column space 的 basis 为 1 个，都为 $a$， left nullspace 的 basis 也为 $n-1$ 个。

**同时$P$为对称矩阵**，即： $P^T = P$。证明：
$$
P^T = \left(\frac{aa^T}{a^Ta}\right)^T = \frac{(a^T)^Ta^T}{a^Ta} = \frac{aa^T}{a^Ta} = P
$$

**同时还有 $P^2 = P$。** 在几何上很容易理解，投影之后再投影，对输入肯定是没有任何作用了。证明：

$$
P^2 = \frac{aa^T}{a^Ta}\frac{aa^T}{a^Ta} = \frac{aa^Taa^T}{a^Taa^Ta}
= \frac{a(a^Ta)a^T}{(a^Ta)a^Ta} = \frac{aa^T}{a^Ta} = P
$$

$P$ 也没有逆矩阵，因为 $P$ 是 singlar 的， rank 不为 $n$。几何上可以理解为，向量 $b$ 被投影之后，再也还原不回来了。


如果把 $a$ 当成未知的，它在一个平面，向量 $b$ 投影到该平面上的情况分析也类似。我们可以先把这个平面的 basis 形成矩，用 $A$ 表示，这样与 $b$ 垂直的向量就是 $p = A\hat{x}$ ，这样就能使用上面同样的思路， $(b-A\hat{x})A\hat{x} = 0$  ，或者使用



