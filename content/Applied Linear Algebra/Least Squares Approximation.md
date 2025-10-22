The least squares approximation is used to fit data with a linear model. To maximze the effectiveness of the approximation, we want to minimize the error of the prediction at all points. We want to find an equation $y = ax +b$ that fits all of the data $(x_{i},y_{i})$ as best as possible.

Say we generate a function $f(x)$ that makes a linear approximation of the data. To see how effective that this function is in predicting we need to create an [[Error Analysis |Error Function]]. 
$$
S = d_{1}^{2}+ d_{2}^{2} +\dots + d_{n}^{2}
$$
The squares are used so that there is no "negative error" that would subtract from the $S$ making the model appear more effective than it is.

### Motavation
Often data will not follow a perfect pattern and contradict iself. That is we will have to many equations for the number of variables (we are overconstrained). But, by making approximations, we can fit to the overcontraining and model the underlying trends outside of the [[Training Neural Nets|Baysian Error]]

## Best Approximation
When choosing our function $f$, we want to determine how good it is at approximating. Say the data point is $\mathbf{b}$ which exists in $\mathbb{R}^{m}$. Our mapping $A\mathbf{z}$ may not be directly on it, that is $\mathbf{b}$ may exist in the [[Orthogonal Complement]] of the transformation $A$. 

Our goal is just to minimize $\left| \left| \mathbf{b} - A\mathbf{z} \right| \right|$, so we just wonder if there is some vector $\mathbf{z}$ in $\mathbb{R}^{n}$ that minimizes the distance, a topic discussed in finding the [[Orthogonal Projection]]. 

## Least Squares

### Linear Modelling
For a linear model our $\mathbf{z}$ is $\begin{bmatrix}r_{0} \\ r_{1} \end{bmatrix}$ for a function $f(x) = r_{0} + r_{1}x$.  Given a set of data points $(x_{1},y_{1}),(x_{2},y_{2})\dots(x_{m},y_{m})$, the $\mathbf{b}$ vector are the points we are trying to match, the $y$. So our system looks like this:
$$
\begin{align}
M = \begin{bmatrix}
1 & x_{1} \\
1 & x_{2} \\
1  & \dots\\
1 & x_{m}

\end{bmatrix} \quad
\mathbf{b} = \begin{bmatrix}
y_{1} \\
y_{2} \\
\dots \\
y_{m}
\end{bmatrix} \\
 \\
M\mathbf{r} = \mathbf{b}
\end{align}
$$
> [!Important]
> Note to solve this we need $\text{rank}(M) = n$.
>  This requires that all of the inputs $x$ are unique and that we have more data points that equations $m\geq n$

$$
\begin{align}
M^{T}M\mathbf{z} = M^{T}\mathbf{b} \\
\mathbf{z} = \left( M^{T}M \right)^{-1}M^{T}\mathbf{b}
\end{align}
$$
>[!Intuition]
> We are looking for the vector $\mathbf{z}$ that solves the equation $A\mathbf{z}=\text{proj}_{R(A)}\mathbf{b}$, since we know by the [[Projection Theorem]] that this what will produce the shortest distance $\left| A\mathbf{z}-\mathbf{b} \right|$. Since we know that the vector then $A\mathbf{z}-\mathbf{b}$ is in the [[Orthogonal Complement]] of the [[The Null Space and Range Space| range space]], and we know that all elements of the complement space of the range space is in the null space of $A^{T}$, therefore:
> $$
 A^{T}(A\mathbf{z}-\mathbf{b}) = 0$$

## Using [[QR Decomposition]] For Least Squares
Since $Q$ is an [[Orthogonal Matrix]], it has the property that $Q^{T}=Q^{-1}$.  So we can write the equation out like:
$$
R_{1}\mathbf{z}=Q_{1}^{-1}\mathbf{b}=Q^{T}\mathbf{b}
$$
What makes $QR$ decomposition so useful is that we can find the size of the error of the fit $A$ with:
$$
\left| \left| A\mathbf{x}-\mathbf{b} \right|  \right| =\left| \left| Q_{2}^{T}\mathbf{b} \right|  \right|
$$
>[!Intuition]
> The size of the error function is depenent on the size of the stuff that $A$ cannot map to. $Q_{2}$ is an orthonormal basis for $R(A)^{\perp}$, and so it descibes the size of $\mathbf{b}$ that cannot be reached by $A$. 

## Generalized Approach
We can use least squares approximation with various sets of functions, not just polynomial. The problem still needs to be linear and the functions must be linearly independent.

**Arbitrary Modelling Function**
$$
\hat{y} = c_{1}f_{1}(t) + c_{2}f_{2}(t) + \dots + c_{n}f_{n}(t)
$$
Where we solve for the $c$ vector that minimizes the MSE.

