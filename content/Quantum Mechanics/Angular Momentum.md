In classical physics, angular momentum describes a particles desire to continue spinning.
$$
\vec{L}=\vec{r}\times \vec{p}
$$
## Finding Ladder Operators
Moving to quantum mechanics, the terms can be represented as operators. The operator in each direction $(x,y,z)$ do not commute.  Finding the [[Commutators]] of the elements of angular momentum can be done like so (THIS IS THE UNITLESS ONE!):
$$
\begin{align}
\left[ \hat{L}_{x}\hat{L}_{y} \right] = i\hat{L}_{z} \\

\end{align}

$$Here we can write a sort of ladder operators similar to what was done for the [[Harmonic Oscillator]]. It is slightly different because the commutator is another operator itself and not just a constant.

We can find that $\hat{L}_{z}$ and $\hat{L}^{2}$ commute, so we can simultaneously find eigenvalues for both $\hat{L}^{2}$ and $\hat{L}_{z}$. We can define two operators $\hat{L}_{+},\hat{L}_{-}$ that commute with $\hat{L}^{2}$ but not with $\hat{L}_{z}$, we can show that the $\hat{L}_{+},\hat{L}_{-}$ raise and lower the state for $\hat{L}_{z}$ but not for $\hat{L}^{2}$. 

The ladder operators $\hat{L}_{+},\hat{L}_{-}$ affect the angular momentum in one component, but never the overall momentum of the state.
### Condition Between The Eigenvalues of $\hat{L}^{2}$ and $\hat{L}_{z}$
Since $\hat{L}^{2}$ is defined by:
$$
\hat{L}^{2}=\hat{L}_{z}^{2} + \hat{L}_{y}^{2} + \hat{L}_{z}^{2}
$$
So the eigenvalues, which represent the angular momentum of the state. The sum of the squares of the angular momentum in each direction must be $\hat{L}^{2}$ eigenvalue. More discussion on this is present in the [[Eigenfunctions Of  Angular Momentum]].

This gives and upper and lower bound on the possible values of the eigenvalues of $\hat{L}_{z}$. Since none of the components of angular momentum do not commute with each other, you can only know one component and magnitude squared of the angular momentum of the state.

>[!Question]
> Why are only half integer values of $l$  allowed?

> [!Example]
> **State With Maximum $\hat{L}_{z}$**
> Given the state $\ket{2,2}$, it has $\left< \hat{L}^{2} \right> =6\hbar^{2}$ and $\left< \hat{L}_{z}^{2} \right> = 4\hbar^{2}$
> We can use the ladder operators to find that $\left< \hat{L}_{x} \right> = 0$ because of the symmetry of the problem. There is no preference to have a state of positive or negative angular momentum in x. To find where the value "hangs around" we find $\left< \hat{L}_{x}^{2} \right> = \hbar^{2}$ which again is consistent with the symmetry where $\hat{L}_{x}, \hat{L}_{y}$ are neither prefered



