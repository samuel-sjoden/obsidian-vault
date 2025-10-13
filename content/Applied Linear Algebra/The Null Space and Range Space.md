The null space and range spaces are special [[Subspaces]] which describe the solution spaces of $A$. The null space is the space of all vectors in the domain that are mapped to the zero space. The range (equivalent to the column space or image) of the matrix is a subspace of the codomain which the matrix $A$ maps to. 

> [!Remeber]
> **Null Space** is an element of the [[Domain]]
> **Range Space** is an element of the [[Codomain]]

### Null Space

The null space (or kernel) of a [[Linear Transform]] is the subspace of the vector space which the linear transform maps directly to the zero space $\hat{0}$. The basis of this subspace are the basis vectors who form the subspace. All linear combinations of this basis are mapped to the [[Zero Space]] by $T$. More intutition on [[Null Space]]

It is a subspace of the [[Domain]] of A. 

To find this basis, find the nontrivial solutions to the [[Homogeneous Equation]] $Ax=0$. The linearly independent vectors that are not the zero vector that solve this equation are the null space of the matrix $A$

Mathematically, the null space of an $m \times n$ matrix is $A$ is the set of $$
N(A) = {x \in \mathbb{R}^n, Ax =\vec{0}}
$$
Where $N$ is a subspace in $\mathbb{R}^n$ and is the null space of $A$ 

> The number of free variables in the system is equal to the dimension of the null space. 

Say the solution to the homogeneous equation was $$
x = \begin{bmatrix}
-5x_{4} \\
2x_{3}-x_{4} \\
x_{3}\\
x_{4} \\
\end{bmatrix}
$$
This can be rewritten as a combination of two vectors
$$
N(A) = \text{span}\left\{ x_{3} \begin{bmatrix}
0 \\
2 \\
1 \\
0
\end{bmatrix} + x_{4} \begin{bmatrix}
-5 \\
-1 \\
0 \\
1 \\
\end{bmatrix}\right\} 
$$
>[!Theorem]
> Let $A=LU$ be and [[LU Decomposition]], then the null space of $A$ is equivalent to the null space of $U$. That is the same basis vectors for the null space of $A$ also span the null space of $U$

### Range Space


The $\text{range}$  of $A$ is defined to be a subspace of $\mathbb{R}^n$ defined by $$
\text{range}(A) = \left\{ y \in \mathbb{R}^n: y = Ax, x \in \mathbb{R}^n \right\}
$$
It is equivalent to the column space and image of $A$.  

>[!question]
>Is it the subspace of $\mathbb{R}^n$ that the linear transform $A$ maps to. 

**Example:**
$$
A = \begin{bmatrix}
1  & 3 & 1 & -1 \\
0 & 2 & 2 & -4 \\
0 & 0 & 0 & 0
\end{bmatrix}
$$
The first and second vectors are linearly independent and span the column space of the range/column space. [[Linear Dependence]]

$$
\text{dim}(R(A)) = 2
$$
$$
\text{dim}(N(A)) = 2
$$
The overall dimension of the domain of the transform.
$$
\text{dim}(R(A) + N(A)) = 4
$$
>[!Theorem]
> Let $A\in R^{m\times n}$ admits the LU decomposition and $\text{rank}(A) = r$, then the first $r$ columns of $L$ form the basis of $\text{range}(A)$ 

If the matrix does not have a full rank, then the last rows of the $L$ matrix will be nothing but zeros.


>[!Example]
>Let $A$ be such  that $A=LU$ where:
> $$
L=
\begin{bmatrix}
1 & 0 & 0 & 0 \\
-1 & 1 & 0 & 0 \\
2 & 1 & 1 & 0 \\
1 & 0 & -1 & 1
\end{bmatrix} $$
$$ U=
\begin{bmatrix}
1 & -2 & 0 & 5 & 1 \\
0 & 0 & 2 & -1 & 0 \\
0 & 0 & 0 & 0 & -1 \\
0 & 0 & 0 & 0 & 0
\end{bmatrix}$$

> Find a basis and determine the dimensions of $R(A)$ and $N(A)$


>[!Solution]
> $\text{rank(U)}=\text{rank(A)}=3$ and $dim(N(A))=2$. Then using the above theorem we can find a basis of $R(A)$ by looking at the first three columns of $L

> Then to find a basis of the null space like $Ux=0$ 

$$ Ux=
\begin{bmatrix}
1 & -2 & 0 & 5 & 1 \\
0 & 0 & 2 & -1 & 0 \\
0 & 0 & 0 & 0 & -1 \\
0 & 0 & 0 & 0 & 0
\end{bmatrix}
\begin{bmatrix}
x_{1} \\
x_{2} \\
x_{3} \\
x_{4} \\
x_{5}
\end{bmatrix}
= 0
$$
then we can find the relationships $x_{5}=0$
$$
\begin{align}
2x_{3}-x_{4}=0 \\
x_{1}-2x_{2}+5x_{4}+x_{5}=0
\end{align}
$$

then the general solution can be found to be 
$$
x= \begin{bmatrix}
x_{2}+5x_{3} \\
x_{2} \\
x_{3} \\
2x_{3} \\
0 \\
\end{bmatrix}
$$
which can be separated to form the basis of the null spaces of A
$$
N(A) = \left\{ \begin{bmatrix}
1 \\
1 \\
0 \\
0 \\
0
\end{bmatrix} 
, \begin{bmatrix}
5 \\
0 \\
1 \\
2 \\
0 \\

\end{bmatrix}
\right\}
$$
Where $x_{2},x_{3}$ are free variables.

>[!Question]
> What is the null space? I don't have an intuition as to why the solution of the free variables build the null space.
## Relationship Between $N(A)$ and $R(A)$
Since $N(A)$ and $R(A)$ are not subspaces of the same space, they are not directly related to each other through orthogonality. However, they are related to each other through the [[Matrix Transpose]] which makes them share spaces.

If $A$ is an $m\times n$ matrix and $A^{T}$ is an $n\times m$ matrix then:
$$
\begin{align}
N(A) \subseteq \mathbb{R}^{n} \\
R(A^{T})\subseteq \mathbb{R}^{n} \\
N(A^{T})\subseteq \mathbb{R}^{m} \\
R(A) \subseteq \mathbb{R}^{m}
\end{align}
$$
The subspaces are actually related though the [[Orthogonal Complement]]

