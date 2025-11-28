 #toc 

Boolean state in which number of **atomic propositions** are true or false 
- **discrete linear time** is an infinite sequence of states $A_0A_1\dots$  with state $A_0$ and time 0 being the current state 
- want to add **temporal modalities** such as "always $a$" - $\square a$, "eventually $a$" - $\diamond a$, "next $a$" - $\circ a$ 
- e.g. "infinitely often $a$" - $\square\diamond a$ 

# Syntax 

Given finite set of atomic propositions, Boolean connectives plus two temporal modalities, $\circ$ (next) and $\cup$ (until)

>[!info] LTL Formula 
>A formula in LTL is defined by the following grammar:
>$\varphi := \text{true}|a|\varphi_1\land\varphi_2|\lnot\varphi|\circ\varphi|\varphi_1\cup\varphi_2$
>where $a\in AP$ and $\varphi_1,\varphi_2$ are LTL formulae
- other modalities can be expressed, e.g. $$\diamond a = true\cup a$$$$\square a = \lnot\diamond\lnot a$$
# Formal Semantics 

A world is labelled by the AP that are true in it, so is letter from alphabet $2^{AP}$
- word $\sigma$ is infinite sequence of worlds, $\sigma\in(2^{AP})^\omega$

>[!info] Definition 
>The **satisfaction relation**, $\sigma\models\varphi$ where $\sigma=A_0A_1\dots$ is a word and $\varphi$ is a formula, is defined recursively by: 
>1. $\sigma\models true$
>2. $\sigma\models a \text{ iff } a\in A_0$
>3. $\sigma\models\varphi_1\land\varphi_2 \text{ iff } \sigma\models\varphi_1\text{ and }\sigma\models\varphi_2$
>4. $\sigma\models\lnot\varphi\text{ iff }\sigma\not\models\varphi$
>5. $\sigma\models\bigcirc\varphi\text{ iff }A_1\dots\models\varphi$ 
>6. $\sigma\models\varphi_1\cup\varphi_2\text{ iff there is }i\geq 0 \text{ such that }A_i\dots\models\varphi_2\text{ and }A_j\dots\models\varphi_1$ for all $0\leq j<i$

The set of all words that satisfy a formula $\varphi$ is called $Words(\varphi)$ 

# Transition Systems 

>[!info] Transition System 
>A **transition system** $TS$ has:
>1. finite set of states $S$
>2. transition relation $\rightarrow\subseteq S\times S$, which is left-total
>3. set of initial states $I\subseteq S$
>4. finite set of atomic propositions $AP$ 
>5. labelling function $L:S\rightarrow 2^{AP}$
- the transitions may be labelled by a finite set of actions $Act$ in which case the transition relation becomes $\rightarrow\subseteq S\times Act\times S$

# Execution of a TS 

>[!info] Definition 
>A **run** of $TS$ is an infinite sequence of states $$s_0\rightarrow s_1\rightarrow\dots$$ where $s_0\in I$ which produces infinite trace $\sigma\in (2^{AP})^\omega, \sigma=L(s_0)L(s_1)\dots$
>
>The set of all possible traces of the TS is called $Traces(TS)$.
>
>Finally, TS satisfies $\varphi,TS\models\varphi$ if $Traces(TS)\subseteq Words(\varphi)$ i.e. if each trace of TS satifies formula $\varphi$
>
>Thus, it is possible that $TS\not\models\varphi$ **and** $TS\not\models\lnot\varphi$

# Example 

![[Screenshot 2025-11-10 at 10.27.30.png]]
$$Traces(TS)=(\{a,b\}\{a,b\})^*a^\omega\cup\{a,b\}^\omega$$
The following hold: $s_1\models\bigcirc(a\land b)$ but $s_3\not\models\bigcirc(a\land b)$, thus $TS\not\models\bigcirc(a\land b)$; on the other hand, $TS\models\square(\lnot b\rightarrow \square(a\land\lnot b))$.













