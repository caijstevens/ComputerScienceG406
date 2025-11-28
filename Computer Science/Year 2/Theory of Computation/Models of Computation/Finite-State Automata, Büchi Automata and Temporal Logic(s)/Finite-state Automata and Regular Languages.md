 #toc 

# Finite-state Automata

> [!info] Definition 
>
> **LTL**: Linear Time Logic 

>[!info] Definition
>A **Deterministic Finite-state Automaton** is a 5-tuple ($Q, \Sigma, \delta, q_0, F$) where:
>- $Q$ is a finite set of **states**
>- $\Sigma$ is a finite **alphabet**
>- $\delta:Q\times\Sigma\mapsto Q$ is the **transition function**
>- $q_0 \in Q$ is the **start state**
>- $F \subseteq Q$ is the set of **accept states**

![[Screenshot 2025-10-06 at 10.15.30.png]]
>[!info] Definition
>Let $M = (Q, Σ, δ , q_0, F$)  
be a DFA and $w = w_1w_2\dots w_n$ be a  
word over $\Sigma$. $M$ accepts $w$ if there  
is a sequence of states $r_0, r_1, r_2, \dots r_n$ satisfying the following conditions: 
>1. $r_0 = q_0$,  
>2. $\delta (r_i, w_{i+1}) = r_{i+1}$ for every $i, 0 \leq i \leq n − 1$, and  
>3. $r_n \in F$.  


# Regular Languages 

>[!info] Definition 
>A language is called a **regular language** if some DFA recognises it. The DFA $M$ **recognises** the language $L$ if $L = \{w | M \space\text{accepts}\space w\}$

### Regular Operations 

- Boolean (set-theoretic):
	- **union** $A\cup B = \{x|x\in A \space\text{or}\space x\in B\}$
	- **intersection** $A\cap B = \{x|x\in A \space\text{and}\space x\in B\}$
	- **difference** $A \backslash B = \{x|x\in A \space\text{and}\space x\notin B\}$
	- **complement** $\overline{A} = \Sigma^* \backslash A$

- Language theory specific:
	- **concatenation** $A\circ B = \{xy|x\in A\space\text{and}\space y\in B\}$
	- **star** (the set of all finite-length strings over the alphabet) $A^* = \{x_1x_2\dots x_k|k\geq 0 \space\text{and}\space x_i\in A\space\text{for every}\space i, 1\leq i\leq k\}$
		- or $A^* = \bigcup\limits^{\infty}_{i=0}A^i$

### Regular Expression 

>[!info] Definition 
>A **Regular Expression** defines a language, are logically equivalent to DFAs ($RE\equiv DFA$)
>The definition is **inductive** (recursive), meaning there are initial REs and new REs can be found by means of regular operations.

>[!todo] Rules 
>$R$ is a Regular Expression over the alphabet $\Sigma$ if $R$ is:
>1. $a$ for some $a\in\Sigma$
>2. $\epsilon$ (empty string)
>3. $\emptyset$ (empty set)
>4. $(R_1\cup R_2)$ where $R_1$ and $R_2$ are REs 
>5. $(R_1\circ R_2)$ where $R_1$ and $R_2$ are REs
>6. $R^*_1$ where $R_1$ is a RE

# Combining Automata

Should run $M_1$ and $M_2$ on input in **parallel**
- use **pairs of states** and define transition function:

![[Screenshot 2025-10-06 at 10.44.51.png]]

The components of the new automaton $M = (Q, \Sigma, \delta, q_0, F)$ are:
1. $Q = Q_1\times Q_2$
2. $\delta((s,u),a) = (\delta_1(s,a), \delta_2(u,a))$ for every $s\in Q_1, u\in Q_2, a\in \Sigma$
3. $q_0 = (q_1,q_2)$
4. $F = \{(s,u)\in Q|s\in F_1\space\text{or}\space u\in F_2\}$

### Concatenation 

$w \in L_1\circ L_2$ only if $x$ and $y$ such that $w=xy, x\in L_1, y\in L_2$
- run $M_1$ on prefix of $w$ and then run $M_2$ on the rest
- requires guessing and therefore **non-deterministic**

# Non-deterministic Finite Automaton 

>[!info] NFA
>A **NFA** is a 5-tuple ($Q, \Sigma, \delta, q_0, F$) where:
>- $Q$ is a finite set of states
>- $\Sigma$ is a finite alphabet
>- $\delta : Q\times (\Sigma\cup\{\epsilon\})\rightarrow\mathcal{P}(Q)$ is the transition function
>- $q_0\in Q$ is the start state
>- $F\subseteq Q$ is set of accept states 

