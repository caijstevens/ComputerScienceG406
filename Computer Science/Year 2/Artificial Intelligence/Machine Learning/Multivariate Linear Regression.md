#ai 

# Multiple Variables 

Hypothesis function: 
$$h_\theta(x)=\theta_0+\theta_1 x_1 +\theta_2 x_2+\theta_3 x_3+\theta_4 x_4$$
$$h_\theta(x)=[\theta_0,\theta_1,\theta_2,\theta_3,\theta_4]\begin{bmatrix}
1 \\x_1\\x_2\\x_3\\x_4
\end{bmatrix}=[\theta_0,\theta_1,\theta_2,\theta_3,\theta_4]\begin{bmatrix}
x_0 \\x_1\\x_2\\x_3\\x_4
\end{bmatrix}
$$
- $x_0=1$

$$h_\theta(x)=\theta^Tx$$
- multivariate linear regression

# Cost Function and Gradient Descent 

|                                                      | Univariate Linear Regression                                                                                                                                                                                                                                   | Multivariate Linear Regression                                                                                                                                                                                                                                                                                                                                                                      |
| ---------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Hypothesis Function                                  | $\hat{y}=h_\theta(x)=\theta_0+\theta_1 x$                                                                                                                                                                                                                      | $h_\theta(x)=\theta_0+\theta_1 x_1+\theta_2 x_2+\dots+\theta_n x_n$                                                                                                                                                                                                                                                                                                                                 |
| Independent Variable                                 | $x$                                                                                                                                                                                                                                                            | $x_m=\begin{bmatrix} x_0 \\x_1\\ \dots \\ x_n \end{bmatrix}\in \mathbb{R}^{n+1}, (x_0=1)$                                                                                                                                                                                                                                                                                                           |
| Model Parameters                                     | $\theta_0,\theta_1$                                                                                                                                                                                                                                            | $\theta_m=\begin{bmatrix} \theta_0 \\ \theta_1\\ \dots \\ \theta_n \end{bmatrix}\in \mathbb{R}^{n+1}, h_\theta(x)=\theta^T x$                                                                                                                                                                                                                                                                       |
| Cost Function                                        | $J(\theta_1,\theta_1)=\frac{1}{2m}\sum\limits^m_{i=1}(h_\theta(x)^{(i)}-y^{(i)})^2$                                                                                                                                                                            | $J(\theta)=\frac{1}{2m}\sum\limits^m_{i=1}(h_{\theta_m}(x_m)^{(i)}-y^{(i)})^2$                                                                                                                                                                                                                                                                                                                      |
| Partial derivative of $J$ with respect to parameters | $\frac{\delta J}{\delta\theta_0}(\theta_0,\theta_1)=\frac{1}{m}\sum\limits^m_{i=1}(h_\theta(x)^{(i)}-y^{(i)})$ $\frac{\delta J}{\delta\theta_1}(\theta_0,\theta_1)=\frac{1}{m}\sum\limits^m_{i=1}(h_\theta(x)^{(i)}-y^{(i)})x_1^{(i)}$                         | $\frac{\delta J}{\delta\theta_0}(\theta)=\frac{1}{m}\sum\limits^m_{i=1}(h_\theta(x)^{(i)}-y^{(i)})x_0^{(i)}$ $\frac{\delta J}{\delta\theta_1}(\theta)=\frac{1}{m}\sum\limits^m_{i=1}(h_\theta(x)^{(i)}-y^{(i)})x_1^{(i)}\space\space\space\space\space$ $\dots$ $\frac{\delta J}{\delta\theta_n}(\theta)=\frac{1}{m}\sum\limits^m_{i=1}(h_\theta(x)^{(i)}-y^{(i)})x_n^{(i)}$                        |
| Gradient Descent                                     | Repeat until convergence {<br>$\theta_0:=\theta_0-\alpha\cdot \frac{\delta J}{\delta\theta_0}(\theta_0,\theta_1)$<br>$\theta_1:=\theta_1-\alpha\cdot \frac{\delta J}{\delta\theta_1}(\theta_0,\theta_1)x^{(i)}$<br>} simultaneously update $\theta_0,\theta_1$ | Repeat until convergence {<br>$\theta_0:=\theta_0-\alpha\cdot \frac{\delta J}{\delta\theta_0}(\theta_0,\theta_1,\dots,\theta_n)$ $\theta_1:=\theta_1-\alpha\cdot \frac{\delta J}{\delta\theta_1}(\theta_0,\theta_1,\dots,\theta_n)$ $\dots$ $\theta_n:=\theta_n-\alpha\cdot \frac{\delta J}{\delta\theta_n}(\theta_0,\theta_1,\dots,\theta_n)$<br>} simultaneously update $\theta_0,\dots,\theta_n$ |

