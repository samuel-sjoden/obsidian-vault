>[!Definition]
> $A \in \mathbb{R}^{m\times n}$ is an **orthogonal matrix** if $$
 A^{T}A=AA^{T}=I$$
 > - The rows of $A$ are orhonormal
 > - The columns of $A$ are orthonormal
 > If one of these conditions are met, the matrix is orthogonal (You dont need orthonormal rows AND columns, just one of the other is sufficent)
 > This further implies that $A^{T}=A^{-1}$.
 >  The identity matrix $I$ is an example of an orthogonal matrix.

>[!Intuition]
> say my columns are a set of orthonormal vectors $$
A = \{ u_{1}, u_{2}, u_{3} \}$$
> Then when I take the transpose, they become my row space.
> $$
 A^{T} = \begin{bmatrix}
 u_{1}^{T} \\
 u_{2}^{T} \\
 u_{3}^{T}
\end{bmatrix}$$
> Then doing matrix multiplication, the only non zero elements will be when the vectors are dotted with themselves. Since we know that they are orthonormal,
> $$
 u_{1}^{T}u_{1}=\left| \left| u \right|  \right| ^{2} = 1$$
 
 This means that the columns of the matrix are orthonormal to the row vectors. If the columns are only [[Orthogonal]], then $A^{T}A$ is a diagonal matrix. If the rows of the matrix $A$ are orthonormal, then taking the transpose results in the columns being orthonormal. 
 
 This means that $A^{-1}$ is also orthogonal if $A$ is orthogonal

What makes orthogonal matrices is how simple it is to find the inverse of the matrix
$$
A^{T}=A^{-1}
$$
If $A$ is an orthogonal matrix, then when it performs transforms on $x$, then it will never scale the magnitude of the vector, only change its direction.
$$
\left| \left| Ax \right|  \right| =\left| \left| x \right|  \right|
$$
The rotation matrix is an orthogonal matrix, and it clearly has this property since it only produces rotations in the vectors and never scales them.

It's like you are showing how much in each orthonormal basis the input vector $x$ has. Thats why its not being scaled.

>[!Question]
> Does this imply that the [[Condition Number]] of an orthogonal matrix is always one?