![[Screenshot 2025-10-13 at 10.20.49.png]]
Problems:
1. more than one next possible state ($q_1$ read 1)
2. $\epsilon$-transition ($q_2$) allows you to skip to the next state without reading the next symbol
3. no next state (can't go anywhere if $q_3$ read 0)

Convention states that a single step in a computation consists of first reading the next input symbol followed by taking any number of $\epsilon$-transitions
![[Screenshot 2025-10-13 at 10.26.00.png]]
- this shows that you can choose to stay in $q_1$ or move to $q_2$ if $q_1$ read 1, and you can skip from $q_2$ to $q_3$ without reading the next input. (reflects figure above)
### Computation of a NFA

>[!info] Definition 
>Let $M = (Q,\Sigma,\delta,q_0,F)$ be a NFA and $w=w_1w_2\dots w_n$ be a word over $\Sigma\cup\{\epsilon\}$
>($\epsilon$s can be freely added inside actual word e.g. $010110$ can be $\epsilon 01\epsilon\epsilon 01\epsilon 10$)
>$M$ accepts $w$ if there exists a sequence of states $r_0,r_1,r_2,\dots,r_n$ satisfying the following conditions:
>- $r_0 = q_0$
>- $r_{i+1}\in\delta(r_i,w_{i+1})$ for every $i,0\leq i\leq n-1$
>- $r_n\in F$

### Difference between DFA and NFA

**DFA**:
- there is a unique computation path.
- either accepts or rejects.
**NFA**:
- there are many computational paths.
- NFA accepts if at least one computation accepts
- only rejects if all computations reject 

**Non-deterministic computation**:
- try all possible paths and accept iff at least one accepts
- always make the "right" choice if there is one

# Converting a NFA into a DFA

At any time there are number of possible states NFA computation can be into.
- DFA needs to keep track of all of these
- DFA's states will be subsets of NFA's state-set
![[Screenshot 2025-10-13 at 10.35.04.png]]

>[!info] Formal Definition 
>Let $N=(Q,\Sigma,\delta,q_0,F)$ be a NFA recognising language $L$. Assume $N$ has no $\epsilon$-transitions. Will construct a DFA $M=(Q',\Sigma,\delta',q_0',F')$
>1. $Q' = \mathcal{P}(Q)$
>2. For $R\in Q'$ and $a\in\Sigma$ let $$\delta'(R,a)=\{q\in Q|q\in\delta(r,a)\space\text{for some}\space r\in R\}$$ or $$\delta'(R,a)=\bigcup_{r\in R}\delta(r,a)$$
>3. $q_0'=\{q_0\}$
>4. $F'=\{R\in Q'|\exists r\in R, r\in F\}$

Taking care of $\epsilon$-transitions:
- for $R\subseteq Q$ let $$E(R)=\{q|q\space\text{is reachable from R through a number of}\space\epsilon\text{-transitions}\}$$
Now:
1. $Q' = \mathcal{P}(Q)$
2. For $R\in Q'$ and $a\in\Sigma$ let $$\delta'(R,a)=\{q\in Q|q\in E(\delta(r,a))\space\text{for some}\space r\in R\}$$ or $$\delta'(R,a)=\bigcup_{r\in R}E(\delta(r,a))$$
3. $q_0'=E(\{q_0\})$
4. $F'=\{R\in Q'|\exists r\in R, r\in F\}$

>[!success] Theorem 
>Every NFA has an equivalent DFA 

>[!tip] Corollary 
>A language is regular iff some NFA recognises it

>[!example] Example 
>Transform the following NFA into a DFA:
>![[Screenshot 2025-10-13 at 10.47.33.png]]
>Having performed the transformation, the result is the following DFA:
>![[Screenshot 2025-10-13 at 10.47.53.png]]
>We can remove the redundant states/transitions (marked in red). The {} state is really needed.


# Closure under Regular Operations 

**Union**:
- already proven via Cartesian-product construction. $$A\cup B=\{x|x\in A\text{ or }x\in B\}$$![[Screenshot 2025-10-13 at 10.54.34.png]]
**Concatenation**:
$$A\circ B=\{xy|x\in A\text{ and }y\in B\}$$
![[Screenshot 2025-10-13 at 10.54.42.png]]
**Star**:
$$A^*=\{x_1x_2\dots x_k|k\geq 0\text{ and }x_i\in A\text{ for every }i, 1\leq i\leq k\}$$
![[Screenshot 2025-10-13 at 10.54.52.png]]

# Equivalence of Finite Automata and Regular Expressions 

>[!info] Theorem 
>A language is regular if and only if some Regular Expression describes it.

>[!success] Proof 
>Given RE $R$, construct NFA that recognises $L(R)$ by Structural Induction 
>1. base case: all initial REs can be implemented by NFAs
>2. inductive step: already proven that regular languages are closed under regular operations

