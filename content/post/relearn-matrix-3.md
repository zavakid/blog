---
title: 投影矩阵
date: 2025-01-07T22:22:02
tags:
  - 矩阵
  - 线性代数
categories:
  - 数学
draft: false
mathjax: true
---
正交向量的内积 $v^tw = 0$。
如果两个子空间正交，就意味着分别来自两个子空间中的任意两个向量是正交的。 

结合前面说的[四个子空间](https://www.foldright.com/post/relearn-matrix-2/)，矩阵为 $A_{m\times n}$ 的 row space 与 nullspace 正交，且维度互补，分别为 $r$ 和 $n-r$；column space 和 left  nullspace 正交，且维度互补，分别为 $r$ 和 $m-r$。
也就是说， 任意的向量 x，在空间 $R^n$ 中，都可以分解为 $x_{row} + x_{null}$ 。

向量 $b$ 投影到向量 $a$ 形成的向量 $p = a(a^tb/a^ta)$ 



