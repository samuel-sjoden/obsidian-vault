When solving the [[Schrodinger Equation in 3D]] the seperation was done in 3D. To take advantage of symmetries in spherically symmetric potentials, spherical coordinates is used.

This is often used when the potential cannot be seperated into three cartesian components but can be written as a distance an orgin (radial component).
$$
V(\vec{r})=V(r)
$$
We again perform [[Seperation of Variables]] on the schodinger eqution:
$$
-\frac{\hbar}{2m}\nabla^{2}\psi(r,\phi,\theta) + V(r)\psi(r, \phi, \theta) = E\psi(r,\phi,\theta)
$$
The radial component gets seperated into a portion dependent only on $r$ and a portion dependent only on angular components $\phi,\theta$.  The momentum term is broken into radial momentum and [[Angular Momentum]]. 
$$
\psi(r,\phi,\theta)=R(r)Y(\phi,\theta)
$$
The resulting solution is much more connected. The solution of one component forces the solution of the other.

> [!Question]
>  Why does a larger state magnitude no necesarrily mean that we are more likely to find the particle there? Do I have a confusion between probability density and expectation value?

## Normalization in Spherical Coordinates
As before, for the total probabilty to be $1$, then then integral of the modulus squared of the wavefunction over all space must be 1.
$$
\int_{\text{all space}} \left| \psi(\vec{r}) \right| ^{2}d\tau = 1
$$
$$
\left[ \int_{0}^{\infty}\left| R(r) \right| ^{2}r^{2}  \, dr \right] \left[ \int_{0}^{\Omega'} \left| Y(\phi,\theta) \right| ^{2}\sin(\theta) \, d\Omega  \right]=1
$$
How to interpret this integral:
- The radial one is the probability of finding the particle at an r, after considering all angles
- The angular one tells you the likleyhood of finding the particle at a given angle considering all radii

> [!Answer]
> This extra $r^{2}$ factor in the probability calculation explains just why the actual radial function is not exactly the probability density. There is another $r^{2}$ factor in there. 

This is why the solution to the spherical well has a radial function with greatest magnitude at the center, but the probability is more evenly distributed. This is why the solution $u(r)=rR(r)$.
$$
\int_{0}^{\infty}\left| u(r) \right| ^{2}dr=1
$$
