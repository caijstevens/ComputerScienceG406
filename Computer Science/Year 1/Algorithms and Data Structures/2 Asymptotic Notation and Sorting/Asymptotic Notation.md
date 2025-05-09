#ads

### Elementary Functions

Should know the following derivations/proofs:
- $log_b(xy) = log_b(x) + log_b(y)$ 
- $log_b(x/y) = log_b(x) - log_b(y)$ 
- $log_b(x^y) = y \cdot log_b(x)$ 
- $log_b(b^x) = x$
- $b^{a \cdot log_b(x)} = x^a$  
- $log_b(x) = \frac{{log_a(x)}}{{log_a(b)}}$ 

### Time Complexity
The **time complexity** of an algorithm can be expressed in terms of the **number of basic operations** used by the algorithm when the input has a particular size.

Basic operations:
- additions
- multiplications
- comparisons of two numbers
- swaps
- assignments of values to variables

The **space complexity** of an algorithm is expressed in terms of the memory required by the algorithm for an input of a particular size.

The **worst-case time complexity** of an algorithm can be expressed in terms of the largest number of basic operations used by the algorithm when the input has a particular size.
- the use of time complexity usually means worst-case time complexity
- average-case analysis is also important, involves average number of operations over all inputs of given size.

Difficult to compute exact number of operations.
- usually not needed, we normally find **upper bounds** for worst-case analysis
- the bounds give possibility to estimate **growth** of number of operations when input size increases.
- estimating operation number is important when input size **large** 

### Big-O Notation
Let f and g be functions from the set of integers or the set of real numbers to the set of real numbers. We say that f is O(g) if there are constants C and k such that $$|f(x)| \leq C \cdot |g(x)|$$ whenever $x \geq k$.

After a certain point (k), the absolute value of f(x) is bounded from above by C times the absolute value of g(x).

In terms of time complexities, f(x) is no worse than $C \cdot g(x)$ for all relatively large input sizes x.

C and k are **witnesses** to the relationship $f(x)$ is $O(g(x))$. If there is a pair of witnesses, then there are infinitely many pairs of witnesses C' and k' such that $C \leq C'$ and $k \leq k'$.

| Big-O form         | Name        |
| ------------------ | ----------- |
| $O(1)$             | constant    |
| $O(log n)$         | logarithmic |
| $O(n)$             | linear      |
| $O(n logn)$        | n log n     |
| $O(n^2)$           | quadratic   |
| $O(n^3)$           | cubic       |
| $O(n^k)$           | polynomial  |
| $O(c^n)$ for c > 1 | exponential |
Sum rule:
- If $f_1(x)$ is $O(g_1(x))$ and $f_2(x)$ is $O(g_2(x))$, then $f_1(x) + f_2(x)$ is $O(max\{|g_1(x)|, |g_2(x)|\})$.

Product rule:
- If $f_1(x)$ is $O(g_1(x))$ and $f_2(x)$ is $O(g_2(x))$, then $f_1(x) \cdot f_2(x)$ is $O(g_1(x) \cdot g_2(x))$.

### Lower bounds: Big-Omega notation
Lower bound function used to help find best function that matches growth rate.

Let f and g be functions from the set of integers or the set of real numbers to the set of real numbers. We say that f is $\Omega (g)$ if there are constants C and k such that $$|f(x)| \geq C \cdot |g(x)|$$ whenever $x > k$.

This also implies that $f(x)$ is $\Omega (g(x))$ if and only if $g(x)$ is $O(f(x))$.

### Same Order Growth Rates

Let f(x) and g(x) be functions from the set of real numbers to the set of real numbers. We say that f(x) is $\Theta (g(x))$ if f(x) is $O(g(x))$ and f(x) is $\Omega (g(x))$.

This also means that f(x) is O(g(x)) and g(x) is O(f(x)).

### Little-o notation
A tool used for disregarding or neglecting small-order terms.

Let f(x) and g(x) be functions from the set of real numbers to the set of real numbers. f(x) is o(g(x)) when $$\lim_{x\to\infty} \frac{f(x)}{g(x)}=0$$ The fraction above tends towards zero as x tends towards infinity.

f(x) being o(g(x)) implies that f(x) is O(g(x)).

If f(x) is **not** O(g(x)), there must be a value of x > k such that $|f(x)| > C \cdot |g(x)|$ . Therefore either $\lim_{n\to\infty} \frac{f(x)}{g(x)}$ does not exist or it is not 0. Therefore f(x) is not o(g(x)).

A function is called **sublinear** if it grows slower than any linear function. 
- That is, if f(x) is o(x), or if $\lim_{x\to\infty} \frac{f(x)}{x}=0$ 

### Little-omega notation

$\omega$ is to o what $\Omega$ is to O

### General rules

1. If $f_1(x)$ is $o(g(x))$ and $f_2(x)$ is $o(g(x))$, then $f_1(x) + f_2(x)$ is $o(g(x))$.
2. If $f_1(x)$ is $O(g(x))$ and $f_2(x) is $o(g(x))$, then $f_1(x) + f_2(x)$ is $O(g(x))$.
3. If $f_1(x)$ is $\Theta (g(x))$ and $f_2(x)$ is $o(g(x))$, then $f_1(x) + f_2(x)$ is $\Theta (g(x))$. 