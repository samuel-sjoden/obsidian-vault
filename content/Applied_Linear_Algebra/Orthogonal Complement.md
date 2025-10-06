### Orthogonal Vectors
We say that $x,y\in \mathbb{R}^n$ are orthogonal of the [[Inner Product]] is zero.

The vectors are Orthonormal if the vectors are both Orthogonal and their [[Norm]] is one. $$
||u||=1
$$
>[!Theorem]
> If there are $n$ vectors in $\mathbb{R}^n$ and they are orthogonal, they are also linearly independent.

>[!Proof]
> If you take the linear combination of the vectors with constants $c_{1},c_{2},\dots,c_{n}$ and made it the solution to the homogenous equation, the vectors are linearly dependent if the only solution to the equation is if $\vec{c}=\vec{0}$.
>
> Taking an inner product with a vector in the set, since each vector in the set is orthogonal, each inner product is zero. The RHS is also zero. The only term that does not go to zero is when the inner product is taken with itself leaving $$
c_{k}<x_{k},x_{k}> = 0
$$


### Orthogonal Subspaces
The orthogonal subspace to another subspace is a subspace where the basis of the subspace is orthogonal to all of the basis vectors in the original basis.

Mathematically:
$$
\begin{align}
U_{1},U_{2}\subset \mathbb{R}^n \\
U_{1} \perp U_{2} \\
\end{align}
$$
**Example**:
Let $$
U = \text{span}(\begin{bmatrix}
1 \\
1 \\
1
\end{bmatrix})
$$
Find all subspaces in $\mathbb{R}^3$ that are orthogonal to $U$

We need a vector $\begin{bmatrix}x \\ y \\ z \end{bmatrix}$ that has a zero inner product with the basis of $U$

$$
1(x) + 1(y) + 1(z) = 0
$$

This vector constitutes the null space of the system of the vector conjured and the basis vector of $U$
$$
\begin{bmatrix}
1 & x \\
1 & y \\
1 & z  \\
\end{bmatrix}
\vec{x}=0
$$
Solving this set of equations will give a basis for a subspace that is orthogonal to $U$

### Orthogonal Complement
If there is some subspace $U$ of $\mathbb{R}^n$ the orthogonal complement of the subspace is the set of all vectors that are orthogonal to the elements of $U$. That is all of the vectors that produce a zero inner product with the vectors in the $U$ subspace.

The sum of a subspace and its orthogonal complement form the whole space that they are a subspace of.

It is the largest possible orthogonal subspace to $U$.

$$
U= \text{span}\left\{ \begin{bmatrix}
1 \\
0 \\
0
\end{bmatrix} \right\} 
$$
then solving the equation $$
\left< \begin{bmatrix}
1 \\
0 \\
0
\end{bmatrix}, \begin{bmatrix}
x \\
y \\
z
\end{bmatrix} \right> =0
$$
We see that $x=0$ and that $y,z$ are free variables.
$$
V=\text{span}\left\{ \begin{bmatrix}
0 \\
1 \\
0
\end{bmatrix}, \begin{bmatrix}
0 \\
0 \\
1
\end{bmatrix} \right\} 
$$
The sum of both subspaces is the entire subspace.

Geometrically, if $U$ is the x axis, $V$ is the $y-z$ plane. Putting both subspaces together, you can represent all vectors in $\mathbb{R}^3$ 

>[!Theorem]
> Let $U\subset \mathbb{R}^n$ be a subspace
> Then:
> 1. $U\perp$ is a subspace
> 2. $(U\perp)\perp$ is just $U$
> 3. The orthogonal complement of the subspace only constituting the zero vector is just $\mathbb{R}^n$. The zero vector is perpendicular to all vectors.
> 4. $\text{dim}\left( U \right) + \text{dim}\left( U\perp \right)=n$
> 5. Let the set of vectors forming the basis of the subspace $U$ have $l$ linearly independent vectors, then the amount of basis vectors required to form $U\perp$ is $n-l$

If the sum of the dimension of two subspaces is greater than the dimension of the overall space, then $U_{1},U_{2}$ cannot be orthogonal complements of each other. Think of two planes in $\mathbb{R}^3$, when they intersect they form a line. This line exists in both subspaces. If you were to form a basis of $U_{2}$ and found the subspace who's basis was all but vectors that are linearly independent of the line of intersection, then that subspace would be the orthogonal complement of $U_{1}$.

#### Relationship to the Null Space

All vectors that are present in the [[Null Space]] of the subspace $U$ are present in the orthogonal complement ($U\perp$).

The fundamental subspaces of an $m\times n$ matrix $A$ are $N(A),R(A),N(A^T),R(A^T)$.  That is the [[The Null Space and Range Space]] of A and its transpose

>[!Question]
> What is meant by fundemental subspaces of the matrix? 

$$
\begin{align}
N(A)\subset \mathbb{R}^n \\
N(A^T)\subset \mathbb{R}^m \\
R(A)\subset \mathbb{R}^m \\
R(A^T)\subset \mathbb{R}^n
\end{align}
$$
An important relationship:
$$
\begin{align}
N(A)=R(A^T)^\perp \\
R(A^T)^\perp=\{ x: x\perp U\forall x\in R(A^T) \} \\
=\{ x:x\perp A^Ty,\forall y \} \\
=\{ x:\left< x,A^Ty \right> =0 \quad\forall y \} \\
=\{ x:\left< Ax,y \right> =0, \forall y \} \\
=\{ x:Ax=0 \}
\end{align}
$$
Which the solutions to $Ax=0$ form the null space.
$$
R(A^T)^\perp=N(A)

$$
> [!Question]
>  How does taking a transpose of a matrix change its mapping? Can we determine the range and null space of A transpose if we know it for A?

>[!Example]
> Find a basis of $N(A), R(A), N(A^T), R(A^T)$.
> $$
A=\begin{bmatrix}
1 &  0 & 0 \\
1 &  1  & 0 \\
0  & -2 & 1
\end{bmatrix}
\begin{bmatrix}
2 & 3 & 1 & 4 \\
0 & -1 & 0 & 1 \\
0 & 0 & -2 & 2
\end{bmatrix}
>$$
> To find the range space of A, we recall that the range space of U is the same as the range space as A. Looking at U, there are three pivot columns, which means that rank(U)=3.
> $$
R(A)= \text{span}\{ \begin{bmatrix}
1 \\
1 \\
0 \\
>
\end{bmatrix}, \begin{bmatrix}
0 \\
1 \\
-2 \\
\end{bmatrix}, \begin{bmatrix}
0 \\
0 \\
1
\end{bmatrix} \}
>$$
> This matrix spans all of the space, therefore the orthogonal complement of the range space of a is just the zero space. The A matrix takes a vector from the fourth dimension and maps it to the third. It spans all of the third dimension.
>
> To find $N(A)$ we find what the solution space to $Ux=0$ is.
> 
> 

The range space of the transpose of A is the same subspaces as the orthogonal complement of the null space of A

>[!Question]
> This does not seem intuitive to me. I think I need to understand the relationship between the subspaces of $A$ and $A^T$ in general







