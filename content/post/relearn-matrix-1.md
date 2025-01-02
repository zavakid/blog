---
title: 理解矩阵 - 理解向量
date: 2024-12-29T14:19:02+08:00
tags:
  - 矩阵
  - 线性代数
categories:
  - 数学
draft: true
mathjax: true
---
线性代数的核心就是围绕着向量的两类操作：
* 加法： $v+w$ 
* 乘法：$cv + dw$ 

#### 点积(dot product) / 内积(inner product)
* 对于 $v = (v_1, v_2)$ 和 $w = (w_1, w_2)$ 来说， $v \cdot w = v_1w_1 + v_2w_2$  。 
* 点积揭示了两个向量之间夹角 $\theta$ 的情况
	* 当点积的结果为 0 时，代表两个向量是垂直的，即 $\theta = 90^\circ$ ，一个简单的记法就是类比 $(1, 0)$  和  $(0, 1)$ 。
	* 当点积结果 $> 0$ 时，夹角是锐角： $0^\circ \leqslant \theta < 90^\circ$
	* 当点积结果 $<0$ 时，夹角是钝角：$90^\circ < \theta \leqslant 180^\circ$
* 两个相同向量的点积是该向量长度的平方根（想象一下 xy 平面中如何求向量长度）
* 单位向量是长度为 1 的向量（而不是各个分量为 1 的向量）
	* 单位向量 $u$ 与另一个单位向量 $U$ 的点击为这两个向量夹角的 cosine 值，既： $u \cdot U = \cos\theta$ 






