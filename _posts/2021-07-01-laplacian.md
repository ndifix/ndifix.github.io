---
layout: post
author: ndifix
title: "ラプラシアンの座標変換"
date: 2021-07-01 0:0:0
categories: Mathematics
---

ラプラシアンの座標変換は好きですか？私は嫌いです。
<!--more-->
## 2次元極座標の場合

{% katex %}
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
{% endkatex %}

まとめると

{% katex %}
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
{% endkatex %}

{% katex %}
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
{% endkatex %}

## 3次元球面座標のとき
{% katex %}
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
{% endkatex %}

まとめると

{% katex %}
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
{% endkatex %}

{% katex %}
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
{% endkatex %}
