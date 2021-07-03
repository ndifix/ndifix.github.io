---
layout: post
author: ndifix
title: "ラプラシアンきらい"
date: 2021-07-01 0:0:0
categories: Mathematics
---

もう二度とラプラシアンの座標変換をしたくないのでまとめておく。
<!--more-->
## 2次元極座標の場合

{% katex %}
\begin{aligned}
	x_1 &= r\cos \phi\\
	x_2 &= r\sin \phi\;\; とすると\\
	r &= \sqrt{x_1^2+x_2^2}\\
	\frac{\partial r}{\partial x_k} &= \frac{x_k}{\sqrt{x_1^2+x_2^2}}\\\\\\
	\frac{\partial x_1}{\partial x_1} &= \frac{\partial r}{\partial x_1}\cos\phi - r\frac{\partial \phi}{\partial x_1}\sin\phi\\
		&= \cos^2\phi - r\frac{\partial \phi}{\partial x_1}\sin\phi\\
	\therefore \frac{\partial \phi}{\partial x_1} &= -\frac{\sin\phi}{r}\\\\\\
	\frac{\partial x_2}{\partial x_2} &= \frac{\partial r}{\partial x_2}\sin\phi + r\frac{\partial \phi}{\partial x_2}\cos\phi\\
		&= \sin^2\phi + r\frac{\partial \phi}{\partial x_2}\cos\phi\\
	\therefore \frac{\partial \phi}{\partial x_2} &= \frac{\cos\phi}{r}\\\\
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
			\left(\begin{array}{ll}
				\frac{\partial}{\partial x_1} &	\frac{\partial}{\partial x_2}
			\end{array}\right)
			\left(\begin{array}{lr}
				\cos\phi & -\frac{\sin\phi}{r}\\
				\sin\phi & \frac{\cos\phi}{r}
			\end{array}\right)
			\left(\begin{array}{l}
				\frac{\partial}{\partial r}\\
				\frac{\partial}{\partial \phi}
			\end{array}\right)\\
		=&
			\left(\begin{array}{ll}
				\cos\phi\frac{\partial}{\partial r}-\frac{\sin\phi}{r}\frac{\partial}{\partial \phi} &
				\sin\phi\frac{\partial}{\partial r}+\frac{\cos\phi}{r}\frac{\partial}{\partial \phi}
			\end{array}\right)
			\left(\begin{array}{lr}
				\cos\phi & -\frac{\sin\phi}{r}\\
				\sin\phi & \frac{\cos\phi}{r}
			\end{array}\right)
			\left(\begin{array}{l}
				\frac{\partial}{\partial r}\\
				\frac{\partial}{\partial \phi}
			\end{array}\right)\\
		=&
			\left(\begin{array}{ll}
				\frac{\sin^2\phi}{r} +\frac{\cos^2\phi}{r} &
				2\frac{\cos\phi\sin\phi}{r^2} -2\frac{\cos\phi\sin\phi}{r^2} 
			\end{array}\right)
			\left(\begin{array}{l}
				\frac{\partial}{\partial r}\\
				\frac{\partial}{\partial \phi}
			\end{array}\right)\\
		&+
			\left(\begin{array}{lr}
				\cos\phi & 	\sin\phi\\
			-\frac{\sin\phi}{r} & \frac{\cos\phi}{r}
			\end{array}\right)
			\left(\begin{array}{lr}
				\cos\phi & -\frac{\sin\phi}{r}\\
				\sin\phi & \frac{\cos\phi}{r}
			\end{array}\right)
			\left(\begin{array}{ll}
				\frac{\partial}{\partial r} & \frac{\partial}{\partial \phi}
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