# Vectorisation

### Vectorisation of Hypothesis Function 

$$h_\theta(x)=\theta^Tx$$
**Parameter Vector:** $\theta=\begin{bmatrix} \theta_0 \\ \theta_1\\ \dots \\ \theta_n \end{bmatrix}\in \mathbb{R}^{n+1}, h_\theta(x)=\theta^T x$

**Variable Vector:** $x_m=\begin{bmatrix} x_0 \\x_1\\ \dots \\ x_n \end{bmatrix}\in \mathbb{R}^{n+1}, (x_0=1)$


For whole training set: $$X=\begin{bmatrix}
(x^{(1)})^T \\ (x^{(2)})^T \\ (x^{(3)})^T \\ (x^{(4)})^T \\ \dots \\ (x^{(m)})^T
\end{bmatrix},\space\space \theta=\begin{bmatrix}
\theta_0 \\ \theta_1 \\ \theta_2 \\\vdots \\\theta_j\\\vdots \\ \theta_n
\end{bmatrix}$$
$$X\theta=\begin{bmatrix}h_\theta(x^{(1)}) \\ h_\theta(x^{(2)}) \\ h_\theta(x^{(3)}) \\ \dots \\ h_\theta(x^{(i)}) \\ \dots \\ h_\theta(x^{(m)})
\end{bmatrix}$$
Therefore: $$h_\theta(X)=X\theta$$
### Vectorisation of Cost Function 

$$X\theta-y=\begin{bmatrix}
h_\theta(x^{(1)})-y^{(1)} \\ h_\theta(x^{(2)})-y^{(2)} \\ h_\theta(x^{(3)})-y^{(3)} \\ \vdots \\ h_\theta(x^{(m)})-y^{(m)} \\
\end{bmatrix}$$
$$(X\theta-y)^T\cdot (X\theta-y)=\sum\limits^m_{i=1}(h_\theta(x^{(i)})-y^{(i)})^2$$
$$J(\theta)=\frac{1}{2m}(X\theta-y)^T(X\theta-y)$$

### Vectorisation of Gradient Descent 

$$\theta_n:=\theta_n-\alpha\frac{1}{m}x^T_n(X\theta-y)\rightarrow \theta:=\theta-\alpha\frac{1}{m}X^T(X\theta-y)$$

Repeat until convergence {
$$\theta:=\theta-\alpha\frac{1}{m}X^T(X\theta-y)$$
}

# Normal Equation 

### Univariate 

![[Screenshot 2025-11-03 at 15.41.30.png]]

### Multivariate 

$$\theta=(X^TX)^{-1}X^Ty$$

### Normal Equation vs Gradient Descent 

| Normal Equation                                                     | Gradient Descent                        |
| ------------------------------------------------------------------- | --------------------------------------- |
| Non-iterative                                                       | Multiple iterations                     |
| No learning rate                                                    | Experimental learning rate              |
| Doesn't need feature scaling                                        | Needs feature scaling                   |
| Slow if training set very large:<br>$(X^TX)^{-1}$ could be $O(n^3)$ | Works well with very large training set |
| Doesn't work for many cases                                         | Works with other types of task too      |