**Note: Constructing an RE from a DFA is harder**
# Generalised Non-Deterministic Finite Automaton (GNFA)

![[Screenshot 2025-10-20 at 10.16.16.png]]

1. Single start state with no incoming edges
2. Single accept state with no outgoing edges 
3. Every transition labelled with a RE

# DFA into RE

1. Convert $n$-state DFA into **equivalent** $n+2$-state GNFA
2. Eliminate all internal states of GNFA while preserving language recognised by automaton 
3. $L(R)=L(DFA)$ so all done :)

### Internal State Elimination 

Pick state $r$ for elimination. For every two states $u$ and $v$ (neither being $r$), do:
![[Screenshot 2025-10-20 at 10.21.01.png]]
- form regular expression for route from $u$ to $v$ via $r$ and concatenate into one expression
- then you can delete $r$
- (be careful if $u\equiv v$ e.g. if a path goes from $u$ to $r$ and then back to $u$)
# Non-Regular Languages 

To prove language is **regular**:
1. construct DFA (or NFA) that recognises $L$
2. produce regular expression that describes $L$

To prove language is **not regular**:
- cannot be recognised by **any DFA**
- assume DFA that recognises $N$, then use an **adversary argument** against DFA to get contradiction 
- e.g. a DFA fails if a state is both an accept state and a non-accept state simultaneously

An **adversary argument** is a choice of input/response that forces a DFA to make a mistake that leads to non-acceptance, and proves that no DFA can recognise the given language

### Pumping Lemma 

>[!question] Lemma 
>For every regular language $L$, there is number $p$ (pumping length of $L$) such that every word $w\in L$ of length $\geq p$ can be divided into three parts, $w=xyz$ for following conditions:
>1. $xy^iz\in L$ for every $i\in\mathbb{N}$ (including $i=0$)
>2. $y$ is a non-empty string
>3. the length of string $xy\leq p$

>[!hint] Example 
>The language $L=\{0^n1^n|n\in\mathbb{N}\}$ is not regular.
>
>Take word $0^p1^p\in L$ where $p$ is pumping length of $L$. If $0^p1^p=xyz$ and $|xy|\leq p$ then $x=0^i, y=0^j$ and $z=0^{p-i-j}1^p$. But then $xy^2z=0^{p+j}1^p\notin L$ as $|y|>0$, i.e. $j>0$
- this is because the first $p$ characters are 0s and $|xy\leq p$ so both $x$ and $y$ must only be 0s
- this leaves $z=0^{p-i-j}$ because $xyz=0^p1^p$
- but $xy^iz$ should also be in $L$ for $i\geq 0$
- trying $i=2$ gives $xy^2z=0^i(0^j)^20^{p-i-j}1^p=0^{p+j}1^p$
- this does not fit the lemma as $p+j\neq p$ so it cannot fit the language of $0^n1^n$.

This lemma utilises the **pigeon-hole principle** which states that for a $p$-state automaton with any word with more than $p$ symbols, at least one state must be visited twice.
- you can pump that part of the input as many times as you like without changing acceptance

# DFA Minimisation

Finding DFA that recognises same language as given DFA with **as few states as possible**
- finitely many possibilities 
- have to check if DFAs recognise same language 

>[!info] Minimisation
>An algorithm that **minimises** a DFA finds an equivalent DFA with the minimal number of states. Answers following important questions:
>1. What is the smallest (statewise) DFA recognising same language?
>2. Do the two DFAs recognise the same language?

>[!success] Algorithm Outline 
>1. Remove all states not reachable from start state 
>2. Contract set of states that are **equivalent** into single state 
>
>Two states are equivalent if an accepted word starting from one is also accepted when starting from the other (and vice versa)

### Equivalent and Distinguishable States 

>[!warning] Extended Transition Function:
>Let DFA $M=(Q,\Sigma,\delta,q_0,F)$ be given, and let $\hat{\delta}:Q\times\Sigma^*\rightarrow Q$ be defined as:
>$$\hat{\delta}(s,\epsilon)=s$$
>$$\hat{\delta}(s,w_1w_1\dots w_n)=\hat{\delta}(\delta(s,w_1),w_2\dots w_n)$$
>
>States are equivalent if $$\{w\in\Sigma^*|\hat{\delta}(s,w)\in F\}=\{w\in\Sigma^*|\hat{\delta}(t,w)\in F\}$$
- otherwise distinguishable

>[!important] Team Splitting Algorithm 
>1. Disqualify states that are unreachable from start
>2. Split states into accept and non-accept states
>3. For every team and input, check if all states from team agree on passing input. Otherwise, split team into maximal subteams that agree 
>4. Return teams as sets of equivalent states 

