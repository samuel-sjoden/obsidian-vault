### Checking if Cartesian Vectors are Linearly Dependent
##### Method 1.
Create a matrix from the vectors and form a homogeneous system. If there are non-trivial solutions to the homogeneous system, the vectors are linear combinations of each other.

If you end up with a row of zeros, this indicates that the coefficients can be any value and still produce the zero vector.
##### Method 2.
If the vectors form an $N \times N$ matrix, the finding the determinant of the matrix will indicate the dependence of the columns.

>[!motivation]
>What is the minimum number of vectors required to form a basis of some vector space.

### Finding A Basis in a Vector Space
If we have some set of vectors $\vec{u_{1}}, \vec{u_{2}, \dots \vec{u_{n}}}$  we want to determine if they form a **spanning set** that is they form a basis of the vector space.

Say there is some subspace $\mathbb{U}$ that is not just the zero space, there are many sets of vectors that form a basis, but it will always be the same number of vectors.

The zero vector is never a part of the basis.

$$
\mathbb{U} = \text{span}(\vec{u_{1}}, \dots,\vec{u_{4}}) \subset \mathbb{R}^4
$$

$$
\begin{bmatrix}
1 & 2 & 1 \\
1 & -2 & -1 \\
1 & 1 & 1 \\
1 & 0 & -1
\end{bmatrix} \rightarrow
\begin{bmatrix}
1 & 2 & 1 \\
0 & 1 & 0 \\
0 & 0 & 1 \\
0 & 0 & 0
\end{bmatrix}
$$
Zero row, therefore these vectors do not form a basis in $\mathbb{R}^4$ . Four pivot elements are required. What about for a subspace of $\mathbb{R}^4$?

$$
c_{1}\vec{u_{1}} + c_{2}\vec{u_{2}} + c_{3}\vec{u_{3}} = \vec{0}
$$
These vectors could form a basis here. There is three pivot elements. So for this subset of $\mathbb{R}^4$, these three vectors form a basis.

Then we can say that $$
\mathbb{U} = \text{span}(\vec{u_{1}}, \vec{u_{2}}, \vec{u_{3}})
$$
Forms a basis for $\mathbb{U}$. This subspace has dimension of three because its basis can be formed with three vectors.

$$
\begin{cases}
\text{dim}(\mathbb{R}^n) = n \\
\end{cases}
$$
### The Null Space and Range Space

The null space and range spaces are special [[Subspaces]].

##### Null Space

The null space of an $m \times n$ matrix is $A$ is the set of $$
N(A) = {x \in \mathbb{R}^n, Ax =\vec{0}}
$$
Where $N$ is a subspace in $\mathbb{R}^n$ and is the null space of $A$ 

The number of free variables in the system is equal to the dimension of the null space. 

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
> Let $A=LU$ be and LU decomposition, then the null space of $A$ is equivalent to the null space of $U$. That is the same basis vectors for the null space of $A$ also span the null space of $U$

##### Range Space

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
The first and second vectors are linearly independent and span the column space of the range/column space.

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
