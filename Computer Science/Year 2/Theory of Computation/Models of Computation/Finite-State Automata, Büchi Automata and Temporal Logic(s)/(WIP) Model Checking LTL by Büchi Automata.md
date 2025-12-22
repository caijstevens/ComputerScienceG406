#wip #toc 

# Setup 

Given TS $\tau$ and LTL formula $\varphi$ both over same set of atomic propositions
- task is to decide if $\tau \models\varphi$
- means all runs of $\tau$ satisfy $\varphi$ 
- If both the runs of $\tau$ and the models of $\varphi$ are represented by Büchi Automata, can construct intersection and check for emptiness
- if empty, $\tau\models\varphi$, otherwise return $a,b\in(2^{AP})^*$ such that $ab^\omega$ is a run of $\tau$ that falsifies $\varphi$ 

# Proof 

1. Transforming TS into BA is trivial
	- move each label from state onto outgoing transitions and introduce new start state instead of multiple from TS
2. Constructing intersection of two BA is easy
	- by product and making sure that alternate infinitely often accepting states 
	- check for emptiness by checking if non-trivial connected component that contains accepting state and is reachable from start state 
3. Harder to transform LTL into equiv BA 
	- translate to generalised BA that has multiple sets of accepting states and acceptance condition that state per set visited infinitely often 
	- easy to turn GBA into equiv BA

# LTL into Büchi

### States 

Input is inf sequence of words $A_0A_1$ where each world $A_i\in 2^{AP}$. Special initial state $s_0$. Every other state has two components:
1. subset of AP that records current world (last seen input symbol)
2. subset of all subformulae of $\varphi$ that should be true in future 

State must be propositionally consistent.
- takes care of all boolean connectives 

### Transitions 

Transition from $s_1$ to $s_2$ labelled by $a\in 2^{AP}$ added if:
1. label $a$ matches first component of state $s_2$
2. state $s_1$ has subformula $\circ\varPsi$ iff state $s_2$ has subformula $\varPsi$
3. whenever state $s_1$ has subformula $\varphi_1\bigcup\varphi_2$:
	a) state $s_1$ has $\varphi_2$ or
	b) state $s_1$ has $\varphi_1$ and state $s_2$ has $\varphi_1\bigcup\varphi_2$
Partly takes care of until operator, but eventually $\varphi_2$ not guaranteed

### Acceptance and Start

Expansion $\varphi_1\bigcup\varphi_2\rightarrow\varphi_2\lor(\varphi_1\land\bigcirc(\varphi_1\bigcup\varphi_2))$ doesn't guarantee that $\varphi_2$ eventually happens.
- any infinite run that always has $\varphi_1\bigcup\varphi_2$ but never $\varphi_2$ is inconsistent.
- preventable by insisting that every run has states that have $\varphi_2$ or haven't got $\varphi_1\bigcup\varphi_2$ infinitely often.

>[!info] Theorem
>For every subformula of the form $\varphi_1\bigcup\varphi_2$, introduce accepting set of states $F_{\varphi_1\bigcup\varphi_2}$ that contains every state that has $\varphi_2$ or hasn't $\varphi_1\bigcup\varphi_2$.
- also introduce start state $s_0$ that has transition $s$ which is labelled with first component of $s$, and only if the formula $\varphi$ is in second component of $s$.

# Merging Accepting Sets 

A Generalised Büchi Automaton has $k$ accepting sets of states $F_1,\dots F_k$ and an infinite run with states $r_0,r_1,r_2,\dots$ accepts if there are infinitely many $r_j$s in each $F_i$

>[!danger] Proposition 
>Every Generalised Büchi Automaton is equivalent to some Büchi Automaton.

>[!check] Proof
>Let $\mathcal{M}$ be Generalised Büchi Automaton with accepting sets of states $F_1,\dots,F_k$. Create $k$ identical copies of $\mathcal{M}, \mathcal{M}_1,\dots\mathcal{M}_k$. The start state of the new automaton is the copy of the start state in $\mathcal{M}_1$. In each $\mathcal{M}_i$, replace each transition of the form $p\rightarrow^a q$ where $p\in F_i$ by transition $p\rightarrow^a r$ where $r$ is the copy of $q$ in $\mathcal{M}_{i+1}$ (in $\mathcal{M}_1$ if $i=k$). The set of accepting states in the new automaton could be any copy of the set $F_i$ in $\mathcal{M}_i$.



