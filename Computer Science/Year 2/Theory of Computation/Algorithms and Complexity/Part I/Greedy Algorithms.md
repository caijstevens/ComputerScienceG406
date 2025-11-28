#toc 

# The Knapsack Problem 

Variant 1: The $0 - 1$ **knapsack problem**:
- "a thief robs a store and finds $n$ items. Item $i$ is worth $v_i$ euros and weighs $w_i$ kilos. The thief can carry at most $W$ kilos in knapsack."
- Which items can he take to maximise profit?

Variant 2: The **fractional knapsack problem**:
- Same setup, but this time the thief can take fractions of items.

We can assume that knapsack is not big enough to carry all items.
$$W<w_1+\dots+w_n$$

**Fractional knapsack problem** is solvable through **greedy** strategy.
1. Compute the "value per kilo" $r_i=v_i/w_i$
2. Sort items by value per kilo in non-increasing order
3. Take as much as possible of item with greatest "value per kilo" then take as much as possible of item with next greatest "value per kilo" etc, until total weight equals knapsack capacity $W$.

>[!success] Example 
>Suppose $W=10kg$ and:
>- $v_1=4\texteuro, w_1=4kg$
>- $v_2=10\texteuro, w_2=2kg$
>- $v_3=12\texteuro, w_3=8kg$
>- $v_4=20\texteuro, w_4=5kg$
>
>Therefore:
>- $r_1=1, r_2=5, r_3=1.5, r_4=4$
>So greedy strategy takes all of item 2, all of item 4, and 3 kilos of item 3 for a total value of $10+20+(3\times 1.5)=34.5\texteuro$

# Running Time 

Greedy strategy:
1. Computing $r_i$ for each $i$ can be done in $\Theta(n)$
2. Sorting the $r_i$ array can be done in $\Theta(n\log n)$
3. Selecting the items can be done in $\Theta(n)$

Therefore, the worst-case running time is $\Theta(n\log n)$


# Greedy Strategy for the 0-1 Knapsack Problem 

Same algorithm does NOT work.
![[Screenshot 2025-10-16 at 16.23.48.png]]

# Correctness of greedy for fractional knapsack 

$n$ items are sorted by $r_i=v_i/w_i$ in non-increasing order i.e $$r_1\geq r_2\geq \dots \geq r_n$$
Two items $p$ and $q$ with $r_p=r_q$ are considered to be equivalent, so $$r_1>r_2>\dots>r_n$$
The total available amount of item $i$ is $w_i$. Let $k$ be such that $$w_1+\dots+w_k\leq W$$ and $$w_1+\dots+w_{k+1}>W$$
Let $x=(x_1,\dots,x_n$) denote a solution: $0\leq x_i\leq w_i$ is the amount the thief takes of item $i$ for $i=1,\dots,n$. The total value stolen is then $\Sigma^n_{i=1}r_ix_i$.

The greedy solution $x$ is given by:
- $x_i=w_i$ for $1\leq i\leq k$,
- $x_{k+1} = W - (w_1+\dots+w_k)$,
- $x_i=0$ for $k+2\leq i\leq n$

Let $x^* = (x^*_1,\dots,x^*_n)$ be an optimal solution.

Objective: prove that $x^*=x$
- suppose $x^*\neq x_i$, then $x^*_i<x_i$ for some $i\leq k+1$
- let $j := \min\{i:x^*_i<x_i\}$
- Also, $x^*_{\ell} > x_{\ell}$ for some $\ell > j$
![[Screenshot 2025-10-16 at 16.46.19.png]] 

Exercise:
1. Check that $y$ is a valid solution, i.e. $0\leq y_i\leq w_i$ for all $1\leq i\leq n$ and that $y_1+\dots+y_n=W$
2. Check that $y$ is a better solution than $x^*$, i.e. $\Sigma^n_{i=1}r_iy_i>\Sigma^n_{i=1}r_ix^*_i$. **CONTRADICTION**

# A Special Case of 0-1 Knapsack

Suppose that, in a $0-1$ knapsack instance, the orders of the items:
- when sorted by **decreasing value $v_i$**, and
- when sorted by **increasing weight $w_i$**,
are the same (i.e. $v_1\geq v_2\geq\dots\geq v_n$ and $w_1\leq w_2\leq\dots\leq w_n$)

This can be solved by a similar greedy algorithm to the fractional knapsack problem.

# Greedy Algorithms for some Optimisation Problems

>[!info] Optimisation problem 
>In an **optimisation problem** we are looking for a solution that optimises a value.
>An **optimal solution** is a solution with optimal value. There can be many optimal solutions.

An algorithm for an optimisation problem goes through a sequence of steps
- each step has set of choices
- greedy algorithm makes in every step the choice that **looks to be the best at the moment**.
- This is called a **greedy** or **locally optimal** choice.

Not all optimisation problems can be solved by greedy algorithms.

# Task Scheduling 

Task scheduling problem:
- Set $T$ of $n$ tasks. Every task $i$ has start time $s_i$ and finish time $f_i$.
- every task to be performed on machine, can only execute one task at a time.
- two tasks $i,j$ can be scheduled on same machine iff **non-conflicting**, i.e. $f_i<s_j$ or $f_j<s_i$
- goal is to schedule all tasks using smallest number of machines

Correctness idea:
- suppose algorithm gives $k$ machines but there exists a better schedule with at most $k-1$ machines.
- let $i$ be the first task scheduled on machine $k$
- by construction of the algorithm, when we schedule task $i$, each of the machines $1,\dots,k-1$ contains tasks that are in conflict with task $i$
- all these $k-1$ tasks all conflict with each other too
- impossible to schedule all tasks in $k-1$ machines

Running time:
- $O(n\log n)$ time