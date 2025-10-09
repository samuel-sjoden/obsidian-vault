This is an aproximation for complex charge distributions from a distance where we assume $\vec{r}\gg \vec{r}'$. A simlifying expansion is used to reduce the complexity when finding the potential of a charge distribution.

The expansion is decaying, therefore the most domanant term is the monopole, then dipole and so forth. The definition of the dipole moments is independent of the coordinate system defintion if the net charge of the system is zero $Q=0$(its a [[Tensors]]!). This is not true of $Q\neq0$.
 > [!Question]
 >  What why this does not make sense. Why does it depend on the definition of the coordinate system? I guess you can do transforms between the coordinate systems and have different results
 
## Applying Expansion to $\vec{E}$
The electric field can addionaly be simplified with the expansion which can be obtained by finding the negative gradient of each monopole of $V(\vec{r})$.

Moment is a something multiplied by a power of coordinate.


### $\rho$ with point Charges
If $\rho$ is a system with $a$ point charges, then the moment expansions become discrete sums over each point charge.


## Physical Dipole Vs. Ideal Dipole
The dipole moment term turns out to not be an exact prediction of the feild of the feild of a physical diode. The monopole moment term is zero because of the zero net charge, but the remaining terms in the expansion still exist.

$$
V(\vec{r})= V_{0}+V_{1}+V_{2}+\dots
$$
Where $V_{n}$ are the contributions from the multipole expansion. For the case of the dipole $V_{0}=0$.  So the representation of the physical dipole is 
$$
V_{phys}(\vec{r})=\frac{kqd\cos(\theta)}{r^2}+O\left( \frac{1}{r}\left( \frac{d}{r} \right) ^2 \right)
$$
The first term is the model for an ideal or point like dipole. This is a good approximation when $r\gg d$, i.e. you are looking at a point that is far away relative to the size of the system.

#### Ideal Dipole Moment of $\vec{E}$
We can apply the negative gradient to the ideal dipole to find the electric feild.
$$
\vec{E} =-\nabla V
$$
$$
\begin{align}
V(\vec{r})=\frac{\frac{1}{4\pi\epsilon_{0}}p\cos(\theta)}{r^2} \\
\nabla V=-2\frac{kp\cos(\theta)}{r^3}\hat{r}+\frac{1}{r}\times-\frac{kp\sin(\theta)}{r^2}\hat{\theta} \\
-\nabla V=\vec{E}=\frac{2kp\sin(\theta)}{r^3}\hat{r}+\frac{kp\sin(\theta)}{r^3}\hat{\theta}
\end{align}
$$
This vector feild remains curl free because by defintion $V$ is a potential function.


