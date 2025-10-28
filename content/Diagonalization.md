An $n\times n$ matrix is a diagonal matrix if all of its elements of the main diagonal are zero. These matrices are favorable to do calculations with because of the reduced number of operations required to calculate them. 

If there is some transform $P$ that can be applied to $A$ and then its inverse applied $P^{-1}$ so that $A$ is left unchanged.
>[!Question]
> What is the fundemental property that keeps $A$ being $A$. Like when we perform row reduction on $A$, we modify the column space, but $A$ still remains $A$

$$
P^{-1}AP =D
$$
Where $D$ is an $n\times n$ diagonal matrix. We can turn this into a classic [[Eigenvalues and Eigenvectors|eigenvalue]] equation from the definition of $D$ which has elements $\begin{bmatrix}\lambda_{1} & \lambda_{2} & \dots & \lambda_{n}\end{bmatrix}$ on its diagonal.
$$
A\begin{bmatrix}
\mathbf{p_{1}} & \mathbf{p_{2}}  & \dots \mathbf{\mathbf{p_{n}}}
\end{bmatrix}=\begin{bmatrix}
\lambda_{1} \mathbf{p_{1}}  & \lambda_{2}\mathbf{p_{2}} & \dots  & \lambda_{n}\mathbf{p_{n}}
\end{bmatrix}
$$
So then we can conclude that if $A$ has $n$ eigenvectors such that $P$ is invertable $\to$ the columns are linearly independent $\to$ requires $n$ linearly independent eigenvectors.

For the matrix to be properly diagonalizable, the **Eigenvalues must be distinct**. That means that each eigenvalue can only correspond to a unique eigenvector. Equivalently, the **multiplicity of the eigenvalues can be no larger than $1$**. 