 #ds 

# Theory of Counting 

>[!info] Definition 
>**Combinatorics** is the study of arrangements of objects and the counting of objects with certain properties
- stemmed from gambling
- considered founded by Pascal and Leibniz

>[!success] Applications 
>- Algorithm complexity
>- Password complexity for cyber attacks and defence
>- Storage space for enumerated objects

### The Product Rule

>[!error] The Product Rule 
>If a procedure can be broken into sequence of two tasks:
>- $n_1$ ways to do first task
>- $n_2$ ways to do second
>- total number of procedure completion methods is $n_1n_2$

>[!hint] The Product Rule (Generalised)
>If task sequence $T_1,T_2,\dots,T_m$ can be done in $n_1,n_2,\dots,n_m$ ways, and every task arrives after occurrence of previous, then there are $n_1\times n_2\times \dots\times n_m$ ways to perform tasks.

### The Sum Rule 

>[!danger] The Sum Rule
>Consider two independent sub-tasks (we need to do only one of the two). If the first task can be done in $n_1$ ways and the second can be done in $n_2$ ways then there are $n_1+n_2$ ways to finish the task

### Inclusion-Exclusion Principle 

If two tasks can be done same time then there is chance of overcounting since some methods counted twice
- add up number of ways to do each task, then subtract number of ways to do both tasks

$$|A\cup B| = |A| +|B| - |A\cap B|$$
$$|A\cup B\cup C| = |A| +|B| + |C| - |A\cap B| - |A\cap C| - |B\cap C| + |A\cap B\cap C|$$

### Permutation and Combination 

>[!info] Permutations 
>The counting of distinct objects in ordered arrangement
>- Number of $r$-permutations of set with $n$ elements is:
>  $P(n,r)=n\times (n-1)\times (n-2)\times\dots\times (n-r+1)$

$$P(n,r)=\frac{n!}{(n-r)!}$$

With repeats, where $n_1$ objects are of one type, etc:
$$P(n; n_1, n_2, \dots, n_k) = \frac{n!}{n_1!n_2!\dots n_k!}$$

>[!info] Combination 
>Counting of distinct objects in **unordered** arrangement
>- example of unordered: "$a,b$" and "$b,a$" are the same 

$$C(n,r) = \binom{n}{r} = \frac{n!}{(n-r)!\times r!}$$


>[!success] Proof
![[Screenshot 2025-10-09 at 10.32.38.png]]

![[Screenshot 2025-10-09 at 10.37.52.png]]
# Set Theory 

>[!info] Set 
>A **set** is a collection of unordered objects 
>- size: $|L|$
>- union: $L\cup R$
>- complement: $\overline{L}$
>- subtract: $L- R$
>- subset: $L \subseteq R$
![[Screenshot 2025-10-09 at 10.41.57.png]]

# Theory of Probability

>[!info] Probability
>The formalisation of uncertain events
>- enables to infer probabilities of interest based on assumptions and observations 

>[!info] Statistics
>Practice of the science of collecting and analysing data 
>- deals with experimental data 
>- extracting knowledge from data

Probability terms:
- An **experiment** is a procedure that yields one of given set of outcomes
- The **sample space** of experiment is set of possible outcomes
- An **event** is any subset of sample space

$S$ is finite sample space of all outcomes
- all outcomes equally likely
- $E$ is event where $E\subseteq S$
- Probability of occurrence of event $E$ is:
$$P(E) = \frac{|E|}{|S|}$$
- $0\leq P(E)\leq 1$
- $P(S) = 1$
- for disjoint events $E_1,E_2,\dots,E_n$, $$P(E_1\cup E_2\cup\dots\cup E_n) = \Sigma^{n}_{i=1}P(E_i)$$

Probability axiom rules:
- Complement rule: $P(\overline{E}) = P(S-E) = P(S) - P(E) = 1 - P(E)$
- Impossible rule: $P(\emptyset) = 0$
- General addition rule: $P(E_1\cup E_2) = P(E_1) + P(E_2) - P(E_1\cap E_2)$
- if $E_1\subseteq E_2$ then $P(E_1)\leq P(E_2)$


