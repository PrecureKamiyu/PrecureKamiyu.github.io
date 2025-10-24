# Semantic Equality Definition

这里的
![\\doteq](https://latex.codecogs.com/svg.image?%5Cdoteq "\doteq")
被称为 semantic equality 又被称为 exact equality 。如果只看 function
类型的话，不难发现这是被称为 extensional equality 的事物。称其为
behavioral equality 也能说的过去。之所以这里都列出来，是因为 Bob
在这里的称呼 就没怎么统一过。

可以理解为 axiomtic equality 是 equality defined rules 。而 extensional
equality 确实是有一些"meta"的感觉的，某种意义上可以称为 functional
interpreted equality 的。

下面是定义 term 之间的一个二元关系
![\\doteq](https://latex.codecogs.com/svg.image?%5Cdoteq "\doteq")
的定义。这是之前的 hereditary termination 的一个扩展？

![\\begin{aligned}
M \\doteq M\' \\in \\text{ans} & \\text{ iff } M, M\' \\stackrel{\*}{\\longmapsto} \\text{yes} \\text{ or } M, M\' \\stackrel{\*}{\\longmapsto} \\text{no} \\\\
M \\doteq M\' \\in \\text{unit} & \\text{ iff } M, M\' \\stackrel{\*}{\\longmapsto} \\langle \\rangle \\\\
M \\doteq M\' \\in A_1 \\times A_2 & \\text{ iff } M \\longmapsto \\langle M_1, M_2 \\rangle, M\' \\longmapsto \\langle M\'\_1, M\'\_2 \\rangle, \\text{ and} \\\\
& M_1 \\doteq M\'\_1 \\in A_1 \\text{ and } M_2 \\doteq M\'\_2 \\in A_2 \\\\
M \\doteq M\' \\in A_1 \\rightarrow A_2 & \\text{ iff } M \\stackrel{\*}{\\longmapsto} \\lambda(x.N), M\' \\stackrel{\*}{\\longmapsto} \\lambda(x.N\'), \\text{ and} \\\\
& \\text{if } M_1 \\doteq M\'\_1 \\in A_1 \\text{ then } \[M_1/x\]N \\doteq \[M\'\_1/x\]N\' \\in A_2
\\end{aligned}](https://latex.codecogs.com/svg.image?%5Cbegin%7Baligned%7D%0AM%20%5Cdoteq%20M%27%20%5Cin%20%5Ctext%7Bans%7D%20%26%20%5Ctext%7B%20iff%20%7D%20M%2C%20M%27%20%5Cstackrel%7B%2A%7D%7B%5Clongmapsto%7D%20%5Ctext%7Byes%7D%20%5Ctext%7B%20or%20%7D%20M%2C%20M%27%20%5Cstackrel%7B%2A%7D%7B%5Clongmapsto%7D%20%5Ctext%7Bno%7D%20%5C%5C%0AM%20%5Cdoteq%20M%27%20%5Cin%20%5Ctext%7Bunit%7D%20%26%20%5Ctext%7B%20iff%20%7D%20M%2C%20M%27%20%5Cstackrel%7B%2A%7D%7B%5Clongmapsto%7D%20%5Clangle%20%5Crangle%20%5C%5C%0AM%20%5Cdoteq%20M%27%20%5Cin%20A_1%20%5Ctimes%20A_2%20%26%20%5Ctext%7B%20iff%20%7D%20M%20%5Clongmapsto%20%5Clangle%20M_1%2C%20M_2%20%5Crangle%2C%20M%27%20%5Clongmapsto%20%5Clangle%20M%27_1%2C%20M%27_2%20%5Crangle%2C%20%5Ctext%7B%20and%7D%20%5C%5C%0A%26%20M_1%20%5Cdoteq%20M%27_1%20%5Cin%20A_1%20%5Ctext%7B%20and%20%7D%20M_2%20%5Cdoteq%20M%27_2%20%5Cin%20A_2%20%5C%5C%0AM%20%5Cdoteq%20M%27%20%5Cin%20A_1%20%5Crightarrow%20A_2%20%26%20%5Ctext%7B%20iff%20%7D%20M%20%5Cstackrel%7B%2A%7D%7B%5Clongmapsto%7D%20%5Clambda%28x.N%29%2C%20M%27%20%5Cstackrel%7B%2A%7D%7B%5Clongmapsto%7D%20%5Clambda%28x.N%27%29%2C%20%5Ctext%7B%20and%7D%20%5C%5C%0A%26%20%5Ctext%7Bif%20%7D%20M_1%20%5Cdoteq%20M%27_1%20%5Cin%20A_1%20%5Ctext%7B%20then%20%7D%20%5BM_1%2Fx%5DN%20%5Cdoteq%20%5BM%27_1%2Fx%5DN%27%20%5Cin%20A_2%0A%5Cend%7Baligned%7D "\begin{aligned}
M \doteq M' \in \text{ans} & \text{ iff } M, M' \stackrel{*}{\longmapsto} \text{yes} \text{ or } M, M' \stackrel{*}{\longmapsto} \text{no} \\
M \doteq M' \in \text{unit} & \text{ iff } M, M' \stackrel{*}{\longmapsto} \langle \rangle \\
M \doteq M' \in A_1 \times A_2 & \text{ iff } M \longmapsto \langle M_1, M_2 \rangle, M' \longmapsto \langle M'_1, M'_2 \rangle, \text{ and} \\
& M_1 \doteq M'_1 \in A_1 \text{ and } M_2 \doteq M'_2 \in A_2 \\
M \doteq M' \in A_1 \rightarrow A_2 & \text{ iff } M \stackrel{*}{\longmapsto} \lambda(x.N), M' \stackrel{*}{\longmapsto} \lambda(x.N'), \text{ and} \\
& \text{if } M_1 \doteq M'_1 \in A_1 \text{ then } [M_1/x]N \doteq [M'_1/x]N' \in A_2
\end{aligned}")

这里
![M \\in A](https://latex.codecogs.com/svg.image?M%20%5Cin%20A "M \in A")
is short for
![M = M \\in A](https://latex.codecogs.com/svg.image?M%20%3D%20M%20%5Cin%20A "M = M \in A")

lemma 1: the relation is symmetric and transitive

1.  ![M \\doteq M\' \\in A](https://latex.codecogs.com/svg.image?M%20%5Cdoteq%20M%27%20%5Cin%20A "M \doteq M' \in A")
    implies
    ![M\' \\doteq M \\in A](https://latex.codecogs.com/svg.image?M%27%20%5Cdoteq%20M%20%5Cin%20A "M' \doteq M \in A").
2.  ![M_1 \\doteq M_2 \\in A](https://latex.codecogs.com/svg.image?M_1%20%5Cdoteq%20M_2%20%5Cin%20A "M_1 \doteq M_2 \in A")
    and
    ![M_2 \\doteq M_3 \\in A](https://latex.codecogs.com/svg.image?M_2%20%5Cdoteq%20M_3%20%5Cin%20A "M_2 \doteq M_3 \in A")
    implies
    ![M_1 \\doteq M_3 \\in A](https://latex.codecogs.com/svg.image?M_1%20%5Cdoteq%20M_3%20%5Cin%20A "M_1 \doteq M_3 \in A")

The proof is omitted since simple induction on type
![A](https://latex.codecogs.com/svg.image?A "A") is more than enough.

A symmetric and transitive relation is called a partial equivalence
relations.

The relation can also extend to a closed substi
![\\gamma](https://latex.codecogs.com/svg.image?%5Cgamma "\gamma"),
variable-wise equivalence:

![\\gamma \\doteq \\gamma\' \\in \\Gamma := \\forall x : A \\in \\Gamma, \\gamma(x) \\doteq \\gamma\'(x) \\in A](https://latex.codecogs.com/svg.image?%5Cgamma%20%5Cdoteq%20%5Cgamma%27%20%5Cin%20%5CGamma%20%3A%3D%20%5Cforall%20x%20%3A%20A%20%5Cin%20%5CGamma%2C%20%5Cgamma%28x%29%20%5Cdoteq%20%5Cgamma%27%28x%29%20%5Cin%20A "\gamma \doteq \gamma' \in \Gamma := \forall x : A \in \Gamma, \gamma(x) \doteq \gamma'(x) \in A")

And we define
![\\Gamma \\gg M \\doteq M \' \\in A](https://latex.codecogs.com/svg.image?%5CGamma%20%5Cgg%20M%20%5Cdoteq%20M%20%27%20%5Cin%20A "\Gamma \gg M \doteq M ' \in A")
(which is relation between
![M](https://latex.codecogs.com/svg.image?M "M") and
![M\'](https://latex.codecogs.com/svg.image?M%27 "M'")):

![\\gamma \\doteq \\gamma\' \\in \\Gamma \\implies \\hat\\gamma (M) \\doteq \\hat \\gamma\'(M\')\\in A](https://latex.codecogs.com/svg.image?%5Cgamma%20%5Cdoteq%20%5Cgamma%27%20%5Cin%20%5CGamma%20%5Cimplies%20%5Chat%5Cgamma%20%28M%29%20%5Cdoteq%20%5Chat%20%5Cgamma%27%28M%27%29%5Cin%20A "\gamma \doteq \gamma' \in \Gamma \implies \hat\gamma (M) \doteq \hat \gamma'(M')\in A")

for open terms ![M](https://latex.codecogs.com/svg.image?M "M") and
![M\'](https://latex.codecogs.com/svg.image?M%27 "M'"), we say they are
equivalent if for every variable-wise equivalent substi
![\\gamma](https://latex.codecogs.com/svg.image?%5Cgamma "\gamma") and
![\\gamma\'](https://latex.codecogs.com/svg.image?%5Cgamma%27 "\gamma'"),
the results of the substi are equivalent.

**lemma 2 head expansion** If
![N \\longmapsto M](https://latex.codecogs.com/svg.image?N%20%5Clongmapsto%20M "N \longmapsto M")
and
![M \\doteq M \' \\in A](https://latex.codecogs.com/svg.image?M%20%5Cdoteq%20M%20%27%20%5Cin%20A "M \doteq M ' \in A")
then
![N \\doteq M \' \\in A](https://latex.codecogs.com/svg.image?N%20%5Cdoteq%20M%20%27%20%5Cin%20A "N \doteq M ' \in A").

**Theorem 3**: If
![\\Gamma \\vdash M : A](https://latex.codecogs.com/svg.image?%5CGamma%20%5Cvdash%20M%20%3A%20A "\Gamma \vdash M : A")
then
![\\Gamma \\gg M \\in A](https://latex.codecogs.com/svg.image?%5CGamma%20%5Cgg%20M%20%5Cin%20A "\Gamma \gg M \in A").

**lemma 4 (sym and trans)**

1.  ![\\Gamma \\gg M \\doteq M \' \\in A](https://latex.codecogs.com/svg.image?%5CGamma%20%5Cgg%20M%20%5Cdoteq%20M%20%27%20%5Cin%20A "\Gamma \gg M \doteq M ' \in A"),
    then
    ![\\Gamma \\gg M \' = M \\in A](https://latex.codecogs.com/svg.image?%5CGamma%20%5Cgg%20M%20%27%20%3D%20M%20%5Cin%20A "\Gamma \gg M ' = M \in A").
2.  ![\\Gamma \\gg M \\doteq M\' \\in A](https://latex.codecogs.com/svg.image?%5CGamma%20%5Cgg%20M%20%5Cdoteq%20M%27%20%5Cin%20A "\Gamma \gg M \doteq M' \in A")
    and
    ![\\Gamma \\gg M\' \\doteq M\'\' \\in A](https://latex.codecogs.com/svg.image?%5CGamma%20%5Cgg%20M%27%20%5Cdoteq%20M%27%27%20%5Cin%20A "\Gamma \gg M' \doteq M'' \in A"),
    then
    ![\\Gamma \\gg M \\doteq M\'\' \\in A](https://latex.codecogs.com/svg.image?%5CGamma%20%5Cgg%20M%20%5Cdoteq%20M%27%27%20%5Cin%20A "\Gamma \gg M \doteq M'' \in A").

Here is the proof. I would say that this is not that hard.

1.  Given
    ![\\Gamma \\gg M \\doteq M \' \\in A](https://latex.codecogs.com/svg.image?%5CGamma%20%5Cgg%20M%20%5Cdoteq%20M%20%27%20%5Cin%20A "\Gamma \gg M \doteq M ' \in A")
    and
    ![\\gamma \' \\doteq \\gamma \\in \\Gamma](https://latex.codecogs.com/svg.image?%5Cgamma%20%27%20%5Cdoteq%20%5Cgamma%20%5Cin%20%5CGamma "\gamma ' \doteq \gamma \in \Gamma"),
    to prove that
    ![\\gamma \' (M\') \\doteq \\gamma (M) \\in A](https://latex.codecogs.com/svg.image?%5Cgamma%20%27%20%28M%27%29%20%5Cdoteq%20%5Cgamma%20%28M%29%20%5Cin%20A "\gamma ' (M') \doteq \gamma (M) \in A").
    It is obvious that we can have
    ![\\gamma \\doteq \\gamma\' \\in \\Gamma](https://latex.codecogs.com/svg.image?%5Cgamma%20%5Cdoteq%20%5Cgamma%27%20%5Cin%20%5CGamma "\gamma \doteq \gamma' \in \Gamma")
    from
    ![\\gamma\' \\doteq \\gamma \\in \\Gamma](https://latex.codecogs.com/svg.image?%5Cgamma%27%20%5Cdoteq%20%5Cgamma%20%5Cin%20%5CGamma "\gamma' \doteq \gamma \in \Gamma"),
    and thus applies this
    ![\\gamma \\doteq \\gamma \' \\in \\Gamma](https://latex.codecogs.com/svg.image?%5Cgamma%20%5Cdoteq%20%5Cgamma%20%27%20%5Cin%20%5CGamma "\gamma \doteq \gamma ' \in \Gamma")
    to
    ![\\Gamma \\gg M \\doteq  M \' \\in A](https://latex.codecogs.com/svg.image?%5CGamma%20%5Cgg%20M%20%5Cdoteq%20%20M%20%27%20%5Cin%20A "\Gamma \gg M \doteq  M ' \in A")
    we have the
    ![\\gamma(M) \\doteq \\gamma \' (M\')\\in \\Gamma](https://latex.codecogs.com/svg.image?%5Cgamma%28M%29%20%5Cdoteq%20%5Cgamma%20%27%20%28M%27%29%5Cin%20%5CGamma "\gamma(M) \doteq \gamma ' (M')\in \Gamma")
    and use the reflexivity of
    ![\\doteq](https://latex.codecogs.com/svg.image?%5Cdoteq "\doteq")
    we have the desired results. Which is pretty obvious
2.  Given
    ![\\gamma \\doteq \\gamma \'\' \\in \\Gamma](https://latex.codecogs.com/svg.image?%5Cgamma%20%5Cdoteq%20%5Cgamma%20%27%27%20%5Cin%20%5CGamma "\gamma \doteq \gamma '' \in \Gamma")
    we want to prove
    ![\\gamma (M) \\doteq \\gamma\'\'(M\'\') \\in A](https://latex.codecogs.com/svg.image?%5Cgamma%20%28M%29%20%5Cdoteq%20%5Cgamma%27%27%28M%27%27%29%20%5Cin%20A "\gamma (M) \doteq \gamma''(M'') \in A").
    How? If we apply (instantiate) to two premises, we will have
    -   ![\\gamma (M)\\doteq \\gamma\'\' (M\')\\in A](https://latex.codecogs.com/svg.image?%5Cgamma%20%28M%29%5Cdoteq%20%5Cgamma%27%27%20%28M%27%29%5Cin%20A "\gamma (M)\doteq \gamma'' (M')\in A")
    -   ![\\gamma(M\')\\doteq \\gamma\'\' (M\'\') \\in A](https://latex.codecogs.com/svg.image?%5Cgamma%28M%27%29%5Cdoteq%20%5Cgamma%27%27%20%28M%27%27%29%20%5Cin%20A "\gamma(M')\doteq \gamma'' (M'') \in A")

    which is not enough for anything. But we can apply
    ![\\gamma\'\' \\doteq \\gamma\'\' \\in \\Gamma](https://latex.codecogs.com/svg.image?%5Cgamma%27%27%20%5Cdoteq%20%5Cgamma%27%27%20%5Cin%20%5CGamma "\gamma'' \doteq \gamma'' \in \Gamma")
    to the second premise. and we have these two:
    -   ![\\gamma(M)\\doteq \\gamma\'\'(M\') \\in A](https://latex.codecogs.com/svg.image?%5Cgamma%28M%29%5Cdoteq%20%5Cgamma%27%27%28M%27%29%20%5Cin%20A "\gamma(M)\doteq \gamma''(M') \in A")
    -   ![\\gamma\'\'(M\')\\doteq \\gamma\'\' (M\'\')\\in A](https://latex.codecogs.com/svg.image?%5Cgamma%27%27%28M%27%29%5Cdoteq%20%5Cgamma%27%27%20%28M%27%27%29%5Cin%20A "\gamma''(M')\doteq \gamma'' (M'')\in A")

    which is more than enough to prove
    ![\\gamma(M)\\doteq \\gamma\'\' (M\'\')\\in A](https://latex.codecogs.com/svg.image?%5Cgamma%28M%29%5Cdoteq%20%5Cgamma%27%27%20%28M%27%27%29%5Cin%20A "\gamma(M)\doteq \gamma'' (M'')\in A")
    using transitivity.

Trivial!

# Definitional (Axiomatic) Equality

![\\text{REFL} \\quad \\frac{\\Gamma \\vdash M : A}{\\Gamma \\vdash M \\equiv M : A} \\qquad
\\text{SYM} \\quad \\frac{\\Gamma \\vdash M \\equiv N : A}{\\Gamma \\vdash N \\equiv M : A}](https://latex.codecogs.com/svg.image?%5Ctext%7BREFL%7D%20%5Cquad%20%5Cfrac%7B%5CGamma%20%5Cvdash%20M%20%3A%20A%7D%7B%5CGamma%20%5Cvdash%20M%20%5Cequiv%20M%20%3A%20A%7D%20%5Cqquad%0A%5Ctext%7BSYM%7D%20%5Cquad%20%5Cfrac%7B%5CGamma%20%5Cvdash%20M%20%5Cequiv%20N%20%3A%20A%7D%7B%5CGamma%20%5Cvdash%20N%20%5Cequiv%20M%20%3A%20A%7D "\text{REFL} \quad \frac{\Gamma \vdash M : A}{\Gamma \vdash M \equiv M : A} \qquad
\text{SYM} \quad \frac{\Gamma \vdash M \equiv N : A}{\Gamma \vdash N \equiv M : A}")

![\\text{TRANS} \\quad \\frac{\\Gamma \\vdash M \\equiv N : A \\quad \\Gamma \\vdash N \\equiv P : A}{\\Gamma \\vdash M \\equiv P : A} \\qquad
\\text{1-}\\eta \\quad \\frac{\\Gamma \\vdash M : 1}{\\Gamma \\vdash M \\equiv \\langle \\rangle : 1}](https://latex.codecogs.com/svg.image?%5Ctext%7BTRANS%7D%20%5Cquad%20%5Cfrac%7B%5CGamma%20%5Cvdash%20M%20%5Cequiv%20N%20%3A%20A%20%5Cquad%20%5CGamma%20%5Cvdash%20N%20%5Cequiv%20P%20%3A%20A%7D%7B%5CGamma%20%5Cvdash%20M%20%5Cequiv%20P%20%3A%20A%7D%20%5Cqquad%0A%5Ctext%7B1-%7D%5Ceta%20%5Cquad%20%5Cfrac%7B%5CGamma%20%5Cvdash%20M%20%3A%201%7D%7B%5CGamma%20%5Cvdash%20M%20%5Cequiv%20%5Clangle%20%5Crangle%20%3A%201%7D "\text{TRANS} \quad \frac{\Gamma \vdash M \equiv N : A \quad \Gamma \vdash N \equiv P : A}{\Gamma \vdash M \equiv P : A} \qquad
\text{1-}\eta \quad \frac{\Gamma \vdash M : 1}{\Gamma \vdash M \equiv \langle \rangle : 1}")

![\\times\\text{-I} \\quad \\frac{\\Gamma \\vdash M_1 \\equiv N_1 : A_1 \\quad \\Gamma \\vdash M_2 \\equiv N_2 : A_2}{\\Gamma \\vdash \\langle M_1, M_2 \\rangle \\equiv \\langle N_1, N_2 \\rangle : A_1 \\times A_2}](https://latex.codecogs.com/svg.image?%5Ctimes%5Ctext%7B-I%7D%20%5Cquad%20%5Cfrac%7B%5CGamma%20%5Cvdash%20M_1%20%5Cequiv%20N_1%20%3A%20A_1%20%5Cquad%20%5CGamma%20%5Cvdash%20M_2%20%5Cequiv%20N_2%20%3A%20A_2%7D%7B%5CGamma%20%5Cvdash%20%5Clangle%20M_1%2C%20M_2%20%5Crangle%20%5Cequiv%20%5Clangle%20N_1%2C%20N_2%20%5Crangle%20%3A%20A_1%20%5Ctimes%20A_2%7D "\times\text{-I} \quad \frac{\Gamma \vdash M_1 \equiv N_1 : A_1 \quad \Gamma \vdash M_2 \equiv N_2 : A_2}{\Gamma \vdash \langle M_1, M_2 \rangle \equiv \langle N_1, N_2 \rangle : A_1 \times A_2}")

![\\times\\text{-}\\beta\\text{-L} \\quad \\frac{\\Gamma \\vdash M_1 : A_1 \\quad \\Gamma \\vdash M_2 : A_2}{\\Gamma \\vdash \\langle M_1, M_2 \\rangle \\cdot 1 \\equiv M_1 : A_1}](https://latex.codecogs.com/svg.image?%5Ctimes%5Ctext%7B-%7D%5Cbeta%5Ctext%7B-L%7D%20%5Cquad%20%5Cfrac%7B%5CGamma%20%5Cvdash%20M_1%20%3A%20A_1%20%5Cquad%20%5CGamma%20%5Cvdash%20M_2%20%3A%20A_2%7D%7B%5CGamma%20%5Cvdash%20%5Clangle%20M_1%2C%20M_2%20%5Crangle%20%5Ccdot%201%20%5Cequiv%20M_1%20%3A%20A_1%7D "\times\text{-}\beta\text{-L} \quad \frac{\Gamma \vdash M_1 : A_1 \quad \Gamma \vdash M_2 : A_2}{\Gamma \vdash \langle M_1, M_2 \rangle \cdot 1 \equiv M_1 : A_1}")

![\\times\\text{-}\\eta \\quad \\frac{\\Gamma \\vdash M : A_1 \\times A_2}{\\Gamma \\vdash M \\equiv \\langle M \\cdot 1, M \\cdot 2 \\rangle : A_1 \\times A_2}](https://latex.codecogs.com/svg.image?%5Ctimes%5Ctext%7B-%7D%5Ceta%20%5Cquad%20%5Cfrac%7B%5CGamma%20%5Cvdash%20M%20%3A%20A_1%20%5Ctimes%20A_2%7D%7B%5CGamma%20%5Cvdash%20M%20%5Cequiv%20%5Clangle%20M%20%5Ccdot%201%2C%20M%20%5Ccdot%202%20%5Crangle%20%3A%20A_1%20%5Ctimes%20A_2%7D "\times\text{-}\eta \quad \frac{\Gamma \vdash M : A_1 \times A_2}{\Gamma \vdash M \equiv \langle M \cdot 1, M \cdot 2 \rangle : A_1 \times A_2}")

![\\to\\text{-E} \\quad \\frac{\\Gamma \\vdash M \\equiv N : A_1 \\rightarrow A_2 \\quad \\Gamma \\vdash M_1 \\equiv N_1 : A_1}{\\Gamma \\vdash \\text{ap}(M; M_1) \\equiv \\text{ap}(N; N_1) : A_2}](https://latex.codecogs.com/svg.image?%5Cto%5Ctext%7B-E%7D%20%5Cquad%20%5Cfrac%7B%5CGamma%20%5Cvdash%20M%20%5Cequiv%20N%20%3A%20A_1%20%5Crightarrow%20A_2%20%5Cquad%20%5CGamma%20%5Cvdash%20M_1%20%5Cequiv%20N_1%20%3A%20A_1%7D%7B%5CGamma%20%5Cvdash%20%5Ctext%7Bap%7D%28M%3B%20M_1%29%20%5Cequiv%20%5Ctext%7Bap%7D%28N%3B%20N_1%29%20%3A%20A_2%7D "\to\text{-E} \quad \frac{\Gamma \vdash M \equiv N : A_1 \rightarrow A_2 \quad \Gamma \vdash M_1 \equiv N_1 : A_1}{\Gamma \vdash \text{ap}(M; M_1) \equiv \text{ap}(N; N_1) : A_2}")

![\\to\\text{-}\\eta \\quad \\frac{\\Gamma \\vdash M : A_1 \\rightarrow A_2}{\\Gamma \\vdash M \\equiv \\lambda(x. \\text{ap}(M; x)) : A_1 \\rightarrow A_2}](https://latex.codecogs.com/svg.image?%5Cto%5Ctext%7B-%7D%5Ceta%20%5Cquad%20%5Cfrac%7B%5CGamma%20%5Cvdash%20M%20%3A%20A_1%20%5Crightarrow%20A_2%7D%7B%5CGamma%20%5Cvdash%20M%20%5Cequiv%20%5Clambda%28x.%20%5Ctext%7Bap%7D%28M%3B%20x%29%29%20%3A%20A_1%20%5Crightarrow%20A_2%7D "\to\text{-}\eta \quad \frac{\Gamma \vdash M : A_1 \rightarrow A_2}{\Gamma \vdash M \equiv \lambda(x. \text{ap}(M; x)) : A_1 \rightarrow A_2}")

![\\times\\text{-E-L} \\quad \\frac{\\Gamma \\vdash M \\equiv N : A_1 \\times A_2}{\\Gamma \\vdash M \\cdot 1 \\equiv N \\cdot 1 : A_1}
\\quad
\\times\\text{-E-R} \\quad \\frac{\\Gamma \\vdash M \\equiv N : A_1 \\times A_2}{\\Gamma \\vdash M \\cdot 2 \\equiv N \\cdot 2 : A_2}](https://latex.codecogs.com/svg.image?%5Ctimes%5Ctext%7B-E-L%7D%20%5Cquad%20%5Cfrac%7B%5CGamma%20%5Cvdash%20M%20%5Cequiv%20N%20%3A%20A_1%20%5Ctimes%20A_2%7D%7B%5CGamma%20%5Cvdash%20M%20%5Ccdot%201%20%5Cequiv%20N%20%5Ccdot%201%20%3A%20A_1%7D%0A%5Cquad%0A%5Ctimes%5Ctext%7B-E-R%7D%20%5Cquad%20%5Cfrac%7B%5CGamma%20%5Cvdash%20M%20%5Cequiv%20N%20%3A%20A_1%20%5Ctimes%20A_2%7D%7B%5CGamma%20%5Cvdash%20M%20%5Ccdot%202%20%5Cequiv%20N%20%5Ccdot%202%20%3A%20A_2%7D "\times\text{-E-L} \quad \frac{\Gamma \vdash M \equiv N : A_1 \times A_2}{\Gamma \vdash M \cdot 1 \equiv N \cdot 1 : A_1}
\quad
\times\text{-E-R} \quad \frac{\Gamma \vdash M \equiv N : A_1 \times A_2}{\Gamma \vdash M \cdot 2 \equiv N \cdot 2 : A_2}")

![\\rightarrow\\text{-I} \\quad \\frac{\\Gamma, x : A_1 \\vdash M_2 \\equiv N_2 : A_2}{\\Gamma \\vdash \\lambda(x.M_2) \\equiv \\lambda(x.N_2) : A_1 \\rightarrow A_2}](https://latex.codecogs.com/svg.image?%5Crightarrow%5Ctext%7B-I%7D%20%5Cquad%20%5Cfrac%7B%5CGamma%2C%20x%20%3A%20A_1%20%5Cvdash%20M_2%20%5Cequiv%20N_2%20%3A%20A_2%7D%7B%5CGamma%20%5Cvdash%20%5Clambda%28x.M_2%29%20%5Cequiv%20%5Clambda%28x.N_2%29%20%3A%20A_1%20%5Crightarrow%20A_2%7D "\rightarrow\text{-I} \quad \frac{\Gamma, x : A_1 \vdash M_2 \equiv N_2 : A_2}{\Gamma \vdash \lambda(x.M_2) \equiv \lambda(x.N_2) : A_1 \rightarrow A_2}")

![\\rightarrow\\text{-}\\beta \\quad \\frac{\\Gamma, x : A_1 \\vdash M_2 : A_2 \\quad \\Gamma \\vdash M_1 : A_1}{\\Gamma \\vdash \\text{ap}(\\lambda(x.M_2); M_1) \\equiv \[M_1/x\]M_2 : A_2}](https://latex.codecogs.com/svg.image?%5Crightarrow%5Ctext%7B-%7D%5Cbeta%20%5Cquad%20%5Cfrac%7B%5CGamma%2C%20x%20%3A%20A_1%20%5Cvdash%20M_2%20%3A%20A_2%20%5Cquad%20%5CGamma%20%5Cvdash%20M_1%20%3A%20A_1%7D%7B%5CGamma%20%5Cvdash%20%5Ctext%7Bap%7D%28%5Clambda%28x.M_2%29%3B%20M_1%29%20%5Cequiv%20%5BM_1%2Fx%5DM_2%20%3A%20A_2%7D "\rightarrow\text{-}\beta \quad \frac{\Gamma, x : A_1 \vdash M_2 : A_2 \quad \Gamma \vdash M_1 : A_1}{\Gamma \vdash \text{ap}(\lambda(x.M_2); M_1) \equiv [M_1/x]M_2 : A_2}")

注意到 ![\\eta](https://latex.codecogs.com/svg.image?%5Ceta "\eta") rule
是某种 expansion 而
![\\beta](https://latex.codecogs.com/svg.image?%5Cbeta "\beta") rule 是
reduction 。之后还会有 commutativity rules。

**theorem 5**

If
![\\Gamma \\vdash M \\equiv N : A](https://latex.codecogs.com/svg.image?%5CGamma%20%5Cvdash%20M%20%5Cequiv%20N%20%3A%20A "\Gamma \vdash M \equiv N : A"),
then
![\\hat \\gamma (M) \\doteq \\hat \\gamma \' (N) \\in A](https://latex.codecogs.com/svg.image?%5Chat%20%5Cgamma%20%28M%29%20%5Cdoteq%20%5Chat%20%5Cgamma%20%27%20%28N%29%20%5Cin%20A "\hat \gamma (M) \doteq \hat \gamma ' (N) \in A"),
for all
![\\gamma \\doteq \\gamma\' \\in \\Gamma](https://latex.codecogs.com/svg.image?%5Cgamma%20%5Cdoteq%20%5Cgamma%27%20%5Cin%20%5CGamma "\gamma \doteq \gamma' \in \Gamma")。注意这里和
![\\Gamma \\gg M \\doteq M\' \\in A](https://latex.codecogs.com/svg.image?%5CGamma%20%5Cgg%20M%20%5Cdoteq%20M%27%20%5Cin%20A "\Gamma \gg M \doteq M' \in A")
不太一样。这里的是通过
![\\equiv](https://latex.codecogs.com/svg.image?%5Cequiv "\equiv")
的到了
![\\doteq](https://latex.codecogs.com/svg.image?%5Cdoteq "\doteq")。

证明可以是类似的。可以看见
![\\equiv](https://latex.codecogs.com/svg.image?%5Cequiv "\equiv")
的定义是 structural 的，我们在
![\\equiv](https://latex.codecogs.com/svg.image?%5Cequiv "\equiv")
上面做 induction。

但是 ![\\equiv](https://latex.codecogs.com/svg.image?%5Cequiv "\equiv")
的 rule 足足有 14 条，我们的证明将会非常的 verbose
而且没什么意义，但依然

-   REFL.
    ![\\Gamma \\vdash M \\equiv M : A](https://latex.codecogs.com/svg.image?%5CGamma%20%5Cvdash%20M%20%5Cequiv%20M%20%3A%20A "\Gamma \vdash M \equiv M : A")
    需要证明
    ![\\hat M \\doteq \\hat M\' \\in A](https://latex.codecogs.com/svg.image?%5Chat%20M%20%5Cdoteq%20%5Chat%20M%27%20%5Cin%20A "\hat M \doteq \hat M' \in A")
    ，怎么说？应该是明显的吧，直接从
    ![\\Gamma \\vdash M : A](https://latex.codecogs.com/svg.image?%5CGamma%20%5Cvdash%20M%20%3A%20A "\Gamma \vdash M : A")
    到
    ![\\Gamma \\gg M \\in A](https://latex.codecogs.com/svg.image?%5CGamma%20%5Cgg%20M%20%5Cin%20A "\Gamma \gg M \in A")
    上就行了。前面已经有的结论。

-   SYM.
    ![\\Gamma \\vdash M \\equiv N : A](https://latex.codecogs.com/svg.image?%5CGamma%20%5Cvdash%20M%20%5Cequiv%20N%20%3A%20A "\Gamma \vdash M \equiv N : A")
    ，给了
    ![\\Gamma \\vdash N \\equiv M : A](https://latex.codecogs.com/svg.image?%5CGamma%20%5Cvdash%20N%20%5Cequiv%20M%20%3A%20A "\Gamma \vdash N \equiv M : A")
    。递归（induction）。

-   TRANS.
    ![\\Gamma \\vdash M \\equiv P : A](https://latex.codecogs.com/svg.image?%5CGamma%20%5Cvdash%20M%20%5Cequiv%20P%20%3A%20A "\Gamma \vdash M \equiv P : A")
    ，给了
    ![\\Gamma \\vdash M \\equiv N : A](https://latex.codecogs.com/svg.image?%5CGamma%20%5Cvdash%20M%20%5Cequiv%20N%20%3A%20A "\Gamma \vdash M \equiv N : A")
    以及
    ![\\Gamma \\vdash N \\equiv P : A](https://latex.codecogs.com/svg.image?%5CGamma%20%5Cvdash%20N%20%5Cequiv%20P%20%3A%20A "\Gamma \vdash N \equiv P : A")
    。证明
    ![\\hat M \\doteq \\hat  P\' : A](https://latex.codecogs.com/svg.image?%5Chat%20M%20%5Cdoteq%20%5Chat%20%20P%27%20%3A%20A "\hat M \doteq \hat  P' : A").

    -   使用 induction ，第一个 premise 加上
        ![\\gamma \\doteq \\gamma \\in \\Gamma](https://latex.codecogs.com/svg.image?%5Cgamma%20%5Cdoteq%20%5Cgamma%20%5Cin%20%5CGamma "\gamma \doteq \gamma \in \Gamma")
        得到
        ![\\hat M \\doteq \\hat N : A](https://latex.codecogs.com/svg.image?%5Chat%20M%20%5Cdoteq%20%5Chat%20N%20%3A%20A "\hat M \doteq \hat N : A").
    -   第二个 premise 加上
        ![\\gamma \\doteq \\gamma\' \\in \\Gamma](https://latex.codecogs.com/svg.image?%5Cgamma%20%5Cdoteq%20%5Cgamma%27%20%5Cin%20%5CGamma "\gamma \doteq \gamma' \in \Gamma")
        得到
        ![\\hat N \\doteq P\' : A](https://latex.codecogs.com/svg.image?%5Chat%20N%20%5Cdoteq%20P%27%20%3A%20A "\hat N \doteq P' : A")

    使用 transitivity of
    ![\\doteq](https://latex.codecogs.com/svg.image?%5Cdoteq "\doteq")
    得证

-   1-![\\eta](https://latex.codecogs.com/svg.image?%5Ceta "\eta").
    ![\\Gamma \\vdash M \\equiv \\langle\\rangle : 1](https://latex.codecogs.com/svg.image?%5CGamma%20%5Cvdash%20M%20%5Cequiv%20%5Clangle%5Crangle%20%3A%201 "\Gamma \vdash M \equiv \langle\rangle : 1")
    。证明
    ![\\hat M \\doteq \\langle \\rangle : 1](https://latex.codecogs.com/svg.image?%5Chat%20M%20%5Cdoteq%20%5Clangle%20%5Crangle%20%3A%201 "\hat M \doteq \langle \rangle : 1")
    。因为
    ![\\hat M](https://latex.codecogs.com/svg.image?%5Chat%20M "\hat M")
    是 closed 的所以后者根据定义是显然的。

-   ![\\times](https://latex.codecogs.com/svg.image?%5Ctimes "\times")-I.
    ![\\Gamma \\vdash \\langle M_1 , M_2 \\rangle \\equiv \\langle N_1 , N_2 \\rangle : A_1 \\times A_2](https://latex.codecogs.com/svg.image?%5CGamma%20%5Cvdash%20%5Clangle%20M_1%20%2C%20M_2%20%5Crangle%20%5Cequiv%20%5Clangle%20N_1%20%2C%20N_2%20%5Crangle%20%3A%20A_1%20%5Ctimes%20A_2 "\Gamma \vdash \langle M_1 , M_2 \rangle \equiv \langle N_1 , N_2 \rangle : A_1 \times A_2")
    。给定了
    ![\\Gamma \\vdash M_1 \\equiv N_1 : A_1](https://latex.codecogs.com/svg.image?%5CGamma%20%5Cvdash%20M_1%20%5Cequiv%20N_1%20%3A%20A_1 "\Gamma \vdash M_1 \equiv N_1 : A_1")
    以及
    ![\\Gamma \\vdash M_2 \\equiv N_2 : A_2](https://latex.codecogs.com/svg.image?%5CGamma%20%5Cvdash%20M_2%20%5Cequiv%20N_2%20%3A%20A_2 "\Gamma \vdash M_2 \equiv N_2 : A_2")。证明
    ![\\langle \\hat M_1, \\hat M_2 \\rangle \\doteq \\langle \\hat N_1\', \\hat N_2\' \\rangle : A_1 \\times A_2](https://latex.codecogs.com/svg.image?%5Clangle%20%5Chat%20M_1%2C%20%5Chat%20M_2%20%5Crangle%20%5Cdoteq%20%5Clangle%20%5Chat%20N_1%27%2C%20%5Chat%20N_2%27%20%5Crangle%20%3A%20A_1%20%5Ctimes%20A_2 "\langle \hat M_1, \hat M_2 \rangle \doteq \langle \hat N_1', \hat N_2' \rangle : A_1 \times A_2")
    。

    递归即可......感觉像是在用自然语言写 Agda

-   ![\\times](https://latex.codecogs.com/svg.image?%5Ctimes "\times")-E-L.
    递归

-   ![\\times](https://latex.codecogs.com/svg.image?%5Ctimes "\times")-E-R.
    递归

-   ![\\times](https://latex.codecogs.com/svg.image?%5Ctimes "\times")-![\\beta](https://latex.codecogs.com/svg.image?%5Cbeta "\beta")-L.
    ![\\Gamma \\vdash \\langle M_1 , M_2 \\rangle \\cdot 1 \\equiv M_1 : A_1](https://latex.codecogs.com/svg.image?%5CGamma%20%5Cvdash%20%5Clangle%20M_1%20%2C%20M_2%20%5Crangle%20%5Ccdot%201%20%5Cequiv%20M_1%20%3A%20A_1 "\Gamma \vdash \langle M_1 , M_2 \rangle \cdot 1 \equiv M_1 : A_1")
    。 证明
    ![\\langle \\hat  M_1 , \\hat M_2  \\rangle \\cdot 1 \\doteq \\hat M_1\' \\in A_1](https://latex.codecogs.com/svg.image?%5Clangle%20%5Chat%20%20M_1%20%2C%20%5Chat%20M_2%20%20%5Crangle%20%5Ccdot%201%20%5Cdoteq%20%5Chat%20M_1%27%20%5Cin%20A_1 "\langle \hat  M_1 , \hat M_2  \rangle \cdot 1 \doteq \hat M_1' \in A_1")
    。明显有
    ![\\langle \\hat M_1 , \\hat M_2 \\rangle \\cdot 1 \\longmapsto \\hat M_1](https://latex.codecogs.com/svg.image?%5Clangle%20%5Chat%20M_1%20%2C%20%5Chat%20M_2%20%5Crangle%20%5Ccdot%201%20%5Clongmapsto%20%5Chat%20M_1 "\langle \hat M_1 , \hat M_2 \rangle \cdot 1 \longmapsto \hat M_1")
    ，如果有
    ![\\hat M_1 \\doteq \\hat M_1 \'](https://latex.codecogs.com/svg.image?%5Chat%20M_1%20%5Cdoteq%20%5Chat%20M_1%20%27 "\hat M_1 \doteq \hat M_1 '")
    的话能够根据定义得到
    ![\\langle \\hat M_1 , \\hat M_2 \\rangle \\cdot 1 \\doteq \\hat M_1 \' \\in A_1](https://latex.codecogs.com/svg.image?%5Clangle%20%5Chat%20M_1%20%2C%20%5Chat%20M_2%20%5Crangle%20%5Ccdot%201%20%5Cdoteq%20%5Chat%20M_1%20%27%20%5Cin%20A_1 "\langle \hat M_1 , \hat M_2 \rangle \cdot 1 \doteq \hat M_1 ' \in A_1")
    。

-   ![\\times](https://latex.codecogs.com/svg.image?%5Ctimes "\times")-![\\beta](https://latex.codecogs.com/svg.image?%5Cbeta "\beta")-R.
    差不多

-   ![\\times](https://latex.codecogs.com/svg.image?%5Ctimes "\times")-![\\eta](https://latex.codecogs.com/svg.image?%5Ceta "\eta").
    ![\\Gamma \\vdash M \\equiv \\langle M \\cdot 1,  M \\cdot 2 \\rangle : A_1 \\times A_2](https://latex.codecogs.com/svg.image?%5CGamma%20%5Cvdash%20M%20%5Cequiv%20%5Clangle%20M%20%5Ccdot%201%2C%20%20M%20%5Ccdot%202%20%5Crangle%20%3A%20A_1%20%5Ctimes%20A_2 "\Gamma \vdash M \equiv \langle M \cdot 1,  M \cdot 2 \rangle : A_1 \times A_2")
    给定了
    ![\\Gamma \\vdash M : A_1 \\times A_2](https://latex.codecogs.com/svg.image?%5CGamma%20%5Cvdash%20M%20%3A%20A_1%20%5Ctimes%20A_2 "\Gamma \vdash M : A_1 \times A_2")
    。证明
    ![\\hat M \\doteq \\langle \\hat M\' \\cdot 1 , \\hat M\' \\cdot 2 \\rangle \\in A_1 \\times A_2](https://latex.codecogs.com/svg.image?%5Chat%20M%20%5Cdoteq%20%5Clangle%20%5Chat%20M%27%20%5Ccdot%201%20%2C%20%5Chat%20M%27%20%5Ccdot%202%20%5Crangle%20%5Cin%20A_1%20%5Ctimes%20A_2 "\hat M \doteq \langle \hat M' \cdot 1 , \hat M' \cdot 2 \rangle \in A_1 \times A_2")
    。 根据
    ![\\doteq](https://latex.codecogs.com/svg.image?%5Cdoteq "\doteq")
    在类型
    ![A_1 \\times A_2](https://latex.codecogs.com/svg.image?A_1%20%5Ctimes%20A_2 "A_1 \times A_2")
    上的定义。需要有
    ![\\hat M \\cdot 1 \\doteq \\langle \\hat M\' \\cdot 1 , \\hat M \' \\cdot 2 \\rangle \\cdot 1](https://latex.codecogs.com/svg.image?%5Chat%20M%20%5Ccdot%201%20%5Cdoteq%20%5Clangle%20%5Chat%20M%27%20%5Ccdot%201%20%2C%20%5Chat%20M%20%27%20%5Ccdot%202%20%5Crangle%20%5Ccdot%201 "\hat M \cdot 1 \doteq \langle \hat M' \cdot 1 , \hat M ' \cdot 2 \rangle \cdot 1")
    和
    ![\\hat M \\cdot 2 \\doteq \\langle \\hat M\' \\cdot 1 , \\hat M \' \\cdot 2 \\rangle \\cdot 2](https://latex.codecogs.com/svg.image?%5Chat%20M%20%5Ccdot%202%20%5Cdoteq%20%5Clangle%20%5Chat%20M%27%20%5Ccdot%201%20%2C%20%5Chat%20M%20%27%20%5Ccdot%202%20%5Crangle%20%5Ccdot%202 "\hat M \cdot 2 \doteq \langle \hat M' \cdot 1 , \hat M ' \cdot 2 \rangle \cdot 2")
    。我们知道
    ![\\langle \\hat M \' \\cdot 1, \\hat M \' \\cdot 2\\rangle \\cdot 1 \\longmapsto \\hat M\' \\cdot 1](https://latex.codecogs.com/svg.image?%5Clangle%20%5Chat%20M%20%27%20%5Ccdot%201%2C%20%5Chat%20M%20%27%20%5Ccdot%202%5Crangle%20%5Ccdot%201%20%5Clongmapsto%20%5Chat%20M%27%20%5Ccdot%201 "\langle \hat M ' \cdot 1, \hat M ' \cdot 2\rangle \cdot 1 \longmapsto \hat M' \cdot 1")
    可以知道上面这两个是显然的。

-   ![\\to](https://latex.codecogs.com/svg.image?%5Cto "\to")-I.
    ![\\Gamma \\vdash \\lambda (x.M_2) \\equiv \\lambda (x. N_2) : A_1 \\to A_2](https://latex.codecogs.com/svg.image?%5CGamma%20%5Cvdash%20%5Clambda%20%28x.M_2%29%20%5Cequiv%20%5Clambda%20%28x.%20N_2%29%20%3A%20A_1%20%5Cto%20A_2 "\Gamma \vdash \lambda (x.M_2) \equiv \lambda (x. N_2) : A_1 \to A_2").
    已知
    ![\\Gamma , x : A_1 \\vdash M_2 \\equiv N_2 : A_2](https://latex.codecogs.com/svg.image?%5CGamma%20%2C%20x%20%3A%20A_1%20%5Cvdash%20M_2%20%5Cequiv%20N_2%20%3A%20A_2 "\Gamma , x : A_1 \vdash M_2 \equiv N_2 : A_2")
    。证明
    ![\\lambda (x . \\hat M_2) \\doteq \\lambda (x. \\hat N_2\') \\in A_1 \\to A_2](https://latex.codecogs.com/svg.image?%5Clambda%20%28x%20.%20%5Chat%20M_2%29%20%5Cdoteq%20%5Clambda%20%28x.%20%5Chat%20N_2%27%29%20%5Cin%20A_1%20%5Cto%20A_2 "\lambda (x . \hat M_2) \doteq \lambda (x. \hat N_2') \in A_1 \to A_2")
    。 根据
    ![\\doteq](https://latex.codecogs.com/svg.image?%5Cdoteq "\doteq")
    在
    ![A_1\\to A_2](https://latex.codecogs.com/svg.image?A_1%5Cto%20A_2 "A_1\to A_2")
    上的定义可以指导，我们需要证明
    ![\\forall M_1 \\doteq M_1\' \\in A_1, \[M_1 / x\] \\hat M_2 \\doteq \[M_1\' / x\] \\hat N_2\'](https://latex.codecogs.com/svg.image?%5Cforall%20M_1%20%5Cdoteq%20M_1%27%20%5Cin%20A_1%2C%20%5BM_1%20%2F%20x%5D%20%5Chat%20M_2%20%5Cdoteq%20%5BM_1%27%20%2F%20x%5D%20%5Chat%20N_2%27 "\forall M_1 \doteq M_1' \in A_1, [M_1 / x] \hat M_2 \doteq [M_1' / x] \hat N_2'")。这需要证明
    ![\[M_1 / x\] \\circ \\gamma](https://latex.codecogs.com/svg.image?%5BM_1%20%2F%20x%5D%20%5Ccirc%20%5Cgamma "[M_1 / x] \circ \gamma")
    以及
    ![\[M_1\' / x\] \\circ \\gamma\'](https://latex.codecogs.com/svg.image?%5BM_1%27%20%2F%20x%5D%20%5Ccirc%20%5Cgamma%27 "[M_1' / x] \circ \gamma'")
    的
    ![\\doteq](https://latex.codecogs.com/svg.image?%5Cdoteq "\doteq")
    关系（实际上是记
    ![\\tau = \\mathrm{weaken}(\\gamma)](https://latex.codecogs.com/svg.image?%5Ctau%20%3D%20%5Cmathrm%7Bweaken%7D%28%5Cgamma%29 "\tau = \mathrm{weaken}(\gamma)")
    ，证明
    ![\\tau\[x \\mapsto M_1\] \\doteq \\gamma\' \[x \\mapsto M_1\'\]](https://latex.codecogs.com/svg.image?%5Ctau%5Bx%20%5Cmapsto%20M_1%5D%20%5Cdoteq%20%5Cgamma%27%20%5Bx%20%5Cmapsto%20M_1%27%5D "\tau[x \mapsto M_1] \doteq \gamma' [x \mapsto M_1']")
    ，这里的记号有点乱）。 得到了上面的
    ![\\doteq](https://latex.codecogs.com/svg.image?%5Cdoteq "\doteq")
    关系之后，递归。

-   ![\\to](https://latex.codecogs.com/svg.image?%5Cto "\to")-E.
    ![\\Gamma \\vdash \\mathsf{ap}(M ; M_1)\\equiv \\mathsf{ap}(N ; N_1) : A_2](https://latex.codecogs.com/svg.image?%5CGamma%20%5Cvdash%20%5Cmathsf%7Bap%7D%28M%20%3B%20M_1%29%5Cequiv%20%5Cmathsf%7Bap%7D%28N%20%3B%20N_1%29%20%3A%20A_2 "\Gamma \vdash \mathsf{ap}(M ; M_1)\equiv \mathsf{ap}(N ; N_1) : A_2")
    。 已知
    ![\\Gamma \\vdash M \\equiv N : A_1 \\to A_2](https://latex.codecogs.com/svg.image?%5CGamma%20%5Cvdash%20M%20%5Cequiv%20N%20%3A%20A_1%20%5Cto%20A_2 "\Gamma \vdash M \equiv N : A_1 \to A_2")
    并且
    ![\\Gamma \\vdash M_1 \\equiv N_1 : A_1](https://latex.codecogs.com/svg.image?%5CGamma%20%5Cvdash%20M_1%20%5Cequiv%20N_1%20%3A%20A_1 "\Gamma \vdash M_1 \equiv N_1 : A_1")
    。 证明
    ![\\mathsf{ap}(\\hat M ; \\hat M_1) \\doteq \\mathsf{ap}(\\hat N ; \\hat N_1) \\in A_2](https://latex.codecogs.com/svg.image?%5Cmathsf%7Bap%7D%28%5Chat%20M%20%3B%20%5Chat%20M_1%29%20%5Cdoteq%20%5Cmathsf%7Bap%7D%28%5Chat%20N%20%3B%20%5Chat%20N_1%29%20%5Cin%20A_2 "\mathsf{ap}(\hat M ; \hat M_1) \doteq \mathsf{ap}(\hat N ; \hat N_1) \in A_2")
    。 在
    ![\\Gamma \\vdash M \\equiv N : A_1 \\to A_2](https://latex.codecogs.com/svg.image?%5CGamma%20%5Cvdash%20M%20%5Cequiv%20N%20%3A%20A_1%20%5Cto%20A_2 "\Gamma \vdash M \equiv N : A_1 \to A_2")
    上面递归，得到
    ![\\hat M \\doteq \\hat N\' : A_1 \\to A_2](https://latex.codecogs.com/svg.image?%5Chat%20M%20%5Cdoteq%20%5Chat%20N%27%20%3A%20A_1%20%5Cto%20A_2 "\hat M \doteq \hat N' : A_1 \to A_2")
    于是能够根据定义，加上
    ![\\hat M_1 \\doteq \\hat N_1 : A_1](https://latex.codecogs.com/svg.image?%5Chat%20M_1%20%5Cdoteq%20%5Chat%20N_1%20%3A%20A_1 "\hat M_1 \doteq \hat N_1 : A_1")
    就能够得到结果

-   ![\\to](https://latex.codecogs.com/svg.image?%5Cto "\to")-![\\beta](https://latex.codecogs.com/svg.image?%5Cbeta "\beta").
    ![\\Gamma \\vdash \\mathsf{ap}(\\lambda(x. M_2) ; M_1) \\equiv \[M_1 / x\]M_2 : A_2](https://latex.codecogs.com/svg.image?%5CGamma%20%5Cvdash%20%5Cmathsf%7Bap%7D%28%5Clambda%28x.%20M_2%29%20%3B%20M_1%29%20%5Cequiv%20%5BM_1%20%2F%20x%5DM_2%20%3A%20A_2 "\Gamma \vdash \mathsf{ap}(\lambda(x. M_2) ; M_1) \equiv [M_1 / x]M_2 : A_2")
    。 已知
    ![\\Gamma , x : A_1 \\vdash M_2 : A_2](https://latex.codecogs.com/svg.image?%5CGamma%20%2C%20x%20%3A%20A_1%20%5Cvdash%20M_2%20%3A%20A_2 "\Gamma , x : A_1 \vdash M_2 : A_2")
    和
    ![\\Gamma \\vdash M_1 : A_1](https://latex.codecogs.com/svg.image?%5CGamma%20%5Cvdash%20M_1%20%3A%20A_1 "\Gamma \vdash M_1 : A_1")
    。 证明
    ![\\mathsf{ap}(\\lambda (x. \\hat M_2); \\hat M_1) \\doteq \[\\hat M_1\' / x\] \\hat M_2\' \\in A_2](https://latex.codecogs.com/svg.image?%5Cmathsf%7Bap%7D%28%5Clambda%20%28x.%20%5Chat%20M_2%29%3B%20%5Chat%20M_1%29%20%5Cdoteq%20%5B%5Chat%20M_1%27%20%2F%20x%5D%20%5Chat%20M_2%27%20%5Cin%20A_2 "\mathsf{ap}(\lambda (x. \hat M_2); \hat M_1) \doteq [\hat M_1' / x] \hat M_2' \in A_2")
    。

    根据
    ![\\mathsf{ap}(\\lambda (x . \\hat M_2) ; \\hat M_1) \\longmapsto \[\\hat M_1 / x \] \\hat M_2](https://latex.codecogs.com/svg.image?%5Cmathsf%7Bap%7D%28%5Clambda%20%28x%20.%20%5Chat%20M_2%29%20%3B%20%5Chat%20M_1%29%20%5Clongmapsto%20%5B%5Chat%20M_1%20%2F%20x%20%5D%20%5Chat%20M_2 "\mathsf{ap}(\lambda (x . \hat M_2) ; \hat M_1) \longmapsto [\hat M_1 / x ] \hat M_2")。
    然后根据第一个 premise 得到
    ![\\hat M_2 \\doteq \\hat M_2\'](https://latex.codecogs.com/svg.image?%5Chat%20M_2%20%5Cdoteq%20%5Chat%20M_2%27 "\hat M_2 \doteq \hat M_2'")；
    根据第二个 premise 得到
    ![\\hat M_1 \\doteq \\hat M_1\'](https://latex.codecogs.com/svg.image?%5Chat%20M_1%20%5Cdoteq%20%5Chat%20M_1%27 "\hat M_1 \doteq \hat M_1'")
    根据
    ![\\doteq](https://latex.codecogs.com/svg.image?%5Cdoteq "\doteq")
    的定义就有
    ![\[\\hat M_1 / x\] \\hat M_2 \\doteq \[\\hat M_1\' /x \] \\hat M_2 \'](https://latex.codecogs.com/svg.image?%5B%5Chat%20M_1%20%2F%20x%5D%20%5Chat%20M_2%20%5Cdoteq%20%5B%5Chat%20M_1%27%20%2Fx%20%5D%20%5Chat%20M_2%20%27 "[\hat M_1 / x] \hat M_2 \doteq [\hat M_1' /x ] \hat M_2 '")
    ，根据 head expansion 就能够证明想要的结果了。

-   ![\\to](https://latex.codecogs.com/svg.image?%5Cto "\to")-![\\eta](https://latex.codecogs.com/svg.image?%5Ceta "\eta").
    ![\\Gamma \\vdash M \\equiv \\lambda(x. \\mathsf{ap}(M; x)) : A_1 \\to A_2](https://latex.codecogs.com/svg.image?%5CGamma%20%5Cvdash%20M%20%5Cequiv%20%5Clambda%28x.%20%5Cmathsf%7Bap%7D%28M%3B%20x%29%29%20%3A%20A_1%20%5Cto%20A_2 "\Gamma \vdash M \equiv \lambda(x. \mathsf{ap}(M; x)) : A_1 \to A_2")。
    已知
    ![\\Gamma \\vdash M : A_1 \\to A_2](https://latex.codecogs.com/svg.image?%5CGamma%20%5Cvdash%20M%20%3A%20A_1%20%5Cto%20A_2 "\Gamma \vdash M : A_1 \to A_2")。
    证明
    ![\\hat M \\doteq \\lambda(x.\\mathsf{ap}(\\hat M\' ; x)) \\in A_1 \\to A_2](https://latex.codecogs.com/svg.image?%5Chat%20M%20%5Cdoteq%20%5Clambda%28x.%5Cmathsf%7Bap%7D%28%5Chat%20M%27%20%3B%20x%29%29%20%5Cin%20A_1%20%5Cto%20A_2 "\hat M \doteq \lambda(x.\mathsf{ap}(\hat M' ; x)) \in A_1 \to A_2")。

    需要证明后者，我们知道，应该证明
    ![\\forall M_1 \\doteq N_1 \\in A, \[M_1 / x\] \\hat M \\doteq \[N_1 / x\] (x. \\mathsf{ap}(\\hat M\' ; x)) \\in A_2](https://latex.codecogs.com/svg.image?%5Cforall%20M_1%20%5Cdoteq%20N_1%20%5Cin%20A%2C%20%5BM_1%20%2F%20x%5D%20%5Chat%20M%20%5Cdoteq%20%5BN_1%20%2F%20x%5D%20%28x.%20%5Cmathsf%7Bap%7D%28%5Chat%20M%27%20%3B%20x%29%29%20%5Cin%20A_2 "\forall M_1 \doteq N_1 \in A, [M_1 / x] \hat M \doteq [N_1 / x] (x. \mathsf{ap}(\hat M' ; x)) \in A_2")。
    对于
    ![\[N_1 / x\](x. \\mathsf{ap}(\\hat M\' ; x))](https://latex.codecogs.com/svg.image?%5BN_1%20%2F%20x%5D%28x.%20%5Cmathsf%7Bap%7D%28%5Chat%20M%27%20%3B%20x%29%29 "[N_1 / x](x. \mathsf{ap}(\hat M' ; x))")
    来说，其应该是
    ![\\mathsf{ap}(\\hat M\'; N_1)](https://latex.codecogs.com/svg.image?%5Cmathsf%7Bap%7D%28%5Chat%20M%27%3B%20N_1%29 "\mathsf{ap}(\hat M'; N_1)")
    ，然后我们知道
    ![\\mathsf{ap}(\\hat M\' ; N_1) \\longmapsto \[N_1 / x\] \\hat M\'](https://latex.codecogs.com/svg.image?%5Cmathsf%7Bap%7D%28%5Chat%20M%27%20%3B%20N_1%29%20%5Clongmapsto%20%5BN_1%20%2F%20x%5D%20%5Chat%20M%27 "\mathsf{ap}(\hat M' ; N_1) \longmapsto [N_1 / x] \hat M'")
    于是剩下的就是 induction 了。

可以看见这里的这些证明并不是一些很难的东西。

这里还可以加上
![\\mathsf{nat}](https://latex.codecogs.com/svg.image?%5Cmathsf%7Bnat%7D "\mathsf{nat}")
和
![\\mathsf{conat}](https://latex.codecogs.com/svg.image?%5Cmathsf%7Bconat%7D "\mathsf{conat}")
的东西。说实话不想加。
