 #toc 

**Büchi Automaton** accepts word in $\Sigma^{\omega}$ (all infinite words over alphabet $\Sigma$) if state sequence exists $r_0,r_1,r_2\dots\in Q^{\omega}$ for following conditions:
1. $r_0=q_0$
2. $(r_i,w_{i+1},r_{i+1})\in\Delta$ for every $i,i>0$
3. there are infinitely many $r_i$s in $F$

Transition relation defined as $\Delta\subseteq Q\times\Sigma\times Q$
- gives set of possible next states 

# $\omega$-Regular Languages

**Regular language** for **infinite words**

>[!tip] Conditions:
>1. $A\cup B$ where both $A$ and $B$ are $\omega$-regular (union)
>2. $AB$ where $A$ is **regular** and $B$ is $\omega$-regular (concatenation)
>3. $A^\omega$, an infinite sequence of words from $A$ where $A$ is regular and doesn't contain the empty word 

>[!info] Theorem 
>An $\omega$-regular language is $\omega$-regular iff some NDBA recognises it

Example:
- For $\Sigma$ being $\{0,1\}$
	- $L_1=\{a\in\Sigma^\omega|a$ contains infinitely many 0s$\}$
	- $L_2=\{a\in\Sigma^\omega|a$ contains finitely many 1s$\}$

### Limits of Regular Languages 

>[!info] Definition 
>Let $A$ be regular language. Limit of $A, \lim{A}$ is language $\{a\in\Sigma^\omega|a$ has infinitely many prefixes in $A\}$
>
>An $\omega$-language is a limit of a RL iff some deterministic BA recognises it.
>

Buchi Automata is a translation format for Linear Temporal Logic (LTL)




