---
title: 投影矩阵
date: 2025-01-06T23:21:02
tags:
  - 矩阵
  - 线性代数
categories:
  - 数学
draft: false
mathjax: true
---
### 夹角与垂直

两个向量的夹角为： 
$$
\cos\theta = \frac{a^Tb}{\parallel{a}\parallel\parallel{b}\parallel}
$$   

两个向量正交，则内积 $a^Tb = 0$。

### 向量投影到向量

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

#### 向量投影向量的矩阵是对称的

**同时$P$为对称矩阵**，即： $P^T = P$。证明：
$$
P^T = \left(\frac{aa^T}{a^Ta}\right)^T = \frac{(a^T)^Ta^T}{a^Ta} = \frac{aa^T}{a^Ta} = P
$$

#### 向量投影到向量的矩阵是幂等的

**同时还有 $P^2 = P$**。 在几何上很容易理解，投影之后再投影，对输入肯定是没有任何作用了。证明：

$$
P^2 = \frac{aa^T}{a^Ta}\frac{aa^T}{a^Ta} = \frac{aa^Taa^T}{a^Taa^Ta}
= \frac{a(a^Ta)a^T}{(a^Ta)a^Ta} = \frac{aa^T}{a^Ta} = P
$$

#### 向量投影到向量的矩阵没有逆矩阵

**$P$ 没有逆矩阵**，因为 $P$ 是 singlar 的， rank 不为 $n$。几何上可以理解为，**向量 $b$ 被投影之后，再也还原不回来了**。


### 向量投影到多维子空间

如果把 $a$ 当成未知的向量，它在一个平面上，向量 $b$ 投影到该平面上的情况分析也类似。我们可以先把这个平面的 basis 形成矩阵，用 $A$ 表示，这样与 $b$ 投影到该平面的向量就是 $a = Ax$ ，这样就能使用上面同样的思路， $(b-Ax)·Ax = 0$  ，这个是点积，有点推导不动了。

换一种思路，因为 $a$ 是由 $A$ 的 column 的线性组合，属于$A$的 column space，所以与 $a$ 垂直的向量必定是落在 $A$ 的 left nullspace 中，也就是 $(b - Ax)$ 落在 $A$ 的 left nullspace 中， 在 left nullspace 中的向量有 $y^TA = A^Ty = 0$ ，所以 $A^T(b-Ax) = 0$，再进行推导得到 $A^TAx = A^Tb$ （好像就是 $Ax=b$ 两边同时用 $A^T$ 来做转换），从而得到 $x=(A^TA)^{-1}A^Tb$ 。 

所以，向量 $b$ 投影到 $A$ 的结果就为 $Ax = A(A^TA)^{-1}A^Tb$。投影矩阵就是 $P = A(A^TA)^{-1}A^T$。

需要注意的是，上面$P$ 出现了 逆矩阵 $(A^TA)^{-1}$，而逆矩阵的出现是有条件的，即 $(A^TA)$ 需要是方阵，假设 $A$ 为 $m\times n$ 的矩阵，则 $(A^TA)$  则为 $n\times n$ 的方阵。同时也需要 $(A^TA)$ 的 rank 为 $n$ ，也就是 non-singlar 。


同时 $(A^TA)$ 的 nullspace， 也就是 $A$ 的 nullspace，证明如下：
$$\begin{align}
  &			&Ax &= 0 & A的\ nullspace\ 性质
\\&\Rightarrow   &A^T(Ax) &= 0 & 左边同时乘\ A^T
\\&\Rightarrow   &(A^TA)x &= 0 & 结合律
\end{align}$$
上面式子说明，$A$ 的 nullspace 是 $A^TA$ 的 nullspace。

接下来看：

$$\begin{align}
	&		    &(A^TA)x &= 0 &(A^TA) 的\ nullspace\ 性质 
\\&\Rightarrow  &x^T(A^TA)x &= 0 &左边同时乘 x^T
\\&\Rightarrow  &(x^TA^T)Ax &= 0 &结合律
\\&\Rightarrow  &(Ax)^TAx &= 0 &利用\ (Ax)^T = x^TA^T
\\&\Rightarrow  &\parallel Ax \parallel^2 &= 0 & 利用A^TA=\parallel A \parallel^2
\\&\Rightarrow  &\parallel Ax \parallel &= 0
\\&\Rightarrow  &Ax&= 0
\end{align}$$

上面式子说明，$(A^TA)$ 的 nullspace 是 $ax$ 的 nullspace 。
所以 **$(A^TA)$ 的 nullspace 与 $A$ 的 nullspace 等价，也就是说如果 $A$ 要有 $P$，则 $A$ 必须 full rank**。


上面得到的投影矩阵 $P$ 是一个一般化的情形，和一维向量投影的性质类似。

#### 投影矩阵是对称矩阵

**$P$ 为对称矩阵**，即 $P^T = P$，证明：
$$\begin{align}
P^T &= (A(A^TA)^{-1}A^T)^T  
\\\\  &= (A^T)^T((A^TA)^{-1})^TA^T
\\\\  &= A(((A^TA)^T)^{-1}A^T)
\\\\  &= A(A^TA)^{-1}A^T
\\\\  &= P
\end{align}$$

#### 投影矩阵是幂等矩阵

**同时也有 $P^2 = P$**。证明：

$$\begin{align}
P^2 &= PP
\\\\  &= (A(A^TA)^{-1}A^T)(A(A^TA)^{-1}A^T)
\\\\  &= A(A^TA)^{-1}((A^TA)(A^TA)^{-1})A^T
\\\\  &= A(A^TA)^{-1}A^T
\\\\  &= P
\end{align}$$

几何意义也类似，投影之后再投影，对输入肯定是没有任何作用了。


#### 投影矩阵没有逆矩阵

类似的，**$P$ 没有逆矩阵，因为向量 $b$ 被投影之后，再也还原不回来了**。


### 投影到四个子空间的矩阵

另外，**既然 $P$ 是把 $b$ 投影到 $A$ 的 column space，那么 $I-P$ 就是把 $b$ 投影到 $A$ 的 left nullspace**，证明：$b - Pb$ 落在 $A$ left nullspace 上，那么 $b - Pb = Ib - Pb = (I-P)b$，也就是说$ (I-P)$ 把 $b$ 投影到 $A$ 的 left nullspace 上。

对应的， **$P_2 = A^T(AA^T)^{-1}A$ 把 $b$ 投影到 $A$ 的 row space 上，对应的 $I-P_2$ 把 $b$ 投影到 $A$ 的 nullspace 上**。


也就是说，我们可以把向量 $b$ 投影到 $A$ 的四个子空间：

| 投影矩阵                      | 投影到A的子空间       |
| ------------------------- | -------------- |
| $P = A(A^TA)^{-1}A^T$     | column space   |
| $P = I - A(A^TA)^{-1}A^T$ | left nullspace |
| $P = A^T(AA^T)^{-1}A$     | row space      |
| $P = I - A^T(AA^T)^{-1}A$ | nullspace      |








