### Infinite Square Well
An important piecewise defined potential that produces a piecewise defined wavefunction.

The boundary conditions at the walls of the potential well enforced that the $\psi(a,t) =0$ if a is a boundary.
The derivative of the wavefunction at the boundary is not continuous as a result of the aphysical system. *he explained it that since there is a second derivative in the SE it cannot be continuous for infinite potential*

All of the solutions to the Schrodinger of this potential are real.



Higher energy wavefunctions will oscillate at higher frequencies -> its in the power of the complex exponential.

Eigenstates of the Hamiltonian will have probabilities that do not evolve in time.


### Finite Square Well

If the potential does not go to infinity, the TISE for the well becomes $$
\frac{d}{dx}^2\psi(x) = \frac{2m(V-E)}{\hbar^2}\psi(x)
$$
Assuming that the potential outside is constant. If the constant term on the right is positive, the results are real exponentials. If negative the solutions are complex exponentials.

In the finite square well the time independent solutions are all real if $\hat{H}$ has no imaginary contributions.

##### Example
Ground state has no nodes.

On the left side, our solutions are decaying exponentials.
Inside the well, the solution can be sines and cosines. Since there is no nodes, the ground state must be a cosine.

Finite square well what does the ground state $\phi_{0}$ look like. Side note about drawing $\psi$ on potential wells does make sense because they are in a different domain.

The overall function looks like a decaying exponential outside, a cosine inside the well, and then the exponential decays to zero. 

To find the energy of the states we need to solve the boundary conditions to find k. 

Adjusting the width and height of the potential well affects the energy of the states and the number of states. If the ground state is very  close to zero, its exponential tails decay rapidly (k is small because $E_{0}$ is small). 

If the energy of the state is relatively high (comparable to the height of the well), it will decay for a long time.

>[!question]
>My intuition tells me larger values in the decaying exponent will result in a sharper decay
>For $\psi$ outside of the well 
> $$
\psi = Ae^{\pm kx}
$$

>[!answer]
> There are two $k$, $k_{1},k_{2}$ the $k_{1}$ on the outside decrease as the states increase in energy

>[!question]
>Since you would build the $\psi$ the same, if one side of the well was larger than the other would the inside still have the same odd/even behaviour?

There are no degenerate states in the one dimensional case. States that share the same energy are considered degenerate states. 

All eigenstates of the Hamiltonian are stationary states, i.e. their probability does not evolve in time.

### Multiple Potential Wells

As soon as we introduce potential wells that are next to each other, we can no longer apply the condition that the exponential decays to zero in the space between the wells.

**Looking at the space between**
Solutions have the form $$
\psi = Ae^{kx} + Be^{-kx}
$$
We can no longer cancel the one that does not decay, but we can also write it as hyperbolic sines and cosines.
$$
\psi = A'\sinh(kx) + B'\cosh(kx)
$$
which give us a symmetric and anti symmetric case.


##### Ground State for Two Wells
Left hand side $\psi$ is a decaying exponential
First well $\psi$ is an oscillatory wave function, and even cosine.
In between $\psi$ is a $\cosh$ 
And so forth

##### First Excited State
We want one node in the wave function. Having sines in the wells would result in two wells, so we just make the space in between a $\sinh$

##### Second Excited State
Symmetric even function with two nodes.
Adding a sine to each well, results in a node in each well and placing a $\cosh$ in between results in an even function.

>[!question]
> I don't have the intuition as to why the state in the well corresponds to the number of wells in the wavefunction


#### Modelling the $H^{2+}$ With Two Potential Wells
It is very unlikely that the electron would end up between the two protons, so our double well model should force the wave function in the middle nears zero.




