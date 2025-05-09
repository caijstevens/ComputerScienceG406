#ads 

To analyse recursive algorithms, have to look at recursive structure e.g MergeSort:
- split input of size n into two halves of equal size n/2
- independently recurse into each half
- merge resulting sorted sequences
- these normally give you recurrence

Methods to solve recurrences:
1. **Induction**
2. **Master Theorem**

### Solving recurrences by the Master Theorem

Can use if the recurrence is of the form $$T(n) = aT(n/b) + f(n)$$
for **constants** $a \geq 1$ and $b > 1$. 

Three cases:
1. If $f(n) = O(n^{\log_b(a) - \epsilon})$ for some constant $\epsilon > 0$ then $T(n) = \Theta (n^{\log_b(a)})$.
2. If $f(n) = \Theta (n^{\log_b(a)} \cdot (\log n)^k)$ with $k \geq 0$ then $T(n) = \Theta (n^{log_b(a)} (\log n)^{k+1}$).
3. If $f(n) = \Omega (n^{\log_b(a) + \epsilon})$ for some constant $\epsilon > 0$ and if $af(n/b) \leq cf(n)$ for some constant $c<1$ and all n large enough then $T(n) = \Theta (f(n))$.

