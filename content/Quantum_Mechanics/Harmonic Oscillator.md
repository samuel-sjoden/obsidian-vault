The harmonic oscillator describes systems that slosh between kinetic and potential energy. Some examples are mass spring systems and LC circuits.

To describe the wavefunctions that exist in this quadratic potential, we are going to use operators.


> If there is an operator who's [[Commutators]] with its adjoint is just one, what are the special properties of an operator which is it adjoint and itself

$$
\begin{align} \\
[O,O^{\dagger}]=1 \\
P\equiv O^{\dagger}O \\
[P, O^{\dagger}]= O^{\dagger}OO^{\dagger}-O^{\dagger}O^{\dagger}O=O^{\dagger} \\
[P, O]=O^{\dagger}OO-OO^{\dagger}O=[O^{\dagger},O]O=(-1)O=-O
\end{align}
$$
We can show that $O^{\dagger}\ket{p}$ where $\ket{p}$ is an eigenvector of the operator $P$, is also an eigenvector of $P$
$$
PO^{\dagger}\ket{p} =(p+1)O^{\dagger}\ket{p}
$$
$$
O^{\dagger}OO^{\dagger}\ket{p} = O^{\dagger}([O,O^{\dagger}]+O^{\dagger}O)\ket{p}
$$
Where we got this from this relation with the commutator.
$$
[O,O^{\dagger}]=OO^{\dagger}-O^{\dagger}O
$$
If we know an eigenvector $\ket{p}$ we can now easily find another eigenvector $O^{\dagger}\ket{p}$ We can call this eigenvector $\ket{p+1}$.
$$
O^{\dagger}\ket{p} = c_{p}\ket{p+1}
$$
Where $c_{p}$ is a scaling factor for the vector $\ket{p+1}$. 
$$
c_{k}^*\bra{p+1} = \bra{p}O
$$
$$
\braket{ p | OO^{\dagger}|p } =c_{p}^*c_{p}\braket{ p+1 | p+1 } = c_{p}^2=(p+1)
$$
$$
O^{\dagger}\ket{p} =\sqrt{ p+1 }\ket{p+1}
$$
and
$$
O\ket{p} =\sqrt{ p }\ket{p-1}
$$
Now since $p\geq 0$ we can make further guarantees on $p$ because if we keep applying $O$ to $\ket{p}$ we want to ensure that it eventually reaches zero and not a negative number. $p$ must then be an integer.

Here $\hat{O}$ and $\hat{O}^{\dagger}$ are ladder operators.

## Solutions to Harmonic Oscillator
Using the above findings about operators we can rewrite the Hamiltonian of the harmonic oscillator so that it has the form of a $\hat{P}$. Then we can guarantee that it's eigenvalues will be $0,1,2,3\dots$. 

$$
\hat{H}=\hbar\omega\left( \hat{N} + \frac{1}{2} \right)
$$
Where $\hat{N}$ is the operator that has the properties of the $\hat{P}$ operator above.

 > Does an operator applied to a state vector not have to preserve normalization?
 
 > [!Example]
 A particle is prepared with state $\ket{10}$. What is its  expected kinetic energy ($\frac{\hbar\omega}{2}\mathbf{\hat{P}^2}$).
 
 > To solve this we rewrite the unit less momentum operator in terms of ladder operators $-\frac{1}{\sqrt{ 2 }}(\hat{a}^{\dagger}-\hat{a})^2$. We can find the expectation value with an inner product. The ladder operators act like ladder operators lol.
 
 >[!Example]
 > A particle in a harmonic oscillator is prepared in the state $$
\ket{\psi(t=0)}  = \frac{1}{\sqrt{ 2 }}(\ket{10} +\ket{11} )$$
> Find $\left< \hat{x}(t) \right>$

> The first step is to find the time dependent state vector $$
\ket{\psi(t)} = \frac{1}{\sqrt{ 2 }}(e^{ -iE_{10}t/\hbar }\ket{10} + e^{ -iE_{11}t/\hbar }\ket{11} )$$
> This can be rewritten as a global phase and a relative phase.
> Rewrite $\left< \hat{x} \right>$ in terms of $\left< \mathbf{\hat{X}} \right>$ so that we can use our ladder operators.
> $$
\left< \hat{x} \right> =\sqrt{ \frac{\hbar}{m\omega} } \left< \mathbf{\hat{X}} \right>$$
> Since we know that $\hat{a}$ will bring the $\ket{10}$ into a $\ket{9}$ which is not seen on the bra side. Same with $\hat{a}^{\dagger}$ which turns $\ket{11}$ into $\ket{12}$ which is also orthogonal to 10 and 11 bras
> $$
\left< \mathbf{\hat{X}} \right>  = \frac{1}{2\sqrt{ 2 }}(\bra{10} + e^{ i\Delta E t/\hbar }\bra{11} )(\sqrt{ 11 }\ket{11}  + e^{ -i\Delta Et/\hbar }\sqrt{ 11 }\ket{10} )$$
> I have left out the kets that would have just turned out to be zero.
> $$
\left< \mathbf{\hat{X}} \right> = \sqrt{ \frac{11}{2} }\cos\left( \frac{\Delta Et}{\hbar} \right)$$
> $$\boxed{\left< \hat{x} \right>=\sqrt{ \frac{\hbar}{\omega m} }\sqrt{ \frac{11}{2} }\cos\left( \frac{\Delta Et}{\hbar} \right)}$$


### Superpositions of Energy Eigenstates

The probability density of position with eigenstates of the Hamiltonian are fixed in time. If the state vector is a superposition of energy eigenstates, a relative phase is introduces and the probability density that shifts.

In the case of adjacent superposition states, the ladder operators which move the states up and down, result in non-zero expectation values (the kets don't cancel). If the states aren't adjacent, the ladder operator cannot "reach" the states and the inner product becomes zero. The probability still evolves in time, but it remains even, so that the expectation value of position remains zero.




