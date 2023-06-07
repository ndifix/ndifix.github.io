---
layout: post
author: ndifix
title: "ラプラシアンの座標変換"
date: 2021-07-04 0:0:0
categories: Mathematics
---

ラプラシアンの座標変換は好きですか？私は嫌いです。\\
ググると腕力でねじ伏せてる導出ばかりが出てくるけど 自分はそれだと演算子を書くだけで30分くらいかかってしまうほど計算が遅いので何とかしたかった。\\
「行列みたいなもの」を使えばこれを解決できることに気付いたので覚書き。「行列ではないけど対称性のある式をまとめて書いた何か」だと思えば読めるはず (多分)。
<!--more-->
- [2次元極座標の場合](#R2)
- [3次元極座標の場合](#R3)
- [n次元極座標の場合](#Rn)
- [今後の課題](#task)

<a id="markdown-R2" name="R2"></a>

## 2次元極座標の場合

$$
\begin{aligned}
	x_1 &= r\cos \phi\\
	x_2 &= r\sin \phi\;\; とすると\\
	r &= \sqrt{x_1^2+x_2^2}\\
	\frac{\partial r}{\partial x_k} &= \frac{x_k}{\sqrt{x_1^2+x_2^2}}
		= \frac{x_k}{r}\\\\
	\frac{\partial x_1}{\partial x_1} &= \frac{\partial r}{\partial x_1}\cos\phi - r\frac{\partial \phi}{\partial x_1}\sin\phi\\
		&= \cos^2\phi - r\frac{\partial \phi}{\partial x_1}\sin\phi\\
	\therefore \frac{\partial \phi}{\partial x_1} &= -\frac{\sin\phi}{r}
		= -\frac{x_2}{r^2}\\\\
	\frac{\partial x_2}{\partial x_2} &= \frac{\partial r}{\partial x_2}\sin\phi + r\frac{\partial \phi}{\partial x_2}\cos\phi\\
		&= \sin^2\phi + r\frac{\partial \phi}{\partial x_2}\cos\phi\\
	\therefore \frac{\partial \phi}{\partial x_2} &= \frac{\cos\phi}{r}
		= \frac{x_1}{r^2}\\
\end{aligned}
$$

まとめると

$$
\begin{aligned}
		\left(\begin{array}{l}
			\frac{\partial}{\partial x_1}\\
			\frac{\partial}{\partial x_2}
		\end{array}\right)
	&=
		\left(\begin{array}{ll}
			\frac{\partial r}{\partial x_1} & \frac{\partial \phi}{\partial x_1}\\
			\frac{\partial r}{\partial x_2} & \frac{\partial \phi}{\partial x_2}
		\end{array}\right)
		\left(\begin{array}{l}
			\frac{\partial}{\partial r}\\
			\frac{\partial}{\partial \phi}
		\end{array}\right)\\
	&=
		\left(\begin{array}{lr}
			\cos\phi & -\frac{\sin\phi}{r}\\
			\sin\phi & \frac{\cos\phi}{r}
		\end{array}\right)
		\left(\begin{array}{l}
			\frac{\partial}{\partial r}\\
			\frac{\partial}{\partial \phi}
		\end{array}\right)\\
	&=
		\left(\begin{array}{lr}
			\frac{x_1}{r} & -\frac{x_2}{r^2}\\
			\frac{x_2}{r} & \frac{x_1}{r^2}
		\end{array}\right)
		\left(\begin{array}{l}
			\frac{\partial}{\partial r}\\
			\frac{\partial}{\partial \phi}
		\end{array}\right)\\
\end{aligned}
$$

$$
	\begin{aligned}
			\frac{\partial^2}{\partial x_1^2} + \frac{\partial^2}{\partial x_2^2}
		=&
			\left(\begin{array}{ll}
				\frac{\partial}{\partial x_1} &	\frac{\partial}{\partial x_2}
			\end{array}\right)
			\left(\begin{array}{l}
				\frac{\partial}{\partial x_1}\\
				\frac{\partial}{\partial x_2}
			\end{array}\right)\\
		=&
			\left(
				\left(\begin{array}{ll}
					\frac{\partial}{\partial x_1} &	\frac{\partial}{\partial x_2}
				\end{array}\right)
				\left(\begin{array}{lr}
					\frac{x_1}{r} & -\frac{x_2}{r^2}\\
					\frac{x_2}{r} & \frac{x_1}{r^2}
				\end{array}\right)
			\right)
			\left(\begin{array}{l}
				\frac{\partial}{\partial r}\\
				\frac{\partial}{\partial \phi}
			\end{array}\right)\\
		&+
			\left(\begin{array}{lr}
				\cos\phi & -\frac{\sin\phi}{r}\\
				\sin\phi & \frac{\cos\phi}{r}
			\end{array}\right)^T
			\left(\begin{array}{lr}
				\cos\phi & -\frac{\sin\phi}{r}\\
				\sin\phi & \frac{\cos\phi}{r}
			\end{array}\right)
			\left(\begin{array}{ll}
				\frac{\partial}{\partial r} &
				\frac{\partial}{\partial \phi}
			\end{array}\right)
			\left(\begin{array}{l}
				\frac{\partial}{\partial r}\\
				\frac{\partial}{\partial \phi}
			\end{array}\right)\\
			&\;\;\;\;\;\; ↑ 積の微分なので。\\
		=&
			\left(\begin{array}{ll}
				\frac{2}{r} - \frac{x_1^2+x_2^2}{r^3} &	0
			\end{array}\right)
			\left(\begin{array}{l}
				\frac{\partial}{\partial r}\\
				\frac{\partial}{\partial \phi}
			\end{array}\right)\\
		&+
			\left(\begin{array}{lr}
				1 & 0\\
				0 & \frac{1}{r^2}
			\end{array}\right)
			\left(\begin{array}{ll}
				\frac{\partial}{\partial r} &
				\frac{\partial}{\partial \phi}
			\end{array}\right)
			\left(\begin{array}{l}
				\frac{\partial}{\partial r}\\
				\frac{\partial}{\partial \phi}
			\end{array}\right)\\
		=&
			\frac{1}{r}\frac{\partial}{\partial r}
			+ \frac{\partial^2}{\partial r^2}
			+	\frac{1}{r^2}\frac{\partial^2}{\partial \phi^2}
	\end{aligned}
$$

<a id="markdown-R3" name="R3"></a>

## 3次元球面座標のとき
$$
\begin{aligned}
	x_1 &= r\sin\theta\cos\phi\\
	x_2 &= r\sin\theta\sin\phi\\
	x_3 &= r\cos\theta\;\; とすると\\
	r &= \sqrt{x_1^2+x_2^2+x_3^2}\\
	\frac{\partial r}{\partial x_k} &= \frac{x_k}{\sqrt{x_1^2+x_2^2+x_3^2}}
		= \frac{x_k}{r}\\
	\\\\
	\frac{\partial}{\partial x_k}(x_1^2+x_2^2) &= \frac{\partial}{\partial x_k}(r^2\sin^2\theta)\\
	2x_k &= 2r\frac{\partial r}{\partial x_k}\sin^2\theta + 2r^2\sin\theta\frac{\partial \theta}{\partial x_k}\cos\theta\\
	x_k &= x_k\sin^2\theta + r^2\sin\theta\frac{\partial \theta}{\partial x_k}\cos\theta\\
	\therefore \frac{\partial \theta}{\partial x_k} &= \frac{x_k\cos\theta}{r^2\sin\theta}
		= \frac{x_k}{r^2}\frac{x_3}{\sqrt{x_1^2+x_2^2}}\;\; ただし k=1,2\\
	\\
	\frac{\partial x_3}{\partial x_3} &= \frac{\partial r}{\partial x_3}\cos\theta - r\frac{\partial \theta}{\partial x_3}\sin\theta\\
		\therefore \frac{\partial \theta}{\partial x_3} &= -\frac{\sin\theta}{r}
			= -\frac{1}{r^2}\sqrt{x_1^2+x_2^2}\\
	\\\\
	\frac{\partial x_1}{\partial x_1}
		&= \frac{\partial r}{\partial x_1}\sin\theta\cos\phi + r\frac{\partial \theta}{\partial x_1}\cos\theta\cos\phi -r\sin\theta\frac{\partial \phi}{\partial x_1}\sin\phi\\
		&= \sin^2\theta\cos^2\phi + \cos^2\theta\cos^2\phi -r\sin\theta\frac{\partial \phi}{\partial x_1}\sin\phi\\
		&= \cos^2\phi -r\sin\theta\frac{\partial \phi}{\partial x_1}\sin\phi\\
		\therefore \frac{\partial \phi}{\partial x_1} &= -\frac{\sin\phi}{r\sin\theta}
			= -\frac{x_2}{x_1^2+x_2^2}\\
	\\
	\frac{\partial x_2}{\partial x_2}
		&= \frac{\partial r}{\partial x_2}\sin\theta\sin\phi + r\frac{\partial \theta}{\partial x_2}\cos\theta\sin\phi +r\sin\theta\frac{\partial \phi}{\partial x_2}\cos\phi\\
		&= \sin^2\theta\sin^2\phi + \cos^2\theta\sin^2\phi +r\sin\theta\frac{\partial \phi}{\partial x_1}\sin\phi\\
		&= \sin^2\phi +r\sin\theta\frac{\partial \phi}{\partial x_1}\cos\phi\\
		\therefore \frac{\partial \phi}{\partial x_2} &= \frac{\cos\phi}{r\sin\theta}
			= \frac{x_1}{x_1^2+x_2^2}\\
	\\
	\frac{\partial \phi}{\partial x_3} &=0
\end{aligned}
$$

まとめると

$$
\begin{aligned}
		\left(\begin{array}{l}
			\frac{\partial}{\partial x_1}\\
			\frac{\partial}{\partial x_2}\\
			\frac{\partial}{\partial x_3}
		\end{array}\right)
	&=
		\left(\begin{array}{lll}
			\frac{\partial r}{\partial x_1} & \frac{\partial \theta}{\partial x_1} & \frac{\partial \phi}{\partial x_1}\\
			\frac{\partial r}{\partial x_2} & \frac{\partial \theta}{\partial x_2} & \frac{\partial \phi}{\partial x_2}\\
			\frac{\partial r}{\partial x_3} & \frac{\partial \theta}{\partial x_3} & \frac{\partial \phi}{\partial x_3}\\
		\end{array}\right)
		\left(\begin{array}{l}
			\frac{\partial}{\partial r}\\
			\frac{\partial}{\partial \theta}\\
			\frac{\partial}{\partial \phi}
		\end{array}\right)\\
	&=
		\left(\begin{array}{llc}
			\sin\theta\cos\phi & \frac{\cos\theta\cos\phi}{r} & -\frac{\sin\phi}{r\sin\theta}\\
			\sin\theta\sin\phi & \frac{\cos\theta\sin\phi}{r} & \frac{\cos\phi}{r\sin\theta}\\
			\cos\theta & -\frac{\sin \theta}{r} & 0\\
		\end{array}\right)
		\left(\begin{array}{l}
			\frac{\partial}{\partial r}\\
			\frac{\partial}{\partial \theta}\\
			\frac{\partial}{\partial \phi}
		\end{array}\right)\\
	&=
		\left(\begin{array}{llc}
				\frac{x_1}{r} & \frac{x_1x_3}{r^2\sqrt{x_1^2+x_2^2}} & -\frac{x_2}{x_1^2+x_2^2}\\
				\frac{x_2}{r} & \frac{x_2x_3}{r^2\sqrt{x_1^2+x_2^2}} & \frac{x_1}{x_1^2+x_2^2}\\
				\frac{x_3}{r} & -\frac{\sqrt{x_1^2+x_2^2}}{r^2} & 0\\
		\end{array}\right)
		\left(\begin{array}{l}
			\frac{\partial}{\partial r}\\
			\frac{\partial}{\partial \theta}\\
			\frac{\partial}{\partial \phi}
		\end{array}\right)\\
\end{aligned}
$$

$$
\begin{aligned}
		\Delta
	=&
		 \left(\begin{array}{lll}
			\frac{\partial}{\partial x_1} &
			\frac{\partial}{\partial x_2} &
			\frac{\partial}{\partial x_3}
		\end{array}\right)
		\left(\begin{array}{l}
			\frac{\partial}{\partial x_1}\\
			\frac{\partial}{\partial x_2}\\
			\frac{\partial}{\partial x_3}
		\end{array}\right)\\
	=&
		\left(
			\left(\begin{array}{lll}
				\frac{\partial}{\partial x_1} &
				\frac{\partial}{\partial x_2} &
				\frac{\partial}{\partial x_3}
			\end{array}\right)
			\left(\begin{array}{llc}
				\frac{x_1}{r} & \frac{x_1x_3}{r^2\sqrt{x_1^2+x_2^2}} & -\frac{x_2}{x_1^2+x_2^2}\\
				\frac{x_2}{r} & \frac{x_2x_3}{r^2\sqrt{x_1^2+x_2^2}} & \frac{x_1}{x_1^2+x_2^2}\\
				\frac{x_3}{r} & -\frac{\sqrt{x_1^2+x_2^2}}{r^2} & 0\\
			\end{array}\right)
		\right)
		\left(\begin{array}{l}
			\frac{\partial}{\partial r}\\
			\frac{\partial}{\partial \theta}\\
			\frac{\partial}{\partial \phi}
		\end{array}\right)\\
	&+
		\left(\begin{array}{llc}
			\sin\theta\cos\phi & \frac{\cos\theta\cos\phi}{r} & -\frac{\sin\phi}{r\sin\theta}\\
			\sin\theta\sin\phi & \frac{\cos\theta\sin\phi}{r} & \frac{\cos\phi}{r\sin\theta}\\
			\cos\theta & -\frac{\sin \theta}{r} & 0\\
		\end{array}\right)^T
		\left(\begin{array}{llc}
			\sin\theta\cos\phi & \frac{\cos\theta\cos\phi}{r} & -\frac{\sin\phi}{r\sin\theta}\\
			\sin\theta\sin\phi & \frac{\cos\theta\sin\phi}{r} & \frac{\cos\phi}{r\sin\theta}\\
			\cos\theta & -\frac{\sin \theta}{r} & 0\\
		\end{array}\right)
		\left(\begin{array}{lll}
			\frac{\partial}{\partial r} &
			\frac{\partial}{\partial \theta} &
			\frac{\partial}{\partial \phi}
		\end{array}\right)
		\left(\begin{array}{l}
			\frac{\partial}{\partial r}\\
			\frac{\partial}{\partial \theta}\\
			\frac{\partial}{\partial \phi}
		\end{array}\right)\\
	=&
		\left(\begin{array}{lll}
			\frac{2}{r} &
			\frac{\cos\theta}{r^2\sin\theta} &
			0
		\end{array}\right)
		\left(\begin{array}{l}
			\frac{\partial}{\partial r}\\
			\frac{\partial}{\partial \theta}\\
			\frac{\partial}{\partial \phi}
		\end{array}\right)\\
	&+
		\left(\begin{array}{ccc}
			1 & 0 & 0\\
			0 & \frac{1}{r^2} & 0 \\
			0	& 0 & \frac{1}{r^2\sin^2\theta}\\
		\end{array}\right)
		\left(\begin{array}{lll}
			\frac{\partial}{\partial r} &
			\frac{\partial}{\partial \theta} &
			\frac{\partial}{\partial \phi}
		\end{array}\right)
		\left(\begin{array}{l}
			\frac{\partial}{\partial r}\\
			\frac{\partial}{\partial \theta}\\
			\frac{\partial}{\partial \phi}
		\end{array}\right)\\
	=&
		\frac{2}{r}\frac{\partial}{\partial r}
		+\frac{\cos\theta}{r^2\sin\theta}\frac{\partial}{\partial \theta}
		+\frac{\partial^2}{\partial r^2}
		+\frac{1}{r^2}\frac{\partial^2}{\partial \theta^2}
		+\frac{1}{r^2\sin^2\theta}\frac{\partial^2}{\partial \phi^2}
\end{aligned}
$$

せっかくなので一般化しておきます。
<a id="markdown-Rn" name="Rn"></a>

## n次元球面座標のとき
$$
\begin{aligned}
	x_1 &= r\cos\theta_1\\
	x_2 &= r\sin\theta_1\cos\theta_2\\
		&\vdots\\
	x_k &= r\prod_{i=1}^{k-1}\sin\theta_i\cos\theta_{k}\\
	x_{n-1} &= r\prod_{i=1}^{n-2}\sin\theta_i\cos\theta_{n-1}\\
	x_n &= r\prod_{i=1}^{n-2}\sin\theta_i\sin\theta_{n-1}\\
	r_k &= \sqrt{\sum_{i=k}^n x_i^2} \;\; とする。\\
	このとき\\
	x_1 &= r_1\cos\theta_1\\
	x_2 &= r_2\cos\theta_2\\
		&\vdots\\
	x_k &= r_k\cos\theta_{k}\\
	x_{n-1} &= r_{n-1}\cos\theta_{n-1}\\
	x_n &= r_{n-1}\sin\theta_{n-1}\\
	r_k &= r\prod_{i=1}^{k-1} \sin\theta_i \;\;(1\leq k<n)\\
	であり\\
	\frac{\partial r_i}{\partial x_j}
		&=
		\begin{cases}
			x_j/r_i\;\; (i\leq j)\\
			0\;\;\;\;\;\;\;\; (i>j)
		\end{cases}\\
	\\\\
	i<n のとき\\
	\frac{\partial x_i}{\partial x_j}
		&= \frac{\partial r_i}{\partial x_j}\cos\theta_i - r_i\frac{\partial \theta_i}{\partial x_j}\sin\theta_i\\
	i<n かつ i<j のとき\\
	0	&= \frac{x_j}{r_i}\cos\theta_i - r_i\frac{\partial \theta_i}{\partial x_j}\sin\theta_i\\
	\frac{\partial \theta_i}{\partial x_j}
		&= \frac{x_j\cos\theta_i}{r_i^2\sin\theta_i}\\
	i<n かつ i=j のとき\\
	1 &= \frac{x_j}{r_i}\cos\theta_i - r_i\frac{\partial \theta_i}{\partial x_j}\sin\theta_i\\
		%&= \frac{x_i}{r_i}\cos\theta_i - r_i\frac{\partial \theta_i}{\partial x_i}\sin\theta_i\\
		&= \cos\theta^2_i - r_i\frac{\partial \theta_i}{\partial x_i}\sin\theta_i\\
	\frac{\partial \theta_i}{\partial x_j} &= -\frac{\sin\theta_i}{r_i}\\
	i<n かつ i>j のとき\\
	0	&= 0\cdot \cos\theta_i - r_i\frac{\partial \theta_i}{\partial x_j}\sin\theta_i\\
	\frac{\partial \theta_i}{\partial x_j} &= 0\\
	\\
	j<i=n のとき\\
	\frac{\partial x_i}{\partial x_j}
		&= \frac{\partial r_{n-1}}{\partial x_j}\sin\theta_{n-1} + r_{n-1}\frac{\partial \theta_{n-1}}{\partial x_j}\cos\theta_{n-1}\\
	0 &= \delta_{j,n-1}\cdot \sin^2\theta_{n-1} + r_{n-1}\frac{\partial \theta_{n-1}}{\partial x_j}\cos\theta_{n-1}\\
	\frac{\partial \theta_{n-1}}{\partial x_j} &= -\frac{\sin\theta_{n-1}}{r_{n-1}} \delta_{j,n-1}\\
	j=i=n のとき\\
	\frac{\partial x_i}{\partial x_j}
		&= \frac{\partial r_{n-1}}{\partial x_{n-1}}\sin\theta_{n-1} + r_{n-1}\frac{\partial \theta_{n-1}}{\partial x_{n-1}}\cos\theta_{n-1}\\
	1 &= \sin\theta^2_{n-1} + r_{n-1}\frac{\partial \theta_{n-1}}{\partial x_{n-1}}\cos\theta_{n-1}\\
	\frac{\partial \theta_{n-1}}{\partial x_n} &= \frac{\cos\theta_{n-1}}{r_{n-1}}
\end{aligned}
$$

$$
よって\\
\begin{aligned}
		\left(\begin{array}{c}
			\frac{\partial}{\partial x_1}\\
			\frac{\partial}{\partial x_2}\\
			\frac{\partial}{\partial x_3}\\
			\vdots\\
			\frac{\partial}{\partial x_n}\\
		\end{array}\right)
	=&
		\left(\begin{array}{clllc}
			\frac{\partial r}{\partial x_1} & \frac{\partial \theta_1}{\partial x_1} & \frac{\partial \theta_2}{\partial x_1} & \cdots & \frac{\partial \theta_{n-1}}{\partial x_1}\\
			\frac{\partial r}{\partial x_2} & \frac{\partial \theta_1}{\partial x_2} & \frac{\partial \theta_2}{\partial x_2} & \cdots & \frac{\partial \theta_{n-1}}{\partial x_2}\\
			\vdots & & & \ddots & \vdots\\
			\frac{\partial r}{\partial x_{n-1}} & \frac{\partial \theta_1}{\partial x_{n-1}} & \frac{\partial \theta_2}{\partial x_{n-1}} & \cdots & \frac{\partial \theta_{n-1}}{\partial x_{n-1}}\\
			\frac{\partial r}{\partial x_n} & \frac{\partial \theta_1}{\partial x_n} & \frac{\partial \theta_2}{\partial x_n} & \cdots & \frac{\partial \theta_{n-1}}{\partial x_n}\\
		\end{array}\right)
		\left(\begin{array}{c}
			\frac{\partial}{\partial r}\\
			\frac{\partial}{\partial \theta_1}\\
			\frac{\partial}{\partial \theta_2}\\
			\vdots\\
			\frac{\partial}{\partial \theta_{n-1}}\\
		\end{array}\right)\\
	=&
		\left(\begin{array}{cccccc}
			\frac{x_1}{r_1} & -\frac{\sin\theta_1}{r_1} & 0 &\cdots & 0 & 0\\
			\frac{x_2}{r_1} & \frac{x_2\cos\theta_1}{r_1^2\sin\theta_1} & -\frac{\sin\theta_2}{r_2} & \cdots & 0 & 0\\
			\vdots & & & \ddots & & \vdots\\
			\frac{x_{n-1}}{r_1} & \frac{x_{n-1}\cos\theta_1}{r_1^2\sin\theta_1} & \frac{x_{n-1}\cos\theta_2}{r_2^2\sin\theta_2} & \cdots & \frac{x_{n-1}\cos\theta_{n-2}}{r_{n-2}^2\sin\theta_{n-2}} & -\frac{\sin\theta_{n-1}}{r_{n-1}}\\
			\frac{x_n}{r_1} & \frac{x_n\cos\theta_1}{r_1^2\sin\theta_1} & \frac{x_n\cos\theta_2}{r_2^2\sin\theta_2} & \cdots & \frac{x_n\cos\theta_{n-2}}{r_{n-2}^2\sin\theta_{n-2}} & \frac{\cos\theta{n-1}}{r_{n-1}}\\
		\end{array}\right)
		\left(\begin{array}{c}
			\frac{\partial}{\partial r}\\
			\frac{\partial}{\partial \theta_1}\\
			\frac{\partial}{\partial \theta_2}\\
			\vdots\\
			\frac{\partial}{\partial \theta_{n-1}}\\
		\end{array}\right)\\
\end{aligned}
$$

$$
\begin{aligned}
		\Delta_n
	=&
		\left(\begin{array}{lll}
			\frac{\partial}{\partial x_1} &
			\cdots &
			\frac{\partial}{\partial x_n}
		\end{array}\right)
		\left(\begin{array}{l}
			\frac{\partial}{\partial x_1}\\
			\vdots\\
			\frac{\partial}{\partial x_n}
		\end{array}\right)\\
	=&
		\left(
			\left(\begin{array}{lll}
				\frac{\partial}{\partial x_1} &
				\cdots &
				\frac{\partial}{\partial x_n}
			\end{array}\right)
			\left(\begin{array}{ccccc}
			\frac{x_1}{r_1} & -\frac{\sin\theta_1}{r_1}  &\cdots & 0 & 0\\
			\frac{x_2}{r_1} & \frac{x_2\cos\theta_1}{r_1^2\sin\theta_1}  & \cdots & 0 & 0\\
			\vdots & \vdots & \ddots & \vdots & \vdots\\
			\frac{x_{n-1}}{r_1} & \frac{x_{n-1}\cos\theta_1}{r_1^2\sin\theta_1} & \cdots & \frac{x_{n-1}\cos\theta_{n-2}}{r_{n-2}^2\sin\theta_{n-2}} & -\frac{\sin\theta_{n-1}}{r_{n-1}}\\
			\frac{x_n}{r_1} & \frac{x_n\cos\theta_1}{r_1^2\sin\theta_1} & \cdots & \frac{x_n\cos\theta_{n-2}}{r_{n-2}^2\sin\theta_{n-2}} & \frac{\cos\theta{n-1}}{r_{n-1}}\\
		\end{array}\right)
		\right)
		\left(\begin{array}{c}
			\frac{\partial}{\partial r}\\
			\frac{\partial}{\partial \theta_1}\\
			\vdots\\
			\frac{\partial}{\partial \theta_{n-1}}\\
		\end{array}\right)\\
	&+
		\left(\begin{array}{ccccc}
			\frac{x_1}{r_1} & -\frac{\sin\theta_1}{r_1}  &\cdots & 0 & 0\\
			\frac{x_2}{r_1} & \frac{x_2\cos\theta_1}{r_1^2\sin\theta_1}  & \cdots & 0 & 0\\
			\vdots & \vdots & \ddots & \vdots & \vdots\\
			\frac{x_{n-1}}{r_1} & \frac{x_{n-1}\cos\theta_1}{r_1^2\sin\theta_1} & \cdots & \frac{x_{n-1}\cos\theta_{n-2}}{r_{n-2}^2\sin\theta_{n-2}} & -\frac{\sin\theta_{n-1}}{r_{n-1}}\\
			\frac{x_n}{r_1} & \frac{x_n\cos\theta_1}{r_1^2\sin\theta_1} & \cdots & \frac{x_n\cos\theta_{n-2}}{r_{n-2}^2\sin\theta_{n-2}} & \frac{\cos\theta{n-1}}{r_{n-1}}\\
		\end{array}\right)^T
		\left(\begin{array}{ccccc}
			\frac{x_1}{r_1} & -\frac{\sin\theta_1}{r_1}  &\cdots & 0 & 0\\
			\frac{x_2}{r_1} & \frac{x_2\cos\theta_1}{r_1^2\sin\theta_1}  & \cdots & 0 & 0\\
			\vdots & \vdots & \ddots & \vdots & \vdots\\
			\frac{x_{n-1}}{r_1} & \frac{x_{n-1}\cos\theta_1}{r_1^2\sin\theta_1} & \cdots & \frac{x_{n-1}\cos\theta_{n-2}}{r_{n-2}^2\sin\theta_{n-2}} & -\frac{\sin\theta_{n-1}}{r_{n-1}}\\
			\frac{x_n}{r_1} & \frac{x_n\cos\theta_1}{r_1^2\sin\theta_1} & \cdots & \frac{x_n\cos\theta_{n-2}}{r_{n-2}^2\sin\theta_{n-2}} & \frac{\cos\theta{n-1}}{r_{n-1}}\\
		\end{array}\right)
		\left(\begin{array}{lll}
			\frac{\partial}{\partial r} &
			\cdots &
			\frac{\partial}{\partial \theta_{n-1}}
		\end{array}\right)
		\left(\begin{array}{c}
			\frac{\partial}{\partial r}\\
			\vdots\\
			\frac{\partial}{\partial \theta_{n-1}}\\
		\end{array}\right)\\
	=&
		\left(\begin{array}{c}
			\frac{n-1}{r_1}\\
			-\frac{\partial}{\partial x_1} \frac{\sin\theta_1}{r_1} + \sum_{i=2}^n \frac{\partial}{\partial x_i}\frac{x_i\cos\theta_1}{r_1^2\sin\theta_1}\\
			\vdots\\
			-\frac{\partial}{\partial x_k} \frac{\sin\theta_k}{r_k} + \sum_{i=k+1}^n \frac{\partial}{\partial x_i}\frac{x_i\cos\theta_k}{r_k^2\sin\theta_k}\\
			\vdots\\
			-\frac{\partial}{\partial x_{n-1}}\frac{\sin\theta_{n-1}}{r_{n-1}} + \sum_{i=n}^n \frac{\partial}{\partial x_i}\frac{x_i\cos\theta_{n-1}}{r_{n-1}^2\sin\theta_{n-1}}\\
		\end{array}\right)^T
		\left(\begin{array}{c}
			\frac{\partial}{\partial r}\\
			\vdots\\
			\frac{\partial}{\partial \theta_k}\\
			\vdots\\
			\frac{\partial}{\partial \theta_{n-1}}\\
		\end{array}\right)\\
	&+
		\left(\begin{array}{cccc}
			\frac{x_1}{r_1} & \frac{x_2}{r_1} &\cdots & \frac{x_n}{r_1}\\
			-\frac{\sin\theta_1}{r_1} & \frac{x_2\cos\theta_1}{r_1^2\sin\theta_1} &\cdots & \frac{x_n\cos\theta_1}{r_1^2\sin\theta_1}\\
			\vdots & \vdots & \ddots & \vdots\\
			0 & 0 & \cdots  & \frac{x_n\cos\theta_{n-2}}{r_{n-2}^2\sin\theta_{n-2}}\\
			0 & 0 & \cdots & \frac{\cos\theta_{n-1}}{r_{n-1}}\\
		\end{array}\right)
		\left(\begin{array}{ccccc}
			\frac{x_1}{r_1} & -\frac{\sin\theta_1}{r_1}  &\cdots & 0 & 0\\
			\frac{x_2}{r_1} & \frac{x_2\cos\theta_1}{r_1^2\sin\theta_1}  & \cdots & 0 & 0\\
			\vdots & \vdots & \ddots & \vdots & \vdots\\
			\frac{x_{n-1}}{r_1} & \frac{x_{n-1}\cos\theta_1}{r_1^2\sin\theta_1} & \cdots & \frac{x_{n-1}\cos\theta_{n-2}}{r_{n-2}^2\sin\theta_{n-2}} & -\frac{\sin\theta_{n-1}}{r_{n-1}}\\
			\frac{x_n}{r_1} & \frac{x_n\cos\theta_1}{r_1^2\sin\theta_1} & \cdots & \frac{x_n\cos\theta_{n-2}}{r_{n-2}^2\sin\theta_{n-2}} & \frac{\cos\theta{n-1}}{r_{n-1}}\\
		\end{array}\right)
		\left(\begin{array}{lll}
			\frac{\partial}{\partial r} &
			\cdots &
			\frac{\partial}{\partial \theta_{n-1}}
		\end{array}\right)
		\left(\begin{array}{c}
			\frac{\partial}{\partial r}\\
			\vdots\\
			\frac{\partial}{\partial \theta_{n-1}}\\
		\end{array}\right)\\
	=&
		\left(\begin{array}{c}
			\frac{n-1}{r_1}\\
			\vdots\\
			2\frac{\sin\theta_k\cos\theta_k}{r_k^2} + \sum_{i=k+1}^n \frac{1}{r_k^2\tan\theta_k}\left(1-2\frac{x_i^2}{r_k^2}-\frac{x_i^2}{r_k^2\sin^2\theta_k}\right)\\
			\vdots\\
		\end{array}\right)^T
		\left(\begin{array}{c}
			\frac{\partial}{\partial r}\\
			\vdots\\
			\frac{\partial}{\partial \theta_k}\\
			\vdots\\
		\end{array}\right)\\
	&+
		\left(\begin{array}{ccccc}
			1 & -\frac{x_1}{r_1}\frac{\sin\theta_1}{r_1}+\sum_{i=2}^n \frac{x_i}{r_1}\frac{x_i\cos\theta_1}{r_1^2\sin\theta_1} & \cdots & -\frac{x_{n-2}}{r_1}\frac{\sin\theta_{n-2}}{r_{n-2}}+ \sum_{i=n-1}^n\frac{x_i}{r_1}\frac{x_i\cos\theta_{n-2}}{r_{n-2}^2\sin\theta_{n-2}} & -\frac{x_{n-1}}{r_1}\frac{\sin\theta_{n-1}}{r_{n-1}}+ \sum_{i=n}^n\frac{x_i}{r_1}\frac{x_i\cos\theta_{n-1}}{r_{n-1}^2\sin\theta_{n-1}}\\
			* & \frac{\sin^2\theta_1}{r_1^2} + \sum_{i=2}^n \frac{x_i^2\cos^2\theta_1}{r_1^4\sin^2\theta_1} & \cdots  & -\frac{x_{n-2}\cos\theta_1}{r_1^2\sin\theta_1}\frac{\sin\theta_{n-2}}{r_{n-2}}+\sum_{i=n-1}^n\frac{x_i\cos\theta_1}{r_1^2\sin\theta_1}\frac{x_i\cos\theta_{n-2}}{r_{n-2}^2\sin\theta_{n-2}} & -\frac{x_{n-1}\cos\theta_1}{r_1^2\sin\theta_1}\frac{\sin\theta_{n-1}}{r_{n-1}}+ \sum_{i=n}^n\frac{x_i\cos\theta_1}{r_1^2\sin\theta_1}\frac{x_i\cos\theta_{n-1}}{r_{n-1}^2\sin\theta_{n-1}}\\
			\vdots & \vdots & \ddots & \vdots &\vdots\\
			* & * & \cdots & \frac{\sin^2\theta_{n-2}}{r_{n-2}^2}+\sum_{i=n-1}^n \frac{x_i^2\cos^2\theta_{n-2}}{r_{n-2}^4\sin^2\theta_{n-2}} & -\frac{x_{n-1}\cos\theta_{n-2}}{r_{n-2}^2\sin\theta_{n-2}}\frac{\sin\theta_{n-1}}{r_{n-1}}+ \sum_{i=n}^n\frac{x_i\cos\theta_{n-2}}{r_{n-2}^2\sin\theta_{n-2}}\frac{x_i\cos\theta_{n-1}}{r_{n-1}^2\sin\theta_{n-1}}\\
			* & * & \cdots & * & \frac{\sin^2\theta_{n-1}}{r_{n-1}^2}+\sum_{i=n}^n \frac{x_i^2\cos^2\theta_{n-1}}{r_{n-1}^4\sin^2\theta_{n-1}}\\
		\end{array}\right)
		\left(\begin{array}{lll}
			\frac{\partial}{\partial r} &
			\cdots &
			\frac{\partial}{\partial \theta_{n-1}}
		\end{array}\right)
		\left(\begin{array}{c}
			\frac{\partial}{\partial r}\\
			\vdots\\
			\frac{\partial}{\partial \theta_{n-1}}\\
		\end{array}\right)\\
	=&
		\left(\begin{array}{c}
			\frac{n-1}{r_1}\\
			\vdots\\
			2\frac{\sin\theta_k\cos\theta_k}{r_k^2} + \frac{1}{r_k^2\tan\theta_k}\left((n-k)-2\frac{r_{k+1}^2}{r_k^2}-\frac{r_{k+1}^2}{r_k^2\sin^2\theta_k}\right)\\
			\vdots\\
		\end{array}\right)^T
		\left(\begin{array}{c}
			\frac{\partial}{\partial r}\\
			\vdots\\
			\frac{\partial}{\partial \theta_k}\\
			\vdots\\
		\end{array}\right)\\
	&+
		\left(\begin{array}{ccccc}
			1 & -\frac{1}{r_1}\frac{x_1\sin\theta_1}{r_1}+ \frac{1}{r_1}\frac{r_2^2\cos\theta_1}{r_1^2\sin\theta_1} & \cdots & -\frac{1}{r_1}\frac{x_{n-2}\sin\theta_{n-2}}{r_{n-2}}+ \frac{1}{r_1}\frac{r_{n-1}^2\cos\theta_{n-2}}{r_{n-2}^2\sin\theta_{n-2}} & -\frac{1}{r_1}\frac{x_{n-1}\sin\theta_{n-1}}{r_{n-1}}+ \frac{1}{r_1}\frac{r_{n}^2\cos\theta_{n-1}}{r_{n-1}^2\sin\theta_{n-1}} \\
			* & \frac{\sin^2\theta_1}{r_1^2} + \frac{r_2^2\cos^2\theta_1}{r_1^4\sin^2\theta_1} & \cdots  & -\frac{\cos\theta_1}{r_1^2\sin\theta_1}\frac{x_{n-2}\sin\theta_{n-2}}{r_{n-2}}+ \frac{\cos\theta_1}{r_1^2\sin\theta_1}\frac{r_{n-1}^2\cos\theta_{n-2}}{r_{n-2}^2\sin\theta_{n-2}} & -\frac{\cos\theta_1}{r_1^2\sin\theta_1}\frac{x_{n-1}\sin\theta_{n-1}}{r_{n-1}}+\frac{\cos\theta_1}{r_1^2\sin\theta_1}\frac{r_{n}^2\cos\theta_{n-1}}{r_{n-1}^2\sin\theta_{n-1}}\\
			* & * & \cdots & -\frac{\cos\theta_2}{r_2^2\sin\theta_2}\frac{x_{n-2}\sin\theta_{n-2}}{r_{n-2}}+ \frac{\cos\theta_2}{r_2^2\sin\theta_2}\frac{r_{n-1}^2\cos\theta_{n-2}}{r_{n-2}^2\sin\theta_{n-2}} & -\frac{\cos\theta_1}{r_1^2\sin\theta_1}\frac{x_{n-1}\sin\theta_{n-1}}{r_{n-1}}+\frac{\cos\theta_1}{r_1^2\sin\theta_1}\frac{r_{n}^2\cos\theta_{n-1}}{r_{n-1}^2\sin\theta_{n-1}}\\
			\vdots & \vdots & \ddots & \vdots &\vdots\\
			* & * & \cdots & \frac{\sin^2\theta_{n-2}}{r_{n-2}^2}+ \frac{r_{n-1}^2\cos^2\theta_{n-2}}{r_{n-2}^4\sin^2\theta_{n-2}} & -\frac{\cos\theta_{n-2}}{r_{n-2}^2\sin\theta_{n-2}}\frac{x_{n-1}\sin\theta_{n-1}}{r_{n-1}} +\frac{\cos\theta_{n-2}}{r_{n-2}^2\sin\theta_{n-2}}\frac{r_{n}^2\cos\theta_{n-1}}{r_{n-1}^2\sin\theta_{n-1}}\\
			* & * & \cdots & * & \frac{\sin^2\theta_{n-1}}{r_{n-1}^2}+ \frac{r_{n}^2\cos^2\theta_{n-1}}{r_{n-1}^4\sin^2\theta_{n-1}}\\
		\end{array}\right)
		\left(\begin{array}{lll}
			\frac{\partial}{\partial r} &
			\cdots &
			\frac{\partial}{
				\partial \theta_{n-1}}
		\end{array}\right)
		\left(\begin{array}{c}
			\frac{\partial}{\partial r}\\
			\vdots\\
			\frac{\partial}{\partial \theta_{n-1}}\\
		\end{array}\right)\\
	=&
		\left(\begin{array}{c}
			\frac{n-1}{r_1}\\
			\vdots\\
			2\frac{\sin\theta_k\cos\theta_k}{r_k^2} + \frac{1}{r_k^2\tan\theta_k}\left((n-k)-2\sin^2\theta_k-1\right)\\
			\vdots\\
		\end{array}\right)^T
		\left(\begin{array}{c}
			\frac{\partial}{\partial r}\\
			\vdots\\
			\frac{\partial}{\partial \theta_k}\\
			\vdots\\
		\end{array}\right)\\
	&+
		\left(\begin{array}{ccccc}
			1 & -\frac{1}{r_1}\cos\theta_1\sin\theta_1+ \frac{1}{r_1}\cos\theta_1\sin\theta_1 & \cdots & -\frac{1}{r_1}\cos\theta_{n-2}\sin\theta_{n-2} +\frac{1}{r_1}\cos\theta_{n-2}\sin\theta_{n-2} & -\frac{1}{r_1}\cos\theta_{n-1}\sin\theta_{n-1}+\frac{1}{r_1}\cos\theta_{n-1}\sin\theta_{n-1} \\
			* & \frac{\sin^2\theta_1}{r_1^2} + \frac{\cos^2\theta_1}{r_1^2} & \cdots  & -\frac{\cos\theta_1}{r_1^2\sin\theta_1} \cos\theta_{n-2}\sin\theta_{n-2}+ \frac{\cos\theta_1}{r_1^2\sin\theta_1}\cos\theta_{n-2}\sin\theta_{n-2} & -\frac{\cos\theta_1}{r_1^2\sin\theta_1} \cos\theta_{n-1}\sin\theta_{n-1}+ \frac{\cos\theta_1}{r_1^2\sin\theta_1}\cos\theta_{n-1}\sin\theta_{n-1}\\
			* & * & \cdots & -\frac{\cos\theta_2}{r_2^2\sin\theta_2} \cos\theta_{n-2}\sin\theta_{n-2}+ \frac{\cos\theta_2}{r_2^2\sin\theta_2}\cos\theta_{n-2}\sin\theta_{n-2} & -\frac{\cos\theta_2}{r_2^2\sin\theta_2} \cos\theta_{n-1}\sin\theta_{n-1}+ \frac{\cos\theta_2}{r_2^2\sin\theta_2}\cos\theta_{n-1}\sin\theta_{n-1}\\
			\vdots & \vdots & \ddots & \vdots &\vdots\\
			* & * & \cdots & \frac{\sin^2\theta_{n-2}}{r_{n-2}^2}+ \frac{\cos^2\theta_{n-2}}{r_{n-2}^2} & -\frac{\cos\theta_{n-2}}{r_{n-2}^2\sin\theta_{n-2}} \cos\theta_{n-1}\sin\theta_{n-1}+ \frac{\cos\theta_{n-2}}{r_{n-2}^2\sin\theta_{n-2}}\cos\theta_{n-1}\sin\theta_{n-1}\\
			* & * & \cdots & * & \frac{\sin^2\theta_{n-1}}{r_{n-1}^2}+ \frac{\cos^2\theta_{n-1}}{r_{n-1}^2}\\
		\end{array}\right)
		\left(\begin{array}{lll}
			\frac{\partial}{\partial r} &
			\cdots &
			\frac{\partial}{
				\partial \theta_{n-1}}
		\end{array}\right)
		\left(\begin{array}{c}
			\frac{\partial}{\partial r}\\
			\vdots\\
			\frac{\partial}{\partial \theta_{n-1}}\\
		\end{array}\right)\\
	=&
		\left(\begin{array}{c}
			\frac{n-1}{r_1}\\
			\vdots\\
			\frac{n-k-1}{r_k^2\tan\theta_k}\\
			\vdots\\
		\end{array}\right)^T
		\left(\begin{array}{c}
			\frac{\partial}{\partial r}\\
			\vdots\\
			\frac{\partial}{\partial \theta_k}\\
			\vdots\\
		\end{array}\right)\\
	&+
		\left(\begin{array}{ccccc}
			1 & 0 & \cdots & 0 & 0 \\
			0 & \frac{1}{r_1^2} & \cdots  & 0 & 0\\
			\vdots & \vdots & \ddots & \vdots &\vdots\\
			0 & 0 & \cdots & \frac{1}{r_{n-2}^2} & 0\\
			0 & 0 & \cdots & 0 & \frac{1}{r_{n-1}^2}\\
		\end{array}\right)
		\left(\begin{array}{lll}
			\frac{\partial}{\partial r} &
			\cdots &
			\frac{\partial}{
				\partial \theta_{n-1}}
		\end{array}\right)
		\left(\begin{array}{c}
			\frac{\partial}{\partial r}\\
			\vdots\\
			\frac{\partial}{\partial \theta_{n-1}}\\
		\end{array}\right)\\
\end{aligned}
$$

$$
まとめると、\\
\begin{aligned}
		\Delta_n
	=&
		\left(\begin{array}{c}
			\frac{n-1}{r_1}\\
			\vdots\\
			\frac{n-k-1}{r_k^2\tan\theta_k}\\
			\vdots\\
			0 \\
		\end{array}\right)^T
		\left(\begin{array}{c}
			\frac{\partial}{\partial r}\\
			\vdots\\
			\frac{\partial}{\partial \theta_k}\\
			\vdots\\
		\end{array}\right)\\
	&+
		\left(\begin{array}{ccccc}
			1 & 0 & \cdots & 0 & 0 \\
			0 & \frac{1}{r_1^2} & \cdots  & 0 & 0\\
			\vdots & \vdots & \ddots & \vdots &\vdots\\
			0 & 0 & \cdots & \frac{1}{r_{n-2}^2} & 0\\
			0 & 0 & \cdots & 0 & \frac{1}{r_{n-1}^2}\\
		\end{array}\right)
		\left(\begin{array}{lll}
			\frac{\partial}{\partial r} &
			\cdots &
			\frac{\partial}{
				\partial \theta_{n-1}}
		\end{array}\right)
		\left(\begin{array}{c}
			\frac{\partial}{\partial r}\\
			\vdots\\
			\frac{\partial}{\partial \theta_{n-1}}\\
		\end{array}\right)\\
	=&
		\frac{n-1}{r_1}\frac{\partial}{\partial r} + \sum_{i=1}^{n-1} \frac{n-i-1}{r_i^2\tan\theta_i}\frac{\partial}{\partial \theta_i}\\
	&+
		\frac{\partial^2}{\partial r^2} + \sum_{i=1}^{n-1} \frac{1}{r_i^2}\frac{\partial^2}{\partial \theta_i^2}\\
	\Delta_n
	=&
		\frac{n-1}{r}\frac{\partial}{\partial r} + \sum_{i=1}^{n-1} \frac{1}{r^2\prod_{j=1}^{i-1}\sin^2\theta_j}\frac{n-i-1}{\tan\theta_i}\frac{\partial}{\partial \theta_i}\\
	&+
		\frac{\partial^2}{\partial r^2} + \sum_{i=1}^{n-1} \frac{1}{r^2\prod_{j=1}^{i-1}\sin^2\theta_j}\frac{\partial^2}{\partial \theta_i^2}\\
\end{aligned}
$$

$$
これに n=3 を代入すると\\
\begin{aligned}
	\Delta_3
	=&
		\frac{2}{r}\frac{\partial}{\partial r} + \sum_{i=1}^{2} \frac{1}{r^2\prod_{j=1}^{i-1}\sin^2\theta_j}\frac{3-i-1}{\tan\theta_i}\frac{\partial}{\partial \theta_i}\\
	&+
		\frac{\partial^2}{\partial r^2} + \sum_{i=1}^{2} \frac{1}{r^2\prod_{j=1}^{i-1}\sin^2\theta_j}\frac{\partial^2}{\partial \theta_i^2}\\
	=&
		\frac{2}{r}\frac{\partial}{\partial r} + \frac{1}{r^2}\frac{1}{\tan\theta_1}\frac{\partial}{\partial \theta_1}\\
	&+
		\frac{\partial^2}{\partial r^2} + \frac{1}{r^2}\frac{\partial^2}{\partial \theta_1^2} + \frac{1}{r^2\sin^2\theta_1}\frac{\partial^2}{\partial \theta_2^2}\\
\end{aligned}\\
と、期待通りの結果が確かめられた。
$$

<a id="markdown-task" name="task"></a>
## 今後の課題
- ヤコビアンが"積" によって必ず対角化されるようなのがなぜなのか理解すること
- もっと"奇妙な" 座標系についても考えてみること
- もっと行列らしくなくて confusing ではない記法を考えること
