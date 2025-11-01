---
layout: post
title: "Parametricity"
date: 2025-10-31
---

<https://www.cs.cmu.edu/~rwh/courses/atpl/pdfs/reynolds.pdf>

# 回顾 System F 或者说 Polymorphic Lambda Calculus

Statics

![\\mathrm{VAR} \\ \\frac{}{ \\Gamma , x :A \\vdash \_{\\Delta} x : A} \\quad \\mathrm{YES} \\ \\frac{}{\\Gamma\\vdash \_{\\Delta} \\mathsf{yes} : \\mathsf{ans}}\\quad \\mathrm{NO}\\ \\frac{}{\\Gamma \\vdash\_{\\Delta} \\mathsf{no}: \\mathsf{ans}}](https://latex.codecogs.com/svg.image?%5Cmathrm%7BVAR%7D%20%5C%20%5Cfrac%7B%7D%7B%20%5CGamma%20%2C%20x%20%3AA%20%5Cvdash%20_%7B%5CDelta%7D%20x%20%3A%20A%7D%20%5Cquad%20%5Cmathrm%7BYES%7D%20%5C%20%5Cfrac%7B%7D%7B%5CGamma%5Cvdash%20_%7B%5CDelta%7D%20%5Cmathsf%7Byes%7D%20%3A%20%5Cmathsf%7Bans%7D%7D%5Cquad%20%5Cmathrm%7BNO%7D%5C%20%5Cfrac%7B%7D%7B%5CGamma%20%5Cvdash_%7B%5CDelta%7D%20%5Cmathsf%7Bno%7D%3A%20%5Cmathsf%7Bans%7D%7D "\mathrm{VAR} \ \frac{}{ \Gamma , x :A \vdash _{\Delta} x : A} \quad \mathrm{YES} \ \frac{}{\Gamma\vdash _{\Delta} \mathsf{yes} : \mathsf{ans}}\quad \mathrm{NO}\ \frac{}{\Gamma \vdash_{\Delta} \mathsf{no}: \mathsf{ans}}")

![\\mathrm{Lam}\\ \\frac{\\Gamma , x :A_1 \\vdash \_{\\Delta} M_2 : A_2}{\\Gamma \\vdash \_{\\Delta} \\lambda(x.M_2) : A_1 \\to A_2}\\quad \\mathrm{App}\\ \\frac{\\Gamma \\vdash \_{\\Delta} M_1 : A_2 \\to A \\quad \\Gamma \\vdash \_{\\Delta} M_2 : A_2}{\\Gamma \\vdash \\mathsf{ap}(M_1 ; M_2) : A}](https://latex.codecogs.com/svg.image?%5Cmathrm%7BLam%7D%5C%20%5Cfrac%7B%5CGamma%20%2C%20x%20%3AA_1%20%5Cvdash%20_%7B%5CDelta%7D%20M_2%20%3A%20A_2%7D%7B%5CGamma%20%5Cvdash%20_%7B%5CDelta%7D%20%5Clambda%28x.M_2%29%20%3A%20A_1%20%5Cto%20A_2%7D%5Cquad%20%5Cmathrm%7BApp%7D%5C%20%5Cfrac%7B%5CGamma%20%5Cvdash%20_%7B%5CDelta%7D%20M_1%20%3A%20A_2%20%5Cto%20A%20%5Cquad%20%5CGamma%20%5Cvdash%20_%7B%5CDelta%7D%20M_2%20%3A%20A_2%7D%7B%5CGamma%20%5Cvdash%20%5Cmathsf%7Bap%7D%28M_1%20%3B%20M_2%29%20%3A%20A%7D "\mathrm{Lam}\ \frac{\Gamma , x :A_1 \vdash _{\Delta} M_2 : A_2}{\Gamma \vdash _{\Delta} \lambda(x.M_2) : A_1 \to A_2}\quad \mathrm{App}\ \frac{\Gamma \vdash _{\Delta} M_1 : A_2 \to A \quad \Gamma \vdash _{\Delta} M_2 : A_2}{\Gamma \vdash \mathsf{ap}(M_1 ; M_2) : A}")

![\\mathrm{LAM} \\ \\frac{\\Gamma \\vdash \_{\\Delta, X \\ \\mathsf{type}} M : A}{\\Gamma \\vdash \_{\\Delta} \\Lambda(X.M) : \\forall (X.A)} \\quad \\mathrm{APP} \\ \\frac{\\Gamma\\vdash\_{\\Delta} M : \\forall (X. B) \\quad \\Delta \\vdash A \\ \\mathsf{type}}{\\Gamma\\vdash \_{\\Delta} \\mathsf{Ap}(M ; A) : \[A/X\]B}](https://latex.codecogs.com/svg.image?%5Cmathrm%7BLAM%7D%20%5C%20%5Cfrac%7B%5CGamma%20%5Cvdash%20_%7B%5CDelta%2C%20X%20%5C%20%5Cmathsf%7Btype%7D%7D%20M%20%3A%20A%7D%7B%5CGamma%20%5Cvdash%20_%7B%5CDelta%7D%20%5CLambda%28X.M%29%20%3A%20%5Cforall%20%28X.A%29%7D%20%5Cquad%20%5Cmathrm%7BAPP%7D%20%5C%20%5Cfrac%7B%5CGamma%5Cvdash_%7B%5CDelta%7D%20M%20%3A%20%5Cforall%20%28X.%20B%29%20%5Cquad%20%5CDelta%20%5Cvdash%20A%20%5C%20%5Cmathsf%7Btype%7D%7D%7B%5CGamma%5Cvdash%20_%7B%5CDelta%7D%20%5Cmathsf%7BAp%7D%28M%20%3B%20A%29%20%3A%20%5BA%2FX%5DB%7D "\mathrm{LAM} \ \frac{\Gamma \vdash _{\Delta, X \ \mathsf{type}} M : A}{\Gamma \vdash _{\Delta} \Lambda(X.M) : \forall (X.A)} \quad \mathrm{APP} \ \frac{\Gamma\vdash_{\Delta} M : \forall (X. B) \quad \Delta \vdash A \ \mathsf{type}}{\Gamma\vdash _{\Delta} \mathsf{Ap}(M ; A) : [A/X]B}")

Dynamics

![\\mathrm{YES} \\ \\frac{}{\\mathsf{yes} \\ \\mathsf{final}}\\quad \\mathrm{NO}\\ \\frac{}{\\mathsf{no}}\\ \\mathsf{final}](https://latex.codecogs.com/svg.image?%5Cmathrm%7BYES%7D%20%5C%20%5Cfrac%7B%7D%7B%5Cmathsf%7Byes%7D%20%5C%20%5Cmathsf%7Bfinal%7D%7D%5Cquad%20%5Cmathrm%7BNO%7D%5C%20%5Cfrac%7B%7D%7B%5Cmathsf%7Bno%7D%7D%5C%20%5Cmathsf%7Bfinal%7D "\mathrm{YES} \ \frac{}{\mathsf{yes} \ \mathsf{final}}\quad \mathrm{NO}\ \frac{}{\mathsf{no}}\ \mathsf{final}")

![\\mathrm{App} \\ \\frac{M_1 \\longmapsto M_1 \' }{\\mathsf{ap}(M_1 ; M_2) \\longmapsto \\mathsf{ap}(M_1\' ; M_2)}\\quad \\mathrm{App}\\text{-}\\mathrm{Lam}\\ \\frac{}{\\mathsf{ap}(\\lambda(x.M); M_2) \\longmapsto \[M_2 / x\] M}](https://latex.codecogs.com/svg.image?%5Cmathrm%7BApp%7D%20%5C%20%5Cfrac%7BM_1%20%5Clongmapsto%20M_1%20%27%20%7D%7B%5Cmathsf%7Bap%7D%28M_1%20%3B%20M_2%29%20%5Clongmapsto%20%5Cmathsf%7Bap%7D%28M_1%27%20%3B%20M_2%29%7D%5Cquad%20%5Cmathrm%7BApp%7D%5Ctext%7B-%7D%5Cmathrm%7BLam%7D%5C%20%5Cfrac%7B%7D%7B%5Cmathsf%7Bap%7D%28%5Clambda%28x.M%29%3B%20M_2%29%20%5Clongmapsto%20%5BM_2%20%2F%20x%5D%20M%7D "\mathrm{App} \ \frac{M_1 \longmapsto M_1 ' }{\mathsf{ap}(M_1 ; M_2) \longmapsto \mathsf{ap}(M_1' ; M_2)}\quad \mathrm{App}\text{-}\mathrm{Lam}\ \frac{}{\mathsf{ap}(\lambda(x.M); M_2) \longmapsto [M_2 / x] M}")

![\\mathrm{APP} \\ \\frac{M\\longmapsto M\'}{\\mathsf{Ap}(M;A)\\longmapsto \\mathsf{Ap}(M\'; A)}\\quad \\text{APP-LAM} \\frac{}{\\mathsf{Ap}(\\Lambda(X.M); A) \\longmapsto \[A/X\]M}](https://latex.codecogs.com/svg.image?%5Cmathrm%7BAPP%7D%20%5C%20%5Cfrac%7BM%5Clongmapsto%20M%27%7D%7B%5Cmathsf%7BAp%7D%28M%3BA%29%5Clongmapsto%20%5Cmathsf%7BAp%7D%28M%27%3B%20A%29%7D%5Cquad%20%5Ctext%7BAPP-LAM%7D%20%5Cfrac%7B%7D%7B%5Cmathsf%7BAp%7D%28%5CLambda%28X.M%29%3B%20A%29%20%5Clongmapsto%20%5BA%2FX%5DM%7D "\mathrm{APP} \ \frac{M\longmapsto M'}{\mathsf{Ap}(M;A)\longmapsto \mathsf{Ap}(M'; A)}\quad \text{APP-LAM} \frac{}{\mathsf{Ap}(\Lambda(X.M); A) \longmapsto [A/X]M}")

总之不知道为什么 Harper 在这里进行一下符号的化简。注意到我们的 term
里面的 variable 不是 typed 的。在 *The Blind Spot* 或者是 *Proofs and
Types* 里面的 variable 都是 Typed 的。这就导致了对于 term
来说，其实不需要 Type Variable 的替换。所以 Harper 将
![\\Lambda(X.M)](https://latex.codecogs.com/svg.image?%5CLambda%28X.M%29 "\Lambda(X.M)")
重写为
![\\Lambda(M)](https://latex.codecogs.com/svg.image?%5CLambda%28M%29 "\Lambda(M)")
以及
![\\mathsf{Ap}(M; A)](https://latex.codecogs.com/svg.image?%5Cmathsf%7BAp%7D%28M%3B%20A%29 "\mathsf{Ap}(M; A)")
重写为
![\\mathsf{Ap}(M)](https://latex.codecogs.com/svg.image?%5Cmathsf%7BAp%7D%28M%29 "\mathsf{Ap}(M)")。其实是无伤大雅的事情。

# Zig Zag Completeness （ZZC） 和 Parametricity Candidate

在 System F 之中存在一个称为 reducible candidate
的概念。这个东西到底是什么？ 我也不太清楚。但重要的是，他的性质： closed
under head expansion 是重要的。

某种意义上 Zig Zag Completeness 是 closed under head expansion
的衍生。只不过 我没有仔细调查过。这种衍生是从 unitary 到 binary relation
的衍生。比如说 reducible candidate 的性质可以这样认为，对于
![M : A](https://latex.codecogs.com/svg.image?M%20%3A%20A "M : A")
而言，如果存在
![N : A](https://latex.codecogs.com/svg.image?N%20%3A%20A "N : A") 使得
![N \\longmapsto M](https://latex.codecogs.com/svg.image?N%20%5Clongmapsto%20M "N \longmapsto M")
则说
![\\mathsf{HE}(M) = N](https://latex.codecogs.com/svg.image?%5Cmathsf%7BHE%7D%28M%29%20%3D%20N "\mathsf{HE}(M) = N")
对于类型 ![A](https://latex.codecogs.com/svg.image?A "A") 的 term 的集合
![C](https://latex.codecogs.com/svg.image?C "C")，称其为 reducible
candidate，如果
![\\forall M \\in C ,\\mathsf{HE}(M) \\in C](https://latex.codecogs.com/svg.image?%5Cforall%20M%20%5Cin%20C%20%2C%5Cmathsf%7BHE%7D%28M%29%20%5Cin%20C "\forall M \in C ,\mathsf{HE}(M) \in C")；或者是
![\\mathsf{HE}(C) \\subseteq C](https://latex.codecogs.com/svg.image?%5Cmathsf%7BHE%7D%28C%29%20%5Csubseteq%20C "\mathsf{HE}(C) \subseteq C")
如果你知道我在说什么的话。

一个二元关系 ![R](https://latex.codecogs.com/svg.image?R "R") 是
![A \\times B](https://latex.codecogs.com/svg.image?A%20%5Ctimes%20B "A \times B")
的子集，那么我们说一个 parametricity candidate 首先要满足 closed under
head expansion，如果说有
![\\mathsf{HE}(M) = N](https://latex.codecogs.com/svg.image?%5Cmathsf%7BHE%7D%28M%29%20%3D%20N "\mathsf{HE}(M) = N")
则
![(M , M\') \\in R](https://latex.codecogs.com/svg.image?%28M%20%2C%20M%27%29%20%5Cin%20R "(M , M') \in R")
implies
![(N, M\')\\in R](https://latex.codecogs.com/svg.image?%28N%2C%20M%27%29%5Cin%20R "(N, M')\in R")，其实和上面的是很类似的。

至于说为什么需要 ZZC，说实话我也不是很清楚。ZZC 指的是，有这样一个蛇形的
Z，从左上角到右下角，则蕴含了左上角到右下角的关系。总之就是如此！可能是因为
![R](https://latex.codecogs.com/svg.image?R "R") 可以是两个不同类型的
term 之间的关系。如果如此的，传递性是不可能有的，因为
![x \\sim y](https://latex.codecogs.com/svg.image?x%20%5Csim%20y "x \sim y")
且
![y \\sim z](https://latex.codecogs.com/svg.image?y%20%5Csim%20z "y \sim z")
能推出
![x \\sim z](https://latex.codecogs.com/svg.image?x%20%5Csim%20z "x \sim z")
而
![x, z \\in A](https://latex.codecogs.com/svg.image?x%2C%20z%20%5Cin%20A "x, z \in A")
于是 ![\\sim](https://latex.codecogs.com/svg.image?%5Csim "\sim") 不应为
![A](https://latex.codecogs.com/svg.image?A "A") 和
![B](https://latex.codecogs.com/svg.image?B "B") 之间的关系。所以 ZZC
应该是这种情况下的传递性的一个弱化的版本（可能）。

# Exact Equality

Context
![\\Delta](https://latex.codecogs.com/svg.image?%5CDelta "\Delta") 上的
![\\delta](https://latex.codecogs.com/svg.image?%5Cdelta "\delta") 和
![\\delta\'](https://latex.codecogs.com/svg.image?%5Cdelta%27 "\delta'")
都是类型的 substi，将变量
![X](https://latex.codecogs.com/svg.image?X "X") 射到 closed 类型
![\\delta(X)](https://latex.codecogs.com/svg.image?%5Cdelta%28X%29 "\delta(X)")。
![\\eta](https://latex.codecogs.com/svg.image?%5Ceta "\eta") 是一个
candidate assignment，他将
![\\Delta](https://latex.codecogs.com/svg.image?%5CDelta "\Delta")
之中的变量 ![X](https://latex.codecogs.com/svg.image?X "X") 射到
![\\delta(X)](https://latex.codecogs.com/svg.image?%5Cdelta%28X%29 "\delta(X)")
和
![\\delta\'(X)](https://latex.codecogs.com/svg.image?%5Cdelta%27%28X%29 "\delta'(X)")
之间的一个 candidate （也就是一个二元关系）。

![\\begin{aligned}M \\sim M\' \\in \\text{ans} \\, \[\\eta : \\delta \\leftrightarrow \\delta\'\] & \\text{ iff } M, M\' \\stackrel{\*}{\\longmapsto} \\text{yes or } M, M\' \\stackrel{\*}{\\longmapsto} \\text{no} \\\\
M \\sim M\' \\in X \\, \[\\eta : \\delta \\leftrightarrow \\delta\'\] & \\text{ iff } M \\, \\eta(X) \\, M\' \\\\
M \\sim M\' \\in A_1 \\to A_2 \\, \[\\eta : \\delta \\leftrightarrow \\delta\'\] & \\text{ iff }
\\begin{cases}
M \\stackrel{\*}{\\longmapsto} \\lambda(x.M_2), \\, M\' \\stackrel{\*}{\\longmapsto} \\lambda(x.M\'\_2), \\\\
M_1 \\sim M\'\_1 \\in A_1 \\, \[\\eta : \\delta \\leftrightarrow \\delta\'\] \\text{ implies } \\\\
\[M_1/x\]M_2 \\sim \[M\'\_1/x\]M\'\_2 \\in A_2 \\, \[\\eta : \\delta \\leftrightarrow \\delta\'\]
\\end{cases} \\\\
M \\sim M\' \\in \\forall(X.A_2) \\, \[\\eta : \\delta \\leftrightarrow \\delta\'\] & \\text{ iff }
\\begin{cases}
M \\stackrel{\*}{\\longmapsto} \\Lambda(M_2), \\, M\' \\stackrel{\*}{\\longmapsto} \\Lambda(M\'\_2), \\text{and if } R : B \\leftrightarrow B\' \\text{ then} \\\\
\[B/t\]M_2 \\sim \[B\'/t\]M\'\_2 \\in A_2 \\, \[\\eta\[X \\mapsto R\] : \\delta\[X \\mapsto B\] \\leftrightarrow \\delta\'\[X \\mapsto B\'\]\]
\\end{cases}\\end{aligned}](https://latex.codecogs.com/svg.image?%5Cbegin%7Baligned%7DM%20%5Csim%20M%27%20%5Cin%20%5Ctext%7Bans%7D%20%5C%2C%20%5B%5Ceta%20%3A%20%5Cdelta%20%5Cleftrightarrow%20%5Cdelta%27%5D%20%26%20%5Ctext%7B%20iff%20%7D%20M%2C%20M%27%20%5Cstackrel%7B%2A%7D%7B%5Clongmapsto%7D%20%5Ctext%7Byes%20or%20%7D%20M%2C%20M%27%20%5Cstackrel%7B%2A%7D%7B%5Clongmapsto%7D%20%5Ctext%7Bno%7D%20%5C%5C%0AM%20%5Csim%20M%27%20%5Cin%20X%20%5C%2C%20%5B%5Ceta%20%3A%20%5Cdelta%20%5Cleftrightarrow%20%5Cdelta%27%5D%20%26%20%5Ctext%7B%20iff%20%7D%20M%20%5C%2C%20%5Ceta%28X%29%20%5C%2C%20M%27%20%5C%5C%0AM%20%5Csim%20M%27%20%5Cin%20A_1%20%5Cto%20A_2%20%5C%2C%20%5B%5Ceta%20%3A%20%5Cdelta%20%5Cleftrightarrow%20%5Cdelta%27%5D%20%26%20%5Ctext%7B%20iff%20%7D%0A%5Cbegin%7Bcases%7D%0AM%20%5Cstackrel%7B%2A%7D%7B%5Clongmapsto%7D%20%5Clambda%28x.M_2%29%2C%20%5C%2C%20M%27%20%5Cstackrel%7B%2A%7D%7B%5Clongmapsto%7D%20%5Clambda%28x.M%27_2%29%2C%20%5C%5C%0AM_1%20%5Csim%20M%27_1%20%5Cin%20A_1%20%5C%2C%20%5B%5Ceta%20%3A%20%5Cdelta%20%5Cleftrightarrow%20%5Cdelta%27%5D%20%5Ctext%7B%20implies%20%7D%20%5C%5C%0A%5BM_1%2Fx%5DM_2%20%5Csim%20%5BM%27_1%2Fx%5DM%27_2%20%5Cin%20A_2%20%5C%2C%20%5B%5Ceta%20%3A%20%5Cdelta%20%5Cleftrightarrow%20%5Cdelta%27%5D%0A%5Cend%7Bcases%7D%20%5C%5C%0AM%20%5Csim%20M%27%20%5Cin%20%5Cforall%28X.A_2%29%20%5C%2C%20%5B%5Ceta%20%3A%20%5Cdelta%20%5Cleftrightarrow%20%5Cdelta%27%5D%20%26%20%5Ctext%7B%20iff%20%7D%0A%5Cbegin%7Bcases%7D%0AM%20%5Cstackrel%7B%2A%7D%7B%5Clongmapsto%7D%20%5CLambda%28M_2%29%2C%20%5C%2C%20M%27%20%5Cstackrel%7B%2A%7D%7B%5Clongmapsto%7D%20%5CLambda%28M%27_2%29%2C%20%5Ctext%7Band%20if%20%7D%20R%20%3A%20B%20%5Cleftrightarrow%20B%27%20%5Ctext%7B%20then%7D%20%5C%5C%0A%5BB%2Ft%5DM_2%20%5Csim%20%5BB%27%2Ft%5DM%27_2%20%5Cin%20A_2%20%5C%2C%20%5B%5Ceta%5BX%20%5Cmapsto%20R%5D%20%3A%20%5Cdelta%5BX%20%5Cmapsto%20B%5D%20%5Cleftrightarrow%20%5Cdelta%27%5BX%20%5Cmapsto%20B%27%5D%5D%0A%5Cend%7Bcases%7D%5Cend%7Baligned%7D "\begin{aligned}M \sim M' \in \text{ans} \, [\eta : \delta \leftrightarrow \delta'] & \text{ iff } M, M' \stackrel{*}{\longmapsto} \text{yes or } M, M' \stackrel{*}{\longmapsto} \text{no} \\
M \sim M' \in X \, [\eta : \delta \leftrightarrow \delta'] & \text{ iff } M \, \eta(X) \, M' \\
M \sim M' \in A_1 \to A_2 \, [\eta : \delta \leftrightarrow \delta'] & \text{ iff }
\begin{cases}
M \stackrel{*}{\longmapsto} \lambda(x.M_2), \, M' \stackrel{*}{\longmapsto} \lambda(x.M'_2), \\
M_1 \sim M'_1 \in A_1 \, [\eta : \delta \leftrightarrow \delta'] \text{ implies } \\
[M_1/x]M_2 \sim [M'_1/x]M'_2 \in A_2 \, [\eta : \delta \leftrightarrow \delta']
\end{cases} \\
M \sim M' \in \forall(X.A_2) \, [\eta : \delta \leftrightarrow \delta'] & \text{ iff }
\begin{cases}
M \stackrel{*}{\longmapsto} \Lambda(M_2), \, M' \stackrel{*}{\longmapsto} \Lambda(M'_2), \text{and if } R : B \leftrightarrow B' \text{ then} \\
[B/t]M_2 \sim [B'/t]M'_2 \in A_2 \, [\eta[X \mapsto R] : \delta[X \mapsto B] \leftrightarrow \delta'[X \mapsto B']]
\end{cases}\end{aligned}")

这里的 ![\\sim](https://latex.codecogs.com/svg.image?%5Csim "\sim") 就是
Closed Under Head Expansion 的，并且是满足 ZZC 的。所以
![\\sim](https://latex.codecogs.com/svg.image?%5Csim "\sim") 是一个
parametricity candidate。

Lemma 2 (Head Expansion). If
![M \\sim M\' \\in A\\,  \[\\eta : \\delta \\leftrightarrow \\delta\'\]](https://latex.codecogs.com/svg.image?M%20%5Csim%20M%27%20%5Cin%20A%5C%2C%20%20%5B%5Ceta%20%3A%20%5Cdelta%20%5Cleftrightarrow%20%5Cdelta%27%5D "M \sim M' \in A\,  [\eta : \delta \leftrightarrow \delta']")
then if
![N \\longmapsto M](https://latex.codecogs.com/svg.image?N%20%5Clongmapsto%20M "N \longmapsto M")
then
![N \\sim M\' \\in A \\, \[ \\eta : \\delta \\leftrightarrow \\delta\'\]](https://latex.codecogs.com/svg.image?N%20%5Csim%20M%27%20%5Cin%20A%20%5C%2C%20%5B%20%5Ceta%20%3A%20%5Cdelta%20%5Cleftrightarrow%20%5Cdelta%27%5D "N \sim M' \in A \, [ \eta : \delta \leftrightarrow \delta']")
and if
![N\' \\longmapsto M\'](https://latex.codecogs.com/svg.image?N%27%20%5Clongmapsto%20M%27 "N' \longmapsto M'")
then
![M \\sim N\' \\in A \\, \[\\eta : \\delta \\leftrightarrow \\delta\'\]](https://latex.codecogs.com/svg.image?M%20%5Csim%20N%27%20%5Cin%20A%20%5C%2C%20%5B%5Ceta%20%3A%20%5Cdelta%20%5Cleftrightarrow%20%5Cdelta%27%5D "M \sim N' \in A \, [\eta : \delta \leftrightarrow \delta']").

Lemma 3 (ZZC) For each type
![A](https://latex.codecogs.com/svg.image?A "A") in
![\\Delta](https://latex.codecogs.com/svg.image?%5CDelta "\Delta"), and
each candidate assignment
![\\eta](https://latex.codecogs.com/svg.image?%5Ceta "\eta") for
![\\delta, \\delta\' : \\Delta](https://latex.codecogs.com/svg.image?%5Cdelta%2C%20%5Cdelta%27%20%3A%20%5CDelta "\delta, \delta' : \Delta"),
the similarity relation
![\\\_ \\sim \\\_ \\in A \\,\[\\eta : \\delta \\leftrightarrow \\delta\'\]](https://latex.codecogs.com/svg.image?%5C_%20%5Csim%20%5C_%20%5Cin%20A%20%5C%2C%5B%5Ceta%20%3A%20%5Cdelta%20%5Cleftrightarrow%20%5Cdelta%27%5D "\_ \sim \_ \in A \,[\eta : \delta \leftrightarrow \delta']")
is zig-zag complete.

记号：
![\\Gamma \\gg \_{\\Delta} M \\doteq M \' \\in A](https://latex.codecogs.com/svg.image?%5CGamma%20%5Cgg%20_%7B%5CDelta%7D%20M%20%5Cdoteq%20M%20%27%20%5Cin%20A "\Gamma \gg _{\Delta} M \doteq M ' \in A")
指的是给定了
![\\gamma \\sim \\gamma\' \\in \\Gamma \\, \[ \\eta : \\delta \\leftrightarrow \\delta\'\]](https://latex.codecogs.com/svg.image?%5Cgamma%20%5Csim%20%5Cgamma%27%20%5Cin%20%5CGamma%20%5C%2C%20%5B%20%5Ceta%20%3A%20%5Cdelta%20%5Cleftrightarrow%20%5Cdelta%27%5D "\gamma \sim \gamma' \in \Gamma \, [ \eta : \delta \leftrightarrow \delta']")
的情况下，有
![\\hat\\gamma(M) \\sim \\hat\\gamma\'(M\') \\in A \\, \[\\eta : \\delta \\leftrightarrow \\delta\'\]](https://latex.codecogs.com/svg.image?%5Chat%5Cgamma%28M%29%20%5Csim%20%5Chat%5Cgamma%27%28M%27%29%20%5Cin%20A%20%5C%2C%20%5B%5Ceta%20%3A%20%5Cdelta%20%5Cleftrightarrow%20%5Cdelta%27%5D "\hat\gamma(M) \sim \hat\gamma'(M') \in A \, [\eta : \delta \leftrightarrow \delta']")。这里
![\\gamma](https://latex.codecogs.com/svg.image?%5Cgamma "\gamma") 将
![\\Gamma](https://latex.codecogs.com/svg.image?%5CGamma "\Gamma")
之中变量射到 closed term 上，并且
![\\eta](https://latex.codecogs.com/svg.image?%5Ceta "\eta")
如前文所述是 candidate
assignment。![\\gamma](https://latex.codecogs.com/svg.image?%5Cgamma "\gamma")
和
![\\gamma\'](https://latex.codecogs.com/svg.image?%5Cgamma%27 "\gamma'")
的这层关系表示的是对于任意的
![\\Gamma \\vdash x : B](https://latex.codecogs.com/svg.image?%5CGamma%20%5Cvdash%20x%20%3A%20B "\Gamma \vdash x : B")
有
![\\gamma(x) \\sim \\gamma\'(x) \\in B \\, \[\\eta : \\delta \\leftrightarrow \\delta\'\]](https://latex.codecogs.com/svg.image?%5Cgamma%28x%29%20%5Csim%20%5Cgamma%27%28x%29%20%5Cin%20B%20%5C%2C%20%5B%5Ceta%20%3A%20%5Cdelta%20%5Cleftrightarrow%20%5Cdelta%27%5D "\gamma(x) \sim \gamma'(x) \in B \, [\eta : \delta \leftrightarrow \delta']")。

Lemma 4 (Compositionality). Suppose that
![\\Delta \\vdash B](https://latex.codecogs.com/svg.image?%5CDelta%20%5Cvdash%20B "\Delta \vdash B")
type and
![\\Delta, X \\vdash A](https://latex.codecogs.com/svg.image?%5CDelta%2C%20X%20%5Cvdash%20A "\Delta, X \vdash A")
type. Let
![\\delta, \\delta\' : \\Delta](https://latex.codecogs.com/svg.image?%5Cdelta%2C%20%5Cdelta%27%20%3A%20%5CDelta "\delta, \delta' : \Delta")
and assume
![\\eta : \\delta \\leftrightarrow \\delta\'](https://latex.codecogs.com/svg.image?%5Ceta%20%3A%20%5Cdelta%20%5Cleftrightarrow%20%5Cdelta%27 "\eta : \delta \leftrightarrow \delta'").
Then,

![M \\sim M\' \\in \[B/X\]A \\, \[\\eta : \\delta \\leftrightarrow \\delta\'\] \\text{ iff } M \\sim M\' \\in A \\, \[\\eta_1 : \\delta_1 \\leftrightarrow \\delta\' \_ 1\],](https://latex.codecogs.com/svg.image?M%20%5Csim%20M%27%20%5Cin%20%5BB%2FX%5DA%20%5C%2C%20%5B%5Ceta%20%3A%20%5Cdelta%20%5Cleftrightarrow%20%5Cdelta%27%5D%20%5Ctext%7B%20iff%20%7D%20M%20%5Csim%20M%27%20%5Cin%20A%20%5C%2C%20%5B%5Ceta_1%20%3A%20%5Cdelta_1%20%5Cleftrightarrow%20%5Cdelta%27%20_%201%5D%2C "M \sim M' \in [B/X]A \, [\eta : \delta \leftrightarrow \delta'] \text{ iff } M \sim M' \in A \, [\eta_1 : \delta_1 \leftrightarrow \delta' _ 1],")

where
![\\delta_1 = \\delta\[X \\mapsto \\hat{\\delta}B\]](https://latex.codecogs.com/svg.image?%5Cdelta_1%20%3D%20%5Cdelta%5BX%20%5Cmapsto%20%5Chat%7B%5Cdelta%7DB%5D "\delta_1 = \delta[X \mapsto \hat{\delta}B]"),
and
![\\delta\' \_ 1 = \\delta\'\\, \[X \\mapsto \\hat{\\delta\'}B\]](https://latex.codecogs.com/svg.image?%5Cdelta%27%20_%201%20%3D%20%5Cdelta%27%5C%2C%20%5BX%20%5Cmapsto%20%5Chat%7B%5Cdelta%27%7DB%5D "\delta' _ 1 = \delta'\, [X \mapsto \hat{\delta'}B]"),
and
![\\eta_1 = \\eta\\, \[X \\mapsto \\\_ \\sim \\\_ \\in B \\, \[\\eta : \\delta \\leftrightarrow \\delta\'\]\]](https://latex.codecogs.com/svg.image?%5Ceta_1%20%3D%20%5Ceta%5C%2C%20%5BX%20%5Cmapsto%20%5C_%20%5Csim%20%5C_%20%5Cin%20B%20%5C%2C%20%5B%5Ceta%20%3A%20%5Cdelta%20%5Cleftrightarrow%20%5Cdelta%27%5D%5D "\eta_1 = \eta\, [X \mapsto \_ \sim \_ \in B \, [\eta : \delta \leftrightarrow \delta']]").

这是使用 induction hypothesis 的关键之一，这表示了
![\[B/X\]](https://latex.codecogs.com/svg.image?%5BB%2FX%5D "[B/X]")
复合到 substi 上的结果。

# Parametricity

Theorem 5 若是
![\\Gamma \\vdash\_{\\Delta} M : A](https://latex.codecogs.com/svg.image?%5CGamma%20%5Cvdash_%7B%5CDelta%7D%20M%20%3A%20A "\Gamma \vdash_{\Delta} M : A")
则
![\\Gamma \\gg \_{\\Delta} M \\in A](https://latex.codecogs.com/svg.image?%5CGamma%20%5Cgg%20_%7B%5CDelta%7D%20M%20%5Cin%20A "\Gamma \gg _{\Delta} M \in A")。

Proof. 对 ![M](https://latex.codecogs.com/svg.image?M "M") 进行
induction

按照 Harper 的说法应该只有两个 cases 是要注意的。

1.  当 ![M](https://latex.codecogs.com/svg.image?M "M") 是由 rule LAM
    得到的。
2.  当 ![M](https://latex.codecogs.com/svg.image?M "M") 是由 rule Lam
    得到的。

回忆到
![\\Gamma \\gg \_{\\Delta} M \\in A](https://latex.codecogs.com/svg.image?%5CGamma%20%5Cgg%20_%7B%5CDelta%7D%20M%20%5Cin%20A "\Gamma \gg _{\Delta} M \in A")
需要证明对于任意的
![\\gamma \\sim \\gamma \' \\in \\Gamma \\, \[\\eta : \\delta \\leftrightarrow \\delta\'\]](https://latex.codecogs.com/svg.image?%5Cgamma%20%5Csim%20%5Cgamma%20%27%20%5Cin%20%5CGamma%20%5C%2C%20%5B%5Ceta%20%3A%20%5Cdelta%20%5Cleftrightarrow%20%5Cdelta%27%5D "\gamma \sim \gamma ' \in \Gamma \, [\eta : \delta \leftrightarrow \delta']")，都有
![\\hat M  \\sim \\hat M\' \\in A \\, \[\\eta : \\delta \\leftrightarrow \\delta\'\]](https://latex.codecogs.com/svg.image?%5Chat%20M%20%20%5Csim%20%5Chat%20M%27%20%5Cin%20A%20%5C%2C%20%5B%5Ceta%20%3A%20%5Cdelta%20%5Cleftrightarrow%20%5Cdelta%27%5D "\hat M  \sim \hat M' \in A \, [\eta : \delta \leftrightarrow \delta']")，其中
![\\hat M = \\hat \\gamma (M)](https://latex.codecogs.com/svg.image?%5Chat%20M%20%3D%20%5Chat%20%5Cgamma%20%28M%29 "\hat M = \hat \gamma (M)")
并且
![\\hat M\' = \\hat \\gamma \' (M)](https://latex.codecogs.com/svg.image?%5Chat%20M%27%20%3D%20%5Chat%20%5Cgamma%20%27%20%28M%29 "\hat M' = \hat \gamma ' (M)")。

1.  当 ![M](https://latex.codecogs.com/svg.image?M "M") 形为
    ![\\Gamma \\vdash \_{\\Delta} \\Lambda (M) : \\forall (X.A)](https://latex.codecogs.com/svg.image?%5CGamma%20%5Cvdash%20_%7B%5CDelta%7D%20%5CLambda%20%28M%29%20%3A%20%5Cforall%20%28X.A%29 "\Gamma \vdash _{\Delta} \Lambda (M) : \forall (X.A)")，premise
    为
    ![\\Gamma\\vdash\_{\\Delta, X \\ \\mathsf{type}} M : A](https://latex.codecogs.com/svg.image?%5CGamma%5Cvdash_%7B%5CDelta%2C%20X%20%5C%20%5Cmathsf%7Btype%7D%7D%20M%20%3A%20A "\Gamma\vdash_{\Delta, X \ \mathsf{type}} M : A")。

    需要证明的是
    ![\\Lambda (\\hat M) \\sim \\Lambda (\\hat M \')\\in A \\, \[\\eta : \\delta \\leftrightarrow \\delta\'\]](https://latex.codecogs.com/svg.image?%5CLambda%20%28%5Chat%20M%29%20%5Csim%20%5CLambda%20%28%5Chat%20M%20%27%29%5Cin%20A%20%5C%2C%20%5B%5Ceta%20%3A%20%5Cdelta%20%5Cleftrightarrow%20%5Cdelta%27%5D "\Lambda (\hat M) \sim \Lambda (\hat M ')\in A \, [\eta : \delta \leftrightarrow \delta']")。根据定义，需要证明的是
    ![R : B \\sim B\'](https://latex.codecogs.com/svg.image?R%20%3A%20B%20%5Csim%20B%27 "R : B \sim B'")
    implies
    ![\[B / t\] \\hat M \\sim \[B\' / t\] \\hat M\' \\in A \\, \[\\eta \[ X \\longmapsto R\] : \\delta\[X \\longmapsto B\] \\leftrightarrow \\delta\'\[X \\longmapsto B\'\]\]](https://latex.codecogs.com/svg.image?%5BB%20%2F%20t%5D%20%5Chat%20M%20%5Csim%20%5BB%27%20%2F%20t%5D%20%5Chat%20M%27%20%5Cin%20A%20%5C%2C%20%5B%5Ceta%20%5B%20X%20%5Clongmapsto%20R%5D%20%3A%20%5Cdelta%5BX%20%5Clongmapsto%20B%5D%20%5Cleftrightarrow%20%5Cdelta%27%5BX%20%5Clongmapsto%20B%27%5D%5D "[B / t] \hat M \sim [B' / t] \hat M' \in A \, [\eta [ X \longmapsto R] : \delta[X \longmapsto B] \leftrightarrow \delta'[X \longmapsto B']]")

    ![\\eta \[X \\longmapsto R\] : \\delta \[X \\longmapsto B\] \\leftrightarrow \\delta\' \[X \\longmapsto B\'\]](https://latex.codecogs.com/svg.image?%5Ceta%20%5BX%20%5Clongmapsto%20R%5D%20%3A%20%5Cdelta%20%5BX%20%5Clongmapsto%20B%5D%20%5Cleftrightarrow%20%5Cdelta%27%20%5BX%20%5Clongmapsto%20B%27%5D "\eta [X \longmapsto R] : \delta [X \longmapsto B] \leftrightarrow \delta' [X \longmapsto B']")
    也是一个 candidate assignment 所以说上面这个直接由 induction 得到。

2.  当 ![M](https://latex.codecogs.com/svg.image?M "M") 形为
    ![\\Gamma \\vdash\_{\\Delta}\\mathsf{Ap}(M) : \[B / X\]A](https://latex.codecogs.com/svg.image?%5CGamma%20%5Cvdash_%7B%5CDelta%7D%5Cmathsf%7BAp%7D%28M%29%20%3A%20%5BB%20%2F%20X%5DA "\Gamma \vdash_{\Delta}\mathsf{Ap}(M) : [B / X]A")，premises
    为
    ![\\Gamma\\vdash\_{\\Delta} M : \\forall (X.A)](https://latex.codecogs.com/svg.image?%5CGamma%5Cvdash_%7B%5CDelta%7D%20M%20%3A%20%5Cforall%20%28X.A%29 "\Gamma\vdash_{\Delta} M : \forall (X.A)")
    且
    ![\\Delta \\vdash B](https://latex.codecogs.com/svg.image?%5CDelta%20%5Cvdash%20B "\Delta \vdash B")。

    证明
    ![\\mathsf{Ap}(\\hat M) \\sim \\mathsf{Ap}(\\hat M\') \\in \[B/X\]A\\, \[\\eta : \\delta \\leftrightarrow \\delta\'\]](https://latex.codecogs.com/svg.image?%5Cmathsf%7BAp%7D%28%5Chat%20M%29%20%5Csim%20%5Cmathsf%7BAp%7D%28%5Chat%20M%27%29%20%5Cin%20%5BB%2FX%5DA%5C%2C%20%5B%5Ceta%20%3A%20%5Cdelta%20%5Cleftrightarrow%20%5Cdelta%27%5D "\mathsf{Ap}(\hat M) \sim \mathsf{Ap}(\hat M') \in [B/X]A\, [\eta : \delta \leftrightarrow \delta']")。

    使用 Lemma 4 上面的相当于证明

    ![\\mathsf{Ap}(\\hat M) \\sim \\mathsf{Ap}(\\hat M\') \\in A \\, \[\\eta \[X \\longmapsto \\\_ \\sim \\\_\] : \\delta \[X \\longmapsto \\hat\\delta B\] \\leftrightarrow \\delta\' \[X \\longmapsto \\hat\\delta\' B\]\]](https://latex.codecogs.com/svg.image?%5Cmathsf%7BAp%7D%28%5Chat%20M%29%20%5Csim%20%5Cmathsf%7BAp%7D%28%5Chat%20M%27%29%20%5Cin%20A%20%5C%2C%20%5B%5Ceta%20%5BX%20%5Clongmapsto%20%5C_%20%5Csim%20%5C_%5D%20%3A%20%5Cdelta%20%5BX%20%5Clongmapsto%20%5Chat%5Cdelta%20B%5D%20%5Cleftrightarrow%20%5Cdelta%27%20%5BX%20%5Clongmapsto%20%5Chat%5Cdelta%27%20B%5D%5D "\mathsf{Ap}(\hat M) \sim \mathsf{Ap}(\hat M') \in A \, [\eta [X \longmapsto \_ \sim \_] : \delta [X \longmapsto \hat\delta B] \leftrightarrow \delta' [X \longmapsto \hat\delta' B]]")

    从 premise 上得到 Induction Hypothesis，可以知道
    ![\\hat M \\longmapsto \^\* \\Lambda(N)](https://latex.codecogs.com/svg.image?%5Chat%20M%20%5Clongmapsto%20%5E%2A%20%5CLambda%28N%29 "\hat M \longmapsto ^* \Lambda(N)")
    以及
    ![\\hat M\' \\longmapsto \^\* \\Lambda(N\')](https://latex.codecogs.com/svg.image?%5Chat%20M%27%20%5Clongmapsto%20%5E%2A%20%5CLambda%28N%27%29 "\hat M' \longmapsto ^* \Lambda(N')")。以及
    ![R : C \\sim C\'](https://latex.codecogs.com/svg.image?R%20%3A%20C%20%5Csim%20C%27 "R : C \sim C'")
    implies
    ![\[C / t\] N \\sim \[C\' / t\] N\' \\in A\\, \[\\eta \[X \\longmapsto R\] : \\delta \[X \\longmapsto C\] \\leftrightarrow \\delta\'\[X \\longmapsto C\'\]\]](https://latex.codecogs.com/svg.image?%5BC%20%2F%20t%5D%20N%20%5Csim%20%5BC%27%20%2F%20t%5D%20N%27%20%5Cin%20A%5C%2C%20%5B%5Ceta%20%5BX%20%5Clongmapsto%20R%5D%20%3A%20%5Cdelta%20%5BX%20%5Clongmapsto%20C%5D%20%5Cleftrightarrow%20%5Cdelta%27%5BX%20%5Clongmapsto%20C%27%5D%5D "[C / t] N \sim [C' / t] N' \in A\, [\eta [X \longmapsto R] : \delta [X \longmapsto C] \leftrightarrow \delta'[X \longmapsto C']]")。

    根据
    ![\\hat M \\longmapsto \^\* \\Lambda (N)](https://latex.codecogs.com/svg.image?%5Chat%20M%20%5Clongmapsto%20%5E%2A%20%5CLambda%20%28N%29 "\hat M \longmapsto ^* \Lambda (N)")
    可以知道
    ![\\mathsf{Ap}(\\hat M) \\longmapsto\^\* \[\\hat \\delta B / t\] N](https://latex.codecogs.com/svg.image?%5Cmathsf%7BAp%7D%28%5Chat%20M%29%20%5Clongmapsto%5E%2A%20%5B%5Chat%20%5Cdelta%20B%20%2F%20t%5D%20N "\mathsf{Ap}(\hat M) \longmapsto^* [\hat \delta B / t] N")
    以及
    ![\\mathsf{Ap}(\\hat M\') \\longmapsto\^\* \[\\hat \\delta\' B / t\] N\'](https://latex.codecogs.com/svg.image?%5Cmathsf%7BAp%7D%28%5Chat%20M%27%29%20%5Clongmapsto%5E%2A%20%5B%5Chat%20%5Cdelta%27%20B%20%2F%20t%5D%20N%27 "\mathsf{Ap}(\hat M') \longmapsto^* [\hat \delta' B / t] N'")。因为
    ![\\\_ \\sim \\\_](https://latex.codecogs.com/svg.image?%5C_%20%5Csim%20%5C_ "\_ \sim \_")
    是 parametricity candidate，所以根据上面的
    ![R : C \\sim C\'](https://latex.codecogs.com/svg.image?R%20%3A%20C%20%5Csim%20C%27 "R : C \sim C'")
    implies... 能够得到

    ![\[\\hat\\delta B / t\] N \\sim \[\\hat\\delta\' B / t\] N\' \\in A \\, \[\\eta \[X \\longmapsto R\] : \\delta \[X \\longmapsto \\hat \\delta B\] \\leftrightarrow \\delta\' \[X \\longmapsto \\hat \\delta\' B \]\]](https://latex.codecogs.com/svg.image?%5B%5Chat%5Cdelta%20B%20%2F%20t%5D%20N%20%5Csim%20%5B%5Chat%5Cdelta%27%20B%20%2F%20t%5D%20N%27%20%5Cin%20A%20%5C%2C%20%5B%5Ceta%20%5BX%20%5Clongmapsto%20R%5D%20%3A%20%5Cdelta%20%5BX%20%5Clongmapsto%20%5Chat%20%5Cdelta%20B%5D%20%5Cleftrightarrow%20%5Cdelta%27%20%5BX%20%5Clongmapsto%20%5Chat%20%5Cdelta%27%20B%20%5D%5D "[\hat\delta B / t] N \sim [\hat\delta' B / t] N' \in A \, [\eta [X \longmapsto R] : \delta [X \longmapsto \hat \delta B] \leftrightarrow \delta' [X \longmapsto \hat \delta' B ]]")

    使用 head expansion 就能够得到想要的结果了。

其实到这里就差不多结束了。上面的当然可以衍生到 Nat 和 Co-Nat
的类型上面。但说实话 System F 的表达能力都已经足够直接定义 Nat 和 Co-Nat
了，何必要再自己多加 rules 呢。 但是 Robert Harper 没有点出的是
Parametricity 是如何称为免费定理的，也就是类型为
![\\forall X ( X \\to X)](https://latex.codecogs.com/svg.image?%5Cforall%20X%20%28%20X%20%5Cto%20X%29 "\forall X ( X \to X)")
的 Term 只能是
![\\Lambda (\\lambda (x.x))](https://latex.codecogs.com/svg.image?%5CLambda%20%28%5Clambda%20%28x.x%29%29 "\Lambda (\lambda (x.x))")
以及
![\\forall X (X \\to X \\to X)](https://latex.codecogs.com/svg.image?%5Cforall%20X%20%28X%20%5Cto%20X%20%5Cto%20X%29 "\forall X (X \to X \to X)")
的 Term 只能是
![\\Lambda (\\lambda (x. \\lambda(y.x)))](https://latex.codecogs.com/svg.image?%5CLambda%20%28%5Clambda%20%28x.%20%5Clambda%28y.x%29%29%29 "\Lambda (\lambda (x. \lambda(y.x)))")
或者是
![\\Lambda (\\lambda (x . \\lambda(y.y)))](https://latex.codecogs.com/svg.image?%5CLambda%20%28%5Clambda%20%28x%20.%20%5Clambda%28y.y%29%29%29 "\Lambda (\lambda (x . \lambda(y.y)))")
呢。 并且对于这个 ZZC
的必要性也没有很好的解释。我觉得接下来可以看的文献应该有：

1.  Neelakantan R. Krishnaswami and Derek Dreyer. Internalizing
    Relational Parametricity in the Extensional Calculus of
    Constructions
    -   用于解释 ZZC
2.  <https://www.cs.cmu.edu/~fp/courses/15814-f21/schedule.html>
    -   Frank Pfennning 的 lecture
        notes。只不过记号都不一样......有可能得需要从头看。但是 fp
        确实是很好地介绍了 parametricity，我以前看过，但是我全部忘记了。
