$LU$ decomposition is a way of decomposing a matrix $A$ into a product of two matrices $L$ and $U$. Not all matrices $A$ have an $LU$ decomposition. A more general form includes a permutation matrix $P$ so that matrices like
$$
\begin{bmatrix}
0 & 1 \\
1 & 0
\end{bmatrix}
$$ Can be decomposed. 

### Importance
$LU$ decomposition is helpful in computational linear algebra for computations that require solutions to the same system with different forcing terms ($\vec{b}$). The computations to find solutions in an already $LU$ decomposed system is much faster than row reduction or finding an inverse and performing matrix multiplication.

In this case it is much faster to perform one computation to reduce the matrix into two matrices: An upper triangular $L$ matrix that describes the row operations that were done to the matrix $A$ to get it into [[Row Echelon Form]].  It is the inverse of all of the product of all of the elementary matrices it takes to reduce $A$.

The other matrix $U$ is the REF form of $A$. 

### Finding Solutions
Once you have an $A=LU$ you can do a process of forward  and backward substitution to find a solution to:
$$
Ax=b
$$
**Step 1.**
$$
LUx=b
$$
The term $Ux$ is really just a vector that we can call $y$ for now.
$$
Ly=b
$$
Since $L$ is a lower triangular matrix, the solution can easily be found.

**Step 2.**
Once you have found the $y$ vector, a quick backward substitution can be used to find the solution $x$

$$
Ux=y
$$
### Properties of $LU$ Decomposition
When performing $LU$ decomposition, the $U$ matrix undergoes row operations that modify the equations, but do not affect the row space of the matrix $A$. This cannot be said for the column space. The column space of the matrix is not preserved by the row operations. $A$ and $U$ do not share the same [[Range Space]]. 

Their transposes on the other hand do, because of the preservation of the row space of the matrix.