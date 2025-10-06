Orthogonal projection is often used in data processing when trying to find the shortest distance from a subspace. This is often a vector orthogonal to the subspace to the point of interest.


We want to generalize the shortest distance between two vectors. 
We define the projection of a vector onto another as:
> [!Definition]
> $$
\text{proj}_{u}x=\left< x,u \right> / \left< u,u \right> u$$
The projection vector is in the span of $u$.

The important vector is $x-\text{proj}_{u}x$ which is orthogonal to $u$. and is the shortest distance from somewhere on the span of $u$ to the endpoint of the $x$ vector.
### Matrix Representation
This vector can be represented as a linear transform of the $x$ vector
$$
\text{proj}_{u}x = \frac{uu^T}{||u||^2}x= Px
$$
where $P$ is the projection matrix. This can be further simplify the definition with 

$$
\text{Inner Product } \equiv u^Tu = 
\begin{bmatrix}
u_{1} & u_{2} & \dots & u_{n}
\end{bmatrix}
\times
\begin{bmatrix}
u_{1} \\
u_{2} \\
\dots \\
u_{n}
\end{bmatrix}
 = c
$$
And similarly,
$$
\text{Outer product } \equiv uu^T
$$
Which is a matrix multiplication which produces an $n\times n$ matrix. So the definition of the projection of x onto u is x transformed by $P$ which is the outer product of u scaled by one over its inner product.

> Intuitively, how does $P$ create a mapping who's range is $u$?

If $P$ is a matrix that has rank of 1 if $u$ is one. This makes sense because rank is the dimension of the image.
## Projecting Onto A Subspace
If we have a subspace $U \subset \mathbb{R}^n$ and has an orthogonal basis. This is satisfied if:
1. There is a spanning set $\{ u_{1},u_{2}, \dots, u_{m} \}$
2. Each vector is the basis is orthogonal$\left< u_{i}, u_{j} \right> =c\delta_{ij}$

If $c=1$, for all $i=j$, then the basis is orthonormal. If the basis is orthonormal, then there is no normalization factors on each projection.

The projection of a vector $x$ onto this subspace $U$ is the sum of the projection vectors on each of the bases
$$
\text{proj}_{U}x = \text{proj}_{u_{1}}x + \text{proj}_{u_{2}}x + \dots \text{proj}_{u_{m}}x
$$

If we know the projection of $x$ onto $U$, we know the component of the vector $x$ that can be represented with the basis of $U$. The remaining components of $x$ cannot be represented by the basis $U$, and therefore is orthogonal to $U$.

Then the shortest distance from the space mapped by $U$ to the point $x$ is the orthogonal component
$$
x - \text{proj}_{U}x
$$
### Matrix Representation
Just like how the overall vector can be represented as the sum of the projections, the matrix that represents the mapping is the sum of all of the matrices.

Since $P$ is a mapping only to $U$, it projects all vectors in $\mathbb{R}^n$ onto $U$. To map to the [[Orthogonal Complement]] $U^\perp$, it is equal to:
$$
P_{\perp}=I-P
$$
This kind of makes sense because the vector $x$ can be thought of the sum of two components: the sum of all of the components in $U$ and the sum of all components orthogonal to $U$.
$$
\vec{x}=\text{proj}_{U}x + \text{proj}_{U^\perp}x
$$
then $$
\vec{x}I = Px + P_{\perp}x
$$
