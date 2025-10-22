QR decomposition seperates a matrix $A$, which must have full row rank, into two matrices $Q,R$. The matrix $Q$ spans all of $\mathbb{R}^{m}$, providing an orthonormal basis for the [[The Null Space and Range Space| The Range Space]] $R(A)$ and it's [[Orthogonal Complement]] $R(A)^{\perp}$

### Finding QR
The QR decomposition can be found using the [[The Grahm-Schmidt Method]] to form an orthognormal basis from the columns of $A$, given that $A$ has a full column rank (the $a$ column vectors are linearly independent).

>[!Clarification]
> The columns of $A$ being linearly independent does not mean they can span all of the [[Codomain]], $\mathbb{R}^{m}$. It means that the vectors are mapped one-to-one (uniquely) when a solution exists. If $m>n$ then not all $b$ have a solution. By rank nullity theorem, the dimension of the null space of this matrix is $0$.  This means that $A$ is just mapping lower dimensional vectors (in $\mathbb{R}^{n}$) onto a hyperplane in the higher dimensional space $\mathbb{R}^{m}$. This hyperplane is $R(A)$. The space orthogonal to the hyperplane is $R(A)^{\perp}$. 

The column vectors $a$ can be written as projections onto the orthonormal basis $w$ like so:
$$
\begin{align}
a_{1} = \left< a_{1},w_{1} \right> w_{1} \\
a_{2}=\left< a_{2},w_{1} \right> w_{1} + \left< a_{2},w_{2} \right> w_{2} \\
\dots \\
a_{n}=\left< a_{n},w_{1} \right> w_{1} + \dots \left< a_{n},w_{n} \right> w_{n}
\end{align}
$$
From how we contstucted the basis $w$.

The $Q_{1}$ matrix can be the orthonormal basis $w$ and the $R_{1}$ matrix is an upper triangular matrix with all of the dot products.

Now this is sufficent to represent $A$ where:
$$
A=Q_{1}R_{1}
$$
But it can be further generalized so that $Q$ contains an orthonormal basis for all of $\mathbb{R}^{m}$. The remaining $\{ w_{n+1}, \dots, w_{m} \}$ are the basis for $R(A)^{\perp}$ and the original $\{ w_{1},\dots ,w_{n} \}$ form a basis for $R(A)$.

$$
\boxed{A=QR=\begin{bmatrix}
Q_{1} & Q_{2}
\end{bmatrix}
\begin{bmatrix}
R_{1} \\
\mathbf{0}
\end{bmatrix}}
$$
The zero is present because all of the linear combinations of $a$ are orthogonal to all elements in the basis $Q_{2}$

>[!Question]
> If I have a full column rank, $\text{rank}(A)=n$, that means that my columns are linearly independent. 