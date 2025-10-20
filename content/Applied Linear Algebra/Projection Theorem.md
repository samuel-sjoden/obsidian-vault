>[!Theorem]
> Let $U \subseteq \mathbb{R}^{n}$ and $x \in \mathbb{R}^{n}$,
> then the size of the projection component is always less than or equal to the magnitude of the difference of the components

> [!Proof]
> This is a triangle inequality, and geometrically we can picture a triangle. The component of $x$ not in $U$ it perpendicular to $U$.  Then the line between the end of $x$ and the end of any $u$ vector is always the hypotenuse of the triangle.
> $$
 \left| u-x\right|^{2} = \left| x -\text{proj}_{u}x \right| ^{2}+\left| u - \text{proj}_{u}x \right| ^{2}$$
> $$
\left| x -\text{proj}_{u}x \right| \leq \left| x-u \right|$$
> For any $u \in U$

This is how you can find the shortest distance between a subspace and a vector. Using the [[Orthogonal Projection]], $x-\text{proj}_{u}x$, we can guarantee it is always at least smaller than any difference of vectors in $u$.

>[!Question]
> Suppose $P$ is an orthogonal projection onti $U$
> 	1. Suppose $x \in U$ what is $Px$?
> 	2. Suppose $x \in U^{\perp}$ what is $Px$?

>[!Solution]
> 1. Just $x$. Imagine scaling an $x.y$ vector in the $x,y$ plane onto the $x,y$ plane
> 2. $\vec{0}$. Imagine a vector only in $\hat{z}$ projected onto the $x,y$ plane.

