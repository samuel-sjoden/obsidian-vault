The commutator is an important relation between two operators that gives information about the commutativity of two operators. It is defined as follows:
$$
[\hat{A},\hat{B}]\equiv(\hat{A}\hat{B}-\hat{B}\hat{A})
$$
If $\hat{A}$ and $\hat{B}$ are commutative, then the commutator is zero. Knowing the output operator of the commutator can additionally be useful to know when wanting to reorder two operators that may not be commutative.

> [!Example]
>  The commutator of position and momentum:
>  
$$
x\left[ i\hbar \frac{d}{dx} \right]\psi-\left[ i\hbar \frac{d}{dx} \right]x\psi
$$
Expanding the second term with chain rule we get
$$
i\hbar \psi
$$
Therefore the commutator $[\hat{X},\hat{P}]=i\hbar$

### Commutative Operators
If two operators commute, it forces the operators to share eigenvectors in both the non-degenerate case and the degenerate case. This means that if two operators commute they share an eigenbasis.

If two observables share an eigenbasis, this means that if you take a measurement of one observable and force one state in this eigenbasis, you know what the other observable is because you have already forced to be a specific state in the eigenbasis.

### Non-Commutative Operators
The opposite is true for non-commutative operators like position and momentum. If two operators don't commute, we know that their eigenspaces are fully distinct. This gives insight into an uncertainty relation between operators that don't commute because each state in one basis is represented with a combination of vectors in the other basis.

The commutator ends up forming the [[Generalized Uncertainty Principle]], the [[Heisenberg's Uncertainty Principle]] is a specific case of with position and momentum.


>[!Question]
> If you can represent the space with either eigenbasis (they both span the same space) since you can have either a position or momentum representation, aren't the eigenvectors the same?

>[!Answer]
> Yes, they both span the same space, but the eigenvectors are different combinations of each other which is why if you have certainty in one domain, there is uncertainty in the other domain.

The standard deviation of a measurement $\Delta x$ is the width of the distribution of our measurements.
$$
\Delta x\equiv \sqrt{ \braket{ (\hat{X}-\braket{ \hat{X}} )^2  }  }
$$
The difference between what the expected measurement is and the actual output is the standard deviation.



