---
layout: post
title: "Kripke Style Logical Relation for Normalization"
date: 2025-10-21
---

这里介绍的是 kripke-stype 的 normalization
。唯一的问题在于，你看完了这个文章之后，去看 kripke
的原论文，大概率是看不懂的。PL
理论总是会有这样重复造轮子的事情出现。准确的说是重新发现已经发现的事物。

我们先是介绍一下文章的技术细节，然后再来讨论哪里是 kripke-style 的。

首先我们在前面的 Lambda Calculus 加上
![\\beta](https://latex.codecogs.com/svg.image?%5Cbeta "\beta")
Reduction 。使得一些 term 变得不是 final 了

![\\frac{M\_{2} \\to \_{\\beta} M\_{2} \'}{ \\mathsf{ap}(M\_{1} ; M\_{2}) \\to \_{\\beta}\\mathsf{ap}(M\_{1} ; M \_{2} \' )}](https://latex.codecogs.com/svg.image?%5Cfrac%7BM_%7B2%7D%20%5Cto%20_%7B%5Cbeta%7D%20M_%7B2%7D%20%27%7D%7B%20%5Cmathsf%7Bap%7D%28M_%7B1%7D%20%3B%20M_%7B2%7D%29%20%5Cto%20_%7B%5Cbeta%7D%5Cmathsf%7Bap%7D%28M_%7B1%7D%20%3B%20M%20_%7B2%7D%20%27%20%29%7D "\frac{M_{2} \to _{\beta} M_{2} '}{ \mathsf{ap}(M_{1} ; M_{2}) \to _{\beta}\mathsf{ap}(M_{1} ; M _{2} ' )}")

剩下的就不写了，反正就是比 Weak Head Reduction 还要多一些 Reduction
。比如说原本的 pair 可以叫做 lazy pair ，现在的 pair
就是我们一般认识之中的 pair 了。

我们称呼 ![M](https://latex.codecogs.com/svg.image?M "M") 是 beta
不可约的，当不存在
![M\'](https://latex.codecogs.com/svg.image?M%27 "M'") 使得
![M \\to \_{\\beta} M\'](https://latex.codecogs.com/svg.image?M%20%5Cto%20_%7B%5Cbeta%7D%20M%27 "M \to _{\beta} M'")
。若是对于 ![M](https://latex.codecogs.com/svg.image?M "M") 来说存在一个
reduction 路线
![M \\to \^\* M \'](https://latex.codecogs.com/svg.image?M%20%5Cto%20%5E%2A%20M%20%27 "M \to ^* M '")
并且 ![M\'](https://latex.codecogs.com/svg.image?M%27 "M'") 是 beta
不可约的。我们称呼 ![M](https://latex.codecogs.com/svg.image?M "M")
是（弱） normalizable 的，记为
![\\mathsf{norm}\_{\\beta}(M)](https://latex.codecogs.com/svg.image?%5Cmathsf%7Bnorm%7D_%7B%5Cbeta%7D%28M%29 "\mathsf{norm}_{\beta}(M)")
。

我们需要证明的是：

定理 1 If
![\\Gamma \\vdash M : A](https://latex.codecogs.com/svg.image?%5CGamma%20%5Cvdash%20M%20%3A%20A "\Gamma \vdash M : A")
then
![\\mathsf{norm} \_{\\beta}(M)](https://latex.codecogs.com/svg.image?%5Cmathsf%7Bnorm%7D%20_%7B%5Cbeta%7D%28M%29 "\mathsf{norm} _{\beta}(M)")

前文没有区分 Closed Term ，这是因为对于任意的 Term ，无论是 Closed 还是
Open 的，都是 normalizable 的。我们引入 Hereditary Normalizable 记为
![\\mathsf{HN}\_{A}\^{\\Delta}(M)](https://latex.codecogs.com/svg.image?%5Cmathsf%7BHN%7D_%7BA%7D%5E%7B%5CDelta%7D%28M%29 "\mathsf{HN}_{A}^{\Delta}(M)")
指的是
![\\Delta \\vdash M : A](https://latex.codecogs.com/svg.image?%5CDelta%20%5Cvdash%20M%20%3A%20A "\Delta \vdash M : A")
是 Hereditary Normalizable 的。

我们需要引入 Context 的 ordering ，称
![\\Delta\' \\le \\Delta](https://latex.codecogs.com/svg.image?%5CDelta%27%20%5Cle%20%5CDelta "\Delta' \le \Delta")
if
![\\Delta \\vdash x : A](https://latex.codecogs.com/svg.image?%5CDelta%20%5Cvdash%20x%20%3A%20A "\Delta \vdash x : A")
implies
![\\Delta\' \\vdash x : A](https://latex.codecogs.com/svg.image?%5CDelta%27%20%5Cvdash%20x%20%3A%20A "\Delta' \vdash x : A")
这里的意思应该是说，![\\Delta\'](https://latex.codecogs.com/svg.image?%5CDelta%27 "\Delta'")
是弱于
![\\Delta](https://latex.codecogs.com/svg.image?%5CDelta "\Delta")
的。比如说
![\\Gamma  , x : A](https://latex.codecogs.com/svg.image?%5CGamma%20%20%2C%20x%20%3A%20A "\Gamma  , x : A")
就是弱于
![\\Gamma](https://latex.codecogs.com/svg.image?%5CGamma "\Gamma")
的。HN 的定义如下：

1.  ![\\mathsf{HN}\_{1}\^{\\Delta}(M) := \\mathsf{norm}\_{\\beta}(M)](https://latex.codecogs.com/svg.image?%5Cmathsf%7BHN%7D_%7B1%7D%5E%7B%5CDelta%7D%28M%29%20%3A%3D%20%5Cmathsf%7Bnorm%7D_%7B%5Cbeta%7D%28M%29 "\mathsf{HN}_{1}^{\Delta}(M) := \mathsf{norm}_{\beta}(M)")
2.  ![\\mathsf{HN}\_{\\mathsf{ans}}\^{\\Delta}(M) := \\mathsf{norm}\_{\\beta}(M)](https://latex.codecogs.com/svg.image?%5Cmathsf%7BHN%7D_%7B%5Cmathsf%7Bans%7D%7D%5E%7B%5CDelta%7D%28M%29%20%3A%3D%20%5Cmathsf%7Bnorm%7D_%7B%5Cbeta%7D%28M%29 "\mathsf{HN}_{\mathsf{ans}}^{\Delta}(M) := \mathsf{norm}_{\beta}(M)")
3.  ![\\mathsf{HN}\_{A_1 \\times A_2}\^{\\Delta}(M) := \\mathsf{HN}\_{A\_{1}} \^{\\Delta}(M \\cdot 1) \\land \\mathsf{HN}\_{A\_{2}}\^{\\Delta} (M\\cdot 2)](https://latex.codecogs.com/svg.image?%5Cmathsf%7BHN%7D_%7BA_1%20%5Ctimes%20A_2%7D%5E%7B%5CDelta%7D%28M%29%20%3A%3D%20%5Cmathsf%7BHN%7D_%7BA_%7B1%7D%7D%20%5E%7B%5CDelta%7D%28M%20%5Ccdot%201%29%20%5Cland%20%5Cmathsf%7BHN%7D_%7BA_%7B2%7D%7D%5E%7B%5CDelta%7D%20%28M%5Ccdot%202%29 "\mathsf{HN}_{A_1 \times A_2}^{\Delta}(M) := \mathsf{HN}_{A_{1}} ^{\Delta}(M \cdot 1) \land \mathsf{HN}_{A_{2}}^{\Delta} (M\cdot 2)")
4.  ![\\mathsf{HN}\_{A_1 \\to A_2} \^{\\Delta}(M) := \\forall \\Delta\' \\le \\Delta, \\mathsf{HN}\_{A\_{1}}\^{\\Delta\'} (M\_{1}) \\implies \\mathsf{HN}\_{A\_{2}}\^{\\Delta\'}(\\mathsf{ap}(M; M\_{1}))](https://latex.codecogs.com/svg.image?%5Cmathsf%7BHN%7D_%7BA_1%20%5Cto%20A_2%7D%20%5E%7B%5CDelta%7D%28M%29%20%3A%3D%20%5Cforall%20%5CDelta%27%20%5Cle%20%5CDelta%2C%20%5Cmathsf%7BHN%7D_%7BA_%7B1%7D%7D%5E%7B%5CDelta%27%7D%20%28M_%7B1%7D%29%20%5Cimplies%20%5Cmathsf%7BHN%7D_%7BA_%7B2%7D%7D%5E%7B%5CDelta%27%7D%28%5Cmathsf%7Bap%7D%28M%3B%20M_%7B1%7D%29%29 "\mathsf{HN}_{A_1 \to A_2} ^{\Delta}(M) := \forall \Delta' \le \Delta, \mathsf{HN}_{A_{1}}^{\Delta'} (M_{1}) \implies \mathsf{HN}_{A_{2}}^{\Delta'}(\mathsf{ap}(M; M_{1}))")
5.  (notice)
    ![\\mathsf{HN}\^{\\Delta}\_{\\Gamma}:= \\forall x : A \\in \\Gamma , \\mathsf{HN}\_{A}\^{\\Delta}(\\gamma x)](https://latex.codecogs.com/svg.image?%5Cmathsf%7BHN%7D%5E%7B%5CDelta%7D_%7B%5CGamma%7D%3A%3D%20%5Cforall%20x%20%3A%20A%20%5Cin%20%5CGamma%20%2C%20%5Cmathsf%7BHN%7D_%7BA%7D%5E%7B%5CDelta%7D%28%5Cgamma%20x%29 "\mathsf{HN}^{\Delta}_{\Gamma}:= \forall x : A \in \Gamma , \mathsf{HN}_{A}^{\Delta}(\gamma x)")

> 需要注意的是，![\\mathsf{HN}\_{A}\^{\\Delta}(M)](https://latex.codecogs.com/svg.image?%5Cmathsf%7BHN%7D_%7BA%7D%5E%7B%5CDelta%7D%28M%29 "\mathsf{HN}_{A}^{\Delta}(M)")
> 可以得到
> ![\\mathsf{norm}\_{\\beta}(M)](https://latex.codecogs.com/svg.image?%5Cmathsf%7Bnorm%7D_%7B%5Cbeta%7D%28M%29 "\mathsf{norm}_{\beta}(M)")
> ，但不是立即就能得到。

我们最终应当证明的是

定理 4
![\\Gamma \\vdash M :A](https://latex.codecogs.com/svg.image?%5CGamma%20%5Cvdash%20M%20%3AA "\Gamma \vdash M :A")
then for all
![\\Delta](https://latex.codecogs.com/svg.image?%5CDelta "\Delta") if
![\\mathsf{HN}\_{\\Gamma}\^{\\Delta}(\\gamma)](https://latex.codecogs.com/svg.image?%5Cmathsf%7BHN%7D_%7B%5CGamma%7D%5E%7B%5CDelta%7D%28%5Cgamma%29 "\mathsf{HN}_{\Gamma}^{\Delta}(\gamma)")
then
![\\mathsf{HN}\_{A}\^{\\Delta}(\\hat \\gamma M)](https://latex.codecogs.com/svg.image?%5Cmathsf%7BHN%7D_%7BA%7D%5E%7B%5CDelta%7D%28%5Chat%20%5Cgamma%20M%29 "\mathsf{HN}_{A}^{\Delta}(\hat \gamma M)")

为了证明这个定理我们需要两个 lemma

lemma 2 (anti monotonicity)
![\\mathsf{HN}\_{A}\^{\\Delta}(M)](https://latex.codecogs.com/svg.image?%5Cmathsf%7BHN%7D_%7BA%7D%5E%7B%5CDelta%7D%28M%29 "\mathsf{HN}_{A}^{\Delta}(M)")
and
![\\Delta\' \\le \\Delta](https://latex.codecogs.com/svg.image?%5CDelta%27%20%5Cle%20%5CDelta "\Delta' \le \Delta")
then
![\\mathsf{HN}\_{A}\^{\\Delta\'}(M)](https://latex.codecogs.com/svg.image?%5Cmathsf%7BHN%7D_%7BA%7D%5E%7B%5CDelta%27%7D%28M%29 "\mathsf{HN}_{A}^{\Delta'}(M)").
lemma 3 (head expansion)
![M \' \\mapsto \_{\\beta} M](https://latex.codecogs.com/svg.image?M%20%27%20%5Cmapsto%20_%7B%5Cbeta%7D%20M "M ' \mapsto _{\beta} M")
and
![\\mathsf{HN}\_{A}\^{\\Delta}(M)](https://latex.codecogs.com/svg.image?%5Cmathsf%7BHN%7D_%7BA%7D%5E%7B%5CDelta%7D%28M%29 "\mathsf{HN}_{A}^{\Delta}(M)"),
then
![\\mathsf{HN}\_{A}\^{\\Delta}(M\')](https://latex.codecogs.com/svg.image?%5Cmathsf%7BHN%7D_%7BA%7D%5E%7B%5CDelta%7D%28M%27%29 "\mathsf{HN}_{A}^{\Delta}(M')").

lemma 2 证明：（固定
![\\Delta](https://latex.codecogs.com/svg.image?%5CDelta "\Delta")和
![\\Delta\'](https://latex.codecogs.com/svg.image?%5CDelta%27 "\Delta'")）
当 ![A](https://latex.codecogs.com/svg.image?A "A") 为 answer 或者是
unit 类型的时候是显然的。确实是显然的。 当
![A](https://latex.codecogs.com/svg.image?A "A") 为
![A_1 \\times A_2](https://latex.codecogs.com/svg.image?A_1%20%5Ctimes%20A_2 "A_1 \times A_2")
，根据 induction hypothesis 当
![A](https://latex.codecogs.com/svg.image?A "A") 为
![A_1 \\to A_2](https://latex.codecogs.com/svg.image?A_1%20%5Cto%20A_2 "A_1 \to A_2")
，我们需要证明对于任意的
![\\Delta\'\' \\le \\Delta\'](https://latex.codecogs.com/svg.image?%5CDelta%27%27%20%5Cle%20%5CDelta%27 "\Delta'' \le \Delta'")
，有 ![M_1](https://latex.codecogs.com/svg.image?M_1 "M_1") 的 HN
，需要的到
![\\mathsf{ap}(M; M_1)](https://latex.codecogs.com/svg.image?%5Cmathsf%7Bap%7D%28M%3B%20M_1%29 "\mathsf{ap}(M; M_1)")
的 HN ，因为
![\\Delta\'\' \\le \\Delta\' \\le \\Delta](https://latex.codecogs.com/svg.image?%5CDelta%27%27%20%5Cle%20%5CDelta%27%20%5Cle%20%5CDelta "\Delta'' \le \Delta' \le \Delta")
于是可以根据
![\\mathsf{HN}\_{A}\^{\\Delta}(M)](https://latex.codecogs.com/svg.image?%5Cmathsf%7BHN%7D_%7BA%7D%5E%7B%5CDelta%7D%28M%29 "\mathsf{HN}_{A}^{\Delta}(M)")
立刻得到
![\\mathsf{ap}(M; M_1)](https://latex.codecogs.com/svg.image?%5Cmathsf%7Bap%7D%28M%3B%20M_1%29 "\mathsf{ap}(M; M_1)")
的 HN。

lemma 3 证明： I mean this is quite obvious.

证明定理 4：当 ![M](https://latex.codecogs.com/svg.image?M "M") 为

-   ![\\mathbf{Var}](https://latex.codecogs.com/svg.image?%5Cmathbf%7BVar%7D "\mathbf{Var}")
    时，![\\hat M := \\hat \\gamma M = \\gamma x](https://latex.codecogs.com/svg.image?%5Chat%20M%20%3A%3D%20%5Chat%20%5Cgamma%20M%20%3D%20%5Cgamma%20x "\hat M := \hat \gamma M = \gamma x")
    ，因为
    ![\\mathsf{HN}(\\gamma)](https://latex.codecogs.com/svg.image?%5Cmathsf%7BHN%7D%28%5Cgamma%29 "\mathsf{HN}(\gamma)")
    ，立刻有
    ![\\mathsf{HN}(\\hat M)](https://latex.codecogs.com/svg.image?%5Cmathsf%7BHN%7D%28%5Chat%20M%29 "\mathsf{HN}(\hat M)")
-   ![\\mathbf{App}](https://latex.codecogs.com/svg.image?%5Cmathbf%7BApp%7D "\mathbf{App}")
    时，![\\hat M  = \\mathsf{ap}(\\hat M ; \\hat M_1)](https://latex.codecogs.com/svg.image?%5Chat%20M%20%20%3D%20%5Cmathsf%7Bap%7D%28%5Chat%20M%20%3B%20%5Chat%20M_1%29 "\hat M  = \mathsf{ap}(\hat M ; \hat M_1)")
    ，需要证明
    ![\\mathsf{HN}\_{A_2}\^{\\Delta}(\\mathsf{ap}(\\hat M ;\\hat M_1))](https://latex.codecogs.com/svg.image?%5Cmathsf%7BHN%7D_%7BA_2%7D%5E%7B%5CDelta%7D%28%5Cmathsf%7Bap%7D%28%5Chat%20M%20%3B%5Chat%20M_1%29%29 "\mathsf{HN}_{A_2}^{\Delta}(\mathsf{ap}(\hat M ;\hat M_1))")
    ；对
    ![\\hat M](https://latex.codecogs.com/svg.image?%5Chat%20M "\hat M")
    和
    ![\\hat M_1](https://latex.codecogs.com/svg.image?%5Chat%20M_1 "\hat M_1")
    递归（induction）得到
    ![\\mathsf{HN}\_{A_1 \\to A_2}(\\hat M)](https://latex.codecogs.com/svg.image?%5Cmathsf%7BHN%7D_%7BA_1%20%5Cto%20A_2%7D%28%5Chat%20M%29 "\mathsf{HN}_{A_1 \to A_2}(\hat M)")
    和
    ![\\mathsf{HN}\_{A_1}(\\hat M_1)](https://latex.codecogs.com/svg.image?%5Cmathsf%7BHN%7D_%7BA_1%7D%28%5Chat%20M_1%29 "\mathsf{HN}_{A_1}(\hat M_1)")
    ，根据 function type 的 HN 定义可以得到
    ![\\mathsf{HN}\_{A_2}\^{\\Delta}(\\mathsf{ap}(\\hat M ;\\hat M_1))](https://latex.codecogs.com/svg.image?%5Cmathsf%7BHN%7D_%7BA_2%7D%5E%7B%5CDelta%7D%28%5Cmathsf%7Bap%7D%28%5Chat%20M%20%3B%5Chat%20M_1%29%29 "\mathsf{HN}_{A_2}^{\Delta}(\mathsf{ap}(\hat M ;\hat M_1))")
    。 当然需要注意到这里的
    ![\\hat  M](https://latex.codecogs.com/svg.image?%5Chat%20%20M "\hat  M")
    实际上是一个 weakened 的
    ![\\gamma](https://latex.codecogs.com/svg.image?%5Cgamma "\gamma")
    作用于 ![M](https://latex.codecogs.com/svg.image?M "M") 的。原本的
    ![\\Gamma \\vdash \\gamma : \\Delta](https://latex.codecogs.com/svg.image?%5CGamma%20%5Cvdash%20%5Cgamma%20%3A%20%5CDelta "\Gamma \vdash \gamma : \Delta")
    将
    ![\\Gamma](https://latex.codecogs.com/svg.image?%5CGamma "\Gamma")
    变量射到
    ![\\Delta](https://latex.codecogs.com/svg.image?%5CDelta "\Delta")
    的 Term ，而 weakened 之后是
    ![\\Gamma , x :A \\vdash \\gamma : \\Delta , x : A](https://latex.codecogs.com/svg.image?%5CGamma%20%2C%20x%20%3AA%20%5Cvdash%20%5Cgamma%20%3A%20%5CDelta%20%2C%20x%20%3A%20A "\Gamma , x :A \vdash \gamma : \Delta , x : A")。
-   ![\\mathbf{Lam}](https://latex.codecogs.com/svg.image?%5Cmathbf%7BLam%7D "\mathbf{Lam}")
    时，![\\hat M = \\lambda (x . \\hat M)](https://latex.codecogs.com/svg.image?%5Chat%20M%20%3D%20%5Clambda%20%28x%20.%20%5Chat%20M%29 "\hat M = \lambda (x . \hat M)")
    ，证明
    ![\\mathsf{HN}\^{\\Delta}\_{A_1 \\to A_2} (\\lambda (x . \\hat M))](https://latex.codecogs.com/svg.image?%5Cmathsf%7BHN%7D%5E%7B%5CDelta%7D_%7BA_1%20%5Cto%20A_2%7D%20%28%5Clambda%20%28x%20.%20%5Chat%20M%29%29 "\mathsf{HN}^{\Delta}_{A_1 \to A_2} (\lambda (x . \hat M))")；给定了
    ![\\Delta\' \\le \\Delta](https://latex.codecogs.com/svg.image?%5CDelta%27%20%5Cle%20%5CDelta "\Delta' \le \Delta")
    以及
    ![\\mathsf{HN}\^{\\Delta\'}\_{A_1}(M\_{1})](https://latex.codecogs.com/svg.image?%5Cmathsf%7BHN%7D%5E%7B%5CDelta%27%7D_%7BA_1%7D%28M_%7B1%7D%29 "\mathsf{HN}^{\Delta'}_{A_1}(M_{1})")
    需要证明
    ![\\mathsf{HN}\^{\\Delta\'}(\\mathsf{ap}(\\lambda (x. \\hat M) ; M_1))](https://latex.codecogs.com/svg.image?%5Cmathsf%7BHN%7D%5E%7B%5CDelta%27%7D%28%5Cmathsf%7Bap%7D%28%5Clambda%20%28x.%20%5Chat%20M%29%20%3B%20M_1%29%29 "\mathsf{HN}^{\Delta'}(\mathsf{ap}(\lambda (x. \hat M) ; M_1))")。可以在
    ![\\gamma](https://latex.codecogs.com/svg.image?%5Cgamma "\gamma")
    上做某种 weakening 由 Lemma 2 Anti Monotonicity 得到
    ![\\mathsf{HN}\^{\\Delta\'}\_{\\Gamma}(\\gamma)](https://latex.codecogs.com/svg.image?%5Cmathsf%7BHN%7D%5E%7B%5CDelta%27%7D_%7B%5CGamma%7D%28%5Cgamma%29 "\mathsf{HN}^{\Delta'}_{\Gamma}(\gamma)")。
    ![M](https://latex.codecogs.com/svg.image?M "M") 由
    ![\\gamma](https://latex.codecogs.com/svg.image?%5Cgamma "\gamma")
    的 weakened 的结果射到
    ![\\hat M](https://latex.codecogs.com/svg.image?%5Chat%20M "\hat M")
    ，随后
    ![\[M\_{1} / x\]](https://latex.codecogs.com/svg.image?%5BM_%7B1%7D%20%2F%20x%5D "[M_{1} / x]")
    也是一种 substi ，射到
    ![\[M_1 / x\] \\hat M](https://latex.codecogs.com/svg.image?%5BM_1%20%2F%20x%5D%20%5Chat%20M "[M_1 / x] \hat M")，他也是有
    HN 的，这两个 substi 的复合
    ![\\gamma \[x \\mapsto M_1\]](https://latex.codecogs.com/svg.image?%5Cgamma%20%5Bx%20%5Cmapsto%20M_1%5D "\gamma [x \mapsto M_1]")
    也是有 HN 的，于是递归可以得到
    ![\[M_1 / x\] \\hat M](https://latex.codecogs.com/svg.image?%5BM_1%20%2F%20x%5D%20%5Chat%20M "[M_1 / x] \hat M")
    的 HN 。 再使用 Head Expansion 就能有
    ![\\mathsf{ap}(\\lambda (x. \\hat M); M_1)](https://latex.codecogs.com/svg.image?%5Cmathsf%7Bap%7D%28%5Clambda%20%28x.%20%5Chat%20M%29%3B%20M_1%29 "\mathsf{ap}(\lambda (x. \hat M); M_1)")
    的 HN 了。
-   ![\\mathbf{Pair}](https://latex.codecogs.com/svg.image?%5Cmathbf%7BPair%7D "\mathbf{Pair}")
    我觉得直接递归不就完了，这有什么？

注意我们还不能得到定理 1 ，对于
![\\Gamma \\vdash M : A](https://latex.codecogs.com/svg.image?%5CGamma%20%5Cvdash%20M%20%3A%20A "\Gamma \vdash M : A")
有
![\\mathsf{HN}\_{A}\^{\\Gamma}(M)](https://latex.codecogs.com/svg.image?%5Cmathsf%7BHN%7D_%7BA%7D%5E%7B%5CGamma%7D%28M%29 "\mathsf{HN}_{A}^{\Gamma}(M)")
我们能够得到，存在一个
![M\'](https://latex.codecogs.com/svg.image?M%27 "M'") 使得
![M\'](https://latex.codecogs.com/svg.image?M%27 "M'")
是不可约的，并且有
![M \\to \_{\\beta} M\'](https://latex.codecogs.com/svg.image?M%20%5Cto%20_%7B%5Cbeta%7D%20M%27 "M \to _{\beta} M'")
吗？其还是不太能的。当 ![A](https://latex.codecogs.com/svg.image?A "A")
是
![\\mathsf{ans}](https://latex.codecogs.com/svg.image?%5Cmathsf%7Bans%7D "\mathsf{ans}")
或是
![\\mathsf{unit}](https://latex.codecogs.com/svg.image?%5Cmathsf%7Bunit%7D "\mathsf{unit}")
的时候，根据定义 norm 是有的，但是对于复合类型其实是没有的。

今天就到这里了，累了，接下来会介绍 neutral terms

Normalizably neutral terms are needed to prove that for theorem 1.

It is written as
![\\mathsf{N N}](https://latex.codecogs.com/svg.image?%5Cmathsf%7BN%20N%7D "\mathsf{N N}")
for neutral terms ![U](https://latex.codecogs.com/svg.image?U "U").
Neutral terms can be defined using CFG

![U : : = x \\mid U \\cdot 1 \\mid U \\cdot 2 \\mid \\mathsf{ap}(U  ; M).](https://latex.codecogs.com/svg.image?U%20%3A%20%3A%20%3D%20x%20%5Cmid%20U%20%5Ccdot%201%20%5Cmid%20U%20%5Ccdot%202%20%5Cmid%20%5Cmathsf%7Bap%7D%28U%20%20%3B%20M%29. "U : : = x \mid U \cdot 1 \mid U \cdot 2 \mid \mathsf{ap}(U  ; M).")

how can we understand what neutral means? Anyway, normalizably neutral
is noted as
![\\mathsf{N N}](https://latex.codecogs.com/svg.image?%5Cmathsf%7BN%20N%7D "\mathsf{N N}")
and is defined as

1.  VAR:
    ![\\mathsf{ N N}\^{\\Delta, x : A}\_{A}(x)](https://latex.codecogs.com/svg.image?%5Cmathsf%7B%20N%20N%7D%5E%7B%5CDelta%2C%20x%20%3A%20A%7D_%7BA%7D%28x%29 "\mathsf{ N N}^{\Delta, x : A}_{A}(x)")
    is true
2.  FST: if
    ![\\mathsf{ N N} \_{A_1 \\times A_2}\^{\\Delta}(U)](https://latex.codecogs.com/svg.image?%5Cmathsf%7B%20N%20N%7D%20_%7BA_1%20%5Ctimes%20A_2%7D%5E%7B%5CDelta%7D%28U%29 "\mathsf{ N N} _{A_1 \times A_2}^{\Delta}(U)")
    then
    ![\\mathsf{ N N}\_{A\_{1}}\^{\\Delta}(U \\cdot 1)](https://latex.codecogs.com/svg.image?%5Cmathsf%7B%20N%20N%7D_%7BA_%7B1%7D%7D%5E%7B%5CDelta%7D%28U%20%5Ccdot%201%29 "\mathsf{ N N}_{A_{1}}^{\Delta}(U \cdot 1)")
3.  SND: similar to the one above
4.  APP: if
    ![\\mathsf{ N N}\_{A_1 \\to A_2}\^{\\Delta}(U)](https://latex.codecogs.com/svg.image?%5Cmathsf%7B%20N%20N%7D_%7BA_1%20%5Cto%20A_2%7D%5E%7B%5CDelta%7D%28U%29 "\mathsf{ N N}_{A_1 \to A_2}^{\Delta}(U)")
    and
    ![\\mathsf{norm}\_{\\beta}(M)](https://latex.codecogs.com/svg.image?%5Cmathsf%7Bnorm%7D_%7B%5Cbeta%7D%28M%29 "\mathsf{norm}_{\beta}(M)")
    then
    ![\\mathsf{ N N}\_{A_2}\^{\\Delta}(\\mathsf{ap}(U;M))](https://latex.codecogs.com/svg.image?%5Cmathsf%7B%20N%20N%7D_%7BA_2%7D%5E%7B%5CDelta%7D%28%5Cmathsf%7Bap%7D%28U%3BM%29%29 "\mathsf{ N N}_{A_2}^{\Delta}(\mathsf{ap}(U;M))")

lemma 4.5 if
![\\mathsf{ N N}\^{\\Delta}\_{A}(U)](https://latex.codecogs.com/svg.image?%5Cmathsf%7B%20N%20N%7D%5E%7B%5CDelta%7D_%7BA%7D%28U%29 "\mathsf{ N N}^{\Delta}_{A}(U)")
and
![\\Delta\' \\le \\Delta](https://latex.codecogs.com/svg.image?%5CDelta%27%20%5Cle%20%5CDelta "\Delta' \le \Delta")
then
![\\mathsf{ N N}\^{\\Delta\'}\_{A}(U)](https://latex.codecogs.com/svg.image?%5Cmathsf%7B%20N%20N%7D%5E%7B%5CDelta%27%7D_%7BA%7D%28U%29 "\mathsf{ N N}^{\Delta'}_{A}(U)").

lemma 5 (pas de deux)

1.  if
    ![\\mathsf{N N }\_{A}\^{\\Delta}(U)](https://latex.codecogs.com/svg.image?%5Cmathsf%7BN%20N%20%7D_%7BA%7D%5E%7B%5CDelta%7D%28U%29 "\mathsf{N N }_{A}^{\Delta}(U)")
    then
    ![\\mathsf{H N }\_{A}\^{\\Delta}(U)](https://latex.codecogs.com/svg.image?%5Cmathsf%7BH%20N%20%7D_%7BA%7D%5E%7B%5CDelta%7D%28U%29 "\mathsf{H N }_{A}^{\Delta}(U)").
2.  if
    ![\\mathsf{H N}\^{\\Delta}\_{A}(M)](https://latex.codecogs.com/svg.image?%5Cmathsf%7BH%20N%7D%5E%7B%5CDelta%7D_%7BA%7D%28M%29 "\mathsf{H N}^{\Delta}_{A}(M)")
    then
    ![\\mathsf{norm}\_{\\beta}(M)](https://latex.codecogs.com/svg.image?%5Cmathsf%7Bnorm%7D_%7B%5Cbeta%7D%28M%29 "\mathsf{norm}_{\beta}(M)")

Proof of lemma 4.5

To prove for
![\\mathsf{N N }\^{\\Delta\'}\_{A}(U)](https://latex.codecogs.com/svg.image?%5Cmathsf%7BN%20N%20%7D%5E%7B%5CDelta%27%7D_%7BA%7D%28U%29 "\mathsf{N N }^{\Delta'}_{A}(U)"),
cases on ![U](https://latex.codecogs.com/svg.image?U "U")

-   ![U](https://latex.codecogs.com/svg.image?U "U") is of form
    ![x](https://latex.codecogs.com/svg.image?x "x"), NN for
    ![U](https://latex.codecogs.com/svg.image?U "U") in context
    ![\\Delta\'](https://latex.codecogs.com/svg.image?%5CDelta%27 "\Delta'")
    is immediate
-   ![U](https://latex.codecogs.com/svg.image?U "U") is of form
    ![U_1 \\cdot 1](https://latex.codecogs.com/svg.image?U_1%20%5Ccdot%201 "U_1 \cdot 1"),
    induction on ![U_1](https://latex.codecogs.com/svg.image?U_1 "U_1")
-   ![U](https://latex.codecogs.com/svg.image?U "U") is of form
    ![U_2 \\cdot 2](https://latex.codecogs.com/svg.image?U_2%20%5Ccdot%202 "U_2 \cdot 2"),
    same as above
-   ![U](https://latex.codecogs.com/svg.image?U "U") is of form
    ![\\mathsf{ap}(U_1 ; M)](https://latex.codecogs.com/svg.image?%5Cmathsf%7Bap%7D%28U_1%20%3B%20M%29 "\mathsf{ap}(U_1 ; M)").
    We have
    ![\\mathsf{HN}](https://latex.codecogs.com/svg.image?%5Cmathsf%7BHN%7D "\mathsf{HN}")
    for ![M](https://latex.codecogs.com/svg.image?M "M") in context
    ![\\Delta](https://latex.codecogs.com/svg.image?%5CDelta "\Delta")
    and
    ![\\mathsf{N N}](https://latex.codecogs.com/svg.image?%5Cmathsf%7BN%20N%7D "\mathsf{N N}")
    for ![U_1](https://latex.codecogs.com/svg.image?U_1 "U_1") in
    context
    ![\\Delta](https://latex.codecogs.com/svg.image?%5CDelta "\Delta").
    For the former, we use lemma from yesterday, we have
    ![\\mathsf{HN}](https://latex.codecogs.com/svg.image?%5Cmathsf%7BHN%7D "\mathsf{HN}")
    for ![M](https://latex.codecogs.com/svg.image?M "M") in context
    ![\\Delta\'](https://latex.codecogs.com/svg.image?%5CDelta%27 "\Delta'").
    And induction on
    ![U_1](https://latex.codecogs.com/svg.image?U_1 "U_1") to get the
    ![\\mathsf{N N}](https://latex.codecogs.com/svg.image?%5Cmathsf%7BN%20N%7D "\mathsf{N N}").

Proof of lemma 5

inductions on types, prove 1 and 2 simultaneously:

-   ![A](https://latex.codecogs.com/svg.image?A "A") is atom type (which
    is
    ![\\mathsf{ans}](https://latex.codecogs.com/svg.image?%5Cmathsf%7Bans%7D "\mathsf{ans}")
    or ![1](https://latex.codecogs.com/svg.image?1 "1")).
    1.  if ![U](https://latex.codecogs.com/svg.image?U "U") is of atom
        type
        ![\\mathsf{asn}](https://latex.codecogs.com/svg.image?%5Cmathsf%7Basn%7D "\mathsf{asn}")
        or
        ![\\mathsf{1}](https://latex.codecogs.com/svg.image?%5Cmathsf%7B1%7D "\mathsf{1}").
        consider ![U](https://latex.codecogs.com/svg.image?U "U") of
        form
        ![\\mathsf{ap}(U; M)](https://latex.codecogs.com/svg.image?%5Cmathsf%7Bap%7D%28U%3B%20M%29 "\mathsf{ap}(U; M)").
        it is obvious that
        ![U](https://latex.codecogs.com/svg.image?U "U") is
        normalizable. then by definition
        ![U](https://latex.codecogs.com/svg.image?U "U") has
        ![\\mathsf{HN}](https://latex.codecogs.com/svg.image?%5Cmathsf%7BHN%7D "\mathsf{HN}").
    2.  this is by definition
-   ![A](https://latex.codecogs.com/svg.image?A "A") is product type, of
    form
    ![A_1 \\times A_2](https://latex.codecogs.com/svg.image?A_1%20%5Ctimes%20A_2 "A_1 \times A_2").
    1.  by definition of
        ![\\mathsf{N N}](https://latex.codecogs.com/svg.image?%5Cmathsf%7BN%20N%7D "\mathsf{N N}")
        on
        ![U \\cdot 1](https://latex.codecogs.com/svg.image?U%20%5Ccdot%201 "U \cdot 1")
        and
        ![U \\cdot 2](https://latex.codecogs.com/svg.image?U%20%5Ccdot%202 "U \cdot 2"),
        we have that
        ![\\mathsf{ N N}](https://latex.codecogs.com/svg.image?%5Cmathsf%7B%20N%20N%7D "\mathsf{ N N}")
        for
        ![U \\cdot 1](https://latex.codecogs.com/svg.image?U%20%5Ccdot%201 "U \cdot 1")
        and
        ![U \\cdot 2](https://latex.codecogs.com/svg.image?U%20%5Ccdot%202 "U \cdot 2").
        By induction, we have
        ![\\mathsf{HN}](https://latex.codecogs.com/svg.image?%5Cmathsf%7BHN%7D "\mathsf{HN}")
        for both terms. And thus by definition of
        ![\\mathsf{HN}](https://latex.codecogs.com/svg.image?%5Cmathsf%7BHN%7D "\mathsf{HN}")
        for product type, we have
        ![\\mathsf{HN}](https://latex.codecogs.com/svg.image?%5Cmathsf%7BHN%7D "\mathsf{HN}")
        for ![U](https://latex.codecogs.com/svg.image?U "U").

    2.  induction on
        ![M\\cdot 1](https://latex.codecogs.com/svg.image?M%5Ccdot%201 "M\cdot 1")
        and
        ![M \\cdot 2](https://latex.codecogs.com/svg.image?M%20%5Ccdot%202 "M \cdot 2"),
        and we have that
        ![\\mathsf{norm}](https://latex.codecogs.com/svg.image?%5Cmathsf%7Bnorm%7D "\mathsf{norm}")
        for both terms. How to get
        ![\\mathsf{norm}(M)](https://latex.codecogs.com/svg.image?%5Cmathsf%7Bnorm%7D%28M%29 "\mathsf{norm}(M)")
        from
        ![\\mathsf{norm}(M \\cdot 1)](https://latex.codecogs.com/svg.image?%5Cmathsf%7Bnorm%7D%28M%20%5Ccdot%201%29 "\mathsf{norm}(M \cdot 1)")
        and
        ![\\mathsf{norm}(M \\cdot 2)](https://latex.codecogs.com/svg.image?%5Cmathsf%7Bnorm%7D%28M%20%5Ccdot%202%29 "\mathsf{norm}(M \cdot 2)")?
        Consider final form of
        ![M \\cdot 1](https://latex.codecogs.com/svg.image?M%20%5Ccdot%201 "M \cdot 1").
        In the process of reduction,
        ![\\beta - \\times-\\mathrm{LFT}](https://latex.codecogs.com/svg.image?%5Cbeta%20-%20%5Ctimes-%5Cmathrm%7BLFT%7D "\beta - \times-\mathrm{LFT}")
        may take place, or may not take place.

        If no beta-LFT rule is used, then only LFT rule is used then we
        have
        ![\\mathsf{norm}(M)](https://latex.codecogs.com/svg.image?%5Cmathsf%7Bnorm%7D%28M%29 "\mathsf{norm}(M)").
        If there is beta-LFT rule used, things are tricky. I don\'t
        really know how to prove it!
-   ![A](https://latex.codecogs.com/svg.image?A "A") is of form
    ![A_1 \\to A_2](https://latex.codecogs.com/svg.image?A_1%20%5Cto%20A_2 "A_1 \to A_2").
    1.  In order to prove
        ![\\mathsf{HN}(U)](https://latex.codecogs.com/svg.image?%5Cmathsf%7BHN%7D%28U%29 "\mathsf{HN}(U)").
        Given
        ![\\Delta\'\\le \\Delta](https://latex.codecogs.com/svg.image?%5CDelta%27%5Cle%20%5CDelta "\Delta'\le \Delta"),
        and a term ![M](https://latex.codecogs.com/svg.image?M "M"),
        which has
        ![\\mathsf{HN}\^{\\Delta\'}\_{A_1}(M)](https://latex.codecogs.com/svg.image?%5Cmathsf%7BHN%7D%5E%7B%5CDelta%27%7D_%7BA_1%7D%28M%29 "\mathsf{HN}^{\Delta'}_{A_1}(M)"),
        we need to show that
        ![\\mathsf{HN}\^{\\Delta\'}\_{A_2}(\\mathsf{ap}(M ; U))](https://latex.codecogs.com/svg.image?%5Cmathsf%7BHN%7D%5E%7B%5CDelta%27%7D_%7BA_2%7D%28%5Cmathsf%7Bap%7D%28M%20%3B%20U%29%29 "\mathsf{HN}^{\Delta'}_{A_2}(\mathsf{ap}(M ; U))").
        Notice that we of course have
        ![\\mathsf{N N}\^{\\Delta\'}(U)](https://latex.codecogs.com/svg.image?%5Cmathsf%7BN%20N%7D%5E%7B%5CDelta%27%7D%28U%29 "\mathsf{N N}^{\Delta'}(U)").
        Given that
        ![\\mathsf{HN}\^{\\Delta\'}\_{A_1}(M)](https://latex.codecogs.com/svg.image?%5Cmathsf%7BHN%7D%5E%7B%5CDelta%27%7D_%7BA_1%7D%28M%29 "\mathsf{HN}^{\Delta'}_{A_1}(M)"),
        using APP definition of
        ![\\mathsf{N N }](https://latex.codecogs.com/svg.image?%5Cmathsf%7BN%20N%20%7D "\mathsf{N N }"),
        we have
        ![\\mathsf{N N}\_{A_2}\^{\\Delta\'}(\\mathsf{ap}(U ; M))](https://latex.codecogs.com/svg.image?%5Cmathsf%7BN%20N%7D_%7BA_2%7D%5E%7B%5CDelta%27%7D%28%5Cmathsf%7Bap%7D%28U%20%3B%20M%29%29 "\mathsf{N N}_{A_2}^{\Delta'}(\mathsf{ap}(U ; M))").
        Using induction to get
        ![\\mathsf{HN}\^{\\Delta\'}\_{A_2}(\\mathsf{ap}(U ; M))](https://latex.codecogs.com/svg.image?%5Cmathsf%7BHN%7D%5E%7B%5CDelta%27%7D_%7BA_2%7D%28%5Cmathsf%7Bap%7D%28U%20%3B%20M%29%29 "\mathsf{HN}^{\Delta'}_{A_2}(\mathsf{ap}(U ; M))").
    2.  We have
        ![\\mathsf{HN}(M)](https://latex.codecogs.com/svg.image?%5Cmathsf%7BHN%7D%28M%29 "\mathsf{HN}(M)").
        choose
        ![\\Delta\'](https://latex.codecogs.com/svg.image?%5CDelta%27 "\Delta'")
        such that
        ![\\Delta\' \\le \\Delta](https://latex.codecogs.com/svg.image?%5CDelta%27%20%5Cle%20%5CDelta "\Delta' \le \Delta"),
        and then we have that
        ![\\mathsf{N N}\_{A_1}\^{\\Delta\'}(x)](https://latex.codecogs.com/svg.image?%5Cmathsf%7BN%20N%7D_%7BA_1%7D%5E%7B%5CDelta%27%7D%28x%29 "\mathsf{N N}_{A_1}^{\Delta'}(x)")
        since ![x](https://latex.codecogs.com/svg.image?x "x") is a
        variable, and then we have
        ![\\mathsf{HN}\_{A_1}\^{\\Delta\'}(x)](https://latex.codecogs.com/svg.image?%5Cmathsf%7BHN%7D_%7BA_1%7D%5E%7B%5CDelta%27%7D%28x%29 "\mathsf{HN}_{A_1}^{\Delta'}(x)")
        by induction on
        ![A\_{1}](https://latex.codecogs.com/svg.image?A_%7B1%7D "A_{1}").
        From
        ![\\mathsf{HN}(M)](https://latex.codecogs.com/svg.image?%5Cmathsf%7BHN%7D%28M%29 "\mathsf{HN}(M)"),
        we have
        ![\\mathsf{HN}\_{A_2}\^{\\Delta\'}(\\mathsf{ap}(M ; x))](https://latex.codecogs.com/svg.image?%5Cmathsf%7BHN%7D_%7BA_2%7D%5E%7B%5CDelta%27%7D%28%5Cmathsf%7Bap%7D%28M%20%3B%20x%29%29 "\mathsf{HN}_{A_2}^{\Delta'}(\mathsf{ap}(M ; x))").
        By induction on
        ![A_2](https://latex.codecogs.com/svg.image?A_2 "A_2"), we have
        ![\\mathsf{norm}\_{\\beta}(\\mathsf{ap}(M; x))](https://latex.codecogs.com/svg.image?%5Cmathsf%7Bnorm%7D_%7B%5Cbeta%7D%28%5Cmathsf%7Bap%7D%28M%3B%20x%29%29 "\mathsf{norm}_{\beta}(\mathsf{ap}(M; x))"),
        from which we may get
        ![\\mathsf{norm}\_{\\beta}(M)](https://latex.codecogs.com/svg.image?%5Cmathsf%7Bnorm%7D_%7B%5Cbeta%7D%28M%29 "\mathsf{norm}_{\beta}(M)").

You can see, in the above proof, we still need

1.  if
    ![\\mathsf{norm}(M \\cdot 1)](https://latex.codecogs.com/svg.image?%5Cmathsf%7Bnorm%7D%28M%20%5Ccdot%201%29 "\mathsf{norm}(M \cdot 1)")
    and
    ![\\mathsf{norm}(M \\cdot 2)](https://latex.codecogs.com/svg.image?%5Cmathsf%7Bnorm%7D%28M%20%5Ccdot%202%29 "\mathsf{norm}(M \cdot 2)")
    then
    ![\\mathsf{norm}(M)](https://latex.codecogs.com/svg.image?%5Cmathsf%7Bnorm%7D%28M%29 "\mathsf{norm}(M)")
2.  if
    ![\\mathsf{norm}(\\mathsf{ap}(M; x))](https://latex.codecogs.com/svg.image?%5Cmathsf%7Bnorm%7D%28%5Cmathsf%7Bap%7D%28M%3B%20x%29%29 "\mathsf{norm}(\mathsf{ap}(M; x))"),
    then
    ![\\mathsf{norm}(M)](https://latex.codecogs.com/svg.image?%5Cmathsf%7Bnorm%7D%28M%29 "\mathsf{norm}(M)")

For the first one, I would happily say I have no idea. But 2. is very
obvious.
