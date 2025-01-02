---
title: 矩阵的四个子空间
date: 2024-12-29T14:19:02+08:00
tags:
  - 矩阵
  - 线性代数
categories:
  - 数学
draft: true
mathjax: true
---
给定一个方程式 $Ax = b$，我们需要回答几个基本问题：
* $x$ 是否**存在**解？
* 如果存在的话，解是否**唯一**？
* 需要满足什么条件，才能让方程式有解？
* 如果有解的话，如何找到所有满足方程式的解 $x$

也可以把上面这几个问题从工程的观点上进行提问：
* 如果有一个系统 $A$，我们期望它能输出 $b$，我们想知道这个系统是否具备这个能力，使得某个 input 可以变成 $b$。 或者反过来说，某个输出 $b$ 非常讨厌，我们不想让系统 $A$ 产生，$A$ 会不会有可能会输出 $b$ ？
* 如果可以，input 是唯一的吗？
* 否则，这个系统 $A$ 应该如何设计，才能让我们能够输出 $b$
* 并且通过这个系统的设计，找出所有可能的 input，让 input的生产也变得更简单些

为了回答上述问题，我们需要去了解矩阵(系统) $A$ 的特性。

### Column space

Column Space 能让我们回答一个问题，即 $Ax = b$ 是否存在解？

Column Space 就是 $A$ 中的每列向量，通过线性组合而成的空间，就是$A$ 的 Column Space，符号为 $C(A)$ ，或者叫 $R(A)$ ，也就是 Range of $A$，$A$ 的值域，很贴切。 其实 $Ax$ 描述的空间就是 $C(A)$。

而只有当 $b$ 落到 $C(A)$ 上，才有解。因为 $x$ 对每列做线性组合只能覆盖到 $C(A)$。

那如何判断 $b$ 落在了 $C(A)$ 上？如果 $b$ 是可以由 $A$ 的 pivot 所在列对应的列能够线性组合而成的话，就说明 $b$ 落在了 $C(A)$ 上。

这样就回答了 $x$ 是否有解的问题。

同时，$C(A)$ 的维度，可以通过 $A$ 的 pivot 数量来定的，也就是 Rank，所以 $A$ 的 Rank 告诉我们 $C(A)$ 的维度。另外一个需要知道的是 $A$ 的转置 $A^t$ 的维度数量，和 $A$ 是一样的。

### Nullspace

为什么要找 Nullspace？

如果我们通过 Column Space 知道了$Ax = b$ 存在解，接下来我们就要回答 $Ax = b$ 是否有唯一解。

如果 Nullspace 不只有零向量，说明 $Ax = b$ 没有唯一解。

而 Nullspace 就是看 $Ax = 0$ 的解空间。

可以这样想，如果 $x'$ 是 $Ax = b$ 的一个解，而 $y'$ 是 Nullspace 中的任意一个非零向量，那么 $Ay' = 0$。我们可以把 $Ax' = b$ 等价改写成 $A(x' + y') = 0$ ，接着根据分配率， $A(x' + 'y) = Ax' + Ay'$，而因为 $Ay' = 0$，所以 $A(x' + 'y) = Ax' + Ay' = Ax' = b$ 。

所以一旦有 $x'$，那么 $y'$ 是多少，就有多少的解。就回答了 $Ax = b$ 是否有唯一解。


接下来计算过程，给出一个矩阵$A$，求出它的 nullspace 的步骤：
1. 通过高斯消去法找到 $U$，（此是的 $U$ 就不一定叫做上三角了，因为有可能不是方针，所以现在 U 叫做 Row Echelon Form，阶梯形式）
2. 从高斯消去法得到的 $U$，可以从中找到 **Pivots** （Pivots的数量就是 rank）
3. 在 $U$ 中，包含 pivot 的列，叫做 pivot column， 不包含 pivot 的列，叫做 free column
4. 对应的，如果在方程中，pivot column 对应的变量，叫做 pivot variable，free column 对应的变量，叫做 free variable
5. 回到方程中，把 pivot variable 使用 free variable 进行代换。因为 pivot variable 太重要了，不能去动它们，我们能动的是 free variable。有点像自变量和因变量，free variable 像自变量，我们可以自由的给他们定义值，但是 pivot variable 不是我们能定的，它们像因变量，一旦 free variable 给出后，它们就定下来了
6. 由上一步得到的 free variable将原来的 $x$ 替换成 $x'$，重新写成方程 $Ax' = 0$ 的形式，就可以把 $Ax'$ 等价换成各个 free variable 的线性组合，这样的线性组合形成的空间，是 $Ax'= 0$ 的解空间。而这样的线性组合形成的空间，就是 **nullspace** 
7. Nullspace 的维度，就是 free variable 的个数。所以从 $A$ 通过高斯消去得到的 $U$ 不仅能告诉我们关于 $A$ 的 rank （pivot column个数），还能告诉我们关于 $A$ 的 nullspace 的维度（free column个数）


通过了解 Column Space 和 Nullspace ，可以回答 存在性和唯一性的问题。通过分析 Column Space，我们可以知道 $b$ 要满足什么条件会有解决，这样就回答了第三个问题。通过分析 Nullspace，我们知道了怎么样的 $x$ 是解，所以能回答第四个问题。

### Row space

$A$ 的 Row space ，就是 $A$ 的所有行(row)  span(张成) 出来的空间。换句话说，就是 $A$的转置 $A^t$ 的 Column space，也就是 $C(A^t)$ 。

### Left nullspace
对称的， $A$ 的 Left Nullspace，就是$A^t$ 的 Nullspace。
