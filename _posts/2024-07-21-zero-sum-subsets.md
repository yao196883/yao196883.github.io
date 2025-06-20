---
title: "Zero Sum Subsets"
date: 2024-07-21
categories: [Math,Exploration]
tags: [Math]
pin: true
math: true
---


## Background
2024年7月17日，瞿振华教授莅临海亮高级中学，对全省来此参加数学夏令营的学生做报告，以开阔我们业余数学爱好者的眼界。

## Introduction
我们在学习 Elemental Number Theory 时，有如下熟知结论：

### Conclusion_1
Given $n$ integers $\{a_1,a_2,\dots,a_n\}$ , $\exists\ I\subseteq \{1,2,\dots,n\}$ and $|I|\ne 0,$ s.t. $n|\sum_{i\in I}{a_i}$<br>
(可考虑部分和，以及利用鸽巢原理)<br>
(其中 $n$ 为最佳,可取 $n-1$ 个 $1$.)

### Conclusion_2
$Erdos,Ginzburg\ and\ Ziv\ Theorem$ (1961)<br>
Given $2n-1$ integers $\{a_1,a_2,\dots,a_n\}$,$\exists\ I\subseteq \{1,2,\dots,2n-1\}$ and $|I|=n,$ s.t. $n|\sum_{i\in I}{a_i}$<br>
(可使用反证法，取p-1次方，导出矛盾)<br>
(其中 $2n-1$ 为最佳,可取 $n-1$ 个 $0,1$.)<br>

### General_Problem
$G$ 为有限交换群, $A$ 是由 $G$ 中元素构成的可重集。<br>
(1) $|A|$ 多大时， $\exists\ B \subseteq A$ and $|B|\ne 0,$ s.t. $\sigma(B)=0$.(称为$Davenport$常数,记作 $D(G)$ )<br>
(2) $ k\in \mathbb{Z}_{>0}$ and $exp(G)|k$ , $|A|$ 多大时， $\exists B \subseteq A$ and $|B|=k,$ s.t. $\sigma(B)=0$.(记作 $S(G)$ )(称 $B$ 为 $k$ 元 $Zero-sum-subset$ )

$exp(G):=\underset{x\in G}{max}\ ord(x)$<br>
$G=C_{n_1}\oplus C_{n_2}\oplus\cdots\oplus C_{n_l},\ n_1|n_2|\cdots|n_l,\ exp(G)=n_l$

$\sigma(B):=\sum_{x\in B}x$, 约定 $\sigma(\emptyset)=0$ <br><br>
(Con.1中, $G=\mathbb{Z} /n\mathbb{Z}=C_n$)<br>
(Con.2中, $G=C_n,k=n=exp(C_n)$ )

### Concerning_Problem
考虑 $G$ 秩为 $2$ 且 $n=p$ 的情形,即<br>
$A=\{(a_1,b_1),(a_2,b_2),\dots,(a_m,b_m)\}\subset\mathbb{Z}^2$<br>
(1) 当 $m$ 多大时, $\exists B \subseteq A$ and $|B|\ne 0,$ s.t. $\sigma(B)\equiv (0,0)\ (mod\ p)$<br>
(2) 当 $m$ 多大时, $\exists B \subseteq A$ and $|B|=p,$ s.t. $\sigma(B)\equiv (0,0)\ (mod\ p)$<br><br>
$Ans_1\ =\ 2p-1$ ($2p-2$ 反例: $p-1$ 个 $(0,1),(1,0)$ )<br>
$Ans_2\ =\ 4p-3$ ($4p-4$ 反例: $p-1$ 个 $(0,0),(0,1),(1,0),(1,1)$ )<br>
(注意到解决Con.1的鸽巢原理无法应用于此处)<br>
(Problem_2 又被称为 Kemnitz' Conjecture )<br>

## Solution_1-Generating_Function
可重集 $A=\{a_1,a_2,\dots,a_m\}$, $a_1,a_2,\dots,a_m \in \mathbb{Z}_{>0}$

$$(1+x^{a_1})(1+x^{a_2})\cdots(1+x^{a_m})=\sum_{B\subset A}x^{\sigma(B)}$$

利用:

$$(1-x^{a_1})(1-x^{a_2})\cdots(1-x^{a_m})=\sum_{B\subset A}(-1)^{|B|}x^{\sigma(B)}$$

### For_Con.1
$n=p,\ a_1,a_2,\dots,a_m\in \mathbb{Z}_{>0}$<br>
$S_k:=\{B\subset A\ |\ \sigma(B)\equiv k\ (mod\ p)\},\ k=0,1,\dots,p-1$<br>

$$f(x):=(1-x^{a_1})(1-x^{a_2})\cdots(1-x^{a_m})\in \mathbb{F}_p/(x^p-1)$$

$$f(x)=\sum_{B\subset A}(-1)^{|B|}x^{\sigma(B)}=\sum_{k=0}^{p-1}(\sum_{B\in S_k}(-1)^{|B|})x^k\ \ (\star)$$

上式可看作是余式，所以表示方式是唯一的.<br>
另一方面,又有 $(1-x^{a_j})=(1-x)(\cdots)$ ,则

$$f(x)=(1-x)^pg(x)$$

$$(1-x)^p=1-\binom{p}{1}x+ \binom{p}{2}x^2+\cdots+(-1)^px^p \overset{mod\ p}{==}1-x^p\overset{mod\ x^p-1}{==}0$$

$\Rightarrow\ f(x)=0$ 结合 $(\star)$ $\Rightarrow $

$$\forall\  0\le k\le p-1,\ \sum_{B\in S_k}(-1)^{|B|}\equiv 0\ (mod\ p)$$

特别的, $k=0$ 时, $\emptyset \in S_k$ 而 $\sum_{B\in S_k}(-1)^{|B|}\equiv 0\ (mod\ p)$<br>
$\Rightarrow\ \exists\ B\in S_0$ and $\|B\|\ne 0,$ s.t. $\sigma(B)\equiv 0\ (mod\ p)$.

<p align="right">$\Box$</p>
注意到这种方法给出了 比使用鸽巢原理更多的信息.