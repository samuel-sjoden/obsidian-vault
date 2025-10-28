### Finding Eigenvalues of $A$
Using the eigenvalue equation
$$
Av=\lambda v
$$
We can rewrite to find that the eigenvector $v$ must exist in the [[The Null Space and Range Space|null space]] of the matrix:$$
(A-\lambda I)v=0
$$
Since the null space of this matrix is non-zero, by rank-nullity theorem $\text{rank}(A) < n$ which implies that the [[Determinants|determinant]] is zero. From this we get the characteristic equation:
$$
\det(A-xI)=0
$$
Which results in a polynomial with roots equal to its eigenvalues.

#### Eigenvalue degeneracy and multiplicity
The characteristic equation can be factored into the form
$$
\pm \prod_{i=1}^{k} (x-\lambda_{i})^{m_{i}}
$$
Where $m_{i}$ corresponds to the [[Geometric Multiplicity]] of the eigenvalue. 